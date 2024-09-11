
# Dify VPS Ubuntu 20.04

1 - Clonar repositório

```
  git clone https://github.com/langgenius/dify.git
```


2 - Acessar pasta

```
  cd dify/docker
```


3 - Copiar variáveis de ambiente

```
  cp .env.example .env
```


4 - Atualizar pacotes do ubuntu

```
  sudo apt update
```

6 - Criar pasta para colocar os arquivos do docker 

```
  mkdir -p ~/.docker/cli-plugins/
```

7 - Fazer download dos arquivos do docker

```
  curl -SL https://github.com/docker/compose/releases/download/v2.3.3/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
```
8 - Adicionar permissões na pasta do docker

```
  chmod +x ~/.docker/cli-plugins/docker-compose
```

9 - Instalar docker

```
  sudo apt install docker-compose
```

10 - Adicionar permissões para manipulação do arquivo docker.sock

```
  sudo chmod 666 /var/run/docker.sock
```

11 - Inicializar o docker

```
  docker compose up -d
```

12 - Visualizar IPs dos projetos que estão rodando no docker

```
  docker ps -q | xargs -n 1 docker inspect --format '{{ .Name }}: {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}'
```

13 - Anotar IPs dos projetos docker-web e docker-api 

14 - Acessar arquivo de configuração do NGINX

```
  sudo nano ~/dify/docker/nginx/conf.d/default.conf
```

15 - Substituir valores do api e web com os IPs anotados anteriormente

16 - Reiniciar o NGINX

```
  docker compose restart nginx
```

17 - Acessar Dify via IP do servidor
