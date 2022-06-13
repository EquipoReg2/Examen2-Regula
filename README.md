# Examen #2 Regularización
###### <sub> </sub>
## Contenido
1. [Resumen](#Resumen) 
2. [Cliente emisor](#Cliente-emisor)
3. [Servidor](#Servidor)
4. [Página del juego](#Pagina)
5. [Cliente receptor](#Cliente-receptor)

# Resumen 
<div align="justify">
</A><i>Por medio de hardware realizar acciones en una página web utilizando un servidor con WebSockets.</i>

![Sistema 1](https://github.com/EquipoDinamit/Examen3/blob/main/imagenes/indicaciones.png "Diagrama del sistema")

Este sistema está compuesto de 3 bloques independientes que interactúan entre sí. Dos de los 3 bloques son clientes, un <b>cliente emisor</b> (controlado por hardware), un <b>cliente receptor</b> (página web con html) y el <b>servidor</b> que permite la comunicación entre los dos clientes con el objetivo de mover objetos o  de realizar diferentes acciones en la página web con la información que envía el bloque emisor.
</div>

<div align="right">
 
<sub>[Contenido](#-)</sub>
</div> 

# Cliente emisor 

### Circuito
<div align="justify">
Los materiales que se utilizaron son: <br>
<ul>
 <li>Arduino</li>
 <li>Joystick</li>
 <li>5 cables hembra/macho</li>
</ul>

El circuito a armar:

<img src="https://github.com/EquipoReg2/Examen2-Regula/blob/main/imagenes/joystick.jpg" alt="Circuito Emisor" style="height: 100%; width:100%;"/>

Es bastante sencilla la composición del circuito ya que el mismo joystick indica los puertos que necesitan ser conectados al arduino, los cuales son 5V, GND, A0, A1 y 2, siendo un total de 5 puertos.
</div>
 
### Código
<div align="justify">
<b>ArduinoEmisor.ino:</b> 
<ul>
 <li>Se abre el archivo en el IDE de Arduino</li>
 <li>En la pestaña de <b>Herramientas</b> se selecciona la placa en la que se subirá el codigo, así como el puerto en el que se encuentre conectado el microocontrolador
 </li>
 <li>Se selecciona el boton de <b>Subir</b></li>
</ul>
<p>Se estima que el código <b>ArduinoEmisor.ino</b> nos otorgue 3 distintos valores mediante el joystick los cuales son 2, 4 y 5 que serán leídos por el código <b>ClienteEmisor.py</b> y enviados al servidor</p>

<b>ClienteEmisor.py:</b>
<ul>
 <li>Desde la ubicacion del archivo <b>Cliente emisor.py</b> abrir el <b>cmd</b> y ejecutar el programa</li>
 <ul>
  <li>En un ejemplo:<br>
    <i>C:\Users\minim\Desktop\Sistema de Computo y Redes\Examen></i><b>python ClienteEmisor.py</b><br></li>
 </ul>
</ul>
 
Lo que se espera del código <b>ClienteEmisor.py</b> es que pueda conectarse con el servidor cuando el <b>main.js</b> se esté ejecutando y que le mande la información leída del arduino para que el servidor la envíe al cliente receptor.
</div>

<img src="https://github.com/EquipoReg2/Examen2-Regula/blob/main/imagenes/emisor.jpg" alt="Circuito Emisor" style="height: 100%; width:100%;"/>

<div align="right">
 
<sub>[Contenido](#-)</sub>
</div> 

# Servidor 
<div align="justify">
Para tener el servidor desde tu computadora hacer lo siguiente:<br>
En caso de tener un modem de INFINITUM se ingresa a http://192.168.1.254/login.html y se busca el apartado <b>DMZ</b> (Demilitarized Zone o Zona desmilitarizada) y se activa la función DMZ<br>
Se busca el apartado <b>Mapeo de Puertos/Port Mapping</b> y una vez ahí, en la sección <b>Reenvio de Puertos</b> se define un puerto nuevo y se especifica que se trata de un Protocolo TCP<br>
 
Nota: Es importante guardar los datos de la <b>Dirección IP Pública</b>
</div>
 
### Código
<div align="justify">
<b>main.js:</b><br>
Si es la primera vez que se ejecuta el servidor es necesario hacer lo siguiente:
<ul>
 <li>Tener descargados por lo menos el <b>package.json</b> y el servidor <b>main.js</b> en la carpeta que se está trabajando</li>
 <li>Desde la ubicación dentro de la carpeta se abre la consola (<b>cmd</b>) y se escribe lo siguiente:
  <ul>
   <li>En un ejemplo:<br>
    <i>C:\Users\minim\Desktop\Sistema de Computo y Redes\Examen></i><b>npm install</b><br></li>
  </ul></ul>
  
  <img src="https://github.com/EquipoDinamit/Examen3/blob/main/imagenes/npminstall.png" alt="Circuito Emisor" style="height: 100%; width:100%;"/><br>
 </div>
  Eso crea dos nuevos elementos en la carpeta de trabajo, una carpeta llamada <b>node_modules</b> donde se almacenarían todas las dependencias y librerías que utilizas en tu proyecto nodejs y el <b>package-lock.json</b> que es ejerce como un historial de las operaciones <i>npm</i> que modifiquen el <b>node_modules</b>.</li>
  Tambien es necesario instalar nodemon y socket.io, estos se instalan con los siguientes comandos: <b>npm install --save nodemon</b> y <b>npm install socket.io</b>
 <ul>
 <li>Ahora desde la consola en la carpeta de trabajo se escribe lo siguiente:
 <ul>
   <li>En un ejemplo:<br>
    <i>C:\Users\minim\Desktop\Sistema de Computo y Redes\Examen></i><b>npm start</b><br></li>
  </ul>
 Como resultado en la consola se despliega el mensaje <b>Servidor corriendo en http://localhost:80</b>, por lo que se debería poder recibir conecciones desde el <b>ClienteEmisor.py</b>. Indicando que todo funciona perfectamente</li>
</ul>
 
<img src="https://github.com/EquipoDinamit/Examen3/blob/main/imagenes/servidor.png" alt="Circuito Emisor" style="height: 100%; width:100%;"/>

 Lo que se espera del código <b>main.js</b> es que reciba la conexión del <b>cliente emisor</b> y que se conecte con el <b>cliente receptor</b> para enviar los datos leídos del arduino y así poder realizar diferentes acciones en el <b>cliente receptor</b>
<div/>
 
<div align="right">
 
<sub>[Contenido](#-)</sub>
</div> 
 
# Cliente receptor 
<div align="justify">
 El cliente receptor cuenta con su html donde se encuentra el juego space invaders como se ve adelante:
 <ul>
 La página a la que se accede es <b>index.html</b>
  </div>
 
  <img src="https://github.com/EquipoDinamit/Examen3/blob/main/imagenes/login.png" alt="Circuito Emisor" style="height: 100%; width:100%;"/></li>
 
 <ul>
  <li>Una vez dentro de la página, se presiona el joystick para dar inicio al juego y listo, a jugar.</li>
 </ul>
 </div>
 
 <img src="https://github.com/EquipoDinamit/Examen3/blob/main/imagenes/inicio.png" alt="Circuito Emisor" style="height: 100%; width:100%;"/>
 

Le rezo a dios para pasar esta materia porfavor

<div align="right">
 
<sub>[Contenido](#-)</sub>
</div>  
