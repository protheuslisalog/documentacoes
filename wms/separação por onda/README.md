# Separação por Onda

**LISA – Logística Integrada Sulamericana**
Sistema: TOTVS | WMS – Gestão de Armazenagem

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

![Figura 1 - Acesso no menu WMS geração da Onda](imagens/figura-01.png)

Acione a opção **"Onda"**.

![Figura 2 - Acesso à tela de geração de Onda](imagens/figura-02.png)

Preencha os parâmetros da rotina conforme as informações abaixo:

| Campo | Descrição |
|-------|-----------|
| **Cliente** | Código do cliente |
| **Loja** | Código da loja do cliente |
| **RH** | Código do Recurso Humano do WMS para o qual estão amarradas as separações |
| **Máximo** | Número máximo de pedidos para geração da Onda |

![Figura 3 - Parâmetros da rotina de geração de Onda](imagens/figura-03.png)

Selecione os itens na tela conforme necessidade e clique em **Confirmar**.

![Figura 4 - Selecionando itens para gerar Onda](imagens/figura-04.png)

Será apresentado o log com os pedidos e o código da Onda de separação.

![Figura 5 - Log da geração da Onda](imagens/figura-05.png)

---

## 2. Vinculando Onda de separação ao RH e imprimindo etiquetas

Acesse a rotina **WMS >> Etiquetas >> Onda**.

![Figura 6 - Acesso no menu WMS para vincular Onda](imagens/figura-06.png)

Preencha os parâmetros e clique em **Ok**.

![Figura 7 - Parâmetros para impressão de etiqueta/vincular RH](imagens/figura-07.png)

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

![Figura 8 - Consulta dados Onda](imagens/figura-08.png)

---

## 4. Importar arquivo para gerar Onda

Monte um arquivo com **um pedido em cada linha** e salve-o com a extensão `.TXT`.

Exemplo de conteúdo:

```text
SYGM67
SYGM68
PED123
```

![Figura 9 - Criando arquivo para importar](imagens/figura-09.png)

![Figura 10 - Arquivo TXT](imagens/figura-10.png)

Acesse a opção **"Importa Onda"** em **"Outras Ações"** e selecione o arquivo montado.

![Figura 11 - Importar arquivo de onda](imagens/figura-11.png)

![Figura 12 - Selecionando arquivo](imagens/figura-12.png)

Ao importar, o sistema exibe uma mensagem informando o caminho do arquivo de log.

![Figura 13 - Mensagem ao importar arquivo](imagens/figura-13.png)

Verifique o log gerado na mesma pasta do arquivo importado.

![Figura 14 - Arquivo de log gerado](imagens/figura-14.png)

Exemplo de conteúdo do log:

```text
SYGM67|SUCESSO|GERADO EM ONDA:000000044306|
SYGM68|SUCESSO|GERADO EM ONDA:000000044306|
PED123|****ERRO****|PEDIDO NAO ENCONTRADO|
```

![Figura 15 - Conteúdo do arquivo de log](imagens/figura-15.png)

![Figura 16 - Registro de onda gerada](imagens/figura-16.png)

---

## 5. Configurar grupo de campanhas/data/onda para aglutinar pedidos

Acesse a opção **"Grupo Campanha"** em **Outras Ações**.

![Figura 17 - Acessando configuração de grupo campanha](imagens/figura-17.png)

Crie os grupos conforme necessidade.

![Figura 18 - Criando os grupos de campanha](imagens/figura-18.png)

A aglutinação dos pedidos será feita quando estiverem no **mesmo grupo de campanha** ou quando **não possuírem um grupo configurado**.

### 5.1. Aglutinar apenas pedidos da mesma data

Para configurar a aglutinação dos pedidos por data, basta criar uma linha com a campanha `DATA` e o grupo `DATA`.

![Figura 19 - Configurar para aglutinar por data](imagens/figura-19.png)

### 5.2. Aglutinar pedidos sem onda gerada

Para configurar o sistema para que aglutine apenas pedidos sem onda gerada, crie uma linha com a campanha `ONDA` e o grupo `ONDA`.

![Figura 20 - Configurar aglutinação para pedidos sem onda](imagens/figura-20.png)
