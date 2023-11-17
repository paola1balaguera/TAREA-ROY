# SQL en MySQL 🚀

## ¿Qué es SQL?

El lenguaje de consulta estructurada (SQL) es un lenguaje de programación para almacenar y procesar información en una base de datos relacional.

## Comandos SQL y Ejemplos 🎯

### CREAR BASES DE DATOS 

El comando para crear una base de datos es:

```sql
    CREATE DATABASE nombre_de_la_base_de_datos;
```
Ejemplo: 

```sql
    CREATE DATABASE MiBaseDeDatos;
```

### BORRAR BASE DE DATOS

```sql
    DROP DATABASE nombre_de_la_base_de_datos;
```
Ejemplo:

```sql
    DROP DATABASE MiBaseDeDatos;
```

### CREAR TABLAS

```sql
    CREATE TABLE nombre_de_la_tabla (
    columna1 tipo_de_dato,
    columna2 tipo_de_dato,
    ...
);
```

Ejemplo:

```sql
    CREATE TABLE Empleados (
    ID INT,
    Nombre VARCHAR(50),
    Edad INT,
    Salario DECIMAL(10, 2)
);
```

### BORRAR TABLAS

```sql
    DROP TABLE nombre_de_la_tabla;
```

Ejemplo:

```sql
    DROP TABLE Empleados;
```

### CREAR LLAVES PRIMARIAS

```sql
    ALTER TABLE nombre_de_la_tabla
    ADD CONSTRAINT nombre_constraint PRIMARY KEY (columna);
```
Ejemplo:
```sql
   ALTER TABLE Empleados
   ADD CONSTRAINT pk_empleados PRIMARY KEY (ID);
```

### CREAR LLAVES FORANEAS

```sql
    ALTER TABLE tabla_hija
    ADD CONSTRAINT nombre_constraint FOREIGN KEY (columna)
    REFERENCES tabla_padre(columna_referenciada);
```
Ejemplo: 

```sql
    ALTER TABLE Ventas
    ADD CONSTRAINT fk_ventas_empleados FOREIGN KEY (EmpleadoID)
    REFERENCES Empleados(ID);
```

### INSERTAR DATOS

```sql
    INSERT INTO nombre_de_la_tabla (columna1, columna2, ...)
    VALUES (valor1, valor2, ...);

```
Ejemplo:

```sql
    INSERT INTO Empleados (ID, Nombre, Edad, Salario)
    VALUES (1, 'Juan', 30, 50000.00);
```

### MODIFICAR DATOS

```sql
    UPDATE nombre_de_la_tabla
    SET columna = nuevo_valor
    WHERE condición;
```
Ejemplo:

```sql
    UPDATE Empleados
    SET Salario = 55000.00
    WHERE ID = 1;
```



### ElIMINAR DATOS

```sql
    DELETE FROM nombre_de_la_tabla
    WHERE condición;
```
Ejemplo:

```sql
    DELETE FROM Empleados
    WHERE ID = 1;
```

<br>
<br>

## INSTRUCCIONES EN LAS CONSULTAS DE DATOS📊

### CONSULTAR DATOS DE 1 TABLA: 

Para consultar datos de una sola tabla, se utiliza la instrucción `SELECT`. Ejemplo:

```sql
    SELECT * FROM nombre_de_la_tabla;
```
Ejemplo:

```sql
    SELECT * FROM Empleados;
```


### CONSULTAR DATOS EN MAS DE 1 TABLA: 

Para consultar datos en múltiples tablas, se emplea la cláusula JOIN. Esto permite combinar datos de tablas relacionadas. Por ejemplo:

```sql
    SELECT t1.columna1, t2.columna2
    FROM tabla1 t1
    JOIN tabla2 t2 ON t1.columna = t2.columna;
```
Ejemplo:

```sql
    SELECT Empleados.Nombre, Ventas.Monto
    FROM Empleados
    JOIN Ventas ON Empleados.ID = Ventas.EmpleadoID;
```

### CREAR TABLAS A PARTIR DE CONSULTAS

Se puede utilizar la instrucción CREATE TABLE junto con SELECT para crear una tabla a partir del resultado de una consulta. Por ejemplo:

```sql
    CREATE TABLE nueva_tabla AS
    SELECT columna1, columna2, ...
    FROM tabla_existente
    WHERE condición;
```
Ejemplo:

```sql
    CREATE TABLE EmpleadosJovenes AS
    SELECT *
    FROM Empleados
    WHERE Edad < 30;
``` 

### Revisar la estructura de una tabla

La estructura de una tabla se puede revisar utilizando el comando DESCRIBE o SHOW COLUMNS FROM. Por ejemplo:

```sql
    DESCRIBE nombre_de_la_tabla;
```
Ejemplo:
```sql
    DESCRIBE Empleados;
```

### ALIAS A UN CAMPO

Para dar alias a un campo en una consulta, se usa la palabra clave AS. Por ejemplo:

```sql
    SELECT columna AS alias
    FROM tabla;
```
Ejemplo:
```sql
    SELECT Nombre AS NombreEmpleado
    FROM Empleados;
```

### ALIAS A UNA TABLA

Para dar alias a una tabla en una consulta, se utiliza la palabra clave AS después del nombre de la tabla. Por ejemplo:

```sql
    SELECT t.columna1, t.columna2
    FROM tabla AS t;

```
Ejemplo:
```sql
    SELECT e.ID, e.Nombre
    FROM Empleados AS e;
```

<br>
<br>

## FUNCIONES DE CADENAS ⛓️

### CONCAT
El comando CONCAT se usa para concatenar dos o más cadenas en una sola:

```sql
    SELECT CONCAT(columna1, ' ', columna2) AS Concatenado
    FROM tabla;
```
Ejemplo:

```sql
    SELECT CONCAT('Hola', ' ', 'Mundo') AS Concatenado;
```

### SUBSTRING
SUBSTRING se emplea para extraer una parte específica de una cadena:

```sql
    SELECT SUBSTRING(columna, inicio, longitud) AS Subcadena
    FROM tabla;
```

### REPLACE
Para reemplazar una cadena, se utiliza la palabra reservada REPLACE:

```sql
    SELECT REPLACE(columna, 'valor_a_reemplazar', 'nuevo_valor') AS Reemplazado
    FROM tabla;
```
Ejemplo:

```sql
SELECT REPLACE('Hola Mundo', 'Mundo', 'Amigo') AS Reemplazado;
```


<br>
<br>

## FUNCIONES NUMERICAS 📠
SUM se usa para calcular la suma de los valores en una columna numérica:

### SUM

```sql
    SELECT SUM(columna) AS Total
    FROM tabla;
```
Ejemplo:

```sql
    SELECT SUM(Precio) AS Total FROM Productos;
```
### COUNT
COUNT cuenta el número de filas que cumplen con una condición especificada:

```sql
    SELECT COUNT(columna) AS Conteo
    FROM tabla;
```
Ejemplo:

```sql
    SELECT COUNT(*) AS TotalEmpleados FROM Empleados;
```
### MAX
MAX devuelve el valor máximo en una columna:

```sql
    SELECT MAX(columna) AS Maximo
    FROM tabla;
```
Ejemplo:

```sql
    SELECT MAX(Precio) AS PrecioMaximo FROM Productos;
```
### MIN
MIN devuelve el valor mínimo en una columna:

```sql
    SELECT MIN(columna) AS Minimo
    FROM tabla;
```
Ejemplo:

```sql
    SELECT MIN(Precio) AS PrecioMinimo FROM Productos;
```
### AVG
AVG se utiliza para calcular el promedio de valores en una columna numérica:

```sql
    SELECT AVG(columna) AS Promedio
    FROM tabla;
```
Ejemplo:

```sql
    SELECT AVG(Edad) AS EdadPromedio FROM Empleados;
```
<br>
<br>

## FUNCIONES DE FECHAS 📆

### DATEDIFF
DATEDIFF se usa para calcular la diferencia en días entre dos fechas:

```sql
    SELECT DATEDIFF(fecha1, fecha2) AS Diferencia
    FROM tabla;
```
Ejemplo:

```sql

```
### DAY
DAY extrae el día de una fecha:

```sql
    SELECT DAY(fecha) AS Dia
    FROM tabla;
```
Ejemplo:

```sql
    SELECT DATEDIFF('2023-11-16', '2023-11-10') AS DiferenciaDias;
```
### MONTH
MONTH extrae el mes de una fecha:

```sql
    SELECT MONTH(fecha) AS Mes
    FROM tabla;
```
Ejemplo:

```sql
    SELECT MONTH('2023-11-16') AS Mes;
```
### YEAR
YEAR extrae el año de una fecha: 
```sql
    SELECT YEAR(fecha) AS Año
    FROM tabla;
```
Ejemplo:

```sql
    SELECT YEAR('2023-11-16') AS Año;
```
### DATE_FORMAT
DATE_FORMAT se utiliza para formatear una fecha según un patrón específico:

```sql
    SELECT DATE_FORMAT(fecha, '%m-%d') AS FechaFormateada
    FROM tabla;
```
Ejemplo:

```sql
    SELECT DATE_FORMAT('2023-11-16', '%m-%d') AS FechaFormateada;
```