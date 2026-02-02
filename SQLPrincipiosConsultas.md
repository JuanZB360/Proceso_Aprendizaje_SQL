* [**🏠 Volver a Menú de Aprendizaje Consultas SQL**](./SQLSelect.md)

---

# 🚀 PRINCIPIOS DE LAS CONSULTAS

Para explicar todas las sentencias utilizaremos la siguiente tabla:

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 1  | Juan  | Pérez     | 28  | México    |
| 2  | Ana   | García    | 24  | España    |
| 3  | Juan  | Rodríguez | 35  | México    |
| 4  | Marta | López     | 19  | Argentina |

---

Para realizar consultas en SQL debes respetar la estructura de las consultas para que el motor de base de datos pueda entender qué es lo que estás buscando.

La primera parte de una consulta y la más importante es:

* **"SELECT":** ¿Qué columnas quieres ver? En esta primera parte dices qué columnas quieres que te traiga como respuesta.
* **"FROM":** ¿De qué tabla vas a traer los datos? Aquí indicas en qué tabla realizarás la consulta.

```sql
    SELECT nombre, edad FROM usuarios; 
    -- trae los nombre y las edades de los registros de la tabla usuarios.
```

Esto nos dará como resultado:

| name  | age |
|:------|:----|
| Juan  | 28  |
| Ana   | 24  |
| Juan  | 35  |
| Marta | 19  |

---

> [!TIP]
> **Nota:** Para traer una tabla completa sin tener que escribir todas las columnas, utilizamos `*` en la consulta:

```sql
    SELECT * FROM usuarios; 
    -- trae todas las columnas de la tabla usuarios.
```

El resultado sería este:

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 1  | Juan  | Pérez     | 28  | México    |
| 2  | Ana   | García    | 24  | España    |
| 3  | Juan  | Rodríguez | 35  | México    |
| 4  | Marta | López     | 19  | Argentina |

---

#### 🏷️ ALIAS
Existen varias formas de utilizar un alias en SQL:

* Para que en la respuesta el nombre de la columna cambie, en el `SELECT` (donde decimos qué columnas de la tabla queremos traer) le asignamos un alias. Para esto usamos la sentencia `AS`:

```sql
    SELECT name AS name_users, age AS age_users FROM users;
``` 

Aquí al recibir el resultado con el nombre de columna que le asignamos en el alias:

| name_users | age_users |
|:-----------|:----------|
| Juan       | 28        |
| Ana        | 24        |
| Juan       | 35        |
| Marta      | 19        |

---

* Podemos utilizar **alias** para el nombre de la tabla; así podemos especificar de qué tabla proviene cada columna. Esto es muy útil cuando realizamos consultas más avanzadas:

```sql
    SELECT u.name, u.age FROM users AS u;
```

Aquí, dentro de nuestra consulta, el alias `u` representará la tabla **users**, y `u.name` se refiere a la columna **name** de la tabla **users**. Este sería el resultado de la consulta:

| name  | age |
|:------|:----|
| Juan  | 28  |
| Ana   | 24  |
| Juan  | 35  |
| Marta | 19  |

---

#### 👤 DISTINCT (Eliminar repetidos)
A veces quieres saber qué valores existen sin que se repitan. Si miras la tabla, hay dos "Juan"; si quisiéramos ver todos los nombres que existen en la tabla sin traer los nombres iguales, esta sentencia es la que deberías usar:

```sql
    SELECT DISTINCT name FROM users;
```
Esto traerá todos los nombres sin que hayan repetidos:

| name  |
|:------|
| Juan  |
| Ana   |
| Marta |

---

> [!NOTE]
> Como puedes observar, aunque en la tabla original existen dos registros con el nombre "Juan", la sentencia `DISTINCT` los agrupa para mostrar únicamente los valores únicos.

---

* [**🏠 Volver a Menú de Aprendizaje Consultas SQL**](./SQLSelect.md)