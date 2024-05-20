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
- Creamos un "crawler":
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/89b84d85-920a-4872-b871-0c5fb05a3840)
- Realizamos las siguientes configuraciones:
  - Elegimos un nombre
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/8ea44053-6cfa-40bd-8b36-6dd9b07eec8d)
  - Adicionamos una fuente de dato:
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/939258fc-aedc-4a3d-b63d-636985bdb896)
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/7f3370e1-e6b9-4ca0-a6ff-8bd51dd97621)
  - Seleccionamos el Bucket creado anteriormente:
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/cd883129-dcbb-4773-9c85-e2c3600a395d)
  - Seleccionamos "add an S3 data source"
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/27c5cd02-54b5-439b-8f52-48c4eccfe76c)
  - Seguimos con la configuracion:
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/7b7b4440-27b2-4afe-85e5-52a9e2f55f8a)
  - En la seccion del IAM Role, seleccionamos el "LabRole":
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/b7cd0d20-b44a-4e84-8994-c48ff2a7253c)
  - Para la siguiente seccion, vamos a crear una base de datos:
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/222d14c3-0942-4d51-99da-2ac5b85ef09d)
  - Seleccionamos un nombre para nuestra base de datos, y la creamos: 
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/c991ac47-6588-42c5-9a99-5a7b365ca1ac)
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/36790e08-5f71-4668-8efe-4f8ac21b4bdb)
  - volvemos a la pagina del crawler, y refrescamos las "target database" para poder seleccionar la base de datos que acabamos de crear: 
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/fcd24b3a-b555-4f4f-a1f1-7123b54ef0a9)
  - Dejamos el resto de las configuraciones por defecto y nos vamos al boton de "Next"
  - Dejamos el las ultimas configuraciones por defecto y damos clic en "Create crawler"
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/8737c76c-9efd-42fd-a022-e9557040506c)
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/cc90d90e-9797-49ab-86b5-a84e9104b1d9)
  - Al tener el crawler creado, procedemos a correrlo (esto puede tardar unos minutos): 
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/07f831d5-458c-42d5-9257-b9ae54bf778b)
  ![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/9227b4a9-e0e8-43da-a46b-ae456fd5417b)


- Mientras se ejecuta, realizaremos los siguientes pasos para ejecutar el servicio de Athena, que nos permite consultar datos en SQL. Primero, necesitamos crear un bucket y un directorio de trabajo. El bucket ya lo creamos en pasos anteriores, por lo que solo queda crear el directorio.
- Pasos:
- Entramos al Bucket:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/652ff9d3-12f7-47a5-9abd-2bb47414d7f9)
- Creamos una nueva carpeta:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/a63e78e6-79f7-49e2-9d28-86645329e370)
- Elegimos un nombre para la carpeta, en nustro caso la nombramos "athena", 
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/00247a5d-6252-40c9-ae5e-df4c10f73677)
- Confirmamos la creacion de la carpeta:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/4c154e7a-07f8-4785-867f-838218cebd32)
- Volvemos al crawler creado, y nos dirigimos a la base de datos:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/02b942c0-e7f4-4ca9-b25e-83704dbe3d86)
- Seleccionamos la base de datos que habiamos creado anteriormente: 
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/4ed31605-4c67-4f3c-ba02-52f2932b4461)
- Visualizamos las tablas que se crearon: 
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/6cc1285d-30ef-48e5-b0cc-b925cf8e180f)
- Ahora podemos entrar a cualquier tabla a visualizar los datos, por ejemplo vamos a ver la tabla de "hdi":
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/cdddd7a3-0ee5-4a3b-986b-4f5a970f0765)
- Observamos todos los atributos y columnas que tenemos en la seccion "Shema": 
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/eca603ea-dbe0-42e2-8ed2-34991b921613)
- NOTA: Podemos editar las columnas segun nuestra necesaidad.
- Tambien podemos observar las tablas creadas en el siguiente apartado: 
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/bdf13f50-36a6-4fa8-8512-6aa14617a088)
- Seleccionamos "export"
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/f4989073-87f3-45d3-8980-b695a1d7661a)
- Viusalizamos los esquemas creados:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/8c79d4a4-1c7f-4777-a896-a22a6c7d0e99)

- Para consultar via SQL las tablas creadas, esto lo podemos hacer con el servicio de AWS "Athena":
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/b39221c9-5e42-4d99-854b-104c6f704b65)
- Una vez estemos en el servicio de Athena, debemos configurar por una unica vez el Bucket y el archivo de salida de los datos:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/532a98d0-8990-4527-809f-6ee61248d90b)
- En esta seccion, nos preguntan a que directorio en Bucket vamos a enviar la salida, para esto vamos a realizar las siguientes configuraciones: 
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/be780013-ac68-4033-8f6c-4b693bf98e9c)
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/a5d5453f-22fd-4c5f-9908-9712d1cbe1ed)
- Seleccionamos el directorio "athena" que habiamos creado anteriormente:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/c76691c7-0b30-4313-909b-94c867d7102a)
- Damos clic en "Guardar"
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/541559e1-8122-45fa-abbc-26b8b5b60051)
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/1c93bec9-e714-4e1d-b19c-6a8dfb350733)
- Entramos al editor de consultas:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/da5d81ce-aee4-4690-a80a-e5193c57dc7e)
- Seleccionamos el origen de datos y la base de datos que hemos estado trabajando:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/d4003b40-c176-4744-af0f-0ec7e5908324)
- Realimos una consulta a una de las tablas:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/27a51f62-90c1-48ab-9a67-724fa8930019)
- Seleccionamos "vista previa de la tabla"
- Observamos como nos crea la sentencia SQL con el siguiente comando: 
```
SELECT * FROM "labsdb"."hdi" limit 10;
```
- Ejecutamos la sentencia:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/dcd60637-f48e-49f4-86fc-7c663a3db666)
- Al final podemos visualizar los diferentes datos de salida:
![image](https://github.com/migueflorez10/Laboratorio_3-2/assets/68928440/24105d2b-c35e-4427-a522-724c8dcfa1aa)
- NOTA: En este momento ya puedes realizar diferentes consultas teniendo en cuenta los datos que tenemos. 
- Laboratorio terminado


## Resultados Esperados
Se espera obtener un Data Warehouse funcional donde se puedan realizar consultas SQL a los datos almacenados en AWS S3. Se deben haber creado las bases de datos y tablas correspondientes en AWS Glue, y se deben haber realizado consultas exitosas con Athena que permitan extraer información relevante de los datos catalogados.

## Descripción del Ambiente de Desarrollo y Técnico
El ambiente de desarrollo utilizado es AWS, específicamente los servicios de S3, Glue y Athena. Se utilizan los datos proporcionados en GitHub, los cuales se ingieren manualmente a S3. Luego, se utilizan las funcionalidades de Glue para catalogar los datos y crear las tablas correspondientes en las bases de datos onudb y tickitdb. Finalmente, se utilizan las capacidades de consultas SQL de Athena para realizar análisis de los datos almacenados en el Data Warehouse.
