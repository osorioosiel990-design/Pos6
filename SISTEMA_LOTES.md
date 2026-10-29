# 📦 Sistema de Lotes - Productos con Diferentes Precios

## 🎯 ¿Cómo Funciona?

El sistema utiliza **lotes de compra** con método **FIFO (First In, First Out)** para manejar el mismo producto con diferentes precios de compra.

---

## 📊 Ejemplo Práctico

### Escenario: Lámparas LED

**Compra 1 (Enero):**
```
Producto: Lámpara LED
Cantidad: 10 unidades
Precio compra: 5 USD cada una
Total invertido: 50 USD
Lote ID: 1
```

**Compra 2 (Marzo):**
```
Producto: Lámpara LED
Cantidad: 15 unidades
Precio compra: 6 USD cada una (subió el precio)
Total invertido: 90 USD
Lote ID: 2
```

**Inventario actual:**
```
Lámpara LED:
- Stock total: 25 unidades
- Lote 1: 10 unidades a 5 USD = 50 USD
- Lote 2: 15 unidades a 6 USD = 90 USD
- Inversión total: 140 USD
- PEP (Precio Promedio): 5.6 USD por unidad
```

---

## 🔄 Método FIFO (First In, First Out)

Cuando vendes lámparas, el sistema usa primero las más antiguas:

### Venta 1: Vender 8 lámparas
```
Sistema busca lotes (ordenados por fecha):
1. Lote 1 (Enero): 10 unidades disponibles
   → Usa 8 unidades del Lote 1
   
Resultado:
- Lote 1: 10 - 8 = 2 unidades restantes
- Lote 2: 15 unidades (no se tocó)
- Costo de venta: 8 × 5 USD = 40 USD
```

### Venta 2: Vender 5 lámparas más
```
Sistema busca lotes:
1. Lote 1 (Enero): 2 unidades disponibles
   → Usa 2 unidades del Lote 1
2. Lote 2 (Marzo): 15 unidades disponibles
   → Usa 3 unidades del Lote 2
   
Resultado:
- Lote 1: 2 - 2 = 0 unidades restantes (agotado)
- Lote 2: 15 - 3 = 12 unidades restantes
- Costo de venta: (2 × 5) + (3 × 6) = 10 + 18 = 28 USD
```

---

## 📋 Cómo Ver los Lotes

### En Inventario:
1. Ir a **Inventario**
2. Buscar el producto (ej: Lámpara LED)
3. Click en el botón **"X lotes"** (donde X es el número de lotes activos)
4. Se abre una ventana mostrando:

```
📦 Lotes de Compra - Lámpara LED
Total invertido en lotes activos: 140 USD

Fecha      | Proveedor  | Cant. Original | Restante | Precio USD | Destino    | Inversión
-----------|------------|----------------|----------|------------|------------|----------
01/01/2024 | ProveedorA | 10             | 2        | 5.00       | 🏪 Tienda  | 10.00 USD
01/03/2024 | ProveedorB | 15             | 12       | 6.00       | 📦 Almacén | 72.00 USD
```

---

## 💰 Cálculo de Ganancia Real

El sistema calcula la ganancia usando el **costo real** de cada lote:

### Ejemplo de Venta:
```
Vendiste 5 lámparas a 10 USD cada una
Total venta: 50 USD

Costo real (FIFO):
- 2 unidades del Lote 1: 2 × 5 = 10 USD
- 3 unidades del Lote 2: 3 × 6 = 18 USD
- Costo total: 28 USD

Ganancia real:
50 USD (venta) - 28 USD (costo) = 22 USD ✅
```

**NO se usa el PEP promedio**, se usa el costo real de cada lote.

---

## 🎯 Beneficios del Sistema de Lotes

### 1. **Precisión en Costos**
- ✅ Calcula el costo real de cada venta
- ✅ No promedia precios (lo que puede ser engañoso)
- ✅ Refleja la realidad del negocio

### 2. **Control de Inventario**
- ✅ Sabes exactamente cuántas unidades compraste a cada precio
- ✅ Puedes ver qué proveedor te vendió más barato
- ✅ Identificas lotes antiguos que no se han vendido

### 3. **Análisis de Rentabilidad**
- ✅ Sabes la ganancia real por venta
- ✅ Puedes identificar qué lotes son más rentables
- ✅ Tomas mejores decisiones de compra

### 4. **Trazabilidad**
- ✅ Cada unidad vendida se rastrea a su lote original
- ✅ Puedes ver el historial completo de compras
- ✅ Útil para auditorías y control

---

## 📊 Ejemplo en Cierres

### Cierre Diario:
```
Ventas del día:
- 5 lámparas a 10 USD = 50 USD

Inversión (costo real FIFO):
- 2 del Lote 1 (5 USD) = 10 USD
- 3 del Lote 2 (6 USD) = 18 USD
- Total inversión: 28 USD

Ganancia:
- 50 USD - 28 USD = 22 USD ✅
```

### Cierre Semanal:
```
Ventas de la semana:
- 20 lámparas vendidas
- Total ventas: 200 USD

Inversión de la semana:
- Costo real de las 20 lámparas vendidas
- Usando FIFO: 110 USD

Ganancia de la semana:
- 200 USD - 110 USD = 90 USD ✅
```

---

## 🔍 ¿Cuándo se Crean Lotes?

Los lotes se crean automáticamente cuando:

1. **Registras una compra** en la sección "Compras"
   - Cada compra crea un nuevo lote
   - El lote incluye: cantidad, precio, fecha, proveedor, destino

2. **NO se crean lotes** cuando:
   - Creas un producto directamente desde "Inventario"
   - En este caso, el sistema usa el PEP del producto como costo

---

## 💡 Recomendaciones

### Para Productos con Precios Variables:
- ✅ **Usa siempre la sección "Compras"** para registrar entradas
- ✅ Esto crea lotes y permite cálculo preciso de costos
- ✅ Es ideal para productos importados con precios en USD

### Para Productos con Precios Fijos:
- ✅ Puedes crearlos directamente desde "Inventario"
- ✅ El sistema usará el PEP como costo
- ✅ Es más simple pero menos preciso

### Para Análisis Detallado:
- ✅ Revisa los lotes periódicamente
- ✅ Identifica lotes antiguos que no se venden
- ✅ Toma decisiones sobre descuentos o promociones

---

## 📈 Ejemplo Completo de Negocio

### Mes 1:
```
Compra: 10 lámparas a 5 USD = 50 USD
Venta: 8 lámparas a 10 USD = 80 USD

Costo real (FIFO): 8 × 5 = 40 USD
Ganancia: 80 - 40 = 40 USD
Stock restante: 2 lámparas (Lote 1)
```

### Mes 2:
```
Compra: 15 lámparas a 6 USD = 90 USD
Venta: 12 lámparas a 10 USD = 120 USD

Costo real (FIFO):
- 2 del Lote 1: 2 × 5 = 10 USD
- 10 del Lote 2: 10 × 6 = 60 USD
- Total: 70 USD

Ganancia: 120 - 70 = 50 USD
Stock restante: 5 lámparas (Lote 2)
```

### Total Acumulado:
```
Inversión total: 50 + 90 = 140 USD
Ventas totales: 80 + 120 = 200 USD
Costo total: 40 + 70 = 110 USD
Ganancia total: 200 - 110 = 90 USD ✅
```

---

## ✅ Resumen

- ✅ **Lotes**: Cada compra crea un lote con su precio específico
- ✅ **FIFO**: Las ventas usan primero los lotes más antiguos
- ✅ **Costo real**: Se calcula usando el precio real de cada lote
- ✅ **Ganancia precisa**: Venta - Costo real (no promedio)
- ✅ **Trazabilidad**: Puedes ver el historial completo de cada producto
- ✅ **Control**: Sabes exactamente qué tienes y a qué precio

---

**Fecha:** 2024  
**Estado:** ✅ Sistema de lotes completamente funcional
