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



## Explicações

Container networking -> Containers que estiverem na mesma networking podem se comunicar, um container
pode ter vários networkings e esses podem se comunicar para troca de dados. Isso é bom pois cada serviço
fica separado e caso seja necessário dar manutenção em um, o outro serviço não ficará parado em conjunto,
bastando criar um novo serviço com um backup e subir no network e gerar a conexão modificando o host, essa
mudança é gerada em alguns minutos e pode não ser perceptível para o usuário final. 

--> Docker compose: 