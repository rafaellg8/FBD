# Practica 1

Alteramos el usuario para cambiar la contraseña. Hacemos commit y generamos el fichero de salida.

`alter user x-login identified by "password";
commit;
SPOOL salida.txt off;
`
Creamos una tabla y mostramos su estructura

`Create table prueba2(
  cad1 char(8),
  num int);
  
  describe prueba2;
  `
Creacion de una tabla con PK, y demás atributos

`  CREATE TABLE plantilla(
dni char(8),
nombre varchar2(15),
estadocivil varchar(10)
CHECK (estadocivil IN ('soltero', 'casado', 'divorciado', 'viudo')),
fechaalta date,
PRIMARY KEY (dni));`

### Buscar la lista completa de los tipos de datos que ofrece Oracler (Data types).
Para ello debe consultarse el apartado correspondiente del manual de referencia de SQL de
Oracler [8].
Tipos de datos:
[https://docs.oracle.com/database/121/SQLRF/sql_elements001.htm#i45441](https://docs.oracle.com/database/121/SQLRF/sql_elements001.htm#i45441)


Creamos la tabla serjefe
`
CREATE TABLE serjefe(
dnijefe REFERENCES plantilla(dni),
dnitrabajador REFERENCES plantilla(dni),
PRIMARY KEY (dnitrabajador)
);
`

Tabla prueba1

`CREATE TABLE prueba1 (
cad char(3),
n int,
x float);
`

### Deduce el diagrama E/R que recoge la semántica de las tablas plantilla y
serjefe.

### Borrar la tabla prueba1 y comprobar las tablas que quedan.
`drop table prueba1;`

Mostramos todas las tablas:

` select * from user_tables; `

### Modifica el esquema de la tabla plantilla añadiendo un nuevo atributo llamado
fechabaja de tipo date.
alter table plantilla add fechabaja date;

==

Tabla proveedor, para ejecutar el archivo, guardamos el archivo como proveedor.sql, y ejecutamos @proveedor. Ojo el archivo debe estar en el mismo directorio de ejecución.
Hacemos lo mismo con la tabla proyecto, piezas y ventas.

### Comprobar que se ha cambiado correctamente el esquema de la tabla Ventas.
La descripción de la tabla debe contener los siguientes campos:

Añadimos el campo fecha:

`
alter table ventas add fecha date;
`

`
Nombre   Nulo     Tipo      
-------- -------- --------- 
CODPRO   NOT NULL CHAR(3)   
CODPIE   NOT NULL CHAR(3)   
CODPJ    NOT NULL CHAR(3)   
CANTIDAD          NUMBER(4) 
FECHA             DATE   
`

==

## INSERT

`
INSERT INTO prueba2 VALUES (’aa’,1);
INSERT INTO prueba2 VALUES(’Aa’,2);
INSERT INTO prueba2 VALUES (’aa’,1);
`

`INSERT INTO plantilla (dni,nombre,estadocivil,fechaalta)
VALUES ('12345678','Pepe','soltero', SYSDATE);
INSERT INTO plantilla (dni,nombre,estadocivil,fechaalta)
VALUES ('87654321','Juan', 'casado', SYSDATE);
INSERT INTO serjefe VALUES ('87654321','12345678');
INSERT INTO plantilla (dni, estadocivil) VALUES ('11223344','soltero');`

== 
## SELECT

### Ejecuta la sentencia SELECT para mostrar el contenido de las tablas PRUEBA2
y PLANTILLA. Intenta mostrar sólo algunos campos de las mismas.

`select dni from plantilla;

select cad1 from prueba2;`

### Ejecuta la sentencia UPDATE sobre la tabla plantilla y cambia el nombre del
trabajador con dni ’12345678’ a ’Luis’.
`update plantilla
set nombre = 'Luis'
where dni='12345678';`
