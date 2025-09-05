# Proyecto TYPO3 con Docker

Este repositorio contiene la configuración mínima para levantar un entorno TYPO3 usando **Docker Compose**.

## 📂 Estructura del proyecto

```

proyecto-typo3/
├── app/
│   └── public/
│       └── index.php
├── docker-compose.yml
└── README.md

````

## 🚀 Cómo ejecutar el proyecto

1. Clonar este repositorio:
   ```bash
   git clone https://github.com/lucas29951/ejercicio-typo3
   cd ejercicio-typo3
2. Levantar los contenedores:
   ```bash
   docker compose up -d
3. Acceder a:
   * Sitio web: [http://localhost:8080](http://localhost:8080)

## 📥 Instalación de TYPO3

1. Entrar al contenedor web:

   ```bash
   docker exec -it typoweb bash
   cd /app
   ```

2. Instalar TYPO3 con Composer:

   ```bash
   composer create-project typo3/cms-base-distribution .
   ```

3. Dar permisos:

   ```bash
   chown -R www-data:www-data /app
   chmod -R 775 /app
   ```

4. Reiniciar contenedor:

   ```bash
   exit
   docker restart typoweb
   ```

5. Completar la instalación en [http://localhost:8080/typo3/](http://localhost:8080/typo3/).

## ⚙️ Variables de entorno (docker-compose.yml)

* `MARIADB_DATABASE=typo3` → Nombre de la base de datos
* `MARIADB_USER=typo3` → Usuario de la BD
* `MARIADB_PASSWORD=typopass` → Contraseña del usuario
* `MARIADB_ROOT_PASSWORD=rootpass` → Contraseña del root de la BD
* `WEB_DOCUMENT_ROOT=/app/public` → Carpeta raíz de TYPO3
* `TYPO3_DB_HOST=dbserv` → Host de la base de datos

---
