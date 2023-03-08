ConnectDevs- A rede social dos DEVs
Este é o backend da aplicação ConnectDEVs - O objetivo dessa aplicação é conseguir armazenar os dados necessários para funcionamento da aplicação ConnectDEVs, contendo cadastro, login, criação, edição e deleção de posts, upload e deleção dos links do portifólio do usuário.

Endpoints

Endpoints
A API tem um total de 4 endpoints, podendo cadastrar seu usuario, realizar login e busca de posts e links.

A url base da API é

Criação de usuário
POST /register - FORMATO DA REQUISIÇÃO

{
"name":"Leticia Pereira Queiroga",
"username":"LeticiaQueiroga",
"email":"leticia@mail.com",
"password":"123456"
}
Caso dê tudo certo, a resposta será assim:

POST /users - FORMATO DA RESPOSTA - STATUS 201

{
"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImxldGljaWFAbWFpbC5jb20iLCJpYXQiOjE2NzgyMTM1MDUsImV4cCI6MTY3ODIxNzEwNSwic3ViIjoiMiJ9.3i6qvSa9WuczHj-GMoupAbUmG2Wc_HUQl6yq2WNp-Nc",
"user": {
"email": "leticia@mail.com",
"name": "Leticia Pereira Queiroga",
"username": "LeticiaQueiroga",
"id": 2
}
}
Possíveis erros
Caso você acabe errando e mandando algum campo errado, a resposta de erro será assim:

POST /users - FORMATO DA RESPOSTA - STATUS 400

"Email already exists"

Login
POST /login - FORMATO DA REQUISIÇÃO

{
"email":"leticia@mail.com",
"password":"123456"
}
Caso dê tudo certo, a resposta será assim:

POST /login - FORMATO DA RESPOSTA - STATUS 200

{
"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImxldGljaWFAbWFpbC5jb20iLCJpYXQiOjE2NzgyMzg5MjEsImV4cCI6MTY3ODI0MjUyMSwic3ViIjoiMiJ9.-Iy2r_FcpLxPif-BQXKoJOtuwoxfLZsYETgNGQjL_yA",
"user": {
"email": "leticia@mail.com",
"name": "Leticia Pereira Queiroga",
"username": "LeticiaQueiroga",
"id": 2
}
}
Com essa resposta, vemos que temos duas informações, o user e o token respectivo, dessa forma você pode guardar o token no localStorage para fazer a gestão do usuário no seu frontend.

Rotas que necessitam de autorização
Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

Authorization: Bearer {token} Após o usuário estar logado, ele deve conseguir buscar os produtos da hamburgueria:

GET /posts

Não é necessário um corpo da requisição.
Caso dê tudo certo, a resposta será assim:

GET /posts - FORMATO DA RESPOSTA - STATUS 200

[
{
"title": "Qual a melhor linguagem de programação na sua opniao? Veja mais",
"text": "sdcadcaLorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
"userId": 2,
"id": 2
}

    {...}

]

POST/posts
{
"title": "Qual a melhor linguagem de programação na sua opniao?",
"text":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
"userId":2
}

Caso dê tudo certo, a resposta será assim:

POST /posts - FORMATO DA RESPOSTA - STATUS 201

[
{
"title": "Qual a melhor linguagem de programação na sua opniao? Veja mais",
"text": "sdcadcaLorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
"userId": 2,
"id": 2
}

]

PATCH/posts/id
{
"title": "Qual a melhor linguagem de programação na sua opniao?",
"text":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
"userId":2
}

Caso dê tudo certo, a resposta será assim:

PATCH/posts/id - FORMATO DA RESPOSTA - STATUS 200

[
{
"title": "Qual a melhor linguagem de programação na sua opniao? Veja mais",
"text": "sdcadcaLorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
"userId": 2,
"id": 2
}

]

DELETE /posts/id

Não é necessário um corpo da requisição.
Caso dê tudo certo, a resposta será assim:

DELETE /posts/id - FORMATO DA RESPOSTA - STATUS 200

[
{}

]

GET /links

Não é necessário um corpo da requisição.
Caso dê tudo certo, a resposta será assim:

GET /links - FORMATO DA RESPOSTA - STATUS 200

[
{
"link": "https://kenzie-burguer-v2-leticia-pq-ueiroga.vercel.app",
"userId": 2,
"id": 1
}
{...}
]

POST/links
{
"link":"https://kenzie-burguer-v2-leticia-pq-ueiroga.vercel.app",
"userId":2
}

Caso dê tudo certo, a resposta será assim:

POST/links- FORMATO DA RESPOSTA - STATUS 201

[
{
"link": "https://kenzie-burguer-v2-leticia-pq-ueiroga.vercel.app",
"userId": 2,
"id": 1
}

]

DELETE /links/id

Não é necessário um corpo da requisição.
Caso dê tudo certo, a resposta será assim:

DELETE /links/id - FORMATO DA RESPOSTA - STATUS 200

[
{}

]
