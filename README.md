# RFM Retail Farmatodo

## Tabla de Contenidos

- [Contexto del Proyecto](#contexto-del-proyecto)
- [Resumen Ejecutivo](#resumen-para-stakeholders)
- [Principales Hallazgos](#principales-hallazgos)
- [Recomendaciones](#recomendaciones)
- [Apéndice Técnico](#apéndice-técnico)
- [Supuestos y Consideraciones](#supuestos-y-consideraciones)

## Contexto del Proyecto 

Farmatodo es una de las principales cadenas de retail farmacéutico y de conveniencia en Latinoamérica, con un modelo omnicanal que combina tiendas físicas y ventas en línea.  
En un mercado altamente competitivo, entender el comportamiento de compra de sus clientes (tanto en frecuencia como en gasto) es clave para diseñar campañas de retención y optimizar el ticket promedio.



## Apéndice Técnico

1. **Origen de los datos**

    - Una porcion de la totalidad de los datos fueron extraidos manualmente del sitio web de Farmatodo.
    - Se creo la tabla de Excel de clientes con datos 100% simulados.
    - Creacion de la tabla de productos con datos 100% reales.
    - Tabla de ventas con datos basados en "fechas ancla" (temporadas) que garantizó que un porcentaje de las ventas siguieran un patrón más “realista” dentro de un conjunto totalmente simulado.
    - Para este proceso se utilizaron funciones logicas, como SI.CONJUNTO (con fechas anidadas) para la clasificacion tanto en la columna **origen** como en **segmentacion_demo**.
    - Para codigos y nombres se usaron funciones como ALEATORIO, ALEATORIO.ENTRE, &, UNIRCADENAS, ESPACIOS, entre otras.
    - Limpieza y estandarizacion de los datos (recortar espacios, UTF-8, etc).

2. **Creacion de la base datos y Carga archivos**

    - Se creo la base de datos en Postgresql y se conecto a Vscode para continuar con el flujo de trabajo desde ahi.
    - Estructura organizada del proyecto:
     - `/csv_files`: Archivos fuente.
     - `/sql_load`: Scripts para creación de tablas y carga inicial.
     - `/queries`: Consultas de análisis y métricas clave.
   - Carga y validación de datos mediante comandos `COPY`. puedes ver las consultas documentadas aqui `/queries`.

4. **Elaboracion de consultas RFM Y Definicion de cohortes**
    
   - Se elaboraron consultas SQL para asignar una cohorte mensual a cada cliente según su primera compra.
   - Se implementaron cálculos para verificar la retención a los 3 y 6 meses desde la cohorte inicial.
   - Todas las consultas están documentadas y disponibles en la carpeta `/queries` del repositorio.

5. **Exportacion a Excel y Analisis exploratorio**

    - Exploracion preliminar de cohortes por medio de tablas dinamicas. 
    - Simulacion complementaria de promedios de retencion de los cohortes.

6. **Análisis y Visualización en Power Bi**

    - Importación de la tabla consolidada de cohortes.
    - Creación de métricas en DAX, como retención promedio global y retención acumulada. (AVERAGE, CALCULATE, FILTER, ALLSELECTED)
    - Construcción del dashboard de retención por cohortes. (en proceso)

    

