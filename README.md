## ✨ Simples sitema de autenticação em Node.js
Esse é um sistema de registro e login feit em Typescript, onde ao se autenticar, o usuário receberá um token `JWT` para permanecer a sessão. Foi utilizado **express.js**, **TypeORM** e **MySQL** nesse projeto! Atualmente as rotas existe são essas abaixo:

## 🧰 Variáveis de ambiente
Crie um arquivo de nome `.env`, onde nele deverá possuir os seguintes atributos abaixo:
```toml
# Porta onde será iniciada a API e secret JWT para assinar os tokens
PORT=8081
JWT_SECRET=SEU SECRET JWT

# development ou production
NODE_ENV=development

# Informações para conexão ao banco de dados MySQL
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASS=admin
DB_NAME=auth_system
```

## 🔧 Buildando e iniciando o projeto
Utilizarei `pnpm` para realizar os passos abaixos.

Para realizar o build do projeto, execute o comando `pnpm tsc` estando dentro da pasta do projeto. Note que uma pasta chamada `build` será criada automaticamente.

Para iniciar o projeto através da build gerada:

```
pnpm start
``` 

Caso seja necessário iniciar em **ambiente de desenvolvimento**, utilize o comando abaixo. Assim seu projeto será reiniciado automaticamente a cada modificação.

```
pnpm dev
```

## 📋 Exemplos de requisições e suas respostas
**POST** `api/v1/auth/register` - Rota para realizar o cadastro de uma nova conta.
> **Request Body:**
> ```json
> {
> 	"username": "AliceDev",
> 	"email": "imalicedev@gmail.com",
> 	"password": "alicedev1234"
> }
> ```
> 
> **Response:**
> ```json
> {
>   "message": "Usuário inserido com sucesso!"
> }

**POST** `api/v1/auth/login` - Rota para realizar o login em uma conta já cadastrada.
> **Request Body:**
> ```json
> {
> 	"email": "imalicedev@gmail.com",
> 	"password": "alicedev1234"
> }
> ```
> 
> **Response:**
> ```json
> {
> 	"token": "eyJh....."
> }
> ```

**GET** `api/v1/profile` - Rota padrão obter dados sobre o usuário logado com o token de sessão. Obrigatório possuir um **Token Bearer** em `Authorization`.
> **Response:**
> ```json
> {
> 	"id": 1,
> 	"email": "imalicedev@gmail.com",
> 	"username": "AliceDev",
> 	"createdAt": "2024-07-12T17:43:33.550Z"
> }