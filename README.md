# Robotica 

Nombre: Victorio
Apellido: Paskevicius
DNI: 48.074.409
Correo Electrónico: vpaskevicius@escuelasproa.edu.ar
(url) de la cuenta personal de github: https://github.com/victorioPaskevicius/Robotica.git

Nombre: Leonel
Apellido: Soto
DNI: 48.537.499
Correo Electrónico: lasoto@escuelasproa.edu.ar
(url) de la cuenta personal de github: leonel12341234

Nombre: Morena
Apellido: Ledesma
DNI: 48.130.190
Correo Electrónico: moledesma@escuelasproa.edu.ar
(url) de la cuenta personal de github: morenaaaledesma


Proyecto:

Plan de Proyecto:
El plan de nuestro proyecto es crear un auto de epoca, hecho con la impresora 3D.
Las funciones que debe realizar son poder moverse en varias direcciones con un control remoto. Esto lo lograremos con el software Arduino.

Arquitectura Física - Sensores:
Debe estar compuesto por el chasis que sera lo que se impimira por impresora 3D, con soportes diseñados para alojar la placa Arduino, baterías, sensores y otros componentes electrónicos. Las ruedas pueden ser impresas o compradas, pero deben estar conectadas con el motor para que tenga funcionamiento.


Detalle de Sensores a Utilizar
Encoder rotativo: Acoplado a los motores para medir la rotación de las ruedas, permitiendo controlar la velocidad o la distancia recorrida con precisión.

Circuito Electrónico:
Montaje

Paso 1. Conectamos los cables en los motores y los sujetamos al chasis. Primero conectamos los cables rojos y negros a los dos motores que tenemos. Los podemos soldar a los bornes metálicos de los motores o utilizar cinta aislante, asegurándonos de que el contacto con el borne es correcto. Para sujetar los motores en el chasis utilizamos las piezas rectangulares y los tornillos.

Colocación de los motores al chasis del robot
Montaje del chasis con los dos motores eductores.
Paso 2. Montamos la rueda loca y el soporte para las pilas. La rueda loca es una rueda sin tracción que gira libremente; el soporte de pilas lo utilizaremos para colocar las cuatro pilas AA encargadas de alimentar la placa Arduino.

Colocación en el chasis de la rueda loca y el portapilas
Colocamos en el chasis la rueda loca y el portapilas.
Paso 3. Colocamos el interruptor. El interruptor lo usaremos para el módulo controlador de motores L298N. Podemos insertarlo en el hueco que hay en medio del chasis.

En el paso 3 colocamos el interruptor que nos va a permitir dar energia al controlador de motores.
Interruptor con sus cables colocado en el chasis.
Paso 4. Colocar la placa de Arduino.

Colocamos la placa Arduino en el chasis.
Chasis con la placa Arduino colocada en la zona delantera.
Paso 5. Colocar el módulo controlador de motores L298N en la zona trasera del chasis. Una vez colocado, unimos los cables de los motores a los correspondientes pines del módulo.

Chasis con el controlador L298N en la zona trasera.
Chasis con el controlador L298N para los motores.
Paso 6. Colocamos la pila de 9V que alimentará al módulo controlador.

Pila de 9V para alimentar el controlador de los motores
Pila de 9V para alimentar el módulo controlador.
Utilizaremos la pila de 9 V como fuente de alimentación del módulo L298N; el cable rojo irá a la entrada de alimentación del módulo y el cable de tierra al GND del controlador y al GND de la placa Arduino.

Paso 7. Conectamos la placa de Arduino con el módulo controlador L298N.

Los pines van conectados en el siguiente orden:

ENA –> Pin 10 (cable verde en la imagen). Debemos recordar que los pines ENA y ENB son los que controlan la velocidad de giro.
ENB –> Pin 5 (cable verde)
IN1 –> Pin 9 (cable naranja)
IN2 –> Pin 8 (cable azul)
IN3 –> Pin 7 (cable azul)
IN4 –> Pin 6 (cable naranja)
Colocamos los cables que conectan la placa Arduino y el controlador L298N.
Colocamos los bables que conectan la placa y el controlador.
Paso 8. Probamos los motores. Una vez que tenemos en el chasis: la placa de Arduino, el controlador L298N, la pila de 9V para alimentar el controlador, el portapilas de 4 pilas para alimentar el Arduino, los motores con sus respectivas ruedas y el interruptor montado; podemos probar los motores y si el giro de las ruedas es el correcto.

Este código para probar el giro de los motores no incluye la biblioteca, sin embargo, si preferís utilizar la biblioteca, mirad el tutorial funcionamiento del módulo controlador de motores L29.

// Motor 1
int ENA = 10;
int IN1 = 9;
int IN2 = 8;

// Motor 2
int ENB = 5;
int IN3 = 7;
int IN4 = 6;

void setup() {
 pinMode (ENA, OUTPUT);
 pinMode (ENB, OUTPUT);
 pinMode (IN1, OUTPUT);
 pinMode (IN2, OUTPUT);
 pinMode (IN3, OUTPUT);
 pinMode (IN4, OUTPUT);  
}

void loop() {
  Adelante();
  delay(5000);
  Atras();
  delay(5000);
  Derecha();
  delay(5000);
  Izquierda();
  delay(5000);
  Parar();
  delay(5000);
}

void Adelante (){
 //Dirección motor A
 digitalWrite (IN1, LOW);
 digitalWrite (IN2, HIGH);
 analogWrite (ENA, 100); //Velocidad motor A
 //Dirección motor B
 digitalWrite (IN3, HIGH);
 digitalWrite (IN4, LOW);
 analogWrite (ENB, 100); //Velocidad motor B
}

void Derecha (){
 //Dirección motor A
 digitalWrite (IN1, HIGH);
 digitalWrite (IN2, LOW);
 analogWrite (ENA, 255); //Velocidad motor A
 //Dirección motor B
 digitalWrite (IN3, HIGH);
 digitalWrite (IN4, LOW);
 analogWrite (ENB, 255); //Velocidad motor A
}

void Izquierda (){
 //Dirección motor A
 digitalWrite (IN1, LOW);
 digitalWrite (IN2, HIGH);
 analogWrite (ENA, 255); //Velocidad motor A
 //Dirección motor B
 digitalWrite (IN3, LOW);
 digitalWrite (IN4, HIGH);
 analogWrite (ENB, 255); //Velocidad motor A
}

void Atras (){
 //Dirección motor A
 digitalWrite (IN1, HIGH);
 digitalWrite (IN2, LOW);
 analogWrite (ENA, 255); //Velocidad motor A
 //Dirección motor B
 digitalWrite (IN3, LOW);
 digitalWrite (IN4, HIGH);
 analogWrite (ENB, 255); //Velocidad motor B
}

void Parar (){
 //Dirección motor A
 digitalWrite (IN1, LOW);
 digitalWrite (IN2, LOW);
 analogWrite (ENA, 0); //Velocidad motor A
 //Dirección motor B
 digitalWrite (IN3, LOW);
 digitalWrite (IN4, LOW);
 analogWrite (ENB, 0); //Velocidad motor A
}

Diseño de elementos y soportes 3D:
Ford Mustang 1969

Programas - Código fuente Backend (atras) (MySQL - Python - Arduino - Git -)
arduino
