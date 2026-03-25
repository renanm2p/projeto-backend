Backend API - Projeto Node.js

## Descrição:

Este projeto é uma API backend desenvolvida em Node.js utilizando Express e Sequelize para gerenciamento de dados. A aplicação segue uma arquitetura modular, com separação clara entre controllers, services, models e rotas.

O sistema oferece funcionalidades típicas de uma API REST, incluindo:

Autenticação de usuários com JWT
Gerenciamento de usuários
CRUD de produtos e categorias
Upload/gestão de imagens de produtos
Documentação da API com Swagger

## Tecnologias Utilizadas:
Node.js
Express
Sequelize (ORM)
PostgreSQL
JWT (jsonwebtoken)
Bcrypt (hash de senhas)
Swagger (documentação)
Jest + Supertest (testes)

## Pré-requisitos:

Antes de iniciar, você precisa ter instalado:

Node.js (>= 18 recomendado)
npm ou yarn
PostgreSQL
Git

## Instalação:
 Clone o repositório
git clone <URL_DO_REPOSITORIO>

Acesse a pasta do projeto
cd projeto-backend/project-root

Instale as dependências
npm install

## Configuração:

Crie um arquivo .env na raiz do projeto (caso não exista) com base no modelo abaixo:

PORT=3000

DB_HOST=localhost
DB_USER=seu_usuario
DB_PASSWORD=sua_senha
DB_NAME=nome_do_banco
DB_PORT=5432

JWT_SECRET=sua_chave_secreta

## Banco de Dados:

O projeto utiliza Sequelize para ORM.

Rodar migrations (se aplicável)
npx sequelize-cli db:migrate
Seed (se houver)
npx sequelize-cli db:seed:all

## Execução:
Ambiente de desenvolvimento
npm run dev
Produção
npm start

A API estará disponível em:

http://localhost:3000

## Estrutura do Projeto:
src/
├── app.js
├── server.js
├── config/
│   └── database.js
├── controllers/
│   ├── AuthController.js
│   ├── UserController.js
│   ├── ProductController.js
│   └── CategoryController.js
├── database/
│   └── index.js
├── middleware/
│   └── auth.js
├── models/
│   ├── User.js
│   ├── Product.js
│   ├── Category.js
│   ├── ProductImage.js
│   └── ProductOption.js
├── routes/
│   ├── userRoutes.js
│   ├── productRoutes.js
│   └── categoryRoutes.js
└── services/
    └── ProductService.js

## Autenticação:

A autenticação é feita via JWT (JSON Web Token).

## Fluxo básico:
Usuário realiza login
Recebe um token JWT
Envia o token no header das requisições protegidas:
Authorization: Bearer <token>

Principais Endpoints:

## Usuários:
POST /users → Criar usuário
GET /users → Listar usuários
 
## Autenticação:
POST /auth/login → Login

## Produtos:
GET /products
POST /products
PUT /products/:id
DELETE /products/:id

## Categorias:
GET /categories
POST /categories

## Documentação da API:

A documentação interativa está disponível via Swagger:

http://localhost:3000/api-docs
Testes:

O projeto utiliza Jest e Supertest.

## Executar testes:
npm test

## Deploy:

## Para deploy em produção:

Configure variáveis de ambiente corretamente
Use um gerenciador de processos como PM2:
npm install -g pm2
pm2 start src/server.js
Configure proxy reverso (ex: Nginx) se necessário

## Troubleshooting:
Erro de conexão com banco
Verifique credenciais no .env
Confirme se o PostgreSQL está rodando
Porta em uso
lsof -i :3000
kill -9 <PID>
Problemas com dependências
rm -rf node_modules package-lock.json
npm install

## Contribuição:

Contribuições são bem-vindas.

## Passos:
Fork do projeto
Crie uma branch:
git checkout -b feature/minha-feature

## Commit:
git commit -m "feat: minha nova feature"

## Push:
git push origin feature/minha-feature
Abra um Pull Request

## Observações Finais:
O projeto segue boas práticas de organização em camadas
Uso de services para lógica de negócio
Middleware para autenticação
Estrutura escalável para crescimento da API