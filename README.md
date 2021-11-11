# EquipoBases

--(ENRIQUE)

--(DANI)

--(IVAN)
```sql
CREATE TABLE teléfono_may (
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

--(GABY)

--(CHRIS)

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
