# Instagram-Tutorial

# Paso 1:

Creamos el proyecto en rails con:
    rails new instagram

Añadimos la gem 'devise' para facilitar la creación de los logins de usuario, y la añadimos a las gemas existentes con:
    bundle install

Funcionamiento de la gema 'devise':

La activamos con el comando:
    rails generate devise:install

Y seguimos los pasos que nos indica el instalador de la gema.
Estos son:
    La configuración del host en config/environments/development.rb
    Añadir las rutas en config/routes.rb
    Incluimos los mensajes flash añadiendo código html en app/views/layouts/application.html.erb
    Generar las vistas de Devise para personalizar el login usando el comando rails generate devise:views

Una vez completados, podemos empezar a crear los modelos necesarios para hacer el login y manejar el sistema de usuarios:

Para ello creamos el modelo de Usuario:
    rails g devise User

Y migramos los cambios:
    rails db:migrate

Para probar el funcionamiento de la página tenemos que iniciar el servidor de Rails con el comando:
    rails server

Y podemos ver la web desde la dirección:
    http://localhost:3000/

Desde esta dirección podemos ver las páginas web de sign in y sign out:
    http://localhost:3000/users/sign_in
    http://localhost:3000/users/sign_out

Que se han creado automáticamente gracias a la gema devise.

NOTA IMPORTANTE:

En el archivo application.html.erb hay una línea que lanza un error extraño:

    <!-- Esta línea da error pero habrá que buscar alguna solución auténtica y no solo limitarse a comentarla -->
    <!--  <%= javascript_pack_tag 'application', 'data-turbolinks-track': 'reload' %> -->

Si elimino esa línea la aplicación se ejecuta correctamente pero después dara errores con las rutas de Rails así que hay que buscar una solución definitiva a este fallo.

Pasos para eliminar este error:

He tenido que instalar la última version estable de node:
    nvm install v16.13.1

Y después he vuelto a instalar el webpacker:
     bundle exec rails webpacker:install

Y todo ha funcionado correctamente.

CAMBIOS EN GIT:

Una vez solucionado este molesto error he subido los nuevos cambios a git, pero como Rails crea una carpeta .git dentro del proyecto de Instagram tutorial, la he eliminado antes con el comando: 
    rm -rf .git

Y luego ya he podido seguir el proceso de git.
Resulta que en github han cambiado el proceso de seguridad y ahora subir archivos con la contraseña y el correo ya no es posible, sino que hay que usar un personal token, el cual está ubicado en el archivo notas.txt.

Además para que el personal token funcione, tenía que añadirle los permisos necesarios en los ajustes del proyecto.

Una vez establecido ya puedo subir los archivos con los comandos:
    git add .
    git commit -m ""
    git push origin main


