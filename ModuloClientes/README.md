<!-- PADRAO-LISA -->
<p align="center">
  <img src="../imagens/banner-lisa.png" alt="Lisa Logística Integrada Sulamericana — Documentação de Sistemas" width="100%">
</p>

<h1 align="center">Módulo de Clientes</h1>
<p align="center"><b>Portal do Cliente</b> · Lisa Logística Integrada Sulamericana</p>

[⬅ Voltar ao índice](../README.md)

---

> Portal de acesso dos clientes da Lisalog às informações de suas operações no armazém, no ERP Protheus (TOTVS).

## Sumário

- [Objetivo](#objetivo)
- [1. Acesso via URL + Arquivo de instalação do Smartclient de acesso ao portal](#1-acesso-via-url--arquivo-de-instalação-do-smartclient-de-acesso-ao-portal)
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

## 1. Acesso via URL + Arquivo de instalação do Smartclient de acesso ao portal

Acesse pelo navegador de internet o link abaixo e informe o código de usuário e senha:

**Links:**

- **Ambiente de TESTE:** <https://li195955.protheus.cloudtotvs.com.br:11303/webapp/?StartProg=SIGAESP&Env=CCFMH3_DEV>
- **Ambiente de PROD:** <https://li195954.protheus.cloudtotvs.com.br:4010/webapp/?Startprog=SIGAESP&Env=CCFMH3_PROD>

<p align="center">
  <img src="imagens/Imagem1.png" alt="Acessando com o usuário e senha">
</p>

<p align="center">
  <img src="imagens/Imagem2.png" alt="Acessando com o usuário e senha"><br>
  <sub><b>Figura 1</b> — Acessando com o usuário e senha</sub>
</p>

Informe o código do grupo e filial que deseja acessar. (Essas informações já virão preenchidas, altere apenas se necessário)

<p align="center">
  <img src="imagens/Imagem3.png" alt="Informando filial Lisalog do acesso"><br>
  <sub><b>Figura 2</b> — Informando filial Lisalog do acesso</sub>
</p>

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

<p align="center">
  <img src="imagens/Imagem4.png" alt="Opções Menu atualizações"><br>
  <sub><b>Figura 3</b> — Opções Menu atualizações</sub>
</p>

### 2.1 Api Pedido

A rotina Api Pedido possui as seguintes opções:

<p align="center">
  <img src="imagens/Imagem5.png" alt="Opções Api Pedido"><br>
  <sub><b>Figura 4</b> — Opções Api Pedido</sub>
</p>

#### Incluir

Realizar a inclusão manual de pedido ou importar informações de um arquivo TXT/XML e DANFE.

<p align="center">
  <img src="imagens/Imagem6.png" alt="Outras ações Api Pedido"><br>
  <sub><b>Figura 5</b> — Outras ações Api Pedido</sub>
</p>

<p align="center">
  <img src="imagens/Imagem7.png" alt="Importar TXT/XML ou Danfe Api Pedido"><br>
  <sub><b>Figura 6</b> — Importar TXT/XML ou Danfe Api Pedido</sub>
</p>

<p align="center">
  <img src="imagens/Imagem8.png" alt="Indicando arquivos locais"><br>
  <sub><b>Figura 7</b> — Indicando arquivos locais</sub>
</p>

<p align="center">
  <img src="imagens/Imagem9.png" alt="Selecionando o arquivo"><br>
  <sub><b>Figura 8</b> — Selecionando o arquivo</sub>
</p>

<p align="center">
  <img src="imagens/Imagem10.png" alt="Layout de arquivo TXT no Excel"><br>
  <sub><b>Figura 9</b> — Layout de arquivo TXT no Excel</sub>
</p>

<p align="center">
  <img src="imagens/Imagem11.png" alt="Conteúdo do arquivo TXT"><br>
  <sub><b>Figura 10</b> — Conteúdo do arquivo TXT</sub>
</p>

#### Outras ações > Cancelar Pedido

Faz uma solicitação de cancelamento do pedido.

<p align="center">
  <img src="imagens/Imagem12.png" alt="Solicitar cancelamento de pedido"><br>
  <sub><b>Figura 11</b> — Solicitar cancelamento de pedido</sub>
</p>

#### Outras ações > Upload Danfe

Realizar o upload da nota fiscal de saída

<p align="center">
  <img src="imagens/Imagem13.png" alt="Enviar Danfe do pedido"><br>
  <sub><b>Figura 12</b> — Enviar Danfe do pedido</sub>
</p>

<p align="center">
  <img src="imagens/Imagem14.png" alt="Campo preenchido com o XML"><br>
  <sub><b>Figura 13</b> — Campo preenchido com o XML</sub>
</p>

<p align="center">
  <img src="imagens/Imagem15.png" alt="Campo preenchido com a DANFE"><br>
  <sub><b>Figura 14</b> — Campo preenchido com a DANFE</sub>
</p>

#### Outras ações > Status

Consulta o status do pedido.

<p align="center">
  <img src="imagens/Imagem16.png" alt="Consulta de status do pedido"><br>
  <sub><b>Figura 15</b> — Consulta de status do pedido</sub>
</p>

#### Outras ações > Importar

Realiza a importação de múltiplos arquivos XML das notas fiscais ou arquivos TXT para geração de pedidos para separação.

<p align="center">
  <img src="imagens/Imagem17.png" alt="Importando múltiplos arquivos para geração de pedidos (xml)"><br>
  <sub><b>Figura 16</b> — Importando múltiplos arquivos para geração de pedidos (xml)</sub>
</p>

<p align="center">
  <img src="imagens/Imagem18.png" alt="Importando múltiplos arquivos para geração de pedidos (txt)"><br>
  <sub><b>Figura 17</b> — Importando múltiplos arquivos para geração de pedidos (txt)</sub>
</p>

<p align="center">
  <img src="imagens/Imagem19.png" alt="Criando arquivo TXT no layout completo"><br>
  <sub><b>Figura 18</b> — Criando arquivo TXT no layout completo</sub>
</p>

<p align="center">
  <img src="imagens/Imagem20.png" alt="Salvando arquivo TXT"><br>
  <sub><b>Figura 19</b> — Salvando arquivo TXT</sub>
</p>

<p align="center">
  <img src="imagens/Imagem21.png" alt="Layout do arquivo TXT"><br>
  <sub><b>Figura 20</b> — Layout do arquivo TXT</sub>
</p>

#### Outras ações > Ajuste CEP

Imprimir dados listados na tela atual.

<p align="center">
  <img src="imagens/Imagem22.png" alt="Tela de Outras ações &gt; Ajuste CEP">
</p>

#### Outras ações > Importar por armazém

Integrar pedidos por armazém.

<p align="center">
  <img src="imagens/Imagem23.png" alt="Tela de Outras ações &gt; Importar por armazém">
</p>

#### Outras ações > Importar por campanha

Integrar pedidos por campanha.

<p align="center">
  <img src="imagens/Imagem24.png" alt="Tela de Outras ações &gt; Importar por campanha">
</p>

#### Outras ações > Transportadora

Incluir ou alterar transportadora dos pedidos.

<p align="center">
  <img src="imagens/Imagem25.png" alt="Tela de Outras ações &gt; Transportadora">
</p>

#### Outras ações > Carta de correção

Enviar carta de correção em (PDF).

<p align="center">
  <img src="imagens/Imagem26.png" alt="Tela de Outras ações &gt; Carta de correção">
</p>

#### Outras ações > Upload Mult Docs

Fazer o Upload de múltiplos documentos.

<p align="center">
  <img src="imagens/Imagem27.png" alt="Tela de Outras ações &gt; Upload Mult Docs">
</p>

#### Outras ações > Reprocessa todos sem saldo

Reprocessa todos pedidos sem saldo.

<p align="center">
  <img src="imagens/Imagem28.png" alt="Tela de Outras ações &gt; Reprocessa todos sem saldo">
</p>

#### Outras ações > Pedido parcial

Acessa a tela dos pedidos parciais.

<p align="center">
  <img src="imagens/Imagem29.png" alt="Tela de Outras ações &gt; Pedido parcial">
</p>

#### Outras ações > Relatório parcial / sem saldo

Imprimir relatório dos pedidos parciais e sem saldo.

<p align="center">
  <img src="imagens/Imagem30.png" alt="Tela de Outras ações &gt; Relatório parcial / sem saldo">
</p>

<p align="center">
  <img src="imagens/Imagem31.png" alt="Tela de Outras ações &gt; Relatório parcial / sem saldo">
</p>

#### Outras ações > Estimativa envio

Altera a estimativa de envio dos pedidos (**Obs.:** rotina da integração da API infracommerce).

<p align="center">
  <img src="imagens/Imagem32.png" alt="Tela de Outras ações &gt; Estimativa envio">
</p>

#### Outras ações > Upload documentos

Fazer upload de documento em PDF.

<p align="center">
  <img src="imagens/Imagem33.png" alt="Tela de Outras ações &gt; Upload documentos">
</p>

#### Outras ações > Imprimir browse

Imprimir dados listados na tela atual.

<p align="center">
  <img src="imagens/Imagem34.png" alt="Tela de Outras ações &gt; Imprimir browse">
</p>

### 2.2 Api Nota de Saída

Disponível apenas para consultar notas de saída enviadas para os pedidos.

<p align="center">
  <img src="imagens/Imagem35.png" alt="Dados Api Nota Saida"><br>
  <sub><b>Figura 21</b> — Dados Api Nota Saida</sub>
</p>

### 2.3 Api Entrada

Enviar entradas de armazenagem.

<p align="center">
  <img src="imagens/Imagem36.png" alt="API Entrada opções"><br>
  <sub><b>Figura 22</b> — API Entrada opções</sub>
</p>

#### Upload

Faz o upload das informações de entrada através do XML das notas fiscais.

<p align="center">
  <img src="imagens/Imagem37.png" alt="Upload de notas de entrada"><br>
  <sub><b>Figura 23</b> — Upload de notas de entrada</sub>
</p>

#### Excluir

Exclui o registro da entrada.

#### Outras ações > Status

Consulta o status da entrada no armazém.

<p align="center">
  <img src="imagens/Imagem38.png" alt="Consulta de status da entrada"><br>
  <sub><b>Figura 24</b> — Consulta de status da entrada</sub>
</p>

#### Alterar Armazém

Permite alterar o armazém da nota fiscal integrada.

<p align="center">
  <img src="imagens/Imagem39.png" alt="Alterar Armazém"><br>
  <sub><b>Figura 25</b> — Alterar Armazém</sub>
</p>

#### Alterar Cod Postagem

Permite alterar o código de postagem da nota fiscal integrada.

<p align="center">
  <img src="imagens/Imagem40.png" alt="Alterar Código de Postagem"><br>
  <sub><b>Figura 26</b> — Alterar Código de Postagem</sub>
</p>

#### Alterar Nf Origem

Permite alterar a nota fiscal de origem.

<p align="center">
  <img src="imagens/Imagem41.png" alt="Alterar NF de Origem"><br>
  <sub><b>Figura 27</b> — Alterar NF de Origem</sub>
</p>

#### Status

Retorna o status atual da nota fiscal integrada.

<p align="center">
  <img src="imagens/Imagem42.png" alt="Status Nota Fiscal"><br>
  <sub><b>Figura 28</b> — Status Nota Fiscal</sub>
</p>

#### Entrada por CSV

Permite enviar o código do produto diferente ao XML.

<p align="center">
  <img src="imagens/Imagem43.png" alt="Entrada por CSV"><br>
  <sub><b>Figura 29</b> — Entrada por CSV</sub>
</p>

#### Enviar DANFE/XML

Permite enviar a Danfe e o XML da nota fiscal.

<p align="center">
  <img src="imagens/Imagem44.png" alt="Enviar DANFE/XML"><br>
  <sub><b>Figura 30</b> — Enviar DANFE/XML</sub>
</p>

#### Download DANFE

Permite baixar a Danfe da nota fiscal.

<p align="center">
  <img src="imagens/Imagem45.png" alt="Download DANFE"><br>
  <sub><b>Figura 31</b> — Download DANFE</sub>
</p>

### 2.4 Agendamentos

Consultar, incluir ou alterar agendamentos de entrada no armazém.

#### Agendamento

Apresenta agenda para inclusão de agendamento.

### 2.5 Produto por fornecedor

Incluir, alterar, visualizar ou excluir cadastro de produto por fornecedor.

<p align="center">
  <img src="imagens/Imagem46.png" alt="Cadastro de produtos por fornecedor"><br>
  <sub><b>Figura 32</b> — Cadastro de produtos por fornecedor</sub>
</p>

## 3. Menu Consultas

Disponíveis as seguintes opções:

### Monitor Pedidos

Apresenta os pedidos com status.

<p align="center">
  <img src="imagens/Imagem47.png" alt="Monitor Pedidos"><br>
  <sub><b>Figura 33</b> — Monitor Pedidos</sub>
</p>

### Recebimento

Monitoramento dos recebimentos no armazém.

<p align="center">
  <img src="imagens/Imagem48.png" alt="Consulta recebimento"><br>
  <sub><b>Figura 34</b> — Consulta recebimento</sub>
</p>

### Painel Por Hora

Apresenta uma análise detalhada das separações realizadas na data escolhida.

<p align="center">
  <img src="imagens/Imagem49.png" alt="Informando data do painel por hora"><br>
  <sub><b>Figura 35</b> — Informando data do painel por hora</sub>
</p>

<p align="center">
  <img src="imagens/Imagem50.png" alt="Painel por hora"><br>
  <sub><b>Figura 36</b> — Painel por hora</sub>
</p>

### Monitoramento

Monitoramento da separação dos pedidos no armazém.

<p align="center">
  <img src="imagens/Imagem51.png" alt="Monitor de separações"><br>
  <sub><b>Figura 37</b> — Monitor de separações</sub>
</p>

### Indicadores

Visão geral das operações no armazém.

<p align="center">
  <img src="imagens/Imagem52.png" alt="Indicadores"><br>
  <sub><b>Figura 38</b> — Indicadores</sub>
</p>

### Números de serie

Permite pesquisar, visualizar detalhes e importar por arquivo TXT.

<p align="center">
  <img src="imagens/Imagem53.png" alt="Números de serie"><br>
  <sub><b>Figura 39</b> — Números de serie</sub>
</p>

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

---

[⬅ Voltar ao índice](../README.md)

<p align="center">
  <img src="../imagens/logo-lisa.png" alt="Lisa" width="110"><br>
  <sub>Lisa Logística Integrada Sulamericana · Tecnologia da Informação</sub>
</p>
