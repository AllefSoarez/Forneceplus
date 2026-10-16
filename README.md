FornecePlus

Aplicação web Full Stack desenvolvida para o gerenciamento de operações comerciais. O sistema permite centralizar o gerenciamento de usuários, fornecedores, categorias, produtos e vendas, utilizando Angular no frontend, Java com Spring Boot no backend e MongoDB para persistência de dados.

Tecnologias

* Java 17
* Spring Boot 4
* Spring Web MVC
* Spring Data MongoDB
* Bean Validation
* Lombok
* Angular 22
* TypeScript
* RxJS
* Angular Router e Angular Forms
* Angular Material/CDK
* MongoDB
* Maven Wrapper
* npm

Funcionalidades

* Cadastro, consulta, atualização e exclusão de usuários.
* Gerenciamento de fornecedores.
* Gerenciamento de categorias.
* Cadastro e gerenciamento de produtos.
* Registro e consulta de vendas.
* Gerenciamento de itens de venda.
* Interface web com páginas de início, cadastro e login.
* Validação de dados no backend.
* Tratamento de exceções da aplicação.
* Comunicação entre frontend e backend por meio de uma API REST.

Estrutura do projeto

Forneceplus-main/
├── Backend/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/forneceplus/Backend/
│   │   │   │   ├── Config/
│   │   │   │   ├── Controllers/
│   │   │   │   ├── Entities/
│   │   │   │   ├── Exceptions/
│   │   │   │   ├── Repositories/
│   │   │   │   ├── Services/
│   │   │   │   └── Utils/
│   │   │   └── resources/
│   │   └── test/
│   ├── .env.example
│   ├── pom.xml
│   ├── mvnw
│   └── mvnw.cmd
└── Frontend/
    ├── public/
    ├── src/app/
    │   ├── cadastro/
    │   ├── categoria/
    │   ├── fornecedor/
    │   ├── home/
    │   ├── header/
    │   ├── footer/
    │   ├── item-venda/
    │   ├── login/
    │   ├── produto/
    │   └── venda/
    ├── angular.json
    └── package.json

Arquitetura

A aplicação é dividida em duas partes principais: frontend e backend.

O frontend, desenvolvido com Angular, é responsável pela interface e pela interação com o usuário. O backend, desenvolvido com Spring Boot, disponibiliza uma API REST para processar as requisições e acessar o banco de dados MongoDB.

O backend segue uma organização em camadas:

1. Entities: representam as estruturas de dados do domínio.
2. Repositories: realizam as operações de acesso e persistência no MongoDB.
3. Services: concentram as operações e regras de negócio.
4. Controllers: recebem as requisições HTTP e disponibilizam os endpoints da API.
5. Config: reúne as configurações da aplicação.
6. Exceptions: organiza o tratamento de exceções.
7. Utils: contém funções auxiliares.

Recursos da API

Os endpoints estão organizados por recurso:

Recurso	Endpoint base
Usuários	/usuarios
Fornecedores	/fornecedores
Categorias	/categorias
Produtos	/produtos
Vendas	/vendas
Itens de venda	/itens

As operações disponíveis devem ser consultadas na implementação de cada controller. Os recursos podem contemplar consultas, criação, atualização e exclusão.

Exemplos de uso

Consultar produtos

Requisição:

GET /produtos

Comando:

curl http://localhost:8081/produtos

A requisição consulta os produtos disponibilizados pela API.

As operações de criação e atualização utilizam requisições HTTP com dados em JSON, conforme os campos definidos para cada recurso.

Como executar localmente

Pré-requisitos

* Git
* Java JDK 17
* Node.js e npm
* MongoDB local ou MongoDB Atlas

O Maven Wrapper está incluído no backend, dispensando a instalação independente do Maven.

1. Clonar o repositório

git clone <URL_DO_REPOSITORIO>
cd Forneceplus-main

Substitua <URL_DO_REPOSITORIO> pela URL do repositório.

2. Configurar o banco de dados

Na pasta Backend, crie um arquivo .env com base no arquivo .env.example.

Configure a conexão com o MongoDB:

MONGODB_URI=sua_uri_de_conexao
MONGODB_DATABASE=Forneceplus

Utilize os dados da sua instância MongoDB e confirme se os nomes das variáveis correspondem à configuração do backend.

Não envie credenciais ou arquivos .env com informações privadas para o GitHub.

3. Executar o backend

Windows:

cd Backend
.\mvnw.cmd spring-boot:run

Linux ou macOS:

cd Backend
chmod +x mvnw
./mvnw spring-boot:run

A API estará disponível em:

http://localhost:8081

4. Executar o frontend

Abra outro terminal na raiz do projeto:

cd Frontend
npm install
npm start

A interface web estará disponível em:

http://localhost:4200

Mantenha o backend e o frontend em execução para utilizar a aplicação.

Testes e compilação

Backend

Executar os testes automatizados:

Windows:

.\mvnw.cmd test

Linux ou macOS:

./mvnw test

Gerar o pacote da aplicação:

./mvnw package

Frontend

Instalar as dependências e executar os testes:

npm install
npm test

Gerar a build de produção:

npm run build

Execute cada comando dentro da pasta correspondente. A execução dos testes depende da configuração presente no projeto.

Configurações importantes

* Banco de dados: o backend precisa de uma conexão válida com o MongoDB.
* Comunicação: o frontend utiliza a API local na porta 8081.
* CORS: a origem de desenvolvimento configurada é http://localhost:4200.
* Segurança: as telas de cadastro e login não garantem, por si só, a existência de autenticação e autorização completas.

Antes de disponibilizar a aplicação em produção, revise as configurações de ambiente, as origens CORS permitidas, a proteção de credenciais e os mecanismos de segurança.

Status do projeto

Recursos documentados:

* Estrutura Full Stack com Angular e Spring Boot.
* Integração com MongoDB.
* Organização do backend em camadas.
* Recursos de gerenciamento comercial.
* Configuração de execução e compilação das aplicações.

Possíveis melhorias:

* Documentar os endpoints com OpenAPI/Swagger.
* Ampliar os testes unitários e de integração.
* Implementar autenticação e autorização, conforme os requisitos.
* Adicionar configurações específicas para produção.
* Automatizar o processo de integração e implantação contínuas.

Licença

Não foi identificada uma licença no material utilizado para esta documentação. Caso o projeto seja disponibilizado para reutilização ou distribuição, defina a licença apropriada e inclua um arquivo LICENSE no repositório.
