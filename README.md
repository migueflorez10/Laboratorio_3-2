### Info de la Materia: Topicos Especiales en Telematica-st0263

### Estudiante:
- Miguel Angel Martinez Florez, mamartinef@eafit.edu.co

### Profesor:  Edwin Nelson Montoya Munera, emontoya@eafit.edu.co  

# Laboratorio 3-2: IMPLEMENTACIÓN DE UN DATA WAREHOUSE SENCILLO CON AWS S3, GLUE y ATHENA.

##  Objetivo
El objetivo del laboratorio 3-2 es familiarizarse con los servicios de AWS S3, Glue y Athena para la implementación de un Data Warehouse sencillo. Se busca entender el proceso de ingestión de datos manual a S3, la catalogación de datos con Glue y la realización de consultas SQL con Athena.

## Descripción de la Actividad 
En la actividad se realiza la ingestión manual de datos a AWS S3 desde un conjunto de datos proporcionados en GitHub. Luego, se procede a catalogar los datos con AWS Glue, creando dos bases de datos (onudb y tickitdb) y las respectivas tablas. Por último, se realizan consultas SQL con AWS Athena a las tablas catalogadas para analizar los datos almacenados.

## Guia paso a paso 

## Resultados Esperados
Se espera obtener un Data Warehouse funcional donde se puedan realizar consultas SQL a los datos almacenados en AWS S3. Se deben haber creado las bases de datos y tablas correspondientes en AWS Glue, y se deben haber realizado consultas exitosas con Athena que permitan extraer información relevante de los datos catalogados.

## Descripción del Ambiente de Desarrollo y Técnico
El ambiente de desarrollo utilizado es AWS, específicamente los servicios de S3, Glue y Athena. Se utilizan los datos proporcionados en GitHub, los cuales se ingieren manualmente a S3. Luego, se utilizan las funcionalidades de Glue para catalogar los datos y crear las tablas correspondientes en las bases de datos onudb y tickitdb. Finalmente, se utilizan las capacidades de consultas SQL de Athena para realizar análisis de los datos almacenados en el Data Warehouse.
