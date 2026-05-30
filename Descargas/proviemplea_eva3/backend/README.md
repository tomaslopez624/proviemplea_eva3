# ProviEmplea - API REST y Documentación OpenAPI - EVA3

**Asignatura:** Desarrollo Backend - Evaluación Sumativa U3
**Integrantes:** - Tomás López Franulic

## Instrucciones de Despliegue
1. Clonar el repositorio.
2. Navegar a la carpeta `backend` y configurar el `.env` (credenciales por defecto de `docker-compose.yaml`).
3. Levantar contenedores: `docker compose up -d --build`
4. Instalar dependencias: `docker compose exec app composer install`
5. Ejecutar migraciones: `docker compose exec app php artisan migrate`

## Swagger UI
El archivo `swagger.yaml` se encuentra en la raíz del proyecto. Para visualizarlo de forma interactiva, el proyecto incluye un contenedor dedicado. -----> `http://localhost:8081`

Se redactó el contrato `swagger.yaml` detallando todos los endpoints CRUD para Personas, Empresas y el flujo de Administración (Contactos) segun las guias aportadas. Se levantó Swagger UI mediante Docker para probar interactivamente las respuestas exitosas (200, 201) y de error (404, 422).

### Tipos de Datos y Estructuras
El contrato YAML incluye `schemas` detallados con ejemplos de datos. Se hizo especial énfasis en la estructura `PersonaCVCiego`, la cual omite deliberadamente los datos de contacto y nombre para cumplir con el requerimiento de no discriminación. Se utilizaron formatos estrictos como `uuid` y arreglos JSON para las competencias.

### Generación de Cliente
Se generó el cliente SDK en PHP utilizando la imagen oficial de Docker:
`docker run --rm -v ${PWD}:/local swaggerapi/swagger-codegen-cli-v3 generate -i /local/swagger.yaml -l php -o /local/api-client-php`

- *Conflicto de UUID:* Durante las pruebas iniciales con el cliente generado, se identificó que las llaves foráneas en `contactos_solicitados` fallaban porque Eloquent esperaba IDs incrementales. Se corrigió forzando `$keyType = 'string'` y el trait `HasUuids` en los modelos de Laravel.
- *Orden de Migraciones:* Se corrigió el error `1824` de MySQL modificando el timestamp de la migración de contactos para que se ejecute estrictamente después de que las tablas referenciadas (`personas` y `empresas`) ya existieran.

###  Rate Limiting
Se implementaron las siguientes mejoras en el código PHP, documentadas debidamente en la sección `info` del Swagger:
- **Rate Limiting:** Se aplicó el middleware `throttle:api` globalmente en `routes/api.php` limitando las peticiones a 60 por minuto por IP para mitigar ataques DDoS.
- **Caché de Consultas:** Se implementó `Cache::remember` en `AdministracionController@estadisticas` con un TTL de 5 minutos (300 segundos). Esto evita el recálculo en tiempo real de los conteos masivos en la base de datos, mejorando drásticamente el tiempo de respuesta del dashboard administrativo.
