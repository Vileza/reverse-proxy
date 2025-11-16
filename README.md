# Reverse proxy

# Esse respositória irá concentrar a criação básica do apache utilizando porxy reverso junto com containerização.

A pasta `docker` é responssável por toda configuração das imagens dos containers incluindo o proxy reverso do apache.

As configurações atuais permitem acesso as urls com os respectivos subdomínios, sendo eles:
```
| Serviço    | Url                 |
|------------|---------------------|
| Blog       | blog.localhost      |
| Dashboard  | dashboard.localhost |
```

Caso queira alterar a url, basta apenas editar o arquivo de configuração do apache 
Local: `/docker/containers/apache/conf/000-default.conf`

Para que os subdomínios sejam direcionados para os serviços corretos, é preciso também configurar o arquivo de `hosts` que fica no seu sistema.
Local - Linux: `/etc`

Para isso basta seguir os seguintes comandos

`cd /etc`
`sudo nano hosts`

Ao abrir o arquivo de hosts, você precisarar mapear o seu local para as respectivas urls.
Exemplo:
`127.0.0.1       blog.localhost`
`127.0.0.1       dashboard.localhost`

Por fim será preciso iniciar os containers, para isso basta executar os seguintes comandos docker:
`docker compose build`
`docker compose up -d`


# Estrutura de pastas

A pasta `docker` é responsável por armazenar toda as configurações dockers e nela, cada container terá seu respectivo arquivo de configuração. Já a pasta `htdocs`, será responsável por guardar todos os arquivos da aplicação em si.