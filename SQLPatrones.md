# BUSQUEDA DE PATRONES

Para explicar todas las sentencias utilizaremos la siguiente tabla:

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 1  | Juan  | Pérez     | 28  | México    |
| 2  | Ana   | García    | 24  | España    |
| 3  | Juan  | Rodríguez | 35  | México    |
| 4  | Marta | López     | 19  | Argentina |

---

La búsqueda de patrones sirve para realizar consultas donde el registro de una columna contenga una línea de caracteres específicos. Para esto utilizamos dos sentencias: `LIKE` (donde coincida con una cadena específica) y `NOT LIKE` (donde **no** coincida con una cadena específica).

---

## 🛠️ LIKE
Permite comparar cadenas; si estas coinciden con el patrón, pasan la condición y se envían a la respuesta de la consulta.

Para traer todos los registros donde el nombre del usuario sea igual a una cadena de texto específica:


```sql
SELECT * FROM users WHERE name LIKE 'Ana';
-- Trae todos los registros que tienen estrictamente la cadena "Ana" y la longitud de 3.
```

**El resultado sería:**
| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 2  | Ana   | García    | 24  | España    |


### 🔍 Búsqueda de patrones con Comodines (`%`)

Para buscar cadenas de texto que coincidan con un patrón sin que sea una búsqueda exacta o **estricta**, utilizamos el símbolo `%`.


#### 1. Comienzo específico
Buscar una cadena que inicie con un carácter o caracteres en específico sin importar cuántos caracteres hay después ni la longitud total de la cadena:

```sql
    SELECT * FROM users WHERE name LIKE 'J%';
    -- Esto traerá todos los nombres que comiencen con la letra "J", sin importar los caracteres posteriores ni la longitud del texto.
```

**El resultado sería:**

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 1  | Juan  | Pérez     | 28  | México    |
| 3  | Juan  | Rodríguez | 35  | México    |


#### 2. Final específico
Buscar una cadena que termine con un carácter o caracteres en específico, sin importar cuántos caracteres hay antes ni la longitud total de la cadena:

```sql
    SELECT * FROM users WHERE name LIKE '%a';
    -- Esto traera todos los nombres que terminen con la letra a sin importar que caracteres hay antes ni la longitud de la cadena de texto.
```
**El resultado sería:**

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 2  | Ana   | García    | 24  | España    |
| 4  | Marta | López     | 19  | Argentina |


#### 3. Contenido específico
Buscar una cadena que contenga un carácter o caracteres en específico sin importar cuántos caracteres hay antes o después:

```sql
    SELECT * FROM users WHERE name LIKE '%a%';
    -- Esto traerá todos los nombres que contengan la letra 'a' sin importar qué caracteres hay antes o después, ni la longitud de la cadena de texto.
```

**El resultado sería:**

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 1  | Juan  | Pérez     | 28  | México    |
| 2  | Ana   | García    | 24  | España    |
| 3  | Juan  | Rodríguez | 35  | México    |
| 4  | Marta | López     | 19  | Argentina |


#### 4. Longitud y Contenido específico
    
Para consultar una cadena de texto que contenga uno o varios caracteres, pero especificando la longitud total de la cadena, debemos usar un guion bajo `_` por cada carácter. Por ejemplo, si es una palabra de 5 caracteres, usamos 5 guiones bajos `'_____'`:


```sql
SELECT * FROM users WHERE name LIKE 'M____a';
-- Esto traerá todos los nombres que comiencen con la letra 'M', seguida de 4 caracteres más (para esto usamos '_') y que terminen con la letra 'a'.
```

**El resultado sería:**

| id | name  | lastName  | age | country   |
|:---|:------|:----------|:----|:----------|
| 4  | Marta | López     | 19  | Argentina |