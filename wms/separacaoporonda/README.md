<!-- PADRAO-LISA -->
<p align="center">
  <img src="../../imagens/banner-lisa.png" alt="Lisa Logística Integrada Sulamericana — Documentação de Sistemas" width="100%">
</p>

<h1 align="center">Separação por Onda</h1>
<p align="center"><b>WMS</b> · Lisa Logística Integrada Sulamericana</p>

[⬅ Voltar ao índice](../../README.md)

---

> **Sistema:** TOTVS · WMS – Gestão de Armazenagem

## Sumário

1. [Geração da Onda de Separação](#1-geração-da-onda-de-separação)
2. [Vinculando Onda de separação ao RH e imprimindo etiquetas](#2-vinculando-onda-de-separação-ao-rh-e-imprimindo-etiquetas)
3. [Consultar Onda de separação](#3-consultar-onda-de-separação)
4. [Importar arquivo para gerar Onda](#4-importar-arquivo-para-gerar-onda)
5. [Configurar grupo de campanhas/data/onda para aglutinar pedidos](#5-configurar-grupo-de-campanhasdataonda-para-aglutinar-pedidos)
   - [5.1. Aglutinar apenas pedidos da mesma data](#51-aglutinar-apenas-pedidos-da-mesma-data)
   - [5.2. Aglutinar pedidos sem onda gerada](#52-aglutinar-pedidos-sem-onda-gerada)

---

## 1. Geração da Onda de Separação

A rotina de geração de Onda de separação está disponível em:

**WMS >> Personalizados >> Cadastros >> Pedidos Aglutinados**

<p align="center">
  <img src="imagens/figura-01.png" alt="Acesso no menu WMS geração da Onda"><br>
  <sub><b>Figura 1</b> — Acesso no menu WMS geração da Onda</sub>
</p>

Acione a opção **"Onda"**.

<p align="center">
  <img src="imagens/figura-02.png" alt="Acesso à tela de geração de Onda"><br>
  <sub><b>Figura 2</b> — Acesso à tela de geração de Onda</sub>
</p>

Preencha os parâmetros da rotina conforme as informações abaixo:

| Campo | Descrição |
|-------|-----------|
| **Cliente** | Código do cliente |
| **Loja** | Código da loja do cliente |
| **RH** | Código do Recurso Humano do WMS para o qual estão amarradas as separações |
| **Máximo** | Número máximo de pedidos para geração da Onda |

<p align="center">
  <img src="imagens/figura-03.png" alt="Parâmetros da rotina de geração de Onda"><br>
  <sub><b>Figura 3</b> — Parâmetros da rotina de geração de Onda</sub>
</p>

Selecione os itens na tela conforme necessidade e clique em **Confirmar**.

<p align="center">
  <img src="imagens/figura-04.png" alt="Selecionando itens para gerar Onda"><br>
  <sub><b>Figura 4</b> — Selecionando itens para gerar Onda</sub>
</p>

Será apresentado o log com os pedidos e o código da Onda de separação.

<p align="center">
  <img src="imagens/figura-05.png" alt="Log da geração da Onda"><br>
  <sub><b>Figura 5</b> — Log da geração da Onda</sub>
</p>

---

## 2. Vinculando Onda de separação ao RH e imprimindo etiquetas

Acesse a rotina **WMS >> Etiquetas >> Onda**.

<p align="center">
  <img src="imagens/figura-06.png" alt="Acesso no menu WMS para vincular Onda"><br>
  <sub><b>Figura 6</b> — Acesso no menu WMS para vincular Onda</sub>
</p>

Preencha os parâmetros e clique em **Ok**.

<p align="center">
  <img src="imagens/figura-07.png" alt="Parâmetros para impressão de etiqueta/vincular RH"><br>
  <sub><b>Figura 7</b> — Parâmetros para impressão de etiqueta/vincular RH</sub>
</p>

| Campo | Descrição |
|-------|-----------|
| **Onda** | Código da Onda |
| **Local** | Local de impressão das etiquetas |
| **RH** | Código do Recurso Humano para o qual serão atribuídas as atividades dos pedidos da Onda |

> **Obs.:** Ao clicar em Ok será perguntado se deseja imprimir as etiquetas.
> Também é possível acessar a impressão de etiquetas pelas opções disponíveis em **Outras Ações**.

---

## 3. Consultar Onda de separação

Acesse a opção **Consultar** em **Outras Ações**. Serão apresentados os pedidos, produtos e Recursos Humanos da onda consultada.

<p align="center">
  <img src="imagens/figura-08.png" alt="Consulta dados Onda"><br>
  <sub><b>Figura 8</b> — Consulta dados Onda</sub>
</p>

---

## 4. Importar arquivo para gerar Onda

Monte um arquivo com **um pedido em cada linha** e salve-o com a extensão `.TXT`.

Exemplo de conteúdo:

```text
SYGM67
SYGM68
PED123
```

<p align="center">
  <img src="imagens/figura-09.png" alt="Criando arquivo para importar"><br>
  <sub><b>Figura 9</b> — Criando arquivo para importar</sub>
</p>

<p align="center">
  <img src="imagens/figura-10.png" alt="Arquivo TXT"><br>
  <sub><b>Figura 10</b> — Arquivo TXT</sub>
</p>

Acesse a opção **"Importa Onda"** em **"Outras Ações"** e selecione o arquivo montado.

<p align="center">
  <img src="imagens/figura-11.png" alt="Importar arquivo de onda"><br>
  <sub><b>Figura 11</b> — Importar arquivo de onda</sub>
</p>

<p align="center">
  <img src="imagens/figura-12.png" alt="Selecionando arquivo"><br>
  <sub><b>Figura 12</b> — Selecionando arquivo</sub>
</p>

Ao importar, o sistema exibe uma mensagem informando o caminho do arquivo de log.

<p align="center">
  <img src="imagens/figura-13.png" alt="Mensagem ao importar arquivo"><br>
  <sub><b>Figura 13</b> — Mensagem ao importar arquivo</sub>
</p>

Verifique o log gerado na mesma pasta do arquivo importado.

<p align="center">
  <img src="imagens/figura-14.png" alt="Arquivo de log gerado"><br>
  <sub><b>Figura 14</b> — Arquivo de log gerado</sub>
</p>

Exemplo de conteúdo do log:

```text
SYGM67|SUCESSO|GERADO EM ONDA:000000044306|
SYGM68|SUCESSO|GERADO EM ONDA:000000044306|
PED123|****ERRO****|PEDIDO NAO ENCONTRADO|
```

<p align="center">
  <img src="imagens/figura-15.png" alt="Conteúdo do arquivo de log"><br>
  <sub><b>Figura 15</b> — Conteúdo do arquivo de log</sub>
</p>

<p align="center">
  <img src="imagens/figura-16.png" alt="Registro de onda gerada"><br>
  <sub><b>Figura 16</b> — Registro de onda gerada</sub>
</p>

---

## 5. Configurar grupo de campanhas/data/onda para aglutinar pedidos

Acesse a opção **"Grupo Campanha"** em **Outras Ações**.

<p align="center">
  <img src="imagens/figura-17.png" alt="Acessando configuração de grupo campanha"><br>
  <sub><b>Figura 17</b> — Acessando configuração de grupo campanha</sub>
</p>

Crie os grupos conforme necessidade.

<p align="center">
  <img src="imagens/figura-18.png" alt="Criando os grupos de campanha"><br>
  <sub><b>Figura 18</b> — Criando os grupos de campanha</sub>
</p>

A aglutinação dos pedidos será feita quando estiverem no **mesmo grupo de campanha** ou quando **não possuírem um grupo configurado**.

### 5.1. Aglutinar apenas pedidos da mesma data

Para configurar a aglutinação dos pedidos por data, basta criar uma linha com a campanha `DATA` e o grupo `DATA`.

<p align="center">
  <img src="imagens/figura-19.png" alt="Configurar para aglutinar por data"><br>
  <sub><b>Figura 19</b> — Configurar para aglutinar por data</sub>
</p>

### 5.2. Aglutinar pedidos sem onda gerada

Para configurar o sistema para que aglutine apenas pedidos sem onda gerada, crie uma linha com a campanha `ONDA` e o grupo `ONDA`.

<p align="center">
  <img src="imagens/figura-20.png" alt="Configurar aglutinação para pedidos sem onda"><br>
  <sub><b>Figura 20</b> — Configurar aglutinação para pedidos sem onda</sub>
</p>

---

[⬅ Voltar ao índice](../../README.md)

<p align="center">
  <img src="../../imagens/logo-lisa.png" alt="Lisa" width="110"><br>
  <sub>Lisa Logística Integrada Sulamericana · Tecnologia da Informação</sub>
</p>
