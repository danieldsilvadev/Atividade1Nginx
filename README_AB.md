# Teste de Carga com Apache Benchmark (AB)

## Atualizar os pacotes do sistema

Antes de instalar qualquer ferramenta, é importante garantir que os pacotes do sistema estão atualizados.
Execute o comando abaixo para atualizar a lista de pacotes disponíveis:

    sudo apt-get update


Esse comando sincroniza as informações dos repositórios e garante que a instalação das ferramentas use as versões mais recentes.

## Instalar o Apache Benchmark

O Apache Benchmark (ab) é uma ferramenta utilizada para testar o desempenho e a capacidade de resposta de servidores web.
Para instalá-lo, use o seguinte comando:

    sudo apt-get install -y apache2-utils


O parâmetro -y confirma automaticamente a instalação, evitando a necessidade de confirmação manual.

## executar o teste de carga

Após a instalação, o comando ab estará disponível.
Para executar um teste de carga simples, utilize o seguinte comando:

    ab -n 1000 -c 100 http://localhost:81/

### Explicação dos parâmetros:

-n 1000 → Número total de requisições que serão enviadas ao servidor.

-c 100 → Número de requisições simultâneas (concorrência).

http://localhost:81/ → Endereço e porta do servidor que será testado.