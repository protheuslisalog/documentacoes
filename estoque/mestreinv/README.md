<!-- PADRAO-LISA -->
<p align="center">
  <img src="../../imagens/banner-lisa.png" alt="Lisa Logística Integrada Sulamericana — Documentação de Sistemas" width="100%">
</p>

<h1 align="center">Criação de Mestre de Inventário por Arquivo</h1>
<p align="center"><b>Estoque</b> · Lisa Logística Integrada Sulamericana</p>

[⬅ Voltar ao índice](../../README.md)

---

## Sumário

- [1. Gerando o arquivo para criação dos mestres](#1-gerando-o-arquivo-para-criação-dos-mestres)
- [2. Acessando a rotina](#2-acessando-a-rotina)
- [3. Criando os mestres](#3-criando-os-mestres)
- [4. Processando o arquivo CSV](#4-processando-o-arquivo-csv)
- [5. Resultado do processamento](#5-resultado-do-processamento)

---

## 1. Gerando o arquivo para criação dos mestres

1. Abra uma planilha no Excel.
2. Preencha:
   - **Primeira coluna:** o armazém.
   - **Segunda coluna:** os endereços.

<p align="center">
  <img src="imagens/Imagem1.png" alt="Planilha com armazém e endereços"><br>
  <sub><b>Figura 1</b> — Planilha com armazém e endereços</sub>
</p>

3. Salve o arquivo do Excel como **.CSV** em uma pasta do computador (por exemplo, `C:\`).

<p align="center">
  <img src="imagens/Imagem2.png" alt="Salvando a planilha em CSV"><br>
  <sub><b>Figura 2</b> — Salvando a planilha em CSV</sub>
</p>

---

## 2. Acessando a rotina

Pesquise por **Mestre** ou acesse:

**Estoque/Custos > Inventário > Mestre**

<p align="center">
  <img src="imagens/Imagem3.png" alt="Acesso à rotina Mestre de Inventário"><br>
  <sub><b>Figura 3</b> — Acesso à rotina Mestre de Inventário</sub>
</p>

---

## 3. Criando os mestres

Acesse **Outras Ações > Automático > Gera Mestre > Endereço**.

<p align="center">
  <img src="imagens/Imagem4.png" alt="Outras Ações, Automático, Gera Mestre"><br>
  <sub><b>Figura 4</b> — Outras Ações › Automático › Gera Mestre</sub>
</p>

### 3.1 Parâmetros

Na tela de geração automática:

<p align="center">
  <img src="imagens/Imagem5.png" alt="Tela de geração automática"><br>
  <sub><b>Figura 5</b> — Tela de geração automática</sub>
</p>

| Campo | O que informar |
|---|---|
| **Geração Automática** | Selecione a opção correspondente. |
| **Gera Mestre** | Selecione **Endereço**. |

<p align="center">
  <img src="imagens/Imagem6.png" alt="Gera Mestre por Endereço"><br>
  <sub><b>Figura 6</b> — Gera Mestre por Endereço</sub>
</p>

Informe os parâmetros necessários:

<p align="center">
  <img src="imagens/Imagem7.png" alt="Parâmetros da geração"><br>
  <sub><b>Figura 7</b> — Parâmetros da geração</sub>
</p>

<p align="center">
  <img src="imagens/Imagem8.png" alt="Parâmetros da geração, continuação"><br>
  <sub><b>Figura 8</b> — Parâmetros da geração (continuação)</sub>
</p>

> ⚠️ **Ponto de atenção:** os endereços do arquivo CSV precisam estar dentro da faixa informada nos parâmetros **Endereço de?** e **Endereço até?**.

---

## 4. Processando o arquivo CSV

1. Clique em **Sim**.

<p align="center">
  <img src="imagens/Imagem9.png" alt="Mensagem de confirmação"><br>
  <sub><b>Figura 9</b> — Mensagem de confirmação</sub>
</p>

2. Altere o tipo da busca para **CSV**.
3. Selecione o arquivo CSV.
4. Clique em **Salvar**.

<p align="center">
  <img src="imagens/Imagem10.png" alt="Selecionando o arquivo CSV"><br>
  <sub><b>Figura 10</b> — Selecionando o arquivo CSV</sub>
</p>

---

## 5. Resultado do processamento

Ao final do processamento é exibida uma mensagem informando:

- os endereços encontrados;
- os endereços criados com sucesso.

---

[⬅ Voltar ao índice](../../README.md)

<p align="center">
  <img src="../../imagens/logo-lisa.png" alt="Lisa" width="110"><br>
  <sub>Lisa Logística Integrada Sulamericana · Tecnologia da Informação</sub>
</p>
