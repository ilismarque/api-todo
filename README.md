<!-- # Desafio 01 - Conceitos do Node.js -->
<h1 align="center" >API Todo</h1>

<p align="center">
  <a href="#-projeto">Projeto</a> •
  <a href="#-tecnologias">Tecnologias</a> •
  <a href="#-requisitos-da-aplicação">Requisitos</a> •
  <a href="#-como-utilizar">Como utilizar</a> •
  <a href="#-rotas">Rotas</a>
  
</p>

---

## 💻 Projeto

Desafio do primeiro modulo da trilha de Node.js do bootcamp Ignite da Rocketseat. Deve ser criada uma API para o gerenciamento de tarefas no estilo _todo_, para aplicar os conceitos aprendidos, como:

- Metódos POST, GET, PUT, PATCH e DELETE
- Parâmetros de requisição
- HTTP codes
- Middlewares

---

## 🛠 Tecnologias

- Node.js
- Express
- Nodemon

---

## 🚀 Como utilizar

Para clonar e rodar esse projeto, é necessário ter o [Git](https://git-scm.com), e o [Node.js](https://nodejs.org/en/download/) instalados em seu computador.

Clone este repositório

```bash
git clone https://github.com/ilismarque/api-todo.git
```

ou

```bash
git clone git@github.com:ilismarque/api-todo.git
```

Instale as dependências (utilizei o yarn, mas sinta-se à vontade para utilizar outro gerenciador)

```bash
yarn
```

ou

```bash
npm install
```

Inicie o servidor

```bash
yarn run dev
```

ou

```bash
npm run dev
```

>O projeto esta configurado para rodar na porta _3333_, caso ela esteja indisponível em sua máquina, altere o arquivo ```server.js``` para uma porta disponível.

Para testar as rotas da API, podem ser utilizadas ferramentas como [Insomnia](https://insomnia.rest/), [Postman](https://www.postman.com/), [Hoppscotch](https://hoppscotch.io/), entre outras.

---

## 💻 Requisitos da aplicação

- [x] Criar um usuário
- [x] Criar uma nova tarefa para um usuário
- [x] Listar todas as tarefas do usuário
- [x] Alterar o _title_ e _deadline_ de uma tarefa existente
- [x] Marcar uma tarefa como feita
- [x] Excluir uma tarefa

---

## 🚀 Rotas

### Usuário

```http
POST /users
```

A rota deve receber `name`, e `username` dentro do corpo da requisição.

```js
{
 name: 'Mrs Tester',
 username: 'mrstester'
}
```

---

### Tarefas

>Todas as rotas devem receber, pelo header da requisição, a propriedade `username` contendo o username do usuário.

```http
GET /todos
```

Retornar uma lista com todas as tarefas do usuário.

```json
[
  {
    "id": "4d235ba4-7dbe-4ce1-9d3b-b19e7079f3e1",
    "title": "task 1",
    "done": false,
    "deadline": "2022-12-28T00:00:00.000Z",
    "created_at": "2022-12-27T13:42:45.888Z"
  },
  {
    "id": "88e378ed-165d-4332-a7b7-2ce3b56d6f3d",
    "title": "task 2",
    "done": false,
    "deadline": "2022-12-18T00:00:00.000Z",
    "created_at": "2022-12-27T13:42:54.634Z"
  }
]
```

```http
POST /todos
```

A rota deve receber `title` e `deadline` no corpo da requisição. Por padrão a tarefa é criada com a propriedade `done` setada com o valor _false_.

```json
{
  "title" : "task 8",
  "deadline": "2023-11-18"
}
```

```http
PUT /todos/:id
```

Altera os campos informados no corpo da requisição para a tarefa que possuir um id igual ao id presente nos parâmetros da rota. Devem ser informadas as propriedades `title` e `deadline` dentro do corpo da requisição, para que as informações sejam atualizadas.

```json
{
  "title" : "task update",
  "deadline": "2023-11-18"
}
```

```http
PATCH /todos/:id/done
```

Altera a propriedade `done` para _true_ da tarefa que possuir um id igual ao id presente nos parâmetros da rota. Não é necessário enviar informações no corpo da requisição.

```http
DELETE /todos/:id
```

Deleta a tarefa que possuir um id igual ao id presente nos parâmetros da rota. Não é necessário enviar informações no corpo da requisição.

---

## 🚀 Status Code

A API retorna os seguintes status codes

| Code | Descrição |
| :--- | :--- |
| 200 | `OK` |
| 201 | `CREATED` |
| 204 | `NO CONTENT`|
| 404 | `BAD REQUEST` |
| 404 | `NOT FOUND` |
