* [**🏠 Volver a estructura de mi aprendizaje**](./README.md)

---

# REALIZACION DE CRUD EN SQL
Ahora que sabemos como crear la base de datos y las tablas es hora de insertar, actualizar, borrar y traer informacion de la base de datos.

## INSERT (Crear registros)
Es cómo metes información dentro de las tablas que ya creaste. Aprenderás a insertar una sola fila o muchas a la vez y verás qué pasa cuando intentas insertar algo que rompe tus reglas (como un CHECK o un UNIQUE).

Esta la forma de poblar tu tabla. Existen dos formas principales:

- Insertar especificando columnas (Recomendado)
Es la forma más segura porque no dependes del orden físico de la tabla.

```sql
    INSERT INTO users (name, lastName, age) 
    VALUES ('Juan', 'Pérez', 28);
```

- Insertar múltiples registros a la vez
Esto es mucho más eficiente que hacer muchos inserts por separado.

```sql
    INSERT INTO users (name, lastName, age) VALUES 
    ('Ana', 'García', 24),
    ('Luis', 'Rodríguez', 35),
    ('Marta', 'López', 19);
```

## SELECT (Consultar datos)
Aquí es donde extraes la información.

- Traer todo

```sql
    SELECT * FROM users;
```

## UPDATE (Actualizar datos)
Para cambiar información existente. 
- Regla de oro: Siempre usa un WHERE.

- La sintaxis siempre sigue este orden:

```sql
    UPDATE nombre_tabla
    SET columna1 = valor1, columna2 = valor2
    WHERE condicion;
```

- UPDATE: la tabla en la que realizaras los cambios.

- SET: Aquí indicas qué columnas quieres cambiar y qué nuevos valores tendrán.

- WHERE: Es el filtro. Indica a quién exactamente vas a cambiar.

actualizar una columna

```sql
    UPDATE users
    SET age = 29
    WHERE id = 1;
```

Actualizar varias columnas a la vez

```sql
    UPDATE users
    SET lastName = 'García de Mendoza', age = 25
    WHERE id = 2;
```

## DELETE (Borrar datos)
Para eliminar filas de la tabla.

- Borrar a un usuario por su ID

```sql
    DELETE FROM users 
    WHERE id = 4;
```

Explicación: * Al igual que con el Update, el WHERE define el objetivo. Si pones solo DELETE FROM users;, vaciarás la tabla por completo.

---

* [**🏠 Volver a estructura de mi aprendizaje**](./README.md)