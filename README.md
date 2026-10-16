<div align="center">

FornecePlus

Gestão comercial em uma aplicação Full Stack

Uma solução web para centralizar o gerenciamento de usuários, fornecedores, categorias, produtos e vendas, combinando uma interface Angular com uma API REST desenvolvida em Java e Spring Boot.

<br>







<br>

Funcionalidades ·
Arquitetura ·
Instalação ·
API ·
Testes

</div>

Sobre o projeto

O FornecePlus é uma aplicação web Full Stack voltada ao gerenciamento de informações e operações comerciais. O projeto reúne uma interface desenvolvida com Angular e um backend Java com Spring Boot, responsável por disponibilizar recursos por meio de uma API REST e persistir os dados no MongoDB.

A estrutura separa a apresentação, as regras de negócio e o acesso aos dados, favorecendo a organização e a evolução do código.

Visão geral

<table>
  <tr>
    <td width="50%">
      <h3>Gestão de cadastros</h3>
      Organização dos registros de usuários, fornecedores, categorias e produtos.
    </td>
    <td width="50%">
      <h3>Controle de vendas</h3>
      Recursos para registrar vendas e administrar os respectivos itens.
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h3>Interface web</h3>
      Aplicação Angular com páginas e componentes organizados por funcionalidade.
    </td>
    <td width="50%">
      <h3>API REST</h3>
      Endpoints HTTP estruturados em controllers, services e repositories.
    </td>
  </tr>
</table>

Funcionalidades

Usuários: criar, consultar, atualizar e excluir registros.

Fornecedores: manter os dados dos fornecedores.

Categorias: organizar os produtos por categoria.

Produtos: gerenciar o catálogo de produtos.

Vendas: registrar e consultar vendas.

Itens de venda: administrar os itens relacionados às vendas.

Interface de acesso: páginas de início, cadastro e login.

Validação de dados: recursos de validação no backend.

Nota: a existência das telas de cadastro e login não significa, por si só, que o sistema tenha autenticação e autorização completas. Avalie esses requisitos antes de disponibilizar a aplicação publicamente.

Tecnologias utilizadas

Camada

Tecnologias

Frontend

Angular 22, TypeScript, RxJS, Angular Router, Angular Forms, Angular Material/CDK, HTML e CSS

Backend

Java 17, Spring Boot 4, Spring Web MVC, Spring Data MongoDB, Bean Validation e Lombok

Banco de dados

MongoDB

Build e dependências

Maven Wrapper, npm

Testes

Testes automatizados no backend e configuração de testes no frontend

Arquitetura

O projeto é dividido em duas aplicações independentes que se comunicam por requisições HTTP.

flowchart LR
    U[Usuário] --> FE[Frontend Angular]
    FE -->|HTTP / JSON| API[API REST]
    API --> C[Controllers]
    C --> S[Services]
    S --> R[Repositories]
    R --> DB[(MongoDB)]

Organização do repositório

Forneceplus-main/
├── Backend/
│   ├── src/main/java/com/forneceplus/Backend/
│   │   ├── Config/
│   │   ├── Controllers/
│   │   ├── Entities/
│   │   ├── Exceptions/
│   │   ├── Repositories/
│   │   ├── Services/
│   │   └── Utils/
│   ├── src/main/resources/
│   ├── src/test/
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

Responsabilidade de cada camada

Camada

Responsabilidade

Controllers

Receber requisições HTTP e retornar respostas da API

Services

Concentrar operações e regras da aplicação

Repositories

Acessar os dados persistidos no MongoDB

Entities

Representar as estruturas de dados do domínio

Config

Reunir configurações da aplicação

Exceptions

Tratar situações de erro específicas

Utils

Agrupar utilitários e funções auxiliares

Começando

Pré-requisitos

Instale as ferramentas abaixo antes de iniciar:

Git

Java JDK 17

Node.js e npm

MongoDB local ou MongoDB Atlas

O backend já inclui o Maven Wrapper, portanto não é necessário instalar o Maven separadamente.

1. Clone o repositório

git clone <URL_DO_REPOSITORIO>
cd Forneceplus-main

Substitua <URL_DO_REPOSITORIO> pela URL real do repositório.

2. Configure o MongoDB

Dentro da pasta Backend, crie um arquivo .env com base no .env.example:

MONGODB_URI=mongodb+srv://<usuario>:<senha>@<cluster-host>/?appName=<nome-da-aplicacao>
MONGODB_DATABASE=Forneceplus

Informe os dados da sua instância MongoDB. Se utilizar uma instalação local, ajuste a URI para o endereço correspondente.

Importante: não compartilhe nem envie credenciais, senhas ou arquivos .env para o GitHub. Mantenha as informações privadas no ambiente local.

3. Inicie o backend

Execute em um terminal:

Windows — PowerShell ou CMD

cd Backend
.\mvnw.cmd spring-boot:run

Linux ou macOS

cd Backend
chmod +x mvnw
./mvnw spring-boot:run

Com a configuração válida, a API estará disponível em:

http://localhost:8081

4. Inicie o frontend

Em um segundo terminal, volte à raiz do projeto e execute:

cd Frontend
npm install
npm start

A aplicação Angular ficará disponível, por padrão, em:

http://localhost:4200

Abra o endereço no navegador. O frontend está configurado para realizar chamadas à API local em http://localhost:8081.

API REST

A API disponibiliza endpoints para os principais recursos do sistema.

Recurso

Endpoint base

Métodos

Usuários

/usuarios

GET, POST, GET /{id}, PUT /{id}, DELETE /{id}

Fornecedores

/fornecedores

GET, POST, GET /{id}, PUT /{id}, DELETE /{id}

Categorias

/categorias

GET, POST, GET /{id}, PUT /{id}, DELETE /{id}

Produtos

/produtos

GET, POST, GET /{id}, PUT /{id}, DELETE /{id}

Vendas

/vendas

GET, POST, GET /{id}, PUT /{id}, DELETE /{id}

Itens de venda

/itens

GET, POST, GET /{id}, PUT /{id}, DELETE /{id}

Exemplo de requisição

Com o backend em execução, uma requisição para consultar os produtos pode ser feita com:

curl http://localhost:8081/produtos

As operações de criação e atualização recebem dados em JSON, de acordo com os campos esperados pelo recurso correspondente.

Testes e build

Backend

Na pasta Backend, execute os testes automatizados:

Windows

.\mvnw.cmd test

Linux ou macOS

./mvnw test

Para compilar e empacotar o backend:

./mvnw package

Frontend

Na pasta Frontend, instale as dependências e execute os testes:

npm install
npm test

Para gerar a build de produção:

npm run build

Configurações importantes

Banco de dados: as operações que dependem de persistência exigem uma URI MongoDB válida e acessível.

URL da API: o frontend utiliza http://localhost:8081 nas chamadas HTTP. Para outros ambientes, ajuste essa configuração.

CORS: o backend permite a origem de desenvolvimento http://localhost:4200. Em produção, configure as origens autorizadas para o domínio utilizado.

Segurança: antes de publicar a aplicação em produção, avalie autenticação, autorização, validação de entradas, tratamento de erros e proteção de credenciais.

Próximas melhorias

Algumas evoluções que podem fortalecer o projeto:

Centralizar URLs e parâmetros em configurações por ambiente.

Documentar a API com OpenAPI/Swagger.

Ampliar os testes unitários e de integração.

Implementar e documentar autenticação e autorização, conforme os requisitos.

Preparar configuração de implantação para ambientes de homologação e produção.

Contribuição

Para contribuir com o projeto:

Crie uma branch para a sua alteração.

Mantenha commits objetivos e descritivos.

Execute os testes disponíveis.

Abra um Pull Request explicando as mudanças realizadas.

Licença

Não foi identificada uma licença no repositório fornecido. Antes de redistribuir ou reutilizar o código, defina a licença desejada e inclua um arquivo LICENSE.

<div align="center">

FornecePlus
Aplicação Full Stack para gestão comercial.

<sub>Angular · Java · Spring Boot · MongoDB</sub>

</div>
