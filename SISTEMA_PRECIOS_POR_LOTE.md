# 💰 Sistema de Precios por Lote - Caso de Uso: Lámparas

## 🎯 Problema Resuelto

**Situación:**
- Compras lámparas antiguas a 5 USD y las vendes a 10 USD
- Los precios suben y compras lámparas nuevas a 7 USD
- Quieres seguir vendiendo las lámparas viejas a 10 USD
- Pero las lámparas nuevas deben venderse a 14 USD (para mantener margen)

**Solución:**
El sistema ahora permite definir **precios de venta específicos para cada lote**, manteniendo el método FIFO (First In, First Out).

---

## 📊 Ejemplo Completo

### Paso 1: Primera Compra (Enero)

```
Compras: 10 lámparas
- Precio compra: 5 USD cada una
- Precio venta: 10 USD cada una (margen: 100%)
- Total invertido: 50 USD

Sistema crea:
✅ Lote 1:
   - Cantidad: 10 lámparas
   - Precio compra: 5 USD
   - Precio venta: 10 USD
   - Fecha: Enero
```

### Paso 2: Ventas (Febrero - Marzo)

```
Vendes: 6 lámparas a 10 USD cada una
- El sistema usa el Lote 1 (FIFO)
- Lote 1 ahora tiene: 4 lámparas restantes
- Ganancia: 6 × (10 - 5) = 30 USD
```

### Paso 3: Segunda Compra (Abril) - Precios Subieron

```
Compras: 15 lámparas nuevas
- Precio compra: 7 USD cada una (subió de 5 USD)
- Precio venta: 14 USD cada una (ajustas para mantener margen)
- Total invertido: 105 USD

Sistema crea:
✅ Lote 2:
   - Cantidad: 15 lámparas
   - Precio compra: 7 USD
   - Precio venta: 14 USD ← NUEVO PRECIO
   - Fecha: Abril
```

### Paso 4: Ventas Continúan (Mayo)

```
Vendes: 5 lámparas a 10 USD cada una
- El sistema usa el Lote 1 (más antiguo, FIFO)
- Lote 1 ahora tiene: 4 - 4 = 0 lámparas restantes (agotado)
- Ganancia: 4 × (10 - 5) = 20 USD

Vendes: 1 lámpara más
- Lote 1 está agotado, sistema usa Lote 2
- Vende a 14 USD (precio del Lote 2)
- Ganancia: 1 × (14 - 7) = 7 USD
```

---

## 🎮 Cómo Usar en la Aplicación

### Al Crear/Editar un Producto

1. Ir a **Inventario**
2. Click en **"+ Nuevo"** o editar un producto existente
3. Seleccionar **Modo de Precio**:
   - **Modo CUP** 🔒: Precios en CUP son fijos, no cambian con la tasa
   - **Modo USD** 💲: Precios en USD son fijos, CUP se actualiza con la tasa

### Al Registrar una Compra

1. Ir a **Compras**
2. Click en **"+ Nueva Compra"**
3. Seleccionar producto
4. Ingresar:
   - **Cantidad**: 15 lámparas
   - **Precio Compra CUP/USD**: 7 USD
   - **Precio Venta CUP/USD**: 14 USD ← **IMPORTANTE: Definir precio de venta para este lote**
   - **Proveedor**: Nombre del proveedor
   - **Destino**: Tienda o Almacén
5. Click en **"Registrar"**

### Al Vender en el POS

1. Ir a **POS**
2. Buscar producto (ej: Lámpara)
3. El sistema automáticamente:
   - Busca el lote más antiguo con stock (FIFO)
   - Usa el precio de venta de ese lote
   - Si el Lote 1 tiene precio 10 USD, vende a 10 USD
   - Si el Lote 1 se agota y pasa al Lote 2, vende a 14 USD

### Ver Lotes en Inventario

1. Ir a **Inventario**
2. Buscar el producto
3. Click en **"X lotes"** (botón azul)
4. Ver tabla con todos los lotes:

```
Fecha    | Proveedor | Cant. | Rest. | Compra CUP | Compra USD | Venta CUP | Venta USD | Destino | Inversión
---------|-----------|-------|-------|------------|------------|-----------|-----------|---------|----------
01/01/24 | ProveedorA| 10    | 0     | 1750       | 5.00       | 3500      | 10.00     | 🏪      | 0
01/04/24 | ProveedorB| 15    | 14    | 2450       | 7.00       | 4900      | 14.00     | 🏪      | 34300
```

**Nota:** Cada lote muestra su propio precio de venta específico.

---

## 🔍 Filtros por Modo de Precio

En **Inventario**, puedes filtrar productos por su modo de precio:

- **💵 Modo CUP (precios fijos)** 🔒: Productos cuyos precios en CUP no cambian con la tasa
- **💵 Modo USD (se actualiza con tasa)** 💲: Productos cuyos precios en CUP se actualizan automáticamente

### Iconos Visuales

En la tabla y tarjetas de inventario verás:

- 🔒 **Candado**: Producto en Modo CUP (precios fijos)
- 💲 **Dólar**: Producto en Modo USD (se actualiza con la tasa)

Estos iconos te permiten identificar rápidamente qué productos se verán afectados cuando cambies la tasa en Ajustes.

---

## 📈 Beneficios

### 1. **Control de Margen por Lote**
- ✅ Cada lote mantiene su propio margen
- ✅ No pierdes dinero por cambios de precio
- ✅ Puedes ajustar precios según el costo real

### 2. **Trazabilidad Completa**
- ✅ Sabes exactamente qué lote se vendió
- ✅ Puedes ver el historial de precios
- ✅ Identificas qué proveedores son más rentables

### 3. **FIFO Inteligente**
- ✅ Vende primero lo más antiguo
- ✅ Evita productos obsoletos en inventario
- ✅ Calcula ganancia real basada en costo específico

### 4. **Flexibilidad de Precios**
- ✅ Puedes mantener precios viejos para stock antiguo
- ✅ Ajustar precios nuevos para stock nuevo
- ✅ No afectar clientes con cambios bruscos

---

## 💡 Ejemplo de Negocio Real

### Escenario: Ferretería con Productos Importados

**Situación:**
- Tasa actual: 350 CUP/USD
- Compras herramientas a 10 USD
- Las vendes a 20 USD (margen 100%)

**Problema:**
- Tasa sube a 400 CUP/USD
- Nuevo costo: 10 USD = 4000 CUP (antes 3500 CUP)
- Si mantienes precio de venta: 20 USD = 8000 CUP
- Margen se reduce significativamente

**Solución con Precios por Lote:**

```
Lote 1 (comprado con tasa 350):
- Costo: 3500 CUP (10 USD)
- Venta: 7000 CUP (20 USD)
- Margen: 3500 CUP ✅

Lote 2 (comprado con tasa 400):
- Costo: 4000 CUP (10 USD)
- Venta: 8000 CUP (20 USD) ← Ajustas precio
- Margen: 4000 CUP ✅
```

**Resultado:**
- Vendes Lote 1 a precio viejo (7000 CUP)
- Vendes Lote 2 a precio nuevo (8000 CUP)
- Mantienes margen en ambos lotes
- No afectas clientes con cambios bruscos

---

## 🎯 Casos de Uso

### 1. **Productos con Precios Estables**
- **Modo recomendado**: CUP 🔒
- **Ejemplo**: Productos nacionales, servicios
- **Ventaja**: Precios predecibles, no cambian con tasa

### 2. **Productos Importados**
- **Modo recomendado**: USD 💲
- **Ejemplo**: Electrónica, herramientas importadas
- **Ventaja**: Mantienes margen en USD, CUP se ajusta automáticamente

### 3. **Transición de Precios**
- **Situación**: Precios de compra subieron
- **Solución**: Crear nuevo lote con precio de venta más alto
- **Ventaja**: Vendes stock antiguo a precio viejo, nuevo a precio nuevo

### 4. **Promociones Específicas**
- **Situación**: Quieres hacer promoción en lote específico
- **Solución**: Crear lote con precio de venta promocional
- **Ventaja**: Promoción controlada, no afecta otros lotes

---

## 🔧 Configuración en Ajustes

En **Ajustes → Opciones de Comportamiento**:

- ✅ **Actualizar precios con tasa**: Si está activado, al cambiar la tasa se actualizan automáticamente los precios CUP de productos en Modo USD
- ✅ **Mostrar equivalentes**: Muestra el equivalente en la otra moneda

**Importante:**
- Solo se actualizan productos en **Modo USD** 💲
- Productos en **Modo CUP** 🔒 no se ven afectados
- Los lotes mantienen sus precios específicos

---

## 📊 Reportes y Métricas

### En Cierres Diarios/Semanales

El sistema calcula:
- ✅ **Inversión**: Suma de costos reales de cada lote vendido
- ✅ **Ganancia**: Ventas - Inversión (usando precios específicos de cada lote)
- ✅ **Margen real**: Basado en costo específico, no promedio

### En Métricas

- ✅ **Top productos más vendidos**: Considera precios específicos de lotes
- ✅ **Top productos mayor ganancia**: Calcula ganancia real por lote
- ✅ **Margen promedio**: Basado en costos reales

---

## ✅ Resumen

El sistema de precios por lote te permite:

1. ✅ **Definir precios de venta específicos** para cada compra
2. ✅ **Mantener precios viejos** para stock antiguo
3. ✅ **Ajustar precios nuevos** para stock nuevo
4. ✅ **Controlar márgenes** por lote
5. ✅ **Identificar rápidamente** productos por modo de precio (🔒 CUP / 💲 USD)
6. ✅ **Filtrar productos** por modo de precio
7. ✅ **Trazabilidad completa** de costos y precios

**Resultado:** Control total sobre tus precios y márgenes, incluso cuando los costos de compra cambian.

---

**Fecha:** 2024  
**Estado:** ✅ Implementado y funcionando  
**Build:** ✅ Exitoso (7.15s)
