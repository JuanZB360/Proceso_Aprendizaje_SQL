# 📊 RANGOS Y LISTAS

Para explicar todas las sentencias utilizaremos la siguiente tabla:

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 1  | Juan  | Pérez     | 28  | México    |
| 2  | Ana   | García    | 24  | España    |
| 3  | Juan  | Rodríguez | 35  | México    |
| 4  | Marta | López     | 19  | Argentina |

---

#### 🔢 Rangos
Para hacer consultas de datos que esperamos que se encuentren en un rango determinado utilizamos la sentencia `BETWEEN`.

En lugar de escribir `age >= 18 AND age <= 30`, escribimos:

```sql
SELECT * FROM users WHERE age BETWEEN 18 AND 25;
```

Así la consulta nos trae todos los registros de los usuarios que tienen una edad entre 18 y 25 años:

| id | name  | lastName | age | country   |
|:---|:------|:---------|:----|:----------|
| 2  | Ana   | García   | 24  | España    |
| 4  | Marta | López    | 19  | Argentina |


#### 📋 Listas
Para hacer consultas donde queremos que los datos tengan valores en específico, utilizamos la sentencia `IN`.

En lugar de escribir una consulta como `country = 'México' OR country = 'España'`, escribimos:

```sql
    SELECT * FROM users WHERE country IN ('México','España');
```

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 1  | Juan  | Pérez     | 28  | México    |
| 2  | Ana   | García    | 24  | España    |
| 3  | Juan  | Rodríguez | 35  | México    |

En el caso de que deseemos traer los registros que **no** estén dentro de una lista de valores específicos, simplemente añadimos `NOT` a la sentencia `IN`, quedando como `NOT IN`.

En lugar de escribir una consulta como `country != 'México' AND country != 'España'`, escribimos:

```sql
    SELECT * FROM users WHERE country NOT IN ('México','España');
```

La respuesta seria:

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 4  | Marta | López     | 19  | Argentina |