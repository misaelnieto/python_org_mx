LEEME PRIMERO PORFAVOR!
=======================

¡Hola! (quien quiera que seas).

Antes de que empieces a tirar flamas y a modificar los archivos .cfg
sin documentar cambios en GIT, déjame hacer una explicación de lo que
estoy haciendo aquí. ¿Comenzamos?

(-) **base.conf**: Este archivo contiene la configuración base del
buildout. Por el momento solo contiene, como partes, a la instancia de
Plone. También contiene la información de *versions.cfg* y de
*puertos.cfg*, los *find-links*, toda la lista de huevos, de slugs
*zcml* y de huevos administrados con *mr.developer*.

(-) **deployment.conf**: Este archivo contiene toda la configuración
del buildout para cuando ya se va a instalar el sitio en linea y se va
a poner en producción. Contiene configuración de *varnish*, *supervisor* y
*repozo* (respaldos). Ahí debería de caber otra configuración como
puede ser *pound*, *munin*, o lo que se nos ocurra.

(-) **development.conf**: En este archivo metí varias utilerías útiles
para cuando estamos en modo desarrollo, pero que no nos sirven de nada
en producción.

¿Cómo las uso?
---------------

(1) Para ejecutar el bootstrap.py:

    python2.6 bootstrap.py -c base.conf

(esto construye el ejecutable *bin/buildout*)

(2) Para ejecutar el buildout minimo (solo construiye plone):

    bin/buildout -c base.conf

(3) El buildout de desarrollo construirá los ctags y los colocará en
el directorio var/ctags. Solo tienes que decirle a *vim* o *emacs* dónde
tomarlos. Para *emac*s es *var/ctags/TAGS* y para *vim* es
*var/ctags/tags*. 
Y para construirlo:

    bin/buildout -c development.conf

(4) Y para construir un buildout para producción es:

    bin/buildout -c deployment.conf

(5) **¡CUIDADO!** Si corres primero el buildout para *deployment.conf*
y después corres el de *base.conf* todas las partes del buildout que
no estén listadas en el *parts* de  *base.conf* serán
desinstaladas. Ya has sido advertido.

Y eso es todo!
Ahora si, a hacer lo que tienes que hacer!


