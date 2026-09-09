Markdown
# 📊 Análisis de Ventas y Dashboard Ejecutivo en Excel

## 📌 Descripción del Proyecto
Este proyecto simula el ciclo completo de análisis de datos de un **Analista Junior de Retail**: desde la ingesta e ingeniería de datos hasta la creación de un Modelo Relacional ($1:N$) y la construcción de un **Dashboard Ejecutivo Interactivo**.

El objetivo principal fue transformar un dataset transaccional crudo con problemas de calidad (duplicados, inconsistencias de formato y campos nulos) en una herramienta reproducible para la toma de decisiones estratégicas.

---

## 🖼️ Dashboard Interactivo

![Preview del Dashboard]
https://github.com/PabloBellu/Excel-Sales-Analytics-Dashboard/blob/main/Excel_Sales_Analytics_Dashboard/Assets/Captura%20Dashboard.png

---

## 🏗️ Arquitectura y Metodología de Trabajo

### 1. Limpieza y Preparación de Datos (ETL)
* **Estandarización:** Corrección de categorías de productos y nombres de regiones.
* **Tratamiento de Nulos:** Imputación de registros transaccionales sin cliente asignado.
* **Columnas Calculadas:** Clasificación de ventas mediante lógica condicional:
  ```excel
  =SI([@Cantidad]>=10; "Venta Alta"; "Venta Normal")

2. Modelado de Datos (Power Pivot)
Diseño de un Esquema en Estrella ($1:N$) conectando la tabla transaccional (tbl_Ventas) con las tablas maestras de dimensión (tbl_Productos y tbl_Clientes).

3. Métricas y Programación en DAX
Creación de medidas explícitas para evitar el uso de medidas implícitas en los reportes:
-Venta Total:
Fragmento de código
Venta Total := SUMX(tbl_Ventas, tbl_Ventas[Cantidad] * tbl_Ventas[Precio_Unitario] * (1 - IF(ISBLANK(tbl_Ventas[Descuento]), 0, tbl_Ventas[Descuento])))
-Unidades Vendidas:Fragmento de códigoUnidades Vendidas := SUM(tbl_Ventas[Cantidad])
-Total Transacciones:Fragmento de códigoTotal Transacciones := DISTINCTCOUNT(tbl_Ventas[ID_Transaccion])

📈 Insights y Hallazgos Clave de Negocio 
-Categoría Líder: Electrónica concentra el 28,6% del volumen total de ingresos, seguida por Tecnología (26,8%). Entre ambas explican más del 55% de la facturación global.
-Rendimiento Regional: Mendoza lidera las ventas por región representando el 43% de los ingresos totales y 1.449 unidades vendidas, superando a Córdoba (40,8%) y Buenos Aires (15,6%).
-Tendencia Operativa: Se observa una correlación directa entre el monto facturado y el volumen físico despachado, con un promedio superior a 300 unidades comercializadas por jornada.

🛠️ Herramientas Utilizadas
Microsoft Excel Desktop (Power Pivot, Tablas Dinámicas, DAX, CUBEVALUE, Slicers).Modelado de Datos Relacional (Esquema en Estrella $1:N$).
