# Configuração do Sistema – Tratamento de Leitura de Código de Barras e Identificação de Produto

## 1. Objetivo

Esta configuração define o comportamento do sistema para **leitura de códigos de barras, identificação de produtos, conversão de códigos EAN e conversão de unidades de medida** durante os processos de WMS.

O tratamento contempla diferentes formas de identificação do produto, respeitando uma ordem de pesquisa dos códigos cadastrados e regras específicas relacionadas ao cliente, filial, endereço e lote.

---

## 2. Parâmetros de Configuração

### 2.1 MV_XFILGRU (código da filial)

**Finalidade:**  
Realiza a conversão de grupo por cliente para localização do produto no apanhe, inventário ou endereçamento.

### Funcionamento

Inventário: Durante a localização do produto, o sistema consulta o **cliente vinculado à zona de armazenagem do endereço inventáriado** para determinar a qual cliente pertence o produto.

Endereçamento: No processo de **endereçamento sem documento**, o sistema consulta os produtos que possuem **saldo a endereçar** para o EAN informado na filial logada consultando o campo `A1_XCLIFIL` no cadastro do cliente.

### Regra

O produto somente poderá ser considerado para a filial corrente quando o vínculo do cliente com a filial for validado através do campo `A1_XCLIFIL`.

---

### 2.2 MV_XFILBAR (código da filial)

**Finalidade:**  
Restringe a localização do produto exclusivamente pela utilização do código de barras.

### Funcionamento

Quando habilitado, o sistema **não permite localizar o produto por outro código de identificação que não seja o código de barras**.

### Regra

> A localização do produto deve ocorrer obrigatoriamente por código de barras.

---

### 2.3 MV_XWMSCOL (código da filial)

**Finalidade:**  
Controla a atribuição da quantidade total durante o processo de apanhe.

### Funcionamento

Quando configurado, o sistema atribui **a quantidade total do produto no apanhe**.

### Regra

Ao realizar a identificação do produto durante o apanhe, a quantidade considerada para o processo corresponde à quantidade total definida para o apanhe.

---

### 2.4 MV_XCF1REC (código da filial)

**Finalidade:**  
Controla a apresentação da quantidade durante a conferência do recebimento.

### Funcionamento

Quando configurado, o sistema **não informa a quantidade durante a conferência do recebimento**.

### Regra

Durante a conferência do recebimento, a quantidade não é apresentada/informada pelo sistema.

---

# 3. Tratamento do EAN-14

## 3.1 Conversão automática EAN-14 para EAN-13

Quando o usuário realiza a leitura de um **EAN-14**, o sistema identifica o código e realiza automaticamente a conversão para **EAN-13**.

Após a conversão, a busca do produto é realizada utilizando o **EAN-13 convertido**.

### Fluxo

```text
EAN-14 informado
       ↓
Conversão para EAN-13
       ↓
Busca do produto pelo EAN-13
       ↓
Produto identificado
```

### Regra

> EAN-14 → conversão automática → EAN-13 → pesquisa do produto.

---

# 4. Ordem de Pesquisa do Produto

A identificação do produto através do código informado segue uma ordem específica de pesquisa.

O sistema realiza as pesquisas sequencialmente até localizar o produto.

## 4.1 Ordem das pesquisas

| Ordem | Campo | Descrição |
|---:|---|---|
| 1 | `B1_CODBAR` | Código de barras |
| 2 | `B1_CODCLAC` | Código CLAC |
| 3 | `B1_XUPC` | Código UPC |
| 4 | `B1_XDUN14` | Código DUN14 |

### Fluxo de identificação

```text
Código informado
       ↓
Pesquisa B1_CODBAR
       ↓
Encontrou?
 ┌─────┴─────┐
Sim         Não
 ↓           ↓
Produto    Pesquisa B1_CODCLAC
             ↓
          Encontrou?
        ┌─────┴─────┐
       Sim         Não
        ↓           ↓
     Produto     Pesquisa B1_XUPC / B1_XDUN14
                    ↓
                 Encontrou?
               ┌─────┴─────┐
              Sim         Não
               ↓           ↓
            Produto      Não localizado
```

---

# 5. Identificação pelo Código de Barras

A primeira tentativa de identificação do produto é realizada pelo campo:

`B1_CODBAR`

Caso o código informado seja localizado nesse campo, o sistema identifica o produto e encerra o processo de pesquisa.

### Regra

```text
Código informado
       ↓
B1_CODBAR
       ↓
Produto localizado
```

Caso não seja localizado, o sistema continua para a próxima forma de identificação.

---

# 6. Identificação pelo Código CLAC

Caso o produto não seja localizado pelo código de barras, o sistema realiza uma nova pesquisa utilizando o campo:

`B1_CODCLAC`

### Regra

```text
B1_CODBAR
   ↓
Não localizado
   ↓
B1_CODCLAC
```

Se o produto for localizado pelo código CLAC, a identificação é concluída.

---

# 7. Identificação pelo UPC / DUN14

Caso o produto também não seja localizado pelo código CLAC, o sistema realiza a pesquisa utilizando:

- `B1_XUPC` — código UPC;
- `B1_XDUN14` — código DUN14.

### Regra

```text
B1_CODBAR
     ↓
B1_CODCLAC
     ↓
B1_XUPC / B1_XDUN14
```

---

# 8. Conversão de Unidade de Medida

Quando o produto é localizado através do **UPC ou DUN14**, o sistema realiza uma validação adicional relacionada ao lote do produto.

O campo utilizado nessa validação é:

`B8_XQTPCX`

### Regra

Se o campo `B8_XQTPCX` estiver preenchido no lote do produto, o sistema realiza a **conversão da unidade de medida**.

### Fluxo

```text
Pesquisa UPC / DUN14
       ↓
Produto localizado
       ↓
Consulta lote do produto
       ↓
B8_XQTPCX está preenchido?
       ↓
      Sim
       ↓
Conversão da unidade de medida
```

### Exemplo conceitual

Um código UPC/DUN14 pode representar uma embalagem contendo múltiplas unidades do produto.

Nesse cenário, o campo `B8_XQTPCX` determina a quantidade utilizada para realizar a conversão da unidade de medida.

---

# 9. Fluxo Completo de Identificação

O processo completo pode ser representado da seguinte forma:

```text
Código de barras informado
          ↓
É EAN-14?
     ┌────┴────┐
    Sim       Não
     ↓          ↓
Converte      Mantém código
para EAN-13
     ↓          ↓
     └────┬─────┘
          ↓
Pesquisa B1_CODBAR
          ↓
      Encontrou?
     ┌────┴────┐
    Sim       Não
     ↓          ↓
  Produto    Pesquisa
             B1_CODCLAC
                  ↓
              Encontrou?
             ┌────┴────┐
            Sim       Não
             ↓          ↓
          Produto    Pesquisa
                     B1_XUPC /
                     B1_XDUN14
                          ↓
                      Encontrou?
                     ┌────┴────┐
                    Sim       Não
                     ↓          ↓
                  Produto    Produto não
                     ↓        localizado
              Consulta lote
                     ↓
              B8_XQTPCX
                preenchido?
                ┌────┴────┐
               Sim       Não
                ↓          ↓
             Converte    Mantém
             unidade     unidade
```

---

# 10. Resumo das Regras

| Configuração / Campo | Finalidade |
|---|---|
| `MV_XFILGRU` | Conversão de grupo por cliente e validação do cliente/filial durante a localização do produto. |
| `MV_XFILBAR` | Não permite localização do produto que não seja realizada pelo código de barras. |
| `MV_XWMSCOL` | Atribui a quantidade total no apanhe. |
| `MV_XCF1REC` | Não informa quantidade na conferência do recebimento. |
| `B1_CODBAR` | Primeira chave utilizada na pesquisa do produto. |
| `B1_CODCLAC` | Segunda chave utilizada na pesquisa do produto. |
| `B1_XUPC` | Código UPC utilizado na terceira etapa de pesquisa. |
| `B1_XDUN14` | Código DUN14 utilizado na terceira etapa de pesquisa. |
| `B8_XQTPCX` | Quantidade utilizada para conversão da unidade de medida quando o produto é localizado por UPC/DUN14. |
| `A1_XCLIFIL` | Define/valida o vínculo do cliente com a filial corrente. |

---

# 11. Regras de Negócio – Resumo

1. O sistema pode identificar produtos através de diferentes códigos.
2. A primeira pesquisa é realizada em `B1_CODBAR`.
3. Caso não seja localizado, a pesquisa é realizada em `B1_CODCLAC`.
4. Caso não seja localizado, a pesquisa é realizada em `B1_XUPC` e `B1_XDUN14`.
5. Ao informar um EAN-14, o sistema realiza a conversão automática para EAN-13 antes da pesquisa.
6. Quando o produto é localizado através de UPC ou DUN14, o sistema verifica o campo `B8_XQTPCX` no lote.
7. Se `B8_XQTPCX` estiver preenchido, é realizada a conversão da unidade de medida.
8. `MV_XFILGRU` controla o tratamento relacionado ao grupo por cliente e à identificação do cliente no inventário/endereço.
9. No endereçamento sem documento, são considerados os produtos com saldo a endereçar para o EAN informado.
10. O vínculo do cliente com a filial corrente é validado pelo campo `A1_XCLIFIL`.
11. `MV_XFILBAR` restringe a localização para utilização do código de barras.
12. `MV_XWMSCOL` atribui a quantidade total no apanhe.
13. `MV_XCF1REC` impede que a quantidade seja informada na conferência do recebimento.
"""
