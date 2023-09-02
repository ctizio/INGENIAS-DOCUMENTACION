# App FRUTAS
La funcionalidad principal de esta app es contar con una Base de Datos llamada Mongodb, donde se podrán consultar nombre, precios y tipos de frutas disponibles

## Requisitos funcionales:
Instalar:
#### Node Js: https://nodejs.org/es
#### Base de datos MongoDB Compass: https://www.mongodb.com/products/tools/compass

## Dependencias a instalar:
En terminal de Visual Code, ejecutar comando:
```
npm i 
```
```
npm i dotenv express mongodb nodemon
```
## Ejecución del proyecto:
En terminal de Visual Code, ejecutar comando:
```
 node server.js
```
## Extension de Visual Code a instalar:
Thunder Client es una extensión liviana y sencilla que sirve para simular llamadas a las API
![:](/images/image4.jpg)

## Consulta a Base de Datos
#### Paso 1
![Paso 1:](/images/image1.jpg)
#### Paso 2
![Paso 2:](/images/image2.jpg)
#### Paso 3
![Paso 3:](/images/image3.jpg)

## Resumen consulta a Base de Datos
| PETICION |  URL | DESCRIPCION |
|:--------:|-----|-------------|
|GET |[/frutas](/frutas)| Obtener todas las frutas| 
|GET |[/frutas/:id](/frutas)| Obtener todas las frutas por id| 
|GET |[/frutas/nombre/:nombre](/frutas)| Obtener frutas por nombre| 
|GET |[/frutas/precio/:precio](/frutas)| Obtener frutas por precio| 

## Diagrama de Flujo
```
Un codigo de mermaid js de un diagrama de flujo de una app que permite consultar en una base de datos (MongoDB), nombre, precios y tipos de frutas.
```
### Mermaid

```mermaid
graph TD
  A[Inicio] --> B[Instalación de MongoDB -driver oficial en Node.js]
  B-->C[Agregar la referencia al Driver mongodb y configurar  acceso al motor clúster MongoDB.]
  C-->D[Crear servidor Express]
  D --> E[Configurar puerto y middleware]
  E--> F[Configurar  conexión y desconexión al clúster de MongoDB]
  F --> G[Definir endpoint /frutas]
  F --> H[Definir endpoint /frutas/:id]
  F --> I[Definir endpoint /frutas/nombre/:nombre]
  F --> J[Definir endpoint /frutas/precio/:precio]

  
  G --> k[Retornar todo el contenido]
  H --> M[Aplicar filtro por id]
 I --> N[Aplicar filtro por nombre]
  J--> O[Aplicar filtro por precio]
  
 
```
## Diagrama de Secuencia
### Mermaid

```mermaid
sequenceDiagram
  participant Cliente
  participant Servidor Express

  Cliente->>+Servidor Express: Realizar solicitud GET /frutas
   Servidor Express->>+MongoDB: Conectar a Base de Datos
  Servidor Express->>+MongoDB: Leer datos de la BD
   Servidor Express->>MongoDB: Desconectar Base de Datos
  Servidor Express-->>-Cliente: Devolver respuesta con contenido de la BD frutas o mensaje de conexión no disponible

  Cliente->>+Servidor Express: Realizar solicitud GET /frutas/:id
  Servidor Express->>+MongoDB: Conectar a Base de Datos
  Servidor Express->>+MongoDB: Leer datos de la BD
  Servidor Express->>MongoDB: Aplicar filtro por id
  Servidor Express->>MongoDB: Desconectar Base de Datos
  Servidor Express-->>-Cliente: Devolver respuesta con resultados de búsqueda o mensaje de conexión no disponible

  Cliente->>+Servidor Express: Realizar solicitud GET frutas/nombre/:nombre
 Servidor Express->>+MongoDB: Conectar a Base de Datos
  Servidor Express->>+MongoDB: Leer datos de la BD
  Servidor Express->>MongoDB: Aplicar filtro por nombre
  Servidor Express->>MongoDB: Desconectar Base de Datos
  Servidor Express-->>-Cliente: Devolver respuesta con resultados de búsqueda o mensaje de conexión no disponible

  Cliente->>+Servidor Express: Realizar solicitud GET /frutas/precio/:precio
 Servidor Express->>+MongoDB: Conectar a Base de Datos
  Servidor Express->>+MongoDB: Leer datos de la BD
  Servidor Express->>MongoDB: Aplicar filtro por precio
  Servidor Express->>MongoDB: Desconectar Base de Datos
  Servidor Express-->>-Cliente: Devolver respuesta con resultados de búsqueda o mensaje de conexión no disponible


```
```
Este diagrama de secuencia representa las interacciones entre el cliente y el servidor Express para
cada uno de los endpoints mencionados en el flujo original. Cada solicitud del cliente al servidor
se procesa en el servidor Express y se devuelve una respuesta correspondiente al resultado de la consulta.
```