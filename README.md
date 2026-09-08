Markdown
# 📊 Análisis de Ventas y Dashboard Ejecutivo en Excel

## 📌 Descripción del Proyecto
Este proyecto simula el ciclo completo de análisis de datos de un **Analista Junior de Retail**: desde la ingesta e ingeniería de datos hasta la creación de un Modelo Relacional ($1:N$) y la construcción de un **Dashboard Ejecutivo Interactivo**.

El objetivo principal fue transformar un dataset transaccional crudo con problemas de calidad (duplicados, inconsistencias de formato y campos nulos) en una herramienta reproducible para la toma de decisiones estratégicas.

---

## 🖼️ Dashboard Interactivo

![Preview del Dashboard](assets/dashboard_preview.png)

---

## 🏗️ Arquitectura y Metodología de Trabajo

### 1. Limpieza y Preparación de Datos (ETL)
* **Estandarización:** Corrección de categorías de productos y nombres de regiones.
* **Tratamiento de Nulos:** Imputación de registros transaccionales sin cliente asignado.
* **Columnas Calculadas:** Clasificación de ventas mediante lógica condicional:
  ```excel
  =SI([@Cantidad]>=10; "Venta Alta"; "Venta Normal")
