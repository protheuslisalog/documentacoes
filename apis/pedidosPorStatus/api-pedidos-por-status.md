# API — Consulta de Pedidos por Status

**Lisa — Logística Integrada Sulamericana**

## Sumário

1. [Objetivo](#1-objetivo)
2. [Endpoint](#2-endpoint)
3. [Parâmetros](#3-parâmetros)
4. [Exemplo de requisição](#4-exemplo-de-requisição)
5. [Retorno](#5-retorno)
6. [Estrutura da resposta](#6-estrutura-da-resposta)
7. [Status dos pedidos](#7-status-dos-pedidos)
8. [Exemplo de interpretação](#8-exemplo-de-interpretação)
9. [Exemplo de consumo](#9-exemplo-de-consumo)
10. [Detalhamento das variáveis](#10-detalhamento-das-variáveis)

---

## 1. Objetivo

A API **Pedidos por Status** permite consultar a quantidade de pedidos de um cliente, agrupados por status, considerando uma determinada data de pedido.

O retorno apresenta:

- Status do pedido;
- Descrição do status;
- Quantidade de pedidos em cada status;
- Cliente;
- Loja;
- Data do pedido.

## 2. Endpoint

**Consulta de pedidos por status**

| Item | Valor |
|---|---|
| **Método** | `GET` |
| **URL** | `{{host}}/rest/wms/v2/pedidosPorStatus/query` |
| **Autenticação** | Basic — `Authorization: Basic {{senhaAutenticacao}}` |
| **Header** | `tenantId: {{empresa}}, {{filial}}` |
| **Header** | `x-id-cliente: {id_cliente}` |

## 3. Parâmetros

Parâmetros de query string:

| Parâmetro | Obrigatório | Tipo | Exemplo | Descrição |
|---|---|---|---|---|
| `senha` | Sim | string | `XXXXXXXX` | Senha utilizada na requisição |
| `chave` | Sim | string | `XXXXXXXX` | Chave utilizada na requisição |
| `dataPedido` | Não | string | `20260812` | Data utilizada para consulta dos pedidos, no formato `AAAAMMDD`. Caso não informado, será apresentada a posição atual de todos os pedidos, independente da data. |

### Formato de `dataPedido`

O parâmetro deve ser informado no formato `AAAAMMDD`.

Exemplo: `20260812` representa `12/08/2026`.

## 4. Exemplo de requisição

```http
GET {{host}}/rest/wms/v2/pedidosPorStatus/query?senha={{senha}}&chave={{chave}}&dataPedido=20260812
Authorization: Basic {{senhaAutenticacao}}
tenantId: {{empresa}}, {{filial}}
```

## 5. Retorno

A API retorna um objeto JSON contendo a lista de status e suas respectivas quantidades.

```json
{
  "items": [
    { "status": "1", "descricaoStatus": "A SEPARAR", "quantidade": 1 },
    { "status": "3", "descricaoStatus": "A CONFERIR", "quantidade": 172 },
    { "status": "4", "descricaoStatus": "CONFERIDO", "quantidade": 106 },
    { "status": "5", "descricaoStatus": "A EXPEDIR", "quantidade": 2433 },
    { "status": "6", "descricaoStatus": "FINALIZADO", "quantidade": 561366 },
    { "status": "7", "descricaoStatus": "CANCELADO", "quantidade": 199 }
  ],
  "cliente": "XXXXXX",
  "loja": "XX",
  "dataPedido": ""
}
```

## 6. Estrutura da resposta

### Objeto principal

| Campo | Tipo | Descrição |
|---|---|---|
| `items` | Array | Lista dos status encontrados na consulta |
| `cliente` | String | Código do cliente |
| `loja` | String | Código da loja do cliente |
| `dataPedido` | String | Data do pedido retornada pela API |

### Item de `items`

| Campo | Tipo | Descrição |
|---|---|---|
| `status` | String | Código do status do pedido |
| `descricaoStatus` | String | Descrição do status |
| `quantidade` | Integer | Quantidade de pedidos naquele status |

## 7. Status dos pedidos

Com base no retorno apresentado:

| Código | Descrição | Exemplo |
|---|---|---|
| 1 | A SEPARAR | 1 |
| 3 | A CONFERIR | 172 |
| 4 | CONFERIDO | 106 |
| 5 | A EXPEDIR | 2.433 |
| 6 | FINALIZADO | 561.366 |
| 7 | CANCELADO | 199 |


## 8. Exemplo de interpretação

Considerando o retorno:

```json
{
  "status": "3",
  "descricaoStatus": "A CONFERIR",
  "quantidade": 172
}
```

Interpretação: existem **172 pedidos** classificados com o status **A CONFERIR**.

Da mesma forma:

```json
{
  "status": "5",
  "descricaoStatus": "A EXPEDIR",
  "quantidade": 2433
}
```

Significa: existem **2.433 pedidos** classificados como **A EXPEDIR**.

## 9. Exemplo de consumo

**Requisição**

```http
GET {{host}}/rest/wms/v2/pedidosPorStatus/query?senha={{senha}}&chave={{chave}}&dataPedido=20260812
```

**Resposta**

```json
{
  "items": [
    { "status": "1", "descricaoStatus": "A SEPARAR", "quantidade": 1 },
    { "status": "3", "descricaoStatus": "A CONFERIR", "quantidade": 172 },
    { "status": "4", "descricaoStatus": "CONFERIDO", "quantidade": 106 },
    { "status": "5", "descricaoStatus": "A EXPEDIR", "quantidade": 2433 },
    { "status": "6", "descricaoStatus": "FINALIZADO", "quantidade": 561366 },
    { "status": "7", "descricaoStatus": "CANCELADO", "quantidade": 199 }
  ],
  "cliente": "XXXXXX",
  "loja": "XX",
  "dataPedido": ""
}
```

## 10. Detalhamento das variáveis

| Variável | Descrição |
|---|---|
| `{{empresa}}` | Código da empresa (utilizar `03`) |
| `{{filial}}` | Código da filial Lisalog |
| `{{host}}` | Endereço host do servidor |
| `{{senha}}` | Senha de acesso ao endpoint |
| `{{chave}}` | Chave de acesso ao endpoint |
| `{{senhaAutenticacao}}` | Senha de autenticação da API |
