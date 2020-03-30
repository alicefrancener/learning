# Começando um projeto Node.js com Express

## Configurar ambiente

- Instalar node
- Criar diretório para projeto
- Iniciar projeto `npm init` e inserir informações do projeto => gera arquivo `package.json`

## Instalar `express` e iniciar servidor

- Instalar `express` com `npm install express`
- Criar arquivo `index.js` e insirer para executar o servidor
- Em `index.js` inserir (abaixo) para criar app e iniciar servidor:

```javascript
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => res.send('Hello World!'))

app.listen(port, () => console.log(`Example app listening on port ${port}!`))
```

- Iniciar servidor com comando `node index.js`
- Testar se servidor está funcionando em **localhost:3000** no navegador ou com comando `netstat -a`

## Roteamento

Roteamento se refere a como uma aplicação responde à uma requisição de um cliente para um endpoint (URI) e a um método de requisição HTTP (GET, POST, PUT, DELETE).

A definição de uma rota segue a estrutura: `app.METHOD(PATH, HANDLER)`

- `app` é uma instância do express
- METHOD é um método de requisição HTTP
- PATH é um path no servidor
- HANDLER é uma função executada para a rota definida

Exemplo:

```javascript
app.post('/', function (req, res) {
  res.send('Got a POST request')
})
```

## Usando `nodemon` 

- Nodemon: is a tool that helps develop node.js based applications by automatically restarting the node application when file changes in the directory are detected.
- `npm install --save-dev nodemon`
- Inserir no `package.json` o seguinte script `"start": "nodemon index.js"` para inicializar servidor com comando `npm start`

*** 

https://cursos.alura.com.br/course/node-rest-api
http://expressjs.com/en/starter/installing.html
http://expressjs.com/en/starter/hello-world.html
http://expressjs.com/en/starter/basic-routing.html