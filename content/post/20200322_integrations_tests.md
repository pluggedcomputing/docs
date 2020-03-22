---
title: Como construir testes de integração no backend Node.JS
date: 2020-03-22
---
> Jest + Supertest a combinação perfeita para testes de integração

## Pré requsiitos
Neste post iremos focar exclusivamente da configuração, escrita e execução dos testes automatizados. Por tando, assumimos aqui que você tem os conhecimentos basicos necessarios para construir uma aplicação em Node.js.

Para fins didaticos, mostramos aqui como estruturamos o nosso projeto de exemplo:

```javascript
| __tests__       // Diretorio onde os testes serão escritos
└─── integrations
└─── setup.js 
| src
└─── controllers  // Funções da controllers do express route
└─── models       // Modelos do banco de dados
└─── services     // Regras de negócio
└─── routes.js    // Definição de rotas express
└─── server.js    // Server para iniciar o app
| package.json
```

## Configurando o JEST

O [Jest](https://jestjs.io/pt-BR/) é um poderoso Framework de Testes em JavaScript, mantido pelo Facebook Inc. com um foco na simplicidade. Funciona com projetos usando: Babel, TypeScript, Node, React, Angular, Vue e muito mais!

### 1. Instalação

Instale Jest usando [yarn](https://yarnpkg.com/):

`> yarn add --dev jest`

Ou [npm](https://www.npmjs.com/):

`> npm install --save-dev jest`

### 2. Gerando um arquivo de configuração básico

Com base no seu projeto, o Jest fará algumas perguntas e criará um arquivo de configuração básico com uma breve descrição para cada opção:

`> jest --init`

Perceba que será criado um arquivo na raiz do seu projeto chamado **jest.config.js**

Dentro desse arquivo existem varias opções de configuração para o Jest. Caso deseje, você pode consultar a [documentação completa](https://jestjs.io/docs/en/configuration).

No entando, vamos destacar algumas opções que consideramos importantes.

**Campo**   | **Descrição**
--------- | ------
bail | Para a execução após uma falha
collectCoverage | Indica se a cobertura deve ser coletada durante e execução
collectCoverageFrom | Indica os arquivos devem ser coletados as informações de cobertura. Indicamos que o valor seja:  `['**/*.{js,jsx}']` // todos os arquivos .js ou .jsx
coverageDirectory | Indica o diretorio onde os arquivos exportados pela coleta da cobertura durante a execução vão ser exportados. Indicamos que o valor seja: `__tests__/coverage`
testEnvironment | O ambiente que vai ser usando nos testes. No nosso caso: `node`
testMatch | O padrão que o Jest usa para detectar arquivos de teste. No nosso caso: `['**/__tests__/**/*.test.js?(x)']` // Todos os arquivos com extensão `.test.js` dentro da pasta `__tests__`
setupFilesAfterEnv | Caminho para os módulos que executam algum código para configurar a estrutura de teste antes de cada teste. No nosso caso: `['./__tests__/setup.js']`

> Lembrando que as configurações são totalmente personalizadas de acordo com cada projeto. 

### 3. Configurando script de testes

Adicione a seguinte seção ao seu **package.json**:
``` javascript
{
  "scripts": {
    "test": "jest"
  }
}
```
> Você tambem pode adicionar algumas opções de execução atraves do [Jest CLI Options](https://jestjs.io/docs/en/cli.html)

## Construindo os Testes

### Configurando ambiente de testes

Antes de tudo é importante informar que em nosso projeto estamos utilizando o MongoDB, um banco de dados NoSQL atravez da biblioteca [mongoose]().

De modo geral os testes são executados em ambientes e com banco de dados separados para não interferir na aplicação em produção.

Aqui nos apenas criamos banco de dados diferentes de acordo com o ambiente. Deste modo, definimos as seguintes variaveis de ambeinte:
```
DB_PROD=mongodb+srv://<user>:<password>@develop-ey1lp.mongodb.net/production?retryWrites=true&w=majority

DB_TEST=mongodb+srv://<user>:<password>@develop-ey1lp.mongodb.net/test?retryWrites=true&w=majority
```
que são utilizadas no nosso arquivo de configuração de modo que se a variavel `NODE_ENV` for igual a **'test'** usaremos o banco de testes, caso contrario, usaremos o banco de produção.

```javascript
require('dotenv').config()

let PORT = process.env.PORT || 3000
let MONGODB_URI = process.env.DB_PROD

if (process.env.NODE_ENV === 'test') {
  MONGODB_URI = process.env.DB_TEST
}

module.exports = {
  MONGODB_URI,
  PORT
}
```

> Em alguns casos ainda é recomendavel adicionar um banco de dados para desenvolvimento.

### Setup e Teardown

Muitas vezes, ao escrever testes, você tem algum trabalho de configuração que precisa ocorrer antes da execução dos testes, e você tem algum trabalho de conclusão que precisa acontecer após a execução dos testes. O Jest fornece funções auxiliares para lidar com isso.

Se você tem algum trabalho que precisa fazer repetidamente para muitos testes, pode usar `beforeEach` e `afterEach`.

Se você só precisa fazer a instalação uma vez, no início de um arquivo. O Jest fornece `beforeAll` e `afterAll` para lidar com esta situação.

Agora vamos configurar o nosso `setup.js`

```javascript
const { server, mongoose } = require('../src/server');

beforeAll(async () => {
  await mongoose.connection.dropDatabase();
  console.log('... Test Started');
});

afterAll(async () => {
  await mongoose.disconnect();
  await server.close();
  console.log('... Test Ended');
});
```

Perceba que logo no começo do arquivo importamos as instancias do `server` e do `mongoose` direto do arquivo `server.js`. Para isso, em seu `server.js` você deve usar:

`module.export = {server, mongoose, app}`

> Isso é importante pois caso você use outras instancias de `server` e `mongoose` o Jest não vai encerrar corretamente as instancias da execução no metodo `afterAll` e vai apresentar o erro: `Jest did not exit one second after the test run has completed.`

no metodo `beforeAll` apenas nos certificamos de limpar toda a base de dados para que não ocorram interferencias nos testes.
> Se você preferir limpar a base de dados a cada testes, use `beforeEach`

Já no metodo `afterAll`, desconectamos a instancia do mongoose e fechamos a instancia do server. 

### Escrevendo os Testes

Para construir nossos testes, vamos utilizar o [SuperTest](https://github.com/visionmedia/supertest), uma biblioteca que fornece uma abstração de alto nível para testar requisições HTTP.

1. Instale o SuperTest

Execute um dos comandos abaixo:  
`> yarn add supertest -D`  
`> npm install supertest --save-dev`

2. Crie o seu arquivo de testes

dentro da pasta `__tests__/integrations`, crie um arquivo `api.test.js`
> A medida que o seu projeto cresce, considere criar arquivos diferentes, seprados por endpoint ou por controller...

3. importe o SuperTest

```javascript
const supertest = require('supertest');
const { app } = require('../../src/server');
const request = supertest(app);
```
4. Entendendo a estrutura dos testes

Usamos `describe` para criar um agrupamento de testes.  
Usamos `it` para criar um caso de teste.  
Usamos `async` e `await` para tratar as execuções assíncronas. [Veja mais](https://jestjs.io/docs/en/tutorial-async).  
Usamos `request.<HTTP_METHOD>('/endpoint')` para acessar os endpoint do nosso servidor com supertest.  
Guardamos a resposta da socicitação ao nosso servidor na constante `response`.  
Usamos `expect` para verificar se os valores atendem a certas condições.  [Veja mais](https://jestjs.io/docs/en/expect). 
Usamos `toBe` como nosso **Matcher** em complemento ao `expect` para testar valores de maneiras diferentes. [Veja mais](https://jestjs.io/docs/en/using-matchers). 

5. Crie os seus testes

Vamos expor aqui alguns exemplos de testes que utilizamos. Para consultar mais exemplos veja a [documentação](https://github.com/visionmedia/supertest).

```javascript
describe('Testando a rota: POST - /question', () => {
    it('Verifica a criação de uma questão do tipo MULTIPLECHOICE', async () => {
      const body = {
          statement: 'statement',
          type: 'MULTIPLECHOICE',
          level: 1,
          tips: 'tips',
          alternatives: [
            {
              text: "text",
              correct: false
            }, 
            {
               text: "text",
               correct: false
            }, 
            {
                text: "text",
                correct: false
            }, {
                text: "text",
                correct: true
            }]
        }
        const response = await request.post('/question').send(body));
        expect(response.statusCode).toBe(201);
    });

```
No caso acima, apenas enviamos uma requisição para o endpoint **'/question'** no metodo **POST** e verifica se o status retornado foi **201**.

Você pode mudar o metodo, o endpoint e o corpo da requisição tranquilamente para se adaptar ao seu contexto. Como por exemplo: 

```javascript
describe('Testando a rota: GET - /question', () => {
  beforeAll(async () => {
    const body = {
          statement: 'statement',
          type: 'MULTIPLECHOICE',
          level: 1,
          tips: 'tips',
          alternatives: [
            {
              text: "text",
              correct: false
            }, 
            {
               text: "text",
               correct: false
            }, 
            {
                text: "text",
                correct: false
            }, {
                text: "text",
                correct: true
            }]
        }
        const response = await request.post('/question').send(body));
  });

  it('Verifica se a consulta retona status 200', async () => {
    const response = await request.get('/question').send();
    expect(response.statusCode).toBe(200);
  });
  it('Verifica se a consulta retona um objeto', async () => {
    const response = await request.get('/question').send();
    expect(response.body).toEqual(expect.any(Object));
  });
```
Perceba que dentro do `it` mudamos apenas o metodo (de **POST** para **GET**) a qual desejamos realizar a requisição.

No caso das requisições de consulta, é natual que você queira sempre criar um objeto antes para que o mesmo seja consultado depois. Nesse caso, usamos o  metodo `beforeEach`.

Podemos ver também que no segundo `it` não verificamos apenas o status da requisição e sim o valor retornado no seu corpo. As verificações com JEST são quase infinitas, seja critivo...

Outra possibilidade é que a sua API suporte o envio de arquivos, deta forma você pode usar:

```javascript
await request(app)
  .post('/')
  .attach('avatar', 'test/fixtures/avatar.jpg') // para arquivos
  .field('name', 'my awesome avatar') // para demais campos
  ...
```

## Executando os Testes

Com tudo isso feito, basicamnete precisamos apenas executar o comando `yarn test` ou `npm test`.

No entrando como nos estamos utilizando configurações de ambiente e banco de dados diferentes, precisamos fazer uma pequena mudança no `package.json` para adicionar a variavel `NODE_ENV=test`:

```javascript
  "scripts": {    
    "test": "NODE_ENV=test jest ",
    ...
  },
```

agora sim, basta executar o comando `yarn test` ou `npm test` e ver a magica acontecer.




