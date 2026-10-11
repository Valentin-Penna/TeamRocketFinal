# Team Rocket · ASTI Robotics Challenge 25/26

Un robot de menos de 140 € que tenía que valer para todo: seguir una línea contrarreloj, pelear en sumo, tirar bolos, dibujar figuras y trabajar en una mini fábrica manejado con un mando de PS5. Este es el código con el que nuestro equipo se presentó al ASTI Robotics Challenge 2025/26.

El dinero lo sacamos imprimiendo piezas en 3D y limpiando ordenadores. El presupuesto final fue de 138,75 €.

## El robot

- Chasis Osoyoo con cuatro motores y ruedas Mecanum.
- Arduino Mega 2560 con un escudo wifi ESP8266.
- Sensores de línea por infrarrojos, ultrasonidos HC-SR04 y un servomotor.

La construcción, las pruebas y el presupuesto están en [la presentación del equipo](TeamRocket_presentacion.pdf).

## Las pruebas principales

**Sigue líneas.** Un control PID con dos ajustes: uno agresivo para las curvas cerradas y otro suave para las rectas. El robot pasa de uno a otro por tiempo, según el tramo del circuito en el que esté.

**Sumo y bolos.** Una máquina de estados: buscar, atacar y escapar. Lleva ultrasonidos delante y detrás, así que puede embestir en los dos sentidos sin darse la vuelta. Los sensores del suelo mandan sobre todo lo demás: si ven el borde, el robot corta el ataque y se aparta.

**DibujaBot.** El robot traza un triángulo, un cuadrado o un rectángulo. Los tiempos de cada lado y de cada giro se ajustan desde una ventana en el ordenador (Python con Tkinter) que se los manda por wifi, sin tener que volver a cargar el programa en el Arduino.

**Mini fábrica y circuito manual.** Aquí conduce una persona. Un script en Python lee el mando de PS5 con pygame y envía las órdenes por UDP a la wifi del robot. Incluye el control de la pinza y de la puerta.

## Cómo está organizado

Cada carpeta (`David`, `Valentin`, `Yori`) guarda el trabajo de un miembro del equipo. Hay varias versiones de la misma prueba porque íbamos probando ajustes distintos y comparando en la pista.

- Los `.ino` se cargan en el Arduino Mega desde el IDE de Arduino.
- Los `.py` se ejecutan en un ordenador conectado a la wifi del robot. Los del mando necesitan `pygame`.
- `INICIO_MANDO_GENERICO.py` deja el robot en espera y lo arranca al pulsar la X del mando.
