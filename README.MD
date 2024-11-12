# Desafío - Django y PostgreSQL Básico

## Descripción del Proyecto

Este proyecto consiste en la creación de un proyecto Django llamado **“desafiodb”** y una aplicación interna llamada **“testdb”**. El proyecto se conecta localmente a una base de datos PostgreSQL llamada **“adl-test”** y se ha configurado para incluir un modelo con una tabla que contiene los campos requeridos. Este ejercicio es fundamental para comprender cómo configurar un entorno Django desde cero y conectarlo a una base de datos PostgreSQL.

## Requerimientos del Proyecto

1. **Instalación y configuración de PostgreSQL**:
   - Instalación del motor de base de datos PostgreSQL en WSL Ubuntu.
   - Creación de la base de datos **“adl-test”** y configuración de un usuario con permisos.
   - Captura de pantalla de la asignación de permisos y la base de datos vacía.

2. **Configuración del proyecto Django**:
   - Creación del proyecto `desafiodb`.
   - Creación de la aplicación `testdb` dentro del proyecto.
   - Conexión de Django a la base de datos PostgreSQL mediante la configuración en `settings.py`.

3. **Modelado de la tabla**:
   - Definición de un modelo llamado `AdlTest` en `testdb/models.py` con los campos:
     - **campo1**: CharField con una longitud máxima de 100 caracteres.
     - **valor1**: IntegerField.

4. **Migraciones**:
   - Generación y aplicación de las migraciones para crear la tabla `adltest` en la base de datos.
   - Captura de pantalla que muestre la correcta ejecución de las migraciones.

5. **Verificación en pgAdmin**:
   - Captura de pantalla de `pgAdmin` mostrando la base de datos **“adl-test”** y la tabla `adltest` creada, junto con las tablas predeterminadas generadas por Django.

## Pasos Realizados

### 1. Configuración de PostgreSQL

- Instalación de PostgreSQL y creación de la base de datos mediante los comandos:
  ```bash
  sudo apt update
  sudo apt install postgresql postgresql-contrib
  
- Creación de la base de datos y asignación de permisos:
  ```bash
    CREATE DATABASE "adl-test";
    CREATE USER testuser WITH PASSWORD 'tu_password';
    GRANT ALL PRIVILEGES ON DATABASE "adl-test" TO testuser;

### 2. Configuración de Django
- Creación de un entorno virtual:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    
- Instalación de Django y psycopg2-binary:

    ```bash
    pip install django psycopg2-binary
    
- Creación del proyecto y la aplicación:
    ```bash
    django-admin startproject desafiodb
    cd desafiodb
    python manage.py startapp testdb
    
### 3. Configuración de settings.py

- Configuración de la base de datos PostgreSQL:
    ```bash
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': 'adl-test',
            'USER': 'testuser',
            'PASSWORD': 'tu_password',
            'HOST': 'localhost',
            'PORT': '5432',
        }
    }
    
### 4. Creación del modelo en testdb/models.py
    
    from django.db import models
    
    class AdlTest(models.Model):
        campo1 = models.CharField(max_length=100)
        valor1 = models.IntegerField()
    
        def __str__(self):
            return self.campo1


### 5. Migraciones
- Generación y aplicación de las migraciones:
    ```bash
    python manage.py makemigrations testdb
    python manage.py migrate

### 6. Verificación
- Capturas de pantalla de la terminal mostrando la correcta ejecución de las migraciones.
- Captura de DBeaver mostrando la base de datos “adl-test” con la tabla adltest y otras tablas generadas por Django.

![Preview Result.](/prints/image.png "Preview Result")