# <u>TALLER BD2</u>



## Consultas sobre una tabla

1. Lista el primer apellido de todos los empleados.

   ```mysql
   mysql> SELECT e.apellido1
       -> FROM empleado AS e;
   +-----------+
   | apellido1 |
   +-----------+
   | Rivero    |
   | Salas     |
   | Rubio     |
   | Suárez    |
   | Loyola    |
   | Santana   |
   | Ruiz      |
   | Ruiz      |
   | Gómez     |
   | Flores    |
   | Herrera   |
   | Salas     |
   | Sáez      |
   +-----------+
   13 rows in set (0,00 sec)
   
   ```

2. Lista el primer apellido de los empleados eliminando los apellidos que estén
    repetidos.

  ```mysql
  mysql> SELECT DISTINCT e.apellido1
      -> FROM empleado AS e;
  +-----------+
  | apellido1 |
  +-----------+
  | Rivero    |
  | Salas     |
  | Rubio     |
  | Suárez    |
  | Loyola    |
  | Santana   |
  | Ruiz      |
  | Gómez     |
  | Flores    |
  | Herrera   |
  | Sáez      |
  +-----------+
  11 rows in set (0,00 sec)
  
  ```

3. Lista todas las columnas de la tabla empleado.

   ```mysql
   mysql> SELECT e.codigo,e.nif,e.nombre,e.apellido1,e.apellido2,e.codigo_departamento
       -> FROM empleado AS e;
   +--------+-----------+--------------+-----------+-----------+---------------------+
   | codigo | nif       | nombre       | apellido1 | apellido2 | codigo_departamento |
   +--------+-----------+--------------+-----------+-----------+---------------------+
   |      1 | 32481596F | Aarón        | Rivero    | Gómez     |                   1 |
   |      2 | Y5575632D | Adela        | Salas     | Díaz      |                   2 |
   |      3 | R6970642B | Adolfo       | Rubio     | Flores    |                   3 |
   |      4 | 77705545E | Adrián       | Suárez    | NULL      |                   4 |
   |      5 | 17087203C | Marcos       | Loyola    | Méndez    |                   5 |
   |      6 | 38382980M | María        | Santana   | Moreno    |                   1 |
   |      7 | 80576669X | Pilar        | Ruiz      | NULL      |                   2 |
   |      8 | 71651431Z | Pepe         | Ruiz      | Santana   |                   3 |
   |      9 | 56399183D | Juan         | Gómez     | López     |                   2 |
   |     10 | 46384486H | Diego        | Flores    | Salas     |                   5 |
   |     11 | 67389283A | Marta        | Herrera   | Gil       |                   1 |
   |     12 | 41234836R | Irene        | Salas     | Flores    |                NULL |
   |     13 | 82635162B | Juan Antonio | Sáez      | Guerrero  |                NULL |
   +--------+-----------+--------------+-----------+-----------+---------------------+
   13 rows in set (0,00 sec)
   
   ```

4. Lista el nombre y los apellidos de todos los empleados.

   ```mysql
   mysql> SELECT e.nombre,e.apellido1,e.apellido2
       -> FROM empleado AS e;
   +--------------+-----------+-----------+
   | nombre       | apellido1 | apellido2 |
   +--------------+-----------+-----------+
   | Aarón        | Rivero    | Gómez     |
   | Adela        | Salas     | Díaz      |
   | Adolfo       | Rubio     | Flores    |
   | Adrián       | Suárez    | NULL      |
   | Marcos       | Loyola    | Méndez    |
   | María        | Santana   | Moreno    |
   | Pilar        | Ruiz      | NULL      |
   | Pepe         | Ruiz      | Santana   |
   | Juan         | Gómez     | López     |
   | Diego        | Flores    | Salas     |
   | Marta        | Herrera   | Gil       |
   | Irene        | Salas     | Flores    |
   | Juan Antonio | Sáez      | Guerrero  |
   +--------------+-----------+-----------+
   13 rows in set (0,00 sec)
   
   ```

5. Lista el identificador de los departamentos de los empleados que aparecen
    en la tabla empleado.

  ```mysql
  mysql> SELECT e.codigo_departamento
      -> FROM empleado AS e;
  +---------------------+
  | codigo_departamento |
  +---------------------+
  |                   1 |
  |                   2 |
  |                   3 |
  |                   4 |
  |                   5 |
  |                   1 |
  |                   2 |
  |                   3 |
  |                   2 |
  |                   5 |
  |                   1 |
  |                NULL |
  |                NULL |
  +---------------------+
  13 rows in set (0,00 sec)
  
  ```

6. Lista el identificador de los departamentos de los empleados que aparecen en la tabla empleado, eliminando los identificadores que aparecen repetidos.

     ```mysql
     mysql> SELECT DISTINCT e.codigo_departamento
         -> FROM empleado AS e;
     +---------------------+
     | codigo_departamento |
     +---------------------+
     |                   1 |
     |                   2 |
     |                   3 |
     |                   4 |
     |                   5 |
     |                NULL |
     +---------------------+
     6 rows in set (0,00 sec)
     
     ```

7. Lista el nombre y apellidos de los empleados en una única columna.

     ```mysql
     mysql> SELECT CONCAT (e.nombre,' ',e.apellido1,' ',apellido2) AS NOMBRES_Y_APELLIDOS
         -> FROM empleado AS e;
     +-----------------------------+
     | NOMBRES_Y_APELLIDOS         |
     +-----------------------------+
     | Aarón Rivero Gómez          |
     | Adela Salas Díaz            |
     | Adolfo Rubio Flores         |
     | NULL                        |
     | Marcos Loyola Méndez        |
     | María Santana Moreno        |
     | NULL                        |
     | Pepe Ruiz Santana           |
     | Juan Gómez López            |
     | Diego Flores Salas          |
     | Marta Herrera Gil           |
     | Irene Salas Flores          |
     | Juan Antonio Sáez Guerrero  |
     +-----------------------------+
     13 rows in set (0,00 sec)
     
     ```

8. Lista el nombre y apellidos de los empleados en una única columna,
     convirtiendo todos los caracteres en mayúscula.

     ```mysql
     mysql> SELECT UPPER(CONCAT(e.nombre,' ',e.apellido1,' ',apellido2)) AS NOMBRES_Y_APELLIDOS
         -> FROM empleado AS e;
     +-----------------------------+
     | NOMBRES_Y_APELLIDOS         |
     +-----------------------------+
     | AARÓN RIVERO GÓMEZ          |
     | ADELA SALAS DÍAZ            |
     | ADOLFO RUBIO FLORES         |
     | NULL                        |
     | MARCOS LOYOLA MÉNDEZ        |
     | MARÍA SANTANA MORENO        |
     | NULL                        |
     | PEPE RUIZ SANTANA           |
     | JUAN GÓMEZ LÓPEZ            |
     | DIEGO FLORES SALAS          |
     | MARTA HERRERA GIL           |
     | IRENE SALAS FLORES          |
     | JUAN ANTONIO SÁEZ GUERRERO  |
     +-----------------------------+
     13 rows in set (0,00 sec)
     
     ```
     
9. Lista el nombre y apellidos de los empleados en una única columna,
     convirtiendo todos los caracteres en minúscula.

     ```MYSQL
     SELECT LOWER(CONCAT(e.nombre,' ',e.apellido1,' ',apellido2)) AS NOMBRES_Y_APELLIDOS
     FROM empleado AS e;mysql> SELECT LOWER(CONCAT(e.nombre,' ',e.apellido1,' ',apellido2)) AS NOMBRES_Y_APELLIDOS
         -> FROM empleado AS e;
     +-----------------------------+
     | NOMBRES_Y_APELLIDOS         |
     +-----------------------------+
     | aarón rivero gómez          |
     | adela salas díaz            |
     | adolfo rubio flores         |
     | NULL                        |
     | marcos loyola méndez        |
     | maría santana moreno        |
     | NULL                        |
     | pepe ruiz santana           |
     | juan gómez lópez            |
     | diego flores salas          |
     | marta herrera gil           |
     | irene salas flores          |
     | juan antonio sáez guerrero  |
     +-----------------------------+
     13 rows in set (0,00 sec)
     
     ```
     
10. Lista el identificador de los empleados junto al nif, pero el nif deberá
      aparecer en dos columnas, una mostrará únicamente los dígitos del nif y la
      otra la letra.

     ```mysql
     mysql> SELECT e.codigo, SUBSTRING(nif, 1, LENGTH(nif) - 1) AS DIGITOS, RIGHT(nif, 1) AS LETRAS
         -> FROM empleado AS e;
     +--------+----------+--------+
     | codigo | DIGITOS  | LETRAS |
     +--------+----------+--------+
     |      1 | 32481596 | F      |
     |      2 | Y5575632 | D      |
     |      3 | R6970642 | B      |
     |      4 | 77705545 | E      |
     |      5 | 17087203 | C      |
     |      6 | 38382980 | M      |
     |      7 | 80576669 | X      |
     |      8 | 71651431 | Z      |
     |      9 | 56399183 | D      |
     |     10 | 46384486 | H      |
     |     11 | 67389283 | A      |
     |     12 | 41234836 | R      |
     |     13 | 82635162 | B      |
     +--------+----------+--------+
     13 rows in set (0,00 sec)
     
     ```
    
11. Lista el nombre de cada departamento y el valor del presupuesto actual del
        que dispone. Para calcular este dato tendrá que restar al valor del
        presupuesto inicial (columna presupuesto) los gastos que se han generado
        (columna gastos). Tenga en cuenta que en algunos casos pueden existir
        valores negativos. Utilice un alias apropiado para la nueva columna columna
        que está calculando.

      ```mysql
      mysql> SELECT d.nombre AS DEPARTAMENTO,(d.presupuesto - d.gasto) AS SALDO
          -> FROM departamento AS d;
      +------------------+--------+
      | DEPARTAMENTO     | SALDO  |
      +------------------+--------+
      | Desarrollo       | 114000 |
      | Sistemas         | 129000 |
      | Recursos Humanos | 255000 |
      | Contabilidad     | 107000 |
      | I+D              |  -5000 |
      | Proyectos        |      0 |
      | Publicidad       |  -1000 |
      +------------------+--------+
      7 rows in set (0,00 sec)
      
      ```
    
12. Lista el nombre de los departamentos y el valor del presupuesto actual
        ordenado de forma ascendente.

      ```mysql
      mysql> SELECT d.nombre AS DEPARTAMENTO,(d.presupuesto - d.gasto) AS SALDO
          -> FROM departamento AS d
          -> ORDER BY SALDO ASC;
      +------------------+--------+
      | DEPARTAMENTO     | SALDO  |
      +------------------+--------+
      | I+D              |  -5000 |
      | Publicidad       |  -1000 |
      | Proyectos        |      0 |
      | Contabilidad     | 107000 |
      | Desarrollo       | 114000 |
      | Sistemas         | 129000 |
      | Recursos Humanos | 255000 |
      +------------------+--------+
      7 rows in set (0,00 sec)
      
      ```
    
13. Lista el nombre de todos los departamentos ordenados de forma
        ascendente.

      ```mysql
      mysql> SELECT d.nombre AS DEPARTAMENTO
          -> FROM departamento AS d
          -> ORDER BY d.nombre ASC;
      +------------------+
      | DEPARTAMENTO     |
      +------------------+
      | Contabilidad     |
      | Desarrollo       |
      | I+D              |
      | Proyectos        |
      | Publicidad       |
      | Recursos Humanos |
      | Sistemas         |
      +------------------+
      7 rows in set (0,00 sec)
      
      ```
    
14. Lista el nombre de todos los departamentos ordenados de forma
        descendente.

      ```mysql
      mysql> SELECT d.nombre AS DEPARTAMENTO
          -> FROM departamento AS d
          -> ORDER BY d.nombre DESC;
      +------------------+
      | DEPARTAMENTO     |
      +------------------+
      | Sistemas         |
      | Recursos Humanos |
      | Publicidad       |
      | Proyectos        |
      | I+D              |
      | Desarrollo       |
      | Contabilidad     |
      +------------------+
      7 rows in set (0,00 sec)
      
      ```
    
15. Lista los apellidos y el nombre de todos los empleados, ordenados de forma
        alfabética tendiendo en cuenta en primer lugar sus apellidos y luego su
        nombre.

      ```mysql
      mysql> SELECT e.apellido1,e.apellido2,e.nombre
          -> FROM empleado AS e
          -> ORDER BY apellido1 ASC,apellido2 ASC,e.nombre ASC;
      +-----------+-----------+--------------+
      | apellido1 | apellido2 | nombre       |
      +-----------+-----------+--------------+
      | Flores    | Salas     | Diego        |
      | Gómez     | López     | Juan         |
      | Herrera   | Gil       | Marta        |
      | Loyola    | Méndez    | Marcos       |
      | Rivero    | Gómez     | Aarón        |
      | Rubio     | Flores    | Adolfo       |
      | Ruiz      | NULL      | Pilar        |
      | Ruiz      | Santana   | Pepe         |
      | Sáez      | Guerrero  | Juan Antonio |
      | Salas     | Díaz      | Adela        |
      | Salas     | Flores    | Irene        |
      | Santana   | Moreno    | María        |
      | Suárez    | NULL      | Adrián       |
      +-----------+-----------+--------------+
      13 rows in set (0,00 sec)
      
      ```
    
16. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
        que tienen mayor presupuesto.

      ```mysql
      mysql> SELECT d.nombre,d.presupuesto
          -> FROM departamento AS d
          -> ORDER BY presupuesto DESC
          -> LIMIT 3;
      +------------------+-------------+
      | nombre           | presupuesto |
      +------------------+-------------+
      | I+D              |      375000 |
      | Recursos Humanos |      280000 |
      | Sistemas         |      150000 |
      +------------------+-------------+
      3 rows in set (0,00 sec)
      
      ```
    
17. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
        que tienen menor presupuesto.

      ```mysql
      mysql> SELECT d.nombre,d.presupuesto
          -> FROM departamento AS d
          -> ORDER BY presupuesto 
          -> LIMIT 3;
      +--------------+-------------+
      | nombre       | presupuesto |
      +--------------+-------------+
      | Proyectos    |           0 |
      | Publicidad   |           0 |
      | Contabilidad |      110000 |
      +--------------+-------------+
      3 rows in set (0,00 sec)
      
      ```
    
18. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
        tienen mayor gasto.

      ```mysql
      mysql> SELECT d.nombre,d.gasto
          -> FROM departamento AS d
          -> ORDER BY gasto DESC
          -> LIMIT 2;
      +------------------+--------+
      | nombre           | gasto  |
      +------------------+--------+
      | I+D              | 380000 |
      | Recursos Humanos |  25000 |
      +------------------+--------+
      2 rows in set (0,01 sec)
      
      ```
    
19. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
        tienen menor gasto.

      ```mysql
      mysql> SELECT d.nombre,d.gasto
          -> FROM departamento AS d
          -> ORDER BY gasto 
          -> LIMIT 2;
      +------------+-------+
      | nombre     | gasto |
      +------------+-------+
      | Proyectos  |     0 |
      | Publicidad |  1000 |
      +------------+-------+
      2 rows in set (0,00 sec)
      
      ```
    
20. Devuelve una lista con 5 filas a partir de la tercera fila de la tabla empleado. La
        tercera fila se debe incluir en la respuesta. La respuesta debe incluir todas las
        columnas de la tabla empleado.

      ```mysql
      mysql> SELECT e.codigo,e.nif,e.nombre,e.apellido1,e.apellido2,e.codigo_departamento
          -> FROM empleado AS e
          -> LIMIT 5 OFFSET 2;
      +--------+-----------+---------+-----------+-----------+---------------------+
      | codigo | nif       | nombre  | apellido1 | apellido2 | codigo_departamento |
      +--------+-----------+---------+-----------+-----------+---------------------+
      |      3 | R6970642B | Adolfo  | Rubio     | Flores    |                   3 |
      |      4 | 77705545E | Adrián  | Suárez    | NULL      |                   4 |
      |      5 | 17087203C | Marcos  | Loyola    | Méndez    |                   5 |
      |      6 | 38382980M | María   | Santana   | Moreno    |                   1 |
      |      7 | 80576669X | Pilar   | Ruiz      | NULL      |                   2 |
      +--------+-----------+---------+-----------+-----------+---------------------+
      5 rows in set (0,01 sec)
      
      ```
    
21. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
        aquellos que tienen un presupuesto mayor o igual a 150000 euros.

      ```mysql
      mysql> SELECT d.nombre,d.presupuesto
          -> FROM departamento AS d
          -> WHERE presupuesto >= 150000;
      +------------------+-------------+
      | nombre           | presupuesto |
      +------------------+-------------+
      | Sistemas         |      150000 |
      | Recursos Humanos |      280000 |
      | I+D              |      375000 |
      +------------------+-------------+
      3 rows in set (0,00 sec)
      ```
    
22. Devuelve una lista con el nombre de los departamentos y el gasto, de
        aquellos que tienen menos de 5000 euros de gastos.

      ```mysql
      mysql> SELECT d.nombre,d.gasto
          -> FROM departamento AS d
          -> WHERE presupuesto <= 5000;
      +------------+-------+
      | nombre     | gasto |
      +------------+-------+
      | Proyectos  |     0 |
      | Publicidad |  1000 |
      +------------+-------+
      2 rows in set (0,00 sec)
      
      ```
    
23. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
        aquellos que tienen un presupuesto entre 100000 y 200000 euros. Sin
        utilizar el operador BETWEEN.

      ```mysql
      mysql> SELECT d.nombre,d.presupuesto
          -> FROM departamento AS d
          -> WHERE presupuesto >= 100000 AND presupuesto <= 200000; 
      +--------------+-------------+
      | nombre       | presupuesto |
      +--------------+-------------+
      | Desarrollo   |      120000 |
      | Sistemas     |      150000 |
      | Contabilidad |      110000 |
      +--------------+-------------+
      3 rows in set (0,01 sec)
      
      ```
    
24. Devuelve una lista con el nombre de los departamentos que no tienen un
        presupuesto entre 100000 y 200000 euros. Sin utilizar el operador BETWEEN.

      ```mysql
      SELECT d.nombre,d.presupuesto
      FROM departamento AS d
      WHERE NOT presupuesto >= 100000 AND presupuesto <= 200000; mysql> SELECT d.nombre,d.presupuesto
          -> FROM departamento AS d
          -> WHERE NOT presupuesto >= 100000 AND presupuesto <= 200000; 
      +------------+-------------+
      | nombre     | presupuesto |
      +------------+-------------+
      | Proyectos  |           0 |
      | Publicidad |           0 |
      +------------+-------------+
      2 rows in set (0,00 sec)
      ```
    
25. Devuelve una lista con el nombre de los departamentos que tienen un
        presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

      ```mysql
      mysql> SELECT d.nombre,d.presupuesto
          -> FROM departamento AS d
          -> WHERE presupuesto BETWEEN 100000 AND 200000; 
      +--------------+-------------+
      | nombre       | presupuesto |
      +--------------+-------------+
      | Desarrollo   |      120000 |
      | Sistemas     |      150000 |
      | Contabilidad |      110000 |
      +--------------+-------------+
      3 rows in set (0,00 sec)
      
      ```
    
26. Devuelve una lista con el nombre de los departamentos que no tienen un
        presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

      ```mysql
      mysql> SELECT d.nombre,d.presupuesto
          -> FROM departamento AS d
          -> WHERE NOT presupuesto BETWEEN 100000 AND 200000; 
      +------------------+-------------+
      | nombre           | presupuesto |
      +------------------+-------------+
      | Recursos Humanos |      280000 |
      | I+D              |      375000 |
      | Proyectos        |           0 |
      | Publicidad       |           0 |
      +------------------+-------------+
      4 rows in set (0,00 sec)
      
      ```
    
27. Devuelve una lista con el nombre de los departamentos, gastos y
        presupuesto, de aquellos departamentos donde los gastos sean mayores
        que el presupuesto del que disponen.

      ```mysql
      mysql> SELECT d.nombre,d.gasto, d.presupuesto
          -> FROM departamento AS d
          -> WHERE d.gasto > d.presupuesto;
      +------------+--------+-------------+
      | nombre     | gasto  | presupuesto |
      +------------+--------+-------------+
      | I+D        | 380000 |      375000 |
      | Publicidad |   1000 |           0 |
      +------------+--------+-------------+
      2 rows in set (0,00 sec)
      
      ```
    
28. Devuelve una lista con el nombre de los departamentos, gastos y
        presupuesto, de aquellos departamentos donde los gastos sean menores
        que el presupuesto del que disponen.

      ```mysql
      mysql> SELECT d.nombre,d.gasto, d.presupuesto
          -> FROM departamento AS d
          -> WHERE d.gasto < d.presupuesto;
      +------------------+-------+-------------+
      | nombre           | gasto | presupuesto |
      +------------------+-------+-------------+
      | Desarrollo       |  6000 |      120000 |
      | Sistemas         | 21000 |      150000 |
      | Recursos Humanos | 25000 |      280000 |
      | Contabilidad     |  3000 |      110000 |
      +------------------+-------+-------------+
      4 rows in set (0,00 sec)
      
      ```
    
29. Devuelve una lista con el nombre de los departamentos, gastos y
        presupuesto, de aquellos departamentos donde los gastos sean iguales al
        presupuesto del que disponen.

      ```mysql
      mysql> SELECT d.nombre,d.gasto, d.presupuesto
          -> FROM departamento AS d
          -> WHERE d.gasto = d.presupuesto;
      +-----------+-------+-------------+
      | nombre    | gasto | presupuesto |
      +-----------+-------+-------------+
      | Proyectos |     0 |           0 |
      +-----------+-------+-------------+
      1 row in set (0,00 sec)
      
      ```
    
30. Lista todos los datos de los empleados cuyo segundo apellido sea NULL.

        ```mysql
        mysql> SELECT e.apellido2
            -> FROM empleado AS e
            -> WHERE e.apellido2 IS NULL;
        +-----------+
        | apellido2 |
        +-----------+
        | NULL      |
        | NULL      |
        +-----------+
        2 rows in set (0,00 sec)
        
        ```

31. Lista todos los datos de los empleados cuyo segundo apellido no sea NULL.

        ```mysql
        mysql> SELECT e.apellido2
            -> FROM empleado AS e
            -> WHERE e.apellido2 IS NOT NULL;
        +-----------+
        | apellido2 |
        +-----------+
        | Gómez     |
        | Díaz      |
        | Flores    |
        | Méndez    |
        | Moreno    |
        | Santana   |
        | López     |
        | Salas     |
        | Gil       |
        | Flores    |
        | Guerrero  |
        +-----------+
        11 rows in set (0,01 sec)
        
        ```

32. Lista todos los datos de los empleados cuyo segundo apellido sea López.

        ```mysql
        mysql> SELECT e.apellido2
            -> FROM empleado AS e
            -> WHERE e.apellido2 ='López';
        +-----------+
        | apellido2 |
        +-----------+
        | López     |
        +-----------+
        1 row in set (0,00 sec)
        
        ```

33. Lista todos los datos de los empleados cuyo segundo apellido
        sea Díaz o Moreno. Sin utilizar el operador IN.

      ```mysql
      mysql> SELECT e.apellido2
          -> FROM empleado AS e
          -> WHERE e.apellido2 ='Díaz' OR e.apellido2 ='Moreno';
      +-----------+
      | apellido2 |
      +-----------+
      | Díaz      |
      | Moreno    |
      +-----------+
      2 rows in set (0,00 sec)
      
      ```
    
34. Lista todos los datos de los empleados cuyo segundo apellido
        sea Díaz o Moreno. Utilizando el operador IN.

      ```mysql
      mysql> SELECT e.apellido2
          -> FROM empleado AS e
          -> WHERE e.apellido2 IN ('Díaz','Moreno');
      +-----------+
      | apellido2 |
      +-----------+
      | Díaz      |
      | Moreno    |
      +-----------+
      2 rows in set (0,00 sec)
      
      ```
    
35. Lista los nombres, apellidos y nif de los empleados que trabajan en el
        departamento 3.

      ```mysql
      mysql> SELECT e.nombre,e.apellido1,e.apellido2,e.nif
          -> FROM empleado AS e
          -> WHERE codigo_departamento = 3;
      +--------+-----------+-----------+-----------+
      | nombre | apellido1 | apellido2 | nif       |
      +--------+-----------+-----------+-----------+
      | Adolfo | Rubio     | Flores    | R6970642B |
      | Pepe   | Ruiz      | Santana   | 71651431Z |
      +--------+-----------+-----------+-----------+
      2 rows in set (0,00 sec)
      
      ```
    
36. Lista los nombres, apellidos y nif de los empleados que trabajan en los
        departamentos 2, 4 o 5.

      ```mysql
      mysql> SELECT e.nombre,e.apellido1,e.apellido2,e.nif
          -> FROM empleado AS e
          -> WHERE codigo_departamento IN (2,4,5);
      +---------+-----------+-----------+-----------+
      | nombre  | apellido1 | apellido2 | nif       |
      +---------+-----------+-----------+-----------+
      | Adela   | Salas     | Díaz      | Y5575632D |
      | Adrián  | Suárez    | NULL      | 77705545E |
      | Marcos  | Loyola    | Méndez    | 17087203C |
      | Pilar   | Ruiz      | NULL      | 80576669X |
      | Juan    | Gómez     | López     | 56399183D |
      | Diego   | Flores    | Salas     | 46384486H |
      +---------+-----------+-----------+-----------+
      6 rows in set (0,00 sec)
      ```
    
      

## Consultas multitabla (Composición interna)

Resuelva todas las consultas utilizando la sintaxis de SQL1 y SQL2.

1. Devuelve un listado con los empleados y los datos de los departamentos
    donde trabaja cada uno.

```sql
SELECT e.nombre,e.codigo_departamento,d.codigo,d.nombre,d.presupuesto,d.gasto
FROM empleado AS e,departamento AS d
WHERE e.codigo_departamento = d.codigo;

Aarón|1|1|Desarrollo|120000.0|6000.0
Adela|2|2|Sistemas|150000.0|21000.0
Adolfo|3|3|Recursos Humanos|280000.0|25000.0
Adrián|4|4|Contabilidad|110000.0|3000.0
Marcos|5|5|I+D|375000.0|380000.0
María|1|1|Desarrollo|120000.0|6000.0
Pilar|2|2|Sistemas|150000.0|21000.0
Pepe|3|3|Recursos Humanos|280000.0|25000.0
Juan|2|2|Sistemas|150000.0|21000.0
Diego|5|5|I+D|375000.0|380000.0
Marta|1|1|Desarrollo|120000.0|6000.0

[Execution complete with exit code 0]
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
  
  Adrián|4|4|Contabilidad|110000.0|3000.0
  Marta|1|1|Desarrollo|120000.0|6000.0
  Aarón|1|1|Desarrollo|120000.0|6000.0
  María|1|1|Desarrollo|120000.0|6000.0
  Diego|5|5|I+D|375000.0|380000.0
  Marcos|5|5|I+D|375000.0|380000.0
  Adolfo|3|3|Recursos Humanos|280000.0|25000.0
  Pepe|3|3|Recursos Humanos|280000.0|25000.0
  Juan|2|2|Sistemas|150000.0|21000.0
  Pilar|2|2|Sistemas|150000.0|21000.0
  Adela|2|2|Sistemas|150000.0|21000.0
  
  [Execution complete with exit code 0]
  
  ```

3. Devuelve un listado con el identificador y el nombre del departamento,
    solamente de aquellos departamentos que tienen empleados.

  ```sql
  SELECT d.codigo,d.nombre
  FROM empleado AS e,departamento AS d
  WHERE e.codigo_departamento = d.codigo;
  
  1|Desarrollo
  2|Sistemas
  3|Recursos Humanos
  4|Contabilidad
  5|I+D
  1|Desarrollo
  2|Sistemas
  3|Recursos Humanos
  2|Sistemas
  5|I+D
  1|Desarrollo
  
  [Execution complete with exit code 0]
  
  ```

4. Devuelve un listado con el identificador, el nombre del departamento y el
     valor del presupuesto actual del que dispone, solamente de aquellos
       departamentos que tienen empleados. El valor del presupuesto actual lo
       puede calcular restando al valor del presupuesto inicial
       (columna presupuesto) el valor de los gastos que ha generado
       (columna gastos).

     ```sql
     SELECT d.codigo,d.nombre,(d.presupuesto - d.gasto) AS P_ACTUAL
     FROM empleado AS e,departamento AS d
     WHERE e.codigo_departamento = d.codigo;
     
     1|Desarrollo|114000.0
     2|Sistemas|129000.0
     3|Recursos Humanos|255000.0
     4|Contabilidad|107000.0
     5|I+D|-5000.0
     1|Desarrollo|114000.0
     2|Sistemas|129000.0
     3|Recursos Humanos|255000.0
     2|Sistemas|129000.0
     5|I+D|-5000.0
     1|Desarrollo|114000.0
     
     ```

5. Devuelve el nombre del departamento donde trabaja el empleado que tiene
     el nif 38382980M.

     ```sql
     SELECT d.nombre
     FROM empleado AS e,departamento AS d
     WHERE e.codigo_departamento = d.codigo AND e.nif IS '38382980M';
     
     Desarrollo
     
     [Execution complete with exit code 0]
     ```

6. Devuelve el nombre del departamento donde trabaja el empleado Pepe Ruiz
     Santana.

     ```sql
     SELECT d.nombre
     FROM empleado AS e,departamento AS d
     WHERE e.codigo_departamento = d.codigo AND e.nombre = 'Pepe' AND e.apellido1 = 'Ruiz' AND e.apellido2 = 'Santana';
     
     Recursos Humanos
     
     [Execution complete with exit code 0]
     ```

7. Devuelve un listado con los datos de los empleados que trabajan en el
     departamento de I+D. Ordena el resultado alfabéticamente.

     ```sql
     SELECT e.nombre
     FROM empleado AS e,departamento AS d
     WHERE e.codigo_departamento = d.codigo AND e.codigo_departamento = '5'
     ORDER BY e.nombre ASC;
     
     Diego
     Marcos
     
     [Execution complete with exit code 0]
     ```

8. Devuelve un listado con los datos de los empleados que trabajan en el
     departamento de Sistemas, Contabilidad o I+D. Ordena el resultado
       alfabéticamente.

     ```sql
     SELECT e.codigo,e.nif,e.nombre,e.apellido1,e.apellido2
     FROM empleado AS e,departamento AS d
     WHERE e.codigo_departamento = d.codigo AND e.codigo_departamento IN (2,4,5)
     ORDER BY e.nombre ASC;
     
     2|Y5575632D|Adela|Salas|Díaz
     4|77705545E|Adrián|Suárez|
     10|46384486H|Diego|Flores|Salas
     9|56399183D|Juan|Gómez|López
     5|17087203C|Marcos|Loyola|Méndez
     7|80576669X|Pilar|Ruiz|
     
     [Execution complete with exit code 0]
     ```

9. Devuelve una lista con el nombre de los empleados que tienen los
     departamentos que no tienen un presupuesto entre 100000 y 200000 euros.

     ```sql
     SELECT e.nombre
     FROM empleado AS e,departamento AS d
     WHERE e.codigo_departamento = d.codigo AND presupuesto NOT BETWEEN 100000 AND 200000;
     
     Adolfo
     Marcos
     Pepe
     Diego
     
     [Execution complete with exit code 0]
     ```

10. Devuelve un listado con el nombre de los departamentos donde existe
     algún empleado cuyo segundo apellido sea NULL. Tenga en cuenta que no
     debe mostrar nombres de departamentos que estén repetidos.

     ```sql
     SELECT DISTINCT d.nombre
     FROM empleado AS e,departamento AS d
     WHERE e.codigo_departamento = d.codigo AND e.apellido2 IS NULL;
     
     Contabilidad
     Sistemas
     
     [Execution complete with exit code 0]
     ```

     

## Consultas multitabla (Composición externa)

Resuelva todas las consultas utilizando las cláusulas LEFT JOIN y RIGHT JOIN.

1. Devuelve un listado con todos los empleados junto con los datos de los
  departamentos donde trabajan. Este listado también debe incluir los
  empleados que no tienen ningún departamento asociado.

  ```mysql
  mysql> SELECT e.nombre,d.nombre AS departamento
      -> FROM empleado AS e
      -> LEFT JOIN departamento AS d ON e.codigo_departamento = d.codigo; 
  +--------------+------------------+
  | nombre       | departamento     |
  +--------------+------------------+
  | Aarón        | Desarrollo       |
  | Adela        | Sistemas         |
  | Adolfo       | Recursos Humanos |
  | Adrián       | Contabilidad     |
  | Marcos       | I+D              |
  | María        | Desarrollo       |
  | Pilar        | Sistemas         |
  | Pepe         | Recursos Humanos |
  | Juan         | Sistemas         |
  | Diego        | I+D              |
  | Marta        | Desarrollo       |
  | Irene        | NULL             |
  | Juan Antonio | NULL             |
  +--------------+------------------+
  13 rows in set (0,00 sec)
  
  ```

2. Devuelve un listado donde sólo aparezcan aquellos empleados que no
  tienen ningún departamento asociado.

  ```mysql
  mysql> SELECT e.nombre,d.nombre AS departamento
      -> FROM empleado AS e
      -> LEFT JOIN departamento AS d ON e.codigo_departamento = d.codigo 
      -> WHERE e.codigo_departamento IS NULL; 
  +--------------+--------------+
  | nombre       | departamento |
  +--------------+--------------+
  | Irene        | NULL         |
  | Juan Antonio | NULL         |
  +--------------+--------------+
  2 rows in set (0,00 sec)
  
  ```

3. Devuelve un listado donde sólo aparezcan aquellos departamentos que no
  tienen ningún empleado asociado.

  ```mysql
  mysql> SELECT e.nombre,d.nombre AS departamento
      -> FROM empleado AS e
      -> RIGHT JOIN departamento AS d ON e.codigo_departamento = d.codigo 
      -> WHERE e.codigo_departamento IS NULL; 
  +--------+--------------+
  | nombre | departamento |
  +--------+--------------+
  | NULL   | Proyectos    |
  | NULL   | Publicidad   |
  +--------+--------------+
  2 rows in set (0,01 sec)
  
  ```

4. Devuelve un listado con todos los empleados junto con los datos de los
  departamentos donde trabajan. El listado debe incluir los empleados que no
  tienen ningún departamento asociado y los departamentos que no tienen
  ningún empleado asociado. Ordene el listado alfabéticamente por el
  nombre del departamento.

  ```mysql
  mysql> SELECT e.nombre,d.nombre AS departamento
      -> FROM empleado AS e
      -> LEFT JOIN departamento AS d ON e.codigo_departamento = d.codigo
      -> UNION
      -> SELECT e.nombre,d.nombre AS departamento
      -> FROM empleado AS e
      -> RIGHT JOIN departamento AS d ON e.codigo_departamento = d.codigo 
      -> WHERE e.codigo_departamento IS NULL;
  +--------------+------------------+
  | nombre       | departamento     |
  +--------------+------------------+
  | Aarón        | Desarrollo       |
  | Adela        | Sistemas         |
  | Adolfo       | Recursos Humanos |
  | Adrián       | Contabilidad     |
  | Marcos       | I+D              |
  | María        | Desarrollo       |
  | Pilar        | Sistemas         |
  | Pepe         | Recursos Humanos |
  | Juan         | Sistemas         |
  | Diego        | I+D              |
  | Marta        | Desarrollo       |
  | Irene        | NULL             |
  | Juan Antonio | NULL             |
  | NULL         | Proyectos        |
  | NULL         | Publicidad       |
  +--------------+------------------+
  15 rows in set (0,00 sec)
  
  ```

  

5. Devuelve un listado con los empleados que no tienen ningún departamento
  asociado y los departamentos que no tienen ningún empleado asociado.
  Ordene el listado alfabéticamente por el nombre del departamento.

  ```mysql
  mysql> SELECT e.nombre,d.nombre AS departamento
      -> FROM empleado AS e
      -> LEFT JOIN departamento AS d ON e.codigo_departamento = d.codigo
      -> UNION
      -> SELECT e.nombre,d.nombre AS departamento
      -> FROM empleado AS e
      -> RIGHT JOIN departamento AS d ON e.codigo_departamento = d.codigo 
      -> WHERE e.codigo_departamento IS NULL
      -> ORDER BY departamento ASC;
  +--------------+------------------+
  | nombre       | departamento     |
  +--------------+------------------+
  | Irene        | NULL             |
  | Juan Antonio | NULL             |
  | Adrián       | Contabilidad     |
  | Aarón        | Desarrollo       |
  | María        | Desarrollo       |
  | Marta        | Desarrollo       |
  | Marcos       | I+D              |
  | Diego        | I+D              |
  | NULL         | Proyectos        |
  | NULL         | Publicidad       |
  | Adolfo       | Recursos Humanos |
  | Pepe         | Recursos Humanos |
  | Adela        | Sistemas         |
  | Pilar        | Sistemas         |
  | Juan         | Sistemas         |
  +--------------+------------------+
  15 rows in set (0,00 sec)
  
  
  ```



## Consultas resumen

1. Calcula la suma del presupuesto de todos los departamentos.

   ```mysql
   mysql> SELECT SUM(d.presupuesto) AS presupuesto_de_todos_los_departamentos
       -> FROM departamento AS d;
   +----------------------------------------+
   | presupuesto_de_todos_los_departamentos |
   +----------------------------------------+
   |                                1035000 |
   +----------------------------------------+
   1 row in set (0,00 sec)
   
   ```

   

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





