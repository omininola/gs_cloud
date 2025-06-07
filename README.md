# GS - Protech The Future | Cloud

## Integrantes

| Nome                   |   RM   |
| :--------------------- | :----: |
| Otavio Miklos Nogueira | 554513 |
| Luciayla Yumi Kawakami | 557987 |

## Links

- Repositório .NET: https://github.com/omininola/gs_dotnet
- Repositório Cloud: https://github.com/omininola/gs_cloud
- Vídeo Youtube: https://youtu.be/iXF6RjugFLg

---

## Dockerfile

O Dockerfile se encontra dentro da pasta `./project`
[Dockerfile](./project/Dockerfile)

## Inicialização

1. Rode o container MySql
```bash
docker run \
    --detach \
    --publish 3306:3306 \
    --name gs_mysql \
    --network gs_network \
    --volume gs_volume:/var/lib/mysql \
    --env MYSQL_USER=user \
    --env MYSQL_PASSWORD=StrongPassword \
    --env MYSQL_DATABASE=GS_DOTNET \
    --env MYSQL_ROOT_PASSWORD=root123 \
    mysql:latest
```

2. Build do projeto .NET
   1. Entre na pasta do app: `cd projeto`
   2. Builde a imagem: `docker build . -t gs_dotnet`
3. Rode o container da imagem
```bash
docker run \
    --detach \
    --publish 8080:8080 \
    --name gs_api \
    --env DB_PASSWORD=StrongPassword \
    --network gs_network \
    gs_dotnet
```

A documentação da API estará disponivel em: **http://localhost:8080/swagger/index.html**

## JSON para testes no Postman

[endpoints.json](./docs/endpoints.json)

### Como importar no Postman

1. Copie o arquivo `endpoints.json`
2. Entre no Postman
3. Clique em importar
4. Cole o json
