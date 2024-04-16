# <u>TALLER BD2</u>



## Consultas sobre una tabla

1. Lista el primer apellido de todos los empleados.

   ```mysql
   SELECT e.apellido1
   FROM empleado AS e;
   ```

2. Lista el primer apellido de los empleados eliminando los apellidos que estén
    repetidos.

  ```mysql
  SELECT DISTINCT e.apellido1
  FROM empleado AS e;
  ```

3. Lista todas las columnas de la tabla empleado.

   ```mysql
   SELECT e.codigo,e.nif,e.nombre,e.apellido1,e.apellido2,e.codigo_departamento
   FROM empleado AS e;
   ```

4. Lista el nombre y los apellidos de todos los empleados.

   ```mysql
   SELECT e.nombre,e.apellido1,e.apellido2
   FROM empleado AS e;
   ```

5. Lista el identificador de los departamentos de los empleados que aparecen
    en la tabla empleado.

  ```mysql
  SELECT e.codigo_departamento
  FROM empleado AS e;
  ```

6. Lista el identificador de los departamentos de los empleados que aparecen en la tabla empleado, eliminando los identificadores que aparecen repetidos.

     ```mysql
     SELECT DISTINCT e.codigo_departamento
     FROM empleado AS e;
     ```

7. Lista el nombre y apellidos de los empleados en una única columna.

     ```mysql
     SELECT CONCAT (e.nombre,' ',e.apellido1,' ',apellido2) AS NOMBRES_Y_APELLIDOS
     FROM empleado AS e;
     ```

8. Lista el nombre y apellidos de los empleados en una única columna,
     convirtiendo todos los caracteres en mayúscula.

     ```mysql
     SELECT UPPER(CONCAT(e.nombre,' ',e.apellido1,' ',apellido2)) AS NOMBRES_Y_APELLIDOS
     FROM empleado AS e;
     ```

9. Lista el nombre y apellidos de los empleados en una única columna,
     convirtiendo todos los caracteres en minúscula.

     ```MYSQL
     SELECT LOWER(CONCAT(e.nombre,' ',e.apellido1,' ',apellido2)) AS NOMBRES_Y_APELLIDOS
     FROM empleado AS e;
     ```

10. Lista el identificador de los empleados junto al nif, pero el nif deberá
      aparecer en dos columnas, una mostrará únicamente los dígitos del nif y la
      otra la letra.

     ```mysql
     SELECT e.codigo, SUBSTRING(nif, 1, LENGTH(nif) - 1) AS DIGITOS, RIGHT(nif, 1) AS LETRAS
     FROM empleado AS e;
     ```

11. Lista el nombre de cada departamento y el valor del presupuesto actual del
        que dispone. Para calcular este dato tendrá que restar al valor del
        presupuesto inicial (columna presupuesto) los gastos que se han generado
        (columna gastos). Tenga en cuenta que en algunos casos pueden existir
        valores negativos. Utilice un alias apropiado para la nueva columna columna
        que está calculando.

      ```mysql
      SELECT d.nombre AS DEPARTAMENTO,(d.presupuesto - d.gasto) AS SALDO
      FROM departamento AS d;
      ```

12. Lista el nombre de los departamentos y el valor del presupuesto actual
        ordenado de forma ascendente.

      ```mysql
      SELECT d.nombre AS DEPARTAMENTO,(d.presupuesto - d.gasto) AS SALDO
      FROM departamento AS d
      ORDER BY SALDO ASC;
      ```

13. Lista el nombre de todos los departamentos ordenados de forma
        ascendente.

      ```mysql
      SELECT d.nombre AS DEPARTAMENTO
      FROM departamento AS d
      ORDER BY d.nombre ASC;
      ```

14. Lista el nombre de todos los departamentos ordenados de forma
        descendente.

      ```mysql
      SELECT d.nombre AS DEPARTAMENTO
      FROM departamento AS d
      ORDER BY d.nombre DESC;
      ```

15. Lista los apellidos y el nombre de todos los empleados, ordenados de forma
        alfabética tendiendo en cuenta en primer lugar sus apellidos y luego su
        nombre.

      ```mysql
      SELECT e.apellido1,e.apellido2,e.nombre
      FROM empleado AS e
      ORDER BY apellido1 ASC,apellido2 ASC,e.nombre ASC;
      ```

16. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
        que tienen mayor presupuesto.

      ```mysql
      SELECT d.nombre,d.presupuesto
      FROM departamento AS d
      ORDER BY presupuesto DESC
      LIMIT 3;
      ```

17. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
        que tienen menor presupuesto.

      ```mysql
      SELECT d.nombre,d.presupuesto
      FROM departamento AS d
      ORDER BY presupuesto 
      LIMIT 3;
      ```

18. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
        tienen mayor gasto.

      ```mysql
      SELECT d.nombre,d.gasto
      FROM departamento AS d
      ORDER BY gasto DESC
      LIMIT 2;
      ```

19. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
        tienen menor gasto.

      ```mysql
      SELECT d.nombre,d.gasto
      FROM departamento AS d
      ORDER BY gasto 
      LIMIT 2;
      ```

20. Devuelve una lista con 5 filas a partir de la tercera fila de la tabla empleado. La
        tercera fila se debe incluir en la respuesta. La respuesta debe incluir todas las
        columnas de la tabla empleado.

      ```mysql
      SELECT e.codigo,e.nif,e.nombre,e.apellido1,e.apellido2,e.codigo_departamento
      FROM empleado AS e
      LIMIT 5 OFFSET 2;
      ```

21. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
        aquellos que tienen un presupuesto mayor o igual a 150000 euros.

      ```mysql
      SELECT d.nombre,d.presupuesto
      FROM departamento AS d
      WHERE presupuesto >= 150000;
      ```

22. Devuelve una lista con el nombre de los departamentos y el gasto, de
        aquellos que tienen menos de 5000 euros de gastos.

      ```mysql
      SELECT d.nombre,d.gasto
      FROM departamento AS d
      WHERE presupuesto <= 5000;
      ```

23. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
        aquellos que tienen un presupuesto entre 100000 y 200000 euros. Sin
        utilizar el operador BETWEEN.

      ```mysql
      SELECT d.nombre,d.presupuesto
      FROM departamento AS d
      WHERE presupuesto >= 100000 AND presupuesto <= 200000; 
      ```

24. Devuelve una lista con el nombre de los departamentos que no tienen un
        presupuesto entre 100000 y 200000 euros. Sin utilizar el operador BETWEEN.

      ```mysql
      SELECT d.nombre,d.presupuesto
      FROM departamento AS d
      WHERE NOT presupuesto >= 100000 AND presupuesto <= 200000; 
      ```

25. Devuelve una lista con el nombre de los departamentos que tienen un
        presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

      ```mysql
      SELECT d.nombre,d.presupuesto
      FROM departamento AS d
      WHERE presupuesto BETWEEN 100000 AND 200000; 
      ```

26. Devuelve una lista con el nombre de los departamentos que no tienen un
        presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

      ```mysql
      SELECT d.nombre,d.presupuesto
      FROM departamento AS d
      WHERE NOT presupuesto BETWEEN 100000 AND 200000; 
      ```

27. Devuelve una lista con el nombre de los departamentos, gastos y
        presupuesto, de aquellos departamentos donde los gastos sean mayores
        que el presupuesto del que disponen.

      ```mysql
      SELECT d.nombre,d.gasto, d.presupuesto
      FROM departamento AS d
      WHERE d.gasto > d.presupuesto;
      ```

28. Devuelve una lista con el nombre de los departamentos, gastos y
        presupuesto, de aquellos departamentos donde los gastos sean menores
        que el presupuesto del que disponen.

      ```mysql
      SELECT d.nombre,d.gasto, d.presupuesto
      FROM departamento AS d
      WHERE d.gasto < d.presupuesto;
      ```

29. Devuelve una lista con el nombre de los departamentos, gastos y
        presupuesto, de aquellos departamentos donde los gastos sean iguales al
        presupuesto del que disponen.

      ```mysql
      SELECT d.nombre,d.gasto, d.presupuesto
      FROM departamento AS d
      WHERE d.gasto = d.presupuesto;
      ```

30. Lista todos los datos de los empleados cuyo segundo apellido sea NULL.

      ```mysql
      SELECT e.apellido2
      FROM empleado AS e
      WHERE e.apellido2 IS NULL;
      ```

31. Lista todos los datos de los empleados cuyo segundo apellido no sea NULL.

      ```mysql
      SELECT e.apellido2
      FROM empleado AS e
      WHERE e.apellido2 IS NOT NULL;
      ```

32. Lista todos los datos de los empleados cuyo segundo apellido sea López.

      ```mysql
      SELECT e.apellido2
      FROM empleado AS e
      WHERE e.apellido2 ='López';
      ```

33. Lista todos los datos de los empleados cuyo segundo apellido
        sea Díaz o Moreno. Sin utilizar el operador IN.

      ```mysql
      SELECT e.apellido2
      FROM empleado AS e
      WHERE e.apellido2 ='Díaz' OR e.apellido2 ='Moreno';
      ```

34. Lista todos los datos de los empleados cuyo segundo apellido
        sea Díaz o Moreno. Utilizando el operador IN.

      ```mysql
      SELECT e.apellido2
      FROM empleado AS e
      WHERE e.apellido2 IN ('Díaz','Moreno');
      ```

35. Lista los nombres, apellidos y nif de los empleados que trabajan en el
        departamento 3.

      ```mysql
      SELECT e.nombre,e.apellido1,e.apellido2,e.nif
      FROM empleado AS e
      WHERE codigo_departamento = 3;
      ```

36. Lista los nombres, apellidos y nif de los empleados que trabajan en los
        departamentos 2, 4 o 5.

      ```mysql
      SELECT e.nombre,e.apellido1,e.apellido2,e.nif
      FROM empleado AS e
      WHERE codigo_departamento IN (2,4,5);
      ```

      

## Consultas multitabla (Composición interna)

Resuelva todas las consultas utilizando la sintaxis de SQL1 y SQL2.

1. Devuelve un listado con los empleados y los datos de los departamentos
  donde trabaja cada uno.

  ```sql
  SELECT e.nombre,e.codigo_departamento,d.codigo,d.nombre,d.presupuesto,d.gasto
  FROM empleado AS e,departamento AS d
  WHERE e.codigo_departamento = d.codigo;
  ```

2. Devuelve un listado con los empleados y los datos de los departamentos
  donde trabaja cada uno. Ordena el resultado, en primer lugar por el nombre
  del departamento (en orden alfabético) y en segundo lugar por los apellidos
  y el nombre de los empleados.

  ```sql
  SELECT e.nombre,e.codigo_departamento,d.codigo,d.nombre,d.presupuesto,d.gasto
  FROM empleado AS e,departamento AS d
  WHERE e.codigo_departamento = d.codigo
  ORDER BY d.nombre,e.apellido1,e.apellido2,e.nombre;
  ```

3. Devuelve un listado con el identificador y el nombre del departamento,
  solamente de aquellos departamentos que tienen empleados.

  ```sql
  SELECT d.codigo,d.nombre
  FROM empleado AS e,departamento AS d
  WHERE e.codigo_departamento = d.codigo AND d.codigo = e.codigo_departamento 
  ```

4. Devuelve un listado con el identificador, el nombre del departamento y el
  valor del presupuesto actual del que dispone, solamente de aquellos
  departamentos que tienen empleados. El valor del presupuesto actual lo
  puede calcular restando al valor del presupuesto inicial
  (columna presupuesto) el valor de los gastos que ha generado
  (columna gastos).

5. Devuelve el nombre del departamento donde trabaja el empleado que tiene
  el nif 38382980M.

6. Devuelve el nombre del departamento donde trabaja el empleado Pepe Ruiz
  Santana.

7. Devuelve un listado con los datos de los empleados que trabajan en el
  departamento de I+D. Ordena el resultado alfabéticamente.

8. Devuelve un listado con los datos de los empleados que trabajan en el
  departamento de Sistemas, Contabilidad o I+D. Ordena el resultado
  alfabéticamente.

9. Devuelve una lista con el nombre de los empleados que tienen los
  departamentos que no tienen un presupuesto entre 100000 y 200000 euros.

10. Devuelve un listado con el nombre de los departamentos donde existe
    algún empleado cuyo segundo apellido sea NULL. Tenga en cuenta que no
    debe mostrar nombres de departamentos que estén repetidos.

## Consultas multitabla (Composición externa)

Resuelva todas las consultas utilizando las cláusulas LEFT JOIN y RIGHT JOIN.

1. Devuelve un listado con todos los empleados junto con los datos de los
departamentos donde trabajan. Este listado también debe incluir los
empleados que no tienen ningún departamento asociado.
2. Devuelve un listado donde sólo aparezcan aquellos empleados que no
tienen ningún departamento asociado.
3. Devuelve un listado donde sólo aparezcan aquellos departamentos que no
tienen ningún empleado asociado.
4. Devuelve un listado con todos los empleados junto con los datos de los
departamentos donde trabajan. El listado debe incluir los empleados que no
tienen ningún departamento asociado y los departamentos que no tienen
ningún empleado asociado. Ordene el listado alfabéticamente por el
nombre del departamento.
5. Devuelve un listado con los empleados que no tienen ningún departamento
asociado y los departamentos que no tienen ningún empleado asociado.
Ordene el listado alfabéticamente por el nombre del departamento.

## Consultas resumen

1. Calcula la suma del presupuesto de todos los departamentos.
2. Calcula la media del presupuesto de todos los departamentos.
3. Calcula el valor mínimo del presupuesto de todos los departamentos.
4. Calcula el nombre del departamento y el presupuesto que tiene asignado,
del departamento con menor presupuesto.
5. Calcula el valor máximo del presupuesto de todos los departamentos.
6. Calcula el nombre del departamento y el presupuesto que tiene asignado,
del departamento con mayor presupuesto.
7. Calcula el número total de empleados que hay en la tabla empleado.
8. Calcula el número de empleados que no tienen NULL en su segundo
apellido.
9. Calcula el número de empleados que hay en cada departamento. Tienes que
devolver dos columnas, una con el nombre del departamento y otra con el
número de empleados que tiene asignados.
10. Calcula el nombre de los departamentos que tienen más de 2 empleados. El
resultado debe tener dos columnas, una con el nombre del departamento y
otra con el número de empleados que tiene asignados.
11. Calcula el número de empleados que trabajan en cada uno de los
departamentos. El resultado de esta consulta también tiene que incluir
aquellos departamentos que no tienen ningún empleado asociado.
12. Calcula el número de empleados que trabajan en cada unos de los
departamentos que tienen un presupuesto mayor a 200000 euros.





