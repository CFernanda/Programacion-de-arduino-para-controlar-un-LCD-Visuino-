# Programación de Arduino, control de un LCD en Visuino-Visualino

### Introducción

Se puede hacer uso de diferentes softwares para la programación en arduino y todo lo que en el incluya, en este caso se utiliza el software Visuino para la programación de Arduino  y el control de un LCD.

### Objetivos

**General**

Aprender a utilizar el software Visuino para la programación de un arduino con el fin de poder controlar un LCD,  mediante el análisis y la investigación llegar a implementarlo en dicho software con  el fin de entender su funcionamiento y familiarizarnos  para utilizarlo en el transcurso de la carrera.

### Marco Teórico

**ARDUINO**

![1_arduino.png](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/1_arduino.png)

**Figura 1:** Arduino

Arduino es una plataforma de desarrollo basada en una placa electrónica de hardware libre que incorpora un microcontrolador re-programable y una serie de pines hembra. Estos permiten establecer conexiones entre el microcontrolador y los diferentes sensores y actuadores de una manera muy sencilla (principalmente con cables dupont).

**ARDUINO UNO**

La arduino Uno es una board basada en un microcontrolador Atmega328. Tiene 14 pines de entrada/salida digital (de los cuales 4 pueden ser utilizados para salidas PWM), 6 entradas análogas, un resonador cerámico de 16 MHz, un conector para USB tipo hembra, un Jack para fuente de Poder, un conector ICSP y un botón reset.

Parte Frontal
Tiene todo lo necesario para manejar el controlador, simplemente conectamos al computador por medio del cable USB o una fuente de poder externa, que puede ser un adaptador AC-DC  o una batería, cabe aclarar que si se alimenta a través del cable USB en el ordenador no es necesario una fuente externa.

![2_arduinoplaca.png](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/2_arduinoplaca.png)

**Figura 2:** Arduino uno

Para programar la board se necesita el IDE Arduino.

**Características**

- Microcontrolador: ATmega328
- Voltaje Operativo: 5v
- Voltaje de Entrada (Recomendado): 7 – 12 v
- Pines de Entradas/Salidas Digital: 14 (De las cuales 6 son salidas PWM)
- Pines de Entradas Análogas: 6
- Memoria Flash: 32 KB (ATmega328) de los cuales 0,5 KB es usado por Bootloader.
- SRAM: 2 KB (ATmega328)
- EEPROM: 1 KB (ATmega328)
- Velocidad del Reloj: 16 MHZ.

**Partes**

![3_partes.jpg](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/3_partes.jpg)

**Figura 3:** Partes del Arduino

**LCD**

El uso de las LCD se ha visto muy requerido tanto en la industria como en los proyectos escolares o de medianas empresas, ya que su uso es bastante agradable a la vista, aunque muchos de nosotros estamos acostumbrados a escuchar dichas siglas y pensar en una pantalla para TV o el display de un ordenador, mientras que los display LCD tienen una gama más abierta de aplicaciones, desde relojes, calculadoras, electrodomésticos, impresoras, etc.

**Qué es una LCD?**

Las siglas LCD significan “Liquid Cristal Display” ó pantalla de cristal líquido. Es una pantalla plana basada en el uso de una sustancia liquida atrapada entre dos placas de vidrio, haciendo pasar por este una corriente eléctrica a una zona especifica, para que así esta se vuelva opaca, y además cuenta (generalmente) con iluminación trasera.
Las pantallas LCD de color, cada pixel individual se divide en tres cédulas o sub pixeles con los colores RGB (Rojo, Verde y Azul) respectivamente. Y así cada pixel puede controlarse para  producir una gran variedad de colores distintos.
 
**Características de las LCD**

Existen una gran variedad de proyectos en los que se incluye una LCD para interfaz con el usuario, lo que modifica las necesidades, las cuales es importante atender más que nada por los precios. Y la importancia de esta en el proyecto.
Algunos factores básicos a considerar en una LCD son:

* Tamaño: El tamaño de un panel LCD generalmente se mide a lo lardo de su diagonal, expresado generalmente en pulgadas. Sin embargo existen más características que pueden describir las dimensiones aproximadas, como por ejemplo la LCD 16×2 (negro sobre fondo azul) se refiere a que tiene la capacidad de tener al mismo tiempo 16 caracteres de manera horizontal en dos renglones (cada uno).

* Resolución: Esta se expresa con las dimensiones horizontal y vertical. las pantallas HD tienen una resolución de 1920×1080 por ejemplo. Y esta puede alcanzar con esta resolución una gran variedad de tamaño, pero si no se ocupa gran a gran detalle esta, estarías desperdiciando calidad (por no utilizar algo que tienes disponible). En 5hz se maneja, por ejemplo la LCD gráfica 128×64 (negro sobre fondo verde). Que a pesar de su tamaño la consideramos suficiente para las aplicaciones estudiantiles, y algunas industriales donde se requiera tener algo claro y legible en un tamaño práctico.

* Brillo: La luminosidad de la pantalla también es importante analizarla, ya que según la aplicación en la que se encuentre esta, requerirá más luz para poder apreciarse, o viceversa. Por lo que la mayoría cuentan con una luz trasera y la posibilidad de poder controlar su luminosidad.

* Iluminación CCFL: Esta iluminación básicamente consta poner detrás de la pantalla una matriz de CCFL, o bien en las orillas o bordes de la pantalla. Sin embargo es más consumo que el led y tiene un menor tiempo de vida, por lo que poco a poco se ah ido poniendo en segundo plano.
Iluminación LED Esta iluminación puede presentarse en dos maneras, en un solo color, (generalmente blanco) o bien en RGB, los blanco suelen ser los más utilizados. Estos al igual que la iluminación CCFL, pueden estar formando una matriz en la parte de atrás, o bien pueden colocarse a los extremos del display.
 
* Contraste:Es la relación entre la intensidad más brillante y la más oscura.

* Angulo de visión: es el ángulo máximo en el que el usuario puede visualizar lo que está en la LCD sin que se pierda mucha calidad.
Número de caracteres. Hay diversos tamaños de LCD y con ello nos limitamos o nos expandamos la posibilidad de mostrar en el display cierto número de caracteres, los tamaños estándar que manejamos son: 16×2, 20×4, 8×2.

![4_LCD.png](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/4_LCD.png)

**Figura 4:** Características de LCD

**Ejemplo de comunicación**
 
1 Conexión.

Tomaremos como ejemplo un display LCD 16×2 (negro sobre fondo azul). Para el control de esta Arduino tiene una librería llamada LiquidCrystal la cual te permite controlar LCD que sean compatibles con el driver Hitachi HD44780. Sin embargo nosotros la modificaremos un poco para que diga 5hz electrónica.

2 Pines.

El pin “RS” controla en que parte de la memoria LCD se están escribiendo los datos. Es aquí donde se mantiene la información que sale en la pantalla, o donde el controlador de esta busca los siguientes datos a mostrar.
El pin de “lectura/escritura”(R/W) selecciona el modo de lectura o de escritura.
 EL pin para habilitar “enable”, este habilita los registros.
8 pines de datos “D00-D07”, Los estados de estos pines son bits que estás escribiendo en un registro, o valores que estás leyendo.
Existe un pin “de contraste” del display.
Existe un pin “de retro-iluminación” (Bklt+ y Bklt-) que le permiten controlar la retroiluminación.
Pin de alimentación (+5V y GND).

3 Circuito.

- El pin “RS” del LCD conectado a la E/S digital en el pin 12.
– El pin “enable” del LCD conectado a la E/S digital en el pin 11. 
– Los pines “D4 – D7” conectado a las E/S digitales desde el pin 5 hasta el 2. 
– Los pines de voltaje y tierra conectados a +5V y tierra.
– El pin “Vo”, que controla el constraste, conectado a un potenciómetro. 
Ajusta el potenciómetro para que el texto tenga el contraste que tú quieras.

![5_paraleloArduinoLCD.png](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/5_paraleloArduinoLCD.png)                                             ![6_esquema-LCD1-300x192.png]( https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/6_esquema-LCD1-300x192.png
) 

**Figura 5:** Diagrama de conexión en paraleo Arduino y LCD.          **Figura 6:** Esquema de conexión Arduino y LCD.

**VISUINO**

![7_Visuino.png]( https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/7_Visuino.png)

**Figura 7:** Visuino

Visuino es el último software innovador de Mitov Software. Un entorno de programación visual que le permite programar sus placas Arduino. Actualmente es compatible con las placas oficiales Arduino, Raspberry Pi, Teensy, Femto IO, ESP8266, ESP32, Controllino, Goldilocks Analogue, FreeSoC2, chipKIT, micro: bit, Maple Mini y la cantidad de clones Arduino, sin embargo, no se limita a su soporte solo y las solicitudes de soporte de nuevo hardware son bienvenidas.

Los componentes que se encuentran en el software Visuino representan sus componentes de hardware y podrá crear y diseñar sus programas fácilmente con la función de arrastrar y soltar. No se necesita equipo ni hardware para ejecutar el software en modo de diseño. Una vez que haya completado el diseño, puede conectar la carga de la placa Arduino y ejecutarla.

![8_visuino.png]( https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/8_visuino.png)

**Figura 8:** Entorno de Visuino

 **VISUALINO**
 
 ![Visualino_logo.jpg](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/Visualino_logo.jpg)
 
 **Figura 9:** Visualino
  
Entorno de programación visual para Arduino,permite hacer un programa con bloques tipo scratch y ver el código que se genera, como de un traductor de bloques a código se tratara. Pero además, permite programar directamente la placa de Arduino y por tanto, hace innecesaria la conexión permanente al PC.

Los bloques generan el código de C/C++ en tiempo real en una ventana. El entorno es similar al del IDE de Arduino, con las mismas opciones principales: Verificar, Subir, Guardar, Cargar y Monitor.

![entorno%20visualino.JPG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/entorno%20visualino.JPG)

### BIBLIOGRAFÍAS
http://arduino.cc/
https://www.visuino.com/
