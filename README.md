# Pipeline de Datos — Arquitectura Medallion en Azure

![Arquitectura](architecture.png)

## Descripción del proyecto

Este proyecto implementa un pipeline de datos end-to-end utilizando Azure Data Factory, Azure Databricks y arquitectura Medallion. El objetivo es integrar datos provenientes de múltiples fuentes, aplicar controles de calidad, enriquecer la información y generar tablas analíticas orientadas al análisis de negocio.

## Tecnologías utilizadas

- Azure Blob Storage — almacenamiento de archivos fuente y tablas Delta
- Azure Data Factory — orquestación del pipeline
- Azure Databricks — transformación y procesamiento distribuido
- Delta Lake — formato de almacenamiento transaccional
- PySpark — procesamiento distribuido de datos

## Arquitectura

El pipeline implementa una arquitectura Medallion:

| Capa | Descripción |
|------|-------------|
| 🟤 Bronze | Ingesta y almacenamiento inicial de datos |
| ⚪ Silver | Limpieza, validación y enriquecimiento |
| 🟡 Gold | Agregaciones y métricas analíticas |

## Estructura del repositorio

```text
pipeline_medallion_azure/
├── notebooks/
│   ├── 00_Generacion_Datasets.ipynb
│   ├── 01_Bronze_Ingesta.ipynb
│   ├── 02_Silver_Limpieza_Enriquecimiento.ipynb
│   └── 03_Gold_Agregaciones_KPIs.ipynb
├── data/
│   └── sample/
├── docs/
│   └── documento_funcional.md
├── architecture.png
└── README.md
```

## Validaciones implementadas

El notebook Silver implementa controles de calidad de datos:

1. Validación de productos existentes
2. Validación de cantidades vendidas
3. Detección de registros duplicados
4. Consolidación de registros rechazados
5. Creación de variables derivadas para análisis

## Resultados

### Ejecución del pipeline

![Pipeline](01_pipeline_ejecutado_correctamente.png)

### Trigger automático

![Trigger](02_trigger_diario.png)

### Notebooks desarrolladas

![Workspace](03_workspace_notebooks.png)

### Capa Bronze

![Bronze escritura](04_escritura_datasets_bronze.png)

![Bronze verificación](05_verificacion_storage_bronze.png)

### Capa Silver

![Rejected](06_silver_registros_rechazados.png)

![Segmentación](07_silver_columnas_derivadas_segmentacion.png)

![Calidad](08_silver_metricas_calidad.png)

### Capa Gold

![Gold segmento](09_gold_segmento_etario.png)

![Gold escritura](10_gold_escritura_delta.png)

![Gold verificación](11_gold_verificacion_storage.png)

![Visualización final](12_visualizacion_segmento_etario.png)

## Cómo configurar el proyecto

1. Clonar el repositorio
2. Crear contenedores en Azure Blob Storage
3. Reemplazar `TU_KEY_AQUI`, `TU_USUARIO_AQUI` y `TU_PASSWORD_AQUI`
4. Ejecutar notebooks en orden:

- 00_Generacion_Datasets
- 01_Bronze_Ingesta
- 02_Silver_Limpieza_Enriquecimiento
- 03_Gold_Agregaciones_KPIs

## Autor

**Javier Redital**

https://reditaljavier.com
