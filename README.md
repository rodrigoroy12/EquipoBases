# EquipoBases

--
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


--(MARLENE)

CREATE TABLE encargo_orden(
    gerente_proveedorid_encargo_proveedor serial,
    no_orden integer,
    primary key (gerente_proveedorid_encargo_proveedor)
);


CREATE TABLE proveedor(
    id_proveedor serial,
    nombre_proveedor varchar(50) not null,
    rfc varchar(13),
    telefono integer,
    primary key(id_proveedor)

);

CREATE TABLE producto_proveedor(
    id_prod_proveedor serial,
    nombre_prod_proveedor varchar(50),
    proveedorid_proveedor integer,
    primary key(id_prod_proveedor),
    foreign key(proveedorid_proveedor) references proveedor

);


CREATE TABLE prod_proveedor_precio(
    producto_proveedorid_prod_proveedor serial,
    precio integer,
    primary key (producto_proveedorid_prod_proveedor)
)

CREATE TABLE prod_proveedor_tipo(
    producto_proveedorid_prod_proveedor serial,
    tipo_producto varchar(50)
)


