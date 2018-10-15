# Ejemplo de onbuild

En este ejemplo podemos ver como a partir de comandos de una imagen con comandos onbuild podemos ejecutar nuestra imagen simplificando tan solo a usar FROM a partir de dicha image que tiene un formato como: 

```
FROM node:0.0.0-jessie

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

ONBUILD ARG NODE_ENV
ONBUILD ENV NODE_ENV $NODE_ENV
ONBUILD COPY package.json /usr/src/app/
ONBUILD RUN npm install && npm cache clean --force
ONBUILD COPY . /usr/src/app

CMD [ "npm", "start" ]
```

de forma que cuando compilemos nuestra imagen: 

```$ docker build -t onbuild .```

a partir de nuestro Dockerfile:

```FROM node:onbuild```

podremos ejecutar nuestra aplicación desde dicha imagen ya que las instrucciones onbuild de la imagen padre de nuestro Dockerfile se lanzaran en nuestro Dockerfile.