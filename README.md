# EquipoBases

--(ENRIQUE)
--(BRUCE)
```sql
-- --------------------------------------
CREATE TABLE minorista (
	id_minorista        INTEGER(10),
	clienteid_cliente   INTEGER(10)
);
-- --------------------------------------
CREATE TABLE miembros (
    id_miembro              INTEGER(10),
	nombre                  VARCHAR(30),
    app                     VARCHAR(30),
    apm                     VARCHAR(30),
    sexo                    VARCHAR(15),
    fecha_inicio            DATE,
	fecha_expiracion        DATE,
    minoristaid_minorista   INTEGER(10),
    cmembresianombre        VARCHAR(30)
);
-- --------------------------------------
CREATE TABLE cmembresia (
	nombre          VARCHAR(30),
	descripcion     VARCHAR(30),
    precio          REAL(10)
);

-- --------------------------------------
CREATE TABLE telefono_miembros (
	miembrosid_miembro      INTEGER(10),
	telefono                VARCHAR(15)
);


-- --------------------------------------
CREATE TABLE minorista_online (
	id_minorista_on       	INTEGER(10),
	nombre                  VARCHAR(30),
    app                     VARCHAR(30),
    apm                     VARCHAR(30),
    sexo                    VARCHAR(15),
    fecha_nac         		DATE,
--	id_tarjeta_registrada   INTEGER(20),
    clienteid_cliente   	INTEGER(10)
);

-- --------------------------------------
CREATE TABLE telefono_min (
	minorista_onlineid_minorista_on    INTEGER(10),
	telefono                		   VARCHAR(10)
);

```
--(DANI)
```sql
CREATE TABLE correo_min(
    minorista_onlineid_minorista_on serial,
    correo varchar(20)
);
CREATE TABLE dir_minorista(
    id_minorista_on serial
    numero integer(10)
    calle varchar(30)
    colonia varchar(20)
    delegacion varchar(20)
    cp integer(8)
);
CREATE TABLE tarjetas_registradas(
    minorista_onlineid_minorista_on serial
    tipo_de_tarjetaid_tipo_de_tarjeta integer(10)
    emisora_tarjetaid_emisora integer(10)
);
CREATE TABLE tipo_de_tarjeta(
    id_tipo_de_tarjeta serial
    tipo varchar(32)
);
CREATE TABLE emisora_tarjeta(
    id_emisora serial
    emisora varchar(20)
);
CREATE TABLE mayorista(
    id_mayorista serial
    nombre varchar(30)
    repre_empresa varchar(30)
    clienteid_cliente integer(10)
    representantesid_representante integer(10)
);
```


--(IVAN)

```sql
CREATE TABLE telefono_may (
	mayoristaid_mayorista 	INTEGER(10),
	teléfono 		INTEGER(10)
);
CREATE TABLE correo_may (
	mayoristaid_mayorista 	INTEGER(10),
	correo 			VARCHAR(30)
);
CREATE TABLE rfc_empresa (
	mayoristaid_mayorista 	INTEGER(10),
	rfc 			VARCHAR(13)
);
CREATE TABLE representantes (
	Id_representantes 	SERIAL,
	nombre 			VARCHAR(20),
	app			VARCHAR(20),
	apm			VARCHAR(20)
);
CREATE TABLE dir_mayorista(
	mayoristaid_mayorista	INTEGER(10),
	numero 			INTEGER(10),
	calle 			VARCHAR(30),
	colonia			VARCHAR(20),
	estado 			VARCHAR(20),
	cp			INTEGER(8),
	municipio		VARCHAR(20)
);
CREATE TABLE compra(
	id_compra 		SERIAL,
	fecha			DATE,
	clienteid_cliente	INTEGER(10),
	id_trabajador		INTEGER(10)
);
```

--(LUIS)

```sql
CREATE TABLE cmodalidad(
    id_modalidad SERIAL,
    nombre VARCHAR(50),
    descripcion VARCHAR(25),
    dependencia VARCHAR(255)
);

CREATE TABLE tipo_pago(
    id_tipo_pago SERIAL,
    fisico_online BIT,
    id_modalidad SMALLINT
);

CREATE TABLE compra_tipo_compra(
    id_compra INTEGER,
    id_tipo_pago INTEGER
);

CREATE TABLE producto_compra(
    id_compra INTEGER,
    id_producto INTEGER,
    precio REAL,
    cantidad SMALLINT
);

CREATE TABLE producto(
    id_producto SERIAL,
    nombre_prodcuto VARCHAR(50),
    id_categoria INTEGER
);

CREATE TABLE categoria(
    id_categoria SERIAL,
    nombre_categoria VARCHAR(50)
);
```


-(NANCY)
```sql
create table catalogo_categoria (
    id_cat_categoria  serial,
	precio real,
	tipo_producto varchar(256),
	marca varchar(32),
	articulo varchar(32),
	cantidad integer,
	tamanio varchar(20),
	categoriaid_categoria integer --añadir esta parte
);

create table promociones_producto (
    productoid_producto INTEGER,
    promocionesid_promocion INTEGER
);

create table promociones (
    id_promocion serial,
    fecha_incio date,
    fecha_fin date,
    cantidad_descuento real,
    tipo_promocion varchar(256)
);

CREATE TABLE envio (
    id_envio serial,
    compraid_compra integer,
    repartidorid_repartidor integer
);

CREATE TABLE empleado (
    id_trabajador serial,
    nombre varchar(30),
    app varchar(30),
    apm varchar(30),
    noss integer,  --o TEXT?
    sexo varchar(30),
    fecha_nac date,
    rfc varchar(13),
    fecha_inicio date,
    fecha_fin date,
    telefono integer,
    salario real,
    horario text,
    area varchar(20)
);
```
--(RODRIGO)
```sql
CREATE TABLE empleado_puesto(
	empleadoid_trabajador INTEGER,
	cpuestoid_cpuesto INTEGER
);

CREATE TABLE cpuesto(
	id_cpuesto INTEGER,
	puesto varchar(30)
);

CREATE TABLE repartidor(
	id_cpuesto INTEGER,
	puesto VARCHAR(30),
	no_licencia INTEGER,
	empleadoid_trabajador INTEGER,
	local_nacionalid_loc_nal INTEGER
);

CREATE TABLE local_nacional(
	id_loc_nal INTEGER,
	tipo VARCHAR(30)
);

CREATE TABLE tipo_unidad(
	local_nacionalid_loc_nal INTEGER,
	tipo_unidad VARCHAR(30)
);
```
--(GABY)

```sql
CREATE TABLE cajero (
	id_cajero      INTEGER(10),
	no_caja        SMALLINT(10),
	empleadoid_trabajador INTEGER(10)
);

CREATE TABLE capacitacion (
	id_trabajador_cap 	INTEGER(10),
	horas_completadas	SMALLINT(10),
	zona_enfoque            VARCHAR(255),
	empleadoid_trabajador   INTEGER(10)
);

CREATE TABLE empacador (
        id_empacador            SMALLINT(5),
	tipo_empacador          VARCHAR(30),
	empleadoid_trabajador   INTEGER(10)
);

CREATE TABLE encargado_almacen (
        id_encargado_alm        INTERGER(10),
	no_computadora          SMALLINT(10),
	empleadoid_trabajador   INTEGER(10)
);
CREATE TABLE encargado_almacen (
        id_encargado_mos        INTERGER(10),
	no_ventas               SMALLINT(10),
	empleadoid_trabajador   INTEGER(10)
);	
```	
	
--(CHRIS)

```sql

CREATE TABLE vigilancia (
 id_trabajador_vig SERIAL,
    recorrido VARCHAR(30),
    equipo VARCHAR(50),
    empleadoid_trabajador INTEGER(10)
);

CREATE TABLE intendencia (
  id_trabajador_int SERIAL,
     materia_trabajo VARCHAR(50),
     uniformes_ototgados VARCHAR(20),
  empleadoid_trabajador INTEGER(10)
);

CREATE TABLE gerente (
   id_gerente SERIAL,
      sucursal VARCHAR(50),
   empleadoid_trabajador INTEGER(10)
);

CREATE TABLE gerente_proveedor (
   id_encargo_proveedor SERIAL,
   gerenteid_gerente INTEGER(10),
   proveedorid_proveedor INTEGER(10)
);

CREATE TABLE encargo_seguimiento (
   gerente_proveedorid_encargo_proveedor SERIAL
     no_seguimiento INTEGER(10)
); 
```

--(MARLENE)
``` sql
CREATE TABLE encargo_orden(
    gerente_proveedorid_encargo_proveedor serial,
    no_orden integer
);


CREATE TABLE proveedor(
    id_proveedor serial,
    nombre_proveedor varchar(50),
    rfc varchar(13),
    telefono integer

);

CREATE TABLE producto_proveedor(
    id_prod_proveedor serial,
    nombre_prod_proveedor varchar(50),
    proveedorid_proveedor integer

);


CREATE TABLE prod_proveedor_precio(
    producto_proveedorid_prod_proveedor serial,
    precio integer
);

CREATE TABLE prod_proveedor_tipo(
    producto_proveedorid_prod_proveedor serial,
    tipo_producto varchar(50),
    
);
```
