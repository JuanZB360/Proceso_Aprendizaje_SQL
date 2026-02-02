* [**🏠 Volver a Menú de Aprendizaje Consultas SQL**](./SQLSelect.md)

---

# 📦 AGRUPACIÓN

Esto nos permitirá sacar el mayor provecho de las funciones de agregación, ya que nos permite dividir toda la información en grupos y realizar cálculos sobre ellos.

---

Para explicar todas las sentencias utilizaremos la siguiente tabla (**products**):

| id | name             | category    | price | stock |
|:---|:-----------------|:------------|:------|:------|
| 1  | Laptop Pro       | Electrónica | 1200  | 15    |
| 2  | Mouse Óptico     | Electrónica | 25    | 50    |
| 3  | Monitor 24"      | Electrónica | 200   | 10    |
| 4  | Silla Ergonómica | Oficina     | 150   | 8     |
| 5  | Teclado Mecánico | Electrónica | 80    | 20    |
| 6  | Escritorio Madera| Oficina     | 300   | 5     |
| 7  | Lámpara LED      | Hogar       | 45    | 30    |
| 8  | Cafetera         | Hogar       | 60    | 12    |

---

## 📂 GROUP BY

Se utiliza para agrupar filas que tienen los mismos valores en columnas específicas. Por ejemplo, agrupar todos los registros de la tabla productos por su **categoría** permitirá que las funciones de agregación operen sobre cada uno de los grupos de categorías de forma independiente.



> [!TIP]
> **Nota:** Cualquier columna que selecciones en el `SELECT` que no sea una función de agregación, **debe** estar incluida en el `GROUP BY`.

```sql
    SELECT category, ROUND(AVG(price)) AS average FROM products
    GROUP BY category;

    -- esta consulta reunira todos los productos por categoria, y mostrara el promedio de los precios por categoria.
```

**El resultado sería:**

| category    | average |
|:------------|:--------|
| Electrónica |   376   |
| Oficina     |   225   |
| Hogar       |   52    |


---

## ⚡ HAVING

Así como el `WHERE` acompaña al `SELECT` y nos permite filtrar los datos de una consulta, `HAVING` acompaña al `GROUP BY` para filtrar los datos de los grupos que hemos generado.



#### **La diferencia clave:**

* **`WHERE`**: Filtra filas individuales **antes** de agrupar. No puede usar funciones como `SUM` o `COUNT`.
* **`HAVING`**: Filtra grupos completos **después** de agrupar. Se usa específicamente con funciones de agregación.

```sql
    SELECT categoria, AVG(price) AS average
    FROM products
    WHERE stock > 0               -- 1. Filtra filas con stock
    GROUP BY categoria             -- 2. Agrupa por categoría
    HAVING AVG(price) > 100        -- 3. Filtra grupos por promedio
    ORDER BY promedio DESC;        -- 4. Ordena de mayor a menor
```

**El resultado sería:**

| category    | average |
|:------------|:--------|
| Electrónica |   376   |
| Oficina     |   225   |

---

* [**🏠 Volver a Menú de Aprendizaje Consultas SQL**](./SQLSelect.md)