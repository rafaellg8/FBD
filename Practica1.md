#Practica 1

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

###Buscar la lista completa de los tipos de datos que ofrece Oracler (Data types).
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

###Deduce el diagrama E/R que recoge la semántica de las tablas plantilla y
serjefe.

###Borrar la tabla prueba1 y comprobar las tablas que quedan.
`drop table prueba1;`

Mostramos todas las tablas:

` select * from user_tables; `

