# EquipoBases

--(ENRIQUE)

--(DANI)

--(IVAN)

--(LUIS)

-(NANCY)
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

--(RODRIGO)

--(GABY)

--(CHRIS)

--(MARLENE)
