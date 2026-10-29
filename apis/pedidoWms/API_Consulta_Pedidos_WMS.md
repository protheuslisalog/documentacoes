# API — Consulta de Pedidos WMS

## 1. Objetivo

Permite consultar detalhes dos pedidos registrados no sistema do cliente. A resposta contém a lista `items` e o campo `hasNext`, que indica se há mais registros/páginas.

## 2. Endpoint

- **Método:** `GET`
- **Caminho:** `/rest/wms/v2/pedidoWms/query`
- **Autenticação:** HTTP Basic
- **Header:** `tenantId: {empresa}, {filial}`
- **Header:** `x-id-cliente: {id_cliente}`


## 3. Autenticação e contexto

- `empresa`: código da empresa; o documento informa `03`.
- `filial`: código da filial Lisalog.
- `senha` e `chave`: também são enviados como parâmetros de consulta.
- `tenantId`: contexto de empresa e filial, no formato informado na documentação.

## 4. Parâmetros

| Parâmetro | Local | Obrigatório | Exemplo | Descrição |
|---|---|---:|---|---|
| `senha` | Query | Sim | `********` | Senha utilizada na requisição. |
| `chave` | Query | Sim | `********` | Chave utilizada na requisição. |
| `dataDe` | Query | Não | `20260801` | Data inicial no formato `AAAAMMDD`. |
| `dataAte` | Query | Não | `20260821` | Data final no formato `AAAAMMDD`. |
| `status` | Query | Não | `1` | Código do status para filtrar pedidos. |
| `pedido` | Query | Não | `3254698` | Número de um pedido específico. |
| `page` | Query | Sim | `1` | Número da página. |
| `pageSize` | Query | Sim | `1000` | Registros por página; máximo documentado: `3000`. |

`20260812` representa 12/08/2026.

## 5. Status dos pedidos

| Código | Descrição |
|---:|---|
| `1` | A SEPARAR |
| `3` | A CONFERIR |
| `4` | CONFERIDO |
| `5` | A EXPEDIR |
| `6` | FINALIZADO |
| `7` | CANCELADO |

## 6. Exemplo de requisição

```http
GET {{host}}/rest/wms/v2/pedidoWms/query?senha={{senha}}&chave={{chave}}&dataDe=20260801&dataAte=20260821&status=1&pedido=&page=1&pageSize=1000
Authorization: Basic {{senhaAutenticacao}}
tenantId: 03, {{filial}}
Accept: application/json
```

## 7. Exemplo de resposta

```json
{
  "items": [
    {
      "pedidoCliente": "4074405V3",
      "pedido": "U06538",
      "nota": "",
      "status": "1",
      "campanha": "TESTE.COM",
      "transportadora": "LOGISTICA LTDA.",
      "cnpjTransportadora": "",
      "dataHoraIntegracao": "",
      "dataHoraPedido": "20260804 11:17",
      "dataRomaneio": "",
      "dataHoraFinalizado": ""
    },
    {
      "pedidoCliente": "4074406V3",
      "pedido": "U06539",
      "nota": "",
      "status": "1",
      "campanha": "TESTE.COM",
      "transportadora": "COURIER S.A",
      "cnpjTransportadora": "",
      "dataHoraIntegracao": "",
      "dataHoraPedido": "20260804 11:17",
      "dataRomaneio": "",
      "dataHoraFinalizado": ""
    }
  ],
  "hasNext": true
}
```

## 8. Estrutura da resposta

| Campo | Tipo | Descrição |
|---|---|---|
| `items` | Array | Lista de pedidos retornados. |
| `items.pedidoCliente` | String | Identificador do pedido informado pelo cliente. |
| `items.pedido` | String | Número do pedido no sistema. |
| `items.nota` | String | Nota fiscal; pode vir vazia quando não houver nota. |
| `items.status` | String | Status atual do pedido. |
| `items.campanha` | String | Campanha associada ao pedido. |
| `items.transportadora` | String | Nome da transportadora. |
| `items.cnpjTransportadora` | String | CNPJ da transportadora. |
| `items.dataHoraIntegracao` | String | Data/hora da integração. |
| `items.dataHoraPedido` | String | Data/hora do pedido, formato `YYYYMMDD HH:mm`. |
| `items.dataRomaneio` | String | Data de geração do romaneio; pode vir vazia. |
| `items.dataHoraFinalizado` | String | Data/hora da finalização; pode vir vazia. |
| `hasNext` | Boolean | `true` se existem mais páginas; `false` caso contrário. |

Os campos opcionais podem ser retornados como strings vazias nos exemplos de origem.

## 9. Paginação

Informe `page` e `pageSize`. O máximo permitido para `pageSize` é 3000. Consulte `hasNext` para verificar se há mais páginas.

## 10. Variáveis

| Variável | Descrição |
|---|---|
| `{{host}}` | Endereço do servidor. |
| `{{empresa}}` | Código da empresa `03`. |
| `{{filial}}` | Código da filial Lisalog. |
| `{{senha}}` | Senha de acesso ao endpoint. |
| `{{chave}}` | Chave de acesso ao endpoint. |
| `{{senhaAutenticacao}}` | Senha para autenticação Basic. |