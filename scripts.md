# Scripts MongoDB - Revendedora de Veículos Seminovos

Documento centralizado com todos os scripts utilizados no projeto, organizados pela checklist de 31 itens, mais operações extras de inserção, atualização e remoção.

---

## BLOCO 1 - Itens 1 e 19: USE e PRETTY

### Item 1 - USE
Seleciona o banco de dados que vamos trabalhar.

```javascript
use revendedora
```

### Item 19 - PRETTY
Formata a saída para ficar mais legível.

```javascript
db.veiculos.find().pretty()
```

---

## BLOCO 2 - Itens 2, 6 e 30: FIND, PROJECT e FINDONE

### Itens 2 e 6 - FIND com PROJECT
Busca todos os veículos da categoria "SUV", retornando apenas marca, modelo e preço.

```javascript
db.veiculos.find(
  { categoria: "SUV" },
  { marca: 1, modelo: 1, preco: 1, _id: 0 }
)
```

### Item 30 - FINDONE
Retorna apenas o primeiro documento que atende ao filtro.

```javascript
db.veiculos.findOne({ marca: "Toyota" })
```

---

## BLOCO 3 - Itens 7, 14 e 15: $GTE, SORT e LIMIT

### Consulta combinada - Os 5 veículos mais caros acima de R$ 100.000

```javascript
db.veiculos.find(
  { preco: { $gte: 100000 } },
  { marca: 1, modelo: 1, preco: 1, _id: 0 }
).sort({ preco: -1 }).limit(5)
```

**O que cada parte demonstra:**
- `$gte: 100000` → **Item 7** (filtro: preço maior ou igual a 100 mil)
- `.sort({ preco: -1 })` → **Item 14** (ordena por preço decrescente)
- `.limit(5)` → **Item 15** (limita a 5 resultados)

---

## BLOCO 4 - Itens 3, 13 e 20: SIZE, EXISTS e ALL

### Consulta combinada - Veículos com teto solar E rodas de liga (e exatamente 7 opcionais)

```javascript
db.veiculos.find(
  {
    opcionais: { $all: ["teto solar", "rodas de liga"], $size: 7 },
    descricao: { $exists: true }
  },
  { marca: 1, modelo: 1, opcionais: 1, _id: 0 }
)
```

**O que cada parte demonstra:**
- `$all: ["teto solar", "rodas de liga"]` → **Item 20** (array contém todos esses elementos)
- `$size: 7` → **Item 3** (array tem exatamente 7 elementos)
- `$exists: true` → **Item 13** (campo descricao existe no documento)

---

## BLOCO 5 - Itens 4, 5, 8 e 9: AGGREGATE, MATCH, GROUP e SUM

### Consulta combinada - Total de vendas por forma de pagamento (vendas ≥ R$ 50.000)

```javascript
db.vendas.aggregate([
  { $match: { preco_final: { $gte: 50000 } } },
  { $group: {
      _id: "$forma_pagamento",
      total_arrecadado: { $sum: "$preco_final" },
      quantidade_vendas: { $sum: 1 }
    }
  }
])
```

**O que cada parte demonstra:**
- `db.vendas.aggregate([...])` → **Item 4** (pipeline de agregação)
- `$match` → **Item 5** (filtra antes de agrupar)
- `$group` → **Item 8** (agrupa por forma_pagamento)
- `$sum: "$preco_final"` → **Item 9** (soma os valores de cada grupo)

---

## BLOCO 6 - Itens 10, 11 e 12: COUNTDOCUMENTS, MAX e AVG

### Consulta 1 - Item 10 (COUNTDOCUMENTS)
Conta quantos veículos estão disponíveis no estoque.

```javascript
db.veiculos.countDocuments({ status: "disponivel" })
```

### Consulta 2 - Itens 11 e 12 (MAX e AVG)
Preço máximo, médio e quantidade de veículos por categoria.

```javascript
db.veiculos.aggregate([
  { $group: {
      _id: "$categoria",
      preco_maximo: { $max: "$preco" },
      preco_medio: { $avg: "$preco" },
      total_veiculos: { $sum: 1 }
    }
  }
])
```

**O que cada parte demonstra:**
- `$max: "$preco"` → **Item 11** (maior preço de cada categoria)
- `$avg: "$preco"` → **Item 12** (preço médio de cada categoria)

---

## BLOCO 7 - Itens 16, 17 e 18: $WHERE, MAPREDUCE e FUNCTION

### Consulta 1 - Item 16 ($WHERE)
Busca veículos cujo ano_modelo é posterior ao ano_fabricacao.

```javascript
db.veiculos.find({ $where: "this.ano_modelo - this.ano_fabricacao > 0" }, { marca: 1, modelo: 1, ano_fabricacao: 1, ano_modelo: 1, _id: 0 })
```

### Consulta 2 - Itens 17 e 18 (MAPREDUCE e FUNCTION)
Calcula o total arrecadado em vendas por vendedor usando map-reduce.

```javascript
db.vendas.mapReduce(function() { emit(this.vendedor_id, this.preco_final); }, function(key, values) { return Array.sum(values); }, { out: "total_por_vendedor" })
```

Para visualizar o resultado:
```javascript
db.total_por_vendedor.find()
```

**O que cada parte demonstra:**
- `mapReduce` → **Item 17**
- As duas `function()` → **Item 18** (função JavaScript: a primeira mapeia, a segunda reduz/soma)

---

## BLOCO 8 - Itens 22 e 23: $TEXT e $SEARCH

### Passo 1 - Criar índice de texto (obrigatório antes da busca)

```javascript
db.veiculos.createIndex({ descricao: "text" })
```

### Passo 2 - Buscar por palavras-chave

```javascript
db.veiculos.find(
  { $text: { $search: "automático diesel" } },
  { marca: 1, modelo: 1, descricao: 1, _id: 0 }
)
```

**O que cada parte demonstra:**
- `$text` → **Item 22** (busca em índice de texto)
- `$search: "automático diesel"` → **Item 23** (termos de busca)

---

## BLOCO 9 - Itens 24, 28 e 29: $FILTER, $COND e $LOOKUP

### Consulta combinada — Vendas com dados de cliente e veículo, categoria de venda e opcionais premium

```javascript
db.vendas.aggregate([
  { $lookup: { from: "veiculos", localField: "veiculo_id", foreignField: "_id", as: "veiculo" } },
  { $lookup: { from: "clientes", localField: "cliente_id", foreignField: "_id", as: "cliente" } },
  { $project: {
      _id: 0,
      cliente_nome: { $arrayElemAt: ["$cliente.nome", 0] },
      veiculo_marca: { $arrayElemAt: ["$veiculo.marca", 0] },
      veiculo_modelo: { $arrayElemAt: ["$veiculo.modelo", 0] },
      preco_final: 1,
      categoria_venda: {
        $cond: { if: { $gte: ["$preco_final", 100000] }, then: "Alto Valor", else: "Padrão" }
      },
      opcionais_premium: {
        $filter: {
          input: { $arrayElemAt: ["$veiculo.opcionais", 0] },
          as: "op",
          cond: { $in: ["$$op", ["couro", "teto solar", "tração 4x4"]] }
        }
      }
  }}
])
```

**O que cada parte demonstra:**
- `$lookup` → **Item 29** (join entre coleções - vendas com veículos e clientes)
- `$cond` → **Item 28** (operador condicional - classifica venda como "Alto Valor" ou "Padrão")
- `$filter` → **Item 24** (filtra apenas opcionais premium dentro do array)

---

## BLOCO 10 - Itens 21, 25 e 31: $SET, UPDATEMANY e $ADDTOSET

### Consulta combinada - Reajusta SUVs em 3% e adiciona opcional "alarme"

```javascript
db.veiculos.updateMany(
  { categoria: "SUV" },
  {
    $set: { ultimo_reajuste: new Date() },
    $mul: { preco: 1.03 },
    $addToSet: { opcionais: "alarme" }
  }
)
```

**O que cada parte demonstra:**
- `updateMany` → **Item 25** (atualiza vários documentos - substitui o update depreciado)
- `$set` → **Item 21** (adiciona/atualiza o campo ultimo_reajuste)
- `$addToSet` → **Item 31** (adiciona "alarme" ao array sem duplicar)

Para verificar o resultado:
```javascript
db.veiculos.find({ categoria: "SUV" }, { marca: 1, modelo: 1, preco: 1, opcionais: 1, ultimo_reajuste: 1, _id: 0 })
```

---

## BLOCO 11 - Item 26: INSERTONE

Substitui o `save()` depreciado. Insere um único documento novo.

```javascript
db.veiculos.insertOne({
  marca: "Peugeot",
  modelo: "208",
  ano_fabricacao: 2022,
  ano_modelo: 2023,
  cor: "Cinza",
  quilometragem: 8500,
  preco: 89000.00,
  categoria: "hatch",
  opcionais: ["ar-condicionado", "câmera de ré", "bluetooth", "sensor de estacionamento"],
  num_donos_anteriores: 1,
  status: "disponivel",
  descricao: "Peugeot 208 Allure turbo, praticamente zero, ideal para quem busca conforto europeu"
})
```

---

## BLOCO 12 - Item 27: RENAMECOLLECTION

Renomeia uma coleção existente.

```javascript
db.total_por_vendedor.renameCollection("ranking_vendedores")
```

Para verificar que os dados foram preservados:
```javascript
db.ranking_vendedores.find()
```

---

## BLOCO 13 - Operações de remoção (exigido pelo PDF)

### Consulta 1 - deleteOne
Remove um único documento.

```javascript
db.veiculos.deleteOne({ marca: "Peugeot", modelo: "208" })
```

### Consulta 2 - deleteMany
Remove vários documentos. Aqui removemos avaliações que foram reprovadas.

```javascript
db.avaliacoes.deleteMany({ aprovada: false })
```

---

## Resumo da cobertura dos 31 itens da checklist

| # | Item | Bloco |
|---|---|---|
| 1 | USE | 1 |
| 2 | FIND | 2 |
| 3 | SIZE | 4 |
| 4 | AGGREGATE | 5 |
| 5 | MATCH | 5 |
| 6 | PROJECT | 2 |
| 7 | GTE | 3 |
| 8 | GROUP | 5 |
| 9 | SUM | 5 |
| 10 | COUNTDOCUMENTS | 6 |
| 11 | MAX | 6 |
| 12 | AVG | 6 |
| 13 | EXISTS | 4 |
| 14 | SORT | 3 |
| 15 | LIMIT | 3 |
| 16 | $WHERE | 7 |
| 17 | MAPREDUCE | 7 |
| 18 | FUNCTION | 7 |
| 19 | PRETTY | 1 |
| 20 | ALL | 4 |
| 21 | SET | 10 |
| 22 | TEXT | 8 |
| 23 | SEARCH | 8 |
| 24 | FILTER | 9 |
| 25 | UPDATEMANY | 10 |
| 26 | INSERTONE | 11 |
| 27 | RENAMECOLLECTION | 12 |
| 28 | COND | 9 |
| 29 | LOOKUP | 9 |
| 30 | FINDONE | 2 |
| 31 | ADDTOSET | 10 |

**Operações adicionais exigidas pelo PDF:**
- Inserção: `insertMany()` (povoamento das 7 coleções) e `insertOne()` (item 26)
- Atualização: `updateMany()` (item 25)
- Remoção: `deleteOne()` e `deleteMany()` (Bloco 13)