
```sql

--(BRUCE)
--LLAVES PRIMARIAS
ALTER TABLE minorista ADD CONSTRAINT pk_minorista PRIMARY KEY (id_minorista);

ALTER TABLE miembros ADD CONSTRAINT pk_miembros PRIMARY KEY (id_miembro );

ALTER TABLE cmembresia ADD CONSTRAINT pk_cmembresia PRIMARY KEY (nombre);

ALTER TABLE telefono_miembros ADD CONSTRAINT pk_telefono_miembros PRIMARY KEY (miembrosid_miembro,telefono);

ALTER TABLE minorista_online ADD CONSTRAINT pk_minorista_online PRIMARY KEY (id_minorista_on );

ALTER TABLE telefono_min ADD CONSTRAINT telefono_min PRIMARY KEY (minorista_onlineid_minorista_on,telefono );

--LLAVES FORANEAS
ALTER TABLE minorista ADD CONSTRAINT fk_minorista_clienteid_cliente_cliente_id_cliente FOREIGN KEY (clienteid_cliente) REFERENCES cliente(id_cliente);

ALTER TABLE minorista_online ADD CONSTRAINT fk_minorista_clienteid_cliente_cliente_id_cliente FOREIGN KEY (clienteid_cliente) REFERENCES cliente(id_cliente);

ALTER TABLE miembros ADD CONSTRAINT fk_miembros_minoristaid_minorista_minorista_id_minorista FOREIGN KEY (minoristaid_minorista) REFERENCES minorista(id_minorista);

ALTER TABLE miembros ADD CONSTRAINT fk_miembros_cmembresianombre_cmembresia_cmembresianombre FOREIGN KEY (cmembresianombre) REFERENCES cmembresia(nombre);

ALTER TABLE telefono_miembros ADD CONSTRAINT fk_telefono_miembros_miembros_id_miembro FOREIGN KEY (miembrosid_miembro) REFERENCES miembros(id_miembro);

ALTER TABLE telefono_min ADD CONSTRAINT fk_telefono_min_minorista_online_id_minorista_on FOREIGN KEY (minorista_onlineid_minorista_on) REFERENCES minorista_online(id_minorista_on);

--NULL AND CHECK
ALTER TABLE miembros ALTER CONSTRAINT chk_miembro_sexo CHECK (sexo= "Mujer" OR sexo="Hombre" OR sexo="Otro");
ALTER TABLE minorista_online ALTER CONSTRAINT chk_minorista_online_sexo CHECK (sexo= "Mujer" OR sexo="Hombre" OR sexo="Otro");

```
```sql
--(NANCY)
--LLAVES PRIMARIAS
ALTER TABLE catalogo_categoria  ADD CONSTRAINT  pk_catalogo_categoria_id_cat_categoria PRIMARY KEY (id_cat_categoria);
--falta catalogo_categoria ¿?
ALTER TABLE promociones  ADD CONSTRAINT  pk_promociones_id_promocion PRIMARY KEY (id_promocion);
ALTER TABLE envio ADD CONSTRAINT pk_envio_id_envio PRIMARY KEY (id_envio);
ALTER TABLE empleado ADD CONSTRAINT pk_empleado_id_trabajador PRIMARY KEY  (id_trabajador);

--LLAVES FORANEAS
ALTER TABLE catalogo_categoria ADD constraint fk_catalogo_categoria_categoriaid_categoria_categoria_id_categoria FOREIGN KEY (categoriaid_categoria) REFERENCES categoria(id_categoria);
ALTER TABLE promociones_producto ADD CONSTRAINT fk_promociones_producto_productoid_producto_producto_id_producto FOREIGN KEY (productoid_prodcto) references producto(id_producto);
ALTER TABLE promociones_producto ADD CONSTRAINT fk_promociones_producto_promocionesid_promocion_promociones_id_promocion FOREIGN KEY (promocionesid_promocion) references promociones(id_promocion);
--promociones no tiene llave foranea
ALTER TABLE envio ADD CONSTRAINT fk_envio_compraid_Compra_compra_id_Compra foreign key (compraid_compra) references compra(id_Compra);
ALTER TABLE envio ADD CONSTRAINT fk_envio_repartidorid_repartidor_repartidor_id_repartidor foreign key (repartidorid_repartidor) references repartidor(id_repartidor);
--empleado no tiene llaves foraneas

--NULL AND CHECK
-- catalogo_categoria no tiene NULL ni CHECk
--promociones_producto no tiene NULL ni CHECK
alter  table promociones alter column  cantidad_descuento set null;
--alter table  promociones add constraint chk_promociones_cantidad_descuento check (cantidad_descuento = );
--envio no tiene NULL ni CHECK
alter table empleado alter CONSTRAINT chk_empleado_noss check
(noss =  ‘[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]’
    OR ‘[0-9]-[0-9]-[0-9]-[0-9]-[0-9]-[0-9]-[0-9]-[0-9]-[0-9]-[0-9]-[0-9]’
    OR ‘[0-9][0-9-][0-9][0-9]-[0-9][0-9]-[0-9][0-9][0-9][0-9]-[0-9]’);
alter table empleado alter constraint chk_empleado_sexo CHECK (sexo= “Mujer, OR “Hombre” OR “Otro”);
alter table empleado alter constraint chk_empleado_rfc CHECK
(rfc = ‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9][A-Z]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-9][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-Z]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-9][A-Z]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][A-Z][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][A-Z][A-Z]’);
alter table empleado alter column fecha_fin set null;


```
```sql
--(DANI)
--LLAVES PRIMARIAS
ALTER TABLE correo_min ADD CONSTRAINT pk_correo_minorista_onlineid_minorista_on PRIMARY KEY (minorista_onlineid_minorista_on)
ALTER TABLE dir_minorista ADD CONSTRAINT pk_dir_minorista_id_minorista_on PRIMARY KEY (minorista_id_minorista_on)
ALTER TABLE tarjetas_registradas ADD CONSTRAINT pk_tarjetas_registradas_minorista_onlineid_minorista_on PRIMARY KEY (minorista_onlineid_minorista_on)
ALTER TABLE tipo_de_tarjeta ADD CONSTRAINT pk_tipo_de_tarjeta_id_tipo_de_tarjeta PRIMARY KEY (id_tipo_de_tarjeta)
ALTER TABLE emisora_tarjeta ADD CONSTRAINT pk_emisora_tarjeta_id_emisora PRIMARY KEY (id_emisora)
ALTER TABLE mayorista ADD CONSTRAINT pk_mayorista_id_mayorista PRIMARY KEY (id_mayorista)
--LLAVES FORANEAS
ALTER TABLE correo_min ADD CONSTRAINT fk_correo_min_minorista_onlineid_minorista_on_minorista_online_id_minorista_on FOREIGN KEY (minorista_onlineid_minorista_on) REFERENCES minorista_online (id_minorista_on)
ALTER TABLE dir_minorista ADD CONSTRAINT fk_dir_minorista_id_minorista_on_minorista_online_id_minorista_on FOREIGN KEY(minorista_online_id_minorista_on) FOREIGN KEY REFERENCES minorista_online (id_minorista_on)
ALTER TABLE tarjetas_registradas ADD CONSTRAINT fk_tarjetas_registradas_minorista_onlineid_minorista_on_minorista_online_id_minorista_on FOREIGN KEY (minorista_onlineid_minorista_on) REFERENCES minorista_online (id_minorista_on)
ALTER TABLE tarjetas_registradas ADD CONSTRAINT fk_tarjetas_registradas_tipo_de_tarjetaid_tipo_de_tarjeta_tipo_de_tarjeta_id_tipo_de_tarjeta FOREIGN KEY (tipo_de_tarjetaid_tipo_de_tarjeta) REFERENCES tipo_de_tarjeta(id_tipo_de_tarjeta)
ALTER TABLE tarjetas_registradas ADD CONSTRAINT fk_tarjetas_registradas_emisora_tarjetaid_emisora_emisora_tarjeta_id_emisora FOREIGN KEY (emisora_tarjetaid_emisora) REFERENCES emisora_tarjeta(id_emisora)
ALTER TABLE mayorista ADD CONSTRAINT fk_mayorista_clienteid_cliente_cliente_id_cliente FOREIGN KEY (clienteid_cliente) REFERENCES cliente(id_cliente)
ALTER TABLE mayorista ADD CONSTRAINT fk_mayorista_representanteid_representante_representantes_id_representante FOREIGN KEY (representanteid_representante) REFERENCES representantes(id_representante)
--NULL AND CHECK
ALTER TABLE tipo_de_tarjeta ALTER CONSTRAINT chk_tipo_de_tarjeta_tipo CHECK (tipo = "Débito" OR "Crédito")







```
```sql
--(IVAN)
--LLAVES PRIMARIAS
ALTER TABLE telefono_may ADD CONSTRAINT pk_telefono_may_mayoristaid_mayorista PRIMARY KEY (mayoristaid_mayorista);
ALTER TABLE correo_may ADD CONSTRAINT pk_correo_may_mayoristaid_mayorista PRIMARY KEY (mayoristaid_mayorista);
ALTER TABLE rfc_empresa ADD CONSTRAINT pk_rfc_empresa_mayoristaid_mayorista PRIMARY KEY (mayoristaid_mayorista);
ALTER TABLE representantes ADD CONSTRAINT pk_representantes_id_representantes PRIMARY KEY (id_representantes);
ALTER TABLE dir_mayorista ADD CONSTRAINT pk_dir_mayorista_mayoristaid_mayorista PRIMARY KEY (mayoristaid_mayorista);
ALTER TABLE compra ADD CONSTRAINT pk_compra_id_compra PRIMARY KEY (id_compra);

--LLAVES FORANEAS
ALTER TABLE telefono_may ADD constraint fk_telefono_may_mayoristaid_mayorista_mayorista_id_mayorista FOREIGN KEY (mayoristaid_mayorista) REFERENCES categoria(id_mayorista);
ALTER TABLE correo_may ADD constraint fk_correo_may_mayoristaid_mayorista_mayorista_id_mayorista FOREIGN KEY (mayoristaid_mayorista) REFERENCES categoria(id_mayorista);
ALTER TABLE rfc_empresa ADD constraint fk_rfc_empresa_mayoristaid_mayorista_mayorista_id_mayorista FOREIGN KEY (mayoristaid_mayorista) REFERENCES categoria(id_mayorista);
ALTER TABLE dir_mayorista ADD constraint fk_dir_mayorista_mayoristaid_mayorista_mayorista_id_mayorista FOREIGN KEY (mayoristaid_mayorista) REFERENCES categoria(id_mayorista);
ALTER TABLE dir_mayorista ADD constraint fk_dir_mayorista_mayoristaid_mayorista_mayorista_id_mayorista FOREIGN KEY (mayoristaid_mayorista) REFERENCES categoria(id_mayorista);
ALTER TABLE dir_mayorista ADD constraint fk_dir_mayorista_mayoristaid_mayorista_mayorista_id_mayorista FOREIGN KEY (mayoristaid_mayorista) REFERENCES categoria(id_mayorista);
ALTER TABLE compra ADD constraint fk_compra_clienteid_cliente_cliente_id_cliente FOREIGN KEY (clienteid_cliente) REFERENCES categoria(id_cliente);
ALTER TABLE compra ADD constraint fk_compra_id_trabajador_empleado_id_trabajador FOREIGN KEY (id_trabajador) REFERENCES categoria(id_trabajador);

--NULL AND CHECK
ALTER TABLE rfc_empresa ALTER CONSTRAINT chk_rfc_empresa CHECK 
(rfc = ‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9][A-Z]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-9][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-Z]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-9][A-Z]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][A-Z][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][A-Z][A-Z]’);



```
```sql
--(RODRIGO)
--LLAVES PRIMARIAS
ALTER TABLE cpuesto ADD CONSTRAINT pk_cpuesto_id_cpuesto PRIMARY KEY  (id_cpuesto);
ALTER TABLE repartidor ADD CONSTRAINT pk_repartidor_id_repartidor PRIMARY KEY  (id_repartidor);
ALTER TABLE local_nacional ADD CONSTRAINT pk_local_nacional_id_loc_nac PRIMARY KEY  (id_loc_nac);

--LLAVES FORANEAS
ALTER TABLE emplead_puesto ADD constraint fk_empleado_puesto_empleadoid_trabajador_empleado_id_trabajador FOREIGN KEY (empeleadoid_trabajador) REFERENCES empleado(id_trabajador);
ALTER TABLE emplead_puesto ADD constraint fk_empleado_puesto_cpuestoid_cpuesto_cpuesto_id_cpuesto FOREIGN KEY (cpuestoid_cpuesto) REFERENCES cpuesto(id_cpuesto);
ALTER TABLE repartidor ADD constraint fk_repartidor_empleadoid_trabajador_empleado_id_trabajador FOREIGN KEY (empeleadoid_trabajador) REFERENCES empleado(id_trabajador);
ALTER TABLE repartidor ADD constraint fk_repartidor_local_nacionalid_loc_nac FOREIGN KEY (local_nacionalid_loc_nac) REFERENCES local_nacional(id_loc_nac);
ALTER TABLE tipo_unidad ADD constraint fk_tipo_unidad_local_nacionalid_loc_nac_local_nacional_id_loc_nac FOREIGN KEY (local_nacionalid_loc_nal) REFERENCES local_nacional(id_loc_nac);

--NULL AND CHECK
ALTER TABLE local_nacional ALTER CONSTRAINT chk_local_nacional_tipo CHECK (tipo= "Local" OR "Nacional");
```

```sql

--(GABY)

--LLAVES PRIMARIAS
ALTER TABLE cajero ADD CONSTRAINT pk_cajero_id_cajero PRIMARY KEY (id_cajero);
ALTER TABLE capacitacion ADD CONSTRAINT pk_capacitacion_id_trabajador_cap PRIMARY KEY (id_trabajador_cap);
ALTER TABLE empacador ADD CONSTRAINT pk_empacador_id_empacador PRIMARY KEY (id_empacador);
ALTER TABLE encargado_almacen ADD CONSTRAINT pk_encargado_almacen_id_encargado_alm PRIMARY KEY (id_encargado_alm);
ALTER TABLE encargado_mostrador ADD CONSTRAINT pk_encargado_mostrador_id_encargado_mos PRIMARY KEY (id_encargado_mos);

--LLAVES FORANEAS
ALTER TABLE cajero ADD constraint fk_cajero_empleadoid_trabajador_empleado_id_trabajador FOREIGN KEY (empleadoid_trabajdor) REFERENCES categoria(id_trabajador);
ALTER TABLE capacitacion ADD constraint fk_capacitacion_empleadoid_trabajador_empleado_id_trabajador FOREIGN KEY (empleadoid_trabajdorr) REFERENCES categoria(id_trabajador);
ALTER TABLE empacador ADD constraint fk_empacador_empleadoid_trabajador_empleado_id_trabajador FOREIGN KEY (empleadoid_trabajdor) REFERENCES categoria(id_trabajador);
ALTER TABLE encargado_almacen ADD constraint fk_encargado_almacen_empleadoid_trabajador_empleado_id_trabajador FOREIGN KEY (empleadoid_trabajdor) REFERENCES categoria(id_trabajador);
ALTER TABLE encargado_mostrador ADD constraint fk_encargado_mostrador_empleadoid_trabajador_empleado_id_trabajador FOREIGN KEY (empleadoid_trabajdor) REFERENCES categoria(id_trabajador);

--NULL AND CHECK
ALTER TABLE capacitacion ALTER COLUMN zona_enfoque SET NULL;
ALTER TABLE capacitacion ALTER COLUMN horas completadas SET NULL;

```


```sql
--(CHRIS)
--LLAVES PRIMARIAS
ALTER TABLE vigilancia ADD CONSTRAINT pk_vigilancia_id_trabajador_vig PRIMARY KEY (id_trabajador_vig);
ALTER TABLE intendencia ADD CONSTRAINT pk_intendencia_id_trabajador_int PRIMARY KEY (id_trabajador_int);
ALTER TABLE gerente ADD CONSTRAINT pk_gerente_id_gerente PRIMARY KEY (id_gerente);
ALTER TABLE gerente_proveedor ADD CONSTRAINT pk_gerente_proveedor_id_encargado_proveedor PRIMARY KEY (id_encargado_proveedor);
ALTER TABLE encargo_seguimiento ADD CONSTRAINT pk_encargo_seguimiento_gerente_proveedorid_encargo_proveedor PRIMARY KEY (gerente_proveedorid_encargo_proveedor);

--LLAVES FORANEAS 
ALTER TABLE vigilancia ADD CONSTRAINT fk_vigilancia_empleadoid_trabajador_empleado_id_trabajador FOREIGN KEY (empleadoid_trabajador) REFERENCES empleado(id_trabajador);
ALTER TABLE intendencia ADD CONSTRAINT fk_intendencia_empleadoid_trabajador_empleado_id_trabajador FOREIGN KEY (empleadoid_trabajador) REFERENCES empleado(id_trabajador);
ALTER TABLE gerente ADD CONSTRAINT fk_gerente_empleadoid_trabajador_empleado_id_trabajador FOREIGN KEY (empleadoid_trabajador) REFERENCES empleado(id_trabajador);
ALTER TABLE gerente_proveedor ADD CONSTRAINT fk_gerente_proveedor_gerenteid_gerente_gerente_id_gerente FOREIGN KEY (gerenteid_gerente) REFERENCES gerente(id_gerente);
ALTER TABLE gerente_proveedor ADD CONSTRAINT fk_gerente_proveedor_proveedorid_proveedor_proveedor_id_proveedor FOREIGN KEY (proveedorid_proveedor) REFERENCES proveedor(id_proveedor);
ALTER TABLE encargo_seguimiento ADD CONSTRAINT fk_encargo_seguimiento_gerente_proveedorid_encargo_proveedor_gerente_proveedor_id_encargo_proveedor FOREIGN KEY (gerente_proveedorid_encargo_proveedor) REFERENCES gerente_proveedor(id_encargo_proveedor);

--NULL AND CHECK
ALTER TABLE vigilancia ALTER COLUMN equipo SET NULL;
ALTER TABLE vigilancia ALTER COLUMN recorrido SET NULL;
ALTER TABLE intendencia ALTER COLUMN uniformes_otorgados SET NULL;
ALTER TABLE intendencia ALTER COLUMN materia_trabajo SET NULL;
```


``` sql

--Marlene

--LLAVES PRIMARIAS
ALTER TABLE encargo_orden  ADD CONSTRAINT  pk_encargo_orden PRIMARY KEY (gerente_proveedorid_encargo_proveedor);
ALTER TABLE proveedor  ADD CONSTRAINT  pk_proveedor PRIMARY KEY (id_proveedor);
ALTER TABLE producto_proveedor ADD CONSTRAINT pk_producto_proveedor PRIMARY KEY (id_prod_proveedor);
ALTER TABLE prod_proveedor_precio ADD CONSTRAINT pk_prod_proveedor PRIMARY KEY  (producto_proveedorid_prod_proveedor);
ALTER TABLE prod_proveedor_tipo ADD CONSTRAINT pk_prod_proveedor_tipo PRIMARY KEY (producto_proveedorid_prod_proveedor);

--LLAVES FORANEAS

ALTER TABLE encargo_orden ADD CONSTRAINT fk_encargo_orden_gerente_proveedorid_encargo_proveedor_gerente_proveedor_id_encargo_proveedor FOREIGN KEY (gerente_proveedorid_encargo_proveedor) references gerente_proveedor(id_encargo_proveedor);

ALTER TABLE producto_proveedor ADD CONSTRAINT fk_producto_proveedor_proveedorid_proveedor_proveedor_id_proveedor FOREIGN KEY (proveedorid_proveedor) references proveedor(id_proveedor);

ALTER TABLE prod_proveedor_precio ADD CONSTRAINT fk_prod_proveedor_precio_producto_proveedorid_prod_proveedor_producto_proveedor_id_prod_proveedor FOREIGN KEY (producto_proveedorid__prod_proveedor) references producto_proveedor(id_prod_proveedor);

ALTER TABLE prod_proveedor_tipo ADD CONSTRAINT fk_prod_proveedor_tipo_producto_proveedorid_prod_proveedor_producto_proveedor_id_prod_proveedor FOREIGN KEY (producto_proveedorid__prod_proveedor) references producto_proveedor(id_prod_proveedor);


--proveedor no tiene llaves foraneas

--NULL AND CHECK
ALTER TABLE proveedor ALTER CONSTRAINT chk_proveedor_rfc CHECK 
(rfc = ‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9][A-Z]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-9][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-Z]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][0-9][A-Z]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][A-Z][0-9]’ OR
‘[A-Z][A-Z][A-Z][A-Z][0-9][0-9][0-9][0-9][0-9][0-9][A-Z][A-Z][A-Z]’);

ALTER TABLE encargo_orden alter column  no_orden set null;


```

