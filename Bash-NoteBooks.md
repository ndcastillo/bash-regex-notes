# Interprete Bash

**Terminal:** Ventana que nos muestra el `prompt` $

**Shell:** Linea de comandos. Este es un `interprete` de comandos, nos da acceso a los servicios del Sistema Operativo.

---

### Tipos de Shell

+ Bourne Shell

+ Bash Shell (Mas Comun)

+ Z shell (Mas Comun)

+ C shell

+ Fish shell

+ Power shell (Windows)

<img title="" src="img/2022-04-19-22-03-13-image.png" alt="" data-align="center" width="202">

<img title="" src="img/2022-04-19-22-03-38-image.png" alt="" data-align="center" width="314">

---

Un **comando** es  un programa que se puede ejecutar desde la **terminal** que puede contener algunos `parámetros` y `opciones`.

## Sistema de Archivos

<img title="" src="https://media.geeksforgeeks.org/wp-content/uploads/linuxDir.jpg" alt="Lightbox" width="326" data-align="center">

Para **limpiar shell** : `Ctrl + L`

**~ :** Virgulilla

^: Circunflejo

El Shell tiene un historial de comandos, con las teclas arriba y abajo puedes navegar por los comandos ya ejecutados.

---

## Algunos comandos Basicos

`ls` : Listar archivos

`ls -lh` : Listar archivos de una manera mas entendible

`ls -a` : Listar archivos ocultos

`pwd` : Identifica la ruta donde nos encontramos

`mkdir` : Crea un Directorio

`cp` : Copiar un Archivo

`rm` : Borra un Archivo

`rmdir` : Borra un Directorio

`file {archivo}`: Identifica un archivo y lo detalla

`clear`: Limpia el Shell

## Ruta Relativa `.`

`cd .` Nos fija en el directorio actual

Un ejemplo de uso de ruta relativa `<link src="./css/main.css" />`

## Ruta absoluta `..`

`cd ..` Nos regresa al directorio padre.

Si se encuentra en una ruta padre y quieres  realizar un llamado a un js u otro, se podría con `<script src="../js/app.js" />`

## Anatomia de un CLI (Command Line Interface)

La anatomia consiste en el nombre del comando, luego la opcion (flag), y despues el argumento. Por ejemplo:

```bash
rm -rf argument
```

## Alias

La manera de acortar comandos largos, es a través de `alias`, por ejemplo:

```bash
alias web='mkdir css && cd css && touch main.css'
```

## Manipulacion de Archivos y Directorios

### Listado de elementos:

`ls -al`: Lista todos los elementos del directorio, incluido los ocultos.

`ls -ls`: Lista todos los elementos del directorio, iniciando por los mas pesados.

`ls -lr`: Lista los elementos de forma inversa

`tree`: Despliega todos los directorios como un arbol

`tree -L #`: Despliega los directorios hasta un nivel #. *flag:* `-L`: Levels

### Manipulación de elementos:

`mkdir {folder}`: Crea un nuevo directorio

`touch {file}`: Crea un nuevo archivo

Un tip para este comando es el utilizar `touch index.{html,css,js}` de esta manera creara tres archivos con nombre `index` y extensiones html, css y js.

`cp {orginal} {copia}`:  Copia un archivo

`mv {file} {path}`: Movera un archivo a la ubicación deseada.

`mv {name} {new_name}`: Cambian el nombre ya sea del archivo o del directorio

`rm {file}`: Elimina un archivo en cuestión.

`rm -i {file}:` Nuestro terminal pedirá información antes de eliminar el archivo.

`rm -r {folder}"`: Elimina el directorio indicado.

#### Flags

Los flags son los argumentos que se le agregan a los comandos, para `ls` sus flags mas comunes son:

`-l`: Long (Listado en formato largo) 

`-a`: Archivos ocultos `-S`: Size (Tamaño en bits) `-r` : Reverse (Invertir)

`-F`: El tipo de archivo ( / directorio, * ejecutable, @ enlace simbólico.)

`-h`: Tamaño en MB, KB 

`-R`: Muestra las carpetas de manera recursiva

## Directorio con Espacio

Es sugerible crear los nombres de archivos y carpetas sin espacios, peros si es necesario, para crear se suele utilizar las comillas de manera que:

```bash
mkdir "mi Carpeta"
mkdir dir1 dir2 dir3 dir4
rm -rf dir1 dir2 dir3 dir4
tree -L 2
mkdir carpeta
mv carpeta otraCarpeta
```

## Eliminar Carpetas

Si deseas eliminar carpetas usualmente se puede utilizar con el comando `rm` pero aveces nuestras carpetas contienen archivos por lo que se usa el flag `-r` de creatividad, para realizar la eliminación por fuerza se puede también utilizar `-f` de force. así tendríamos que las flags para `-rm`:Remove tendríamos.

`-r`: Recursividad `-f`:Force `-i` Informacion

## Visor de Archivos de texto plano

`head` me muestra las primeras 10 lineas de texto

Si usamos el flag `-n` podemos hacer que nos muestre un n números de lineas, por ejemplo:

```bash
head archivo.md -n 15
less archivo.md
cat archiv.md
```

`tail` este me muestra las ultimas 10 lineas de texto, y también se puede utilizar con el flag `-n`.

Otro visor de texto util es `less`, o tambien es util `cat` que nos mostrara todo el contenido del archivo de texto plano.<img title="" src="https://static.platzi.com/media/user_upload/porque-los-gatos-mueven-la-cola-2-af5d748b-8d4e-42c8-8f8c-133406a01512.jpg" alt="Preview" width="279" data-align="center">Si te encuentras en una distribución de linux nativa, se puede utilizar el comando `xgd-open archivo.md` para abrir algún documento en cuestión, pero si te encuentras con WSL, lo sugerible es que intercambies en la misma terminal a `cmd`, y luego vuelvas a la misma con `bash`. Por ejemplo:

```bash
cmd.exe
bash
```

![](img/2022-04-19-21-42-36-image.png)

En WSL tambien se podria utilizar el comando `wslview arhivo.md`, algunos ejemplos serian:

```bash
wslview archivo.md
wslview carpeta
wslview . 
```

El comando `wslview` nos abrira la carpeta con la ruta relativa `.` que este caso es la carpeta actual.

En una distribución nativa se utiliza `nautilus`.

## Un comando puede ser 4 cosas

1. Un programa ejecutable

2. Un comando de utilidad de la shell

3. Una funcion de shell

4. Un alias.

Ahora, como saber si un comando es  de los 4 tipos mencionados anteriormente, bueno lo sabremos con el comando `type`, por ejemplo

```bash
type cd
#-> cd is a shell builtin
type mkdir
#-> mkdir is /usr/bun/mkdir
type ls
#-> ls is aliased to `ls --color=auto`
```

Los flags que coloquemos por ejemplo long, usualmente se colocan con dos guiones y luego un parametro, de manera que:

```bash
ls --long
```

Para pedir ayuda en los comandos podemos utilizar el flag`-help`, ejemplos:

```bash
ls --help
cd --help
mv --help
```

tambien podemos usar la utilidad de `help`, esta utilidad es exclusiva de bash shell por ejemplo:

```bash
help ls
help cd
help mv
```

Dentro de bash también podemos hacer uso de `man cd`, ojo en versión nativa. Tambien podríamos usar `info cd`, otro es `whatis cd` nos mostrara un linea muy corta de su funcionamiento.

```bash
man cd
info cd
whatis cd
```

Se puede realizar **programación en Bash Shell**.

### Working Bash History

Podemos reusar comandos ya ejecutados dentro del Bash, muchas distribuciones inclusive puede almacenar los 1000 comandos de los usuarios. Para entrar en los ultimos comandos utilizados, utilizamos el comando `history`:

```bash
history
```

![](img/2022-04-28-21-56-48-image.png)

Puede utilizar el comando `!254` para seleccionar el comando completo.

```bash
!254
// clear
```

### Key-Sequences para la administración del Bash

**Ctrl+C**: Usado para salir de un comando cuando este no responde.

**Ctrl+D**: Para cerrar sesión de un shell

**Ctrl+R**: Abriremos el "reversed I-search" prompt, que nos ayudara a localizar comandos previamente utilizados con una sintaxis que coloquemos.

**Ctrl+Z**: Usado para interrumpir un proceso que este ejecutando la shell.

### Alias

Se hace uso del comando `alias`, con la siguiente sintaxis:

```bash
alias l="ls -al"
```

Un punto importante a mencionar, es que estos únicamente se encontraran disponibles en el interprete actual, es decir no se podrán utilizar luego de que se cierre la ventana del shell. Esto se puede configurar en las **variables de entorno del S.O**

### WildCards

Los wildcards son comodines que nos ayuda a seccionar a un número de directorio o archivos.

```bash
ls *.html
rm -rf *.html
ls juanito?
ls -al juanito?
ls [[:upper:]]* // Mayusculas
ls [[:lower:]]* // Minuscula
ls [ad]* // Que empiecen con 'a' o 'd'
ls [a][i]* // Que empicen con 'ai'
ls [!a] // Cualquier caracteres que no coincida con 'a'
```

![](img/2022-04-30-11-00-52-image.png)

![](img/2022-04-30-11-01-35-image.png)

![](img/2022-04-30-11-03-27-image.png)

![](img/2022-04-30-11-04-28-image.png)

![Preview](https://static.platzi.com/media/user_upload/Screenshot%202021-04-22%20205231-1a78df8b-57f7-4012-9e61-9dfebaed510d.jpg)

![](img/2022-04-30-11-06-32-image.png)

![](img/2022-04-30-11-09-56-image.png)

![](img/2022-04-30-11-12-54-image.png)

![](img/2022-04-30-11-14-19-image.png)

![](img/2022-04-30-11-14-35-image.png)

### Redirecciones: Funcionamiento de la SHELL

Cuando colocamos un texto con nuestro teclado en la linea de comandos, esta sera nuestro **stdin** (Standar Input) que lo describe como 0, y lsa salida de nuestro comando en la shell nos puede dar 2 salidas, un **stdout** (Standar Output) con codigo 1, y el **stderr** (Standar Error) con código 2.

![](img/2022-04-30-11-18-55-image.png)

![](img/2022-04-30-11-48-49-image.png)

Por ejemplo si realizo:

```bash
ls Documents > prueba txt
head prueba.txt
```

![](img/2022-04-30-12-03-43-image.png)

### + Redireccionamiento Pipe Operator

Nos permite redirigir el `stdout` (Standar Output) de un comando a un `stdin` (Standar Input) de otro comando, permitiendo generar filtros, encadenamientos y funcionales distintas. (Simbolo pipe '|' )

Listamos el directorio actual y lo observamos como si fuese un archivo de texto plano:

```bash
    ls -lh | less
    ls -lh | sort | less
```

El comando `tee` nos permite crear un archivo de texto plano. Por ejemplo `tee test.txt`, luego escribes que es lo que deseas tener en el archivo.

```bash
    ls -lh | less | tee observacion.txt
```

#### Cowsay

Para obtener una vaquita en nuestro interprete de S.O, podemos hacerlo con el comando `cowsay`. Una prueba seria:

```bash
    cowsay 'Hola'
```

Para colocarle color podriamos usar `lolcat`. Para ejecutar el comando de `cowsay` y 'lolcat' es importante que tengas instalado los paquetes correspondientes.

```bash
    cowsay 'Hola'
    cowsat -f dragon 'Hola' | lolcat
```

![](./img/Screenshot_1.png)

Utilizo un piper operator para introducir como standar input a el comando lolcat.

![](./img/cowsay-lolcat.png)

## OPERADORES DE CONTROL

Se pude hacer uso de los operadores `&` para ejecutar de manera asincrona, y tambienn se podria utilizar un `&&`. Tambien se puede utilizar `||` para ejecutar de manera sincronza pero que sin condicionar un `stdout` exitoso como lo hace `&&`. 

Esto vamos a utilizarlo con `webpack`.

El siguiente Script nos ayuda a crear las carpetas de `css`, `src` con los archivos de estilos `main.css`, `tablet.css` y `desktop.css`. Tambien nos creara los achivos de dinanismo de web como `app.js` en la carpeta de `src`.

```bash
mkdir src css && touch ./css/main.css ./css/tablet.css ./css/desktop.css ./src/app.js index.html && echo "Archivos Creados Correctamente" && code ./ -r && code index.html
```

## PERMISOS DE ARCHIVOS

#### Tipos de archivos:

`-`: Un archivo normal

`d`: Un directorio

`l`: Un link simbólico

`b`: Un archivo de bloque especial. Son archivos que manejan la información de los bloques de datos como USB.

#### Tipo de modo

La lectura del tipo de modo se lo realiza por tres set de datos Dueño, Grupo, Todos. Esto dependerá del usuario que estemos logeados.

![](img/2022-05-03-09-49-32-image.png)

`r`: read - Permiso de Lectura

`w`: write - Permiso de Escritura

`x`: execute - Permiso de Ejecución del Programa.

Como observamos, cada uno de los permisos son representados por un bit [0,1] por ende también podemos cambiar de base y utilizarlos en el sistema octal, es decir:

000: 0, 001:1,...., 111:7 -> en el ejemplo seria 755

![](img/2022-05-03-09-46-49-image.png)

![Preview](https://static.platzi.com/media/user_upload/1-0e5c063a-3fba-42a8-84cc-a2bf6687206b.jpg)

El comando a utilizar para dar persmisos a un archivo u directorio es a traves de `chmod` (Change Mode). Tambien debemos referencias al usuario, a un grupo para todos o aplicar para todos:

![](img/2022-05-03-09-58-24-image.png)

#### Comando super util > text.txt

Para crear archivos de texto plano con `> texto.txt`, recuerda que `>` es un operador de redirecionamiento I/O, como no envió nada a texto.txt, entonces este se creara como un archivo de texto plano vació.

Para cambiar permisos en la Linea de Comandos:

```bash
chmod test.txt u+r // Permisos de Lectura al usuario
chmod test.txt u-w // No permito escritura al usuario
chmod test.txt u+x // No permito escritura al usuario
```

Para saber que usuario estoy logeado utilizo el comando `whoami`

```bash
sudo su // Ingresar como root
su ndcastillo // Ingresar como usuario ndcastillo
sudo rm text.txt // Cambiar de usuario a root solo en es linea de codigo
```

Para cambiar la contraseña en usuario se hace uso de la utilidad de `passwd`

```bash
passwd
\\ Cambiara la contraseña
```

Cuando cree un archivo, este se asociara al usuario que lo crea y le dará todos los permisos.

## VARIABLES DE ENTORNO

### Links Simbolicos

Es una especie de acceso directo desde el interprete del S.O (Terminal), se puede activar por `ln -s`, estos hacen referencia hacia a un lugar. Un ejemplo seria:

```bash
ln -s ~\Desktop\Dev dev
```

![](img/2022-05-04-09-40-24-image.png)

![](img/2022-05-04-09-40-50-image.png)

## Ingreso a Variables de entorno

Utilizando la utilidad `printenv` o también con `env`, nos listara todas las variables de entorno del sistema.

![](img/2022-05-06-05-25-45-image.png)

Esta variables están definidas de acuerdo a las asignación \$VAR, por ejemplo si se quiere ir al home `cd $HOME`. Para saber cuantos archivos binarios cuentas, basta con que señale un:

```bash
echo $PATH
```

<<<<<<< HEAD
A esta dirección se encontraran los interpretes de lenguaje, archivos binarios y los manejadores de paquetes como `apt`, `node`, `pip`, etc.

Se puede crear nuestras propias variables de entorno, y definir por default estas variables para no únicamente utilizar `alias`.

Para ello debemos modificar el texto plano `.bashrc`, este se encuentra en el /home/ .

![](img/2022-05-10-01-56-25-image.png)

En el archivo **.bashrc**

```r
lh -lahS
```

Guardamos el archivo, y reiniciamos el interprete `bash`.

```bash
lh
```

![](img/2022-05-10-02-04-49-image.png)

### + Agregar rutas de variables de entorno

Si decidimos crear una nueva ruta de variables de entorno que contenga los binarios que yo quisiera, primero imprimimos las direccion establecidas con:

```bash
echo $PATH
```

![](img/2022-05-10-02-11-53-image.png)

ahora para agregar una nueva ruta, realizamos el siguiente anexo en `.bashrc`:

```bash
PATH=$PATH:/home/davidcastillo/user/Music
```

![](img/2022-05-10-02-12-56-image.png)

Ahora cuando hagamos el llamado a la variable `$PATH` veremos que se agrego una nueva ruta de variables de entorno.

![](img/2022-05-10-02-13-49-image.png)

Las variables de entorno nos ayuda en las configuraciones de los servidores en la nube, ocultar archivos, valores, y otros.

## + COMANDOS DE BUSQUEDA

```bash
which code
# /mnt/c/Users/raycr/AppData/Local/Programs/Microsoft VS Code/bin/code
```

`witch` nos realiza la búsqueda de binarios, es decir programas ejecutables. 

En resumen buscara los binarios ejecutables como variables de entorno.

El comando principal de búsqueda sera `find`, y necesitamos especificar la ruta donde deseamos realizar la búsqueda, y agregar tres argumentos el de `-name` ,`-type` y `-size`.

```bash
find ./ -name file
find ./ -name *.txt
```

Tiene otro argumento para especificar que tipo de archivo se requiere buscar si es **archivo (file)** o un **directorio (directory)**. Por ejemplo:

```bash
find ./ -type f -name index ## Para un Archivo
find ./ -type d -name Documents ## Para un Documento
find ./ -type fd -name "D*"
```

Tambien se pueden usar wildcards con este comando de búsqueda:

```bash
find ./ -type f -name *.log 
find ./ -type f -name "I*"
```

<img src="img/2022-08-09-07-17-32-image.png" title="" alt="" width="228">

Tambien se puede filtrar la búsqueda por el tamaño usando notación científica de $k,M,G$ etc. Se puede filtrar tanto dando medidas exactas, como también especificando si son mayores o menores a un tamaño en especifico.

Iguales a 4KB

```bash
find ./ -size 4k
```

<img src="img/2022-08-09-07-18-43-image.png" title="" alt="" width="222">

Mayores a 4KB

```bash
find ./ size +4k
```

<img src="img/2022-08-09-07-23-06-image.png" title="" alt="" width="362">

Menores a 4KB

```bash
find ./ size -4k
```

<img src="img/2022-08-09-07-23-59-image.png" title="" alt="" width="238">

Encontrar todos los archivos de texto en home y guardar la salida en un archivo `.txt`, y publicar un mensaje `echo` diciendo *Se han guardado exitosamente los nombres de los archivos .txt*.

```bash
find ./ -type f -name *.txt > mis-documentos-de-texto.txt && echo 'Los documentos de texto se han guardado exitosamente'
```

![](img/2022-08-09-07-29-34-image.png)

Existen mas parámetros para revisar acerca del comando de búsqueda, como lo son `mindepth`, `maxdepth` y `-empty`. Esta es una tabla de sus funcionalidades y outputs.

| Opción      | Salida                              |
| ----------- | ----------------------------------- |
| `-size`     | Busca por tamaño                    |
| `-mindepth` | Asigna una nivel profundidad mínima |
| `-maxdepth` | Asigna una nivel profundidad máxima |
| `-type`     | Busca por el tipo de archivo        |
| `-name`     | Busca por el nombre del archivo     |

Podemos buscar archivos que se encuentren vacíos, estos nos pueden ayudar a eliminar archivos a través de un pipe operator.

```bash
find ./ -type d -empty
```

<img src="img/2022-08-09-07-43-31-image.png" title="" alt="" width="242">

Si definimos la profundidad de directorios a través de `-maxdepth` en 2 carpetas utilizaremos el siguiente CLI.

```bash
find ./ -type d -maxdepth 2
```

<img src="img/2022-08-09-07-44-53-image.png" title="" alt="" width="208">

Ahora definimos la profundidad mínima de 2 en la búsqueda, esto buscara mínimo en dos carpetas adelante de la ruta relativa.

```bash
find ./ -type d -mindepth 2
```

<img src="img/2022-08-09-07-46-31-image.png" title="" alt="" width="245">

Por ultimo podemos usar el visor de texto `less` para observar de mejor manera los documentos o archivos buscados:

```bash
find ./ | less
```

### Ejercicios realizados

1. Busca tus archivos mayores a 100Mb, con una profundidad máxima de 4, que comiencen por la letra d.

```bash
find ./ -maxdepth 4 -type f -name "d*" -size +100M
```

2. Busca los archivos que tengan extensión “.pdf” con una profundidad mínima de 2.

```bash
find ./ -mindepth 2 -type f -name *.pdf
```

3. Busca todas las carpetas que comiencen por la letra “A” con una profundidad máxima de 5, que estén vacías.

```bash
find ./ -maxdepth 5 -type d -name "A*" -empty
```

4. Busca todo lo que tenga una letra “j” que pese más de 1b. Luego guarda la salida en un archivo llamado “LosArchivosJ.txt” y cuando termine de hacer todo eso imprime un mensaje que diga “Comando terminado con éxito”.

```bash
find ./ -name "*d*" -size +1 > LosArchivosJ.txt && echo "Comando terminado con exito"
```

### Comando `grep`

Utilizamos el comando `grep` para buscar texto dentro de un archivo, podemos expandir nuestro conocimiento a través de las expresiones regulares.

Grep significa: Global Regular Expression Print, y se identifica como un comando regex (Regular Expression) para realizar su búsqueda.

**Sintaxis**

```bash
grep [Expresión Regular] [Nombre de archivo]
```

Por ejemplo para el archivo `movies.csv`, que es una tabla de películas con 9125 registros de 6 variables, si queremos traernos los registros que contengan la palabra *the*, usamos el siguiente CLI:

```bash
grep the movies.csv
```

![](img/2022-08-09-10-33-30-image.png)

Los argumentos de `grep` son los siguientes:

| Opción | Función                        |
| ------ | ------------------------------ |
| `-m`   | Limita el numero de búsquedas  |
| `-c`   | Numero de ocurrencias          |
| `-v`   | Observaciones que NO coinciden |
| `-i`   | Ignore case sensitive          |

Para ver únicamente los 10 primeros resultados utilizamos `-m` en `grep`, de manera que:

```bash
grep -m 10 the movies.csv
```

<img src="img/2022-08-09-11-21-23-image.png" title="" alt="" width="375">

```bash
grep -c the movies.csv
```

<img src="img/2022-08-09-11-16-38-image.png" title="" alt="" width="261">

```bash
grep -ci the movies.csv
```

<img src="img/2022-08-09-11-16-59-image.png" title="" alt="" width="261">

```bash
grep -vci the emovies.csv
```

<img src="img/2022-08-09-11-18-42-image.png" title="" alt="" width="296">

Ahora para contar el numero de saltos de lineas, numero de palabras y numero de bits tiene nuestro archivo podemos hacer uso de comando `wc` o Write Counts. De manera que:

```bash
wc movies.csv
```

<img title="" src="img/2022-08-09-11-30-44-image.png" alt="" width="294">

La primera nos dice el numero de saltos de linea, que en este caso seria el numero de registros menos 1, dado a que el primer salto de linea es para los indices, despues tenemos el numero de letras usadas en el documentos. Por ultimo tenemos el tamaño en bits del archivo.

```bash
wc -l movies.csv    # Numero de lineas
wc -w movies.csv    # Numero de palabras
wc -b movies.csv    # Numero de bits 
```

Grep nos ayuda a filtrar lineas de código, buscar registros, filtrar textos, y demás.

## Utilidades de Red

Para saber información acerca de los dispositivos de red que tiene nuestro computador, servidor y/o otro dispositivo que funcione con Linex, podemos usar el comando `ifconfig`:

```bash
ifconfig
```

Nos aparecera a lado izquierdo el dispositivo de nuestra tarjeta de red, router, ont ,etc con la cual nuestro computador puede conectarse. Ademas nos da información acerca de protocolos de red, números de IP, puertos disponibles, etc. 

Otra utilidad de Red es `ping`, utilizado para verificar una conexión con algun server o computador.

```bash
ping www.google.com
```

Ahora podemos utilizar tambien alguna interfaz o utilidades conocidas como `curl` que es muy usada en conexiones de red, peticiones HTTP, consultas a una API, servicios IOT, condificación/decodificación, etc. Una aplicación sencilla seria traernos el documento HTTP de google. (Ojito usaremos un pipe operator para guarlo en un archivo `index.html`).

```bash
curl www.google.com > index.html
```

<img src="img/2022-08-09-11-49-10-image.png" title="" alt="" width="348">

Otra utilidad de red es `wget` que es muy semejante a `curl`, pero para este caso no es necesario usar el *pipe operator*, ahora directamente realiza la descarga. Es muy usado para descargar repositorios, instaladores entre otros.

```bash
wget www.google.com
```

![](img/2022-08-09-11-54-48-image.png)

Un comando para ver la ruta que los paquetes IP siguen a traves de una red podemos usar el comando `traceroute www.google.com` en donde nos dara los routers, servidores y computadores por los que pase para llegar a su destino y ademas el tiempo de duración que le toma.

```bash
traceroute www.google.com
```

Para ver los dispositivos de red usamos `netstat`. Es muy similar a ifconfig, pero en forma de una tabla.

```bash
netstat
```

## Comprimir Archivos

Creamos una carpeta con nombre carpeta 🥲, y luego a través del comando `tar`.

```bash
mkdir carpeta
tar -cvf carpeta.tar ./carpeta
```

Tambien se puede comprimir a traves de un algoritmo gz, de agregando un nuevo parametro al CLI que seria una `-z`.

```bash
tar -cvzf carpeta.tar.gz ./carpeta
```

Para realizar la descompresión se usa el argumento de `-z` de forma que:

```bash
tar -xcvf carpeta.tar.gz
```

Otro CLI para comprimir es el `zip`:

```bash
zip -r carpeta.zip ./carpeta
```

Para la descompresión, se hace uso el CLI `unzip`.

Para el comando `tar`

| Opción | Función                                          |
| ------ | ------------------------------------------------ |
| `-c`   | Compresión                                       |
| `-x`   | Descompresión                                    |
| `-z`   | Especificación de compresión en `tar` o `tar.gz` |
| `-v`   | Verbose, muestra de la lista.                    |

Para el Comando `zip`

| Opción  | Función       |
| ------- | ------------- |
| `zip`   | Compresión    |
| `unzip` | Descompresión |

## Manejo de Procesos

El manejo de procesos no es util para realizar cierta configuraciones y monitoreo de lo que se esta ejecutando en nuestro ordenador.

### Ver los procesos activos en la terminal `ps`

Para ver los procesos que se ejecutan en el bash o la terminal usamos el comando `ps`.

```bash
ps
```

Todo proceso tiene un Id y un tiempo de ejecución.

<img src="img/2022-08-10-07-38-38-image.png" title="" alt="" width="245">

### Ver todos los procesos de manera detallada `top`

Podemos observar los procesos mas detallados utilizando el comando `top`, observaremos el uso de CPU, RAM, su Id entre otros parámetros característicos de un procesos.

![](img/2022-08-10-07-43-16-image.png)

Podemos filtrar el procedimiento a traves la tecla "u" y colocar el usuario, la tecla "h" se para entrar al centro de ayuda y la tecla "q" para salir de la interfaz.

Otra terminal de administración de procesos es **htop** la cual es un poco mas amigable, la instalamos con la paqueteria apt:

```bash
sudo apt-get install htop
```

![](img/2022-08-10-07-48-29-image.png)

### Matar un proceso `kill`

Para matar un proceso lo realizamos a traves del comando `kill` y con el Id del proceso, de forma que:

```bash
kill -9 129
```

![](img/2022-08-10-07-50-17-image.png)

Para terminar el proceso inmediatamente

```bash
killall -9 129
```

### Procesos de Foreground y Background

El Foreground y el Background son estados de los procesos, y seran los que nos diran que se encuentran ejecutando (running) o que se encuentran parados (stopped).
Para ello utilizamos `cat > document.txt` y nos encontraremos con la inserción del documento de texto, pero en vez de salir del editor de texto con Ctrl+D utilizamos Ctrl+Z y suspenderemos nuestro proceso.

<img src="img/2022-08-10-21-29-53-image.png" title="" alt="" width="410">

A través de `jobs` veremos los procesos que se encuentra suspendidos.

<img title="" src="img/2022-08-10-21-30-36-image.png" alt="" width="336">

Para correr de nuevo el proceso hacemos uso de `fg [numero]` 

<img src="img/2022-08-10-21-31-50-image.png" title="" alt="" width="258">

Otras maneras de llevar un proceso al background es usar:

```bash
cat > document.txt &
bg 1
```

## Concatenar archivos .txt

Para realizar la concatenación de archivos podemos realizar con el comando `cat`, y definiendo las entradas de archivos de texto, luego usaremos el pipe operator `>` para señalar a  que archivo de texto queremos enviar la concatenación.

```bash
cat > hola.txt
Hola, # Darle Ctrl+D para salir guardando los cambios
cat > nombre.txt
David! 

cat hola.txt nombre.txt > saludo.txt
cat saludo.txt
# Hola, David!
```

<img src="img/2022-08-18-15-26-30-image.png" title="" alt="" width="502">
