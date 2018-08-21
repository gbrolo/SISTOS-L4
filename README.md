# SISTOS-L4
Universidad del Valle de Guatemala
Sistemas Operativos, S.10 2018 - Laboratorio 4

## Archivos
En la carpeta ```/files```.

## Respuestas

1. ¿Cuál es el propósito de los archivos sched.h modificados?
Sirven para manejar las calendarizaciones en Linux. Existen distintos tipos de calendarizaciones y por eso cada una tiene valores distintos por que esos valores son los que el sistema llama.

2. ¿Cuál es el propósito de la definición incluida y las definiciones existentes en el archivo?
```SCHED_NORMAL``` realiza una calendarizacion normal CFS, ```SCHED_FIFO``` utiliza un stack para calendarizar, ```SCHED_RR``` utiliza Round Robbin, ```SCHED_BATCH``` utiliza varios chunks de memoria para calendarizar y la definicion incluida creara un nuevo proceso de calendarizacion con los parametros que le definamos.

3. ¿Qué es una task en Linux?
En Linux no existen tasks; generalmente una task se refiere a un proceso o un thread interno en el Kernel de Linux. En ocasiones se refiere a las tareas que los procesos deben de correr.

4. ¿Cuál es el propósito de task_struct y cuál es su análogo en Windows?
```task_struct``` es un elemento de la lista de tasks y su proposito es contener la estructura de los descriptores de los procesos, para que el kernel sepa como se conforman los procesos que seran corridos. Su analogo en Windows son las estructuras de registros para el kernel de Windows NT.

5. ¿Qué información contiene sched_param?
Contiene los parametros para la calendarizacion a implementar.

6. ¿Qué tipo de tareas calendariza la póliza EDF?
Calendariza tareas en tiempo real.

7. ¿Para qué sirve la función rt_policy y para qué sirve la llamada unlikely en ella?
Sirve para elegir la poliza a emplear; la llamada sirve para diferenciar que tipo de poliza se quiere implementar, si es FIFO o Round Robbin.

8. Indique la precedencia de prioridades para las pólizas EDF, RT y CFS, de acuerdo con los cambios realizados hasta ahora.
Ya que CASIO emplea RT, esta tendra la prioridad mas alta, luego seguira EDF y por ultimo CFS.

9. Explique el contenido de la estructura casio_task.
Se define primero la estructura de los nodos que usara la poliza. Luego, se define un espacio long para el deadline en el que el proceso deberia completarse. Asimismo, se define una estructura para la lista de cabezas y la lista de nodos que tendra el proceso, asi como una lista de tasks. 

10. Explique el propósito de la estructura casio_rq.
Se define primero una estructura raiz y luego las listas de cabezas de rq y de las cabezas de CASIO.

11. ¿Qué indica el campo .next de esta estructura?
Indica el siguiente task que debera ejecutarse en la poliza.

12. Tomando   en   cuenta las   funciones para   manejo   de   lista y red-black tree de casio_tasks, explique el ciclo de vida de una casio_task desde el momento en el que  se  le  asigna  esta  clase  de  calendarización  mediante sched_setscheduler.  El objetivo es que indique el orden y los escenarios en los que se ejecutan estas funciones, así   como   las   estructuras   de   datos   por   las   que   pasa.   ¿Por   qué se guardan   las casio_tasks en un red-black tree y en una lista encadenada?
Primero se debera hacer la llamada a la task y posteriormente se debera hacer un enqueue para alocar la memoria para la task a ejecutar como parte del proceso. Esto se obtiene de la lista de tareas definida y esta task se pasa luego a un red black tree para ir ordenando los procesos segun el tiempo en el que deba irse cumpliendo. Asi, se va llenando el red black tree con la informacion de la lista, utilizando las funciones para saber que task ir colocando y en que orden. Luego se llama a dequeue para liberar la task en cuestion, hasta que el arbol queda vacio.

13. ¿Cuándo preemptea una casio_task a la task actualmente en ejecución?
Cuando el tiempo de la task actualmente en ejecucion sobrepasa el tiempo que esta definido para que la casio_task se ejecute.

14. ¿Qué información contiene el archivo system que se especifica como argumento en la ejecución de casio_system?
Contiene la informacion del kernel y configuracion del sistema host en el que se esta ejecutando el programa, con el fin de obtener todas las listas de tareas de los procesos que actualmente se ejecutan en el sistema.

### Screenshots
![1](https://github.com/gbrolo/SISTOS-L3/blob/master/img/1.PNG)
![2](https://github.com/gbrolo/SISTOS-L3/blob/master/img/2.PNG)
![3](https://github.com/gbrolo/SISTOS-L3/blob/master/img/3.PNG)
![4](https://github.com/gbrolo/SISTOS-L3/blob/master/img/4.PNG)
![5](https://github.com/gbrolo/SISTOS-L3/blob/master/img/5.PNG)
![6](https://github.com/gbrolo/SISTOS-L3/blob/master/img/6.PNG)
![7](https://github.com/gbrolo/SISTOS-L3/blob/master/img/7.PNG)
![8](https://github.com/gbrolo/SISTOS-L3/blob/master/img/8.PNG)
![9](https://github.com/gbrolo/SISTOS-L3/blob/master/img/9.PNG)
![10](https://github.com/gbrolo/SISTOS-L3/blob/master/img/10.PNG)
![11](https://github.com/gbrolo/SISTOS-L3/blob/master/img/11.PNG)
![12](https://github.com/gbrolo/SISTOS-L3/blob/master/img/12.PNG)
![13](https://github.com/gbrolo/SISTOS-L3/blob/master/img/13.PNG)
![14](https://github.com/gbrolo/SISTOS-L3/blob/master/img/14.PNG)
![15](https://github.com/gbrolo/SISTOS-L3/blob/master/img/15.PNG)
![16](https://github.com/gbrolo/SISTOS-L3/blob/master/img/16.PNG)
![17](https://github.com/gbrolo/SISTOS-L3/blob/master/img/17.PNG)
