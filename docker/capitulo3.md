# Instalando o Docker

Existem várias maneiras de instalar o Docker. Podemos instalar no windows, mac e linux, instalar na nuvem ou no notebook(ou desktop), podemos instalar também por scripts, ou instaladores do tipo "next, next, next", existem realmente muitas formas de instalar o Docker.

## Docker desktop

O Docker desktop é um produto da Docker,inc, ele roda na versão de 64-bit no windows e no mac, e pode ser instalado facilmente

## Instalando Docker no linux

Existem várias maneiras de instalar o Docker no Linux, para mim a maneira mais facíl é através do bom e velho terminal. No momento eu tenho instalado na minha máquina o Pop_Os 21.10, uma distribuição Linux baseada em Ubuntu.

1. Primeiro atualizamos o gerenciador de pacotes(no meu caso o apt);

```bash
sudo apt-get update
```

2. Instalando o Docker do repositório oficial

```bash
sudo apt-get install docker.io
```

Pronto, o Docker já está instalado! Mas para termos certeza vamos "rodar" alguns comando para testar;

1. Vamos saber a versão do Docker;

```bash
 sudo docker --version
```

A saída no terminal deve ser algo como:

```bash
Docker version 20.10.7, build 20.10.7-0ubuntu5.1
```

2. Alguns informações sobre números de containers etc...

```bash
sudo dock info
```

Novamente, a saída deve ser semelhante a está;

```bash
Client:
 Context:    default
 Debug Mode: false

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 20.10.7
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
```
