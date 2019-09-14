# Espacio de Definición Institucional

### GNU Privacy Guard

Ese el nombre nombre y apellido de GnuPG, y que de ahora en más nos referiremos directamente como GPG. GPG es una implementación completa y libre del estándar [OpenPGP](https://www.openpgp.org/about/ "Open PGP"), que define los formatos para la encriptación, firmas, certificados e intercambios de llaves públicas. Si bien hoy no vamos a entrar en todos los conceptos técnicos, dejamos un par puntos que hay que saber:

**Cifrado asimétrico**
A muy grosso modo es que si firmamos / encriptamos un archivo con una llave (pública o privada), unicamente puede ser verificado / desencriptado con la llave complementaria.

**Anillos de claves (keyring)**
El keyring es el deposito donde se almacenan todas las claves GPG, tanto públicas como privadas. Cada vez que tengamos que hacer alguna operación vamos a necesitar acceder a este almacén para recuperar el key especifico.

**Servidores de claves (keyservers)**
Son servidores donde se almacenan las llaves públicas para ser utilizadas por terceros y así puedan verificar nuestra identidad o desencriptar nuestros mensajes.

#### Instalación y configuración PGP
1. **Instalación**
    ```sh
    $ sudo apt install pgp
    ```
    
2. **Generación de clave e identificación personal**
    Este comando nos pedirá un nombre, un apellido, una dirección de correo electrónico y finalmente presionamos "V" (Vale) para pedir una contraseña que protegerá la información generada.
    ```sh
    $ sudo gpg --gen-key
    ```
    
3. **Exportar nuestra Public Key**
    Este comando nos permitirá exportar nuestra public key al archivo mykey.asc dentro del nuestro lugar de trabajo actual en la terminal.
    ```sh
    $ gpg --armor --export you@exammple.com > mykey.asc
    ```
    
4. **Crear servidor basico para que un compañero pueda descargarla**
    Crea un servidor en la carpeta actual al que todos tendran acceso por su ip y puerto específico.
    ```sh
    $ python2 -m SimpleHTTPServer 80
    ```
    ```sh
    $ python3 -m http.server 80
    ```
    Luego para obtener su ip debe tipear en su terminal 
    ```sh
    $ ip a
    ```
    Finalmente si desea descargar el archivo mykey.asc, su colega debe tipear
    ```sh
    $  wget nuestra_ip:puerto/mykey.asc
    ```
    *Nota: El comando wget sin especificar la ruta del archivo, descargará todo el contenido de la carpeta que se utilizo para montar el servidor http.

7. **Verificar que el archivo contenga la key**
    Hacemos uso del comando cat para ver su contenido
    ```sh
    $  cat mykey.asc
    ```
    
6. **Importar una Public Key**
    Antes de realizar el comando, debemos tener descargada la key que queremos que añadir a nuestra lista de keys publicas importadas. En este caso he descargado una key de nombre mykey.asc de un compañero de trabajo.
    ```sh
    $ gpg --import mykey.asc
    ```
    
7. **Comprobar importación**
    Este comando nos permitirá ver la lista de keys disponibles en nuestro terminal.
    ```sh
    $ gpg --list-key
    ```
    
8. **Eliminar una Key del almacen de claves**
    Primero debemos eliminar la secret key de dicha clave mediante su dirección o primeros 8 digitos.
    ```sh
    $ sudo gpg --delete-secret-key 00AA11BB
    $ sudo gpg --delete-secret-key email@dominio.com
    ```
     Luego debemos eliminar su public key
    ```sh
    $ sudo gpg --delete-key 00AA11BB
    $ sudo gpg --delete-key email@dominio.com
    ```
    
9. **Enviar un archivo encryptado para que solo su receptor pueda descifararlo con su private key**
    Creamos nuestro archivo y redactamos le mensaje deseado (En caso de que el archivo exista, saltear este paso).
    ```sh
    $ nano holamundo.txt
    ```
    Luego encriptamos y enviamos con el siguiente comando (recordar example@dominio.com permitira buscar y tomar la key en nuestor terminal con dicho correo o bién podemos hacer uso de los primeros 8 digitos)
    ```sh 
    $ gpg --output holamundo.txt.gpg --encrypt --recipient example@dominio.com holamundo_encryptado.txt
    ```
    ```sh 
    $ gpg --output holamundo.txt.gpg --encrypt --recipient 00AA11BB holamundo_encryptado.txt
    ```
    *Nota: El segundo "holamundo.txt" se guardará en el lugar de trabajo del terminal con el documento original ya encriptado.

10. **Desencriptando documento encriptado**
    Nos pedirá la contraseña (la que introdujo en este caso el propietario de la public key cuando generó su par de claves). Una vez ingresada ya podremos leer el documento.
    ```sh 
    $ sudo --output holamundo.txt --decrypt holamundo.txt.gpg 
    ```
