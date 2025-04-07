# Ejercicios vistas, índices y procedimientos

 - Definir una query compleja, y una actualización en alguna tabla a partir de ella, que apunte a la base de datos bands y que implique el mayor número de tablas posibles, por ejemplo:
 
   - Obtén el top 10 de bandas con mayor duración de cualquiera de sus álbumes de los 00s, siendo que el primer album de esas bandas haya salido en los 90s. Cambia la duración de todos los álbumes de estas 10 bandas a 0.
   
   - Selecciona la banda indie best seller de los 00s, con una media de sus álbumes igual o superior a 30 mins y que todos sus miembros sean los mismos que desde la fundación de la banda (que no tenga former members). Haz que uno de ellos abandone la banda.
   
/*I want to find bands whose names start with A, 
whose last album was released before 2004, 
that are associated with only one genre 
and whose no musician has status former (no musician left the band). */

SELECT b.band_name
FROM bandas.Band b
-- Bands whose names start with 'A'
WHERE b.band_name LIKE 'A%'
-- Bands whose last album was released before 2004
AND b.band_id IN (
    SELECT a.band_id
    FROM bandas.Album a
    GROUP BY a.band_id
    HAVING MAX(a.release_date) < '2004-01-01'
)
-- Bands associated with only one genre
AND b.band_id IN (
    SELECT g.band_id
    FROM bandas.band_genre g
    GROUP BY g.band_id
    HAVING COUNT(DISTINCT g.genre_name) = 1
)
-- Bands where no musician has 'former' status
AND b.band_id NOT IN (
    SELECT m.band_id
    FROM bandas.band_musician m
    WHERE m.musician_status = 'former'
)

   
 - Escríbela en SQL y comprueba que saca lo que pretendías. Todavía sin tener en cuenta la actualización.
 - Usa `EXPLAIN ANALYZE` para evaluar cuánto tarda en ejecutar, en tiempo (ms) y en costo.

'-> Nested loop antijoin  (cost=2093 rows=2967) (actual time=166..171 rows=12 loops=1)\n    -> Filter: ((b.band_name like \'A%\') and <in_optimizer>(b.band_id,b.band_id in (select #2)) and <in_optimizer>(b.band_id,b.band_id in (select #3)))  (cost=1016 rows=1102) (actual time=166..171 rows=20 loops=1)\n        -> Table scan on b  (cost=1016 rows=9919) (actual time=0.0769..3.02 rows=10000 loops=1)\n        -> Select #2 (subquery in condition; run only once)\n            -> Filter: ((b.band_id = `<materialized_subquery>`.band_id))  (cost=12571..12571 rows=1) (actual time=0.235..0.235 rows=0.119 loops=589)\n                -> Limit: 1 row(s)  (cost=12571..12571 rows=1) (actual time=0.235..0.235 rows=0.119 loops=589)\n                    -> Index lookup on <materialized_subquery> using <auto_distinct_key> (band_id = b.band_id)  (actual time=0.235..0.235 rows=0.119 loops=589)\n                        -> Materialize with deduplication  (cost=12571..12571 rows=6779) (actual time=138..138 rows=1517 loops=1)\n                            -> Filter: (max(a.release_date) < \'2004-01-01\')  (cost=11009 rows=6779) (actual time=1.51..136 rows=1517 loops=1)\n                                -> Group aggregate: max(a.release_date)  (cost=11009 rows=6779) (actual time=1.5..135 rows=6878 loops=1)\n                                    -> Index scan on a using band_id  (cost=3561 rows=32325) (actual time=1.46..126 rows=34634 loops=1)\n        -> Select #3 (subquery in condition; run only once)\n            -> Filter: ((b.band_id = `<materialized_subquery>`.band_id))  (cost=9773..9773 rows=1) (actual time=0.392..0.392 rows=0.282 loops=71)\n                -> Limit: 1 row(s)  (cost=9773..9773 rows=1) (actual time=0.392..0.392 rows=0.282 loops=71)\n                    -> Index lookup on <materialized_subquery> using <auto_distinct_key> (band_id = b.band_id)  (actual time=0.384..0.384 rows=0.282 loops=71)\n                        -> Materialize with deduplication  (cost=9773..9773 rows=9056) (actual time=27.2..27.2 rows=2328 loops=1)\n                            -> Filter: (count(distinct g.genre_name) = 1)  (cost=7687 rows=9056) (actual time=0.0929..24.8 rows=2328 loops=1)\n                                -> Group aggregate: count(distinct g.genre_name)  (cost=7687 rows=9056) (actual time=0.0855..20.6 rows=8902 loops=1)\n                                    -> Covering index scan on g using PRIMARY  (cost=2343 rows=23190) (actual time=0.0773..9.67 rows=23632 loops=1)\n    -> Filter: (m.musician_status = \'former\')  (cost=1.91 rows=2.69) (actual time=0.006..0.006 rows=0.4 loops=20)\n        -> Index lookup on m using PRIMARY (band_id = b.band_id)  (cost=1.91 rows=2.69) (actual time=0.00543..0.00559 rows=0.95 loops=20)\n'


 - Define los índices que creas necesarios para optimizar tu búsqueda.
 - Comprueba que el tiempo de ejecución ha mejorado.
 - Crea un procedimiento que ejecute la query, encuentre los elementos a actualizar y los actualice en la base de datos con `UPDATE` y ejecútalo con `CALL`
 - Crea una vista que muestre los cambios
 
   
   