# Create-Img-Docker
-------------------

**FROM:** Este é o comando mais importante, pois ele especifica a imagem base para a construção de uma nova. Na maioria das vezes a imagem especificada vai ser uma distribuição linux, se essa imagem não for encontrada na máquina local, o docker tentará buscar em algum repository. Caso queira, por exemplo, fazer a build do seu app em GO dentro do container, você vai precisar de uma imagem que tenha o GO instalado e configurado. Outra forma também seria criar diversas instruções com o comando RUN para fazer essa instalação.

**RUN:** Esse comando serve para executar outros comandos que a versão do sistema operacional permite. Por exemplo, se for debian vc pode instalar pacotes com apt-get, se for CentOS você pode utilizar o yum para pegar as dependências que seu serviço precisa para rodar. Com o RUN você também pode criar arquivos, pastas, enfim acho que deu pra entender que ele executa os mesmo comando do que você executaria na sua máquina, logo você consegue fazer praticamente tudo, e deixar a sequência de comandos versionada aqui dentro.

**ENV:** Serve para você setar variáveis de ambiente, você pode tanto deixar essas variáveis setadas de forma fixa dentro do Dockerfile quanto passá-las dinamicamente na hora que você instanciar o container. Para passar essas variáveis de ambiente na instanciação do container basta usar o parâmetro -e.

> **Exemplo:** _docker run -e ACCESSTOKEN=abcd [nome da imagem].

**COPY:** O COPY serve para você poder copiar arquivos e pastas para dentro da imagem do Docker, nesse exemplo eu copiei o arquivo elasticpush que estava dentro da pasta bin na minha máquina local para dentro da pasta /app na imagem do docker.

**ENTRYPOINT:** Com esse parâmetro você pode setar se quer que algo seja executado na hora da instanciação do container. Então, quando você der um docker run nessa imagem, ela já vai instanciar e executar o programa que está no caminho que você colocar entre colchetes. No nosso caso queremos que essa imagem execute nossa aplicação do Elasticpush, o mesmo vale para quaisquer outros serviços como Redis, Elasticsearch, Nodejs, etc…

