- Iniciar container

```bash
sudo docker start <nome do container>
```

- Parar container

```bash
sudo docker stop <nome do container>
```

- Reiniciar container

```bash
sudo docker restart <nome do container>
```

- Listar containers

```bash
sudo docker container ls
```

- Listar imagens

```bash
 sudo docker container ls
```

- Remover container

```bash
sudo docker rm <id do container>
```

- Remover imagem

```bash
sudo docker rmi <id da imagem>
```

- Criar container docker do mysql com a porta 3306

```bash
sudo docker run --name nome-do-container -e MYSQL_ROOT_PASSWORD=sua-senha -p 3306:3306 -d mysql
```

- Mostrar os container que estão em execução

```shell
sudo docker ps
```

- Acessar shell do container mysql e executar sql

```bash
sudo docker exec -it nome-do-container bash
mysql -uroot -p
```
