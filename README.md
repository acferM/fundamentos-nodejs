# Fundamentos NodeJS

Esta é a primeira aplicação construida no Ignite (curso da Rocketseat), onde é mostrado os conceitos básicos de NodeJS.

# Métodos HTTP

## GET

### Funcionalidade: 

O método GET serve para buscar informações de dentro do servidor.

### Como usar (ExpressJS)

```js
const express = require('express')

const app = express()

app.get('/rota', (request, response) => {
  // Seu código

  return response.json(/* Seu retorno em JSON */)
})

app.listen(3333)
```

**GET NÃO RECEBE BODY PARAMS**

---

## POST

### Funcionalidade: 

O método POST inserir uma informação no servidor.

### Como usar (ExpressJS)

```js
const express = require('express')

const app = express()

app.post('/rota', (request, response) => {
  // Seu código

  return response.json(/* Seu retorno em JSON */)
})
```

app.listen(3333)

---

## PUT

### Funcionalidade: 

O método PUT serve para alterar por completo uma informação no servidor.

### Como usar (ExpressJS)

```js
const express = require('express')

const app = express()

app.put('/rota', (request, response) => {
  // Seu código

  return response.json(/* Seu retorno em JSON */)
})

app.listen(3333)
```

---

## PATCH

### Funcionalidade: 

O método PATCH serve para atualizar uma parte específica da informação no servidor.

### Como usar (ExpressJS)

```js
const express = require('express')

const app = express()

app.patch('/rota', (request, response) => {
  // Seu código

  return response.json(/* Seu retorno em JSON */)
})

app.listen(3333)
```

---

## DELETE

### Funcionalidade: 

O método DELETE serve Deletar uma informação do servidor.

### Como usar (ExpressJS)

```js
const express = require('express')

const app = express()

app.delete('/rota', (request, response) => {
  // Seu código

  return response.json(/* Seu retorno em JSON */)
})

app.listen(3333)
```

**DELETE NÃO RECEBE BODY PARAMS**

# Tipos de parâmetros

Ao fazer uma chamada a uma api, há vários parâmetros que passamos para fazer a operação.

## Route Params

### Como passar em rotas HTTP

```js
'https://suaApi.com/users/1'
```

### Funcionalidade

Os route params são parâmetros que estão diretamente nas rotas, eles são utilizados em rotas que dependem diretamente desses parâmetros, por exemplo, ao deletar um usuário, precisa-se do parâmetro de ID de qual usuário será deletado.

### Como usar

```js
const express = require('express')

const app = express()

app.delete('/users/:id', (request, response) => {
  const { id } = request.params

  console.log(id) // 1

  // Seu código

  return response.json(/* Seu retorno em JSON */)
})

app.listen(3333)
```

---

## Query Params

### Como passar em rotas HTTP

```js
'https://suaApi.com/users?user=usuario&type=tipo'
```

### Funcionalidade

Os query params são parâmetros que não são obrigatórios na rota, ou seja a rota não necessariamente depende destes parâmetros, eles são principalmente usados para fazer pesquisas.

### Como usar

```js
const express = require('express')

const app = express()

app.get('/users/', (request, response) => {
  const { user, type } = request.query

  console.log(user) // usuario
  console.log(type) // tipo

  // Seu código

  return response.json(/* Seu retorno em JSON */)
})

app.listen(3333)
```

---

## Body Params

### Funcionalidade

Os body params são parâmetros que não se passam diretamente na rota, eles são objetos complexos de informações, para usá-los é necessário uma ferramenta para fazer a requisição, seja por um script ou por um app como o <a href="https://insomnia.rest">Insomnia</a>.

### Exemplo de Body Param em JSON

```json
{
  "name": "usuario",
  "email": "usuario@email.com",
  "senha": "123",
  "tipo": "tipo"
}
```

### Como usar

```js
const express = require('express')

const app = express()

app.post('/users/:id', (request, response) => {
  const { name, email, senha, tipo } = request.params

  console.log(name) // usuario
  console.log(email) // usuario@email.com
  console.log(senha) // 123
  console.log(tipo) // tipo

  // Seu código

  return response.json(/* Seu retorno em JSON */)
})

app.listen(3333)
```