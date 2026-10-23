# 5toRojo-ClaudioCarbonara
Pensamiento Computacional
Clase 1 Verificacion de GitHub
Clase 3 proyecto de Tinker card 
Tuvimos que hacer un trabajo en físico sobre distancias en la cual debíamos calcular qué distancia era más corta y el porqué 
Despuws de ello tuvimos que hacer dos trabajos en tinker cardo sobre unas luces que pared de en cierto tiempo

Trabajo uno con 6 led:
https://www.tinkercad.com/things/5NQAf6lvy5q/editel

2
​
3
int led1 = 4;
4
int led2 = 5;
5
int led3 = 6;
6
int led4 = 7;
7
int led5 = 8;
8
int led6 = 9;
9
​
10
int boton = 2;
11
bool activado = false;
12
​
13
void setup()
14
{
15
 pinMode(led1, OUTPUT);
16
 pinMode(led2, OUTPUT);
17
 pinMode(led3, OUTPUT);
18
 pinMode(led4, OUTPUT);
19
 pinMode(led5, OUTPUT);
20
 pinMode(led6, OUTPUT);
21
​
22
 pinMode(boton, INPUT_PULLUP);
23
}
24
​
25
void loop()
26
{
27
 if (digitalRead(boton) == LOW)
28
 {
29
   activado = true;
30
 }
31
​
32
 if (activado == true)
33
 {
34
   digitalWrite(led1, HIGH);
35
   digitalWrite(led2, HIGH);
36
   digitalWrite(led3, HIGH);
37
   digitalWrite(led4, HIGH);
38
   digitalWrite(led5, HIGH);
39
   digitalWrite(led6, HIGH);
40
​
41
   delay(8000);
42
​
43
   digitalWrite(led1, LOW);
44
   digitalWrite(led2, LOW);
45
   digitalWrite(led3, LOW);
46
   digitalWrite(led4, LOW);
47
   digitalWrite(led5, LOW);
48
   digitalWrite(led6, LOW);
49
​
50
   delay(8000);




   Trabajo 2
   https://www.tinkercad.com/things/aBqEUeuQoxM/editel
   1
// C++ code
2
//
3
​
4
int ledrojo = 4;
5
int ledverde = 5;
6
int interruptor = 2;
7
​
8
void setup()
9
{
10
  pinMode(ledrojo, OUTPUT);
11
  pinMode(ledverde, OUTPUT);
12
  pinMode(interruptor, INPUT_PULLUP);
13
}
14
​
15
void loop()
16
{
17
  if (digitalRead(interruptor) == LOW)
18
  {
19
    digitalWrite(ledrojo, HIGH);
20
    digitalWrite(ledverde, LOW);
21
​
22
    delay(1000);
23
​
24
    digitalWrite(ledrojo, LOW);
25
    digitalWrite(ledverde, HIGH);
26
​
27
    delay(1000);
28
  }
29
  else
30
  {
31
    digitalWrite(ledrojo, LOW);
32

   digitalWrite(ledverde, LOW);
33
  }
34
}

Foto
<img width="1280" height="960" alt="d3a51a99-4d2a-44c7-b715-43c80c5a7718" src="https://github.com/user-attachments/assets/c827a9be-f3fc-40ad-b6be-c716cc5bd99d" />


Actividad 4 pensamiento computacional 
Proyecto: Indicador de disponibilidad de un espacio
 
1. ¿Cuál es el problema?
 
A veces las personas no saben si una salón para estudiar está ocupado o disponible, lo que puede causar interrupciones.
 
2. ¿Quién se beneficiaría de la solución?
 
Los estudiantes y profesores que utilizan espacios para estudiar o trabajar.
 
3. ¿Cómo ayudará el prototipo?
 
Mediante un interruptor que permite señalar manualmente si el espacio está ocupado o disponible. El Arduino recibirá esa información y encenderá una luz roja cuando esté ocupado o una verde cuando esté disponible.


 
1 (Arduino Uno R3)


1
// C++ code
2
//
3
int ledRojo = 8;
4
int ledVerde = 9;
5
int interruptor = 2;
6
​
7
void setup() {
8
 pinMode(ledRojo, OUTPUT);
9
 pinMode(ledVerde, OUTPUT);
10
 pinMode(interruptor, INPUT_PULLUP);
11
}
12
​
13
void loop() {
14
 int estado = digitalRead(interruptor);
15
​
16
 if (estado == LOW) {
17
   digitalWrite(ledRojo, HIGH);
18
   digitalWrite(ledVerde, LOW);
19
 } else {
20
   digitalWrite(ledRojo, LOW);
21
   digitalWrite(ledVerde, HIGH);
22
 }
23
}
Clase 4 pensamiento computacional: Ejercicio 1
Llegada de estudiantes: Generación y registro del evento de llegada (estampa de tiempo / timestamp), asignación de un identificador único (ticket) y detección inicial si el estudiante pertenece a un grupo prioritario.
Registro y categorización del trámite: Identificación del tipo de trámite a realizar (Entrega de documentos, Solicitud de constancia o Consulta general), lo cual determinará el tiempo estimado de servicio.
Gestión de colas y prioridades: Organización de los estudiantes en la fila de espera utilizando una estructura de datos adecuada (como una cola con prioridad) que equilibre el orden de llegada (FIFO) con la urgencia/prioridad.
Atención en ventanilla: Asignación del estudiante que encabeza la cola a la ventanilla única, cálculo del tiempo transcurrido en espera y procesamiento del trámite según su duración.
Cierre de atención y métricas: Salida del estudiante del sistema, registro de métricas individuales (tiempo de espera, tiempo de servicio) y actualización de promedios para evaluación del desempeño del centro.

Campo	Tipo de Dato	Descripción
id_estudiante	Texto / Entero	Identificador único o matrícula del estudiante.
numero_ticket	Entero	Número de turno asignado al llegar.
tipo_tramite	Cadena de texto	Categórico: "Entrega", "Constancia", "Consulta".
es_prioritario	Booleano	VERDADERO si aplica condición prioritaria (discapacidad, adultos mayores, etc.), FALSO en caso contrario.
hora_llegada	Tiempo / Entero	Momento exacto en que ingresa al sistema (segundos/minutos).
hora_inicio_atencion	Tiempo / Entero	Momento en que pasa a la ventanilla.
hora_fin_atencion	Tiempo / Entero	Momento en que finaliza su trámite.
tiempo_estimado	Entero	Duración aproximada del trámite según su tipo.

ALGORITMO SistemaGestionVentanilla

ESTRUCTURA Estudiante
    id_estudiante : TEXTO
    numero_ticket : ENTERO
    tipo_tramite : TEXTO
    es_prioritario : BOOLEANO
    hora_llegada : ENTERO
    tiempo_estimado : ENTERO
FIN_ESTRUCTURA

INICIO
    // Inicialización de variables
    ColaPrioritaria = CREAR_COLA()
    ColaRegular = CREAR_COLA()
    contador_tickets = 0
    ventanilla_ocupada = FALSO
    
    MIENTRAS centro_atencion_abierto HACER
        
        // --- 1 y 2. LLEGADA Y REGISTRO ---
        SI estudiante_llega() ENTONCES
            contador_tickets = contador_tickets + 1
            nuevo_estudiante = CREAR(Estudiante)
            nuevo_estudiante.numero_ticket = contador_tickets
            nuevo_estudiante.id_estudiante = LEER_ID()
            nuevo_estudiante.tipo_tramite = LEER_TRAMITE()
            nuevo_estudiante.es_prioritario = LEER_PRIORIDAD()
            nuevo_estudiante.hora_llegada = OBTENER_TIEMPO_ACTUAL()
            
            // Asignar tiempo estimado según tipo de trámite
            SEGÚN nuevo_estudiante.tipo_tramite HACER
                CASO "Constancia": nuevo_estudiante.tiempo_estimado = 3  // Rápido
                CASO "Entrega":    nuevo_estudiante.tiempo_estimado = 5  // Medio
                CASO "Consulta":   nuevo_estudiante.tiempo_estimado = 10 // Largo
            FIN_SEGÚN
            
            // --- 3. CLASIFICACIÓN EN COLAS ---
            SI nuevo_estudiante.es_prioritario ES VERDADERO ENTONCES
                ENCOLAR(ColaPrioritaria, nuevo_estudiante)
            SINO
                ENCOLAR(ColaRegular, nuevo_estudiante)
            FIN_SI
        FIN_SI

        // --- 4. ATENCIÓN EN VENTANILLA ---
        SI ventanilla_ocupada ES FALSO ENTONCES
            SI NO ESTA_VACIA(ColaPrioritaria) ENTONCES
                siguiente = DESENCOLAR(ColaPrioritaria)
                ATENDER_ESTUDIANTE(siguiente)
            SINO SI NO ESTA_VACIA(ColaRegular) ENTONCES
                siguiente = DESENCOLAR(ColaRegular)
                ATENDER_ESTUDIANTE(siguiente)
            FIN_SI
        FIN_SI

        // --- 5. CIERRE Y LIBERACIÓN ---
        SI ventanilla_completo_tramite_actual() ENTONCES
            ventanilla_ocupada = FALSO
            REGISTRAR_METRICAS(siguiente.hora_llegada, OBTENER_TIEMPO_ACTUAL())
        FIN_SI

    FIN_MIENTRAS
FIN

PROCEDIMIENTO ATENDER_ESTUDIANTE(estudiante)
    ventanilla_ocupada = VERDADERO
    tiempo_inicio = OBTENER_TIEMPO_ACTUAL()
    tiempo_espera = tiempo_inicio - estudiante.hora_llegada
    IMPRIMIR "Atendiendo ticket: ", estudiante.numero_ticket, " Tiempo espera: ", tiempo_espera
FIN_PROCEDIMIENTO

Prioridad Absoluta (Legal/Social): Estudiantes con discapacidad, embarazadas o condiciones especiales van directos a la ColaPrioritaria. Se atienden bajo la regla FIFO dentro de su grupo.
Prioridad por Tipo de Trámite (Cola Regular): Para la cola general, se aplica una ordenación secundaria basada en la técnica SJF (Shortest Job First / El trabajo más corto primero) combinada con tiempo máximo de espera.
Orden de rapidez: 1° Solicitud de constancia (rápido) → 2° Entrega de documentos (medio) → 3° Consulta general (largo).
Justificación
Reducción del tiempo promedio de espera: Resolver primero los trámites rápidos (como la solicitud de constancias) desahoga con mayor velocidad la cantidad total de personas en la fila, lo que baja significativamente el tiempo de espera medio del sistema.
Equidad e inclusión: Garantiza la atención preferente a personas con necesidades prioritarias sin vulnerar las normativas institucionales.
Prevención de hambruna (starvation): Al mantener el orden estricto de llegada dentro de cada subcategoría y limitar cuántos trámites rápidos pueden adelantarse seguidos a una consulta general, se evita que las consultas largas queden postergadas indefinidamente.

EJERCICIO 2

Cantidad de Estudiantes por Parada
Escuela (E): Punto de origen/salida y destino final.
Parada 1 (P 
1
​	
 ): 4 estudiantes
Parada 2 (P 
2
​	
 ): 6 estudiantes
Parada 3 (P 
3
​	
 ): 3 estudiantes
Parada 4 (P 
4
​	
 ): 8 estudiantes
Parada 5 (P 
5
​	
 ): 5 estudiantes
Parada 6 (P 
6
​	
 ): 2 estudiantes
Total de estudiantes a recoger: 28 estudiantes.
Matriz de Distancias (km)
Desde / Hacia	Escuela (E)	P 
1
​	
 	P 
2
​	
 	P 
3
​	
 	P 
4
​	
 	P 
5
​	
 	P 
6
​	
 
Escuela (E)	0	2.5	4.0	7.5	6.0	8.5	5.0
Parada 1 (P 
1
​	
 )	2.5	0	2.0	5.5	4.5	7.0	4.0
Parada 2 (P 
2
​	
 )	4.0	2.0	0	3.5	3.0	5.5	4.5
Parada 3 (P 
3
​	
 )	7.5	5.5	3.5	0	2.5	3.0	6.0
Parada 4 (P 
4
​	
 )	6.0	4.5	3.0	2.5	0	3.5	3.0
Parada 5 (P 
5
​	
 )	8.5	7.0	5.5	3.0	3.5	0	4.5
Parada 6 (P 
6
​	
 )	5.0	4.0	4.5	6.0	3.0	4.5	0

 Paso 1 (Inicio): Comenzar en el nodo inicial, en este caso la Escuela (E). Marcar la Escuela como visitada.
Paso 2 (Evaluación de candidatos): Revisar las distancias desde el nodo actual hacia todas las paradas que no han sido visitadas aún.
Paso 3 (Selección voraz): Seleccionar la parada no visitada que tenga la menor distancia desde la posición actual.
Paso 4 (Actualización): Avanzar hacia esa parada, sumando su distancia al recorrido acumulado y marcándola como visitada.
Paso 5 (Repetición): Repetir los Pasos 2, 3 y 4 hasta que las 6 paradas hayan sido visitadas.
Paso 6 (Retorno): Una vez recogidas las 6 paradas, regresar a la Escuela (E) para completar el circuito o finalizar la entrega de estudiantes.

Desde E: Distancias a no visitados →P 
1
​	
 (2.5), P 
2
​	
 (4.0), P 
3
​	
 (7.5), P 
4
​	
 (6.0), P 
5
​	
 (8.5), P 
6
​	
 (5.0).
Elige P 
1
​	
  (distancia 2.5 km). Acumulado: 2.5 km.
Desde P 
1
​	
 : Distancias a no visitados →P 
2
​	
 (2.0), P 
3
​	
 (5.5), P 
4
​	
 (4.5), P 
5
​	
 (7.0), P 
6
​	
 (4.0).
Elige P 
2
​	
  (distancia 2.0 km). Acumulado: 4.5 km.
Desde P 
2
​	
 : Distancias a no visitados →P 
3
​	
 (3.5), P 
4
​	
 (3.0), P 
5
​	
 (5.5), P 
6
​	
 (4.5).
Elige P 
4
​	
  (distancia 3.0 km). Acumulado: 7.5 km.
Desde P 
4
​	
 : Distancias a no visitados →P 
3
​	
 (2.5), P 
5
​	
 (3.5), P 
6
​	
 (3.0).
Elige P 
3
​	
  (distancia 2.5 km). Acumulado: 10.0 km.
Desde P 
3
​	
 : Distancias a no visitados →P 
5
​	
 (3.0), P 
6
​	
 (6.0).
Elige P 
5
​	
  (distancia 3.0 km). Acumulado: 13.0 km.
Desde P 
5
​	
 : Distancias a no visitados →P 
6
​	
 (4.5).
Elige P 
6
​	
  (distancia 4.5 km). Acumulado: 17.5 km.
Regreso a la Escuela (E): Desde P 
6
​	
  a E son 5.0 km.
Llegada a E: Acumulado final: 22.5 km.
Ruta Propuesta (Ruta A - Vecino Más Cercano)
Escuela→P 
1
​	
 →P 
2
​	
 →P 
4
​	
 →P 
3
​	
 →P 
5
​	
 →P 
6
​	
 →Escuela
Distancia Total Recorrida: 22.5 km.

Rutas Evaluadas
Ruta A (Algoritmo Vecino Más Cercano):
Sequence: E→P 
1
​	
 →P 
2
​	
 →P 
4
​	
 →P 
3
​	
 →P 
5
​	
 →P 
6
​	
 →E
Distancias: 2.5+2.0+3.0+2.5+3.0+4.5+5.0=22.5 km
Ruta B (Alternativa Perimetral / Geográfica):
Se visita primero la zona exterior y luego se regresa haciendo un bucle.
Sequence: E→P 
6
​	
 →P 
4
​	
 →P 
5
​	
 →P 
3
​	
 →P 
2
​	
 →P 
1
​	
 →E
Distancias: 5.0+3.0+3.5+3.0+3.5+2.0+2.5=22.5 km
Ruta C (Orden Numérico Secuencial Ineficiente):
Sequence: E→P 
1
​	
 →P 
2
​	
 →P 
3
​	
 →P 
4
​	
 →P 
5
​	
 →P 
6
​	
 →E
Distancias: 2.5+2.0+3.5+2.5+3.5+4.5+5.0=23.5 km
Tabla Comparativa
Criterio / Parámetro	Ruta A (Propuesta)	Ruta B (Alternativa Perimetral)	Ruta C (Secuencial Directa)
Distancia total	22.5 km	22.5 km	23.5 km
Tiempo total estimado (a 30 km/h prom.)	45 min	45 min	47 min
Número de paradas	6 paradas	6 paradas	6 paradas
Estudiantes en paradas iniciales	4+6=10 (35.7%)	2+8=10 (35.7%)	4+6=10 (35.7%)
Conclusión y Justificación
Bajo el criterio de Menor Distancia / Menor Tiempo: Las Rutas A y B son óptimas e iguales en recorrido (22.5 km), superando a la Ruta C por 1 km de ahorro.
Elección Recomendada (Ruta A): La Ruta A es superior en la práctica operativa escolar porque recoge a 18 de los 28 estudiantes (64%) en las primeras 3 paradas (P 
1
​	
 ,P 
2
​	
 ,P 
4
​	
 ), reduciendo el tiempo total acumulado que la mayoría de los niños pasan dentro del vehículo en movimiento.
Criterio de paradas: Dado que todas las opciones deben recoger obligatoriamente a los estudiantes en las 6 paradas fijadas por la institución, el número de paradas es constante (6), por lo que el factor determinante es la minimización de la distancia/tiempo.

EJERCICIO 3

Error de cálculo en el promedio: El código original solo suma las calificaciones (nota1 + nota2 + nota3) pero nunca las divide entre la cantidad de notas (3). Esto provoca que el resultado esté en una escala de hasta 300 puntos, alterando por completo la condición de aprobación (>= 60).
Falta de validación de datos: No existe ningún filtro para comprobar si las calificaciones ingresadas son lógicas. Si el usuario introduce números negativos o mayores a 100, el algoritmo los procesará de igual forma.
Falta de información (Limitación): El programa emite un veredicto de aprobación, pero no muestra al estudiante cuál fue su promedio numérico, dejándolo sin saber su calificación final exacta.

2 y 3. Corrección del Pseudocódigo y Validación de Notas (0 a 100)
Para solucionar el cálculo y asegurar que las notas estén dentro del rango válido de 0 a 100, se incorpora una estructura de control repetitiva (MIENTRAS) que filtra los datos erróneos antes de procesarlos.

El 2
Cuál era el problema original?
En el ejercicio original, el código decía: promedio = nota1 + nota2 + nota3.
Si un estudiante sacaba 80 en cada materia, el resultado de esa suma era 240. ¡Un promedio jamás puede ser mayor que las notas individuales! El error era que sumaba las notas pero nunca las dividía entre la cantidad total de notas.
¿Cómo se corrigió?
Para obtener un promedio real, la regla matemática es sumar todos los valores y dividirlos entre el número de elementos. Como son tres notas, la fórmula correcta debe incluir la división entre 3 y usar paréntesis para el orden de las operaciones:promedio = (nota1 + nota2 + nota3) / 3
De esta forma, si las tres notas son 80, la suma da 240, al dividirla entre 3 el promedio resultante es 80, lo cual sí es correcto.

El 3
Para qué sirve?
En la vida real, un profesor o un sistema escolar no puede aceptar notas negativas (como -10) ni notas imposibles (como 1500). La validación es un filtro de seguridad para asegurarnos de que los datos ingresados sean lógicos.
¿Cómo funciona en el algoritmo?
Para lograr esto, utilizamos un bucle (MIENTRAS). El funcionamiento paso a paso es el siguiente:
El sistema pide las tres notas.
Revisa una por una con una condición estricta: que la nota 1 esté entre 0 y 100, que la nota 2 esté entre 0 y 100, y que la nota 3 también lo esté.
Si todas son correctas: El programa continúa su camino hacia el cálculo del promedio.
Si tan solo una nota está mal (por ejemplo, si alguien escribe 105 por error): El programa muestra un mensaje de error y vuelve a repetir todo el proceso desde el inicio, obligando al usuario a escribir las notas de nuevo hasta que sean válidas.

Se añadieron dos mejoras clave al diseño final:
Visualización del promedio: Se imprime el valor numérico exacto de la nota final.
Estado de recuperación: Se incluyó un rango intermedio (entre 50 y 59) para indicar si el estudiante tiene derecho a un examen de recuperación antes de suspender definitivamente.

ALGORITMO CalcularPromedioEstudiante

INICIO
    // Declaración de variables
    REAL nota1, nota2, nota3, promedio
    BOOLEAN notas_validas
    
    notas_validas = FALSO
    
    // TAREA 3: Validación para que las notas estén entre 0 y 100
    MIENTRAS notas_validas == FALSO HACER
        ESCRIBIR "Ingrese las tres notas (valores entre 0 y 100):"
        LEER nota1, nota2, nota3
        
        SI (nota1 >= 0 Y nota1 <= 100) Y (nota2 >= 0 Y nota2 <= 100) Y (nota3 >= 0 Y nota3 <= 100) ENTONCES
            notas_validas = VERDADERO
        SINO
            ESCRIBIR "Error: Una o mas notas estan fuera del rango permitido (0 a 100). Intente de nuevo."
        FIN_SI
    FIN_MIENTRAS
    
    // TAREA 2: Corrección del cálculo del promedio (Suma dividida entre la cantidad de notas)
    promedio = (nota1 + nota2 + nota3) / 3
    
    // TAREA 4: Mejora adicional (Mostrar promedio e indicar recuperación)
    ESCRIBIR "El promedio final es: ", promedio
    
    SI promedio >= 60 ENTONCES
        ESCRIBIR "Estado: Aprueba"
    SINO SI promedio >= 50 Y promedio < 60 ENTONCES
        ESCRIBIR "Estado: Debe presentar recuperacion"
    SINO
        ESCRIBIR "Estado: No aprueba (Reprobado)"
    FIN_SI

FIN


