# Mi Configuración de Vim

El propósito de este documento es recopilar todas las opciones disponibles en mi
configuración para poner un poco de orden en la misma y servirme de recordatorio
de todo lo que tengo disponible. Evidentemente no pretendo replicar la ayuda de
vim ni de los plugins, solo destacar aquellas opciones que puedo necesitar en un
determinado momento. Del mismo modo puede servir de una suerte de manual de
instrucciones para aquel que decida clonar esta configuración.

Debido a la naturaleza altamente "mutante" de mi configuración, este documento
estará sujeto del mismo modo a un numero elevado de modificaciones en el futuro.

A todo esto habría que sumarle todo lo que Vim aporta de serie, que no es poco.

> La tecla `<Leader>` la tengo mapeada a `,` y la tecla `<LocalLeader>` la tengo
mapeada a la tecla espaciadora

    DISCLAIMER & AGRADECIMIENTOS

    Evidentemente es necesario un conocimiento previo de Vim para sacarle todo
    el partido posible a esta configuración, del mismo modo que será necesario
    recurrir a la ayuda de ciertos plugins para familiarizarse con ellos más
    allá de las pautas que doy en este documento.

    Esta configuración está basada en las de muchos otros, tantos que ni los
    recuerdo a todos y seria bastante injusto recordar a algunos y omitir a
    otros. Pero gracias a que muchos comparten generosamente su configuración,
    yo he llegado a la mía y sirva esta documento también de pequeña
    compensación por lo mucho que otros me han aportado. Y gracias también a
    todos aquellos desarrolladores que crearon los plugins que incluyo (e incluí
    en el pasado) por que sin su maravillosa contribución y generosidad al
    compartirlos con el resto del mundo, esta configuración no sería posible.

## Unite

Unite es una interfaz que unifica varios 'resultados de búsquedas' bajo un mismo
aspecto y siguiendo el comportamiento por defecto de Vim (modal). Es casi una
API sobre la que podemos construir nuestras propias soluciones. Sirve tanto para
abrir un archivo, como para cambiar de buffer, cambiar de esquema de color o
para hacer una búsqueda con regex (vimgrep, grep, Ack, ag, ...). Sirve hasta
para consultar los registros, ayuda, comandos... Resumiendo, es una navaja suiza
que bien empleada nos permite sustituir un varios plugins distintos por uno
solo (en este caso: CtrlP, Ack, YankRing, TagmaTasks y Tagbar).

> Una de las principales ventajas de Unite es que me permite subsanar uno de los
problemas que intentaba solucionar inicialmente con este documento, que es el
recordar todas las opciones y atajos que con tanto esfuerzo y tiempo he
incorporado a Vim. Es muy normal que tengamos disponible un plugin que usamos de
cuando en cuando, lo tengamos personalizado y cuando vayamos a emplearlo no
recordemos ni todas sus opciones, ni los atajos. Pues bien, con Unite es
sencillo crear un menú para ese plugin donde mostremos las opciones que tenemos
para el y los atajos que les hemos asignado y gracias otra vez a la magia de
Unite, ni siquiera necesitamos recordar el atajo a este menú, podemos buscarlo
dentro del indice de menús de Unite. Problema resuelto de forma rápida y
elegante.

El mayor inconveniente de Unite y a su vez una de sus mayores ventajas es que no
viene configurado apenas, dejando a nuestro gusto y responsabilidad el adaptarlo
a nuestro modo de trabajo.

### Fuentes y Menus

Yo he configurado Unite siguiendo dos vías distintas, por un lado lo utilizo
para acceder a fuentes directas (lo que Unite denomina *sources*) a través de un
atajo usando la tecla `<Leader>` y por otro lado llamando a menús usando la
tecla `<LocalLeader>`

- Las __fuentes__ llamadas directamente a través de un atajo con `<Leader>` las uso
  para aquellas tareas más comunes como abrir archivos, buscar dentro del
  archivo, hacer una búsqueda de archivos mediante regex (ag, ack, grep), etc.
  Un ejemplo de como abrir un archivo con Unite.

![unite_file](http://joedicastro.com/static/pictures/unite_file.gif "unite file")

- Los __menus__ los uso para agrupar las opciones bien por plugins o bien por
  funcionalidad. Ademas muestro los atajos en aquellas opciones que tengo
  mapeadas directamente, esto me permite no tener que consultar mi `~/.vimrc`
  para recordar cuales eran cuando me olvido de alguno. Un ejemplo que muestra
  las opciones que tengo disponibles para gestionar un repositorio git desde
  Vim.

![unite_git](http://joedicastro.com/static/pictures/unite_git.gif "unite_git")

También para no tener que recordar todos los menús que he creado, hay un menú
maestro que me permite acceder a cada uno de ellos y ver los atajos asociados a
cada uno de ellos. Unite posee un mecanismo que nos permite acceder a una lista
de menús generada automáticamente, y aunque en este caso ni se muestran
ordenados ni se pueden ver los atajos asociados directamente yo he creado las
descripciones de los menús de manera que se puedan ver los atajos. Es lo que el
comando `:menu` de Vim debería haber sido: cómodo, intuitivo y de fácil
navegación.

- `<LocalLeader>u` o `:Unite menu` muestra los menús disponibles


### Navegacion dentro de Unite

TODO: completar este apartado

## Gestion de Plugins

![neobundle](http://joedicastro.com/static/pictures/unite_menu_neobundle.png "neobundle")

Un plugin para gobernarlos a todos! NeoBundle me permite administrar el resto de
los plugins, a el mismo incluido. __A su vez lo tengo configurado para que se
instale a si mismo la primera vez que se ejecute vim con esta configuración
(también instala automáticamente el resto de plugins).__

Las ventajas de este plugin frente a otros similares como Vundle son las
siguientes:

- Permite usar plugins desde otras fuentes distintas a git (svn, hg, dir, ...)
- Permite establecer la revisión exacta que queremos emplear
- Permite marcar plugins como no actualizables
- Permite cargar los plugins bajo demanda, no al principio, para agilizar el
  arranque de Vim y el consumo de recursos
- Permite añadir multitud de opciones a cada plugin, como por ejemplo que se
  haga el `build` de forma automática si es necesario al instalar/actualizar
- Y muchas mas posibilidades, sobre todo si también usamos 'Vimproc' y 'Unite'
  del mismo autor

La mejor manera de usar NeoBundle es a través de Unite

__Unite__

- `<LocalLeader>n` o `:Unite menu:neobundle`, muestra un menú con las opciones
  de Neobundle

### Menu

Voy a detallar aquí lo que hace cada uno de las entradas del menu:vim

- *neobundle* nos muestra una lista de los plugins instalados. Seleccionándolos
  (uno o varios) podemos realizar varias acciones sobre ellos

- *log* muestra el registro de operaciones de neobundle

- *lazy* nos muestra la lista de los plugins que tenemos configurados para ser
  cargados bajo demanda

- *update* actualiza automáticamente todos los plugins (e instala aquellos que
  no lo estén)

- *search* búsqueda de plugins por el nombre en vim.org y GitHub (pueden
  aparecer duplicados los que se encuentren en ambos sitios)

- *install* instala aquellos plugins que no hayan sido instalados pero si estén
  en el vimrc

- *check* comprueba que todos los plugins incluidos en .vimrc estén instalados,
  de lo contrario nos preguntara por su instalación

- *docs* instala la documentación de todos los plugins de forma manual

- *clean* elimina aquellos plugins que ya no estén configurados pero aun
  permanezcan en el disco

- *list* lista todos los plugins instalados

- *direct edit* sirve para editar el archivo `direct_bundles.vim` donde
  neobundle guarda aquellos plugins que se han instalado directamente (por
  ejemplo a través de la búsqueda)

> __Actualización de Plugins__

> NeoBundle es una muy buena y potente herramienta que nos permite administrar
de forma muy sencilla nuestros plugins. Pero es una herramienta que conviene
utilizar con cuidado, sentido común y guardando unas ciertas precauciones, sobre
todo si usamos vim como herramienta profesional.

> Dado que en mi caso y en el de muchos otros, instalamos y actualizamos varios
plugins directamente desde el repositorio git, esto nos expone a actualizaciones
inestables de los mismos.

> Este es mi modo de actualizar los plugins que puede servir como guia u
orientación de como hacerlo sin que nuestro flujo de trabajo se vea
interrumpido.

> Lo primero es aclarar que mi configuración de vim está situada en el
directorio `$HOME/dotfiles/vim` y utilizo enlaces simbólicos para que vim pueda
localizar la configuración que espera por defecto. En concreto lo tengo
establecido de esta manera:

  > - `~/.vim` es un enlace simbólico que apunta a `~/dotfiles/vim`
  > - `~/.vimrc` es un enlace simbólico que apunta a `~/dotfiles/vim/vimrc`

> De modo que cuando quiero hacer una actualización de los plugins de vim, lo
único que tengo que hacer es crear una copia de la carpeta de vim en
`~/dotfiles` para tener un backup en caso de que algún plugin no funcione como
es debido.

> De hecho, hago esto sin salir de Vim y con la ayuda de ranger, en sencillos
pasos:

>    1. entro en ranger desde vim pulsando `<Leader>rt`
>    2. voy a la carpeta `vim` en `~/dotfiles` y creo una copia pulsando `yy` y
>       luego `pp` y me crea una copia llamada `vim_`
>    3. actualizo los plugins de vim con `:BundleUpdate`
>    4. sigo trabajando con normalidad
>    5. si veo que algún plugin se ha vuelto inestable durante la actualización
>       y lo necesito para seguir trabajando, simplemente borro la carpeta
>       `~/dotfiles/vim` y renombro la copia en `~/dotfiles/vim_` a
>       `~/dotfiles/vim`. Con salir de vim y volver a entrar tenemos una
>       configuración probada y completamente funcional sin esfuerzo.

> Usando este procedimiento o algo similar nos ahorramos muchos disgustos a la
hora de realizar las actualizaciones. Evidentemente, en caso de que solo falle
un plugin siempre podemos sustituir únicamente la carpeta de ese plugin dentro
de `~/dotfiles/vim/bundle` en lugar de toda la configuración de Vim.

> __Alternativa__

> Otra opción la tenemos a través de NeoBundle, que nos permite especificar la
revisión que queremos instalar de un plugin, e incluso nos permite decirle que
no se actualice nunca, si no nos interesa actualizarlo.


## Esquemas de color

![unite_colorscheme](http://joedicastro.com/static/pictures/unite_colorscheme.gif "unite colorscheme")

Para cambiar de esquemas de color podemos hacerlo a través de Unite:

__Unite__

- `<LocalLeader>v` o `:Unite menu:vim` accedemos al menú *vim* donde
  podemos cambiar el esquema seleccionando la opción correspondiente
- `:Unite colorscheme -auto-preview` seleccionamos el esquema de la lista con
  previsualización del mismo



## Navegacion

![unite navegacion](http://joedicastro.com/static/pictures/unite_menu_navegacion.png "unite navegacion")

>   __Atajos__

> Ademas de las opciones disponibles en el menú tengo configurados una serie de
> atajos que hacen mucho más sencillo el desplazarse entre ventanas.

>   - `<C-H>` desplazamiento a la siguiente ventana a la izquierda
>   - `<C-J>` desplazamiento a la ventana inferior
>   - `<C-K>` desplazamiento a la ventana superior
>   - `<C-L>` desplazamiento a la siguiente ventana a la derecha

__Unite__

`<LocalLeader>b` o `:Unite menu:navegacion` muestra el menú de navegación

### Menu

- Las tres primeras entradas del menú nos permiten acceder rápidamente al buffer,
ventana o pestaña que deseemos con rapidez.

- *location list* y *quickfix* nos dejan acceder a ambas ventanas a través de la
interfaz de Unite

- *redimensionar ventanas* utiliza el plugin winresizer para redimensionar
  (cambiar de tamaño) muy fácilmente las ventanas de vim.
   > __Atajos__
   >
   > - `h`, `j`, `k`, `l` mueve el divisor de ventanas usando los movimientos
   >   típicos de Vim
   > - `<CR>` finaliza el redimensionado y `q` lo cancela

- las dos siguientes entradas nos permiten crear nuevas ventanas, tanto en
  posición vertical como horizontal y la siguiente opción nos permite cerrar
  cualquier ventana abierta.

- *cerrar/abrir ventana quickfix* nos abre/cierra la ventana quickfix y a
  diferencia de la quinta entrada no la muestra a través de Unite.

- *scratch* nos crea un nuevo buffer temporal en el que no se guardara nada de
  lo que editemos en ella, el contenido es descartado en cuanto cerramos la
  aplicación. La ventana aparecerá siempre encima de la ventana actual

- *zoom* hace zoom sobre una ventana, ocultando el resto.


## Sesiones

![unite sesiones](http://joedicastro.com/static/pictures/unite_menu_sesiones.png "unite sesiones")

Este menú nos permite guardar las sesiones de trabajo, bien bajo el nombre por
defecto o uno personalizado para que posteriormente podamos cargarlas y seguir
trabajando donde lo habíamos dejado.

__Unite__

`<LocalLeader>h` o `:Unite menu:sesiones` muestra el menú de sesiones


## Marcadores

![unite marcadores](http://joedicastro.com/static/pictures/unite_menu_marcadores.png "unite marcadores")

Con las entradas de este menú podemos guardar marcadores de los archivos que
queramos para poder abrirlos de forma rápida y directa. Nos permite añadir una
descripción para cada uno y elegir el archivo donde guardarlos.


__Unite__

`<LocalLeader>m` o `:Unite menu:marcadores` muestra el menú de marcadores


## Edicion de texto

![unite texto](http://joedicastro.com/static/pictures/unite_menu_texto.png "unite texto")

Este menú aglutina algunas de las funciones que podemos usar para la edición de
texto.

__Unite__

`<LocalLeader>e` o `:Unite menu:texto` muestra el menú de sesiones

### Menu

- *activar/desactivar el resaltado de búsqueda* nos sirve para ocultar el
   resaltado de los resultados una vez hemos realizado la búsqueda

- *conmutar los números de linea* conmuta entre no mostrar los números de línea,
  mostrarlos relativos y mostrarlos absolutos.

- *mostrar caracteres no imprimibles* nos conmuta la visualización de los
  caracteres no visibles tales como tabulados, retornos de carro, espacios a
  final de linea, etc

- las tres entradas siguientes nos permiten plegar/desplegar los pliegues que
  tengamos en nuestro documento, bien sea individualmente o todos a la vez

- las siguientes 3 entradas nos sirven para pegar/copiar al portapapeles del
  sistema y para activar/desactivar el paste mode (todo se pega literalmente)

- la siguiente entrada elimina esos espacios que se quedan a veces al final de
  la linea y que suelen ser casi siempre innecesarios y sin cometido alguno
  (excepto quizás en Markdown)

- *estadísticas de texto para la posición actual* muestra en la linea de
  comandos el numero de lineas, palabras, caracteres y bytes (totales y de la
  posición actual)

- la entrada que le sigue muestra una lista de palabras con la frecuencia con la
  que aparece cada palabra para un texto dado

- *muestra los dígrafos disponibles* muestra una tabla con todos los dígrafos
  disponibles y los caracteres necesarios para generarlos
   > Los dígrafos son caracteres especiales que se forman a partir otros dos

- *inserta texto lorem ipsum* sirve para generar texto aleatorio para rellenar
  borradores y pruebas de diseño, muy usado en diseño web. Genera el famoso
  texto [Lorem Ipsum][lorem]

   [lorem]: http://es.wikipedia.org/wiki/Lorem_ipsum

- la ultima entrada muestra información ampliada sobre un carácter en la linea
  de comandos. Muestra el valor Unicode en decimal, hexadecimal, octal, el
  nombre Unicode, la HTML entity, el código Emoji y cualquier dígrafo
  disponible.

### Otras herramientas

A parte de las herramientas incluidas en el menú, disponemos de otra serie de
ellas para poder editar texto más fácilmente.

TODO: añadir text-objs


- __easydigraph__ sirve para insertar un dígrafo de forma bastante sencilla,
   sobre todo cuando se trata de insertar varios simultáneamente.

    ![easydigraph](http://joedicastro.com/static/pictures/easydigraph.gif "easydigraph")
    >
    > __Atajo__
    >
    > - `<Leader>dd {motion}` convierte en dígrafo la selección efectuada con el
    >   movimiento.

- __vim-commentary__ herramienta extremadamente sencilla para
  comentar/descomentar fragmentos de texto/código. Simplemente tenemos que
  pulsar un atajo seguido de un movimiento para comentar/descomentar o pulsar el
  atajo después de una selección visual.

    ![commentary](http://joedicastro.com/static/pictures/commentary.gif "commentary")

    > __Atajo__
    >
    >  - `<Leader>c` o `gc`

- __vim-surround__ nos sirve para "envolver" un objeto de texto de vim con un
  par de caracteres o etiquetas similares (paréntesis, comillas, etiquetas HTML,
  ...). También nos permite cambiar o eliminar los ya existentes.

    ![surround](http://joedicastro.com/static/pictures/surround.gif "surround")

    > __Atajos__

    > - `ys{motion or text-object}{char}` crear "envolvente" (*'your surround'*)
    > - `cs{orig_char}{dest_char}` cambiar "envolvente" (*'change surround'*)
    > - `ds{char}` eliminar "envolvente"  (*'delete surround'*)
    > - `S{char}` para usarlo en modo visual (solo para crear)

    > *Si elegimos el primer miembro de un par, e.g '(', entonces nos crea el
    > envolvente con un espacio entre el envolvente y la seleccion. Si elegimos el
    > ultimo miembro, e.g. ')', entonces nos lo crea sin los espacios.*

- __vim-speeddating__ sirve para incrementar/decrementar de forma inteligente
  valores de fechas y horas.

    ![speeddating](http://joedicastro.com/static/pictures/speeddating.gif "speeddating")

    > __Atajos__

    > - `<C-A>` Incrementa el valor bajo el cursor una unidad
    > - `<C-X>` Decrementa el valor bajo el cursor una unidad
    > - `d<C-A>` Cambia la fecha/hora bajo el cursor a la hora actual en UTC
    > - `d<C-X>` Cambia la fecha/hora bajo el cursor a la hora actual en local

- __vim-smartinput__ provee de autocompletado inteligente para pares de
  caracteres muy empleados en programación como son __(), {}, [], "", '', ``__

     El funcionamiento es muy sencillo, si escribimos el primero de este par de
  caracteres, aparece automáticamente el segundo y el cursor se mueve al interior
  de los mismos. Entonces escribimos lo que queremos y cuando acabemos solo
  tenemos que introducir el segundo carácter. Sin en cambio solo quisiéramos el
  primero, bastaría con pulsar la tecla __Delete__

    ![smartinput](http://joedicastro.com/static/pictures/smartinput.gif "smartinput")


- __neocomplete__ autocompleta palabras clave, métodos, ... con solo escribir
  las primeras letras.  Bien usado permite agilizar mucho la escritura de código
  o texto. Neocomplete es un plugin que mejora el autocompletado por defecto de
  Vim, con búsqueda con lógica difusa (fuzzy) al mismo tiempo que se escribe.
  Esta plagado de opciones y es completamente personalizable.

    ![neocomp](http://joedicastro.com/static/pictures/neocomp.gif "neocomp")

    > __Atajos__

    > - `<CR>`    inserta la palabra seleccionada
    > - `<C-N>`   nos desplaza a la palabra inferior en la lista de opciones
    > - `<C-P>`   nos desplaza a la palabra superior en la lista de opciones

## Revision de ortografia

![unite spell](http://joedicastro.com/static/pictures/unite_menu_spell.png "unite spell")

 Estas entradas sirven para la corrección ortográfica del texto y son
 suficientemente autoexplicativas por si mismas.

__Unite__

- `<LocalLeader>s` o `:Unite menu:ortografia` activa el menú con las opciones
  para la corrección ortográfica


## Busqueda de archivos (grep)

![unite grep](http://joedicastro.com/static/pictures/unite_menu_grep.png "unite grep")

Este menú contiene la opciones para búsqueda de archivos por su contenido o de
búsqueda de archivos de los que conocemos su nombre o parte de el pero no el
path completo donde se encuentran. Por esta razón separo estas herramientas de
la gestión de archivos, por que son herramientas para buscar nuestro archivo en
lugar de ir a tiro fijo.

__Unite__

- `<LocalLeader>a` o `:Unite menu:grep` activa el menú de búsqueda de archivos


### Menu

- la primera entrada es la clásica herramienta de búsqueda del contenido de un
  archivo a partir de un patrón basado en una expresión regular. Si tenemos
  instalada la utilidad `ag` usara esta, en su defecto la herramienta `ack` y en
  ausencia de ambas el clásico `grep`. Cuando la ejecutemos nos solicitara el
  directorio destino (target) donde realizar la búsqueda recursiva y luego la
  expresión regular (pattern).

- la siguiente entrada realiza exactamente la misma función pero limitándose a
  los archivos incluidos dentro del repositorio cuando nos encontremos dentro de
  un repositorio de git. Es decir, que buscaría dentro de los archivos que
  podemos listar con el comando `$ git ls-files`

- *find* realiza la búsqueda por el nombre del archivo empleando la conocida
  herramienta `find`

- *locate* también utiliza el nombre para buscar el archivo dentro de la base de
  datos de la herramienta `locate`

- *vimgrep* utiliza la herramienta interna de vim para realizar búsquedas en
  función de expresiones regulares, pero debido a su lentitud debería emplearse
  como ultimo recurso cuando no disponemos de las herramientas de la primera
  entrada.

## Busqueda dentro del buffer

![unite busquedas](http://joedicastro.com/static/pictures/unite_menu_busquedas.png "unite busquedas")

__Unite__

- `<LocalLeader>f` o `:Unite menu:busquedas` activa el menú de búsquedas

### Menu

- *linea* busca todas las lineas en las que aparezca la palabra (o parte de
  ella) que introduzcamos

- la siguiente entrada busca todas las lineas donde aparece la palabra que está
  situada bajo el cursor en el momento de activar la búsqueda

- *encabezados*  muestra todos los "encabezados" del documento y permite navegar
  entre ellos. Muy útil para navegar entre los headers de documentos Markdown
  como este, aunque soporta también varios tipos de archivo como el código fuente de
  distintos lenguajes donde muestra las etiquetas generadas por ctags

- *marcas* lista todas las marcas del archivo

- *pliegues* permite movernos entre los distintos pliegues

- *cambios*  muestra las lineas donde se han realizado cambios en el documento
  en orden temporal inverso (primero los mas recientes)

- *saltos* muestra una lista de los últimos saltos producidos

- *undos* la historia de cambios que podemos deshacer

- *tareas* visualiza las tareas pendientes para el buffer actual (o para una
  lista de archivos) y muestra marcas en la columna lateral izquierda de signos
  para cada una de las tareas. Estas tareas se definen por medio de palabras
  clave en el buffer, como __TODO__, __FIXME__, __NOTE__, __XXX__ , __COMBAK__ y
  __@todo__

### Otras herramientas

- __vim-signature__ un plugin que sirve para conmutar, mostrar y navegar por las
  marcas. Las marcas se muestran en la columna lateral de signos de Vim, a la
  izquierda de los números de línea.

    ![signature](http://joedicastro.com/static/pictures/signature.gif "signature")

    > __Atajos__

    > - Marcadores alfabéticos

    >   - `m[a-zA-Z]` conmuta la marca y la muestra/oculta
    >   -  `m,`       activa el siguiente marcador disponible
    >   -  `m<Space>` borra todos los marcadores
    >   -  <code>]`</code>      salta al marcador siguiente
    >   -  <code>[`</code>      salta al marcador previo
    >   -  `]'`       salta al comienzo de la siguiente línea que tenga un marcador
    >   -  `['`       salta al comienzo de la anterior línea que tenga un marcador

    > - Marcadores simbólicos

    >   -  `m[0-9]`       activa el marcador simbólico correspondiente `!@#$%^&*()`
    >   -  `m<S-[0-9]>`   eliminar todos los marcadores iguales
    >   -  `]-`           salta a la siguiente línea que tenga el mismo marcador
    >   -  `[-`           salta a la anterior línea que tenga el mismo marcador
    >   -  `m<BS>`        elimina todos los marcadores simbólicos


## Registros

![unite registros](http://joedicastro.com/static/pictures/unite_menu_registros.png "unite registros")

__Unite__

- `<LocalLeader>i` o `:Unite menu:registros` activa el menú de registros

### Menu

- *yanks* mantiene un registro de el texto que ha sido "yankeado" (copiado),
  borrado o cambiado. Está ordenado cronológicamente empezando por el más
  reciente

- *comandos* muestra la historia de los últimos comandos ejecutados en la linea
  de comandos

- *búsquedas* lista la ultimas búsquedas efectuadas

- *registros* enseña el contenido de los registros de Vim

- *mensajes* muestra el registro de mensajes de Vim (como el comando `:messages`)

- *deshacer* activa el plugin gundo que sirve para hacer mas amigable la
  utilización del árbol de deshacer de Vim. De esta manera podemos ver el árbol
  de los cambios realizados, previsualizar los cambios que vamos a realizar y
  saber a donde vamos a retornar antes de deshacer un cambio.

    ![gundo](http://joedicastro.com/static/pictures/gundo.gif "gundo")

## Archivos y directorios

![unite archivos](http://joedicastro.com/static/pictures/unite_menu_archivos.png "unite archivos")

__Unite__

- `<LocalLeader>o` o `:Unite menu:archivos` activa el menú de archivos y
  directorios

### Menu

- *abrir archivo* abre una lista de los archivos disponibles en el directorio de
  trabajo

- *abrir archivo reciente* muestra los últimos archivos abiertos

- *abrir archivo con búsqueda recursiva* no solo lista los archivos del
  directorio de trabajo si no que ademas incluye los de los subdirectorios

- las tres entradas siguientes son similares a las de arriba trabajando con
  directorios en lugar de archivos

- *crear nuevo directorio* nos permite crear un nuevo directorio sin necesidad
  de abrir un explorador de archivos

- *cambiar directorio de trabajo* nos permite cambiar el directorio de trabajo
  actual independientemente del que se usara para llamar a Vim

- *conocer el directorio de trabajo* es el equivalente al comando `pwd`

- *guardar como root* permite guardar un archivo que solo tiene permisos para
  `root` sin necesidad de ejecutar vim desde ese usuario o utilizando `$ sudo` y
  perder de ese modo las ventajas de nuestra configuración.

- *guardado rápido* guarda rápidamente un archivo sin tener que ejecutar el
  comando `:w`

- *abrir ranger* llama al programa externo
  [Ranger](http://joedicastro.com/productividad-linux-ranger.html) para navegar
  por el sistema de archivos y elegir el archivo que queremos editar.

    ![ranger](http://joedicastro.com/static/pictures/ranger_vim.gif "ranger")

- *abrir vimfiler* abre el explorador de archivos vimfiler, muy completo y
  basado en Unite. Lo uso principalmente en donde no tengo instalado ranger.

    ![vimfiler](http://joedicastro.com/static/pictures/vimfiler.png "vimfiler")

  TODO: completar vimfiler

### Otras herramientas

- __utl__ es un plugin que nos permite abrir URLs y enlaces a otro tipo de
  archivos desde vim.

    ![utl](http://joedicastro.com/static/pictures/utl.gif "utl")

    > __Atajo__

    > `<Leader>j` si usamos el atajo sobre un enlace se abrirá el destino
    > correspondiente en la aplicación que tengamos configurada


## Edicion de codigo


### Menu

- *syntastic check* y *syntastic errors* son dos opciones de Syntastic, un
  plugin que comprueba la sintaxis de numerosos lenguajes (python, ruby, lua,
  haskell, css, html, js, json, ...) a través de herramientas externas. Muestra
  los errores de sintaxis en la columna de signos de Vim, a la izquierda de los
  números de línea. También muestra un resumen del numero de errores y la
  localización del primero de ellos en la barra de estado (en este caso la de
  Powerline)

    > *Estas herramientas necesitan estar instaladas para que el plugin funcione
    correctamente.

- *contar lineas de codigo* ejecuta el programa externo `$ cloc` sobre el
  archivo y muestra el resultado en Unite.

- *conmutar lines de indentado* sirve para mostrar lineas verticales en el
  código indentado (sangrado) con espacios para marcar los niveles de indentado.
  Lo tengo desactivado por defecto.

    ![indentLine](http://joedicastro.com/static/pictures/indentline.gif "indentLine")


TODO: Añadir entradas de python-mode
TODO: Añadir entradas de Virtualenv
TODO: Añadir entradas de coveragepy

### vimux

![vimux](http://joedicastro.com/static/pictures/vimux.gif "vimux")

Sirve para interactuar entre vim y tmux. Básicamente permite enviar comandos a
un panel de tmux e interactuar con el sin perder el foco en Vim. Tal y como lo
tengo configurado, si no hay ningún otro panel abierto aparte del de Vim, se
abrirá uno debajo de este ocupando el 20% del espacio, en otro caso se
ejecutara en el panel abierto.

__Atajos__

- `<Leader>xr` guarda el buffer actual, limpia el panel y ejecuta el contenido
  del buffer con `python2`
- `<Leader>xt` igual que el atajo anterior pero ejecuta el contenido precedido
  por el programa unix `time` para conocer el tiempo total empleado en su
  ejecucion.
- `<Leader>xp` igual que al atajo anterior pero empleando `pypy` en lugar de
  `python2`
- `<Leader>xc` llama a un prompt en la linea de comandos en el que podemos
  introducir el comando que queremos que se ejecute en el panel de tmux
- `<Leader>xl` repite el ultimo comando que se he ejecutado con vimux
- `<Leader>xs` interrumpe la ejecución del comando que hayamos lanzado con vimux
- `<Leader>xi` salta al panel donde se ha ejecutado el comando de vimux y entra
  en *copy mode*
- `<Leader>xz` cierra el panel donde se ha ejecutado el comando de vimux


### UltiSnips

![ulti](http://joedicastro.com/static/pictures/ulti.gif "ulti")

Ultisnips es un plugin para gestionar Snippets, el mas avanzado y potente que
conozco para Vim.  Los snippets son porciones de código o texto en las que
cierta parte es declarada como variable y el resto como fija y nos ayudan a no
tener que teclear una y otra vez las mismas porciones de texto/código.
Simplemente invocamos el snippet con el identificador y el texto fijo es
insertado automáticamente, dejando aquellas partes declaradas como variables
para ser rellenadas de forma interactiva. Se puede apreciar mejor en la imagen
el funcionamiento de los mismos.

Ultisnips trae por defecto algunos snippets predefinidos para varios lenguajes y
algunos globales. La mejor característica de Ultisnips es que nos permite
definir los nuestros propios con un nivel de control y automatismo que ningún
otro plugin nos ofrece. Es lo suficiente complejo para no entrar aquí en
detalles, es necesario leerse detenidamente la ayuda para comprenderlo.
Destacaría de todos modos que nos permite emplear comandos externos (shell,
vimscript y Python) dentro de los mismos o que podemos usarlos con selecciones
visuales, así como anidar snippets o usar transformaciones de texto.

__Atajos__

- `<Tab>` precedido por el identificador nos lanza el snippet
- `<C-J>` nos desplaza al siguiente campo a rellenar
- `<C-K>` nos desplaza al anterior campo a rellenar

En el directorio `./UltiSnips` guardo mis snippets personalizados.



## DVCS: Git

![unite git](http://joedicastro.com/static/pictures/unite_menu_git.png "unite git")

__Unite__

- `<localleader>g` o `:Unite menu:git` abre el menú de Git

### Menu

- *tig* abrimos la aplicación externa [tig][tig] que es un interfaz ncurses para
  git. Evidentemente esto solo funciona cuando te encuentras dentro de un
  repositorio git.

    ![tig](http://joedicastro.com/static/pictures/tig.gif "tig")

  [tig]: https://github.com/jonas/tig

- El resto de entradas son comandos típicos de Git que se ejecutan a traves de
  la herramienta Fugitive

    TODO: Completar Fugitive

### Otras herramientas

- *vim-gitgutter* muestra los cambios que se producen en el buffer con respecto
  al repositorio git en el que se encuentra. Hace un git diff y muestra el
  estado de cada linea que se ha cambiado/eliminado/añadido en la columna de
  signos de Vim a la izquierda de los números de línea.


## Desarrollo Web

### HTML5

Proporciona funciones de autocompletado, sintaxis e indentación para HTML5. Para
ello tiene soporte de SVG, RDFa, microdata y WAI-AIRA.

### Sparkup

![sparkup](http://joedicastro.com/static/pictures/sparkup.gif "sparkup")

Sparkup nos permite escribir archivos HTML más rápido, de manera más concisa y
de forma menos tediosa. Se basa en Zen Coding, por lo que toda la nomenclatura
que funciona con Zen Coding es valida para Sparkup.

__Atajos__

- `<C-E>` ejecutar sparkup sobre la expresión bajo el cursor
- `<C-N>` saltar a la siguiente etiqueta/atributo vacío

La mejor forma de comprender como funciona es acceder a los ejemplos en la ayuda
de Vim, `:h sparkup-examples` <vimhelp:sparkup-examples> y si tienes
conocimientos de Python consultar el código en
`~/.vim/bundle/vim-sparkup/ftplugin/html/sparkup.py`



## Gestion de color

![unite colorv](http://joedicastro.com/static/pictures/unite_menu_colorv.png "unite colorv")

ColorV es el complemento perfecto para editar archivos CSS a la hora de lidiar
con colores. No solo nos permite previsualizarlos en el archivo para saber que
color se corresponde con cada definición, si no que ademas nos provee de
herramientas para escoger colores (tanto en la consola como en modo gráfico),
esquemas de color, trabaja con varios espacios de color, etc. Tiene
prácticamente todo lo que se puede necesitar para la gestión del color, sin
envidiar a muchas herramientas profesionales.


__Unite__

`<LocalLeader>c` o `:Unite menu:colorv` nos abre el menu de *colorv*
donde se encuentran todas estas opciones

![colorv](http://joedicastro.com/static/pictures/colorv.gif "ColorV")

### Menu

- `<Leader>cv` muestra la ventana de ColorV
- `<Leader>cw` muestra la ventana de ColorV con el color debajo del cursor
- `<Leader>cpp` previsualiza los colores en el buffer actual
- `<Leader>ce` edita el color situado bajo de el cursor
- `<Leader>cE` edita el color situado bajo de el cursor y cambia todas los
 colores similares en el mismo buffer (con confirmación previa)
- `<Leader>cii` inserta un color empleando la ventana de ColorV. La segunda i
 puede ser sustituida por una `r` para insertar un color con nomenclatura
 RGB, una `m` para CMYK, etc... consultar la ayuda para más información
- `<Leader>cn` muestra una ventana lateral con una lista de colores por
  nombre (colores Web del W3C)
- `<Leader>cgh` muestra una ventana lateral con una lista de colores
  con el mismo tono que el situado bajo el cursor. La `h` puede ser cambiada
  para mostrar una lista de colores por saturación `s`, análogos `a`, ...
  consultar la ayuda para una lista completa
- `<Leader>cd` muestra un selector de color gráfico (GUI)
- `<Leader>css` elegir un esquema de color desde
 [Kuler](https://kuler.adobe.com) o [ColourLovers](http://www.colourlovers.com/)
- `<Leader>csf` muestra los esquemas marcados como favoritos (`f` para marcar
 como favorito, `F` para desmarcarlo)
- `<Leader>csn` crea un nuevo esquema


    > __Atajos en la ventana de ColorV__

    > - `z/Z` cambia el tamaño de la ventana
    > - `?` muestra los atajos disponibles cíclicamente
    > - `q` cierra la ventana

TODO: terminar el menu

## Markdown

![unite markdown](http://joedicastro.com/static/pictures/unite_menu_markdown.png "unite markdown")

Nos permite previsualizar el renderizado de un archivo Markdown en el navegador,
soporta además la extensión `extra` de Markdown.  El archivo es renderizado con
Python-Markdown, crea un archivo temporal html y lo abre en una pestaña en el
navegador. Usado en conjunto con algún plugin que refresque la pestaña del
navegador al cambiar el archivo html, conseguimos previsualizar los cambios sin
abandonar vim.

__Unite__

- `<localleader>k` o `:Unite menu:markdown` nos abre el menú markdown

### Menu

- *previsualizar* renderiza el documento markdown en un archivo temporal y lo
  abre en una pestaña del navegador

- *refrescar* reescribe el fichero html con los cambios introducidos

    ![mep]( http://joedicastro.com/static/pictures/mep.gif "mep")

## Utilidades de Linux/Unix

### DirDiff

![DirDiff](http://joedicastro.com/static/pictures/dirdiff.gif "DirDiff")

Funciona de modo similar a vimdiff pero entre directorios en lugar de archivos.

__Comandos__

- `:DirDiff {A:directorio 1} {B: directorio 2}` muestra las diferencias entre
  los dos directorios
- `:DirDiffQuit` sale del modo DirDiff


### Editor hexadecimal

![hex](http://joedicastro.com/static/pictures/hexman.gif "hex")

Este plugin en realidad utiliza la herramienta `xxd` para visualizar un archivo
de forma hexadecimal.

Este es un plugin a manejar con cuidado y sabiendo lo que se está haciendo.
Conviene ademas abrir el archivo en modo binario (`$ vim -b archivo`) y volver
siempre al modo ASCII (abandonar el modo binario) antes de guardar el archivo.

__Atajos__

- `<F6>` entrar/salir del modo Hexadecimal
- `<leader>hd` elimina el carácter Hexadecimal bajo el cursor
- `<leader>hi` inserta un carácter ASCII antes del cursor
- `<leader>hg` ir al byte que le indiquemos (en hexadecimal)
- `<leader>hn` o `<Tab>` ir al siguiente byte
- `<leader>hp` o `<Shift><Tab>` ir al byte anterior
- `<leader>ht` mueve el cursor del área Hexadecimal al área ASCII y viceversa
- `?`          muestra la ayuda



## Internalizacion

### Traduccion de archivos .po

![po](http://joedicastro.com/static/pictures/po.gif "po")

Es una utilidad para añadir sintaxis y algunos atajos para los archivos `.po` de
traducción de cadenas (GNU gettext)

__Atajos__

- `/u` se desplaza a la siguiente cadena sin traducir
- `/U` se desplaza a la anterior cadena sin traducir
- `/c` copia la cadena `msgid` a `msgstr`
- `/C` crea un comentario para esa entrada
- `/d` elimina la cadena `msgstr` (solo en Insert mode)
- `/f` se desplaza a la siguiente cadena "fuzzy"
- `/F` se desplaza a la anterior cadena "fuzzy"
- `/z` etiqueta la entrada "fuzzy"
- `/Z` elimina la etiqueta de la entrada "fuzzy"
- `/s` muestra estadísticas `msgfmt` del archivo
- `/e` navega a través de los errores `msgfmt` del archivo
- `/t` introduce la información del traductor en la cabecera
- `/T` introduce la información del equipo de traducción en la cabecera
- `/W` formatea todo el archivo
- `gf` abre en otra ventana el archivo que está debajo del cursor


## vim-transpose

![transpose](http://joedicastro.com/static/pictures/transpose.gif "transpose")

Sirve para transponer filas y columnas, que puede ser muy útil para editar
cierto tipo de archivos (e.g. *csv*). Funciona con selecciones visuales.

__Comandos__

- `:Transpose` hace la transposición por defecto
- `:TransposeCSV {separador} {delimitador}` hace la transposición teniendo en cuenta la separación por
  punto y coma o el separador que le especifiquemos y el delimitador
- `:TransposeTab` hace la transposición teniendo en cuenta los tabulados
- `:TransposeWords` hace la transposición por palabras e inserta una
  interrogación donde falte una
- `:TransposeInteractive` para transposiciones complejas


## Herramientas de Vim

![unite vim](http://joedicastro.com/static/pictures/unite_menu_vim.png "unite vim")

TODO: completar herramientas de Vim

## Prerequisitos

TODO: completar prerequisitos

Para que todos los plugins incluidos funcionen adecuadamente es necesario
disponer de una versión de Vim superior o igual a la __7.3__ y compilada para
dar soporte a Python, Lua y Ruby. Esto se puede saber empleando el comando
`:version` que ademas de darnos el numero de versión nos dirá que opciones
soporta precediéndolas de un símbolo más `+`

Ademas es necesario tener instalados una serie de programas para un
funcionamiento integral:

- __ctags__, para generar las "etiquetas" de los archivos de código fuente. Suele
  venir distribuido como `exuberant-ctags`
- __ag__, __ack__ o __grep__ para la búsqueda del contenido de archivos mediante expresiones
  regulares
- __git__ para las operaciones de control de versiones

__Fuente__

Es necesario ademas emplear la fuente `Dejavu Sans for Powerline` para el plugin
Powerline. Esta fuente está incluida en este mismo repositorio en la carpeta
`../fonts`

## Plugins & Esquemas de color

- __badwolf__  <https://github.com/sjl/badwolf>
- __colorv.vim__ <https://github.com/Rykka/colorv.vim>
- __coveragepy.vim__ <https://github.com/alfredodeza/coveragepy.vim>
- __crontab.vim__ <https://github.com/vim-scripts/crontab.vim>
- __csapprox__ <https://github.com/godlygeek/csapprox>
- __DirDiff.vim__ <http://github.com/joedicastro/DirDiff.vim>
- __easydigraph.vim__ <https://github.com/Rykka/easydigraph.vim>
- __gundo.vim__ <https://github.com/sjl/gundo.vim>
- __harlequin__ <https://github.com/nielsmadan/harlequin>
- __hexman.vim__ <https://github.com/vim-scripts/hexman.vim>
- __html5.vim__ <https://github.com/othree/html5.vim>
- __indentLine__ <https://github.com/Yggdroot/indentLine>
- __JSON.vim__ <https://github.com/vim-scripts/JSON.vim>
- __loremipsum__ <https://github.com/vim-scripts/loremipsum>
- __molokai__ <https://github.com/tomasr/molokai>
- __neobundle.vim__ <https://github.com/Shougo/neobundle.vim>
- __neocomplete.vim__ <https://github.com/Shougo/neocomplete.vim>
- __po.vim--gray__ <https://github.com/vim-scripts/po.vim--gray>
- __python-mode__ <https://github.com/klen/python-mode>
- __scratch-utility__ <https://github.com/vim-scripts/scratch-utility>
- __summerfruit256.vim__ <https://github.com/vim-scripts/summerfruit256.vim>
- __syntastic__ <https://github.com/scrooloose/syntastic>
- __ultisnips__ <https://github.com/SirVer/ultisnips>
- __unite-colorscheme__ <https://github.com/ujihisa/unite-colorscheme>
- __unite-filetype__ <https://github.com/osyo-manga/unite-filetype>
- __unite-fold__ <https://github.com/osyo-manga/unite-fold>
- __unite-help__ <https://github.com/tsukkee/unite-help?>
- __unite-locate__ <https://github.com/ujihisa/unite-locate>
- __unite-mark__ <https://github.com/tacroe/unite-mark>
- __unite-outline__ <https://github.com/Shougo/unite-outline>
- __unite-quickfix__ <https://github.com/osyo-manga/unite-quickfix>
- __unite-session__ <https://github.com/Shougo/unite-session>
- __unite.vim__ <https://github.com/Shougo/unite.vim>
- __utl.vim__ <https://github.com/vim-scripts/utl.vim>
- __vim-characterize__ <https://github.com/tpope/vim-characterize>
- __vim-commentary__ <https://github.com/tpope/vim-commentary>
- __vim-fugitive__ <https://github.com/tpope/vim-fugitive>
- __vim-gitgutter__ <https://github.com/airblade/vim-gitgutter>
- __vim-github256__ <https://github.com/joedicastro/vim-github256>
- __vim-markdown__ <https://github.com/joedicastro/vim-markdown>
- __vim-markdown-extra-preview__ <https://github.com/joedicastro/vim-markdown-extra-preview>
- __vim-molokai256__  <https://github.com/joedicastro/vim-molokai256>
- __vim-pentadactyl__ <https://github.com/joedicastro/vim-pentadactyl>
- __vim-powerline__ <https://github.com/joedicastro/vim-powerline>
- __vim-repeat__ <https://github.com/tpope/vim-repeat>
- __vim-signature__ <https://github.com/kshenoy/vim-signature>
- __vim-smartinput__ <https://github.com/kana/vim-smartinput>
- __vim-sparkup__ <https://github.com/joedicastro/vim-sparkup>
- __vim-speeddating__ <https://github.com/tpope/vim-speeddating>
- __vim-surround__ <https://github.com/tpope/vim-surround>
- __vim-textobj-entire__ <https://github.com/kana/vim-textobj-entire>
- __vim-textobj-indent__ <https://github.com/kana/vim-textobj-indent>
- __vim-textobj-lastpat__ <https://github.com/kana/vim-textobj-lastpat>
- __vim-textobj-line__ <https://github.com/kana/vim-textobj-line>
- __vim-textobj-underscore__ <https://github.com/kana/vim-textobj-underscore>
- __vim-textobj-user__ <https://github.com/kana/vim-textobj-user>
- __vim-tmux__ <https://github.com/vimez/vim-tmux>
- __vim-transpose__ <https://github.com/salsifis/vim-transpose>
- __vim-unite-history__ <https://github.com/thinca/vim-unite-history>
- __vim-virtualenv__ <https://github.com/jmcantrell/vim-virtualenv>
- __vimfiler__ <https://github.com/Shougo/vimfiler.vim>
- __vimproc__ <https://github.com/Shougo/vimproc.vim>
- __vimux__ <https://github.com/benmills/vimux>
- __webapi-vim__ <https://github.com/mattn/webapi-vim>
- __winresizer__ <https://github.com/jimsei/winresizer>
- __zoomwintab.vim__ <https://github.com/vim-scripts/zoomwintab.vim>

# ...Work in progress!

FIXME: Realizar una revisión de calidad

