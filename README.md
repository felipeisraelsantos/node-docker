# Início de projeto node com docker

#### Iniciar projeto em node

Criando o arquivo package.json

```bash
$ npm init -y
```



#### Criando arquivos

```bash
$ touch inde.js Dockerfile
```



#### Instalação do express

```shell
$ npm install express
```



#### Criando .dockerignore

arquivos ao qual o docker deve ignorar  

```
$ touch .dockerignore
```



#### Alterando o arquivo package.json 

adicione a linha "start": "node index.js"

```json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index.js"
  }
```



### Criando uma imagem

```shell
$ docker build -t dockernode/docker-node . 
```



### Rodando o container

  docker run -p < portaacesso:portacontainer > -d < imagem a ser utilizada>

```shell
$ docker run -p 3000:3000 -d dockernode/docker-node
```



![](/home/felipe/Imagens/retornodocker.png)



### Ver imagens que estão rodando

```
$ docker ps
```



![](/home/felipe/Imagens/dockerruning.png)



### Usando docker compose



#### criando arquivo docker-compose.yml

```
$ touch docker-compose.yml
```



##### definindo versão do composer e servicos

```
version: "3"

services:
    app:
        build: .                    ( indicação de onde está o arquivo Dockerfile)
        command: npm start          ( comando a ser executado quando a aplicação subir )
        ports:
            - "3000:3000"           ( redirecionamento de portas )
        volumes: 
            - .:/usr/app            ( pasta aonde serão refletidas as alterações )
```



### instalando nodemom

```
$ npm install nodemon
```



### altere novamente o package.json 

```json
adicione a linha "start": "node index.js" para "start": "nodemon index.js"

"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "nodemon index.js"

  }
```



### Parando o container para modificações

docker ps  ( para listar as imagens )

docker stop < CONTAINER ID NAMES >

```shell
$ docker stop a49c1ab8242c (no meu caso)
```



### subindo as alterações

```shell
$ docker-compose up
```





![](/home/felipe/Imagens/dockercompose.png)

