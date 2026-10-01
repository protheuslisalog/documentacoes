# Módulo de Clientes

> Portal de acesso dos clientes da Lisalog às informações de suas operações no armazém, no ERP Protheus (TOTVS).

## Sumário

- [Objetivo](#objetivo)
- [1. Acesso via URL + Arquivo de instalação do Stmartclient de acesso ao portal](#1-acesso-via-url--arquivo-de-instalação-do-stmartclient-de-acesso-ao-portal)
- [2. Menu atualizações](#2-menu-atualizações)
  - [2.1 Api Pedido](#21-api-pedido)
  - [2.2 Api Nota de Saída](#22-api-nota-de-saída)
  - [2.3 Api Entrada](#23-api-entrada)
  - [2.4 Agendamentos](#24-agendamentos)
  - [2.5 Produto por fornecedor](#25-produto-por-fornecedor)
- [3. Menu Consultas](#3-menu-consultas)
  - [Monitor Pedidos](#monitor-pedidos)
  - [Recebimento](#recebimento)
  - [Painel Por Hora](#painel-por-hora)
  - [Monitoramento](#monitoramento)
  - [Indicadores](#indicadores)
  - [Números de serie](#números-de-serie)
- [4. Relatórios](#4-relatórios)

## Objetivo

Disponibilizar acesso aos clientes da Lisalog as informações de suas operações no armazém e permitir enviarem dados de pedidos para separação ou entradas para armazenagem.

## 1. Acesso via URL + Arquivo de instalação do Stmartclient de acesso ao portal

Acesse pelo navegador de internet o link abaixo e informe o código de usuário e senha:

**Links:**

- **Ambiente de TESTE:** <https://li195955.protheus.cloudtotvs.com.br:11303/webapp/?StartProg=SIGAESP&Env=CCFMH3_DEV>
- **Ambiente de PROD:** <https://li195954.protheus.cloudtotvs.com.br:4010/webapp/?Startprog=SIGAESP&Env=CCFMH3_PROD>

![Acessando com o usuário e senha](imagem1.png)

![Acessando com o usuário e senha](imagem2.png)

*Figura 1 - Acessando com o usuário e senha*

Informe o código do grupo e filial que deseja acessar. (Essas informações já virão preenchidas, altere apenas se necessário)

![Informando filial Lisalog do acesso](imagem3.png)

*Figura 2 - Informando filial Lisalog do acesso*

## 2. Menu atualizações

Em Atualizações estão disponíveis as seguintes opções:

- **Api Pedido** — Enviar pedidos para separação, visualizar pedidos, consulta de informações de pedidos, cancelar pedidos, envio de notas fiscais de saída, controlar pedidos integrados sem saldo (1) e controlar pedidos parciais (2).

  > **Obs.:** Para habilitar o funcionamento das rotinas 1 e 2, é necessário ativar no cadastro do cliente o campo `INT PD S SLS - A1_XPEDSS` = SIM.

- **Api Nota Saída** — Enviar / Consultar notas fiscais de saída enviadas para os pedidos.
- **Api Entrada** — Envio, visualizar e exclusão de documentos de entrada para armazenagem.
- **Romaneio** — Consulta e download de Romaneios de saída, entrada ou devolução, e/ou consulta TFA de entrada.
- **Agendamentos** — Agendamento de entregas das entradas no armazém.
- **Produto Por Fornecedor** — Cadastro de produtos por fornecedor.
- **Api Documentos** — Enviar / Consultar documentos enviadas.
- **Download Ret Armazenagem** — Fazer o download da nota fiscal de retorno de remessa de armazenagem.
- **Pre Pedido Rolo** — Importar / enviar / visualizar / alterar / aprovar / cancelar e reprovar pre pedidos.
- **Rolo Armazenado** — Importar / visualizar / excluir paking list.
- **Atualiza Qtd. Mínima** — Atualizar a quantidade mínima via arquivo.
- **Lançamento Serviços** — Fazer o download e aprovar o demonstrativo de serviço.
- **Log de Integração** — Consultar log de integração dos pedidos
- **Integrações** — Executa a integra com outros sistemas já integrados com o Protheus

![Opções Menu atualizações](imagem4.png)

*Figura 3 - Opções Menu atualizações*

### 2.1 Api Pedido

A rotina Api Pedido possui as seguintes opções:

![Opções Api Pedido](imagem5.png)

*Figura 4 - Opções Api Pedido*

#### Incluir

Realizar a inclusão manual de pedido ou importar informações de um arquivo TXT/XML e DANFE.

![Outras ações Api Pedido](imagem6.png)

*Figura 5 - Outras ações Api Pedido*

![Importar TXT/XML ou Danfe Api Pedido](imagem7.png)

*Figura 6 - Importar TXT/XML ou Danfe Api Pedido*

![Indicando arquivos locais](imagem8.png)

*Figura 7 - Indicando arquivos locais*

![Selecionando o arquivo](imagem9.png)

*Figura 8 - Selecionando o arquivo*

![Layout de arquivo TXT no Excel](imagem10.png)

*Figura 9 - Layout de arquivo TXT no Excel*

![Conteúdo do arquivo TXT](imagem11.png)

*Figura 10 - Conteúdo do arquivo TXT*

#### Outras ações > Cancelar Pedido

Faz uma solicitação de cancelamento do pedido.

![Solicitar cancelamento de pedido](imagem12.png)

*Figura 11 - Solicitar cancelamento de pedido*

#### Outras ações > Upload Danfe

Realizar o upload da nota fiscal de saída

![Enviar Danfe do pedido](imagem13.png)

*Figura 12 - Enviar Danfe do pedido*

![Campo preenchido com o XML](imagem14.png)

*Figura 13 - Campo preenchido com o XML*

![Campo preenchido com a DANFE](imagem15.png)

*Figura 14 - Campo preenchido com a DANFE*

#### Outras ações > Status

Consulta o status do pedido.

![Consulta de status do pedido](imagem16.png)

*Figura 15 - Consulta de status do pedido*

#### Outras ações > Importar

Realiza a importação de múltiplos arquivos XML das notas fiscais ou arquivos TXT para geração de pedidos para separação.

![Importando múltiplos arquivos para geração de pedidos (xml)](imagem17.png)

*Figura 16 - Importando múltiplos arquivos para geração de pedidos (xml)*

![Importando múltiplos arquivos para geração de pedidos (txt)](imagem18.png)

*Figura 17 - Importando múltiplos arquivos para geração de pedidos (txt)*

![Criando arquivo TXT no layout completo](imagem19.png)

*Figura 18 - Criando arquivo TXT no layout completo*

![Salvando arquivo TXT](imagem20.png)

*Figura 19 - Salvando arquivo TXT*

![Layout do arquivo TXT](imagem21.png)

*Figura 20 - Layout do arquivo TXT*

#### Outras ações > Ajuste CEP

Imprimir dados listados na tela atual.

![Tela de Outras ações > Ajuste CEP](imagem22.png)

#### Outras ações > Importar por armazém

Integrar pedidos por armazém.

![Tela de Outras ações > Importar por armazém](imagem23.png)

#### Outras ações > Importar por campanha

Integrar pedidos por campanha.

![Tela de Outras ações > Importar por campanha](imagem24.png)

#### Outras ações > Transportadora

Incluir ou alterar transportadora dos pedidos.

![Tela de Outras ações > Transportadora](imagem25.png)

#### Outras ações > Carta de correção

Enviar carta de correção em (PDF).

![Tela de Outras ações > Carta de correção](imagem26.png)

#### Outras ações > Upload Mult Docs

Fazer o Upload de múltiplos documentos.

![Tela de Outras ações > Upload Mult Docs](imagem27.png)

#### Outras ações > Reprocessa todos sem saldo

Reprocessa todos pedidos sem saldo.

![Tela de Outras ações > Reprocessa todos sem saldo](imagem28.png)

#### Outras ações > Pedido parcial

Acessa a tela dos pedidos parciais.

![Tela de Outras ações > Pedido parcial](imagem29.png)

#### Outras ações > Relatório parcial / sem saldo

Imprimir relatório dos pedidos parciais e sem saldo.

![Tela de Outras ações > Relatório parcial / sem saldo](imagem30.png)

![Tela de Outras ações > Relatório parcial / sem saldo](imagem31.png)

#### Outras ações > Estimativa envio

Altera a estimativa de envio dos pedidos (**Obs.:** rotina da integração da API infracommerce).

![Tela de Outras ações > Estimativa envio](imagem32.png)

#### Outras ações > Upload documentos

Fazer upload de documento em PDF.

![Tela de Outras ações > Upload documentos](imagem33.png)

#### Outras ações > Imprimir browse

Imprimir dados listados na tela atual.

![Tela de Outras ações > Imprimir browse](imagem34.png)

### 2.2 Api Nota de Saída

Disponível apenas para consultar notas de saída enviadas para os pedidos.

![Dados Api Nota Saida](imagem35.png)

*Figura 21 - Dados Api Nota Saida*

### 2.3 Api Entrada

Enviar entradas de armazenagem.

![API Entrada opções](imagem36.png)

*Figura 22 - API Entrada opções*

#### Upload

Faz o upload das informações de entrada através do XML das notas fiscais.

![Upload de notas de entrada](imagem37.png)

*Figura 23 - Upload de notas de entrada*

#### Excluir

Exclui o registro da entrada.

#### Outras ações > Status

Consulta o status da entrada no armazém.

![Consulta de status da entrada](imagem38.png)

*Figura 24 - Consulta de status da entrada*

#### Alterar Armazém

Permite alterar o armazém da nota fiscal integrada.

![Alterar Armazém](imagem39.png)

*Figura 25 - Alterar Armazém*

#### Alterar Cod Postagem

Permite alterar o código de postagem da nota fiscal integrada.

![Alterar Código de Postagem](imagem40.png)

*Figura 26 - Alterar Código de Postagem*

#### Alterar Nf Origem

Permite alterar a nota fiscal de origem.

![Alterar NF de Origem](imagem41.png)

*Figura 27 - Alterar NF de Origem*

#### Status

Retorna o status atual da nota fiscal integrada.

![Status Nota Fiscal](imagem42.png)

*Figura 28 - Status Nota Fiscal*

#### Entrada por CSV

Permite enviar o código do produto diferente ao XML.

![Entrada por CSV](imagem43.png)

*Figura 29 - Entrada por CSV*

#### Enviar DANFE/XML

Permite enviar a Danfe e o XML da nota fiscal.

![Enviar DANFE/XML](imagem44.png)

*Figura 30 - Enviar DANFE/XML*

#### Download DANFE

Permite baixar a Danfe da nota fiscal.

![Download DANFE](imagem45.png)

*Figura 31 - Download DANFE*

### 2.4 Agendamentos

Consultar, incluir ou alterar agendamentos de entrada no armazém.

#### Agendamento

Apresenta agenda para inclusão de agendamento.

### 2.5 Produto por fornecedor

Incluir, alterar, visualizar ou excluir cadastro de produto por fornecedor.

![Cadastro de produtos por fornecedor](imagem46.png)

*Figura 32 - Cadastro de produtos por fornecedor*

## 3. Menu Consultas

Disponíveis as seguintes opções:

### Monitor Pedidos

Apresenta os pedidos com status.

![Monitor Pedidos](imagem47.png)

*Figura 33 - Monitor Pedidos*

### Recebimento

Monitoramento dos recebimentos no armazém.

![Consulta recebimento](imagem48.png)

*Figura 34 - Consulta recebimento*

### Painel Por Hora

Apresenta uma análise detalhada das separações realizadas na data escolhida.

![Informando data do painel por hora](imagem49.png)

*Figura 35 - Informando data do painel por hora*

![Painel por hora](imagem50.png)

*Figura 36 - Painel por hora*

### Monitoramento

Monitoramento da separação dos pedidos no armazém.

![Monitor de separações](imagem51.png)

*Figura 37 - Monitor de separações*

### Indicadores

Visão geral das operações no armazém.

![Indicadores](imagem52.png)

*Figura 38 – Indicadores*

### Números de serie

Permite pesquisar, visualizar detalhes e importar por arquivo TXT.

![Números de serie](imagem53.png)

*Figura 39 - Números de serie*

## 4. Relatórios

- **Monitor Pedido** — Informações diversas dos pedidos.
- **Estoque** — Arquivos com informações sobre o saldo dos produtos.
- **Lote/Endereço** — Arquivo com informações de saldo por lote/localização.
- **Reversa** — Informações sobre o processo de reversa.
- **Saldos Disponíveis** — Informações de saldos disponíveis para pedidos.
- **Entradas** — Informações do processo de recebimento dos produtos.
- **Entradas x Saídas** — Informações do processo de recebimento / saída dos produtos.
- **Kardex** — Informações da movimentação de entrada / saída dos produtos.
- **Kardex Lote** — Informações da movimentação de entrada / saída dos produtos por Lote.
- **Estoque mínimo** — Informações do estoque mínimo dos produtos.
- **Estoque Rolos** — Informações do estoque de Rolos.
- **Rel Posição Estoque** — Informações de estoque dos produtos.
