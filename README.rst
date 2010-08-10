=============
Introducción
=============

Este es el buildout_ que se usa para el sitio de PythonMexico.org basado en Plone 
3.3.5. El hosting y la administración de este sitio corren por cuenta de 
`iServices de México`_.

.. _buildout: http://www.buildout.org/
.. _`iServices de México`: http://iservices.com.mx

¿Cómo instalarlo?
-----------------

Voy a describir los pasos requeridos para que puedas instalar una copia idéntica 
del sitio de la comunidad de PythonMexico. Estas instrucciones las escribí para 
una máquina con Ubuntu 10.04.


Instalación de dependencias
~~~~~~~~~~~~~~~~~~~~~~~~~~~

    $ sudo aptitude install build-essential git-core subversion zlib1g-dev
    
Compilación de Python 2.4
~~~~~~~~~~~~~~~~~~~~~~~~~~

Los repositorios de Ubuntu 10.04 ya no traen Python 2.4. Tendremos que bajarlo y 
compilarlo a mano. Si tienes algo de experiencia con la línea de comandos, no tendrás 
problemas.

Primero hay que bajar el código fuente de python,

    $ wget http://www.python.org/ftp/python/2.4.6/Python-2.4.6.tar.bz2

después hay que descomprimirlo,
    
    $ tar -xjf Python-2.4.6.tar.bz2
    
    $ cd Python-2.4.6
    
Y por último construirlo e instalarlo. Esta vez instalaremos Python2.4 en el 
directorio ``/opt/Python2.4`` para que no interfiera con la instalación de Python 
2.6 que ubuntu trae por defecto.
    
    $ sudo mkdir -p /opt/Python2.4
    $ ./configure --prefix=/opt/python2.4 && make && sudo make install

Dependencias de buildout
~~~~~~~~~~~~~~~~~~~~~~~~~

Plone es un software muy complejo. La mejor manera de instalarlo es usando 
Buildout. Para ello necesitamos instalar manualmente PIP_ y ZopeSkel_:

.. _PIP: http://pip.openplans.org/
.. _ZopeSkel: http://plone.org/products/zopeskel

Primero PIP:

    $ wget http://peak.telecommunity.com/dist/ez_setup.py
    
    $ sudo /opt/Python2.4/bin/python2.4 ez_setup.py
    
    $ sudo /opt/Python2.4/bin/easy_install pip
    

Después ZopeSkel:

    $ sudo /opt/Python2.4/bin/pip install ZopeSkel

    
Construir el Buildout
~~~~~~~~~~~~~~~~~~~~~~

Primero hay que obtener un clon del Buildout.

    $ git clone git://github.com/tzicatl/python_org_mx.git
    
Después hay que ejecutar el script ``bootstrap.py``:

    $ /opt/Python2.4/bin/python2.4 bootstrap.py
    
Y, por último, ejecutar el recien creado script ``bin/buildout``:

    $ bin/buildout
    
Este último comando descargará todo el software necesario para poder ejecutar 
Plone 3.3.5 con todos productos usados en la web de pythonmexico.

Cuando termine el buildout, podrás ejecutar Plone con el siguiente comando:

    $ bin/instance fg
    
Esto ejecutará plone en modo ``foreground`` y el sitio estará accesible en 
http://localhost:8080/


Configurar Plone
~~~~~~~~~~~~~~~~~

Abre en tu navegador la siguiente URL: http://localhost:8080/manage_main. Se te 
pedirá un nombre de usuario y contraseña. Por default se ha configurado una 
cuenta joe_ con el nombre ``admin``.

.. _joe: http://www.answers.com/topic/joe-account

La página que se te presenta puede parecer un poco complicada, pero es cuestion 
de aprender a usarla. El sitio plone aún no está configurado del todo, es 
necesario agregar lo que se conoce como "una instancia de Plone". 

De menú descolgable (El único que hay), selecciona ``Plone Site`` y presiona 
el botón ``Add`` y llena el formulario de esta manera:

    Id: pythonmexico
    Title: Sitio de la comunidad de Python en méxico
    Description: Noticias, eventos y manuales útiles para la comunidad de Python en México.
    Extension Profiles: Plone Help Center, Python Theme, Twitter Portlet.
    

Haz click en el botón: ``Add`` y después abre esta página en el navegador:
http://localhost/pythonmexico 

Listo. Ya tienes tu copia de PythonMexico en tu computadora.



Colaboradores
--------------

`iServices de México`_. - http://iservices.com.mx

`Noe Nieto`_ - tzicatl_arroba_gmail.com
Erik Rivera - erik_arroba_gmail.com



.. _`iServices de México`: http://iservices.com.mx
.. _`Noe Nieto: http://noenieto.com

Este documento está escrito en formato reST.

.. _reST: http://docutils.sourceforge.net/rst.html

