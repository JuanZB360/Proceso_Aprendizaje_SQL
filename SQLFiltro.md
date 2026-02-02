# 🔍 FILTRANDO Y ORDENANDO DATOS

Para explicar todas las sentencias utilizaremos la siguiente tabla:

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 1  | Juan  | Pérez     | 28  | México    |
| 2  | Ana   | García    | 24  | España    |
| 3  | Juan  | Rodríguez | 35  | México    |
| 4  | Marta | López     | 19  | Argentina |

Aquí es donde comenzamos a interactuar verdaderamente con la base de datos especificando de qué manera queremos que nos traiga los datos. La sentencia principal aquí es `WHERE`.

---

## 🛠️ WHERE
Esta sentencia es la que nos permitirá filtrar la información; solo dejará pasar los datos que cumplan con una condición. Aquí entran en juego los operadores de comparación y lógicos.



### 📊 Operadores de comparación:
* **=**: Igual a.
* **!=** o **<>**: Diferente de.
* **>**: Mayor que.
* **<**: Menor que.
* **>=**: Mayor o igual.
* **<=**: Menor o igual.

Un ejemplo útil sería traer todos los registros donde la edad sea mayor a 25:

```sql
    SELECT * FROM users WHERE age = 25;
```

| id | name | lastName  | age | country |
|:---|:-----|:----------|:----|:--------|
| 1  | Juan | Pérez     | 28  | México  |
| 3  | Juan | Rodríguez | 35  | México  |

---

### 🧠 Operadores lógicos:



* **AND**: Se deben cumplir todas las condiciones.
* **OR**: Se debe cumplir al menos una condición.
* **NOT**: Invierte la condición (trae lo que no cumpla la regla).

Con los operadores lógicos podemos utilizar también los de comparación para permitir que la consulta evalúe más de una condición de búsqueda:

```sql
    -- Usuarios de 'España' que tienen más de 20 años
    SELECT * FROM users 
    WHERE country = 'España' AND age > 20;

    -- Usuarios que son de 'Argentina' O de 'Colombia'
    SELECT * FROM users 
    WHERE country = 'Argentina' OR country = 'Colombia';
```