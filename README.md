# Challenge Bravo
> projeto de um webservice em FastApi

[![Python Version][python-image]][python-url]
![Coverage][mongodb-image]
[![FastApi][fastapi-image]][fastApi-url]
![Coverage][coverage-image]

Criado em Python e junto ao framework FastApi e utilizando o banco de dados MongoDB
## Pacotes

Segue a lista de pacotes utilizados no projeto.

Package                                      | Version  |
---------------------------------------------| ---------|
[FastApi][fastApi-url]                       | 0.109.2  |
[Uvicorn][uvicorn-url]                       | 0.27.1   |
[Pydantic][pydantic-url]                     | 2.6.1    |
[Httpx][httpxl-url]                          | 0.26.0   |
[Pymongo][pymongo-url]                       | 4.6.1    |
[Redis][redis-url]                           | 5.0.3    |


## Intuito do projeto:

O produto criado foi feito como desafio proposto pela empresa Hurb.
A ideia é poder fazer conversões de moedas, como também poder criar
novas, deletar, atualizar e fazer conversões com moedas já utilizadas.

## Casos de Uso:
Utilizamos o <b>dolar como `moeda de lastro`</b>, logo novas moedas deveram especificar o seu valor em relação ao dolar em sua criação.

### Para fazermos uma conversão:
- Chamamos o endpoint `/api/v1/currency` com os seguintes [query-parameters](https://en.wikipedia.org/wiki/Query_string "query-parameters")
```json
{
	"from": "USD",  // Dessa moeda
    "to": "BRA",    // coverta pra essa moeda
    "amount":100    // Esse valor
}
```

### Para criarmos uma moeda precisamos:
- Passar os seguintes valores no body do endpoint: `[POST]/api/v1/currency/{acronym-desejado}`
```json
{
	"acronym": "string",
	"name": "string",
	"dolar_price_reference": 5
    // valor com referencia ao dolar, como explicado acima.
}
```

### Para atualizarmos uma moeda precisamos:
- Passar os seguintes valores no body do endpoint: `[PUT] /api/v1/currency/{acronym-desejado}`
```json
{
    "acronym": "new-value",
	"updated_at": "29/05/2024, 17:10:21",
	"name": "new-currency",
	"dolar_price_reference": 5
    // valor com referencia ao dolar, como explicado acima.
}
```

### Para deletarmos uma moeda precisamos:
- chamar o endpoint: `[DELETE] /api/v1/currency/{acronym-desejado}`


## Instalação:

### Etapas para uso em desenvolvimento:
1. Com seu ambiente python, instale a lista de pacotes.
```sh
pip install -r requeriments-dev.txt
```
2. Após ter instalado as bibliotecas necessarias utilize do comando:
```sh
docker compose up
```
3. Com isso o projeto já estará funcionando.

4. <b>(Optional)</b> Caso não queira subir com docker compose é possivel utilizar o comando:
```sh
uvicorn app.main:app
```
Isso fará com que o banco de dados utilizado não seja instanciado mas possibilitando o funcionamento do projeto.


# <img src="https://avatars1.githubusercontent.com/u/7063040?v=4&s=200.jpg" alt="Hurb" width="24" /><a href="https://github.com/hurbcom/challenge-bravo">O Desafio Challenge-Bravo Pode ser encontrada aqui.</a>

<!-- Markdown link & img dfn's -->
[python-image]: https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54
[python-url]: https://www.python.org/
[fastApi-image]: https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi
[mongodb-image]: https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white
[fastApi-url]: https://fastapi.tiangolo.com/
[uvicorn-url]: https://www.uvicorn.org/
[pydantic-url]: https://docs.pydantic.dev/latest/
[httpxl-url]: https://www.python-httpx.org/
[pymongo-url]: https://www.mongodb.com/docs/drivers/pymongo/
[redis-url]: https://github.com/redis/redis-py
[fastapi-image]: https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi
[coverage-image]: https://coverage-badge.samuelcolvin.workers.dev/tiangolo/fastapi.svg
