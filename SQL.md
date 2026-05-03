
* [**🏠 Volver a estructura de mi aprendizaje**](./README.md)

---

# 📔 SQL: Bitácora de Aprendizaje

En este documento llevaré una bitácora sobre todo mi proceso de aprendizaje en bases de datos con el lenguaje.

**SQL (Structured Query Language)** es un lenguaje estandarizado para gestionar y manipular bases de datos relacionales, permitiendo a los usuarios consultar, insertar, actualizar y eliminar datos de manera estructurada a través de comandos (como SELECT, INSERT, UPDATE, DELETE) en tablas organizadas por filas y columnas, siendo fundamental para aplicaciones y análisis de datos en casi cualquier sector.

---

## 🧐 ¿Qué es SQL?
SQL (Structured Query Language) es el lenguaje estándar diseñado para comunicarse con las **Bases de Datos Relacionales (RDBMS)**.

---

## 🏗️ Sistemas de Bases de Datos Relacionales (RDBMS)

### ✅ Ventajas:
* **Estructura tabular:** (tablas, filas y columnas).
* **Integridad de datos.**
* **Flexibilidad.**
* **Escalabilidad.**

### 🧩 Componentes:

#### 1. DDL (Data Definition Language)
**Lenguaje de Definición de Datos:** es el proceso de estructuración de la base de datos, en donde construimos todo el esquema en donde almacenaremos la información.

**Sentencias utilizadas:**
* `CREATE`: Para crear la base de datos y tablas.
* `ALTER`: Para modificar la estructura de las tablas (añadir o cambiar columnas).
* `DROP`: Para eliminar tablas o índices.

#### 2. DML (Data Manipulation Language)
**Lenguaje de Manipulación de Datos:** es el proceso mediante el cual manipulamos la información que almacenamos en la base de datos.

**Sentencias utilizadas:**
* `SELECT`: Esta sentencia se utiliza para realizar consultas sobre los datos.
* `INSERT`: Con esta instrucción podemos insertar los valores en una base de datos.
* `UPDATE`: Sirve para modificar los valores de uno o varios registros.
* `DELETE`: Se utiliza para eliminar las filas de una tabla.

#### 3. DQL (Data Query Language)
**Lenguaje de Consulta de Datos:** es el proceso mediante el cual podemos traer información de nuestra base de datos.

**Sentencia utilizada:**
* `SELECT`: Para hacer consultas utilizando condiciones.

---

## 💡 Conceptos Fundamentales

### ⚖️ Diferencia entre Datos e Información
* **Datos:** Hechos o cifras sin procesar.
* **Información:** Resultado de procesar y analizar los datos para obtener significado o contexto.

### 📂 Entidades
Representan **Objetos o Conceptos** importantes que necesitan ser definidos y gestionados. Son los cimientos sobre los cuales se construyen las bases de datos, permitiendo una organización clara y estructurada.

> **Ejemplo:** En un sistema de gestión de una biblioteca las entidades pueden incluir: *Libros, Usuarios y Préstamos.*

### 🏷️ Atributos
Son las propiedades o características de las entidades que describen sus detalles específicos.

> **Ejemplo:** Para una entidad **Libro**, los atributos podrían ser: *Título, Autor y fecha_Publicacion.*

| 📖 Libro |
| :--- |
| **Id** |
| **Título** |
| **Autor** |
| **fecha_Pub** |

---

## 🔑 Claves de Datos
* **Clave Primaria (PK):** Es un atributo que identifica de manera única cada registro en una tabla.
* **Clave Foránea (FK):** Es un campo en una tabla (tabla hija) que almacena el identificador de un registro en una tabla distinta (tabla padre), permitiendo conectar la información de manera estructurada.

---

## 🔗 Relaciones
Son asociaciones lógicas entre dos o más tablas que permiten conectar datos, organizarlos eficientemente y garantizar la integridad referencial. Se establecen utilizando **Claves Primarias (PK)** y **Claves Foráneas (FK)** para vincular información común, evitando redundancia y registros huérfanos.

> **Ejemplo:** En un sistema de gestión de biblioteca un usuario puede tener muchos préstamos y un préstamo está relacionado a un libro.
> 
> `| usuario | 1:M | prestamos | M:N | libros |`

**Importancia:** Las relaciones permiten definir cómo interactúan las entidades, facilitando consultas y operaciones complejas en la base de datos.

---

### 📊 Cardinalidad
Es la relación que puede existir entre dos tablas. Estas relaciones pueden ser:

#### 1. Uno a Uno (1:1)
Un registro en la entidad A está relacionado con un registro en la entidad B.
* **Ejemplo:** Una persona tiene solo un pasaporte / Un pasaporte pertenece solo a una persona.
* Es la menos común en bases de datos grandes.
* Útil para relaciones directas y exclusivas.
* No especifica cuál es la jerarquía en la relación (quién es la entidad fuerte y débil).

#### 2. Uno a Muchos (1:N)
Un registro de la entidad A se relaciona con muchos registros de la entidad B.
* **Ejemplo:** Un autor puede escribir muchos libros / Un libro solo tiene un autor.
* Es la más común en las bases de datos.
* Permite que una entidad principal (**amo**, la entidad A) esté vinculada a múltiples entidades secundarias (**esclavo**, la entidad B).

#### 3. Muchos a Muchos (M:N)
Muchos registros de una entidad A están relacionados a muchos registros de una entidad B.
* **Ejemplo:** Un estudiante puede inscribirse a muchos cursos / Un curso tiene muchos estudiantes.
* **Buena práctica:** Crear una **tabla intermedia** para relacionar dos tablas con esta cardinalidad.

---

* [**🏠 Volver a estructura de mi aprendizaje**](./README.md)