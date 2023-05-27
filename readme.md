# redox-handwired-3dp
## Contenido / Content
- [redox-handwired-3dp](#redox-handwired-3dp)
  - [Contenido / Content](#contenido--content)
- [ES](#es)
  - [Materiales](#materiales)
  - [Pasos a seguir](#pasos-a-seguir)
  - [QMK](#qmk)
    - [Instalación](#instalación)
    - [Configuración](#configuración)
    - [Cargar firmware](#cargar-firmware)
  - [VIAL](#vial)
- [EN](#en)
  - [Materials needed:](#materials-needed)
  - [Steps](#steps)
- [Referencias / References](#referencias--references)

![my-redox](https://i.imgur.com/6SMD83O.jpeg)
![other-redox](https://i.imgur.com/jXOqhLl.jpeg)
# ES
Hice un Redox Handwired siguiendo todas las referencias que encontré pero se me hizo coomo que estaba todo muy disperso o poco explicado, así que voy a explicar cómo hacerlo.
 
## Materiales
* 70x: Switches compatibles con Cherry.  
* 70x: Diodos (1N4148).  
* 70x: Keycaps compatible con Cherry.  
  * 10x (8x para layout 1u): 1.25u keycaps.  
  * 6x: 1.5u keycaps.  
  * 54x (56x para layout 1u): 1u keycaps.  
* 14x: tornillos M3 8mm.  
* 2x: 3.5 mm plug de 3 polos.  
* 2x: Arduino pro micros.  
* A lot of cable
* A lot of soldering

## Pasos a seguir
1. Imprimir plates. Se puede elegir que sean todas 1u, yo imprimí ese. [link](https://www.thingiverse.com/thing:2704567/files).  
2. Poner switches con el "huequito" mirando para abajo.
3. Imprimir el case mientras haces el resto.
4. Soldar segun muestra el [Buildlog](https://i.imgur.com/WoZ36il.jpeg). Conectar todo excepto la conexión entre los dos arduinos. Eso se conecta en [serial](https://github.com/qmk/qmk_firmware/blob/master/docs/feature_split_keyboard.md). [Imagen](https://user-images.githubusercontent.com/2170248/92296490-2d15cb00-ef70-11ea-801f-5ace313013e6.JPG).  
5. Poner el plate con el case.   

Ahora solo queda configurar [QMK](#qmk), compilarlo y ponerlo en el arduino izquierdo. 

Si queres usar VIAL, podes hacerlo salteando este paso y siguiendo los pasos de [VIAL](#vial).

## QMK 
### Instalación  
[Docs instalación](https://docs.qmk.fm/#/newbs_getting_started).  
1. Instalar [VS Code](https://code.visualstudio.com/download).  
2. Instalar [QMK MSYS](https://msys.qmk.fm/).
3. Abrir QMK MSYS. Correr `qmk setup`. Te va a pedir clonar el repositorio, lo clonas.
4. Te pregunta si queres cambiar el directorio principal de QMK, escribis `y` + enter.
5. Te pregunta si queres instalar las dependencias, escribis `y` + enter.  

### Configuración 
6. En `qmk_firmware/keyboards/redox` va a estar la configuración de tu teclado.
7. Escribir lo siguiente en la consola de QMK MSYS.
   1. `qmk config user.keyboard=redox/rev1`
   2. `qmk config user.keymap=default`
8. En `qmk-firmware/keyboards/redox/rev1/config.h` agregar `#define SPLIT_HAND_PIN D2`
9.  Modificar `qmk_firmware/keyboards/redox/keymaps/default/keymap.c` a gusto, te podes guiar con la [documentación](https://docs.qmk.fm/#/keycodes).   
10. Escribir `qmk compile -kb redox -km default` + enter, en QMK MSYS.

### Cargar firmware
Instalar [QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases/tag/0.2.2). Si te pide instalar drivers, instalalos. 

En ``qmk_firmware/`` va a quedar un archivo llamado ``redox_rev1_default.hex`` o algo parecido, lo importante es que sea un archivo .hex. 

* Abrimos QMK Toolbox, 
* seleccionamos el archivo, 
* seleccionamos atmega32u4, 
* marcamos Auto-Flash, 
* conectamos el teclado y hacemos puente con algo que sea conductivo (el estanio por ejemplo) entre estos dos [pines](https://www.shellhacks.com/wp-content/uploads/arduino_pro_micro_reset_pins.jpg).  
Te tendria que aparecer un texto amarillo en el QMK Toolbox, cuando te aparezca el segundo tecto amarillo que dice algo como: ``Atmel DFU dive disconected (libusb0): ...``  

LISTO! Ya tenes tu teclado. Cuando quieras cambiar la configuración del QMK, lo cambias en `qmk_firmware/keyboards/redox/keymaps/default/keymap.c`, lo volves a compilar (`10. `) y lo volves a [Cargar](#cargar-firmware).  

## VIAL
in process  

---
# EN
in process 

## Materials needed:
* 70x: Cherry compatible switches.  
* 70x: Diodes (1N4148).  
* 70x: Cherry compatible keycaps.  
  * 10x (8x for 1u Layout): 1.25u keycaps.  
  * 6x: 1.5u keycaps.  
  * 54x (56x for 1u Layout): 1u keycaps.  
* 14x: M3 8mm screws.  
* 2x: 3 poles 3.5 mm plug.  
* 2x: Arduino pro micros.  
* A lot of cable.  
* A lot of soldering.  

## Steps
--- 

# Referencias / References
Proyecto HW: [@MattDB](https://www.thingiverse.com/thing:2704567).  
Proyecto Original: [@mattdibi](https://github.com/mattdibi/redox-keyboard).  
Biuldlog: [IDK](https://imgur.com/a/phr2z).  
QMK Docs: [Docs](https://docs.qmk.fm/#/).  
Video (ESP): [JC Nerd](https://www.youtube.com/watch?v=mz8WG5e--jA&t=12s). 