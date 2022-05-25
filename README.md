# Demo-codigos-uf2-para-PI-PICO
## Abraham Jhared Flores Azcona, 19211640

---

### Resumen
Aqui se tienen dos codigos ejemplo de autoria propia donde se les hicieron las modificaciones pertinentes para poder ser compilados
al archivo .uf2 que se necesita para ejecutarse en la Raspberry PI PICO. El principal detalle es tener todo en orden y tener lista la instalacion
del SDK que el [PDF Adjunto (p. 80)](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf) indica, para no batallar con el resto del tutorial.

---

### Pasos

#### Paso 1: Crear carpetas para ambos programas
Primero creamos las carpetas pertinentes para cada uno de los programas; de preferencia que tengan el nombre igual al ejercicio de C++ que deseamos
correr en la PI PICO. **IMPORTANTE**: la carpetas deben ser creadas en la misma carpeta donde se encuentre el `pico-sdk`.

EJ:

![pico_001](https://user-images.githubusercontent.com/99265478/170366513-012eda18-be62-45fa-8b66-bf683f92153d.png)

#### Paso 2: Entrar a las carpetas y crear los CMakeLists.txt, text.cpp y el pico_sdk_import.cmake
Entramos a cada una de las carpetas y creamos los archivos pertinentes. Se brindan los archivos en el repo. **IMPORTANTE**: si se desea 
usar un archivo .cpp propio, el formato del archivo debe ser el siguiente:
```cpp
//librerias del programa
#include "pico/stdlib.h" //LIBRERIA IMPORTANTE PARA LA PI PICO

//resto del codigo

//dentro del main
stdio_init_all(); //uso de librerias PI PICO

while(true) {
//codigo que queremos desplegar en conexion serial en Linux
}
```
