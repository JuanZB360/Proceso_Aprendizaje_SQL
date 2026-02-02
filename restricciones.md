* [**🏠 Volver a estructura de mi aprendizaje**](./README.md)

---

# 🛡️ Restricciones en Bases de Datos

Son reglas que limitan cómo pueden interactuar las entidades y las relaciones entre sí. Esto garantiza la integridad y coherencia de los datos.

---

## 🌐 Restricciones por dominio
Se refiere a las limitaciones sobre los valores que pueden tomar los atributos en una entidad. Permite que los datos sean válidos y consistentes.

### 📊 Tipos de datos
Cada atributo en la entidad tiene un tipo de dato asociado:
* **Enteros:** `INT`
* **Decimales:** `FLOAT`, `DOUBLE`
* **Cadenas:** `VARCHAR`
* **Texto:** `TEXT`
* **Fechas:** `DATE`
* **Hora:** `TIME`
* **Fecha y hora:** `DATETIME`, `TIMESTAMP`
* **Booleanos:** `BOOLEAN`

### 📏 Rango de valores 
Puedes especificar rangos de valores permitidos para ciertos atributos. 
* **Ejemplo:** Que una cadena no tenga más de 100 caracteres.
* **Ejemplo:** Que el ingreso solo puede ser entre 18 y 50 años.
* **Lista de valores permitidos:** Para atributos que solo pueden tomar valores específicos como una lista definida. (Ej. estado civil: casado, soltero, divorciado, etcétera).

### ✅ Expresiones de validación 
Utilizar funciones o expresiones para validar un valor y verificar que cumpla una condición.
* **Ejemplo:** Verificar un correo electrónico.

### ❗ Restricciones adicionales 
La obligatoriedad de un atributo que siempre debe tener un valor.

---

## 🏢 Restricciones por entidad 
Son las restricciones que se aplican a una entidad en particular.

* **Integridad de la entidad:** Asegura que los datos dentro de una entidad cumplen con unas condiciones o reglas. 
    * *Ejemplo:* Que una fecha de nacimiento no sea posterior a la fecha actual; que el precio de un producto esté en números positivos.
* **Unicidad:** Asegura que los valores de un atributo sean únicos.
    * *Ejemplo:* Como la cédula, que es única para cada persona.
* **Cardinalidad:** Define cuántas veces una instancia de una entidad puede relacionarse con instancia de otra entidad.
* **Participación:** Especifica si la existencia de una entidad depende de su participación en una relación específica.
    * *Ejemplo:* Relación uno a muchos empleado-departamento; cada departamento debe tener al menos un empleado para existir.
* **Negocio:** Está relacionada directamente al dominio o negocio al que se le desarrolla la base de datos.
    * *Ejemplo:* Que la cantidad de un producto en una tienda no sea nunca menor a cero.

---

## 🔗 Relación referencial 
Se refiere a las reglas que aseguran la coherencia y la integridad referencial entre entidades relacionadas.

* **Clave externa:** Es la referencia fundamental; es la clave foránea a través de la cual se llama la clave primaria de la entidad relacionada.
* **Restricción en cascada:** Es la automatización de datos de manera automática al generarse un cambio en la entidad principal.
    * *Ejemplo:* Si se actualiza un ID en la entidad principal, todas las claves foráneas que hacen referencia a ese ID se actualizarán. Si se elimina, todos los registros que estén relacionados se eliminarán.

---

* [**🏠 Volver a estructura de mi aprendizaje**](./README.md)