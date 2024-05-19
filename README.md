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
- En AWS necesitamos buscar y acceder al servicio llamado "S3":
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/3781dcac-75aa-4c36-b62a-73d662f73ed6)
- Creamos un "Bucket"
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/5a914763-8883-4273-8227-f9db1acea29b)
- Realizamos las iguientes configuraciones para el "Bucket":
  - Elegimos un nombre para el Bucket
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/6175719a-acaf-478f-835c-95d7e264fb6b)
  - En propiedades de objetos, habilitamos los ACL:
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/a40b2445-dd18-4b21-8cd7-1c87f171800c)
  - Dejamos las propiedades de objetos por defecto
  - En "Configuración de bloqueo de acceso público para este bucket", desbloquemos el acceso publico: 
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/0bad75cb-7f27-48d5-bbf7-27f8169cf2a9)
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/9524a0fb-fc63-496f-b4f0-1ec820a0bdea)

  - Control de versiones (por defecto)
  - Etiquetas (por defecto)
  - Cifrado predeterminado (por defecto)
  - Hacemos clic en "crear bucket"
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/faee2d7c-9bdf-426a-8346-b7169df5577a)

- Ingresamos al Bucket creado:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/7fd4c945-445b-4698-adca-46c139376dcf)

- Vamos a subir los datos de catalogacion:
  - ¡Para encontrar la carpeta "datasets", tienes dos opciones!
    - Accede a este GitHub: https://github.com/st0263eafit/st0263-241.git y descarga directamente la carpeta "datasets".
    - La carpeta "datasets" también se encuentra dentro de los archivos del repositorio. Puedes explorarlos y descargarla desde allí.
  - Subir los archivos de los datasets onu y tickit al bucket.
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/6454eab0-f04c-4021-8b93-3e93e4bf38ea)
  - NOTA: Para la catalogación y el manejo de tablas en Athena, es importante que dentro de un mismo directorio se encuentren el mismo tipo de datos. En el caso de onu, se debe crear un directorio que represente cada tabla final y dentro de cada directorio colocar los archivos con los mismos tipos de datos. Esto mismo se aplica para tickitdb.
  - Cargamos los archivos:
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/c78da160-b6d4-4211-bdb9-8b80f67b07fa)
  - Subimos la carpeta onu:
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/b2c7d3c7-2eb6-48f0-b043-14d05060e444)
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/c1a3f3ff-4673-461a-a771-a766d62e95d7)

  - Seleccionamos la opcion cargar
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/e14c2031-a326-4a6f-83a4-ee945cfeebab)
  - En este momento los datos ya entan cargados en S3 y ya podemos proceder a catalogar los datos.

- Nos vamos nuevamente a la terminal de AWS, y buscamos el servicio "AWS Glue":
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/dfc0b100-3b90-4317-b543-64bb82a9f4d5)
- "AWS Glue" lo vamos a utilizar para poder crear y catalogar las tablas
- Cuando accedemos al servicio, dirigimos nuestra atención al panel izquierdo y seleccionamos la opción "Crawlers" que se encuentra en la sección "Data Catalog", con el fin de catalogar las tablas.
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/b842a1fc-a8b0-49a5-b15d-3ca04002a908)
- 








## Resultados Esperados
Se espera obtener un Data Warehouse funcional donde se puedan realizar consultas SQL a los datos almacenados en AWS S3. Se deben haber creado las bases de datos y tablas correspondientes en AWS Glue, y se deben haber realizado consultas exitosas con Athena que permitan extraer información relevante de los datos catalogados.

## Descripción del Ambiente de Desarrollo y Técnico
El ambiente de desarrollo utilizado es AWS, específicamente los servicios de S3, Glue y Athena. Se utilizan los datos proporcionados en GitHub, los cuales se ingieren manualmente a S3. Luego, se utilizan las funcionalidades de Glue para catalogar los datos y crear las tablas correspondientes en las bases de datos onudb y tickitdb. Finalmente, se utilizan las capacidades de consultas SQL de Athena para realizar análisis de los datos almacenados en el Data Warehouse.
