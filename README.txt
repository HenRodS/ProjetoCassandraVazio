Passo a passo para criar e utilizar esse projeto com SGDB NoSQL Cassandra

Passo 1: Baixe o Docker Desktop
  1.1: Baixe do site e siga o assistente "https://www.docker.com/"
  
Passo 2: Preparar a pasta do projeto
  2.1: Crie uma pasta no seu computador para o projeto, e dentro dele crie duas pastas:
    readme.txt
    data.cql
  2.2: Dentro de data.cql, coloque o seguinte comando para criar um DB vazio:
    CREATE KEYSPACE IF NOT EXISTS meu_projeto
    WITH replication = {'class':'SimpleStrategy', 'replication_factor':1};

Passo 3: Criar o container Cassandra com volume
  3.1: abra o PowerShell (se usar o windows) na pasta do projeto
  3.2: Coloque esse comando:
    docker run -d --name cassandra --hostname cassandra -p 9042:9042 -v F:\local\do\projeto:/data cassandra
    
Passo 4: Executar o script data.cql
  4.1: coloque esse comando:
    docker exec -it cassandra cqlsh -f /data/data.cql

Passo 5: Parar e remover o container (quando necessário)
  5.1: Coloque esses comandos:
    docker stop cassandra
    docker rm cassandra
