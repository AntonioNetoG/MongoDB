# 🚗 Banco de Dados NoSQL: Revendedora de Veículos Seminovos

**Projeto da Disciplina de Banco de Dados (2026.1) \- CIn/UFPE**

Este projeto implementa um banco de dados NoSQL orientado a documentos no **MongoDB** para gerenciar as operações de uma revendedora de veículos seminovos. O banco modela entidades como clientes, veículos, vendedores, mecânicos, avaliações, serviços e vendas, e demonstra na prática **31 operações e funcionalidades** da linguagem de consulta do MongoDB.

O repositório está organizado em dois entregáveis principais: o **script de povoamento** (inserção dos dados nas 7 coleções) e o **script de consultas** (cobertura dos 31 itens da checklist).

---

## 🎯 Objetivo e Domínio

O objetivo foi modelar e explorar um domínio real e relacional em um banco de dados orientado a documentos, evidenciando as diferenças de abordagem em relação ao modelo relacional tradicional.

- **SGBD:** MongoDB (shell)  
- **Banco de dados:** `revendedora`  
- **Coleções:** `clientes`, `vendedores`, `mecanicos`, `veiculos`, `avaliacoes`, `servicos`, `vendas`  
- **Desafio principal:** Modelar referências entre coleções sem chaves estrangeiras nativas, garantir integridade referencial no momento da inserção e demonstrar consultas complexas com pipelines de agregação, `$lookup` entre coleções, busca textual e MapReduce.

---

## 📄 Relatório do Projeto

A documentação completa do projeto pode ser acessada através do relatório técnico:

📑 **[Acessar Relatório Completo](https://docs.google.com/document/d/1K1IpNMqdNIA0eralQpZFZKm2GBabNmXgd-kpNHkQTos/edit?tab=t.0)**

---

## 🗄️ Estrutura das Coleções

O banco `revendedora` é composto por **7 coleções** com um total de **538 documentos**:

| Coleção | Documentos | Descrição |
| :---- | :---: | :---- |
| `clientes` | 150 | Dados cadastrais e preferências dos compradores |
| `veiculos` | 100 | Características, opcionais, preço e status de cada veículo |
| `vendedores` | 8 | Cadastro dos consultores de venda |
| `mecanicos` | 10 | Cadastro dos mecânicos responsáveis por avaliações e serviços |
| `avaliacoes` | 80 | Avaliações técnicas de veículos, vinculadas a clientes e mecânicos |
| `servicos` | 120 | Serviços realizados nos veículos, vinculados a mecânicos |
| `vendas` | 70 | Registro das transações de venda, vinculadas a veículos, clientes e vendedores |

**Atenção:** As coleções `avaliacoes`, `servicos` e `vendas` referenciam documentos das demais coleções. Os IDs são resolvidos em tempo real com `db.colecao.findOne({...})._id`, garantindo referências corretas sem IDs hardcoded.

---

## 📋 Scripts do Projeto

### 1\. Povoamento (`povoamento.md`)

Contém todos os `insertMany()` necessários para popular as 7 coleções na ordem correta de dependência. Deve ser executado integralmente antes dos scripts de consulta.

**Ordem obrigatória de execução:**

1\. clientes    → independente

2\. vendedores  → independente

3\. mecanicos   → independente

4\. veiculos    → independente

5\. avaliacoes  → depende de clientes e mecanicos

6\. servicos    → depende de veiculos e mecanicos

7\. vendas      → depende de veiculos, clientes e vendedores

**Exemplo de inserção com referência dinâmica (`vendas`):**

db.vendas.insertMany(\[

  {

    veiculo\_id:  db.veiculos.findOne({ marca: "Toyota", modelo: "Corolla" }).\_id,

    cliente\_id:  db.clientes.findOne({ nome: "Ana Paula Ferreira" }).\_id,

    vendedor\_id: db.vendedores.findOne({ nome: "Fernanda Lira" }).\_id,

    preco\_final: 89500.00,

    forma\_pagamento: "financiamento",

    parcelas: 36,

    data\_venda: new Date("2024-03-10"),

    observacoes: "Financiamento pelo Itaú com entrada negociada"

  }

  // ...

\])

---

### 2\. Consultas (`scripts.md`)

Cobre os **31 itens obrigatórios** da checklist, organizados em 13 blocos temáticos. Cada bloco combina operadores relacionados em uma única consulta expressiva, além de demonstrá-los individualmente quando necessário.

**Visão geral dos 31 itens cobertos:**

| \# | Item | Bloco |
| :---: | :---- | :---: |
| 1 | `USE` | 1 |
| 2 | `FIND` | 2 |
| 3 | `$SIZE` | 4 |
| 4 | `AGGREGATE` | 5 |
| 5 | `$MATCH` | 5 |
| 6 | `PROJECT` | 2 |
| 7 | `$GTE` | 3 |
| 8 | `$GROUP` | 5 |
| 9 | `$SUM` | 5 |
| 10 | `COUNTDOCUMENTS` | 6 |
| 11 | `$MAX` | 6 |
| 12 | `$AVG` | 6 |
| 13 | `$EXISTS` | 4 |
| 14 | `SORT` | 3 |
| 15 | `LIMIT` | 3 |
| 16 | `$WHERE` | 7 |
| 17 | `MAPREDUCE` | 7 |
| 18 | `FUNCTION` | 7 |
| 19 | `PRETTY` | 1 |
| 20 | `$ALL` | 4 |
| 21 | `$SET` | 10 |
| 22 | `$TEXT` | 8 |
| 23 | `$SEARCH` | 8 |
| 24 | `$FILTER` | 9 |
| 25 | `UPDATEMANY` | 10 |
| 26 | `INSERTONE` | 11 |
| 27 | `RENAMECOLLECTION` | 12 |
| 28 | `$COND` | 9 |
| 29 | `$LOOKUP` | 9 |
| 30 | `FINDONE` | 2 |
| 31 | `$ADDTOSET` | 10 |

**Operações adicionais exigidas:** `insertMany()` (povoamento), `deleteOne()` e `deleteMany()` (Bloco 13).

---

## 🚀 Como Executar

### Pré-requisitos

1. Tenha o **MongoDB** instalado e o serviço `mongod` em execução.  
2. Acesse o shell interativo:  
     
   mongosh

### Passo 1 - Povoamento

Execute o script de povoamento **na ordem das seções**. Todas as inserções devem ser realizadas com o banco `revendedora` selecionado:

use revendedora

// Execute cada bloco do script de povoamento em sequência

### Passo 2 - Consultas

Com o banco populado, execute os blocos do script de consultas:

use revendedora

// Execute os blocos conforme necessário

**Atenção para o Bloco 8:** A busca textual (`$text` / `$search`) exige a criação prévia de um índice. Execute o `createIndex` antes da consulta:

db.veiculos.createIndex({ descricao: "text" })

**Atenção para o Bloco 7:** O resultado do `mapReduce` é gravado na coleção `total_por_vendedor`. O Bloco 12 a renomeia para `ranking_vendedores`. Execute os blocos em ordem para evitar erros de referência.

---

## 🛠️ Tecnologias Utilizadas

- 🍃 **MongoDB** \- SGBD NoSQL orientado a documentos  
- 🖥️ **mongosh** \- Shell interativo do MongoDB  
- 🐍 **JavaScript** \- Linguagem nativa das operações MongoDB (funções, MapReduce)

---

## 👥 Equipe

| Login | Nome |
| :---- | :---- |
| agan | Antonio Gonçalves de Albuquerque Neto |
| dcms3 | Daniel Cavalcanti da Motta Silveira |
| fam3 | Felipe de Aquino Mulato |
| gmtbn | Gabriel Mezzalira Teixeira Batista do Nascimento |
| iccs | Iago Coutinho da Costa e Silva |
| laco | Leonardo Alves Cavalcanti de Oliveira |

---

*Projeto desenvolvido para a disciplina de Banco de Dados \- CIn/UFPE, 2026.1.*  
