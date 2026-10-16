FornecePlus

Aplicação web para gerenciamento de operações comerciais, com módulos de usuários, fornecedores, categorias, produtos, vendas e itens de venda. O projeto utiliza uma arquitetura separada entre frontend e backend, com comunicação por API REST e persistência em MongoDB.

Visão geral

O FornecePlus foi desenvolvido como uma aplicação full stack para centralizar cadastros e operações básicas de gestão comercial em uma interface web.

Principais funcionalidades

Cadastro, consulta, edição e remoção de usuários.

Gerenciamento de fornecedores.

Gerenciamento de categorias.

Gerenciamento de produtos.

Registro e manutenção de vendas.

Gerenciamento de itens associados às vendas.

Interface com páginas de início, cadastro e login.

API REST organizada em controllers, services, repositories e entities.

Persistência de dados com MongoDB.

Status: projeto em desenvolvimento. Consulte os módulos e endpoints implementados no código antes de utilizar a aplicação em um ambiente de produção.

Tecnologias

Frontend

Angular 22

TypeScript

Angular Router

Angular Forms

Angular Material/CDK

RxJS

HTML e CSS

Backend

Java 17

Spring Boot 4

Spring Web MVC

Spring Data MongoDB

Bean Validation

Lombok

Maven

Banco de dados

MongoDB

Arquitetura

O repositório está dividido em duas aplicações principais:

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
    ├── src/
    │   └── app/
    │       ├── cadastro/
    │       ├── categoria/
    │       ├── fornecedor/
    │       ├── home/
    │       ├── header/
    │       ├── footer/
    │       ├── item-venda/
    │       ├── login/
    │       ├── produto/
    │       └── venda/
    ├── angular.json
    └── package.json

Fluxo da aplicação

O usuário interage com a interface Angular.

O frontend envia requisições HTTP para a API REST.

Os controllers do Spring recebem as requisições e encaminham as operações aos services.

Os services executam as regras da aplicação e utilizam os repositories para acessar o MongoDB.

A API retorna as respostas ao frontend.

Requisitos

Antes de executar o projeto, instale:

Java JDK 17

Node.js e npm

MongoDB local ou MongoDB Atlas

Git

O backend inclui Maven Wrapper (mvnw/mvnw.cmd), portanto não é necessário instalar o Maven separadamente.

Configuração e execução

Execute o backend e o frontend em terminais separados.

1. Clone o repositório

git clone <URL_DO_REPOSITORIO>
cd Forneceplus-main

Substitua <URL_DO_REPOSITORIO> pelo endereço real do repositório no GitHub.

2. Configure o banco de dados

Na pasta Backend, crie um arquivo chamado .env, utilizando .env.example como referência:

MONGODB_URI=mongodb+srv://<usuario>:<senha>@<cluster-host>/?appName=<nome-da-aplicacao>
MONGODB_DATABASE=Forneceplus

Preencha as variáveis com os dados do seu ambiente MongoDB. Para uma instalação local, utilize a URI correspondente à sua instância.

Segurança: não publique o arquivo .env, credenciais ou strings de conexão. O arquivo deve permanecer fora do controle de versão.

3. Execute o backend

A partir da raiz do repositório:

Windows (PowerShell ou CMD):

cd Backend
.\mvnw.cmd spring-boot:run

Linux ou macOS:

cd Backend
chmod +x mvnw
./mvnw spring-boot:run

A API ficará disponível, por padrão, em:

http://localhost:8081

4. Execute o frontend

Abra outro terminal na raiz do repositório:

cd Frontend
npm install
npm start

O servidor de desenvolvimento do Angular ficará disponível, por padrão, em:

http://localhost:4200

Acesse esse endereço no navegador. O frontend está configurado para consumir a API local em http://localhost:8081.

Endpoints da API

Os endpoints abaixo estão definidos nos controllers do backend. Para operações de criação e atualização, envie um corpo JSON compatível com a entidade correspondente.

Recurso

Base do endpoint

Operações

Usuários

/usuarios

Listar, consultar por ID, criar, atualizar e excluir

Fornecedores

/fornecedores

Listar, consultar por ID, criar, atualizar e excluir

Categorias

/categorias

Listar, consultar por ID, criar, atualizar e excluir

Produtos

/produtos

Listar, consultar por ID, criar, atualizar e excluir

Vendas

/vendas

Listar, consultar por ID, criar, atualizar e excluir

Itens de venda

/itens

Listar, consultar por ID, criar, atualizar e excluir

Com o backend em execução local, por exemplo, a listagem de produtos pode ser consultada em http://localhost:8081/produtos.

Métodos HTTP utilizados

Método

Finalidade

GET

Consultar recursos

POST

Criar recursos

PUT

Atualizar recursos

DELETE

Excluir recursos

Testes e build

Backend

Na pasta Backend, execute os testes automatizados:

./mvnw test

No Windows:

.\mvnw.cmd test

Para gerar o artefato compilado:

./mvnw package

Frontend

Na pasta Frontend:

npm test

Para gerar a build:

npm run build

Os comandos devem ser executados com as dependências instaladas e um ambiente compatível com as versões utilizadas no projeto.

Considerações técnicas

O frontend utiliza o endereço http://localhost:8081 diretamente nas chamadas HTTP. Para outros ambientes, será necessário ajustar a configuração da URL da API.

O backend está configurado para permitir requisições de desenvolvimento originadas de http://localhost:4200. Em produção, configure as origens permitidas de acordo com o domínio implantado.

A execução funcional das operações que dependem do banco exige uma URI MongoDB válida e acessível.

A presença de telas de login e cadastro não deve ser interpretada, por si só, como garantia de autenticação e autorização seguras. Essas camadas devem ser avaliadas e implementadas conforme os requisitos da aplicação antes de uma implantação pública.

Próximas evoluções

Possíveis melhorias para versões futuras:

Centralizar a URL da API em configuração por ambiente.

Documentar os contratos da API com OpenAPI/Swagger.

Implementar autenticação e autorização com mecanismos apropriados.

Ampliar a cobertura de testes de integração e de interface.

Adicionar instruções de implantação e configuração para produção.

Contribuição

Contribuições são bem-vindas. Para propor uma melhoria:

Crie uma branch específica para sua alteração.

Faça commits objetivos e descritivos.

Valide as mudanças com os testes disponíveis.

Abra um Pull Request explicando o objetivo e o impacto da alteração.

Licença

Nenhuma licença foi identificada no repositório fornecido. Antes de redistribuir ou reutilizar o projeto, defina uma licença e registre-a no arquivo LICENSE, conforme a intenção dos autores.

Desenvolvido como projeto full stack para prática de desenvolvimento web, integração entre frontend e backend, construção de APIs REST e persistência de dados.
