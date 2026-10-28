# Tenis distribuido – Sistemas Informáticos Industriales

**Autor:** Santiago Carazo Pintado (matrícula 55777)
**Asignatura:** Sistemas Informáticos Industriales – ETSIDI, UPM (curso 2026-2027)

## Descripción

Juego de tenis en C++ con OpenGL y GLUT para dos jugadores. A lo largo de las prácticas evolucionará hasta poder jugarse en red entre dos ordenadores, con un proceso logger, un bot y comunicación por sockets.

## Controles

- Raqueta izquierda: `w` (arriba) y `s` (abajo)
- Raqueta derecha: `o` (arriba) y `l` (abajo)

## Compilación y ejecución

    cd workspace
    mkdir build
    cd build
    cmake ..
    make
    ./logger
    (abrir otra terminal)
    ./tenis

## Funcionalidades por práctica

- **Práctica 1:** movimiento de las raquetas y de la pelota.
- **Práctica 2:** Comunicación mediante tuberías con nombre (FIFO)
	- Nuevo programa `logger` que crea una tubería con nombre (`/tmp/FIFO_LOGGER`), la lee en un bucle y muestra los mensajes por pantalla.
	- El juego `tenis` abre la tubería en escritura en `CMundo::Init()`, envía un mensaje cada vez que un jugador marca un punto (en `OnTimer()`) y la cierra en el destructor.
	- La partida termina cuando un jugador llega a 3 puntos: se cierra el tenis y, al detectar el cierre de la tubería, el logger también termina.