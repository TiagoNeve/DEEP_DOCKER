# DOCKER 

## DOCKER commands

docker run [Nome da imagem] -> Cria um contatiner a partir de uma imagem

docker build -t [Nome da imagem] . -> Cria uma imagem a partir de um Dockerfile

docker ps  -> Lista os containters que estão executando no momento

docker stop [Id do container] -> Para o serviço do container.

docker rm -f [Id do container] -> Para e apaga o serviço do container, junto com o container

docker images -> Lista todas as imagens que estão na sua máquina.

docker login -u [Seu nome de usuário no Docker HUB] -> Inicia um login para poder dar push das imagens que forem buildadas.

