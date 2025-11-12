# Configuração dos Nós com Nginx e Load Balancer

## Criar os containers dos nós

Crie os containers dos nós (Node 1, Node 2, Node 3, etc.) já com o volume vinculado ao diretório onde estão os arquivos do build do projeto (por exemplo, /var/www/atlas-vital/dist):

    sudo docker run -it --name node1 -v /var/www/nome o arquivo:/usr/share/nginx/html nginx:1.29.3-alpine


Obs.: As portas podem variar conforme sua configuração.

## Acessar a pasta de configuração do Nginx em cada nó

Entre no container ou acesse o diretório de configuração diretamente (caso tenha um volume para isso):

    cd /etc/nginx/conf.d

## Editar o arquivo default.conf

Em cada nó, edite o arquivo default.conf (ou crie um volume separado para esse arquivo, para facilitar a edição).

O conteúdo deve ser o seguinte:

    server {
        listen       80;
        listen  [::]:80;

        location / {
            root   /usr/share/nginx/html;
            try_files $uri $uri/ /index.html;
        }
    }


Esse arquivo define que o Nginx vai servir o conteúdo da aplicação (por exemplo, uma aplicação React) e redirecionar qualquer rota desconhecida para o index.html.

## Reiniciar todos os containers

Para aplicar as mudanças, pare e reinicie todos os containers:

    sudo docker stop $(sudo docker ps -aq)
    sudo docker start $(sudo docker ps -aq)

## Testar no navegador

Após reiniciar, abra o navegador e acesse:

http://localhost:<porta_do_loadbalance>


obs: obviamente vc vai substituir <porta_do_loadbalance> pela porta que você definiu no container do load balancer Nginx :)