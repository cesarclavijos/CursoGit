Github - es un controlador de versiones

Ventajas en GIT


Solo necesita tus archivos o recursos locales, por ende no requiere internet. Git no borra, generalmente solo añade información. No se puede perder información sin que git sea capas de detectarlo ya que coloca un ID.

GIT TIENE TRES ESTADOS 

- Areas : 

working directory : (modified) primer estado, Aqui es donde va a pasar la mayoría del tiempo es donde se trabaja con eso vas añadiendo todas las partes al staging, Git add para pasar a staged

Staging Area:(staged) segundo estado, una vez todos los cambios están listos se añade al repositorio, este es un archivo que indica que archivos irán para el comité es una lista que contiene la informaciones los cambios ,git commit para pasar al tercer estado

Local repository: (commited) tercer estado, donde se almacena los metadatos y los objetos del proyecto, si quieres pasarlo a otra persona deberas hace run push a otro repositorio remoto


Instalando Git
Antes de empezar a utilizar Git, tienes que instalarlo en tu computadora.
Ubuntu:
Correr esto en la terminal
apt-get install git
Para otras distribuciones de linux:
https://git-scm.com/download/linux
Mac:
Correr esto en la terminal
brew install git
Si no tienes instalado brew, corre esto en la terminal
	.	/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Windows:
https://git-scm.com/download/winfinalmentegit --version 
Para confirmar que has instalado bien git, confirma que este comando te arroje la version de git que tienes instalado
git --version 


Configurar GIT
git config --global user.name "cesar Clavijo" # configurar el nombre del usuario
git config --global user.email cesar_hcs@hotmail.com # se configura el email del usuario
git config --list # se confirman los cambios
git config user.name # confirmar nombre 


GIT INI - crear proyecto
git init # inicializa un repositorio vacío de git se puede ver con ls -a
git add README.md

GIT ADD - 
Git add archivo.txt # añadir el archivo

GIT STATUS

# con este podemos saber el estado del proyecto
Git status
# los archivos sin seguimiento son aquellos archivos que estan mi working directory, y no estan listo para pasar a stage.




Si modifico el archivo al dar git status me dice que ese archivo fue modificado.y los cambios no han sido guardados, haciendo git add al archivo se soluciona

Con el comando GIT add — all se agregan todos los archivos 


GIT COMMITED

Git commit -m “comentario” # en el cual se describe que se esta realizando, después de eso el archivo se envía.
# si no se usa el -m se abre el editor y se pueden añadir modificaciones y comentarios


GIT LOG 
 El cual sirve para ver el estado de los comits

Git log # esta compuesto por el hash de 40 caracteres único, usuario fecha y comentario

Git remote 
Este comando sirve para  manejar un conjunto de repositorios remotos, se puede ver, crear y borrar.
Git remote # vemos el nombre de repositorio
Git remote -v # nombre del repositorio, el link al repositorio y vemos que podemos hacer fetch and push
￼

git remote add upstraim https://github.com/cesarclavijos/pruebacursogit2.git # para añadir el repositorio con el nombre 
￼


De esta manera puedo hacer push a dos repositorios remotos

￼ACTUALIZAR PROYECTOS

GIT CLONE

Hay dos formas de initializer repositorios git init and git clone 
 Desde githube se puede usar la opción de clonar

￼git clone https://github.com/cesarclavijos/pruebacursogit2.git 3 con esto creo un clone del repositorio

Con SSH toca crea una llave para crear una comunicación remota y poder transferir los archivos.


 Esta para enlistas las llaves

ssh-keygen -t rsa -b 4096 -C "cesar_hcs@hotmail.com" # con este comando creo una llave


￼

Control click en la dirección que genera.

cd ~   # vamos al home 
code .ssh/id_rsa.pub # obtenemos la llave, la copio y la pego en GitHuB



Ya podemos clonar con la llave
git clone git@github.com:cesarclavijos/pruebacursogit2.git





GITHUB GIT REMOTE AND GIT PUSH

git remote add origin https://github.com/cesarclavijos/CursoGit.git # copias este comando de GitHub, origin es el nombre de la carpeta (upstream) también es otro nombre por defecto
Git remote -v # poder ver que el repositorio fue añadido correctamente
Git push origin master # push es para enviar archivos del repositorio local al remoto, la carpeta origin, sobre la rama master



GIT PULL
Sirve para traer los cambios que han subido año repositorio
Git pull origin master # Jala los cambios de git a la carpeta origin 



GIT HELP
Comando para mostrar ayuda de un comando de git
Git help # arroja documentación de comando de git de forma resumida
Git hel - -all # te dice para que sirve los comandos 
Git help (comandfo) # tra la documentazione de cada comando


REPARACION BASICA

GET CLEAN
Remueve los archivos no trakeados del working directory, 
Git clean -f # borra todos los archivos que no estén trakeados, es un comando bastante peligroso ya que borra todo
Git clean -n # confirma que quieres borrar 
Git checkout - - archivo3.txt # elimina archivos trakeados 


BRANCH

Etapas:


1, es el código base, por defecto en la rama master 
2, apartar de un comitte se crea una rama derivada, el cual es el clone de la ultima version y en ella se trabaja sin afectar la rama master.
3, agregar los comitt, que es agregar los cambios (add comity) lo cual esta en la rama del usuario
4, se hace un pull request para agregar código a la rama principal
5, se hace coed review para saber si se arrglean cosas o se aprueba para ir al siguiente paso
6, Aceptar el pull request para que con merge se mezcle con la rama master

GIT BRANCH
Gir branch # listamos todas las ramas que existen e identificamos en cual estamos ubicado


Git branch normbre_rama # así se crea una rama 
git branch -d rama_1# elimina una rama
git branch -m nombre_2 nombre_nuevo # cambia el nombre de las ramas



GIT CHECKOUT

El identificador de los log, lo que hace es identificar a un comité único, nunca se va a repetir, los log aveces si no se encuentran quiere decir que se esta haciendo en la rama equivocada.

Git checkout 12332111 # con eso podemos ver que contenía la version especifica que se realizo commit, nos muestra el head y el apuntador hacia el commit, nos dice que el head esta en la version del commit
Git checkout master # vamos al ultimo commit de la rama

Git checkout sirve para moverse entre ramas y commit







Git pull origin master # trae todos los cambios de la rama master

Git checkout -b rama_nueva2 # crea la rama y nos movemos a esa rama



GIT MERGE

(Fast forward)
Es la mezcla del código, a la rama master 






Git merge rama_nueva2 # se hace desde la master para traer los cambios a esta rama 







(Recursive)

Se hace un branch al master y otra persona despliega un nuevo cambio, este es el merge recursive









Nota mensajes útiles 
"error: There was a problem with the editor 'vi  se soluciona con lo siguiente  git config --global core.editor $(which vim)

You have not concluded your merge (MERGE_HEAD exists). Se soluciona con lo siguiente git merge --abort



MANEJO DE CONFLICTOS
Cuando dos desarrolladores trabajan sobre la misma linea de código. Existen dos tipos de conflictos

1, Cuando inicias proceso de merge, cuando quieres iniciar un merge pero el ambiente de trabajo esta sucio, en esos caso se puede eliminar los cambios que estan en master pero no fueron comiteados y después de eso subir los cambios con el merge
2, durante proceso de merge, creamos una rama con la mas reciente verso y realizamos los cambios. Al master le añadimos cambios y hacemos comité, lo cual genera un error al no tener en la rama la ultima version, el dev debe saber para que sirve el código y con eso resolver los problemas



GIT STASH
Quiere decir reserva o escondite en ingles, se puede ver como un bolsillo, sirve para guardar la porción de código en la cual estas trabajando pero no esta completo.

Got stash




Got stash pop # recuperas los cambios que tenia en el bolsillo




Segun la imagen. El ultimo cambio que entra es el primero que sale, lo cual indica que se tiene que usar varias veces pop por cambios mas viejos

Git stash clear # se borra la lista de stash


GIT TAG
 Sirve para crear, listar, verificar o eliminar el objeto tag. Un tag es un apuntador a un solo commit, no tiene una historia detrás.


git tag Mi_primer_tag # este es un tag ligero es el mas sencillo de crear
git tag -a v1.0 -m "version 1.0"  # un tag anotado
Git tag # enlistas los tags creados
git tag -a v0.0 -m "version inicial" f1c3dcb11f61e44fdcb7335a6c8b817354235ee9 # así asignamos un tag a una version en especifico
git checkout V0.0 # viajo a un cmmid especifico
Git show v1.0 #nos muesli la información del commit que esta asignado con el tag


Git tag -d v0.0 3 se elimina el tag



