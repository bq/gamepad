=======
RoboPad
=======

RoboPad es una aplicación Android para controlar robots a través del Bluetooth del dispositivo móvil. Puedes elegir distintos tipos de robots con sus mandos de control específicos de cada uno. Todos los robots deben utilizar una placa Arduino y un módulo Bluetooth.

Los tipos de robots que se pueden seleccionar hoy en día son aquellos diseñados por la empresa Bq, además de cualquier otro que sea controlado por una placa Arduino.

Puedes usar una impresora 3D para crear tu PrintBot (Renacuajo, Escarabajo y Rhino). Tanto los archivos con las partes imprimibles como el código Arduino de cada uno de los printbots de Bq se puede descargar desde la web http://diwo.bq.com/tag/printbot/

Hay un mando de control para robots genéricos que te permite controlar tu propio robot con hasta 6 funcionalidades más la cruceta de movimientos o bien aumentar el número de funcionalidades de algún printbot ya existente con los 6 botones de comandos.

Estos 6 botones mandan el siguiente carácter a la placa Arduino:

| Botón 1 - '1'
| Botón 2 - '2'
| Botón 3 - '3'
| Botón 4 - '4'
| Botón 5 - '5'
| Botón 6 - '6'

Las opciones de robot genérico, Cangrejo y Rhino estás ocultas ya que su UI no está terminada. Puedes hacerlos visibles en el layout ``activity_select_robot.xml``.

Si tienes alguna duda puedes consultarnos mandando un correo a diy@bq.com.


Características
===============

#. Controla robots que utilicen una placa Arduino a través del Bluetooth de tu dispositivo móvil

#. 6 botones en el tipo de robot genérico para usar en tus propios robots

#. Mandos de control específicos para los PrintBots Renacuajo, Escarabajo, Evolution, Rhino y Cangrejo de bq. Ahora, algunos también pueden activar el modo siguelíneas, el modo huye luz o el modo esquiva obstáculos.

#. Administración de la conexión Bluetooth para ahorrar batería


Instalación
===========

#. RoboPad depende de la biblioteca droid2ino. Clona el repositorio droid2ino::

    git clone https://github.com/bq/droid2ino.git

#. Instala la biblioteca droid2ino en tu repositorio local::
  
    cd droid2ino/droid2ino
    gradle install

#. Instala `Android Studio <https://developer.android.com/sdk/installing/studio.html>`_ y `Gradle <http://www.gradle.org/downloads>`_.

#. Si usas Linux de 64 bits, necesitarás instalar ia32-libs-multiarch::

	sudo apt-get update
	sudo apt-get upgrade
	sudo apt-get install ia32-libs-multiarch 

#. Clona el repositorio RoboPad::
	
	git clone https://github.com/bq/robopad.git

#. En Android Studio, ve a ``File`` > ``Open`` y selecciona el proyecto RoboPad clonado previamente.

#. Mete el código Arduino adecuado a tu robot. Puedes encontrarlo en la carpeta Arduino de este proyecto o en la `web de DIWO de Bq <http://diwo.bq.com/robopad-3/>`_ 
   
#. Para instalar el firmware del printbot Cangrejo que se encuentra en la carpeta de Arduino, tienes que copiar la carpeta ``Oscillator`` (que está en la carpeta Oscillator_Lib) en la carpeta ``libraries``  en la carpeta donde has instalado el programa de Arduino. Puedes encontrar información más detallada para hacer esto en la  `documentación de la web de Arduino <http://arduino.cc/en/Guide/Libraries>`_. 


Requisitos
==========


- `Java JDK <http://www.oracle.com/technetwork/es/java/javase/downloads/jdk7-downloads-1880260.html>`_ 

- `Android Studio <https://developer.android.com/sdk/installing/studio.html>`_ 
  
- `Maven <http://maven.apache.org/download.cgi>`_. Si estás en Ubuntu::
    
    sudo apt-get update
    sudo apt-get install maven

- `Gradle <http://www.gradle.org/downloads>`_ versión 3.3
  
- `Arduino IDE <http://arduino.cc/en/Main/Software#.UzBT5HX5Pj4>`_ 

- La placa Arduino con un módulo Bluetooth


Limitaciones
============

- Para evitar el problema de mostrar mensajes recibidos por parte de la placa Arduino vacíos o partidos, la librería droid2ino utiliza una serie de carácteres de escape. 
 
  - Carácter de escape de inicio del mensaje: ``&&`` 

  - Carácter de escape de fin del mensaje : ``%%``

  Por lo tanto, un ejemplo de cómo el programa Arduino tiene que mandar un mesaje sería::

	  &&Hola mundo desde Arduino%%

- El mando de control de robot genérico tiene 6 botones que pueden ser usados para dotar a tu propio robot de más funcionalidad. Estos botones mandan los mensajes '1', '2', '3', '4', '5' y '6' respectivamnete a la placa Arduino.


Licencia
========

RoboPad es distribuido en términos de la licencia GPL. Consulte la web http://www.gnu.org/licenses/ para más detalles.
