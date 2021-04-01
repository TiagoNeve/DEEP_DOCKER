# DOCKER 

## DOCKER commands

docker run [Nome da imagem] -> Cria um contatiner a partir de uma imagem

docker build -t [Nome da imagem] . -> Cria uma imagem a partir de um Dockerfile

docker ps  -> Lista os containters que estão executando no momento

docker stop [Id do container] -> Para o serviço do container.

docker rm -f [Id do container] -> Para e apaga o serviço do container, junto com o container

docker images -> Lista todas as imagens que estão na sua máquina.

docker login -u [Seu nome de usuário no Docker HUB] -> Inicia um login para poder dar push das imagens que forem buildadas.

docker exec -it(Interativo) [id do container] -> Acessa o CLI do container.

docker volume create [Nome do volume] -> Cria um volume para a persistência de dados

docker run -dp [portHost:portDocker] -v(Volume) [volumeHost:PathDocker] [image]

docker run -it --network [nomeDoNetowrk] [nomeDaImagem]

docker-compose up -d -> Executa o docker-compose e sobe as configuração no arquivo docker-compose.yml

docker-compose down -> Tira os serviços que foram sobidos com o docker compose.


## COMPOSE

version:  --> Define a versão que deve-se utilizar o compose.

services: --> Lista os containers que serão utilizados.

[nameServiço]:
    image: [nomeDaImagem]  --> Isso cria um serviço com o nome que foi dado utilizando a imagem que foi 
    apresentada.

    command: [comandoNoTerminal]  --> Informa qual o comando que vai ser executado após a subida do container.

    ports:
        - [portHost:portContainer] --> Declara quais portas estarão utilizando

    working_dir: [nome Do diretório] -> Pasta onde vai ficar o seu trabalho

    volumes:
        - [pastaDasAlterações : pastaOndeVaiFicarOApp]
    
    environment:
        MYSQL_HOST: mysql
        MYSQL_USER_PASSWORD: root
        MYSQL_DB: [nome do bando de dados]
    
 

## Explicações

Container networking -> Containers que estiverem na mesma networking podem se comunicar, um container
pode ter vários networkings e esses podem se comunicar para troca de dados. Isso é bom pois cada serviço
fica separado e caso seja necessário dar manutenção em um, o outro serviço não ficará parado em conjunto,
bastando criar um novo serviço com um backup e subir no network e gerar a conexão modificando o host, essa
mudança é gerada em alguns minutos e pode não ser perceptível para o usuário final. 

--> Docker compose: Cria um arquivo com o nome docker-compose.yml , assim esse arquivo consegue fazer um
container automático, sem precisar digitar tanto código para subir um container.
Sempre tente definir a versão do compose mais atual logo no inicio do script
Depois é necessário definir os serviços (Containers) que serão utilzados no projeto.
Para a geração do serviço é necessário atribuir um name ao serviço e logo após os seus atributos
e valores.
Algumas imagens não vem com um terminal rodando para segurar o serviço, por isso é necessário utilizar o
atributo command: e informar um comando utilizado no terminal para que o mesmo fique ativo e o serviço
em pé.
Para gerar uma comunicação entre um container e o host que está rodando ele é necessário utilizar as portas
para declarar no compose basta utilizar o atributo -> ports: [- 3000:3000]
Para gerar a persistência de alterações, no compose fica bastante fácil de mapear essas variações,
basta definir o seu diretório de trabalho com o : working_dir: [Diretório de trablho] e depois atribuir
os volumes: - [./:/app]. 
Caso precise, você pode declarar as variáveis de ambientes no compose também, basta utilizar o atributo:
environment: [ValoresDasVariáveis]
No arquivo de compose você pode declarar todos os serviços necessários da aplicação e rodar todos com
um único comando.
No compose você pode declarar tanto os serviços que serão utilizados, como tambéms os volumes e networks,
sendo bastante completo para a geração de container com maior velocidade.

