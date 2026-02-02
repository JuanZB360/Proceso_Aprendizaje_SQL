* [**🏠 Volver a Menú de Aprendizaje Consultas SQL**](./SQLSelect.md)

---

# 🔗 RELACIONES (JOINs)

En una base de datos, la información suele estar distribuida en múltiples tablas. Para realizar consultas integrales, necesitamos acceder y combinar datos de estas tablas mediante la sentencia `JOIN`. Estas relaciones son posibles gracias al uso de las **claves foráneas (Foreign Keys)**.

---

### 📂 Tabla: `categorias` (Tabla Maestra)
| id_categoria | nombre_categoria |
| :----------- | :--------------- |
| 1            | Electrónica      |
| 2            | Oficina          |
| 3            | Hogar            |
| 4            | Gaming           |
| 5            | Aseo             |


### 📦 Tabla: `productos` (Tabla con Llave Foránea)
| id_producto | nombre_producto   | precio | stock | fk_categoria |
| :---------- | :---------------- | :----- | :---- | :----------- |
| 1           | Laptop Pro        | 1200   | 15    | 1            |
| 2           | Mouse Óptico      | 25     | 50    | 1            |
| 3           | Silla Ergonómica  | 150    | 8     | 2            |
| 4           | Escritorio Madera | 300    | 5     | 2            |
| 5           | Lámpara LED       | 45     | 30    | 3            |
| 6           | Monitor 144hz     | 400    | 12    | 4            |
| 7           | Teclado RGB       | 100    | 20    | NULL         |

---

## 🔄 INNER JOIN ... ON

Es el tipo de unión más común. Nos permite traer todos los registros en los que existe una coincidencia exacta entre ambas tablas. Si un registro de la **Tabla A** no está conectado (no tiene una clave foránea válida) con la **Tabla B**, ese registro **no se mostrará** en el resultado final.



> [!TIP]
> **Nota:** Aquí es donde el uso de los **alias** cobra vida, ya que ayudan a simplificar las consultas cuando los nombres de las tablas son muy extensos.

### Componentes clave:
* **`INNER JOIN`**: Es el complemento del `FROM`. Mientras que en el `FROM` definimos la tabla principal, con el `INNER JOIN` indicamos la tabla secundaria con la que deseamos relacionarla.
* **`ON`**: Es la cláusula donde definimos la condición de igualdad. Establecemos qué valores deben coincidir para que la relación se cumpla.
    * *Ejemplo:* La clave primaria de la tabla `categorias` debe ser igual a la clave foránea `fk_categoria` en la tabla `productos`.

### Ejemplo Práctico:
```sql
    SELECT p.nombre_producto, p.precio, c.nombre_categoria 
    FROM productos AS p
    INNER JOIN categorias AS c
    ON c.id_categoria = p.fk_categoria;
    -- aqui estamos pidiendo todos los registros en donde estan relacionadas las claves primarias y foraneas de cotegorias.
```

| p.nombre_producto   | p.precio | c.nombre_categoria |
| :------------------ | :-----   | :----------------- |
| Laptop Pro          | 1200     |     Electrónica    |
| Mouse Óptico        | 25       |     Electrónica    |
| Silla Ergonómica    | 150      |       Oficina      |
| Escritorio Madera   | 300      |       Oficina      |
| Lámpara LED         | 45       |        Hogar       |
| Monitor 144hz       | 400      |       Gaming       |

- en la respuesta el unico registro que no aparece es en donde la clave foranea de categorias en la tabla productos es 'NULL'.

---

## 🔄 TIPOS DE JOIN

Existen varios tipos de `JOIN` que nos permiten realizar consultas complejas entre tablas relacionadas. La diferencia principal radica en cómo manejan los datos que **no** tienen una coincidencia exacta en ambas tablas.

---

### ⬅️ LEFT JOIN ... ON

A diferencia del `INNER JOIN`, esta sentencia devuelve **todos** los registros de la tabla principal (la que declaramos en el `FROM`), independientemente de si existe una relación en la tabla secundaria. En los casos donde no hay coincidencia, SQL rellena los campos de la tabla relacionada con el valor `NULL`.



La estructura sintáctica es idéntica a la del `INNER JOIN`, pero su comportamiento lógico es más inclusivo.

### Ejemplo Práctico:
```sql
    SELECT p.nombre_producto, p.precio, c.nombre_categoria 
    FROM productos AS p   -- tabla izquierda (principal)
    LEFT JOIN categorias AS c  -- tabla derecha relacionada
    ON c.id_categoria = p.fk_categoria;
    -- aqui estamos pidiendo todos los registros de la tabla productos sin importar si estan relacionadas las claves primarias y foraneas de cotegorias.
```

| p.nombre_producto   | p.precio | c.nombre_categoria |
| :------------------ | :-----   | :----------------- |
| Laptop Pro          | 1200     |     Electrónica    |
| Mouse Óptico        | 25       |     Electrónica    |
| Silla Ergonómica    | 150      |       Oficina      |
| Escritorio Madera   | 300      |       Oficina      |
| Lámpara LED         | 45       |        Hogar       |
| Monitor 144hz       | 400      |       Gaming       |
| Teclado RGB         | 100      |        NULL        |

> [!NOTE]
> **Punto clave:** Al utilizar `LEFT JOIN`, garantizamos que no se pierda ningún registro de nuestra tabla base (`productos`). En la columna de la relación (`nombre_categoria`), el valor `NULL` indica que no se encontró una coincidencia en la tabla de categorías para ese ítem específico.

---

### ➡️ RIGHT JOIN ... ON
A diferencia del `LEFT JOIN`, esta sentencia prioriza la tabla de la derecha (la tabla relacionada que se menciona después del `JOIN`). Permite mostrar todos los registros de la tabla derecha, incluso si no tienen una relación correspondiente en la tabla izquierda (`FROM`). En esos casos, las columnas pertenecientes a la tabla principal mostrarán el valor `NULL`.

### Ejemplo Práctico:
```sql
    SELECT p.nombre_producto, p.precio, c.nombre_categoria 
    FROM productos AS p   -- tabla izquierda (principal)
    RIGHT JOIN categorias AS c  -- tabla derecha relacionada
    ON c.id_categoria = p.fk_categoria;
    -- aqui estamos pidiendo todos los registros de la tabla categoria en que estan relacionadas las claves primarias y foraneas, pero si hay algun registro de la tabla categorias que no esta relacionada con ningun producto esta aparecera en la respuesta con los valores de producto en 'NULL'.
```

| p.nombre_producto   | p.precio | c.nombre_categoria |
| :------------------ | :-----   | :----------------- |
| Laptop Pro          | 1200     |     Electrónica    |
| Mouse Óptico        | 25       |     Electrónica    |
| Silla Ergonómica    | 150      |       Oficina      |
| Escritorio Madera   | 300      |       Oficina      |
| Lámpara LED         | 45       |        Hogar       |
| Monitor 144hz       | 400      |       Gaming       |
| NULL                | NUL      |        Aseo        |

---

> [!IMPORTANT]
> **Nota técnica:** En una sola consulta podemos utilizar tantos `JOIN` como sean necesarios para relacionar múltiples tablas. No hay un límite estricto, siempre que exista una columna lógica que sirva de puente (clave primaria y foránea) entre ellas.



### Ejemplo de encadenamiento:
```sql
    SELECT 
        p.nombre_producto, 
        c.nombre_categoria, 
        prov.nombre_proveedor
    FROM productos AS p
    INNER JOIN categorias AS c ON p.fk_categoria = c.id_categoria
    INNER JOIN proveedores AS prov ON p.fk_proveedor = prov.id_proveedor;
```

---

* [**🏠 Volver a Menú de Aprendizaje Consultas SQL**](./SQLSelect.md)