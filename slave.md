# Índice de Funciones

1. `get_mac_address()`
2. `receive_file_via_scp(username, password, ip, port, remote_path, local_path)`
3. `calculate_blake2(file_path)`
4. `calculate_sha512(file_path)`
5. `calculate_sha384(file_path)`
6. `decrypt_message_with_rsa(encrypted_message, private_key)`
7. `clear_directory(path)`
8. `calculate_file_hash(file_path)`
9. `handle_request(conn, addr, public_key, private_key, slave_path, scp_username, scp_password)`
    9.1 `conn.recv(1024).decode('utf-8')`
    9.2 `conn.send(public_key.encode('utf-8'))`
    9.3 `get_mac_address()`
    9.4 `clear_directory(slave_path)`
    9.5 `receive_file_via_scp(scp_username, scp_password, addr[0], 22, remote_path, local_path)`
    9.6 `calculate_file_hash(local_path)`
    9.7 `conn.send(b"FILES_RECEIVED")`
    9.8 `conn.recv(1024).decode('utf-8')`
    9.9 `calculate_blake2(os.path.join(slave_path, "stego_file"))`
    9.10 `os.system(f"steghide extract -sf {os.path.join(slave_path, 'stego_file')} -p '{steghide_password}' -xf {os.path.join(slave_path, 'extracted_message')}")`
    9.11 `calculate_sha512(os.path.join(slave_path, "encriptado_con_RSA"))`
    9.12 `decrypt_message_with_rsa(encrypted_message, private_key)`
    9.13 `calculate_sha384(os.path.join(slave_path, "mensaje_descifrado.txt"))`
10. `main()`

# Explicación del Código por Índice

## 1. `get_mac_address()`
Esta función obtiene la dirección MAC del dispositivo en el que se está ejecutando el código. Utiliza la librería `uuid` para obtener el nodo y luego formatea la dirección MAC en el formato estándar.

## 2. `receive_file_via_scp(username, password, ip, port, remote_path, local_path)`
Esta función recibe un archivo vía SCP (Secure Copy Protocol). Utiliza la librería `paramiko` para establecer una conexión SSH y transferir el archivo desde un servidor remoto a una ruta local especificada.

## 3. `calculate_blake2(file_path)`
Esta función calcula el hash BLAKE2 del archivo especificado por `file_path`. Abre el archivo en modo binario y actualiza el hash en bloques de 4096 bytes hasta que se complete la lectura del archivo.

## 4. `calculate_sha512(file_path)`
Esta función calcula el hash SHA-512 del archivo especificado por `file_path`. Abre el archivo en modo binario y actualiza el hash en bloques de 4096 bytes hasta que se complete la lectura del archivo.

## 5. `calculate_sha384(file_path)`
Esta función calcula el hash SHA-384 del archivo especificado por `file_path`. Abre el archivo en modo binario y actualiza el hash en bloques de 4096 bytes hasta que se complete la lectura del archivo.

## 6. `decrypt_message_with_rsa(encrypted_message, private_key)`
Esta función desencripta un mensaje utilizando RSA y una llave privada. Importa la llave privada y utiliza `PKCS1_OAEP` para realizar la desencriptación del mensaje encriptado en bloques del tamaño adecuado.

## 7. `clear_directory(path)`
Esta función elimina todos los archivos y directorios dentro de la ruta especificada `path`. Itera sobre cada archivo y directorio, eliminándolos según sea necesario.

## 8. `calculate_file_hash(file_path)`
Esta función calcula el hash SHA-512 del archivo especificado por `file_path`. Abre el archivo en modo binario y actualiza el hash en bloques de 4096 bytes hasta que se complete la lectura del archivo.

## 9. `handle_request(conn, addr, public_key, private_key, slave_path, scp_username, scp_password)`
Esta función maneja las solicitudes recibidas a través de la conexión `conn` desde la dirección `addr`. Utiliza la clave pública y privada para encriptación y desencriptación, y realiza varias operaciones dependiendo de la solicitud recibida.

### Subíndices de `handle_request`

### 9.1 `conn.recv(1024).decode('utf-8')`
Recibe y decodifica una solicitud desde la conexión.

### 9.2 `conn.send(public_key.encode('utf-8'))`
Envía la clave pública a través de la conexión.

### 9.3 `get_mac_address()`
Obtiene la dirección MAC del dispositivo.

### 9.4 `clear_directory(slave_path)`
Limpia el directorio especificado por `slave_path`.

### 9.5 `receive_file_via_scp(scp_username, scp_password, addr[0], 22, remote_path, local_path)`
Recibe un archivo desde un servidor remoto utilizando SCP.

### 9.6 `calculate_file_hash(local_path)`
Calcula el hash del archivo especificado por `local_path`.

### 9.7 `conn.send(b"FILES_RECEIVED")`
Envía una confirmación de que los archivos han sido recibidos.

### 9.8 `conn.recv(1024).decode('utf-8')`
Recibe y decodifica la contraseña de `steghide`.

### 9.9 `calculate_blake2(os.path.join(slave_path, "stego_file"))`
Calcula el hash BLAKE2 del archivo `stego_file`.

### 9.10 `os.system(f"steghide extract -sf {os.path.join(slave_path, 'stego_file')} -p '{steghide_password}' -xf {os.path.join(slave_path, 'extracted_message')}")`
Extrae el mensaje oculto utilizando `steghide`.

### 9.11 `calculate_sha512(os.path.join(slave_path, "encriptado_con_RSA"))`
Calcula el hash SHA-512 del archivo encriptado con RSA.

### 9.12 `decrypt_message_with_rsa(encrypted_message, private_key)`
Desencripta el mensaje utilizando la llave privada RSA.

### 9.13 `calculate_sha384(os.path.join(slave_path, "mensaje_descifrado.txt"))`
Calcula el hash SHA-384 del mensaje desencriptado.

## 10. `main()`
La función principal que genera una clave RSA, establece un servidor esclavo y espera conexiones entrantes en el puerto 2222. Al recibir una conexión, llama a `handle_request` para manejar las solicitudes.
