# API Flask - Adopción de Perros

API Rest construida con Python y Flask para gestionar un catálogo de perros disponibles para adopción. El proyecto utiliza MongoDB para almacenar la información de los perros y un sistema de cache en Redis para optimizar consultas frecuentes. El proyecto se ejecuta utilizando contenedores en Docker para el API, la base de datos MongoDB y la cache Redis, con volúmenes para la persistencia de datos y una red interna para la comunicación entre los contenedores.

## Características
- **CRUD completo:** Operaciones para crear, leer, actualizar, y borrar información de perros.
- **Filtros y búsquedas avanzadas:** Posibilidad de filtrar, buscar y ordenar perros por atributos como raza, edad, tamaño, etc.
- **MongoDB:** Base de datos NoSQL para almacenamiento eficiente y escalable.
- **Docker:** Contenedores Docker para la API, MongoDB y Redis.
- **Redis:** Sistema de cache para reducir la carga en la base de datos y optimizar el rendimiento en consultas frecuentes.
- **Swagger UI:** Documentación interactiva para probar los endpoints fácilmente.
  
## Requisitos previos
- Python 3.x
- Pip (instalador de paquetes de python)
- Docker y Docker Compose

## Estructura del proyecto

```bash
.
controllers/
  dog_controller.py      # Controlador que gestiona las peticiones HTTP
errors/
  error_handlers.py      # Manejador de errores personalizados
infrastructure/
  mongo.py               # Configuración y conexión a la base de datos MongoDB
  swagger.py             # Configuración para la documentación Swagger
models/
  dog_model.py           # Definición del modelo de datos para los perros
services/
  dog_service.py         # Lógica para manejar las operaciones sobre perros
static/
  swagger.json           # Archivo de especificación Swagger
app.py                   # Punto de entrada de la aplicación Flask
config.py                # Configuraciones de la aplicación para Mongo y Redis Cache
docker-compose.yml       # Archivo para configurar y ejecutar los contenedores Docker
Dockerfile               # Archivo para construir la imagen Docker de la API
requirements.txt         # Dependencias del proyecto
README.md                # Este archivo

```

## Instalación y ejecución

### 1. Clona el repositorio en la carpeta deseada

```bash
git clone https://github.com/EmmanuelMoscoso/dogs_adoption-restapi.git

cd dogs_adoption_restapi

```
### 2. Crear y activar un entorno virtual

**Windows**

```bash
python -m venv venv
source venv/Scripts/activate
```

**Mac y Linux**

```bash
python -m venv venv
source venv/bin/activate
````

### 3. Instalar dependencias
Si prefieres ejecutar el proyecto **FUERA** de Docker, de lo contrario, **ve al paso 4**

```bash
pip install -r requirements.txt
````

### 4. Ejecutar Docker Compose
Para levantar los servicios con Docker (API, MongoDB, Redis):

```bash
docker-compose up --build -d
````

### 5. Acceder a Swagger UI

La API estará disponible en http://localhost:5000/swagger, donde podrás probar los diferentes endpoints.

## USO

- **GET /dogs** = Obtener todos los perros
- **GET /dogs/{id}** = Obtener perro por ID
- **GET /dogs/search** = Obtener perros por filtros
- **POST /dogs** = Crear un nuevo perro
- **PUT /dogs/{id}** = Actualizar información completa de un perro
- **PATCH  /dogs/{id}** = Actualizar campos específicos por ID
- **PATCH /dogs/{id}/adopted** = Marcar un perro como adoptado
- **DELETE /dogs/{id}** = Borrar un perro por ID
