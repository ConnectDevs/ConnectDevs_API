# **ConnectDevs - A rede social dos DEVs**

</br>

Este é o backend da aplicação ConnectDEVs - O objetivo dessa aplicação é conseguir armazenar os dados necessários para funcionamento da aplicação ConnectDEVs, contendo cadastro, login, criação, edição e deleção de posts, upload e deleção dos links do portifólio do usuário.

</br>

---
</br>

## **Endpoints**

A API tem um total de **4 endpoints**, podendo cadastrar seu usuario, realizar login e busca de posts e links.

A url base da API é:&nbsp;&nbsp; ``https://connectdevsapi.onrender.com``

</br>

---
</br>

## **Criação de usuário**
FORMATO DA REQUISIÇÂO:&nbsp;&nbsp; ``POST /register``

{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"name":&nbsp;&nbsp;&nbsp;"Leticia Pereira Queiroga",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"username":&nbsp;&nbsp;&nbsp;"LeticiaQueiroga",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"email":&nbsp;&nbsp;&nbsp;"leticia@mail.com",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"password":&nbsp;&nbsp;&nbsp;"123456"
    </br>
}

</br></br>

## **Caso dê tudo certo, a resposta será assim:**

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 201 - Created``

</br>

DADOS DA RESPOSTA:

{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"accessToken": &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImxldGljaWFAbWFpbC5jb20iLCJpYXQiOjE2NzgyMTM1MDUsImV4cCI6MTY3ODIxNzEwNSwic3ViIjoiMiJ9.3i6qvSa9WuczHj-GMoupAbUmG2Wc_HUQl6yq2WNp-Nc",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"user": &nbsp;&nbsp;{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"email": "leticia@mail.com",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"name": "Leticia Pereira Queiroga",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"username": "LeticiaQueiroga",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": 2
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
    </br>
}

</br></br>

## **Possíveis erros:**

Caso você acabe errando e mandando algum campo errado, a resposta de erro será assim:

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 400 - Bad Request``

MENSAGEM DE ERRO: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;``"Email already exists"``

</br>

---

</br>

## **Login do usuário**
FORMATO DA REQUISIÇÂO:&nbsp;&nbsp; ``POST /login``

{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"email":&nbsp;&nbsp;&nbsp;"leticia@mail.com",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"password":&nbsp;&nbsp;&nbsp;"123456"
    </br>
}

</br></br>

## **Caso dê tudo certo, a resposta será assim:**

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 200 - OK``

</br>

DADOS DA RESPOSTA:

{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"accessToken": &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImxldGljaWFAbWFpbC5jb20iLCJpYXQiOjE2NzgyMTM1MDUsImV4cCI6MTY3ODIxNzEwNSwic3ViIjoiMiJ9.3i6qvSa9WuczHj-GMoupAbUmG2Wc_HUQl6yq2WNp-Nc",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"user": &nbsp;&nbsp;{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"email": "leticia@mail.com",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"name": "Leticia Pereira Queiroga",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"username": "LeticiaQueiroga",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": 2
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
    </br>
}

</br>

Com essa resposta, vemos que temos duas informações, o user e o token respectivo, dessa forma você pode guardar o token no localStorage para fazer a gestão do usuário no seu frontend.

</br>

---
</br>


## **Rotas que necessitam de autorização:**

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

``Authorization: Bearer {token}``

Após o usuário estar logado, ele deve conseguir buscar os posts:

</br>

---
</br>

**[ Necessário Token ]**

## **Listar informações do usuário logado / AutoLogin**
FORMATO DA REQUISIÇÂO:&nbsp;&nbsp; ``GET /users/id``&nbsp;&nbsp;&nbsp;&nbsp;**[ Id do Usuário ]**

Não é necessário um corpo da requisição.

</br></br>

## **Caso dê tudo certo, a resposta será assim:**

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 200 - OK``

</br>

DADOS DA RESPOSTA:

{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"accessToken": &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImxldGljaWFAbWFpbC5jb20iLCJpYXQiOjE2NzgyMTM1MDUsImV4cCI6MTY3ODIxNzEwNSwic3ViIjoiMiJ9.3i6qvSa9WuczHj-GMoupAbUmG2Wc_HUQl6yq2WNp-Nc",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"user": &nbsp;&nbsp;{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"email": "leticia@mail.com",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"name": "Leticia Pereira Queiroga",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"username": "LeticiaQueiroga",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": 2
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}
    </br>
}

</br>

---
</br>

**[ Necessário Token ]**

## **Listar todos os Posts da API**
FORMATO DA REQUISIÇÂO:&nbsp;&nbsp; ``GET /posts``

Não é necessário um corpo da requisição.

</br></br>

## **Caso dê tudo certo, a resposta será assim:**

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 200 - OK``

</br>

DADOS DA RESPOSTA:

[{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"title": "Qual a melhor linguagem de programação na sua opniao? Veja mais",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text": "sdcadcaLorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"userId": 2,
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": 2,
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"username": "LeticiaQueiroga"
    </br>
}]

</br>

---
</br>

**[ Necessário Token ]**

## **Criação de Posts**
FORMATO DA REQUISIÇÂO:&nbsp;&nbsp; ``POST /posts``

{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"title": "Qual a melhor linguagem de programação na sua opniao?",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"userId": 2 &nbsp;&nbsp;&nbsp;&nbsp;**[ Id do Usuário ]**
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"username": "LeticiaQueiroga"
    </br>
}

</br></br>

## **Caso dê tudo certo, a resposta será assim:**

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 201 - Created``

</br>

DADOS DA RESPOSTA:

[{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"title": "Qual a melhor linguagem de programação na sua opniao?",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"userId": 2
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": 2
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"username": "LeticiaQueiroga"
    </br>
}]

</br>

---
</br>

**[ Necessário Token ]**

## **Atualização(Edição) de Posts**
FORMATO DA REQUISIÇÂO:&nbsp;&nbsp; ``PATCH /posts/id`` &nbsp;&nbsp;&nbsp;&nbsp;**[ Id do Post ]**

{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"title": "Qual a melhor linguagem de programação na sua opniao?",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"userId":2 &nbsp;&nbsp;&nbsp;&nbsp;**[ Id do Usuário ]**
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"username": "LeticiaQueiroga"
    </br>
}

</br></br>

## **Caso dê tudo certo, a resposta será assim:**

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 200 - OK``

</br>

DADOS DA RESPOSTA:

[{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"title": "Qual a melhor linguagem de programação na sua opniao?",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"userId":2
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": 2
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"username": "LeticiaQueiroga"
    </br>
}]

</br>

---
</br>

**[ Necessário Token ]**

## **Remoção de Posts**
FORMATO DA REQUISIÇÂO:&nbsp;&nbsp; ``DELETE /posts/id`` &nbsp;&nbsp;&nbsp;&nbsp;**[ Id do Post ]**

Não é necessário um corpo da requisição.

</br></br>

## **Caso dê tudo certo, a resposta será assim:**

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 200 - OK``

</br>

DADOS DA RESPOSTA:

[&nbsp;&nbsp;{&nbsp;}&nbsp;&nbsp;]

</br>

---
</br>

**[ Necessário Token ]**

## **Listar todos os Links de Repositórios da API**
FORMATO DA REQUISIÇÂO:&nbsp;&nbsp; ``GET /links``

Não é necessário um corpo da requisição.

</br></br>

## **Caso dê tudo certo, a resposta será assim:**

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 200 - OK``

</br>

DADOS DA RESPOSTA:

[{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"link": "https://kenzie-burguer-v2-leticia-pq-ueiroga.vercel.app",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"userId": 2,
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": 1
    </br>
}]

</br>

---
</br>

**[ Necessário Token ]**

## **Publicar novo Link de Repositório**
FORMATO DA REQUISIÇÂO:&nbsp;&nbsp; ``POST /links``

{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"link": "https://kenzie-burguer-v2-leticia-pq-ueiroga.vercel.app",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"userId": 2 &nbsp;&nbsp;&nbsp;&nbsp;**[ Id do Usuário ]**
    </br>
}

</br></br>

## **Caso dê tudo certo, a resposta será assim:**

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 201 - Created``

</br>

DADOS DA RESPOSTA:

[{
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"link": "https://kenzie-burguer-v2-leticia-pq-ueiroga.vercel.app",
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"userId": 2,
    </br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": 1
    </br>
}]

</br>

---
</br>

**[ Necessário Token ]**

## **Remoção de Links**
FORMATO DA REQUISIÇÂO:&nbsp;&nbsp; ``DELETE /links/id`` &nbsp;&nbsp;&nbsp;&nbsp;**[ Id do Link ]**

Não é necessário um corpo da requisição.

</br></br>

## **Caso dê tudo certo, a resposta será assim:**

FORMATO DA RESPOSTA:&nbsp;&nbsp;``STATUS 200 - OK``

</br>

DADOS DA RESPOSTA:

[&nbsp;&nbsp;{&nbsp;}&nbsp;&nbsp;]
