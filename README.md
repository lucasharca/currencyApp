# CurrencyApp

API para conversão de moedas desenvolvida com NodeJS me Typescript para o desafio do Hurb.

## Tecnologias utilizadas

- Ambiente em Docker
- NodeJs
- Express
- Axios
- Redis
- IORedis(ORM)

## Iniciando a aplicação
Para roda a aplicação será necessário possuir Docker e Docker-compose.
` cd $pasta-da-aplicação`
` docker-compose build --no-cache`
` docker-compose up -d`

A aplicação estará disponível em `http://localhost:3333`

Endpoint para conversão: `http://localhost:3333/currency/convert`

Endpoint para criação de moeda: `http://localhost:3333/currency/create`

Endpoint para remoção de moeda: `http://localhost:3333/currency/remove`

Endpoint para valor de uma moeda comparada ao dolar: `http://localhost:3333/currency/recover`

Endpoint para atualizar o banco de dados com cotação mais recente: `http://localhost:3333/currency/fetch`

## Moedas disponíveis
A API, originalmente, converte entre as seguintes moedas:

- USD: Dólar americano
- BRL: Real brasileiro
- EUR: Euro
- BTC: Bitcoin
- ETH: Ethereum

Ex: USD para BRL, USD para BTC, ETH para BRL, etc...

Novas moedas podem ser adicionadas utilizando o endpoint `http://localhost:3333/currency/create`

Ex: `http://localhost:3333/currency/create?name=AUD&value=0.6771`

Onde `name` é o nome da moeda que será adicionada e `value` é o valor dela comparada ao dólar americano onde 1 dólar equivale a moeda a ser adicionada

Caso um valor não seja informado ele buscará em uma API externa pela moeda correspondente e seu valor cotado se disponível.

## Remoção de Moedas

O endpoint para remover moedas do banco de dados é `http://localhost:3333/currency/remove`
passando o nome da moeda que será removida.

EX: `http://localhost:3333/currency/remove?name=AUD`

## Busca de moeda

É possível buscar uma moeda específica no bando de dados e exibir o seu valor comparado com o dólar americano

EX: `http://localhost:3333/currency/recover?currency=BRL`

## Conversão de moedas

O endpoint de conversão é `http://localhost:3333/currency/convert`

A requisição recebe como parâmetros:

A moeda de origem: `from` ;

A moeda final: `to` ;

o valor a ser convertido: `amount` ;

Ex: `http://localhost:3333/currency/convert?from=BRL&to=USD&amount=123.45`

