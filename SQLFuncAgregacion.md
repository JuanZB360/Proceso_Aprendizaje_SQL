# FUNCIONES DE AGREGACION
Aqui es donde no solo filtramos datos sino que tambien calculamos resultados permitiendo realizar dicersas operaciones.

> [!TIP]
> **Nota:** en este punto no usaremos GROUP BY esto lo utilizaremos mas adelante.

---

Para explicar todas las sentencias utilizaremos la siguiente tabla:

| id |  name   | price  | stock |
|:---|:--------|:-------|:------|
| 1  | bolso   | 20000  |  28   |
| 2  | gorra   | 15000  |  24   |
| 3  | cobija  | 25000  |  35   |
| 4  | bufanda | 30000  |  19   |

---

## Contar (COUNT)
Sirve para saber cuantos registros hay.
- COUNT(*): Cuenta todas las filas de la tabla sin importar si hay vacios.
- COUNT(columna): Cuenta todas las filas donde la columna no es null.

```sql
    SELECT COUNT(*) AS total_registros FROM users;
```

**El resultado sería:**

| total_registros |
|:----------------|
|       4         |

---

Podemos utilizar la la funcion 'COUNT' junto con 'WHERE' para contar filas que cumplan una condicion en especifico.

```sql
    SELECT COUNT(*) AS total_products FROM products 
    WHERE stock > 25;
    --Cuanta todos los registros donde el stock sea mayor a 25
```

**El resultado sería:**

| total_usuarios_juan |
|:--------------------|
|          2          |

---

## Sumar (SUM)
Nos permite sumar todos los valores de una columna numerica.

- SUM(age): suma todos los registros en la columna edad.

```sql
    SELECT SUM(price) AS suma_precios FROM users;
    --suma todos los precios de la tabla products.
```

**El resultado sería:**

| suma_precios |
|:-------------|
|    90000     |

- SUM(price * stock): tambien nos permite sumar la operacion de dos columnas en un registro.

Ej. multiplica el precio por la cantidad de un producto.

```sql
    SELECT SUM(price * stock) AS value_inventory FROM products;
    -- multiplica el precio y la cantidad de un producto y sumas todos los resultados de esta operacion en cada registro.
```

**El resultado sería:**

| total_usuarios_juan |
|:--------------------|
|      2365000        |

---

## Promedio (AVG)
esta funcion suma todos los valores numericos y los divide entre el numero de filas, dando como resultado el promedio, automaticamente.

Ej. promedio de los precios de los productos de la tienda.

```sql
    SELECT AVG(price) AS average_products FROM products;
    -- promedio de todos los precios de los productos de la tienda.
```

**El resultado sería:**

| average_products |
|:-----------------|
|      22000       |


#### Funciones que pueden complementar AVG()
- ROUND(AVG(price)): Busca el valor más cercano (puede subir o bajar).
- TRUNCATE(AVG(price)): Simplemente corta los decimales sin importar si el siguiente es un 9.
- FLOOR(AVG(price)): Siempre redondea hacia abajo al entero más cercano.

---

## Maximo y Minimo (MAX() y MIN())
busca el valo mas alto y el mas pequeño, funciona con fechas(MIN es la mas antigua) y texto(MIN es la que comienza con 'A')


```sql
    SELECT MAX(price) AS max_price, MIN(price) AS min_price FROM products;
    --el resultado sera el precio mas alto y mas bajo de la tabla productos.
```

|  max_price   | min_price  |
|:-------------|:-----------|
|    30000     |   15000    |