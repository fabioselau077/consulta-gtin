# Consulta GTIN v1.0.0
## Introdução
Como não tem nenhuma API pública para recuperar informações do produto pelo GTIN, criei essa API simples. <br>
A API utiliza web scrapy por trás que recupera algumas informações do produto. <br>

## Campos
Atualmente está recuperando o nome, NCM (Código e Descrição), CEST (Código e Descrição) e a imagem do produto. Todos esses campos são retornados caso a API consiga recuperar, se retornar uma string vazia, significa que não tem essa informação.

## Documentação
### URL Base
`$ curl -XGET https://consulta-gtin.herokuapp.com/{gtin}`

### Exemplos

#### Consulta GTIN sem CEST
```
$ curl --location --request GET 'https://consulta-gtin.herokuapp.com/7894900709841'
Response:
{
  "nome": "REFRIGERANTE COCA COLA LATA",
  "imagem": "https://consulta-gtin.herokuapp.com/imagem/7894900709841",
  "ncm": {
    "codigo": "22021000",
    "descricao": "Agua incl.mineral/gaseif.adicion.acucar, aromatizada,etc",
    "completo": "22021000 - Agua incl.mineral/gaseif.adicion.acucar, aromatizada,etc"
  },
  "cest": {
    "codigo": "",
    "descricao": "",
    "completo": ""
  }
}
```
#### Consulta GTIN com CEST
```
$ curl --location --request GET 'https://consulta-gtin.herokuapp.com/7894900709841'
Response:
{
  "nome": "HASTE CARTUCHO JOHNSON JOHNSON C/150 UNIT",
  "imagem": "https://consulta-gtin.herokuapp.com/imagem/7891010560812",
  "ncm": {
    "codigo": "56012190",
    "descricao": "Outros artigos de pastas (ouates) de algodao",
    "completo": "56012190 - Outros artigos de pastas (ouates) de algodao"
  },
  "cest": {
    "codigo": "2005100",
    "descricao": "Hastes flexíveis (uso não medicinal)",
    "completo": "2005100 - Hastes flexíveis (uso não medicinal)"
  }
}
```
#### Recuperar Imagem
`$ curl -XGET https://consulta-gtin.herokuapp.com/imagem/{gtin}`
```
$ curl --location --request GET 'https://consulta-gtin.herokuapp.com/imagem/7894900709841'
Response:
  ***Foto do Produto ou uma Foto em Branco (caso não tenha)***

```

## TODO
- [x] Recuperando NCM
- [x] Recuperando CEST
- [x] Recuperando Imagem
- [ ] Recuperando Dados Fiscais

## Suporte
Para suporte basta criar uma Issue.

## Se isso te ajudou...
Considera-se a uma doação. As doações são utilizadas para pagar o plano Hobby do Heroku ($7). <br>
[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/fabioselau)

