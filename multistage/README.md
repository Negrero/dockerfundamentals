# Multistage
Para la compilacion multistage ejecutaremos:

```$ docker build -t multi . -f Dockerfile.multi```

Y ahora ejecutamos nuestra imagen:

```docker run -e url=https://www.docker.com multi```

nota: app es una aplicación de Golang que se utiliza para contar las etiquetas de enlaces internos/externos en una página web

referencia:[autor: https://github.com/alexellis/href-counter]