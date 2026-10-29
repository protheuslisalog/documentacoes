# Documentação das APIs WMS — Lisa / Lisalog

**Lisa — Logística Integrada Sulamericana**

Documentação unificada das APIs de integração com o WMS (Protheus/TOTVS).

## Sumário

1. [Visão geral](#1-visão-geral)
2. [Autenticação](#2-autenticação)
3. [Resumo dos endpoints](#3-resumo-dos-endpoints)
4. [Envio de pedidos para separação](#4-envio-de-pedidos-para-separação) — `POST /PEDIDOWMS`
5. [Atualização de dados do pedido](#5-atualização-de-dados-do-pedido) — `PUT /PEDIDOWMS`
6. [Cancelamento de pedido](#6-cancelamento-de-pedido) — `PUT /PEDIDOWMS`
7. [Consulta de status do pedido](#7-consulta-de-status-do-pedido) — `GET /WMSSTATUS`
8. [Consulta de status de pedidos por data](#8-consulta-de-status-de-pedidos-por-data) — `GET /RSSTSPG`
9. [Consulta de pedidos por status (quantidades)](#9-consulta-de-pedidos-por-status-quantidades) — `GET /wms/v2/pedidosPorStatus/query`
10. [Glossário de status](#10-glossário-de-status)
11. [Pontos de atenção na documentação original](#11-pontos-de-atenção-na-documentação-original)

---

## 1. Visão geral

| Item | Valor |
|---|---|
| Base URL (homologação) | `https://li195956.protheus.cloudtotvs.com.br:11257/rest` |
| Formato | JSON (`Content-Type: application/json`) |
| Ambiente de produção | Deve ser solicitado à Lisalog: IP, porta, usuário e senha |

Para as APIs de consulta (`WMSSTATUS`, `RSSTSPG`), os dados de **chave**, **senha** e **código da filial** devem ser solicitados ao coordenador do WMS.

## 2. Autenticação

Todas as APIs utilizam **Basic Authorization**:

```http
Authorization: Basic <base64(usuario:senha)>
```

### Credenciais do ambiente de homologação (conforme documentos originais)

| Campo | Valor |
|---|---|
| Usuário | `usrapiwmsteste` |
| Senha | `apiwms#245@` (ver observação no [item 11](#11-pontos-de-atenção-na-documentação-original) sobre maiúscula/minúscula) |

> ⚠️ Estas credenciais são de teste, mas estão em texto puro neste arquivo. Remova-as antes de compartilhar o documento externamente.

---

## 3. Resumo dos endpoints

| API | Método | Caminho | Finalidade |
|---|---|---|---|
| Separação de pedidos | `POST` | `/PEDIDOWMS` | Enviar pedidos para separação nos armazéns da Lisalog |
| Atualiza pedido | `PUT` | `/PEDIDOWMS` | Atualizar dados de um pedido (NF, DANFE, transportadora etc.) |
| Cancelamento de pedido | `PUT` | `/PEDIDOWMS` | Solicitar cancelamento de um pedido (`cstatus = "C"`) |
| Status do pedido | `GET` | `/WMSSTATUS` | Consultar o status de um pedido |
| Status de pedidos por data | `GET` | `/RSSTSPG` | Consultar status dos pedidos de uma data (paginado) |
| Pedidos por status | `GET` | `/wms/v2/pedidosPorStatus/query` | Quantidade de pedidos agrupados por status |

> `PUT /PEDIDOWMS` atende duas operações (atualização e cancelamento). A API distingue pelo conteúdo: no cancelamento envia-se `"cstatus": "C"`.

---

## 4. Envio de pedidos para separação

**Objetivo:** enviar pedidos e suas informações para separação nos armazéns da Lisalog.

- **Método:** `POST`
- **URL:** `{{host}}/rest/PEDIDOWMS`
- **Header:** `Content-Type: application/json`

### 4.1 Exemplo de JSON

```json
{
  "ccodfilial": "01",
  "ccgc": "71586952000157",
  "cpedido": "1234",
  "cenderecodestino": "RUA COPPINI",
  "cbairrodestino": "CENTRO",
  "ccidadedestino": "SAO PAULO",
  "cestadodestino": "SP",
  "ccomplementodestino": "CASA 2",
  "cnomedestino": "JOAO",
  "ccpfcnpjdestino": "35478258067",
  "ccepdestino": "09341340",
  "cnumerodestino": "79",
  "ccontatodestino": "JOAO",
  "cfonedestino": "5511996899999",
  "stringxmlnfe": "",
  "cnota": "1111",
  "cserie": "1",
  "ccgctransportadora": "",
  "ccodigoservicocorreios": "",
  "carmazem": "",
  "curldanfe": "",
  "ccampanha": "",
  "nvalordeclarado": 0,
  "cdanfebase64": "",
  "cetiquetabase64": "",
  "campanhaObs": "",
  "cboletobase64": "",
  "ccartacorrecaobase64": "",
  "cguiast64": "",
  "ccomprovantepagamento64": "",
  "cpedidomarketplace": "",
  "cTransportadora": "",
  "nquantidadevolumes": 1,
  "cemaildestino": "",
  "nProtocolo": 12341251234,
  "cRastreio": "",
  "cPlp": "",
  "cNotaOriginal": "",
  "cSerieOriginal": "",
  "cCnpjFornecedor": "",
  "aitens": [
    {
      "citempedido": "0001",
      "cproduto": "10650X",
      "ccodbarras": "",
      "cdescricao": "TELEFONE FIXO",
      "nqtd": 1,
      "nvalorunitario": 10.10,
      "clote": "",
      "npesokg": 0
    }
  ],
  "volumes": [
    {
      "codigoVolume": "X1",
      "descricaoVolume": "Descricao volume X1",
      "codigoBarras": "1234",
      "embalagemDoProduto": false,
      "altura": 1,
      "peso": 1,
      "largura": 1,
      "comprimento": 1,
      "produtos": [
        {
          "produto": "10650X",
          "quantidade": 1,
          "altura": 1,
          "largura": 1,
          "comprimento": 1
        }
      ]
    }
  ]
}
```

### 4.2 Campos do pedido

**Legenda — obrigatoriedade**

- **Conteúdo:** o campo precisa vir preenchido.
- **Estrutura:** a chave precisa existir no JSON (mesmo vazia).
- **Cond.:** *Não; passa a ser obrigatório se o cliente (código e loja) estiver habilitado no parâmetro `MV_XCVLDCV`.*

| Campo | Tipo | Conteúdo | Estrutura | Descrição |
|---|---|---|---|---|
| `ccodfilial` | Texto | Sim | Sim | Filial Lisalog onde deve ser separado o pedido |
| `ccgc` | Texto | Sim | Sim | CNPJ do emitente do pedido |
| `cpedido` | Texto | Sim | Sim | Número do pedido |
| `cenderecodestino` | Texto | Não | Sim | Endereço de entrega do pedido |
| `cbairrodestino` | Texto | Não | Sim | Bairro de entrega do pedido |
| `ccidadedestino` | Texto | Não | Sim | Município de entrega do pedido |
| `cestadodestino` | Texto | Não | Sim | Estado (UF) de entrega do pedido |
| `ccomplementodestino` | Texto | Não | Sim | Complemento do endereço de entrega |
| `cnomedestino` | Texto | Não | Sim | Nome do cliente de entrega |
| `ccpfcnpjdestino` | Texto | Não | Sim | CPF ou CNPJ do cliente de entrega |
| `ccepdestino` | Texto | Não | Sim | CEP de entrega do pedido |
| `cnumerodestino` | Texto | Não | Sim | Número do endereço de entrega |
| `ccontatodestino` | Texto | Não | Sim | Nome do contato de entrega do pedido |
| `cfonedestino` | Texto | Não | Sim | Telefone de contato do destinatário |
| `cemaildestino` | Texto | Não | Não | E-mail do destinatário do pedido |
| `ccodigopedido` | Texto | Não | Não | Código ID do pedido nas plataformas de marketplace |
| `stringxmlnfe` | Texto | Cond. | Sim | String com o XML da NF-e |
| `cnota` | Texto | Cond. | Sim | Número da nota fiscal |
| `cserie` | Texto | Cond. | Sim | Série da nota fiscal |
| `ccgctransportadora` | Texto | Cond. | Sim | CNPJ da transportadora |
| `nquantidadevolumes` | Numérico | Não | Não | Quantidade de volumes do pedido |
| `ccodigoservicocorreios` | Texto | Não | Sim | Código do serviço dos Correios |
| `carmazem` | Texto | Não | Sim | Armazém de retirada do pedido. Enviar preenchido apenas em casos específicos (ex.: produtos com avaria, enviar `"AV"`) |
| `curldanfe` | Texto | Não | Não | URL para download da DANFE |
| `ccampanha` | Texto | Cond. | Cond. (estrutura) | Sigla da campanha |
| `campanhaObs` | Texto | Não | Não | *(sem descrição no documento original)* |
| `nvalordeclarado` | Numérico | Não | Não | Valor declarado do pedido (para finalidade de seguro) |
| `cdanfebase64` | Texto | Cond. | Cond. (estrutura) | Arquivo PDF da DANFE codificado em base64 |
| `cetiquetabase64` | Texto | Cond. | Cond. (estrutura) | Etiqueta de transporte em ZPL |
| `cboletobase64` | Texto | Não | Não | Boleto codificado em base64 |
| `ccartacorrecaobase64` | Texto | Não | Não | Carta de correção codificada em base64 |
| `cguiast64` | Texto | Não | Não | Guia de ST codificada em base64 |
| `ccomprovantepagamento64` | Texto | Não | Não | Comprovante de pagamento codificado em base64 |
| `cpedidomarketplace` | Texto | Não | Não | Número do pedido do marketplace |
| `cTransportadora` | Texto | Não | Não | Identificação da transportadora |
| `nProtocolo` | Numérico | Cond. | Cond. (estrutura) | Número do protocolo de autorização da NF-e |
| `cRastreio` | Texto | Não | Não | Código do rastreio na transportadora |
| `cPlp` | Texto | Não | Não | Código da PLP da transportadora |
| `cNotaOriginal` | Texto | Não | Não | Número da nota de entrada (saídas de devolução) |
| `cSerieOriginal` | Texto | Não | Não | Série da nota de entrada (saídas de devolução) |
| `cCnpjFornecedor` | Texto | Não | Não | CNPJ do emitente da nota de entrada (saídas de devolução) |
| `aitens` | Array | Sim | Sim | Produtos a serem separados |
| `volumes` | Array | Não | Não | Volumes a serem utilizados no pedido |

### 4.3 Campos de `aitens[]`

| Campo | Tipo | Conteúdo | Estrutura | Descrição |
|---|---|---|---|---|
| `citempedido` | Texto | Não | Sim | Código do item do pedido |
| `cproduto` | Texto | Sim | Sim | Código do produto |
| `ccodbarras` | Texto | Não | Sim | Código de barras do produto (EAN) |
| `cdescricao` | Texto | Sim | Sim | Descrição do produto |
| `nqtd` | Texto* | Sim | Sim | Quantidade do produto |
| `nvalorunitario` | Numérico | Sim | Sim | Valor unitário do produto |
| `clote` | Texto | Sim | Sim | Número do lote |
| `npesokg` | Numérico | Não | Sim | Peso unitário do produto, em quilos |
| `cNotaOriginal` | Texto | Não | Não | Número da nota de entrada (saídas de devolução) |
| `cSerieOriginal` | Texto | Não | Não | Série da nota de entrada (saídas de devolução) |
| `enderecoFisicoArmazem` | Texto | Não | Não | *(sem descrição no documento original)* |

\* A tabela original indica `Texto`, mas o exemplo envia número (`"nqtd": 1`). Veja o [item 11](#11-pontos-de-atenção-na-documentação-original).

### 4.4 Campos de `volumes[]`

| Campo | Tipo | Conteúdo | Estrutura | Descrição |
|---|---|---|---|---|
| `codigoVolume` | Texto | Sim | Sim | Código de identificação do volume. Cada embalagem diferente deve ter um código único, usado para identificar a embalagem a ser utilizada |
| `descricaoVolume` | Texto | Sim | Sim | Descrição do volume |
| `codigoBarras` | Texto | Não | Sim | Código de barras da embalagem (se houver código impresso na embalagem) |
| `embalagemDoProduto` | Lógico | Sim | Sim | Indica se deve ser usada a própria embalagem do produto na expedição, sem nova embalagem |
| `altura` | Numérico | Não | Sim | Altura total da embalagem, em **metros** |
| `largura` | Numérico | Não | Sim | Largura total da embalagem, em **metros** |
| `comprimento` | Numérico | Não | Sim | Comprimento total da embalagem, em **metros** |
| `peso` | Numérico | Não | Sim | Peso total do volume com os produtos, em **quilogramas** |
| `produtos` | Array | Não | Não | Produtos que devem ser alocados no volume |

### 4.5 Campos de `volumes[].produtos[]`

| Campo | Tipo | Conteúdo | Estrutura | Descrição |
|---|---|---|---|---|
| `produto` | Texto | Sim | Sim | Código do produto |
| `quantidade` | Numérico | Sim | Sim | Quantidade do produto |
| `altura` | Numérico | Não | Sim | Altura do produto |
| `largura` | Numérico | Não | Sim | Largura do produto |
| `comprimento` | Numérico | Não | Sim | Comprimento do produto |

### 4.6 Regras gerais

- Campos **não obrigatórios no conteúdo** e **obrigatórios na estrutura** não devem ser enviados como `null`. Se não houver conteúdo: texto → `""`; numérico → `0`.
- **Importante:** alguns campos não obrigatórios podem ser necessários para a separação, dependendo da operação. Antes de enviar um campo sem informação, valide com o time operacional da Lisalog se ele é necessário para o processo de separação.

---

## 5. Atualização de dados do pedido

Atualiza dados de um pedido já enviado.

- **Método:** `PUT`
- **URL (homologação):** `https://li195956.protheus.cloudtotvs.com.br:11257/rest/PEDIDOWMS`

### 5.1 Exemplo de JSON

```json
{
  "ccodfilial": "07",
  "ccgc": "71586952000257",
  "cpedido": "1234",
  "cnota": "1111",
  "cserie": "1",
  "cdanfebase64": "",
  "nvalordeclarado": 0,
  "stringxmlnfe": "",
  "ccgctransportadora": "",
  "curldanfe": "",
  "cboletobase64": "",
  "ccartacorrecaobase64": "",
  "curlguiaST": "",
  "ccomprovantepagamento64": "",
  "cetiquetabase64": "",
  "cRastreio": "",
  "ccampanha": "",
  "lalteraetiqueta": false,
  "cPlp": ""
}
```

> No documento original o exemplo traz `"lalteraetiqueta": False` (sintaxe Python). Em JSON válido o booleano é `false`.

### 5.2 Campos

**Identificação do pedido**

| Campo | Descrição |
|---|---|
| `ccodfilial` | Filial Lisa que irá expedir o pedido |
| `ccgc` | CNPJ do emitente do pedido |
| `cpedido` | Número do pedido |

**Campos que serão atualizados**

| Campo | Descrição |
|---|---|
| `cnota` | Número da nota fiscal |
| `cserie` | Série da nota fiscal |
| `cdanfebase64` | DANFE em PDF, codificada em base64 |
| `nvalordeclarado` | Valor declarado do pedido |
| `stringxmlnfe` | XML da nota fiscal |
| `ccgctransportadora` | CNPJ da transportadora que irá coletar o pedido |
| `curldanfe` | URL para download da DANFE em PDF |
| `cboletobase64` | Boleto em base64 |
| `ccartacorrecaobase64` | Carta de correção em base64 |
| `curlguiaST` | URL para download da guia de ST em PDF |
| `ccomprovantepagamento64` | Comprovante de pagamento em base64 |
| `cetiquetabase64` | Etiqueta de transporte no padrão ZPL |
| `cRastreio` | Código do rastreio na transportadora |
| `ccampanha` | Campanha do pedido |
| `lalteraetiqueta` | Inclui (`true`) ou não (`false`) uma etiqueta ao pedido |
| `cPlp` | Código da PLP da transportadora |

---

## 6. Cancelamento de pedido

Envia uma solicitação de cancelamento de pedido.

- **Método:** `PUT`
- **URL (homologação):** `https://li195956.protheus.cloudtotvs.com.br:11257/rest/PEDIDOWMS`

### 6.1 Exemplo de JSON

```json
{
  "ccodfilial": "07",
  "ccgc": "71586952000257",
  "cpedido": "1234",
  "cstatus": "C"
}
```

### 6.2 Campos

| Campo | Descrição |
|---|---|
| `ccodfilial` | Filial Lisa que irá expedir o pedido |
| `ccgc` | CNPJ do emitente do pedido |
| `cpedido` | Número do pedido |
| `cstatus` | Status do pedido — **enviar sempre a letra `"C"`** |

---

## 7. Consulta de status do pedido

- **Método:** `GET`
- **URL (homologação):** `https://li195956.protheus.cloudtotvs.com.br:11257/rest/WMSSTATUS`
- **Headers:** `Content-Type: application/json`, `Authorization: Basic ...`

### 7.1 Parâmetros (todos obrigatórios)

| Parâmetro | Descrição |
|---|---|
| `CHAVE` | Código identificador do cliente na Lisa |
| `FILIALLISA` | Filial da consulta |
| `SENHA` | Senha de acesso |
| `CGC` | CNPJ da empresa |
| `PEDIDO` | Código do pedido |

### 7.2 Exemplo de requisição

```http
GET https://li195956.protheus.cloudtotvs.com.br:11257/rest/WMSSTATUS?CHAVE=01719201&FILIALLISA=01&SENHA=1234&CGC=71586952000157&PEDIDO=19730380
```

### 7.3 Exemplo de resposta

```json
{
  "ASTATUS": [
    {
      "ASERIEMAI": [
        {
          "CIMEISERIE": "WSBC565425895",
          "CPRODUTO": "123546",
          "CPRODCLIENTE": "123456"
        }
      ],
      "AEMBALAGEM": [
        {
          "CCODIGO": "000008",
          "CDESCRICAO": "10X10X10",
          "NALTURA": 10,
          "NCOMPRIMENTO": 10,
          "NLARGURA": 10,
          "NQUANTIDADE": 1
        }
      ],
      "CCAMPANHA": "ITASH",
      "CPEDCLIENTE": "19730380",
      "CEMBALAGEM": "19730380",
      "CRASTREIO": "",
      "CROMANEIO": "",
      "DATAEXPEDIDO": "20220603",
      "DATAROMANEIO": "20220603",
      "HORAEXPEDIDO": "09:21",
      "LETIQUETAINTEGRADA": false,
      "NCUBAGEM": 0,
      "NPESOBRU": 0,
      "NPESOLIQ": 0,
      "NQTDCAIXA": 0,
      "NQTDPALLET": 0,
      "CPEDLISA": "SYBVRJ",
      "CSTATUS": "FINALIZADO"
    }
  ],
  "CCGC": "71586952000157",
  "CCHAVE": "01719201",
  "CFILIALWMS": "01",
  "CPEDIDO": "19730380"
}
```

### 7.4 Campos retornados

| Campo | Descrição |
|---|---|
| `CPEDIDO` | Código do pedido |
| `CCHAVE` | Chave de acesso utilizada |
| `CFILIALWMS` | Filial do pedido |
| `CCGC` | CNPJ da requisição |
| `CPEDCLIENTE` | Código do pedido solicitado |
| `CCAMPANHA` | Campanha informada para o pedido |
| `CPEDLISA` | Código do pedido Lisa |
| `CSTATUS` | Status do pedido (ver [glossário](#10-glossário-de-status)) |
| `CPRODUTO` | Código do produto na Lisa |
| `CIMEISERIE` | Número de série/IMEI |
| `CPRODCLIENTE` | Código do produto no cliente |
| `CEMBALAGEM` | Embalagem utilizada no pedido |
| `CRASTREIO` | Código do rastreio |
| `CROMANEIO` | Código do romaneio |
| `LETIQUETAINTEGRADA` | Indica se o pedido tem etiqueta integrada (`true`/`false`) |
| `NCUBAGEM` | Cubagem do pedido |
| `NPESOBRU` | Peso bruto do pedido |
| `NPESOLIQ` | Peso líquido do pedido |
| `NQTDCAIXA` | Quantidade de caixas |
| `NQTDPALLET` | Quantidade de pallets |
| `CCODIGO` | Código da embalagem |
| `CDESCRICAO` | Descrição da embalagem |
| `NALTURA` | Altura da embalagem, em centímetros |
| `NLARGURA` | Largura da embalagem, em centímetros |
| `NCOMPRIMENTO` | Comprimento da embalagem, em centímetros |
| `NQUANTIDADE` | Quantidade da embalagem |
| `DATAEXPEDIDO` | Data de expedição do pedido (`AAAAMMDD`) |
| `DATAROMANEIO` | Data da geração do romaneio (`AAAAMMDD`) |
| `HORAEXPEDIDO` | Hora da expedição do pedido (`HH:MM`) |

---

## 8. Consulta de status de pedidos por data

- **Método:** `GET`
- **URL (homologação):** `https://li195956.protheus.cloudtotvs.com.br:11257/rest/RSSTSPG`
- Retorna **100 pedidos por página**. Se a data possuir mais de 100 pedidos, faça novas chamadas com o parâmetro `PAGINA` para obter as demais páginas.

### 8.1 Parâmetros

| Parâmetro | Obrigatório | Descrição |
|---|---|---|
| `CHAVE` | Sim | Código identificador do cliente na Lisa |
| `FILIALLISA` | Sim | Filial da consulta |
| `SENHA` | Sim | Senha de acesso |
| `CGC` | Sim | CNPJ da empresa |
| `DATAPEDIDO` | Sim | Data para consulta do pedido (`AAAAMMDD`) |
| `PAGINA` | Não | Número da página |

### 8.2 Exemplo de requisição

```http
GET https://li195956.protheus.cloudtotvs.com.br:11257/rest/RSSTSPG?CGC=86646128000142&CHAVE=123456&FILIALLISA=07&SENHA=123456&DATAPEDIDO=20190529&PAGINA=1
```

### 8.3 Exemplo de resposta

```json
{
  "CDATAPEDIDO": "20260101",
  "LISTAPEDIDOS": [
    {
      "ASTATUS": [
        {
          "AEMBALAGEM": [],
          "ASERIIMEI": [
            {
              "CIMEISERIE": "",
              "CPRODCLIENTE": "Y-YP1269",
              "CPRODUTO": "YBEY-YP1269"
            }
          ],
          "CCAMPANHA": "LOJA INTERNA B2C",
          "CEMBALAGEM": "",
          "CPEDCLIENTE": "3619731",
          "CPEDLISA": "TBTRZ2",
          "CRASTREIO": "",
          "CROMANEIO": "314776",
          "CSTATUS": "FINALIZADO",
          "CURLTRACKING": "",
          "DATAEXPEDIDO": "20260221",
          "DATAROMANEIO": "20260221",
          "HORAEXPEDIDO": "18:10",
          "ITENS": [
            {
              "IDNOTAORIGEM": "",
              "ITEMNOTAORIGEM": "",
              "LOTE": "AUTO130181",
              "NOTA": "9AH3CM",
              "NOTAORIGEM": "",
              "PRODUTO": "Y-YP1269",
              "QUANTIDADE": 1,
              "SERIE": "W",
              "SERIEORIGEM": ""
            }
          ],
          "LETIQUETAINTEGRADA": true,
          "NCUBAGEM": 0,
          "NOTACLIENTE": "2845857",
          "NPESOBRU": 1,
          "NPESOLIQ": 1,
          "NQTDCAIXA": 1,
          "NQTDPALLET": 0
        }
      ],
      "CCGC": "35689522000127",
      "CCHAVE": "86280601",
      "CFILIALWMS": "01",
      "CPEDIDO": "3619731"
    }
  ],
  "PAGCORRENTE": 1,
  "PAGTOTAL": 1
}
```

> Os espaços em branco que aparecem em alguns valores do exemplo original (ex.: `"CPEDCLIENTE": "3619731      "`) foram removidos aqui para legibilidade. A API pode devolver campos texto com espaços à direita — vale aplicar `trim` no consumo.

### 8.4 Campos retornados

| Campo | Descrição |
|---|---|
| `CDATAPEDIDO` | Data dos pedidos (`AAAAMMDD`) |
| `PAGCORRENTE` | Página corrente |
| `PAGTOTAL` | Número total de páginas |
| `LISTAPEDIDOS[]` | Lista de pedidos da página |
| `CPEDIDO` | Código do pedido |
| `CCHAVE` | Chave de acesso utilizada |
| `CFILIALWMS` | Filial do pedido |
| `CCGC` | CNPJ da requisição |
| `ASTATUS[]` | Status/dados de expedição do pedido |
| `CPEDCLIENTE` | Código do pedido solicitado |
| `CPEDLISA` | Código do pedido Lisa |
| `CSTATUS` | Status do pedido (ver [glossário](#10-glossário-de-status)) |
| `CCAMPANHA` | Campanha informada para o pedido |
| `CPRODUTO` | Código do produto na Lisa |
| `CIMEISERIE` | Número de série/IMEI |
| `CPRODCLIENTE` | Código do produto no cliente |
| `LETIQUETAINTEGRADA` | Indica se o pedido tem etiqueta integrada (`true`/`false`) |
| `ITENS[]` | Itens do pedido: `PRODUTO`, `QUANTIDADE`, `LOTE`, `NOTA`, `SERIE`, `NOTAORIGEM`, `SERIEORIGEM`, `IDNOTAORIGEM`, `ITEMNOTAORIGEM` |

Os demais campos (`CEMBALAGEM`, `CRASTREIO`, `CROMANEIO`, `CURLTRACKING`, `DATAEXPEDIDO`, `DATAROMANEIO`, `HORAEXPEDIDO`, `NCUBAGEM`, `NOTACLIENTE`, `NPESOBRU`, `NPESOLIQ`, `NQTDCAIXA`, `NQTDPALLET`) aparecem no exemplo, mas sem descrição individual no documento original; seguem o mesmo significado descrito no [item 7.4](#74-campos-retornados).

---

## 9. Consulta de pedidos por status (quantidades)

Consulta a quantidade de pedidos de um cliente, agrupados por status, para uma determinada data de pedido.

- **Método:** `GET`
- **URL:** `{{host}}/rest/wms/v2/pedidosPorStatus/query`
- **Autenticação:** Basic — `Authorization: Basic {{senhaAutenticacao}}`
- **Header:** `tenantId: {{empresa}}, {{filial}}`

### 9.1 Parâmetros

| Parâmetro | Obrigatório | Exemplo | Descrição |
|---|---|---|---|
| `senha` | Sim | `XXXXXXXX` | Senha utilizada na requisição |
| `chave` | Sim | `XXXXXXXX` | Chave utilizada na requisição |
| `dataPedido` | Não | `20260812` | Data de consulta no formato `AAAAMMDD` (`20260812` = 12/08/2026). Se omitido, retorna a posição atual de todos os pedidos, independente da data |

### 9.2 Exemplo de requisição

```http
GET {{host}}/rest/wms/v2/pedidosPorStatus/query?senha={{senha}}&chave={{chave}}&dataPedido=20260812
Authorization: Basic {{senhaAutenticacao}}
tenantId: {{empresa}}, {{filial}}
```

### 9.3 Exemplo de resposta

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

### 9.4 Estrutura da resposta

**Objeto principal**

| Campo | Tipo | Descrição |
|---|---|---|
| `items` | Array | Lista dos status encontrados na consulta |
| `cliente` | String | Código do cliente |
| `loja` | String | Código da loja do cliente |
| `dataPedido` | String | Data do pedido retornada pela API |

**Item de `items`**

| Campo | Tipo | Descrição |
|---|---|---|
| `status` | String | Código do status do pedido |
| `descricaoStatus` | String | Descrição do status |
| `quantidade` | Integer | Quantidade de pedidos naquele status |

Interpretação: `{"status":"3","descricaoStatus":"A CONFERIR","quantidade":172}` significa que existem **172 pedidos** com status **A CONFERIR**.

### 9.5 Variáveis

| Variável | Descrição |
|---|---|
| `{{empresa}}` | Código da empresa (utilizar `03`) |
| `{{filial}}` | Código da filial Lisalog |
| `{{host}}` | Endereço host do servidor |
| `{{senha}}` | Senha de acesso ao endpoint |
| `{{chave}}` | Chave de acesso ao endpoint |
| `{{senhaAutenticacao}}` | Senha de autenticação da API |

---

## 10. Glossário de status

### 10.1 Status textual (`CSTATUS`) — `WMSSTATUS` e `RSSTSPG`

| Status | Significado |
|---|---|
| `INTEGRADO` | Pedido recebido, aguardando processamento |
| `A SEPARAR` | Pedido gerado, separação ainda não iniciada |
| `SEPARANDO` | Pedido em processo de separação |
| `A CONFERIR` | Separação finalizada, conferência ainda não iniciada |
| `CONFERINDO` | Pedido em processo de conferência |
| `EM PESAGEM` | Pedido em processo de pesagem *(listado apenas na API `WMSSTATUS`)* |
| `CONFERIDO` | Pedido com conferência finalizada |
| `A EXPEDIR` | Pedido pronto para retirada da transportadora |
| `FINALIZADO` | Pedido expedido |

### 10.2 Status numérico — `pedidosPorStatus`

| Código | Descrição |
|---|---|
| `1` | A SEPARAR |
| `3` | A CONFERIR |
| `4` | CONFERIDO |
| `5` | A EXPEDIR |
| `6` | FINALIZADO |
| `7` | CANCELADO |

> Códigos e descrições são os valores observados no exemplo de resposta; o documento original não apresenta a lista completa (ex.: códigos `0` e `2`).

---

## 11. Pontos de atenção na documentação original

Itens que aparecem inconsistentes entre os documentos de origem e merecem confirmação com a Lisalog:

1. **Senha de teste:** os documentos de *Atualiza pedido*, *Separação* informam `apiwms#245@` (token `...IzI0NUA=` após `YXBp`), enquanto *Cancelamento*, *Status por data* e *Status do pedido* informam `Apiwms#245@` (com **A** maiúsculo, token `...QXBpd21z...`). São credenciais diferentes.
2. **`nqtd` (itens da separação):** a tabela diz `Texto`, o exemplo envia número.
3. **`ccodigopedido`:** consta na tabela e na descrição de campos da separação, mas não no JSON de exemplo.
4. **`cNotaOriginal` / `cSerieOriginal`:** aparecem no nível do pedido (exemplo e tabela) e dentro de `aitens`; a descrição textual só documenta a versão de `aitens`.
5. **`curlguiaST` vs `cguiast64`:** na atualização, a guia de ST é enviada por URL (`curlguiaST`); na separação, em base64 (`cguiast64`).
6. **Unidades de medida:** na separação, dimensões dos volumes em **metros**; no `WMSSTATUS`, dimensões da embalagem em **centímetros**.
7. **Nome do array de séries:** `ASERIEMAI` no `WMSSTATUS` e `ASERIIMEI` no `RSSTSPG` (grafias diferentes para o mesmo conceito).
8. **`HORAEXPEDIDO`:** descrito como `HH:SS`, mas o exemplo (`09:21`, `18:10`) indica `HH:MM`.
9. **Exemplo de `RSSTSPG`:** a requisição usa `DATAPEDIDO=20190529`, enquanto a resposta traz `CDATAPEDIDO` `20260101` (exemplos independentes).
10. **Respostas de `POST`/`PUT /PEDIDOWMS`:** os documentos não descrevem o corpo de resposta nem códigos de erro.
11. **Sumários dos PDFs de Atualiza pedido / Cancelamento / Status por data** estavam sem títulos (erro de indicador do Word); a estrutura foi reconstruída a partir do conteúdo.
