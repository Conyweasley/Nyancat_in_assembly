# Trabajo de Laboratorio: VC FrameBuffer en QEMU emulando una RPi3

## Descripción

Este trabajo de laboratorio tiene como objetivo principal la comprensión y aplicación de conceptos de programación en lenguaje ensamblador ARMv8, a través de la manipulación del FrameBuffer de video en una Raspberry Pi 3 emulada mediante QEMU.
Este laboratorio proporciona una experiencia práctica en programación de bajo nivel y manejo de dispositivos gráficos, emulando una plataforma real de manera virtual.

## Objetivos:
* Escribir programas en ensamblador ARMv8.
* Comprender la interfaz de entrada/salida del microprocesador mediante una interfaz visual, manipulando píxeles en memoria.
* Simular el funcionamiento del FrameBuffer de la Raspberry Pi 3 usando el emulador QEMU debido a la imposibilidad de realizar pruebas físicas.

## Descripción del FrameBuffer:
El FrameBuffer es un método de acceso gráfico que representa cada píxel de la pantalla como una ubicación en el mapa de memoria principal. En la Raspberry Pi 3, la inicialización del FrameBuffer se realiza mediante un servicio especial llamado mailbox, que permite al CPU comunicarse con el Video Core (VC) y definir la memoria donde se almacenará el estado de cada píxel. La configuración utilizada es de 640x480 píxeles con un formato de color ARGB de 32 bits.

## Ejercicios:
* Ejercicio 1: Generación de imagen estática.
Se debe escribir un programa en ensamblador que cree una imagen estática utilizando al menos tres colores diferentes y dos figuras de distinta forma. La imagen debe ocupar toda la pantalla y no puede ser un patrón aleatorio.

* Ejercicio 2: Generación de figuras en movimiento.
Requiere un programa que muestre figuras en movimiento sobre un fondo no continuo, usando al menos tres colores y con una duración mínima de 10 segundos. Se permite reutilizar el código del primer ejercicio.


## Estructura

* Configuración de pantalla: `640x480` pixels, formato `ARGB` 32 bits.
* El registro `X0` contiene la dirección base del FrameBuffer (Pixel 1)
* **[app.s](app.s)** Este archivo contiene la apliación. Todo el hardware ya está inicializado anteriormente.
* **[start.s](start.s)** Este archivo realiza la inicialización del hardware
* **[Makefile](Makefile)** Archivo que describe como construir el software _(que ensamblador utilizar, que salida generar, etc)_
* **[memmap](memmap)** Este archivo contiene la descripción de la distribución de la memoria del programa y donde colocar cada sección.
* **README.md** este archivo

## Uso

El archivo _Makefile_ contiene lo necesario para construir el proyecto.

**Para correr el proyecto ejecutar**

```bash
$ make run
```
Esto construirá el código y ejecutará qemu para su emulación

REQUIRES:
1- SETTING UP AARCH64 TOOLCHAIN
$ sudo apt install gcc-aarch64-linux-gnu
2- SETTING UP QEMU ARM (incluye aarch64)
$ sudo apt install qemu-system-arm
3- FETCH AND BUILD AARCH64 GDB
$ sudo apt install gdb-multiarch

## Static
![preview_NyanCat](preview_NyanCat.png)

## Animation
![preview-NyanCat-Video](preview-NyanCat-Video.gif  )



