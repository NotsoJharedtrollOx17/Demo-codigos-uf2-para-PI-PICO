# Demo-codigos-uf2-para-PI-PICO
## Abraham Jhared Flores Azcona, 19211640

---

### Resumen
Aqui se tienen dos codigos ejemplo de autoria propia donde se les hicieron las modificaciones pertinentes para poder ser compilados
al archivo .uf2 que se necesita para ejecutarse en la Raspberry PI PICO. El principal detalle es tener todo en orden (incluyendo el paquete `minicom`) y tener la instalacion
del SDK que el [PDF Adjunto (p. 80)](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf) indica, para no batallar con el resto del tutorial.

---

### Pasos

#### Paso 1: Crear carpetas para ambos programas
Primero creamos las carpetas pertinentes para cada uno de los programas; de preferencia que tengan el nombre igual al ejercicio de C++ que deseamos
correr en la PI PICO. **IMPORTANTE**: la carpetas deben ser creadas en la misma carpeta donde se encuentre el `pico-sdk`.

EJ:

![pico_001](https://user-images.githubusercontent.com/99265478/170366513-012eda18-be62-45fa-8b66-bf683f92153d.png)

#### Paso 2: Entrar a las carpetas y crear los CMakeLists.txt, test.cpp y el pico_sdk_import.cmake
Entramos a cada una de las carpetas y creamos los archivos pertinentes. Se brindan los archivos en el repo. **IMPORTANTE**: si se desea 
usar un archivo .cpp propio, el nombre del archivo debe ser *test*.cpp y el formato del codigo debe ser el siguiente:
```cpp
//librerias del programa
#include "pico/stdlib.h" //LIBRERIA IMPORTANTE PARA LA PI PICO

//resto del codigo

//dentro del main y antes de las impresiones en consola
stdio_init_all(); //uso de librerias PI PICO

while(true) {
//codigo que queremos desplegar en conexion serial en Linux
sleep_ms(2000); //retraso 
}
```

#### Paso 3: Creacion y ejecucion del folder `build`
Siguiendo los pasos del [PDF Adjunto (p. 80)](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf):
```bash
mkdir build
cd build
export PICO_SDK_PATH=../../pico-sdk
cmake ..
make
```
Que nos genera el archivo `test.uf2` dentro de la carpeta `build`.

#### Paso 4: Carga de `test.uf2` a la PI PICO
Abrimos la carpeta de `build` desde el Explorador de Archivos y arrastramos el `test.uf2` hacia la RP-PI2 (la PI PICO cuando se conecta en modo BOOTSEL). Carga
el archivo hacia la PI PICO, la cierra y el codigo ejecutable ya se encuentra ejecutandose en la PI PICO. 

![build_001](https://user-images.githubusercontent.com/99265478/170375728-7b735011-0470-4c2a-b9ba-3e249c975989.png)

#### Paso 5: Muestra de la ejecucion del programa en consola
Teniendo conectada la PI PICO a la computadora, comprobamos la conexion USB serial por medio del comando:
```bash
sudo dmesg | grep tty
```
El puerto serial debe aparecer con terminacion `ACM0`

![abrah@abrah: ~-Pictures_001](https://user-images.githubusercontent.com/99265478/170378091-86fd5dd7-2d9c-46e8-94c6-71e5dd03f7e0.png)

De ser asi, escribimos:
```bash
sudo minicom -b 115200 -o -D /dev/ttyACM0
```
Para desplegar la salida del programa en la consola:

![abrah@abrah: ~-Pictures_002](https://user-images.githubusercontent.com/99265478/170379422-e3c015c3-2146-40f3-96f8-86a9f07ffa9e.png)
