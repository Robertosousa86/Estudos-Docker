# Docker - TLDR

Docker é um software que roda em linux e windows. Ele cria, gerencia e faz orquestração de containers, a companhia que criou e continua a desenvolver tecnologias e soluções que facilitam que o código criado no pc seja executado facilmente na nuvem.

# Docker, Inc

Foi criada pelo desenvolvedor Solomon Hykes.

# A arquitetura do docker

A tecnologia principal por traz do docker pode ser dividida em três partes:

- O runtime
- O Daemon(engine)
- O orquestrador

O runtime opera em baixo nível e é o responsável por iniciar e finalizar os containers(isso inclui construir todas as partes do sistema operacional, como os namespaces e os cgroups). Docker implementa uma arquitetura em camadas de baixo e alto nível de runtimes trabalhando juntos. Uma tipica instalação de docker contem um único processo de conteinerização(docker-containerd) controlando a instancia de runc(docker-runc) associada a cada container rodando. O **docker daemon(dockerd)** fica por cima da conteinerização e roda tarefas de alto-nível como por exemplo: Expondo a API remota do docker, gerenciando imagens, volumes, redes, etc...
O trabalho principal do docker daemon é providenciar uma interface padrão facíl de usar que abstrai os niveis baixos.
