# Seguridad
<h2>WINDOWS</h2>
<h3>ETERNALBLUE</h3>

Después de instalar la máquina de Kali y la máquina de Windows que hemos creado con Vagrant, seguimos estos pasos:

1. Abrimos la terminal en la máquina Kali Linux y ejecutamos el siguiente comando para entrar en la consola de Metasploit:

    msfconsole

2. Una vez en la consola de Metasploit, podemos buscar exploits utilizando el comando `search`. En este caso, queremos investigar las vulnerabilidades MS17, así que añadimos "ms17" a la búsqueda:

![imagen1](./images/Screenshot_3.png)

Observamos que hay una vulnerabilidad conocida como "eternalblue."

3. Para seleccionar esta vulnerabilidad, vemos que tiene un número asignado (por ejemplo, 0). Usamos el comando `use` seguido del número correspondiente:

    "use 0" 

4. Luego, verificamos los detalles necesarios para configurar el exploit utilizando el comando `options`. En este caso, notamos que necesitamos configurar el valor de `RHOSTS`.

![imagen2](./images/Screenshot_4.png)

5. Configuramos `RHOSTS` con la dirección IP del sistema que queremos atacar. Podemos obtener esta dirección IP utilizando `nmap`, ya que estamos en la misma red:

    set RHOSTS <dirección_IP_del_objetivo>

6. Una vez configurado `RHOSTS`, ejecutamos el exploit utilizando el comando `run` o `exploit`:

![imagen3](./images/Screenshot_5.png)


7. Después de que el exploit se complete con éxito, podemos verificar que estamos dentro del sistema de directorios de la máquina Windows utilizando el comando `pwd`.

![imagen4](./images/Screenshot_6.png)

<h3>GLASSFISH</h3>


Lo primero que hemos de hacer es crear dentro del escritorio de kali dos archivos: user.txt y pass.txt. Dentro de dichos archivos debemos escribir el usuario y contraseña, que en este caso son `admin` y `sploit`.


1.Al igual que en el ejemplo de eternalblue, lo que he hecho ha sido buscar la vulnerabilidad `glassfish` utilizando el comando `search glassfish`.

![glassfish1](./images/glassfish1.png)

2.Usamos el comando `use 1` para seleccionar esa vulnerabilidad.

3.Ahora podemos usar los comandos `show options` u `options` para ver qué opciones son configurables en este exploit

![glassfish2](./images/glassfish2.png)

4.Pasamos a configurar el sploit

![glassfish3](./images/glassfish3.png)

y añadimos las rutas de el archivo de contraseña y usuario. Después usamos `run` para hacer funcionar el exploit.

![glassfish4](./images/glassfish4.png)

5. Ahora simplemente nos vamos al navegador y ponemos la dirección ip del windows en el que estamos usando el sploit y el puerto, y eso nos permitirá entrar en el glassfish del windows.

![glassfish5](./images/glassfish5.png)












<h2>LINUX</h2>

Para la parte de *Linux* mostraremos en 1º lugar una vulnerabilidad por la red.

1. Si entramos en un navegador y buscamos la ip de la máquina victima podemos ver que de normal tiene un listado de directorios que revela información sobre el servicio de base de datos, la máquina y el puerto usado, además de dejar opción a poder descargar cualquier archivo del servidor sin logearte.

![imagen5](./images/Screenshot_7.png)

2. Dentro de la terminal de metasploit hemos buscado algún exploit de ssh.

![imagen6](./images/Screenshot_7.1.png)

3. Para precisar más la busqueda hemos buscado alguno que tuviera que ver con las credenciales de inicio de sesión:

![imagen7](./images/Screenshot_7.2.png)

4. El exploit ssh_login del modulo scanner funciona leyendo un fichero de texto con los nombre de los usuarios y otro fichero que almacena posibles contraseñas (Son obligatorios para la ejecución del escaner). Ademas de colocar en el RHOSTS la ip de nuestra victima.

![imagen8](./images/Screenshot_8.png)

![imagen9](./images/Screenshot_8.1.png)

5. Podemos observar como nos muestra por pantalla el usuario y la contraseña de dicho usuario.

![imagen10](./images/Screenshot_8.2.png)
