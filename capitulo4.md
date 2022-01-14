# A perspectiva do desenvolvedor

Podemos rodar uma aplicação a partir de um container do Docker. Clonando o repositório localmente, usamos o host do Docker para fazer a "conteinerização".

1. Eu costumo criar uma pasta no diretório raiz e depois clonar o repositório em questão dentro desta nova pasta;

```bash
$ mkdir teste
$ cd teste
$ sudo git clone https://github.com/nigelpoulton/psweb.git
```

2. Agora entramos no diretório que acabamos de clonar

```bash
teste$ cd psweb
teste/psweb$ ls -l
# A saída no terminal teve ser algo como:
total 28
-rw-r--r--@ 1 ubuntu ubuntu 338 24 Apr 19:29 Dockerfile
-rw-r--r--@ 1 ubuntu ubuntu 396 24 Apr 19:32 README.md
-rw-r--r--@ 1 ubuntu ubuntu 341 24 Apr 19:29 app.js
-rw-r--r-- 1 ubuntu ubuntu 216 24 Apr 19:29 circle.yml
-rw-r--r--@ 1 ubuntu ubuntu 377 24 Apr 19:36 package.json
drwxr-xr-x 4 ubuntu ubuntu 128 24 Apr 19:29 test
drwxr-xr-x 3 ubuntu ubuntu 96 24 Apr 19:29 views
```

O exemplo é uma aplicação em nodejs, o repositório git contém um arquivo chamado `Dockfile`, esse arquivo mostra ao Docker como fazer o build do aplicativo incluindo as dependências.

3. Podemos listar o conteúdo do arquivo com o seguinte comando:

```bash
teste/psweb$ sudo cat Dockerfile
```

O conteúdo deve ser algo como:

```bash
FROM alpine
LABEL maintainer="nigelpoulton@hotmail.com"
RUN apk add --update nodejs nodejs-npm
COPY . /src
WORKDIR /src
RUN npm install
EXPOSE 8080
ENTRYPOINT ["node", "./app.js"]
```

4. Usamos o comando `docker image build` para criar uma nova imagem do Docker criando assim, uma nova imagem chamada test:latest. Para isso rodamos o comando dentro do diretório que contém o arquivo `Dockerfile` e o app em questão:

```bash
teste/psweb$ sudo docker image build -t test:latest .
```

No terminal a saída sera:

```bash
Sending build context to Docker daemon 74.75kB
Step 1/8 : FROM alpine
latest: Pulling from library/alpine
88286f41530e: Pull complete
Digest: sha256:f006ecbb824...0c103f4820a417d
Status: Downloaded newer image for alpine:latest
---> 76da55c8019d
<Snip>
Successfully built f154cb3ddbd4
Successfully tagged test:latest
```

5. Podemos usar um comando para listar as imagens e nos certificarmos se os passos anteriores estão ok:

```bash
teste/psweb$ sudo docker image ls
```

E se tudo der certo, no terminal a mensagem no terminal será:

```bash
REPO TAG IMAGE ID CREATED SIZE
test latest f154cb3ddbd4 1 minute ago 81.5MB
```

6. Agora podemos iniciar um container da imagem e testar o app executando o comando:

```bash
teste/psweb$ docker container run -d \
--name web1 \
--publish 8080:8080 \
test:latest
```
