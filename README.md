Semana-18---Docker-Swarm

  Nesta aula aprendi a realizar o deploy de uma aplicação utilizando o Swarm. 
        
  Foi utilizado um arquivo docker-compose.yml de exemplo onde foram criados diversos serviços, como por exemplo: foram definicas imagens, um volume para cada volume, foi definido uma rede de portas, tudo fazendo um binding, foram informadas as dependências entre outras coisas.

  Essa ideia segue o conceito de microsserviços e entrega diversos serviços espalhados pelo cluster entre os seus nós. Além disso, esses serviços vão se comunicar a fim de construir uma aplicação. O mais interessante dessa ferramenta é que cada serviço funcionará de forma isolada em seus próprio containers. Isso é muito legal!
        
  O objetivo da aplicação ensinada pelo professor é subir um serviço responsável por ser o visualizador de como está rodando cada container, cada serviço, cada tarefa dentro do Swarm e o core é uma aplicação de votação, quando se escolhe entre uma ou outra opção, outra tela mostra a porcentagem de quem está ganhando ou perdendo. 

  São múltiplos serviços interconectados que funcionam juntos, mas um não interfere no funcionamento do outro, no máximo há as dependências. 

  Esse exemplo do professor é uma aplicação com código aberto para acesso de qualquer um (não tenho o endereço aqui). Para explicar os serviços utilizados, basicamente é uma aplicação feita em Python que se comunica com o Redis  (que conta os votos e envia para um worker (um dos nós no Swarm) que está rodando o ambiente .NET, ele então, faz o envio do voto para um banco de dados, o banco de dados exibe o resultado em uma aplicação node. Esse é o resultado do Docker, do Swarm e do compose juntos.

   Subindo a Stack:
          
- Depois de ter criado o Swarm, entrar na máquina Leader;
- Lá copiar o conteúdo do docker-compose.yml e salvar com o mesmo nome da seguinte forma: cat > docker-compose.yml - salvar dando o CTRL+D;
- É possível confirmar se deu certo dando um cat docker-compose.yml (ele vai listar o conteúdo do documento) ou apenas um ls (vai mostrar o arquivo dentro da máquina);
- Para dar o deploy e gerar os serviços: docker stack deploy --compose-file docker- compose.yml;
- O comando docker stack ls vai listar a stack criada: 

![lista stack](https://user-images.githubusercontent.com/88297299/169656199-a9ce7487-6409-4bdf-932c-6a27eb776149.jpg)

- Para ver a aplicação funcionando é só colocar o IP de uma das máquinas e a porta de cada serviço no navegador.  (Por exemplo: 192.168.99.100:5000);

- Para finalizar a aplicação é só dar o comando: docker stack rm vote.

Imagens da aplicação em execução:

![votação](https://user-images.githubusercontent.com/88297299/169656162-0779b450-d582-40ea-b888-9929497d99f4.jpg)

![Porcentagem](https://user-images.githubusercontent.com/88297299/169656153-b4a741d2-a443-4862-92ba-305e2676cff4.jpg)

![visualizer](https://user-images.githubusercontent.com/88297299/169656170-c0eb7611-55fc-49a0-b74c-b2ffc474bb53.jpg)


Fim do Curso 

Oferecido pela Alura 
Professor Daniel Artine
