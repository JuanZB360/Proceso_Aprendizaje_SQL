# PRESENTACION DE LOS DATOS

Para explicar todas las sentencias utilizaremos la siguiente tabla:

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 1  | Juan  | Pérez     | 28  | México    |
| 2  | Ana   | García    | 24  | España    |
| 3  | Juan  | Rodríguez | 35  | México    |
| 4  | Marta | López     | 19  | Argentina |

---

Una vez realizada la consulta y filtrados los datos, podemos definir cómo presentar la información, ya sea organizándola bajo un **orden** determinado o **limitando** la cantidad de registros devueltos.

---

#### 1. Ordenar resultados (`ORDER BY`)
Para organizar los datos de manera ascendente (`ASC`) o descendente (`DESC`), utilizamos la sentencia `ORDER BY`.


```sql
    SELECT * FROM users ORDER BY age DESC;
    -- Ordena a los usuarios del mayor al más joven.
```

**El resultado sería:**

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 3  | Juan  | Rodríguez | 35  | México    |
| 1  | Juan  | Pérez     | 28  | México    |
| 2  | Ana   | García    | 24  | España    |
| 4  | Marta | López     | 19  | Argentina |

---

### 2. Limitar resultados (`LIMIT`)

Una vez que hemos filtrado y ordenado nuestros datos, podemos controlar la cantidad de registros que la base de datos nos devuelve utilizando la cláusula `LIMIT`.

Esta sentencia es especialmente útil cuando trabajamos con tablas que contienen miles de filas y solo necesitamos visualizar una pequeña muestra o las primeras posiciones de un ranking.


#### Ejemplo de uso:
Si queremos obtener únicamente los primeros 2 usuarios de nuestra tabla:


```sql
    SELECT * FROM users LIMIT 2;
    -- Esta consulta solo devolverá los dos primeros registros que coincidan con los criterios.
```


**El resultado sería:**

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 1  | Juan  | Pérez     | 28  | México    |
| 2  | Ana   | García    | 24  | España    |