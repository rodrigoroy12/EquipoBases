# EquipoBases
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
