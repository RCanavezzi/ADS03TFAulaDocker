Sistema de Pesquisa de Satisfação
Este projeto foi desenvolvido para criar uma aplicação web para coletar pesquisas de satisfação dos alunos do Curso de Análise e Desenvolvimento de Sistemas. A aplicação utiliza Docker para fornecer um ambiente de desenvolvimento consistente e portátil.

Estrutura do Projeto
O projeto consiste nos seguintes componentes principais:

Containers Docker:

PostgreSQL: Um banco de dados relacional para armazenar dados estruturados.
MongoDB: Um banco de dados NoSQL para armazenamento de dados mais flexíveis.
Node.js: O servidor da aplicação que executa a aplicação de pesquisa de satisfação.
Código Fonte:

O código da aplicação está localizado no diretório src, que inclui o arquivo principal da aplicação (app.js) e o package.json para gerenciar as dependências.
Começando
Para configurar o ambiente de desenvolvimento, siga estes passos:

Clone o Repositório:

git clone <repository-url>
cd satisfaction-survey-system
Construa e Execute os Containers: Use o Docker Compose para construir e executar os containers. No diretório raiz do projeto, execute:

docker-compose up -d
Acesse a Aplicação: Assim que os containers estiverem em execução, você pode acessar a aplicação em http://localhost:3000.

Configuração
PostgreSQL: : O container do PostgreSQL está configurado com acesso administrativo. Você pode personalizar as configurações do banco de dados no arquivo docker/postgres/Dockerfile.

MongoDB: O container do MongoDB também está configurado com acesso administrativo. A configuração pode ser ajustada no arquivo docker/mongodb/Dockerfile.

Node.js: O container do Node.js executa a versão 22 e está configurado no arquivo docker/nodejs/Dockerfile.