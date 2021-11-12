
```sql
SELECT *
FROM
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

