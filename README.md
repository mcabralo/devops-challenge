# DevOps challenge

Imagine um cenário onde você precisa armazenar um determinado dado gerado dentro de um container orquestrado por Docker de forma persistente, ou seja, de forma que em uma eventual queda do container o dado não seja perdido. Levando em conta essa premissa, responda as questões a seguir:

1- Quais técnicas você conhece e qual delas você usaria para implementar uma rotina que atenda essa premissa, escrevendo dados em um arquivo? Justifique sua resposta.

    Existem 3 táticas principais para fazer isso no docker: "Volumes, Bind mounts, tmpfs mounts e named pipes". Dentre estes os 2 últimos não salvam diretamente os na máquina do HOST, mas os colocam na memória. São muito úteis para comunicação. 

    Dentre os que sobraram o Bind é mais antigo e tem menos funcionalidades, logo o Volume seria minha escolha. Considerando uma rotina de programação é melhor termos todas as estruturas de controle à mão do controlador. Como temos a possibilidade de controlar os volumes pelo Docker, temos acesso a uma variedade de estruturas que podem aplicar soluções aos casos mais diferentes, como pode exemplo o uso de drivers para fazer a persistência de dados em outros locais de forma remota, fazendo toda esta persistência cada vez mais segura e ágil.

2- Faça um fork deste repositório e implemente esta rotina usando Docker. 

    Considerando que a QR usa MySql e PostGres como repositório de dados, criei um docker-compose que irá rodar e salvar ambos repositório baseados em imagens padrões criadas pelo Docker. Além disso coloquei o Adminer (serviço Php para visualizar a estrutura e os bancos de dados) para facilitar a vizualização. Caso esteja sendo utilizado o Driver Toolbox, é necessário saber qual o IP gerado pela máquina. 
    Ao rodar `docker-compose up` os 3 serviços serão levantados e irá criar 2 pastas (caso não existam ainda) para persistir os dados do Container.

Realize um pull request com a resposta da primeira pergunta na descrição juntamente com a implementação da solução.
