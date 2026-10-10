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


