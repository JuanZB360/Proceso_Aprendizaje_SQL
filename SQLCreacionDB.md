* [**🏠 Volver a estructura de mi aprendizaje**](./README.md)

---

# SENTENCIAS SQL

## 🏗️ CREACION DE BASE DE DATOS
para comenzar prime hay que crear la base de datos, para esto utilizamos la sentencia:

    ``` sql
    -- Forma básica
    CREATE DATABASE nombre_base_datos;

    -- Forma segura (evita errores si ya existe)
    CREATE DATABASE IF NOT EXISTS nombre_base_datos;
    ```

- En la mayoría de los sistemas, los nombres de las bases de datos no deben contener espacios. Se recomienda usar snake_case (ej. tienda_online).

## BORRAR UNA BASE DE DATOS
Para eliminar una base de datos por completo usamos la sentencia:

    ``` sql
    -- Borrado radical
    DROP DATABASE nombre_de_tu_base;

    -- Forma segura (evita errores si la base no existe)
    DROP DATABASE IF EXISTS mi_proyecto_db;
    ```


## UTILIZAR LA BASE DE DATOS
Para comenzar a usar la base de datos y crear sus tablas y realizar consultas debemos seleccionarla, para esto usamos la sentencia:

    ```sql
    USE nombre-base-datos;
    ```
---

* [**🏠 Volver a estructura de mi aprendizaje**](./README.md)