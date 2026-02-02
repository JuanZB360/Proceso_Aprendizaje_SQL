* [**🏠 Volver a estructura de mi aprendizaje**](./README.md)

---

# 🔑 CLAVES Y RELACIONES EN SQL

---

## 🥇 CLAVE PRIMARIA (Primary key - PK)
Es el identificador único de cada fila en una tabla. Piensa en ella como el ADN o el número de documento de identidad: no puede haber dos iguales y nadie puede carecer de él.

* **Unicidad:** No se pueden repetir valores.
* **Obligatoriedad:** No puede ser NULL.
* **Inmutabilidad:** (Idealmente) No debería cambiar nunca.

```sql
    CREATE TABLE autores (
        autor_id INT PRIMARY KEY AUTO_INCREMENT, -- Esta es la PK
        nombre VARCHAR(100) NOT NULL
    );
```


# 🔗 CLAVE FORANEA (Foreign Key - FK)

Es una columna en una tabla que "apunta" a la **Clave Primaria** de otra tabla. Su función es crear un vínculo lógico y garantizar la **Integridad Referencial**.

> [!IMPORTANT]
> **Integridad Referencial:** Es la regla que impide que existan "hijos huérfanos". No puedes tener un libro de un autor que no existe en la tabla de autores.



### 📝 Ejemplo de Implementación:

```sql
CREATE TABLE libros (
    libro_id INT PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(200),
    autor_id INT, -- Esta columna será la conexión
    
    -- Definimos la relación
    CONSTRAINT fk_autor
    FOREIGN KEY (autor_id) 
    REFERENCES autores(autor_id)
);
```

* **CONSTRAINT fk_categoria:** Es el nombre de la regla (puedes ponerle el que quieras, pero `fk_` es el estándar).
* **FOREIGN KEY (categoria_id):** Indica qué columna de la tabla actual (productos) será el enlace.
* **REFERENCES categorias(id):** Indica a qué tabla y a qué columna apunta.



# ⚡ ACCIONES REFERENCIALES (El efecto Cascada)

¿Qué pasa si borras a un autor que tiene 10 libros escritos? Aquí es donde definimos el comportamiento del sistema mediante reglas. Las más usadas son:

---

### 🌊 ON DELETE CASCADE (En Cascada)
Si borras el registro "padre", automáticamente se borran todos los registros "hijos" asociados. Es útil para limpiar datos residuales.

* **Uso común:** Si borras una Cuenta de Usuario, se borran sus Configuraciones de perfil.

---

### 🕳️ ON DELETE SET NULL
Si borras el registro "padre", el campo en la tabla "hija" se pone en NULL. El hijo sobrevive, pero queda sin padre.

* **Uso común:** Si borras una Categoría, los Productos asociados se quedan "Sin categoría" pero no desaparecen.

---

### 🚫 ON DELETE RESTRICT (Por defecto)
No te permite borrar el registro "padre" mientras existan "hijos" conectados. SQL lanzará un error.

* **Uso común:** Evitar borrar un Cliente que tiene Facturas pendientes de pago.

```sql
    CREATE TABLE cursos (
        id INT PRIMARY KEY AUTO_INCREMENT,
        titulo VARCHAR(100)
    );
```

```sql
    -- Tabla Hija
    CREATE TABLE lecciones (
        id INT PRIMARY KEY AUTO_INCREMENT,
        titulo VARCHAR(100),
        curso_id INT,
        
        CONSTRAINT fk_curso_leccion
        FOREIGN KEY (curso_id) 
        REFERENCES cursos(id)
        ON DELETE CASCADE -- Si borro el curso, se borran sus lecciones automáticamente
    );
```

### 🔄 ON UPDATE CASCADE

El comando **ON UPDATE CASCADE** es el hermano del borrado en cascada, pero su función es mantener la sincronía cuando los identificadores (IDs) cambian.

Aunque en un mundo ideal las Claves Primarias (**PRIMARY KEY**) no deberían cambiar nunca, a veces sucede (por errores de captura, cambios en códigos de SKU o reestructuraciones). **ON UPDATE CASCADE** asegura que, si el ID del "padre" cambia, todos los "hijos" se actualicen automáticamente para no perder la conexión.

```sql
-- Tabla Padre
CREATE TABLE cursos (
    id INT PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(100)
);

-- Tabla Hija
CREATE TABLE lecciones (
    id INT PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(100),
    curso_id INT,
    
    CONSTRAINT fk_curso_leccion
    FOREIGN KEY (curso_id) 
    REFERENCES cursos(id)
    ON DELETE CASCADE -- Si borro el curso, se borran sus lecciones automáticamente
    ON UPDATE CASCADE  -- Si cambio el ID del curso, se actualiza en las lecciones
);
```

---

* [**🏠 Volver a estructura de mi aprendizaje**](./README.md)