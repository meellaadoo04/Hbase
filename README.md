# Hbase

HBase es una base de datos no relacional que no soporta Joins y donde el acceso a todos los datos se realiza principalmente mediante las claves de las filas. 

No disponen de un esquema fijo por lo que se puede agregar o quitar columnas de manera dinamica y cada fila puede contener diferentes columnas. 

 HBase se inspira en Bigtable de Google y es ideal para aplicaciones que requieren lecturas y escrituras a rapida velocidad pero no para crear relaciones complejas enntre los datos 
 
UTILIZACIÓN 

Creamos los archivos docker-compose.yml y hbase-site.xml 

Ejecutamos el Docker --> 
```bash
docker-compose up -d`
```

Accedemos a la consola de Hbase -->
```bash
docker exec -it hbase bash
```

Dentro del contendeor iniciamos la shell --> 
```bash
bin/hbase shell
```

Para la creación de la tabla deberemos utilizar el siguiente formato: 

 

create "nombre de la tabla", "nombre_filas"  --> 
```bash
create 'jugadores_futbol', 'nombre', 'nacionalidad', 'goles', 'asistencias' 
```
 

Para la insercción de datos utilizamos el siguiente comando: 
Put 'nombre_tabla', 'jugador', 'fila',  'valor'


 
```bash
# Datos para el jugador 1 

put 'jugadores_futbol', 'player1', 'nombre:', 'Lionel Messi' 

put 'jugadores_futbol', 'player1', 'nacionalidad:', 'Argentina' 

put 'jugadores_futbol', 'player1', 'goles:', '800' 

put 'jugadores_futbol', 'player1', 'asistencias:', '300' 

  

# Datos para el jugador 2 

put 'jugadores_futbol', 'player2', 'nombre:', 'Cristiano Ronaldo' 

put 'jugadores_futbol', 'player2', 'nacionalidad:', 'Portugal' 

put 'jugadores_futbol', 'player2', 'goles:', '810' 

put 'jugadores_futbol', 'player2', 'asistencias:', '220' 

  

# Datos para el jugador 3 

put 'jugadores_futbol', 'player3', 'nombre:', 'Kylian Mbappé' 

put 'jugadores_futbol', 'player3', 'nacionalidad:', 'France' 

put 'jugadores_futbol', 'player3', 'goles:', '250' 

put 'jugadores_futbol', 'player3', 'asistencias:', '100' 

 ```

Consultar la tabla  

 
```bash
scan 'jugadores_futbol' 
```
 

Consultar un jugador especifico 

 
```bash
get 'jugadores_futbol', 'player1' 
```
 

Consultar solo los nombres 

 
```bash
scan 'jugadores_futbol', {COLUMNS => ['nombre:']} 
```
 

Contar el numero de filas de cada tabla 

 
```bash
count 'jugadores_futbol' 
```
 

Muestrame solo las 2 primeras filas 

 
```bash
scan 'jugadores_futbol', {LIMIT => 2} 
```
 
