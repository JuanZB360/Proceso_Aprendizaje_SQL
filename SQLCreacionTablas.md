# 🛠️ MANIPULACION DE TABLAS

---

## 🏗️ CREACION DE TABLAS
- Antes de crear, debemos saber qué materiales tenemos. Estos son los más comunes:

### 📊 Tipos de Datos Frecuentes: 
* **INT / INTEGER:** Números enteros.
* **DECIMAL(p,s) / NUMERIC:** Números con decimales exactos (ideal para dinero).
* **VARCHAR(n):** Texto variable con un límite de n caracteres.
* **TEXT:** Para textos largos (descripciones, artículos).
* **BOOLEAN:** Verdadero (TRUE) o Falso (FALSE).
* **DATE / TIMESTAMP:** Fechas y horas.

### 🛡️ Restricciones (Constraints)
* **PRIMARY KEY:** Identificador único (no se repite, no es nulo).
* **NOT NULL:** El campo es obligatorio.
* **UNIQUE:** No permite valores duplicados.
* **DEFAULT:** Asigna un valor si no se provee uno.
* **CHECK:** Valida una condición (ej: age > 18).
* **FOREIGN KEY:** Une una tabla con otra (integridad referencial).

- Para comenzar a crear nuestra base de datos debemos utilizar tipos de datos y restricciones para que la table este bien estructurada:

```sql
    CREATE TABLE productos (
        id INT PRIMARY KEY AUTO_INCREMENT UNIQUE, -- clave primaria con un valor unico y incrementa mienta su valor para cada registro Ej. 1, 2, 3, 4... 
        
        nombre VARCHAR(100) NOT NULL, -- atributo de cadena con unalongitud maxima de 100 caracteres
        
        descripcion TEXT,-- atributo de texto largo
        
        precio DECIMAL(10, 2) NOT NULL CHECK (precio > 0),-- valor decimal con una longitud maxima de 10 digitos y puede tener 2 numeros decimales, no puede ser nulo ni menor a 0
        
        stock INT DEFAULT 0, -- numero entero con un valor por defecto de 0
        
        fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP, -- dato de fecha y hora con el valor de la hora del registro por defecto
        
        sku VARCHAR(20) UNIQUE -- Código de barras único
    );
```

## ⚙️ MODIFICACION DE COLUMNAS EN UNA TABLA

### 🔄 Modificación de Tablas (ALTER)
A veces el diseño original cambia. Para eso usamos ALTER TABLE.

Agregar una columna

```sql
    ALTER TABLE productos ADD COLUMN color VARCHAR(30);
    Cambiar el tipo de dato o nombre de una columna
    Nota: La sintaxis varía un poco según el motor (MySQL usa MODIFY o CHANGE).
```


### 📝 Cambiar tipo de dato
Para modificar el tipo de dato de un atributo en una tabla.

```sql
    ALTER TABLE productos MODIFY COLUMN nombre VARCHAR(150);
```

### 🏷️ Renombrar una columna
para modificar el nombre de un atributo en una table.

```sql
    ALTER TABLE productos RENAME COLUMN descripcion TO detalle;
```

### 🗑️ Eliminar una columna
para eliminar una columna(atributo) en una tabla.

```sql
    ALTER TABLE productos DROP COLUMN color;
```

## ⚠️ VACIAR Y ELIMINAR TABLAS
Hay dos formas de "borrar", pero funcionan muy diferente:

- TRUNCATE: Borra todos los datos dentro de la tabla, pero mantiene la estructura (la tabla queda vacía como nueva). Es mucho más rápido que borrar fila por fila.

```sql
    TRUNCATE TABLE productos;
```

- DROP: Borra la tabla completa (datos y estructura). Desaparece de la base de datos.

```sql
    DROP TABLE IF EXISTS productos;
```

## 🔄 RENOMBRAR LA TABLA COMPLETA
Si decides que tu tabla debe llamarse de otra forma:

```sql
ALTER TABLE productos RENAME TO inventario_general;
```