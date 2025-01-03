# Trabajo de Laboratorio: VC FrameBuffer en QEMU emulando una RPi3

## Descripción



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



