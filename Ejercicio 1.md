## Instalación de Jekyll

1. Con este comando instalamos ruby.
```sudo apt-get install ruby-full build-essential zlib1g-dev```

2. Los  siguientes comandos añadirán un entorno de variables en el fichero ~/.bashrc para configurar el path  de gem.
````
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
````

3. Instalamos las gemas, que hay que hacerlo como usuario.
``gem install jekyll bundler``Verificamos que Jekill esta instalado con el comando ``jekyll -v``

## Creación de un sitio en Jekyll

1. Primero hay que crear un repositorio en GitHub y a partir de ahí hay dos opciones:

- Clonar el repositorio: ``git clone https://github.com/tu_cuenta_github/myblog.git``

- Crear un directorio y conectarlo al repositorio: 
````
mkdir repositorio
cd repositorio
git init
git remote add origin https://github.com/tu_cuenta_github/myblog.gi
````

2. Creamos una rama nueva donde se publicara el sitio ``git checkout -b gh-pages``

3. Ahora crearemos el proyecto jekyll de forma automático ``jekyll new nombre_del_sitio``

4. Probamos el sitio localmente ``jekyll serve``

5. Agregamos y confirmamos el trabajo 
````
git add .
git commit -m 'Initial GitHub pages site with Jekyll'
````

6. Subimos los cambios al repositorio de GitHub ``git push -u origin gh-pages`` 

7. Ahora publicamos la página de la siguiente manera:

- Ingresar a configuraciones (settings) del repositorio (rueda dentada) y elegir la opción páginas  (pages) de la barra lateral izquierda y automáticamente se genera un dominio. Para comprobar su  funcionamiento se puede hace click en Visitar sitio (visit site): https://tu_cuenta_github.github.io/myblog

## Configuración de un sitio en Jekyll

1. Configuramos el fichero Gemfile teniendo que quedar asi:
````
source "https://rubygems.org"
# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!
# gem "jekyll", "~> 4.3.4"
# This is the default theme for new Jekyll sites. You may change this to anything you like.
gem "minima", "~> 2.5"
# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
gem "github-pages", group: :jekyll_plugins
group :jekyll_plugins do
 gem “jekyll-feed”, “~> 0,12”
end
````

2. Para personalizar y configurar tu sitio abra que editar el fichero _config.yml que tiene este formato:
````
title: Blog personal de tu_nombre_y_apellidos
email: tu_usuario@educantabria.es
description: >- # this means to ignore newlines until "baseurl:"
 Bienvenidos a mi sitio web de tu_nombre_y_apellidos ! Mi primer sitio en el generador de 
páginas estáticas Jekyll 
baseurl: /myblog
url: https://tu_cuenta_github.github.io
twitter_username: usuario
github_username: usuario
# Build settings
theme: mínima
theme: jekyll-the-minimal” (otro tema)
plugins:
 - jekyll-feed
````

## Desplegamos el sitio en Jekyll

1. Instalamos plugins, “gemas” definidos en _config.yml y Gemfile
````
bundle install
bundle update
````

2. Desplegamos la página ``bundle exec jekyll serve --host IP_local``