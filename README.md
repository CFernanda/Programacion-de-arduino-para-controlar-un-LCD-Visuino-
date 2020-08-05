# Programación de Arduino, control de un LCD en Visuino-Visualino

### Introducción

Se puede hacer uso de diferentes softwares para la programación en arduino y todo lo que en el incluya, en este caso se utiliza el software Visuino para la programación de Arduino  y el control de un LCD.

### Objetivos

**General**

Aprender a utilizar el software Visuino para la programación de un arduino con el fin de poder controlar un LCD,  mediante el análisis y la investigación llegar a implementarlo en dicho software con  el fin de entender su funcionamiento y familiarizarnos  para utilizarlo en el transcurso de la carrera.

### Marco Teórico

**ARDUINO UNO**
La arduino Uno es una board basada en un microcontrolador Atmega328. Tiene 14 pines de entrada/salida digital (de los cuales 4 pueden ser utilizados para salidas PWM), 6 entradas análogas, un resonador cerámico de 16 MHz, un conector para USB tipo hembra, un Jack para fuente de Poder, un conector ICSP y un botón reset.

Parte Frontal
Tiene todo lo necesario para manejar el controlador, simplemente conectamos al computador por medio del cable USB o una fuente de poder externa, que puede ser un adaptador AC-DC  o una batería, cabe aclarar que si se alimenta a través del cable USB en el ordenador no es necesario una fuente externa.

![1_arduinoplaca.png](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/1_arduinoplaca.png)

**Figura 1:** Arduino uno

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

**Figura 2:** Partes del Arduino

**LCD**
**Qué es una LCD?**

Las siglas LCD significan “Liquid Cristal Display” ó pantalla de cristal líquido. Es una pantalla plana basada en el uso de una sustancia liquida atrapada entre dos placas de vidrio, haciendo pasar por este una corriente eléctrica a una zona especifica, para que así esta se vuelva opaca, y además cuenta (generalmente) con iluminación trasera.
Las pantallas LCD de color, cada pixel individual se divide en tres cédulas o sub pixeles con los colores RGB (Rojo, Verde y Azul) respectivamente. Y así cada pixel puede controlarse para  producir una gran variedad de colores distintos.
 
**Características de las LCD**

* Tamaño: El tamaño de un panel LCD generalmente se mide a lo lardo de su diagonal, expresado generalmente en pulgadas. Sin embargo existen más características que pueden describir las dimensiones aproximadas, como por ejemplo la LCD 16×2 (negro sobre fondo azul) se refiere a que tiene la capacidad de tener al mismo tiempo 16 caracteres de manera horizontal en dos renglones (cada uno).

* Resolución: Esta se expresa con las dimensiones horizontal y vertical. las pantallas HD tienen una resolución de 1920×1080 por ejemplo. Y esta puede alcanzar con esta resolución una gran variedad de tamaño, pero si no se ocupa gran a gran detalle esta, estarías desperdiciando calidad (por no utilizar algo que tienes disponible). En 5hz se maneja, por ejemplo la LCD gráfica 128×64 (negro sobre fondo verde). Que a pesar de su tamaño la consideramos suficiente para las aplicaciones estudiantiles, y algunas industriales donde se requiera tener algo claro y legible en un tamaño práctico.

* Brillo: La luminosidad de la pantalla también es importante analizarla, ya que según la aplicación en la que se encuentre esta, requerirá más luz para poder apreciarse, o viceversa. Por lo que la mayoría cuentan con una luz trasera y la posibilidad de poder controlar su luminosidad.

* Iluminación CCFL: Esta iluminación básicamente consta poner detrás de la pantalla una matriz de CCFL, o bien en las orillas o bordes de la pantalla. Sin embargo es más consumo que el led y tiene un menor tiempo de vida, por lo que poco a poco se ah ido poniendo en segundo plano.
Iluminación LED Esta iluminación puede presentarse en dos maneras, en un solo color, (generalmente blanco) o bien en RGB, los blanco suelen ser los más utilizados. Estos al igual que la iluminación CCFL, pueden estar formando una matriz en la parte de atrás, o bien pueden colocarse a los extremos del display.
 
* Contraste:Es la relación entre la intensidad más brillante y la más oscura.

* Angulo de visión: es el ángulo máximo en el que el usuario puede visualizar lo que está en la LCD sin que se pierda mucha calidad.
Número de caracteres. Hay diversos tamaños de LCD y con ello nos limitamos o nos expandamos la posibilidad de mostrar en el display cierto número de caracteres, los tamaños estándar que manejamos son: 16×2, 20×4, 8×2.

![4_LCD.png](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/4_LCD.png)

**Figura 3:** Características de LCD

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

![5_paraleloArduinoLCD.png](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/5_paraleloArduinoLCD.png)                                                                                           ![6_esquema-LCD1-300x192.png]( https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/6_esquema-LCD1-300x192.png
) 

**Figura 4:** Diagrama de conexión en paraleo Arduino y LCD.          **Figura 5:** Esquema de conexión Arduino y LCD.

**VISUINO**

![7_Visuino.png]( https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/7_Visuino.png)

**Figura 6:** Visuino

Visuino es el último software innovador de Mitov Software. Un entorno de programación visual que le permite programar sus placas Arduino. Actualmente es compatible con las placas oficiales Arduino, Raspberry Pi, Teensy, Femto IO, ESP8266, ESP32, Controllino, Goldilocks Analogue, FreeSoC2, chipKIT, micro: bit, Maple Mini y la cantidad de clones Arduino, sin embargo, no se limita a su soporte solo y las solicitudes de soporte de nuevo hardware son bienvenidas.

Los componentes que se encuentran en el software Visuino representan sus componentes de hardware y podrá crear y diseñar sus programas fácilmente con la función de arrastrar y soltar. No se necesita equipo ni hardware para ejecutar el software en modo de diseño. Una vez que haya completado el diseño, puede conectar la carga de la placa Arduino y ejecutarla.

![8_visuino.png]( https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/8_visuino.png)

**Figura 7:** Entorno de Visuino

 **VISUALINO**
 
 ![9_visualino.jpg](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/9_visualino.jpg)
 
 **Figura 8:** Visualino
  
Entorno de programación visual para Arduino,permite hacer un programa con bloques tipo scratch y ver el código que se genera, como de un traductor de bloques a código se tratara. Pero además, permite programar directamente la placa de Arduino y por tanto, hace innecesaria la conexión permanente al PC.

Los bloques generan el código de C/C++ en tiempo real en una ventana. El entorno es similar al del IDE de Arduino, con las mismas opciones principales: Verificar, Subir, Guardar, Cargar y Monitor.

![10_entorno%20visualino.JPG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/10_entorno%20visualino.JPG)

 **Figura 9:** Entorno Visualino
 
 ## Manual de Usuario
 
**Descarga e Instalación de Visualino**

Para controlar un LCD con Visualino lo primero que se debe hacer es descargar el software Visualino en http://www.visualino.net/index.es.html

* Se abre la pantalla que se muestra a continuación.

![11_Plataforma%20visualino.JPG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/11_Plataforma%20visualino.JPG) 

**Figura 10:** Página de Visualino 

* En la parte inferior de la página se encuentra la opcion para descargar.

![12_VisualinoDescarga.jpg](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/12_VisualinoDescarga.jpg) 

**Figura 11:** Descarga de Visualino 

* Damos click en la el gráfico de la descarga y se abre una nueva pantalla, que permitira elegir para que tidpo de sistema operativo se necesita descargar damos click en el que necesitemos y se despliega una nueva ventana donde muestras las versiones que tiene **Visualino** por lo general la última es la que más actualizada se encuentra.

![13_descargas_pasos.jpg](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/13_descargas_pasos.jpg) 

**Figura 12:** Ventanas de Descarga

* Se descargará un archivo comprimido Figura 13 el mismo que al descomprimir se mostrará una nueva carpeta mostrada en la Figura 14 con todo lo que arduino trae.

![14_CARPETA.PNG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/14_CARPETA.PNG)![15_Visualino.PNG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/15_Visualino.PNG)  

**Figura 13:** Archivo comprimido en Carpeta                  **Figura 14:** Archivo Descomprimido en Carpeta 
 
 * En la carpeta se encontrará el compilador como se muestra en la Figura 15,  si se desea se puede crear un acceso directo en el escritorio, Figura 16  para hacer fácil su ingreso, caso contrario dando doble click en el compilador ya se tiene el software Visualino para trabajar.
 
 
![16_Compilador.JPG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/16_Compilador.JPG)
 
  **Figura 15:** Compilador
 
![17_%20Escritorio.JPG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/17_%20Escritorio.JPG)
 
 **Figura 16:** Acceso directo en Escritorio 
  
  * Como se vio en la Figura 16 el Software se abre y esta listo para usarse,el entorno para trabajar es el mostrado a continuación en la Figura 17.
  * Al ingresar en visualino tenemos en la parte izquierda los bloques con diferentes funciones el area para crear el codigo de los bloques y en la parte derecha esta una hoja en la que se va a ir formando el codigo de bloques en C++. como se vio en la figuran
 
 ![19_Area%20de%20trabajo.JPG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/19_Area%20de%20trabajo.JPG)
 
  **Figura 17:** Entorno de Visualino

**Control de la LCD**
  
**CÓDIGO**

* Para hacer el control de una LCD en el programa visualino se utiliza los bloques directos de LCD 

![20_LCD.PNG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/20_LCD.PNG)

**Figura 18:** Bloques para LCD
  
 - LCD (2x16): En este bloque se puede ingresar el número de pines con los que se va a trabajar
 
 - LCD IMPRIMIR: con ayuda de otro tipo de funciones como las de **"TEXTO"** se ingresa el mensaje que se desea imprimir, ademas permite escoger en que fila o columna va a ir el mensaje.
 
 - El cuarto bloque controla la iluminación.
 
A l iniciar en el Visualino se tiene el bloque de incio y repetir en la primera para el LCD  como se muestra en la figura 18  en la parte de inicio entra el codigo para  dar inico al programa y en repetir todo lo que queremos que la pantalla LCD repita.  

- Por lo cual en la figura 19 se muestra el código cuando queremos que el mensaje que enviemos al inicio sea estático y durará por 1s estara en la parte de Inicio.

![20_PARTE%20DE%20INICIO.PNG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/20_PARTE%20DE%20INICIO.PNG)

**Figura 19** Codigo para mensaje estático.

Como podemos ver solo se utiliza adicional al bloque de imprimir, bloques de texto para el mensaje, matemáticaspara definir las filas y columnas y un bloque controlador para el tiempo que necesitemos el mensaje.

- En la figura 20 se muestra el codigo para la LCD genere un mensaje que sea repetitivo por un tiempo teniendo en cuento que esto debe estar en la parte de Repetir.

![20_PARTE%20DE%20INICIO1.PNG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/20_PARTE%20DE%20INICIO1.PNG)
![20_PARTE%20DE%20INICIO2.PNG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/20_PARTE%20DE%20INICIO2.PNG)

**Figura 20:** Codigo para que un mensaje sea repetitivo.

Como se ve en esta ocasión se requiere de bloques de control que permitan realizar lo que en progrmacion basica se conoce como bucles FOR para que el mensaje sea repetitivo,bloques de texto para el mensaje, matemáticaspara definir las filas.
 y columnas y un bloque controlador para el tiempo que necesitemos el mensaje. 

Finalmente el código queda así como se muestra en la figura 21

![codigoCompleto.png](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/codigoCompleto.png)

**Figur 21:** Codigo completo, muestra un mensaje estático por un tiempo y luego un mensaje repetivo en constaste movimiento.

**Circuito en Tinkercad**

Para comprobar que el código funciona se debe armar el circuito con el arduino y la LCD, cargar el codigo dando click en el botòn subir y nos mostrara lo que se programó.
Entonces en la plataforma TINKERCAD se arma el circuito figura 22 teniendo en cuenta lo pines a trabajar y los pines que van a tierra y a VCC.

![23_Circuito%20LCD.PNG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/23_Circuito%20LCD.PNG)

**Figura 22:** Circuito armado en Tinkercad.

El potenciómetro se utiliza para regular el contraste de la pantalla y la resistencia es de protección.
En la parte superior Izquierda se encuentra una pestaña que doice **Código** y junto  ell **Iniciar simulación** damos click en **Código** y se nos abre una ventana donde debemos ingresar el codigo que se hizo en  visualino.

![24_entornoTINKERCAD.png](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/24_entornoTINKERCAD.png)

**Figura 23:** Botones de Código e iniicar simulación.

![25_Codigo_tinkercad.PNG](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/25_Codigo_tinkercad.PNG)

**Figura 24**: Código de visualino copiado en tinkercad

una vez ingresado el código damos click en el botón **iniciar la simulación**  y se puede visualizar el mensaje.

![26_Mensaje%20en%20la%20LCD.png](https://github.com/CFernanda/Programacion-de-arduino-para-controlar-un-LCD-Visuino-/blob/master/IMG/26_Mensaje%20en%20la%20LCD.png)


**Figura 25:** LCD controlado por arduino.

### BIBLIOGRAFÍAS
http://arduino.cc/
https://www.visuino.com/


