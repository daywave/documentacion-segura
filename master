# Documentación del Código

## Índice

1. [send_file_via_scp](#function-1)
2. [receive_all](#function-2)
3. [select_file](#function-3)
4. [calculate_sha384](#function-4)
5. [calculate_sha512](#function-5)
6. [calculate_blake2](#function-6)
7. [encrypt_message_with_rsa](#function-7)
8. [get_filename](#function-8)
9. [clear_directory](#function-9)
10. [calculate_file_hash](#function-10)
11. [handle_file_transfer](#function-11)
    1. [Loop principal](#sub-function-111)
    2. [Escribir mensaje](#sub-function-1111)
        1. [Detener conexión](#sub-function-11111)
    3. [Seleccionar archivo](#sub-function-1112)
    4. [Salir](#sub-function-1113)
    5. [Opción inválida](#sub-function-1114)
    6. [Calcular SHA-384](#sub-function-112)
    7. [Leer archivo](#sub-function-113)
    8. [Encriptar mensaje](#sub-function-114)
    9. [Eliminar archivo sin encriptar](#sub-function-115)
    10. [Calcular SHA-512](#sub-function-116)
    11. [Seleccionar archivo para ocultar](#sub-function-117)
    12. [Ocultar mensaje](#sub-function-118)
    13. [Calcular Blake2](#sub-function-119)
    14. [Calcular hashes SHA-512](#sub-function-1110)
    15. [Enviar solicitud de transferencia](#sub-function-1111)
12. [main](#function-12)

## Funciones

### Function 1: send_file_via_scp

Esta función envía un archivo a un servidor remoto utilizando SCP (Secure Copy Protocol) a través de una conexión SSH proporcionada por `paramiko`.

### Function 2: receive_all

Esta función recibe todos los datos de un socket hasta que no haya más datos que recibir y devuelve los datos como una cadena decodificada en UTF-8.

### Function 3: select_file

Esta función abre un cuadro de diálogo para seleccionar un archivo utilizando `tkinter` y devuelve la ruta del archivo seleccionado.

### Function 4: calculate_sha384

Esta función calcula el hash SHA-384 de un archivo dado y devuelve el valor hexadecimal del hash.

### Function 5: calculate_sha512

Esta función calcula el hash SHA-512 de una cadena de datos y devuelve el valor hexadecimal del hash.

### Function 6: calculate_blake2

Esta función calcula el hash Blake2 de un archivo dado y devuelve el valor hexadecimal del hash.

### Function 7: encrypt_message_with_rsa

Esta función encripta un mensaje utilizando RSA con una clave pública y devuelve el mensaje encriptado en formato de bytes.

### Function 8: get_filename

Esta función solicita al usuario que ingrese el nombre de un archivo y devuelve el nombre del archivo con la extensión `.txt`.

### Function 9: clear_directory

Esta función elimina todos los archivos y subdirectorios en el directorio especificado.

### Function 10: calculate_file_hash

Esta función calcula el hash SHA-512 de un archivo dado y devuelve el valor hexadecimal del hash.

### Function 11: handle_file_transfer

#### Sub-function 11.1: Loop principal

Este es el bucle principal que permite al usuario seleccionar una opción para escribir un mensaje, seleccionar un archivo o salir.

#### Sub-function 11.1.1: Escribir mensaje

Permite al usuario ingresar un mensaje, guarda el mensaje en un archivo y calcula su hash SHA-384.

#### Sub-function 11.1.1.1: Detener conexión

Envía una señal de "STOP" para cerrar la conexión con el esclavo y cierra el socket.

#### Sub-function 11.1.2: Seleccionar archivo

Permite al usuario seleccionar un archivo usando `tkinter`.

#### Sub-function 11.1.3: Salir

Envía una señal de "STOP" para cerrar la conexión con el esclavo y cierra el socket.

#### Sub-function 11.1.4: Opción inválida

Muestra un mensaje de opción inválida y continúa el bucle.

#### Sub-function 11.2: Calcular SHA-384

Calcula el hash SHA-384 del archivo seleccionado y lo guarda en un archivo.

#### Sub-function 11.3: Leer archivo

Lee el contenido del archivo seleccionado.

#### Sub-function 11.4: Encriptar mensaje

Encripta el mensaje utilizando la clave pública RSA y guarda el mensaje encriptado en un archivo.

#### Sub-function 11.5: Eliminar archivo sin encriptar

Elimina el archivo original sin encriptar.

#### Sub-function 11.6: Calcular SHA-512

Calcula el hash SHA-512 del mensaje encriptado y lo guarda en un archivo.

#### Sub-function 11.7: Seleccionar archivo para ocultar

Permite al usuario seleccionar un archivo para ocultar el mensaje encriptado utilizando `tkinter`.

#### Sub-function 11.8: Ocultar mensaje

Oculta el mensaje encriptado en el archivo seleccionado utilizando `steghide`.

#### Sub-function 11.9: Calcular Blake2

Calcula el hash Blake2 del archivo con el mensaje oculto y lo guarda en un archivo.

#### Sub-function 11.10: Calcular hashes SHA-512

Calcula los hashes SHA-512 de los archivos relevantes y los guarda en un diccionario.

#### Sub-function 11.11: Enviar solicitud de transferencia

Envía una solicitud de transferencia de archivo al esclavo y maneja la transferencia y confirmación de archivos.

### Function 12: main

La función principal configura el entorno necesario, establece una conexión con el esclavo, solicita la clave pública, la dirección MAC, y llama a `handle_file_transfer` para gestionar la transferencia de archivos.

