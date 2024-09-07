# Docker Compose Database Configurations

Este repositorio contiene configuraciones de Docker Compose para varias bases de datos populares y sus correspondientes herramientas de administración web. Estas configuraciones están diseñadas para facilitar la configuración y el despliegue rápido de entornos de desarrollo de bases de datos.

## Bases de datos incluidas

- MySQL con phpMyAdmin
- MariaDB con phpMyAdmin
- PostgreSQL con pgAdmin
- MongoDB con Mongo Express
- SQL Server con Azure Data Studio

## Requisitos previos

- Docker
- Docker Compose

## ¿Cómo usar?

1. Crea un archivo `.env` en el directorio raíz y define las variables de entorno necesarias. Por ejemplo:

```dotenv
# Variables genéricas
DB_PASSWORD=my_secure_password
DB_DATABASE=my_database
DB_USER=user

# Variables específicas

# Puertos para bases de datos
MYSQL_PORT=3306
MARIADB_PORT=3307
POSTGRES_PORT=5432
MONGODB_PORT=27017
SQLSERVER_PORT=1433

# Puertos para servicios web
PHPMYADMIN_MYSQL_PORT=8080
PHPMYADMIN_MARIADB_PORT=8081
PGADMIN_PORT=8081
MONGO_EXPRESS_PORT=8082
ADMINER_PORT=8083
AZURE_DATA_STUDIO_PORT=8084

POSTGRES_USER=${DB_USER}
MYSQL_USER=${DB_USER}
MONGO_INITDB_ROOT_USERNAME=${DB_USER}

PGADMIN_EMAIL=admin@example.com
PGADMIN_PASSWORD=admin_password

ACCEPT_EULA=Y
SA_PASSWORD=${DB_PASSWORD}
```

2. Navega al directorio de la base de datos que deseas utilizar:

```bash
cd mysql-phpmyadmin
```

3. Inicia un contenedor:

```bash
docker-compose -f mysql-phpmyadmin-compose.yml up -d
```

4. Iniciar multiples contenedores:

```bash
docker-compose -f mysql-phpmyadmin-compose.yml -f postgresql-pgadmin-compose.yml up -d
```

5. Para detener un contenedor:

```bash
docker-compose -f mysql-phpmyadmin-compose.yml down
```

6. Para detener multiples contenedores:

```bash
docker-compose -f mysql-phpmyadmin-compose.yml -f postgresql-pgadmin-compose.yml down
```

## Estructura del repositorio

```bash
.
├── docker-compose-db-readme.md
├── mariadb-phpmyadmin-compose.yml
├── mongodb-express-compose.yml
├── mysql-phpmyadmin-compose.yml
├── postgres-pgadmin-compose.yml
└── sqlserver-azuredatastudio-compose.yml
```

## Configuraciones

### MySQL y phpMyAdmin

- MySQL: `http://localhost:${MYSQL_PORT}` (por defecto 3306)
- phpMyAdmin para MySQL: `http://localhost:${PHPMYADMIN_MYSQL_PORT}` (por defecto 8080)

### MariaDB y phpMyAdmin

- MariaDB: `http://localhost:${MARIADB_PORT}` (por defecto 3307)
- phpMyAdmin para MariaDB: `http://localhost:${PHPMYADMIN_MARIADB_PORT}` (por defecto 8081)

### PostgreSQL y pgAdmin

- PostgreSQL: `http://localhost:${POSTGRES_PORT}` (por defecto 5432)
- pgAdmin: `http://localhost:${PGADMIN_PORT}` (por defecto 8081)

### MongoDB y Mongo Express

- MongoDB: `http://localhost:${MONGODB_PORT}` (por defecto 27017)
- Mongo Express: `http://localhost:${MONGO_EXPRESS_PORT}` (por defecto 8082)

### SQL Server

- SQL Server: `http://localhost:${SQLSERVER_PORT}` (por defecto 1433)

## Personalización

Puedes personalizar cada configuración editando el archivo `docker-compose.yml` correspondiente. Asegúrate de actualizar las variables de entorno en el archivo `.env` según sea necesario.

## Contribución

Las contribuciones son bienvenidas. Por favor, abre un issue o un pull request para sugerir cambios o mejoras.
