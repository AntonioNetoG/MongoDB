# Scripts de Povoamento - Revendedora de Veículos Seminovos

Documento com todos os scripts utilizados para popular as 7 coleções do banco `revendedora`. Os scripts devem ser executados na ordem apresentada, pois as coleções de avaliações, serviços e vendas dependem dos IDs das demais.

> **Observação importante:** As coleções `avaliacoes`, `servicos` e `vendas` foram inseridas usando `db.colecao.findOne({nome: "..."})._id` para buscar IDs em tempo real, garantindo referências corretas entre coleções e evitando problemas de IDs hardcoded.

---

## BLOCO 0 - Selecionar/criar o banco de dados

```javascript
use revendedora
```

---

## BLOCO 1 - Coleção `clientes` (150 documentos)

```javascript
db.clientes.insertMany([
  {
    nome: "Ana Paula Ferreira",
    cpf: "123.456.789-00",
    telefone: "(81) 98801-1111",
    email: "ana.ferreira@gmail.com",
    endereco: {
      rua: "Rua das Flores",
      numero: "142",
      bairro: "Boa Viagem",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-03-15"),
    observacoes: "Cliente interessada em SUVs com baixa quilometragem"
  },
  {
    nome: "Bruno Cavalcanti",
    cpf: "234.567.890-11",
    telefone: "(81) 98802-2222",
    email: "bruno.cavalcanti@hotmail.com",
    endereco: {
      rua: "Avenida Agamenon Magalhães",
      numero: "800",
      bairro: "Derby",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-05-20"),
    observacoes: "Prefere veículos com financiamento facilitado"
  },
  {
    nome: "Carla Nunes Rodrigues",
    cpf: "345.678.901-22",
    telefone: "(81) 98803-3333",
    email: "carla.nunes@yahoo.com",
    endereco: {
      rua: "Rua do Riachuelo",
      numero: "55",
      bairro: "Santo Antônio",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-07-08"),
    observacoes: "Busca hatch econômico para uso urbano"
  },
  {
    nome: "Diego Albuquerque",
    cpf: "456.789.012-33",
    telefone: "(81) 98804-4444",
    email: "diego.albuquerque@gmail.com",
    endereco: {
      rua: "Rua Padre Carapuceiro",
      numero: "320",
      bairro: "Boa Viagem",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-09-12"),
    observacoes: "Quer trocar seu carro atual por uma pickup"
  },
  {
    nome: "Eduarda Lima Santos",
    cpf: "567.890.123-44",
    telefone: "(81) 98805-5555",
    email: "eduarda.lima@gmail.com",
    endereco: {
      rua: "Avenida Caxangá",
      numero: "1200",
      bairro: "Caxangá",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-11-30"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Felipe Monteiro",
    cpf: "678.901.234-55",
    telefone: "(81) 98806-6666",
    email: "felipe.monteiro@outlook.com",
    endereco: {
      rua: "Rua Marquês do Herval",
      numero: "78",
      bairro: "Madalena",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-01-17"),
    observacoes: "Interessado em sedans executivos de até 60 mil reais"
  },
  {
    nome: "Gabriela Vasconcelos",
    cpf: "789.012.345-66",
    telefone: "(81) 98807-7777",
    email: "gabriela.vasconcelos@gmail.com",
    endereco: {
      rua: "Rua Benfica",
      numero: "410",
      bairro: "Benfica",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-02-25"),
    observacoes: "Busca veículo para toda a família, com espaço e conforto"
  },
  {
    nome: "Henrique Barros",
    cpf: "890.123.456-77",
    telefone: "(81) 98808-8888",
    email: "henrique.barros@gmail.com",
    endereco: {
      rua: "Avenida Boa Viagem",
      numero: "2500",
      bairro: "Boa Viagem",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-04-10"),
    observacoes: "Cliente fidelizado, já comprou dois veículos anteriormente"
  },
  {
    nome: "Isabela Correia",
    cpf: "901.234.567-88",
    telefone: "(81) 98809-9999",
    email: "isabela.correia@hotmail.com",
    endereco: {
      rua: "Rua Visconde de Jequitinhonha",
      numero: "190",
      bairro: "Boa Viagem",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-05-14"),
    observacoes: "Prefere veículos automáticos com câmera de ré"
  },
  {
    nome: "João Pedro Melo",
    cpf: "012.345.678-99",
    telefone: "(81) 98810-0000",
    email: "joao.melo@gmail.com",
    endereco: {
      rua: "Rua da Aurora",
      numero: "33",
      bairro: "Boa Vista",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-06-22"),
    observacoes: "Motorista de aplicativo, busca veículo econômico e confortável"
  },
  {
    nome: "Larissa Freitas",
    cpf: "111.222.333-00",
    telefone: "(81) 98811-1010",
    email: "larissa.freitas@gmail.com",
    endereco: {
      rua: "Rua Ernesto de Paula Santos",
      numero: "620",
      bairro: "Boa Viagem",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-07-05"),
    observacoes: "Interesse em veículos com teto solar"
  },
  {
    nome: "Marcos Vinícius Prado",
    cpf: "222.333.444-11",
    telefone: "(81) 98812-2020",
    email: "marcos.prado@outlook.com",
    endereco: {
      rua: "Estrada do Arraial",
      numero: "950",
      bairro: "Casa Amarela",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-08-19"),
    observacoes: "Procura pickup para uso em fazenda no interior"
  },
  {
    nome: "Natália Souza",
    cpf: "333.444.555-22",
    telefone: "(81) 98813-3030",
    email: "natalia.souza@gmail.com",
    endereco: {
      rua: "Rua Amélia",
      numero: "88",
      bairro: "Graças",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-09-30"),
    observacoes: "Quer veículo com até 50 mil km rodados"
  },
  {
    nome: "Otávio Ramos",
    cpf: "444.555.666-33",
    telefone: "(81) 98814-4040",
    email: "otavio.ramos@gmail.com",
    endereco: {
      rua: "Rua José Osório",
      numero: "215",
      bairro: "Afogados",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-10-11"),
    observacoes: "Busca minivan para transporte escolar"
  },
  {
    nome: "Priscila Andrade",
    cpf: "555.666.777-44",
    telefone: "(81) 98815-5050",
    email: "priscila.andrade@yahoo.com",
    endereco: {
      rua: "Avenida Norte",
      numero: "1750",
      bairro: "Encruzilhada",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-11-02"),
    observacoes: "Interessada em veículos flex com bom custo-benefício"
  },
  {
    nome: "Lara Carvalho Santos",
    cpf: "859.381.350-38",
    telefone: "(81) 98285-2679",
    email: "lara.siqueira55@gmail.com",
    endereco: {
      rua: "Avenida Conde da Boa Vista",
      numero: "132",
      bairro: "Graças",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-04-17"),
    observacoes: "Interessado em financiamento com entrada facilitada"
  },
  {
    nome: "Gustavo Albuquerque Almeida",
    cpf: "833.765.818-79",
    telefone: "(81) 98859-4611",
    email: "gustavo.siqueira36@yahoo.com",
    endereco: {
      rua: "Rua do Futuro",
      numero: "36",
      bairro: "Torre",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-06-09"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "Breno Magalhães Cardoso",
    cpf: "204.194.489-22",
    telefone: "(81) 98735-6635",
    email: "breno.oliveira94@outlook.com",
    endereco: {
      rua: "Avenida 17 de Agosto",
      numero: "2206",
      bairro: "Casa Forte",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-02-18"),
    observacoes: "Interesse em pickup para trabalho no interior"
  },
  {
    nome: "Joana Maciel Nunes",
    cpf: "691.296.821-18",
    telefone: "(81) 98093-4733",
    email: "joana.pereira30@outlook.com",
    endereco: {
      rua: "Avenida Parnamirim",
      numero: "423",
      bairro: "Santo Amaro",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-08-21"),
    observacoes: "Quer trocar veículo atual por um mais novo"
  },
  {
    nome: "Yuri Martins Nunes",
    cpf: "463.314.786-44",
    telefone: "(81) 99437-2169",
    email: "yuri.wanderley94@hotmail.com",
    endereco: {
      rua: "Rua Barão de Souza Leão",
      numero: "679",
      bairro: "Benfica",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-05-21"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Aline Araújo Galvão",
    cpf: "432.963.886-17",
    telefone: "(81) 98469-1525",
    email: "aline.freitas35@outlook.com",
    endereco: {
      rua: "Rua do Espinheiro",
      numero: "874",
      bairro: "Rosarinho",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-11-16"),
    observacoes: "Cliente fidelizado, já adquiriu veículo anteriormente"
  },
  {
    nome: "Manuela Vieira Ribeiro",
    cpf: "371.242.352-81",
    telefone: "(81) 99103-5304",
    email: "manuela.siqueira52@yahoo.com",
    endereco: {
      rua: "Rua João de Barros",
      numero: "908",
      bairro: "Parnamirim",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-02-25"),
    observacoes: "Cliente interessado em SUVs compactos com baixo consumo"
  },
  {
    nome: "Igor Ribeiro Brandão",
    cpf: "263.911.796-64",
    telefone: "(81) 99221-2040",
    email: "igor.mendes77@yahoo.com",
    endereco: {
      rua: "Avenida 17 de Agosto",
      numero: "2177",
      bairro: "Afogados",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-11-24"),
    observacoes: "Procura sedan automático para uso familiar"
  },
  {
    nome: "Talita Wanderley Magalhães",
    cpf: "373.887.756-53",
    telefone: "(81) 98228-5808",
    email: "talita.martins59@yahoo.com",
    endereco: {
      rua: "Rua Real da Torre",
      numero: "1088",
      bairro: "Dois Irmãos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-09-04"),
    observacoes: "Quer trocar veículo atual por um mais novo"
  },
  {
    nome: "Joana Fernandes Brandão",
    cpf: "619.723.303-29",
    telefone: "(81) 98765-3646",
    email: "joana.lacerda42@gmail.com",
    endereco: {
      rua: "Rua Dona Benvinda de Farias",
      numero: "89",
      bairro: "Casa Forte",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-05-08"),
    observacoes: "Cliente interessado em SUVs compactos com baixo consumo"
  },
  {
    nome: "Enzo Vasconcelos Pereira",
    cpf: "187.849.597-18",
    telefone: "(81) 99557-9727",
    email: "enzo.gomes85@hotmail.com",
    endereco: {
      rua: "Rua Dona Benvinda de Farias",
      numero: "2261",
      bairro: "Torre",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-09-28"),
    observacoes: "Interessado em financiamento com entrada facilitada"
  },
  {
    nome: "Elaine Nascimento Wanderley",
    cpf: "873.847.806-35",
    telefone: "(81) 99460-6107",
    email: "elaine.falcão84@yahoo.com",
    endereco: {
      rua: "Rua João de Barros",
      numero: "1804",
      bairro: "Apipucos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-02-08"),
    observacoes: "Prefere veículos com câmbio automático e câmera de ré"
  },
  {
    nome: "Caio Cardoso Santos",
    cpf: "702.667.335-85",
    telefone: "(81) 98451-1117",
    email: "caio.ítalo81@gmail.com",
    endereco: {
      rua: "Avenida Conde da Boa Vista",
      numero: "947",
      bairro: "Espinheiro",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-06-03"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Enzo Dias Falcão",
    cpf: "597.319.652-26",
    telefone: "(81) 99481-8744",
    email: "enzo.macedo53@hotmail.com",
    endereco: {
      rua: "Rua Setúbal",
      numero: "396",
      bairro: "Aflitos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-06-14"),
    observacoes: "Cliente fidelizado, já adquiriu veículo anteriormente"
  },
  {
    nome: "Júlia Justino Souza",
    cpf: "789.769.761-22",
    telefone: "(81) 98124-7596",
    email: "julia.costa32@outlook.com",
    endereco: {
      rua: "Rua Setúbal",
      numero: "789",
      bairro: "Jaqueira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-07-06"),
    observacoes: "Interesse em pickup para trabalho no interior"
  },
  {
    nome: "Júlia Barbosa Lima",
    cpf: "553.927.982-80",
    telefone: "(81) 98200-1828",
    email: "julia.pereira97@gmail.com",
    endereco: {
      rua: "Avenida Parnamirim",
      numero: "978",
      bairro: "Torre",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-08-16"),
    observacoes: "Prefere veículos com câmbio automático e câmera de ré"
  },
  {
    nome: "Beatriz Souza Martins",
    cpf: "488.102.499-43",
    telefone: "(81) 99897-8454",
    email: "beatriz.pinto90@outlook.com",
    endereco: {
      rua: "Rua Gervásio Pires",
      numero: "2286",
      bairro: "Várzea",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-04-10"),
    observacoes: "Prefere veículos com câmbio automático e câmera de ré"
  },
  {
    nome: "Bruno Siqueira Lobo",
    cpf: "655.162.865-50",
    telefone: "(81) 98117-1821",
    email: "bruno.bezerra68@yahoo.com",
    endereco: {
      rua: "Avenida Domingos Ferreira",
      numero: "242",
      bairro: "Dois Irmãos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-03-03"),
    observacoes: "Interessado em financiamento com entrada facilitada"
  },
  {
    nome: "Caio Galvão Barbosa",
    cpf: "513.222.683-41",
    telefone: "(81) 99185-1651",
    email: "caio.cunha85@gmail.com",
    endereco: {
      rua: "Avenida Mário Melo",
      numero: "2325",
      bairro: "Apipucos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-05-07"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Carolina Moreira Barbosa",
    cpf: "371.505.234-95",
    telefone: "(81) 99321-5915",
    email: "carolina.moreira97@yahoo.com",
    endereco: {
      rua: "Rua Manoel de Carvalho",
      numero: "307",
      bairro: "Boa Viagem",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-10-19"),
    observacoes: "Procura sedan automático para uso familiar"
  },
  {
    nome: "Daniel Wanderley Nascimento",
    cpf: "618.371.235-54",
    telefone: "(81) 99804-2127",
    email: "daniel.nunes37@hotmail.com",
    endereco: {
      rua: "Avenida Domingos Ferreira",
      numero: "1804",
      bairro: "Encruzilhada",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-11-27"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Norberto Falcão Costa",
    cpf: "999.237.370-24",
    telefone: "(81) 99822-2753",
    email: "norberto.dias37@hotmail.com",
    endereco: {
      rua: "Rua Frei Cassimiro",
      numero: "872",
      bairro: "Tamarineira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-11-21"),
    observacoes: "Quer trocar veículo atual por um mais novo"
  },
  {
    nome: "Heitor Bezerra Tavares",
    cpf: "357.966.152-21",
    telefone: "(81) 99299-7939",
    email: "heitor.oliveira1@outlook.com",
    endereco: {
      rua: "Avenida Beberibe",
      numero: "545",
      bairro: "Afogados",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-12-15"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Bruna Pinto Albuquerque",
    cpf: "109.214.177-98",
    telefone: "(81) 99851-3442",
    email: "bruna.nunes75@gmail.com",
    endereco: {
      rua: "Rua Capitão Zuzinha",
      numero: "616",
      bairro: "Derby",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-01-10"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Vinícius Andrade Nascimento",
    cpf: "798.355.782-23",
    telefone: "(81) 98724-7658",
    email: "vinicius.barbosa21@hotmail.com",
    endereco: {
      rua: "Rua do Futuro",
      numero: "735",
      bairro: "Ilha do Leite",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-03-24"),
    observacoes: "Cliente indicado por outro comprador da loja"
  },
  {
    nome: "Sílvio Cunha Falcão",
    cpf: "984.852.930-41",
    telefone: "(81) 98546-3608",
    email: "silvio.mendes5@gmail.com",
    endereco: {
      rua: "Avenida Parnamirim",
      numero: "1937",
      bairro: "Caxangá",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-08-12"),
    observacoes: "Interesse em pickup para trabalho no interior"
  },
  {
    nome: "Davi Araújo Santos",
    cpf: "775.297.508-52",
    telefone: "(81) 98570-2137",
    email: "davi.andrade83@outlook.com",
    endereco: {
      rua: "Avenida Engenheiro Abdias de Carvalho",
      numero: "1647",
      bairro: "Tamarineira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-02-09"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "Débora Cavalcante Oliveira",
    cpf: "211.710.544-54",
    telefone: "(81) 99492-6139",
    email: "debora.lacerda66@yahoo.com",
    endereco: {
      rua: "Avenida Rui Barbosa",
      numero: "1587",
      bairro: "Iputinga",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-01-23"),
    observacoes: "Cliente fidelizado, já adquiriu veículo anteriormente"
  },
  {
    nome: "Lucas Sales Wanderley",
    cpf: "803.836.859-95",
    telefone: "(81) 98403-6967",
    email: "lucas.lima86@yahoo.com",
    endereco: {
      rua: "Rua Manoel de Carvalho",
      numero: "1362",
      bairro: "Rosarinho",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-12-10"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Otávio Falcão Cunha",
    cpf: "434.512.813-47",
    telefone: "(81) 99135-3085",
    email: "otavio.cunha86@hotmail.com",
    endereco: {
      rua: "Avenida Mascarenhas de Morais",
      numero: "722",
      bairro: "Encruzilhada",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-09-27"),
    observacoes: "Cliente interessado em SUVs compactos com baixo consumo"
  },
  {
    nome: "Norberto Teixeira Nascimento",
    cpf: "540.904.693-87",
    telefone: "(81) 99340-6279",
    email: "norberto.ramos57@yahoo.com",
    endereco: {
      rua: "Rua dos Coelhos",
      numero: "885",
      bairro: "Dois Irmãos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-12-06"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Eduardo Teixeira Bezerra",
    cpf: "779.748.734-52",
    telefone: "(81) 98191-4848",
    email: "eduardo.araújo26@outlook.com",
    endereco: {
      rua: "Rua da Hora",
      numero: "110",
      bairro: "Imbiribeira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-08-20"),
    observacoes: "Quer trocar veículo atual por um mais novo"
  },
  {
    nome: "Larissa Lima Vieira",
    cpf: "524.744.689-34",
    telefone: "(81) 99471-7291",
    email: "larissa.freitas32@yahoo.com",
    endereco: {
      rua: "Rua da Hora",
      numero: "32",
      bairro: "Aflitos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-04-06"),
    observacoes: "Interesse em modelos turbo esportivos"
  },
  {
    nome: "Amanda Sales Vieira",
    cpf: "151.670.355-25",
    telefone: "(81) 98934-3184",
    email: "amanda.falcão68@yahoo.com",
    endereco: {
      rua: "Rua Capitão Zuzinha",
      numero: "2448",
      bairro: "Rosarinho",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-10-27"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Olívia Pinto Albuquerque",
    cpf: "556.262.861-70",
    telefone: "(81) 98921-5246",
    email: "olivia.brandão36@hotmail.com",
    endereco: {
      rua: "Avenida Norte Miguel Arraes",
      numero: "2145",
      bairro: "Várzea",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-05-15"),
    observacoes: "Procura sedan automático para uso familiar"
  },
  {
    nome: "Carolina Teixeira Barbosa",
    cpf: "378.443.427-79",
    telefone: "(81) 98165-3267",
    email: "carolina.araújo50@hotmail.com",
    endereco: {
      rua: "Avenida Cruz Cabugá",
      numero: "635",
      bairro: "Várzea",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-07-14"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Vanessa Vieira Cunha",
    cpf: "163.311.952-63",
    telefone: "(81) 98797-1320",
    email: "vanessa.macedo1@yahoo.com",
    endereco: {
      rua: "Rua João de Barros",
      numero: "1233",
      bairro: "Santo Amaro",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-09-24"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Vanessa Lacerda Araújo",
    cpf: "599.324.379-65",
    telefone: "(81) 98994-1475",
    email: "vanessa.cardoso86@yahoo.com",
    endereco: {
      rua: "Rua dos Coelhos",
      numero: "1666",
      bairro: "Torre",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-03-20"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Gustavo Freitas Siqueira",
    cpf: "677.778.127-20",
    telefone: "(81) 99316-8022",
    email: "gustavo.vieira24@hotmail.com",
    endereco: {
      rua: "Avenida Conde da Boa Vista",
      numero: "1075",
      bairro: "Santo Amaro",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-04-15"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Téo Magalhães Mendes",
    cpf: "384.870.951-63",
    telefone: "(81) 98516-2341",
    email: "teo.santos96@yahoo.com",
    endereco: {
      rua: "Rua Capitão Zuzinha",
      numero: "223",
      bairro: "Casa Amarela",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-11-03"),
    observacoes: "Interesse em modelos turbo esportivos"
  },
  {
    nome: "Nicole Oliveira Magalhães",
    cpf: "131.353.304-12",
    telefone: "(81) 99272-3496",
    email: "nicole.gomes61@hotmail.com",
    endereco: {
      rua: "Rua dos Coelhos",
      numero: "478",
      bairro: "Várzea",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-12-09"),
    observacoes: "Interesse em modelos turbo esportivos"
  },
  {
    nome: "Adriano Martins Lacerda",
    cpf: "721.865.835-24",
    telefone: "(81) 99592-3683",
    email: "adriano.costa75@outlook.com",
    endereco: {
      rua: "Rua Real da Torre",
      numero: "1287",
      bairro: "Santo Amaro",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-12-07"),
    observacoes: "Procura sedan automático para uso familiar"
  },
  {
    nome: "Emanuela Holanda Brandão",
    cpf: "348.204.813-48",
    telefone: "(81) 99741-2983",
    email: "emanuela.andrade69@gmail.com",
    endereco: {
      rua: "Rua Henrique Dias",
      numero: "1527",
      bairro: "Espinheiro",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-01-28"),
    observacoes: "Cliente fidelizado, já adquiriu veículo anteriormente"
  },
  {
    nome: "Marina Costa Pinto",
    cpf: "470.750.948-68",
    telefone: "(81) 99448-3506",
    email: "marina.rocha94@yahoo.com",
    endereco: {
      rua: "Avenida Engenheiro Abdias de Carvalho",
      numero: "1116",
      bairro: "Cidade Universitária",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-07-27"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Emanuela Dias Moreira",
    cpf: "972.351.950-21",
    telefone: "(81) 98571-8385",
    email: "emanuela.magalhães60@hotmail.com",
    endereco: {
      rua: "Avenida Mário Melo",
      numero: "1562",
      bairro: "Tamarineira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-08-28"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Tomás Tavares Nascimento",
    cpf: "463.916.364-53",
    telefone: "(81) 98572-5526",
    email: "tomas.sales25@gmail.com",
    endereco: {
      rua: "Rua do Espinheiro",
      numero: "998",
      bairro: "Ilha do Leite",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-09-25"),
    observacoes: "Prefere veículos com câmbio automático e câmera de ré"
  },
  {
    nome: "Viviane Macedo Coutinho",
    cpf: "828.602.558-12",
    telefone: "(81) 98190-5820",
    email: "viviane.freitas89@hotmail.com",
    endereco: {
      rua: "Rua Barão de Souza Leão",
      numero: "1264",
      bairro: "Poço da Panela",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-09-17"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Elaine Lobo Albuquerque",
    cpf: "438.460.819-68",
    telefone: "(81) 98554-6023",
    email: "elaine.araújo16@outlook.com",
    endereco: {
      rua: "Rua Gervásio Pires",
      numero: "798",
      bairro: "Rosarinho",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-12-18"),
    observacoes: "Interesse em modelos turbo esportivos"
  },
  {
    nome: "Viviane Rocha Almeida",
    cpf: "321.856.595-45",
    telefone: "(81) 99483-9595",
    email: "viviane.costa25@outlook.com",
    endereco: {
      rua: "Rua Imperial",
      numero: "941",
      bairro: "Poço da Panela",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-05-01"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Tatiane Gomes Dias",
    cpf: "146.155.666-47",
    telefone: "(81) 99428-3068",
    email: "tatiane.costa2@yahoo.com",
    endereco: {
      rua: "Avenida Mário Melo",
      numero: "1174",
      bairro: "Cidade Universitária",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-08-11"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "André Cavalcante Macedo",
    cpf: "216.941.166-61",
    telefone: "(81) 99007-2213",
    email: "andre.ribeiro20@gmail.com",
    endereco: {
      rua: "Rua do Futuro",
      numero: "2315",
      bairro: "Encruzilhada",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-04-04"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Juliana Cunha Lacerda",
    cpf: "710.909.733-38",
    telefone: "(81) 99588-9561",
    email: "juliana.ramos57@yahoo.com",
    endereco: {
      rua: "Rua Imperial",
      numero: "2420",
      bairro: "Derby",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-10-20"),
    observacoes: "Cliente interessado em SUVs compactos com baixo consumo"
  },
  {
    nome: "Heloísa Lobo Costa",
    cpf: "881.312.740-37",
    telefone: "(81) 98541-2330",
    email: "heloisa.barbosa23@hotmail.com",
    endereco: {
      rua: "Rua Capitão Zuzinha",
      numero: "317",
      bairro: "Torre",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-07-15"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Flávia Macedo Teixeira",
    cpf: "133.337.395-46",
    telefone: "(81) 99439-8438",
    email: "flavia.galvão30@gmail.com",
    endereco: {
      rua: "Rua Manoel de Carvalho",
      numero: "1093",
      bairro: "Iputinga",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-02-18"),
    observacoes: "Prefere veículos com câmbio automático e câmera de ré"
  },
  {
    nome: "Manuela Ribeiro Dias",
    cpf: "946.245.173-17",
    telefone: "(81) 98339-6039",
    email: "manuela.ramos16@outlook.com",
    endereco: {
      rua: "Avenida 17 de Agosto",
      numero: "1255",
      bairro: "Soledade",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-09-18"),
    observacoes: "Motorista de aplicativo, busca economia e conforto"
  },
  {
    nome: "Giovana Pereira Lacerda",
    cpf: "140.542.852-51",
    telefone: "(81) 99236-5102",
    email: "giovana.pereira30@gmail.com",
    endereco: {
      rua: "Rua dos Coelhos",
      numero: "2366",
      bairro: "Pina",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-10-02"),
    observacoes: "Interesse em modelos turbo esportivos"
  },
  {
    nome: "Iara Rocha Macedo",
    cpf: "631.767.552-45",
    telefone: "(81) 98371-8141",
    email: "iara.pereira61@yahoo.com",
    endereco: {
      rua: "Rua João de Barros",
      numero: "1682",
      bairro: "Tamarineira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-11-04"),
    observacoes: "Quer trocar veículo atual por um mais novo"
  },
  {
    nome: "Pedro Cardoso Cunha",
    cpf: "810.607.395-94",
    telefone: "(81) 99935-7561",
    email: "pedro.vieira12@gmail.com",
    endereco: {
      rua: "Avenida Beberibe",
      numero: "1043",
      bairro: "Rosarinho",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-07-28"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Lucas Falcão Wanderley",
    cpf: "573.523.155-34",
    telefone: "(81) 99061-6927",
    email: "lucas.brandão57@yahoo.com",
    endereco: {
      rua: "Avenida Norte Miguel Arraes",
      numero: "221",
      bairro: "Várzea",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-09-05"),
    observacoes: "Cliente indicado por outro comprador da loja"
  },
  {
    nome: "Lourenço Ramos Holanda",
    cpf: "596.224.129-90",
    telefone: "(81) 99246-4920",
    email: "lourenco.fernandes71@hotmail.com",
    endereco: {
      rua: "Rua Real da Torre",
      numero: "2272",
      bairro: "Ilha do Leite",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-04-27"),
    observacoes: "Cliente indicado por outro comprador da loja"
  },
  {
    nome: "Igor Vieira Carvalho",
    cpf: "763.952.257-73",
    telefone: "(81) 99910-5781",
    email: "igor.cunha62@outlook.com",
    endereco: {
      rua: "Rua Dona Benvinda de Farias",
      numero: "1008",
      bairro: "Benfica",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-07-07"),
    observacoes: "Cliente indicado por outro comprador da loja"
  },
  {
    nome: "Flávia Bezerra Lobo",
    cpf: "239.984.171-45",
    telefone: "(81) 99582-7798",
    email: "flavia.bezerra35@outlook.com",
    endereco: {
      rua: "Rua Amaury de Medeiros",
      numero: "20",
      bairro: "Areias",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-10-19"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Marina Ribeiro Ramos",
    cpf: "651.595.453-52",
    telefone: "(81) 99130-9903",
    email: "marina.vieira42@yahoo.com",
    endereco: {
      rua: "Avenida Parnamirim",
      numero: "782",
      bairro: "San Martin",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-04-28"),
    observacoes: "Interesse em modelos turbo esportivos"
  },
  {
    nome: "Camila Oliveira Moreira",
    cpf: "862.584.822-58",
    telefone: "(81) 98790-3492",
    email: "camila.oliveira17@yahoo.com",
    endereco: {
      rua: "Avenida Engenheiro Abdias de Carvalho",
      numero: "2427",
      bairro: "Tamarineira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-08-04"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Ingrid Silva Justino",
    cpf: "247.519.991-93",
    telefone: "(81) 99986-3529",
    email: "ingrid.macedo34@gmail.com",
    endereco: {
      rua: "Avenida Beberibe",
      numero: "1638",
      bairro: "Graças",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-11-28"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Benedito Moreira Brandão",
    cpf: "835.877.599-79",
    telefone: "(81) 98073-2121",
    email: "benedito.brandão88@hotmail.com",
    endereco: {
      rua: "Rua Manoel de Carvalho",
      numero: "1187",
      bairro: "Caxangá",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-07-04"),
    observacoes: "Interesse em modelos turbo esportivos"
  },
  {
    nome: "Lara Ítalo Costa",
    cpf: "554.270.810-48",
    telefone: "(81) 99850-1474",
    email: "lara.moreira8@gmail.com",
    endereco: {
      rua: "Rua Imperial",
      numero: "1478",
      bairro: "Poço da Panela",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-03-08"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Camila Vasconcelos Galvão",
    cpf: "911.284.274-32",
    telefone: "(81) 98161-7267",
    email: "camila.tavares75@hotmail.com",
    endereco: {
      rua: "Rua da Hora",
      numero: "961",
      bairro: "Benfica",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-08-09"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Mateus Vieira Teixeira",
    cpf: "793.659.261-19",
    telefone: "(81) 98904-6661",
    email: "mateus.brandão55@outlook.com",
    endereco: {
      rua: "Avenida Cruz Cabugá",
      numero: "1034",
      bairro: "Benfica",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-04-13"),
    observacoes: "Quer trocar veículo atual por um mais novo"
  },
  {
    nome: "Letícia Costa Barbosa",
    cpf: "490.685.467-83",
    telefone: "(81) 98605-5837",
    email: "leticia.falcão51@gmail.com",
    endereco: {
      rua: "Avenida Recife",
      numero: "43",
      bairro: "Boa Vista",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-05-25"),
    observacoes: "Interesse em modelos turbo esportivos"
  },
  {
    nome: "Davi Lacerda Andrade",
    cpf: "324.751.294-89",
    telefone: "(81) 98513-3240",
    email: "davi.brandão83@gmail.com",
    endereco: {
      rua: "Avenida Conde da Boa Vista",
      numero: "1275",
      bairro: "Jaqueira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-10-12"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Kléber Pereira Teixeira",
    cpf: "434.865.525-32",
    telefone: "(81) 98411-3165",
    email: "kleber.sales65@outlook.com",
    endereco: {
      rua: "Rua Manoel de Carvalho",
      numero: "1126",
      bairro: "Torre",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-08-26"),
    observacoes: "Interesse em pickup para trabalho no interior"
  },
  {
    nome: "Geovana Cardoso Carvalho",
    cpf: "579.177.244-38",
    telefone: "(81) 99761-7511",
    email: "geovana.pereira51@outlook.com",
    endereco: {
      rua: "Rua Real da Torre",
      numero: "1093",
      bairro: "Casa Forte",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-06-22"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Sofia Cavalcante Siqueira",
    cpf: "490.942.753-57",
    telefone: "(81) 98221-4830",
    email: "sofia.santos80@yahoo.com",
    endereco: {
      rua: "Rua Jorge de Lima",
      numero: "2309",
      bairro: "Rosarinho",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-11-03"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Júlia Holanda Fernandes",
    cpf: "764.518.219-27",
    telefone: "(81) 98092-1609",
    email: "julia.tavares15@outlook.com",
    endereco: {
      rua: "Avenida Rui Barbosa",
      numero: "971",
      bairro: "Parnamirim",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-08-12"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Geovana Holanda Wanderley",
    cpf: "529.701.860-29",
    telefone: "(81) 99813-7797",
    email: "geovana.tavares79@gmail.com",
    endereco: {
      rua: "Rua Henrique Dias",
      numero: "1155",
      bairro: "Imbiribeira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-04-15"),
    observacoes: "Motorista de aplicativo, busca economia e conforto"
  },
  {
    nome: "Enzo Nunes Costa",
    cpf: "802.476.657-92",
    telefone: "(81) 98734-1992",
    email: "enzo.dias25@yahoo.com",
    endereco: {
      rua: "Avenida Rui Barbosa",
      numero: "1872",
      bairro: "Graças",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-11-21"),
    observacoes: "Interessado em financiamento com entrada facilitada"
  },
  {
    nome: "Rafael Souza Cardoso",
    cpf: "349.228.905-82",
    telefone: "(81) 98420-2124",
    email: "rafael.siqueira28@hotmail.com",
    endereco: {
      rua: "Rua Amaury de Medeiros",
      numero: "964",
      bairro: "Tamarineira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-10-01"),
    observacoes: "Interesse em pickup para trabalho no interior"
  },
  {
    nome: "Murilo Gomes Wanderley",
    cpf: "356.917.278-24",
    telefone: "(81) 99353-1422",
    email: "murilo.silva46@hotmail.com",
    endereco: {
      rua: "Rua do Futuro",
      numero: "984",
      bairro: "Rosarinho",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-03-09"),
    observacoes: "Cliente interessado em SUVs compactos com baixo consumo"
  },
  {
    nome: "Kléber Lobo Cunha",
    cpf: "638.216.863-18",
    telefone: "(81) 98975-8344",
    email: "kleber.bezerra76@outlook.com",
    endereco: {
      rua: "Avenida Rui Barbosa",
      numero: "1861",
      bairro: "Dois Irmãos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-10-02"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Paloma Sales Fernandes",
    cpf: "569.758.131-17",
    telefone: "(81) 98980-7580",
    email: "paloma.galvão14@yahoo.com",
    endereco: {
      rua: "Rua Dona Benvinda de Farias",
      numero: "1826",
      bairro: "Espinheiro",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-06-20"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "Caio Gomes Dias",
    cpf: "739.748.699-80",
    telefone: "(81) 99458-6327",
    email: "caio.lacerda68@yahoo.com",
    endereco: {
      rua: "Rua Imperial",
      numero: "1868",
      bairro: "Dois Irmãos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-02-26"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Igor Coutinho Coutinho",
    cpf: "998.887.664-37",
    telefone: "(81) 98880-8398",
    email: "igor.cunha44@hotmail.com",
    endereco: {
      rua: "Rua Amaury de Medeiros",
      numero: "1867",
      bairro: "Soledade",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-12-04"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Elaine Moreira Falcão",
    cpf: "361.483.256-97",
    telefone: "(81) 99890-8770",
    email: "elaine.pereira11@gmail.com",
    endereco: {
      rua: "Rua do Espinheiro",
      numero: "1778",
      bairro: "Aflitos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-03-18"),
    observacoes: "Cliente interessado em SUVs compactos com baixo consumo"
  },
  {
    nome: "Emanuela Albuquerque Albuquerque",
    cpf: "437.786.225-62",
    telefone: "(81) 98724-7929",
    email: "emanuela.teixeira77@gmail.com",
    endereco: {
      rua: "Rua Imperial",
      numero: "1450",
      bairro: "Aflitos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-03-22"),
    observacoes: "Motorista de aplicativo, busca economia e conforto"
  },
  {
    nome: "César Costa Andrade",
    cpf: "965.669.476-24",
    telefone: "(81) 99561-5564",
    email: "cesar.pinto72@hotmail.com",
    endereco: {
      rua: "Avenida Norte Miguel Arraes",
      numero: "2290",
      bairro: "Pina",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-01-06"),
    observacoes: "Interesse em pickup para trabalho no interior"
  },
  {
    nome: "Amanda Magalhães Fernandes",
    cpf: "447.459.106-33",
    telefone: "(81) 99781-3347",
    email: "amanda.lima19@yahoo.com",
    endereco: {
      rua: "Rua Gervásio Pires",
      numero: "135",
      bairro: "Graças",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-07-14"),
    observacoes: "Motorista de aplicativo, busca economia e conforto"
  },
  {
    nome: "Téo Martins Nunes",
    cpf: "419.838.432-82",
    telefone: "(81) 99221-2391",
    email: "teo.ribeiro21@gmail.com",
    endereco: {
      rua: "Avenida Norte Miguel Arraes",
      numero: "213",
      bairro: "Graças",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-08-22"),
    observacoes: "Cliente fidelizado, já adquiriu veículo anteriormente"
  },
  {
    nome: "Marina Lacerda Ramos",
    cpf: "524.379.320-75",
    telefone: "(81) 98233-6655",
    email: "marina.carvalho37@yahoo.com",
    endereco: {
      rua: "Rua dos Coelhos",
      numero: "2439",
      bairro: "Várzea",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-01-08"),
    observacoes: "Cliente fidelizado, já adquiriu veículo anteriormente"
  },
  {
    nome: "Flávia Souza Silva",
    cpf: "309.408.316-27",
    telefone: "(81) 99565-5186",
    email: "flavia.moreira16@outlook.com",
    endereco: {
      rua: "Rua Real da Torre",
      numero: "2047",
      bairro: "Derby",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-03-13"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Bruna Araújo Bezerra",
    cpf: "672.953.784-55",
    telefone: "(81) 98147-7505",
    email: "bruna.pinto3@gmail.com",
    endereco: {
      rua: "Avenida 17 de Agosto",
      numero: "328",
      bairro: "Rosarinho",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-10-13"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Lara Cunha Teixeira",
    cpf: "217.514.121-51",
    telefone: "(81) 98351-8538",
    email: "lara.pereira56@outlook.com",
    endereco: {
      rua: "Avenida Parnamirim",
      numero: "443",
      bairro: "San Martin",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-10-13"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Eduardo Freitas Fernandes",
    cpf: "863.447.326-52",
    telefone: "(81) 99595-3754",
    email: "eduardo.bezerra82@gmail.com",
    endereco: {
      rua: "Avenida Rui Barbosa",
      numero: "2183",
      bairro: "Dois Irmãos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-06-12"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Manuela Ribeiro Barbosa",
    cpf: "205.249.362-35",
    telefone: "(81) 98355-3504",
    email: "manuela.rocha99@gmail.com",
    endereco: {
      rua: "Avenida General San Martin",
      numero: "2033",
      bairro: "Benfica",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-11-19"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Lara Maciel Moreira",
    cpf: "984.742.423-29",
    telefone: "(81) 98900-2118",
    email: "lara.ramos81@yahoo.com",
    endereco: {
      rua: "Rua Imperial",
      numero: "1135",
      bairro: "Boa Vista",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-09-03"),
    observacoes: "Interesse em pickup para trabalho no interior"
  },
  {
    nome: "Júlia Ramos Oliveira",
    cpf: "158.477.951-46",
    telefone: "(81) 98157-2479",
    email: "julia.vieira75@yahoo.com",
    endereco: {
      rua: "Rua Capitão Zuzinha",
      numero: "178",
      bairro: "Jaqueira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-06-20"),
    observacoes: "Motorista de aplicativo, busca economia e conforto"
  },
  {
    nome: "Olívia Ribeiro Souza",
    cpf: "561.205.930-53",
    telefone: "(81) 99462-2381",
    email: "olivia.oliveira32@hotmail.com",
    endereco: {
      rua: "Avenida Cruz Cabugá",
      numero: "1803",
      bairro: "Jaqueira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-06-12"),
    observacoes: "Cliente indicado por outro comprador da loja"
  },
  {
    nome: "Lourenço Mendes Cunha",
    cpf: "893.446.795-86",
    telefone: "(81) 98107-6482",
    email: "lourenco.cardoso13@gmail.com",
    endereco: {
      rua: "Rua Capitão Zuzinha",
      numero: "1593",
      bairro: "Areias",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-12-28"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Gabriela Ribeiro Cardoso",
    cpf: "183.696.779-28",
    telefone: "(81) 99877-6731",
    email: "gabriela.coutinho90@outlook.com",
    endereco: {
      rua: "Rua dos Coelhos",
      numero: "1615",
      bairro: "Parnamirim",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-05-18"),
    observacoes: "Cliente fidelizado, já adquiriu veículo anteriormente"
  },
  {
    nome: "Manuela Cardoso Gomes",
    cpf: "786.819.948-97",
    telefone: "(81) 99868-9624",
    email: "manuela.coutinho86@gmail.com",
    endereco: {
      rua: "Rua Henrique Dias",
      numero: "2092",
      bairro: "Poço da Panela",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-06-10"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "Breno Cardoso Padilha",
    cpf: "597.296.331-27",
    telefone: "(81) 98317-2264",
    email: "breno.costa65@outlook.com",
    endereco: {
      rua: "Avenida Norte Miguel Arraes",
      numero: "2220",
      bairro: "Apipucos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-11-11"),
    observacoes: "Cliente indicado por outro comprador da loja"
  },
  {
    nome: "Larissa Maciel Gomes",
    cpf: "711.485.257-30",
    telefone: "(81) 98370-3712",
    email: "larissa.oliveira53@yahoo.com",
    endereco: {
      rua: "Rua João de Barros",
      numero: "982",
      bairro: "Jaqueira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-12-26"),
    observacoes: "Motorista de aplicativo, busca economia e conforto"
  },
  {
    nome: "Davi Wanderley Barbosa",
    cpf: "416.928.903-70",
    telefone: "(81) 99851-4178",
    email: "davi.galvão74@outlook.com",
    endereco: {
      rua: "Avenida 17 de Agosto",
      numero: "1901",
      bairro: "Areias",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-09-17"),
    observacoes: "Cliente fidelizado, já adquiriu veículo anteriormente"
  },
  {
    nome: "Pedro Almeida Lacerda",
    cpf: "241.993.356-16",
    telefone: "(81) 99313-8873",
    email: "pedro.albuquerque14@outlook.com",
    endereco: {
      rua: "Avenida Cruz Cabugá",
      numero: "2123",
      bairro: "Casa Forte",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-02-25"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "Ivan Ramos Bezerra",
    cpf: "250.950.547-21",
    telefone: "(81) 99938-4637",
    email: "ivan.andrade4@yahoo.com",
    endereco: {
      rua: "Rua Henrique Dias",
      numero: "228",
      bairro: "Soledade",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-04-13"),
    observacoes: "Procura sedan automático para uso familiar"
  },
  {
    nome: "Adriano Araújo Santos",
    cpf: "426.201.959-93",
    telefone: "(81) 98686-3392",
    email: "adriano.oliveira37@hotmail.com",
    endereco: {
      rua: "Rua Manoel de Carvalho",
      numero: "1945",
      bairro: "Parnamirim",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-08-20"),
    observacoes: "Cliente interessado em SUVs compactos com baixo consumo"
  },
  {
    nome: "Eduardo Santos Cavalcante",
    cpf: "320.955.253-80",
    telefone: "(81) 99925-9647",
    email: "eduardo.carvalho37@yahoo.com",
    endereco: {
      rua: "Rua Barão de Souza Leão",
      numero: "1243",
      bairro: "Casa Forte",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-04-14"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Isadora Vieira Lima",
    cpf: "213.956.611-86",
    telefone: "(81) 99097-1269",
    email: "isadora.ítalo19@hotmail.com",
    endereco: {
      rua: "Rua Imperial",
      numero: "1768",
      bairro: "Boa Viagem",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-04-19"),
    observacoes: "Cliente fidelizado, já adquiriu veículo anteriormente"
  },
  {
    nome: "Tomás Falcão Falcão",
    cpf: "187.636.469-18",
    telefone: "(81) 99952-9618",
    email: "tomas.mendes61@gmail.com",
    endereco: {
      rua: "Avenida Conde da Boa Vista",
      numero: "1594",
      bairro: "Poço da Panela",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-12-01"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Caio Andrade Barbosa",
    cpf: "850.772.743-23",
    telefone: "(81) 99580-6447",
    email: "caio.oliveira46@hotmail.com",
    endereco: {
      rua: "Rua Capitão Zuzinha",
      numero: "1396",
      bairro: "Cordeiro",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-12-16"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Tomás Gomes Lima",
    cpf: "833.894.568-14",
    telefone: "(81) 98600-4302",
    email: "tomas.almeida6@gmail.com",
    endereco: {
      rua: "Avenida Beberibe",
      numero: "1280",
      bairro: "Dois Irmãos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-09-16"),
    observacoes: "Interesse em pickup para trabalho no interior"
  },
  {
    nome: "Thiago Magalhães Coutinho",
    cpf: "295.392.465-16",
    telefone: "(81) 99773-6438",
    email: "thiago.carvalho48@outlook.com",
    endereco: {
      rua: "Rua Henrique Dias",
      numero: "1648",
      bairro: "Jaqueira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-06-06"),
    observacoes: "Motorista de aplicativo, busca economia e conforto"
  },
  {
    nome: "Viviane Tavares Nunes",
    cpf: "916.631.373-20",
    telefone: "(81) 99489-7955",
    email: "viviane.pinto78@gmail.com",
    endereco: {
      rua: "Rua Amaury de Medeiros",
      numero: "749",
      bairro: "Areias",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-02-03"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Paloma Teixeira Fernandes",
    cpf: "556.717.834-64",
    telefone: "(81) 98341-8272",
    email: "paloma.ramos6@outlook.com",
    endereco: {
      rua: "Rua Gervásio Pires",
      numero: "1454",
      bairro: "Derby",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-11-26"),
    observacoes: "Cliente interessado em SUVs compactos com baixo consumo"
  },
  {
    nome: "Daniel Falcão Brandão",
    cpf: "515.472.625-96",
    telefone: "(81) 98327-1510",
    email: "daniel.lacerda87@hotmail.com",
    endereco: {
      rua: "Rua do Futuro",
      numero: "1804",
      bairro: "Imbiribeira",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-02-08"),
    observacoes: "Interesse em modelos turbo esportivos"
  },
  {
    nome: "Manuela Nunes Nunes",
    cpf: "492.680.133-87",
    telefone: "(81) 98314-8371",
    email: "manuela.nunes57@outlook.com",
    endereco: {
      rua: "Avenida Norte Miguel Arraes",
      numero: "324",
      bairro: "Parnamirim",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-07-11"),
    observacoes: "Procura carro com teto solar e bancos de couro"
  },
  {
    nome: "Joaquim Barbosa Carvalho",
    cpf: "126.853.290-73",
    telefone: "(81) 99060-7340",
    email: "joaquim.cavalcante34@gmail.com",
    endereco: {
      rua: "Avenida Cruz Cabugá",
      numero: "1837",
      bairro: "Várzea",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-12-16"),
    observacoes: "Prefere veículos com câmbio automático e câmera de ré"
  },
  {
    nome: "Júlio Gomes Lima",
    cpf: "562.276.830-66",
    telefone: "(81) 98179-6236",
    email: "julio.ítalo9@outlook.com",
    endereco: {
      rua: "Rua Capitão Zuzinha",
      numero: "2230",
      bairro: "Areias",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-03-23"),
    observacoes: "Busca veículo flex com bom custo-benefício"
  },
  {
    nome: "Amanda Brandão Rocha",
    cpf: "912.470.620-38",
    telefone: "(81) 98248-4292",
    email: "amanda.barbosa64@hotmail.com",
    endereco: {
      rua: "Rua Real da Torre",
      numero: "1488",
      bairro: "Poço da Panela",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-09-05"),
    observacoes: "Interessado em financiamento com entrada facilitada"
  },
  {
    nome: "Fábio Lima Fernandes",
    cpf: "507.834.836-71",
    telefone: "(81) 99076-7730",
    email: "fabio.vasconcelos10@yahoo.com",
    endereco: {
      rua: "Rua da Hora",
      numero: "1308",
      bairro: "Espinheiro",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-08-22"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Ubirajara Gomes Padilha",
    cpf: "664.755.701-33",
    telefone: "(81) 99572-3114",
    email: "ubirajara.bezerra8@yahoo.com",
    endereco: {
      rua: "Rua Amaury de Medeiros",
      numero: "518",
      bairro: "Apipucos",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-05-06"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "Renato Ítalo Araújo",
    cpf: "454.631.390-20",
    telefone: "(81) 98513-4216",
    email: "renato.gomes81@outlook.com",
    endereco: {
      rua: "Rua Imperial",
      numero: "2195",
      bairro: "Graças",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-10-19"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "Rodrigo Falcão Maciel",
    cpf: "837.719.445-82",
    telefone: "(81) 98084-1464",
    email: "rodrigo.oliveira83@gmail.com",
    endereco: {
      rua: "Avenida Norte Miguel Arraes",
      numero: "2372",
      bairro: "Afogados",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-10-14"),
    observacoes: "Interessado em financiamento com entrada facilitada"
  },
  {
    nome: "Lara Santos Tavares",
    cpf: "742.658.396-92",
    telefone: "(81) 99959-5949",
    email: "lara.barbosa88@yahoo.com",
    endereco: {
      rua: "Avenida Mascarenhas de Morais",
      numero: "1228",
      bairro: "Benfica",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-12-02"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "Giovana Cunha Macedo",
    cpf: "575.308.448-87",
    telefone: "(81) 98294-6121",
    email: "giovana.justino45@outlook.com",
    endereco: {
      rua: "Avenida Mascarenhas de Morais",
      numero: "545",
      bairro: "Poço da Panela",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-06-08"),
    observacoes: "Motorista de aplicativo, busca economia e conforto"
  },
  {
    nome: "Júlio Dias Ramos",
    cpf: "353.244.199-16",
    telefone: "(81) 98594-7293",
    email: "julio.barbosa21@yahoo.com",
    endereco: {
      rua: "Rua Amaury de Medeiros",
      numero: "1351",
      bairro: "Rosarinho",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-03-16"),
    observacoes: "Quer veículo com baixa quilometragem e único dono"
  },
  {
    nome: "Júlia Tavares Fernandes",
    cpf: "609.123.192-60",
    telefone: "(81) 99035-8491",
    email: "julia.nascimento75@hotmail.com",
    endereco: {
      rua: "Rua João de Barros",
      numero: "209",
      bairro: "Boa Vista",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2024-08-20"),
    observacoes: "Cliente indicado por outro comprador da loja"
  },
  {
    nome: "Nicole Galvão Macedo",
    cpf: "392.649.108-23",
    telefone: "(81) 98882-3194",
    email: "nicole.justino47@outlook.com",
    endereco: {
      rua: "Avenida Norte Miguel Arraes",
      numero: "1661",
      bairro: "Poço da Panela",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-07-02"),
    observacoes: "Interessado em financiamento com entrada facilitada"
  },
  {
    nome: "Aline Almeida Nunes",
    cpf: "666.395.175-59",
    telefone: "(81) 99032-8378",
    email: "aline.maciel88@outlook.com",
    endereco: {
      rua: "Rua Frei Cassimiro",
      numero: "496",
      bairro: "Parnamirim",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-07-12"),
    observacoes: "Interesse em modelos turbo esportivos"
  },
  {
    nome: "Téo Albuquerque Nunes",
    cpf: "873.247.303-87",
    telefone: "(81) 99042-7576",
    email: "teo.oliveira5@gmail.com",
    endereco: {
      rua: "Rua da Hora",
      numero: "1374",
      bairro: "Cidade Universitária",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-03-20"),
    observacoes: "Cliente indicado por outro comprador da loja"
  },
  {
    nome: "Patrícia Gomes Moreira",
    cpf: "727.426.266-60",
    telefone: "(81) 99262-5902",
    email: "patricia.bezerra66@outlook.com",
    endereco: {
      rua: "Rua Capitão Zuzinha",
      numero: "2016",
      bairro: "Encruzilhada",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-01-12"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Sofia Carvalho Cunha",
    cpf: "697.415.915-98",
    telefone: "(81) 99288-1436",
    email: "sofia.cavalcante84@yahoo.com",
    endereco: {
      rua: "Rua do Futuro",
      numero: "2379",
      bairro: "Caxangá",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2022-10-16"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "Sabrina Brandão Justino",
    cpf: "734.893.961-58",
    telefone: "(81) 98302-4968",
    email: "sabrina.vasconcelos90@gmail.com",
    endereco: {
      rua: "Avenida Rui Barbosa",
      numero: "791",
      bairro: "Pina",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-06-14"),
    observacoes: "Busca hatch econômico para deslocamento urbano"
  },
  {
    nome: "Camila Holanda Nascimento",
    cpf: "520.613.893-88",
    telefone: "(81) 99885-8726",
    email: "camila.ítalo18@gmail.com",
    endereco: {
      rua: "Avenida Engenheiro Abdias de Carvalho",
      numero: "859",
      bairro: "Rosarinho",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2025-09-13"),
    observacoes: "Primeira compra de veículo seminovo"
  },
  {
    nome: "Samuel Vieira Wanderley",
    cpf: "450.659.462-96",
    telefone: "(81) 99581-5331",
    email: "samuel.almeida32@yahoo.com",
    endereco: {
      rua: "Avenida Recife",
      numero: "2295",
      bairro: "Encruzilhada",
      cidade: "Recife",
      estado: "PE"
    },
    data_cadastro: new Date("2023-05-25"),
    observacoes: "Interesse em pickup para trabalho no interior"
  }
])
```

---

## BLOCO 2 - Coleção `vendedores` (8 documentos)

```javascript
db.vendedores.insertMany([
  {
    nome: "Carlos Mendonça",
    cpf: "111.222.333-44",
    telefone: "(81) 99001-1111",
    email: "carlos@revendedora.com",
    salario_base: 2500.00,
    comissao_percentual: 3.5,
    data_admissao: new Date("2019-03-10"),
    ativo: true
  },
  {
    nome: "Fernanda Lira",
    cpf: "222.333.444-55",
    telefone: "(81) 99002-2222",
    email: "fernanda@revendedora.com",
    salario_base: 2800.00,
    comissao_percentual: 4.0,
    data_admissao: new Date("2020-07-15"),
    ativo: true
  },
  {
    nome: "Rafael Souza",
    cpf: "333.444.555-66",
    telefone: "(81) 99003-3333",
    email: "rafael@revendedora.com",
    salario_base: 2600.00,
    comissao_percentual: 3.0,
    data_admissao: new Date("2021-01-20"),
    ativo: false
  },
  {
    nome: "Tatiane Oliveira",
    cpf: "444.555.666-77",
    telefone: "(81) 99004-4444",
    email: "tatiane@revendedora.com",
    salario_base: 2700.00,
    comissao_percentual: 3.8,
    data_admissao: new Date("2020-11-05"),
    ativo: true
  },
  {
    nome: "Marcelo Figueiredo",
    cpf: "555.666.777-88",
    telefone: "(81) 99005-5555",
    email: "marcelo@revendedora.com",
    salario_base: 3000.00,
    comissao_percentual: 4.5,
    data_admissao: new Date("2018-06-01"),
    ativo: true
  },
  {
    nome: "Juliana Bezerra",
    cpf: "666.777.888-99",
    telefone: "(81) 99006-6666",
    email: "juliana@revendedora.com",
    salario_base: 2550.00,
    comissao_percentual: 3.2,
    data_admissao: new Date("2022-02-14"),
    ativo: true
  },
  {
    nome: "Anderson Lima",
    cpf: "777.888.999-00",
    telefone: "(81) 99007-7777",
    email: "anderson@revendedora.com",
    salario_base: 2450.00,
    comissao_percentual: 3.0,
    data_admissao: new Date("2022-08-30"),
    ativo: false
  },
  {
    nome: "Patrícia Wanderley",
    cpf: "888.999.000-11",
    telefone: "(81) 99008-8888",
    email: "patricia@revendedora.com",
    salario_base: 2900.00,
    comissao_percentual: 4.2,
    data_admissao: new Date("2017-09-22"),
    ativo: true
  }
])
```

---

## BLOCO 3 - Coleção `mecanicos` (10 documentos)

```javascript
db.mecanicos.insertMany([
  {
    nome: "Sérgio Batista",
    cpf: "101.202.303-44",
    telefone: "(81) 99101-1111",
    email: "sergio@revendedora.com",
    especialidades: ["motor", "suspensão", "freios"],
    salario: 3200.00,
    data_admissao: new Date("2018-04-10"),
    ativo: true
  },
  {
    nome: "Rogério Nascimento",
    cpf: "202.303.404-55",
    telefone: "(81) 99102-2222",
    email: "rogerio@revendedora.com",
    especialidades: ["funilaria", "pintura", "estética"],
    salario: 3000.00,
    data_admissao: new Date("2019-08-22"),
    ativo: true
  },
  {
    nome: "Luciano Ferraz",
    cpf: "303.404.505-66",
    telefone: "(81) 99103-3333",
    email: "luciano@revendedora.com",
    especialidades: ["elétrica", "ar-condicionado", "som"],
    salario: 3100.00,
    data_admissao: new Date("2020-02-14"),
    ativo: true
  },
  {
    nome: "Tiago Moreira",
    cpf: "404.505.606-77",
    telefone: "(81) 99104-4444",
    email: "tiago@revendedora.com",
    especialidades: ["motor", "transmissão", "freios"],
    salario: 3300.00,
    data_admissao: new Date("2017-11-30"),
    ativo: true
  },
  {
    nome: "Wellington Gomes",
    cpf: "505.606.707-88",
    telefone: "(81) 99105-5555",
    email: "wellington@revendedora.com",
    especialidades: ["suspensão", "alinhamento", "balanceamento"],
    salario: 2900.00,
    data_admissao: new Date("2021-05-17"),
    ativo: true
  },
  {
    nome: "Fábio Cavalcante",
    cpf: "606.707.808-99",
    telefone: "(81) 99106-6666",
    email: "fabio@revendedora.com",
    especialidades: ["funilaria", "pintura"],
    salario: 2800.00,
    data_admissao: new Date("2022-03-08"),
    ativo: false
  },
  {
    nome: "Alexandre Pereira",
    cpf: "707.808.909-00",
    telefone: "(81) 99107-7777",
    email: "alexandre@revendedora.com",
    especialidades: ["elétrica", "motor", "transmissão", "ar-condicionado"],
    salario: 3500.00,
    data_admissao: new Date("2016-09-01"),
    ativo: true
  },
  {
    nome: "Bruno Cardoso",
    cpf: "808.909.010-11",
    telefone: "(81) 99108-8888",
    email: "bruno.cardoso@revendedora.com",
    especialidades: ["estética", "higienização", "polimento"],
    salario: 2600.00,
    data_admissao: new Date("2023-01-10"),
    ativo: true
  },
  {
    nome: "Edmilson Santos",
    cpf: "909.010.111-22",
    telefone: "(81) 99109-9999",
    email: "edmilson@revendedora.com",
    especialidades: ["motor", "freios", "suspensão", "transmissão"],
    salario: 3400.00,
    data_admissao: new Date("2015-06-20"),
    ativo: true
  },
  {
    nome: "Paulo Henrique Dias",
    cpf: "010.111.222-33",
    telefone: "(81) 99110-0000",
    email: "paulo.dias@revendedora.com",
    especialidades: ["ar-condicionado", "elétrica", "som"],
    salario: 2950.00,
    data_admissao: new Date("2021-09-15"),
    ativo: true
  }
])
```

---

## BLOCO 4 - Coleção `veiculos` (100 documentos, divididos em 3 inserções)

### Parte 1 - Veículos populares (43 documentos)

```javascript
db.veiculos.insertMany([
  {
    marca: "Volkswagen",
    modelo: "Gol",
    ano_fabricacao: 2018,
    ano_modelo: 2019,
    cor: "Branco",
    quilometragem: 52000,
    preco: 38000.00,
    categoria: "hatch",
    opcionais: ["ar-condicionado", "direção hidráulica", "travas elétricas"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Gol em ótimo estado, revisado, ideal para uso urbano e baixo consumo"
  },
  {
    marca: "Chevrolet",
    modelo: "Onix",
    ano_fabricacao: 2020,
    ano_modelo: 2020,
    cor: "Prata",
    quilometragem: 31000,
    preco: 58000.00,
    categoria: "hatch",
    opcionais: ["ar-condicionado", "vidros elétricos", "sensor de ré", "câmera de ré", "bluetooth"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Onix Plus automático com baixa quilometragem, perfeito para motoristas de aplicativo"
  },
  {
    marca: "Hyundai",
    modelo: "HB20",
    ano_fabricacao: 2021,
    ano_modelo: 2021,
    cor: "Azul",
    quilometragem: 18000,
    preco: 62000.00,
    categoria: "hatch",
    opcionais: ["ar-condicionado", "vidros elétricos", "travas elétricas", "bluetooth"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "HB20 Vision com pouquíssimo uso, em perfeito estado, primeira revisão feita"
  },
  {
    marca: "Renault",
    modelo: "Kwid",
    ano_fabricacao: 2021,
    ano_modelo: 2021,
    cor: "Laranja",
    quilometragem: 19000,
    preco: 35000.00,
    categoria: "hatch",
    opcionais: ["ar-condicionado", "direção elétrica", "bluetooth"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Kwid Intense automático, econômico e prático para cidade, primeiro carro ideal"
  },
  {
    marca: "Fiat",
    modelo: "Argo",
    ano_fabricacao: 2019,
    ano_modelo: 2020,
    cor: "Vermelho",
    quilometragem: 41000,
    preco: 45000.00,
    categoria: "hatch",
    opcionais: ["ar-condicionado", "direção elétrica", "travas elétricas", "bluetooth"],
    num_donos_anteriores: 2,
    status: "disponivel",
    descricao: "Argo Drive 1.0 em bom estado, revisado, econômico e ótimo para cidade"
  },
  {
    marca: "Volkswagen",
    modelo: "Polo",
    ano_fabricacao: 2021,
    ano_modelo: 2021,
    cor: "Branco",
    quilometragem: 24000,
    preco: 72000.00,
    categoria: "hatch",
    opcionais: ["ar-condicionado", "vidros elétricos", "bluetooth", "sensor de ré", "rodas de liga"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Polo TSI automático, esportivo e econômico, ótimo para quem busca conforto em hatch"
  },
  {
    marca: "Toyota",
    modelo: "Corolla",
    ano_fabricacao: 2019,
    ano_modelo: 2020,
    cor: "Preto",
    quilometragem: 45000,
    preco: 95000.00,
    categoria: "sedan",
    opcionais: ["ar-condicionado", "couro", "teto solar", "câmera de ré", "sensor de estacionamento", "bluetooth"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Corolla XEI impecável, couro legítimo, teto solar, revisões todas na concessionária"
  },
  {
    marca: "Honda",
    modelo: "Civic",
    ano_fabricacao: 2019,
    ano_modelo: 2019,
    cor: "Prata",
    quilometragem: 38000,
    preco: 105000.00,
    categoria: "sedan",
    opcionais: ["ar-condicionado", "couro", "câmera de ré", "sensor de estacionamento", "bluetooth", "rodas de liga"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Civic EXL turbo automático, único dono, sem detalhes, revisado na concessionária"
  },
  {
    marca: "Toyota",
    modelo: "Yaris",
    ano_fabricacao: 2020,
    ano_modelo: 2020,
    cor: "Prata",
    quilometragem: 36000,
    preco: 75000.00,
    categoria: "sedan",
    opcionais: ["ar-condicionado", "vidros elétricos", "câmera de ré", "bluetooth", "sensor de ré"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Yaris XLS sedan automático, confortável e econômico, revisões feitas na Toyota"
  },
  {
    marca: "Volkswagen",
    modelo: "Virtus",
    ano_fabricacao: 2022,
    ano_modelo: 2022,
    cor: "Branco",
    quilometragem: 15000,
    preco: 88000.00,
    categoria: "sedan",
    opcionais: ["ar-condicionado", "vidros elétricos", "câmera de ré", "bluetooth", "sensor de estacionamento", "rodas de liga"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Virtus Highline TSI automático com pouquíssimo uso, esportivo e elegante"
  },
  {
    marca: "Volkswagen",
    modelo: "Jetta",
    ano_fabricacao: 2014,
    ano_modelo: 2015,
    cor: "Bege",
    quilometragem: 126644,
    preco: 114600.00,
    categoria: "sedan",
    opcionais: ["sensor de ré", "direção elétrica", "faróis de LED", "câmera de ré"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Volkswagen Jetta completo, revisões feitas na concessionária, sem detalhes"
  },
  {
    marca: "Volkswagen",
    modelo: "Voyage",
    ano_fabricacao: 2016,
    ano_modelo: 2016,
    cor: "Vermelho",
    quilometragem: 80135,
    preco: 65700.00,
    categoria: "sedan",
    opcionais: ["faróis de LED", "start-stop", "couro", "vidros elétricos", "tração 4x4", "travas elétricas"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Volkswagen Voyage completo, revisões feitas na concessionária, sem detalhes"
  },
  {
    marca: "Volkswagen",
    modelo: "Up",
    ano_fabricacao: 2021,
    ano_modelo: 2021,
    cor: "Branco",
    quilometragem: 33272,
    preco: 37400.00,
    categoria: "hatch",
    opcionais: ["bluetooth", "piloto automático", "couro", "travas elétricas", "teto solar"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Volkswagen Up automático com baixa quilometragem, único dono"
  },
  {
    marca: "Volkswagen",
    modelo: "Fox",
    ano_fabricacao: 2019,
    ano_modelo: 2019,
    cor: "Azul",
    quilometragem: 82420,
    preco: 74200.00,
    categoria: "hatch",
    opcionais: ["bluetooth", "tração 4x4", "central multimídia", "câmera de ré"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Volkswagen Fox diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Volkswagen",
    modelo: "CrossFox",
    ano_fabricacao: 2020,
    ano_modelo: 2021,
    cor: "Vermelho",
    quilometragem: 20502,
    preco: 42100.00,
    categoria: "hatch",
    opcionais: ["faróis de LED", "couro", "piloto automático", "vidros elétricos"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Volkswagen CrossFox em ótimo estado, revisado, ideal para uso urbano"
  },
  {
    marca: "Chevrolet",
    modelo: "Cruze",
    ano_fabricacao: 2017,
    ano_modelo: 2017,
    cor: "Cinza",
    quilometragem: 106796,
    preco: 80000.00,
    categoria: "sedan",
    opcionais: ["rodas de liga", "ar-condicionado", "travas elétricas", "couro", "bluetooth"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Chevrolet Cruze seminovo, praticamente zero, garantia de fábrica"
  },
  {
    marca: "Chevrolet",
    modelo: "Cobalt",
    ano_fabricacao: 2015,
    ano_modelo: 2015,
    cor: "Cinza",
    quilometragem: 48213,
    preco: 65900.00,
    categoria: "sedan",
    opcionais: ["start-stop", "rodas de liga", "teto solar", "direção elétrica", "couro", "travas elétricas"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Chevrolet Cobalt completo, revisões feitas na concessionária, sem detalhes"
  },
  {
    marca: "Chevrolet",
    modelo: "Prisma",
    ano_fabricacao: 2016,
    ano_modelo: 2016,
    cor: "Cinza",
    quilometragem: 28078,
    preco: 104600.00,
    categoria: "sedan",
    opcionais: ["teto solar", "central multimídia", "start-stop", "sensor de estacionamento", "sensor de ré", "faróis de LED", "couro"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Chevrolet Prisma flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Chevrolet",
    modelo: "Celta",
    ano_fabricacao: 2014,
    ano_modelo: 2014,
    cor: "Verde",
    quilometragem: 61591,
    preco: 41800.00,
    categoria: "hatch",
    opcionais: ["central multimídia", "teto solar", "piloto automático", "câmera de ré"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Chevrolet Celta turbo automático, esportivo e econômico"
  },
  {
    marca: "Chevrolet",
    modelo: "Joy",
    ano_fabricacao: 2015,
    ano_modelo: 2016,
    cor: "Marrom",
    quilometragem: 94742,
    preco: 65300.00,
    categoria: "hatch",
    opcionais: ["teto solar", "vidros elétricos", "direção hidráulica", "sensor de estacionamento"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Chevrolet Joy turbo automático, esportivo e econômico"
  },
  {
    marca: "Toyota",
    modelo: "Etios",
    ano_fabricacao: 2021,
    ano_modelo: 2021,
    cor: "Azul",
    quilometragem: 78747,
    preco: 44200.00,
    categoria: "hatch",
    opcionais: ["travas elétricas", "rodas de liga", "vidros elétricos"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Toyota Etios flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Toyota",
    modelo: "Camry",
    ano_fabricacao: 2023,
    ano_modelo: 2024,
    cor: "Verde",
    quilometragem: 115267,
    preco: 87000.00,
    categoria: "sedan",
    opcionais: ["rodas de liga", "travas elétricas", "couro", "sensor de estacionamento"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Toyota Camry automático com baixa quilometragem, único dono"
  },
  {
    marca: "Honda",
    modelo: "City",
    ano_fabricacao: 2018,
    ano_modelo: 2018,
    cor: "Verde",
    quilometragem: 80970,
    preco: 122600.00,
    categoria: "sedan",
    opcionais: ["central multimídia", "faróis de LED", "ar-condicionado", "bluetooth"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Honda City seminovo, praticamente zero, garantia de fábrica"
  },
  {
    marca: "Honda",
    modelo: "Accord",
    ano_fabricacao: 2019,
    ano_modelo: 2020,
    cor: "Bege",
    quilometragem: 62568,
    preco: 98500.00,
    categoria: "sedan",
    opcionais: ["rodas de liga", "tração 4x4", "direção hidráulica", "faróis de LED"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Honda Accord diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Honda",
    modelo: "Fit",
    ano_fabricacao: 2022,
    ano_modelo: 2023,
    cor: "Branco",
    quilometragem: 116711,
    preco: 42500.00,
    categoria: "hatch",
    opcionais: ["sensor de estacionamento", "tração 4x4", "couro"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Honda Fit diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Hyundai",
    modelo: "Elantra",
    ano_fabricacao: 2021,
    ano_modelo: 2021,
    cor: "Preto",
    quilometragem: 127843,
    preco: 71600.00,
    categoria: "sedan",
    opcionais: ["couro", "central multimídia", "ar-condicionado", "rodas de liga", "vidros elétricos"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Hyundai Elantra seminovo, praticamente zero, garantia de fábrica"
  },
  {
    marca: "Hyundai",
    modelo: "i30",
    ano_fabricacao: 2018,
    ano_modelo: 2019,
    cor: "Cinza",
    quilometragem: 84550,
    preco: 68000.00,
    categoria: "hatch",
    opcionais: ["rodas de liga", "travas elétricas", "vidros elétricos", "bluetooth", "piloto automático", "câmera de ré"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Hyundai i30 diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Nissan",
    modelo: "Sentra",
    ano_fabricacao: 2022,
    ano_modelo: 2023,
    cor: "Azul",
    quilometragem: 97764,
    preco: 89200.00,
    categoria: "sedan",
    opcionais: ["faróis de LED", "start-stop", "sensor de ré", "direção hidráulica", "teto solar"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Nissan Sentra flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Nissan",
    modelo: "Versa",
    ano_fabricacao: 2016,
    ano_modelo: 2017,
    cor: "Branco",
    quilometragem: 79636,
    preco: 109000.00,
    categoria: "sedan",
    opcionais: ["direção elétrica", "start-stop", "central multimídia", "piloto automático"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Nissan Versa em ótimo estado, revisado, ideal para uso urbano"
  },
  {
    marca: "Nissan",
    modelo: "March",
    ano_fabricacao: 2018,
    ano_modelo: 2019,
    cor: "Marrom",
    quilometragem: 45576,
    preco: 31100.00,
    categoria: "hatch",
    opcionais: ["central multimídia", "bluetooth", "direção elétrica", "piloto automático", "sensor de estacionamento", "direção hidráulica", "vidros elétricos"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Nissan March automático com baixa quilometragem, único dono"
  },
  {
    marca: "Ford",
    modelo: "Ka",
    ano_fabricacao: 2021,
    ano_modelo: 2021,
    cor: "Azul",
    quilometragem: 91459,
    preco: 30600.00,
    categoria: "hatch",
    opcionais: ["direção hidráulica", "faróis de LED", "central multimídia", "câmera de ré"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Ford Ka seminovo, praticamente zero, garantia de fábrica"
  },
  {
    marca: "Ford",
    modelo: "Fiesta",
    ano_fabricacao: 2015,
    ano_modelo: 2016,
    cor: "Vermelho",
    quilometragem: 128475,
    preco: 32800.00,
    categoria: "hatch",
    opcionais: ["câmera de ré", "faróis de LED", "travas elétricas", "ar-condicionado"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Ford Fiesta em ótimo estado, revisado, ideal para uso urbano"
  },
  {
    marca: "Ford",
    modelo: "Fusion",
    ano_fabricacao: 2023,
    ano_modelo: 2024,
    cor: "Verde",
    quilometragem: 12312,
    preco: 68500.00,
    categoria: "sedan",
    opcionais: ["ar-condicionado", "câmera de ré", "rodas de liga", "direção hidráulica", "tração 4x4"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Ford Fusion flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Fiat",
    modelo: "Cronos",
    ano_fabricacao: 2015,
    ano_modelo: 2015,
    cor: "Bege",
    quilometragem: 38427,
    preco: 55000.00,
    categoria: "sedan",
    opcionais: ["tração 4x4", "couro", "ar-condicionado", "faróis de LED", "travas elétricas"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Fiat Cronos flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Fiat",
    modelo: "Mobi",
    ano_fabricacao: 2017,
    ano_modelo: 2017,
    cor: "Cinza",
    quilometragem: 80487,
    preco: 54600.00,
    categoria: "hatch",
    opcionais: ["bluetooth", "tração 4x4", "direção elétrica", "faróis de LED", "rodas de liga", "travas elétricas"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Fiat Mobi flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Fiat",
    modelo: "Uno",
    ano_fabricacao: 2015,
    ano_modelo: 2015,
    cor: "Vermelho",
    quilometragem: 43123,
    preco: 40100.00,
    categoria: "hatch",
    opcionais: ["travas elétricas", "tração 4x4", "bluetooth", "piloto automático", "direção elétrica", "faróis de LED"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Fiat Uno em ótimo estado, revisado, ideal para uso urbano"
  },
  {
    marca: "Renault",
    modelo: "Sandero",
    ano_fabricacao: 2015,
    ano_modelo: 2016,
    cor: "Preto",
    quilometragem: 126113,
    preco: 66700.00,
    categoria: "hatch",
    opcionais: ["start-stop", "bluetooth", "couro", "câmera de ré"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Renault Sandero automático com baixa quilometragem, único dono"
  },
  {
    marca: "Renault",
    modelo: "Stepway",
    ano_fabricacao: 2018,
    ano_modelo: 2018,
    cor: "Vermelho",
    quilometragem: 72634,
    preco: 39600.00,
    categoria: "hatch",
    opcionais: ["bluetooth", "central multimídia", "travas elétricas"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Renault Stepway turbo automático, esportivo e econômico"
  },
  {
    marca: "Renault",
    modelo: "Logan",
    ano_fabricacao: 2015,
    ano_modelo: 2015,
    cor: "Azul",
    quilometragem: 40990,
    preco: 77300.00,
    categoria: "sedan",
    opcionais: ["câmera de ré", "piloto automático", "direção elétrica", "direção hidráulica", "travas elétricas", "ar-condicionado"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Renault Logan turbo automático, esportivo e econômico"
  },
  {
    marca: "Peugeot",
    modelo: "208",
    ano_fabricacao: 2021,
    ano_modelo: 2022,
    cor: "Marrom",
    quilometragem: 70814,
    preco: 68200.00,
    categoria: "hatch",
    opcionais: ["start-stop", "central multimídia", "sensor de estacionamento", "ar-condicionado", "tração 4x4", "bluetooth"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Peugeot 208 seminovo, praticamente zero, garantia de fábrica"
  },
  {
    marca: "Citroën",
    modelo: "C3",
    ano_fabricacao: 2015,
    ano_modelo: 2015,
    cor: "Verde",
    quilometragem: 108788,
    preco: 46300.00,
    categoria: "hatch",
    opcionais: ["bluetooth", "direção elétrica", "rodas de liga", "couro", "central multimídia"],
    num_donos_anteriores: 2,
    status: "reservado",
    descricao: "Citroën C3 seminovo, praticamente zero, garantia de fábrica"
  },
  {
    marca: "Kia",
    modelo: "Cerato",
    ano_fabricacao: 2023,
    ano_modelo: 2023,
    cor: "Prata",
    quilometragem: 66926,
    preco: 122600.00,
    categoria: "sedan",
    opcionais: ["tração 4x4", "ar-condicionado", "teto solar", "vidros elétricos", "central multimídia", "travas elétricas"],
    num_donos_anteriores: 3,
    status: "disponivel",
    descricao: "Kia Cerato flex, ótimo custo-benefício, documentação em dia"
  }
])
```

### Parte 2 - Veículos intermediários (47 documentos)

```javascript
db.veiculos.insertMany([
  {
    marca: "Honda",
    modelo: "HR-V",
    ano_fabricacao: 2020,
    ano_modelo: 2021,
    cor: "Vermelho",
    quilometragem: 28000,
    preco: 115000.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "couro", "câmera de ré", "sensor de estacionamento", "bluetooth", "rodas de liga"],
    num_donos_anteriores: 1,
    status: "reservado",
    descricao: "HR-V EXL automático, único dono, documentação em dia, excelente estado de conservação"
  },
  {
    marca: "Ford",
    modelo: "Ranger",
    ano_fabricacao: 2018,
    ano_modelo: 2018,
    cor: "Cinza",
    quilometragem: 78000,
    preco: 135000.00,
    categoria: "pickup",
    opcionais: ["ar-condicionado", "tração 4x4", "caçamba revestida", "bluetooth", "sensor de ré"],
    num_donos_anteriores: 2,
    status: "disponivel",
    descricao: "Ranger XLS 4x4 diesel, revisada, ideal para trabalho no campo e cidade"
  },
  {
    marca: "Jeep",
    modelo: "Compass",
    ano_fabricacao: 2019,
    ano_modelo: 2020,
    cor: "Branco",
    quilometragem: 55000,
    preco: 128000.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "couro", "teto solar", "câmera de ré", "sensor de estacionamento", "bluetooth", "rodas de liga", "tração 4x4"],
    num_donos_anteriores: 2,
    status: "disponivel",
    descricao: "Compass Limited com teto solar e tração 4x4, completo de opcionais"
  },
  {
    marca: "Fiat",
    modelo: "Strada",
    ano_fabricacao: 2021,
    ano_modelo: 2022,
    cor: "Branco",
    quilometragem: 22000,
    preco: 85000.00,
    categoria: "pickup",
    opcionais: ["ar-condicionado", "direção elétrica", "bluetooth", "câmera de ré"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Strada Volcano cabine dupla, pouco uso, ótima para trabalho e lazer"
  },
  {
    marca: "Renault",
    modelo: "Duster",
    ano_fabricacao: 2017,
    ano_modelo: 2018,
    cor: "Prata",
    quilometragem: 91000,
    preco: 55000.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "direção hidráulica", "travas elétricas"],
    num_donos_anteriores: 3,
    status: "disponivel",
    descricao: "Duster Expression com km rodada, revisado recentemente, bom custo-benefício"
  },
  {
    marca: "Volkswagen",
    modelo: "T-Cross",
    ano_fabricacao: 2022,
    ano_modelo: 2022,
    cor: "Laranja",
    quilometragem: 12000,
    preco: 118000.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "vidros elétricos", "câmera de ré", "sensor de estacionamento", "bluetooth", "rodas de liga", "teto solar"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "T-Cross Highline seminovo com apenas 12 mil km, todos os opcionais de fábrica"
  },
  {
    marca: "Chevrolet",
    modelo: "S10",
    ano_fabricacao: 2019,
    ano_modelo: 2020,
    cor: "Preto",
    quilometragem: 64000,
    preco: 148000.00,
    categoria: "pickup",
    opcionais: ["ar-condicionado", "couro", "tração 4x4", "bluetooth", "sensor de ré", "câmera de ré", "rodas de liga"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "S10 LTZ 4x4 diesel automática, completa, revisada e com laudo cautelar aprovado"
  },
  {
    marca: "Toyota",
    modelo: "Hilux",
    ano_fabricacao: 2020,
    ano_modelo: 2021,
    cor: "Cinza",
    quilometragem: 47000,
    preco: 210000.00,
    categoria: "pickup",
    opcionais: ["ar-condicionado", "couro", "tração 4x4", "bluetooth", "sensor de ré", "câmera de ré", "rodas de liga", "teto solar"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Hilux SRX automática diesel, o mais completo da categoria, revisões na Toyota"
  },
  {
    marca: "Fiat",
    modelo: "Pulse",
    ano_fabricacao: 2022,
    ano_modelo: 2023,
    cor: "Vermelho",
    quilometragem: 9000,
    preco: 98000.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "vidros elétricos", "câmera de ré", "bluetooth", "sensor de estacionamento"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Pulse Impetus turbo com apenas 9 mil km, praticamente zero, garantia de fábrica"
  },
  {
    marca: "Nissan",
    modelo: "Kicks",
    ano_fabricacao: 2020,
    ano_modelo: 2021,
    cor: "Branco",
    quilometragem: 33000,
    preco: 102000.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "câmera de ré", "bluetooth", "sensor de estacionamento", "rodas de liga"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Kicks SV CVT automático, excelente custo-benefício no segmento de SUVs compactos"
  },
  {
    marca: "Hyundai",
    modelo: "Creta",
    ano_fabricacao: 2021,
    ano_modelo: 2022,
    cor: "Cinza",
    quilometragem: 21000,
    preco: 122000.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "couro", "teto solar", "câmera de ré", "sensor de estacionamento", "bluetooth", "rodas de liga"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Creta Ultimate com teto solar panorâmico, couro e todos os opcionais, único dono"
  },
  {
    marca: "Chevrolet",
    modelo: "Tracker",
    ano_fabricacao: 2021,
    ano_modelo: 2022,
    cor: "Azul",
    quilometragem: 27000,
    preco: 108000.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "vidros elétricos", "câmera de ré", "bluetooth", "sensor de estacionamento", "rodas de liga"],
    num_donos_anteriores: 1,
    status: "reservado",
    descricao: "Tracker Premier turbo automático, baixa quilometragem, excelente conservação"
  },
  {
    marca: "Mitsubishi",
    modelo: "L200 Triton",
    ano_fabricacao: 2019,
    ano_modelo: 2019,
    cor: "Preto",
    quilometragem: 82000,
    preco: 162000.00,
    categoria: "pickup",
    opcionais: ["ar-condicionado", "couro", "tração 4x4", "bluetooth", "câmera de ré", "rodas de liga"],
    num_donos_anteriores: 2,
    status: "disponivel",
    descricao: "L200 Triton Sport HPE 4x4 diesel, robusta e bem equipada, revisada e com laudo aprovado"
  },
  {
    marca: "Honda",
    modelo: "WR-V",
    ano_fabricacao: 2019,
    ano_modelo: 2019,
    cor: "Cinza",
    quilometragem: 58000,
    preco: 78000.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "câmera de ré", "bluetooth", "sensor de estacionamento", "rodas de liga"],
    num_donos_anteriores: 2,
    status: "disponivel",
    descricao: "WR-V EX automático, espaçoso e econômico, revisado e com pneus novos"
  },
  {
    marca: "Jeep",
    modelo: "Renegade",
    ano_fabricacao: 2020,
    ano_modelo: 2021,
    cor: "Verde",
    quilometragem: 43000,
    preco: 112000.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "couro", "câmera de ré", "sensor de estacionamento", "bluetooth", "rodas de liga", "tração 4x4"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Renegade Longitude 4x4 automático, completo, revisado e com garantia estendida"
  },
  {
    marca: "Volkswagen",
    modelo: "Nivus",
    ano_fabricacao: 2017,
    ano_modelo: 2018,
    cor: "Vermelho",
    quilometragem: 100404,
    preco: 134100.00,
    categoria: "SUV",
    opcionais: ["faróis de LED", "teto solar", "sensor de estacionamento", "tração 4x4", "start-stop"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Volkswagen Nivus completo, revisões feitas na concessionária, sem detalhes"
  },
  {
    marca: "Volkswagen",
    modelo: "Taos",
    ano_fabricacao: 2023,
    ano_modelo: 2024,
    cor: "Azul",
    quilometragem: 79197,
    preco: 119800.00,
    categoria: "SUV",
    opcionais: ["teto solar", "travas elétricas", "faróis de LED", "ar-condicionado", "piloto automático", "start-stop"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Volkswagen Taos em ótimo estado, revisado, ideal para uso urbano"
  },
  {
    marca: "Volkswagen",
    modelo: "Tiguan",
    ano_fabricacao: 2018,
    ano_modelo: 2019,
    cor: "Cinza",
    quilometragem: 70793,
    preco: 98000.00,
    categoria: "SUV",
    opcionais: ["sensor de estacionamento", "start-stop", "direção hidráulica", "direção elétrica"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Volkswagen Tiguan diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Volkswagen",
    modelo: "Saveiro",
    ano_fabricacao: 2014,
    ano_modelo: 2014,
    cor: "Bege",
    quilometragem: 93498,
    preco: 150900.00,
    categoria: "pickup",
    opcionais: ["direção elétrica", "bluetooth", "câmera de ré", "central multimídia", "direção hidráulica", "ar-condicionado", "piloto automático"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Volkswagen Saveiro flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Volkswagen",
    modelo: "Amarok",
    ano_fabricacao: 2018,
    ano_modelo: 2018,
    cor: "Preto",
    quilometragem: 9214,
    preco: 168200.00,
    categoria: "pickup",
    opcionais: ["vidros elétricos", "couro", "travas elétricas", "sensor de ré", "faróis de LED", "sensor de estacionamento", "teto solar"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Volkswagen Amarok turbo automático, esportivo e econômico"
  },
  {
    marca: "Chevrolet",
    modelo: "Spin",
    ano_fabricacao: 2023,
    ano_modelo: 2023,
    cor: "Cinza",
    quilometragem: 76879,
    preco: 128600.00,
    categoria: "SUV",
    opcionais: ["teto solar", "direção hidráulica", "piloto automático", "rodas de liga", "direção elétrica", "ar-condicionado", "sensor de estacionamento"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Chevrolet Spin diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Chevrolet",
    modelo: "Equinox",
    ano_fabricacao: 2022,
    ano_modelo: 2022,
    cor: "Marrom",
    quilometragem: 29566,
    preco: 113000.00,
    categoria: "SUV",
    opcionais: ["piloto automático", "vidros elétricos", "couro", "faróis de LED", "teto solar", "rodas de liga", "sensor de ré"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Chevrolet Equinox em ótimo estado, revisado, ideal para uso urbano"
  },
  {
    marca: "Chevrolet",
    modelo: "Trailblazer",
    ano_fabricacao: 2014,
    ano_modelo: 2014,
    cor: "Branco",
    quilometragem: 25294,
    preco: 137300.00,
    categoria: "SUV",
    opcionais: ["piloto automático", "direção elétrica", "sensor de estacionamento", "sensor de ré", "couro", "travas elétricas"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Chevrolet Trailblazer seminovo, praticamente zero, garantia de fábrica"
  },
  {
    marca: "Chevrolet",
    modelo: "Montana",
    ano_fabricacao: 2018,
    ano_modelo: 2018,
    cor: "Prata",
    quilometragem: 105754,
    preco: 147100.00,
    categoria: "pickup",
    opcionais: ["direção hidráulica", "direção elétrica", "câmera de ré", "bluetooth", "teto solar", "faróis de LED", "sensor de estacionamento"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Chevrolet Montana em ótimo estado, revisado, ideal para uso urbano"
  },
  {
    marca: "Toyota",
    modelo: "Corolla Cross",
    ano_fabricacao: 2017,
    ano_modelo: 2017,
    cor: "Bege",
    quilometragem: 107113,
    preco: 73000.00,
    categoria: "SUV",
    opcionais: ["piloto automático", "central multimídia", "sensor de estacionamento", "câmera de ré", "vidros elétricos"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Toyota Corolla Cross automático com baixa quilometragem, único dono"
  },
  {
    marca: "Toyota",
    modelo: "SW4",
    ano_fabricacao: 2016,
    ano_modelo: 2016,
    cor: "Branco",
    quilometragem: 32704,
    preco: 165000.00,
    categoria: "SUV",
    opcionais: ["direção elétrica", "central multimídia", "rodas de liga"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Toyota SW4 flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Toyota",
    modelo: "RAV4",
    ano_fabricacao: 2017,
    ano_modelo: 2017,
    cor: "Branco",
    quilometragem: 21224,
    preco: 147800.00,
    categoria: "SUV",
    opcionais: ["piloto automático", "direção elétrica", "vidros elétricos"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Toyota RAV4 seminovo, praticamente zero, garantia de fábrica"
  },
  {
    marca: "Honda",
    modelo: "CR-V",
    ano_fabricacao: 2017,
    ano_modelo: 2017,
    cor: "Marrom",
    quilometragem: 120399,
    preco: 162700.00,
    categoria: "SUV",
    opcionais: ["piloto automático", "direção elétrica", "sensor de estacionamento", "câmera de ré"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Honda CR-V turbo automático, esportivo e econômico"
  },
  {
    marca: "Honda",
    modelo: "ZR-V",
    ano_fabricacao: 2016,
    ano_modelo: 2016,
    cor: "Azul",
    quilometragem: 39831,
    preco: 103400.00,
    categoria: "SUV",
    opcionais: ["couro", "direção hidráulica", "piloto automático", "sensor de ré"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Honda ZR-V flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Hyundai",
    modelo: "Tucson",
    ano_fabricacao: 2017,
    ano_modelo: 2018,
    cor: "Cinza",
    quilometragem: 102936,
    preco: 158000.00,
    categoria: "SUV",
    opcionais: ["câmera de ré", "faróis de LED", "vidros elétricos", "central multimídia", "bluetooth", "travas elétricas", "ar-condicionado"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Hyundai Tucson automático com baixa quilometragem, único dono"
  },
  {
    marca: "Hyundai",
    modelo: "ix35",
    ano_fabricacao: 2015,
    ano_modelo: 2016,
    cor: "Azul",
    quilometragem: 106871,
    preco: 132800.00,
    categoria: "SUV",
    opcionais: ["câmera de ré", "tração 4x4", "piloto automático", "vidros elétricos"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Hyundai ix35 diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Hyundai",
    modelo: "Santa Fe",
    ano_fabricacao: 2020,
    ano_modelo: 2020,
    cor: "Prata",
    quilometragem: 77946,
    preco: 155000.00,
    categoria: "SUV",
    opcionais: ["rodas de liga", "sensor de estacionamento", "bluetooth", "faróis de LED", "sensor de ré"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Hyundai Santa Fe turbo automático, esportivo e econômico"
  },
  {
    marca: "Nissan",
    modelo: "Frontier",
    ano_fabricacao: 2020,
    ano_modelo: 2020,
    cor: "Bege",
    quilometragem: 118434,
    preco: 150700.00,
    categoria: "pickup",
    opcionais: ["travas elétricas", "ar-condicionado", "vidros elétricos"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Nissan Frontier diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Nissan",
    modelo: "X-Trail",
    ano_fabricacao: 2014,
    ano_modelo: 2015,
    cor: "Branco",
    quilometragem: 91588,
    preco: 157400.00,
    categoria: "SUV",
    opcionais: ["faróis de LED", "start-stop", "ar-condicionado", "piloto automático", "sensor de estacionamento", "tração 4x4", "câmera de ré"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Nissan X-Trail em ótimo estado, revisado, ideal para uso urbano"
  },
  {
    marca: "Ford",
    modelo: "EcoSport",
    ano_fabricacao: 2019,
    ano_modelo: 2019,
    cor: "Cinza",
    quilometragem: 112193,
    preco: 122000.00,
    categoria: "SUV",
    opcionais: ["teto solar", "tração 4x4", "sensor de ré"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Ford EcoSport diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Ford",
    modelo: "Territory",
    ano_fabricacao: 2017,
    ano_modelo: 2017,
    cor: "Verde",
    quilometragem: 97658,
    preco: 178500.00,
    categoria: "SUV",
    opcionais: ["direção elétrica", "direção hidráulica", "câmera de ré"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Ford Territory turbo automático, esportivo e econômico"
  },
  {
    marca: "Fiat",
    modelo: "Toro",
    ano_fabricacao: 2018,
    ano_modelo: 2018,
    cor: "Azul",
    quilometragem: 81919,
    preco: 153000.00,
    categoria: "pickup",
    opcionais: ["tração 4x4", "couro", "câmera de ré", "start-stop", "teto solar", "direção hidráulica", "direção elétrica"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Fiat Toro diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Fiat",
    modelo: "Fastback",
    ano_fabricacao: 2019,
    ano_modelo: 2019,
    cor: "Marrom",
    quilometragem: 21399,
    preco: 87400.00,
    categoria: "SUV",
    opcionais: ["bluetooth", "central multimídia", "sensor de ré"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Fiat Fastback diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Renault",
    modelo: "Captur",
    ano_fabricacao: 2020,
    ano_modelo: 2020,
    cor: "Verde",
    quilometragem: 11442,
    preco: 81700.00,
    categoria: "SUV",
    opcionais: ["direção hidráulica", "couro", "central multimídia", "câmera de ré", "ar-condicionado"],
    num_donos_anteriores: 2,
    status: "vendido",
    descricao: "Renault Captur completo, revisões feitas na concessionária, sem detalhes"
  },
  {
    marca: "Renault",
    modelo: "Oroch",
    ano_fabricacao: 2020,
    ano_modelo: 2020,
    cor: "Azul",
    quilometragem: 65700,
    preco: 177700.00,
    categoria: "pickup",
    opcionais: ["travas elétricas", "rodas de liga", "bluetooth", "faróis de LED", "teto solar", "vidros elétricos"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Renault Oroch turbo automático, esportivo e econômico"
  },
  {
    marca: "Jeep",
    modelo: "Commander",
    ano_fabricacao: 2020,
    ano_modelo: 2020,
    cor: "Prata",
    quilometragem: 46200,
    preco: 166300.00,
    categoria: "SUV",
    opcionais: ["sensor de ré", "couro", "câmera de ré", "travas elétricas", "tração 4x4", "piloto automático"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Jeep Commander completo, revisões feitas na concessionária, sem detalhes"
  },
  {
    marca: "Jeep",
    modelo: "Wrangler",
    ano_fabricacao: 2017,
    ano_modelo: 2018,
    cor: "Verde",
    quilometragem: 79516,
    preco: 93600.00,
    categoria: "SUV",
    opcionais: ["ar-condicionado", "piloto automático", "teto solar", "vidros elétricos", "sensor de ré", "travas elétricas", "direção elétrica"],
    num_donos_anteriores: 3,
    status: "vendido",
    descricao: "Jeep Wrangler flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Peugeot",
    modelo: "2008",
    ano_fabricacao: 2021,
    ano_modelo: 2021,
    cor: "Verde",
    quilometragem: 91012,
    preco: 109700.00,
    categoria: "SUV",
    opcionais: ["sensor de estacionamento", "travas elétricas", "teto solar", "câmera de ré"],
    num_donos_anteriores: 1,
    status: "vendido",
    descricao: "Peugeot 2008 flex, ótimo custo-benefício, documentação em dia"
  },
  {
    marca: "Citroën",
    modelo: "C4 Cactus",
    ano_fabricacao: 2015,
    ano_modelo: 2015,
    cor: "Bege",
    quilometragem: 20924,
    preco: 103900.00,
    categoria: "SUV",
    opcionais: ["start-stop", "sensor de ré", "faróis de LED", "bluetooth"],
    num_donos_anteriores: 3,
    status: "disponivel",
    descricao: "Citroën C4 Cactus turbo automático, esportivo e econômico"
  },
  {
    marca: "Caoa Chery",
    modelo: "Tiggo 5x",
    ano_fabricacao: 2022,
    ano_modelo: 2022,
    cor: "Azul",
    quilometragem: 53215,
    preco: 73200.00,
    categoria: "SUV",
    opcionais: ["vidros elétricos", "rodas de liga", "câmera de ré", "direção elétrica", "central multimídia", "teto solar"],
    num_donos_anteriores: 2,
    status: "reservado",
    descricao: "Caoa Chery Tiggo 5x automático com baixa quilometragem, único dono"
  },
  {
    marca: "Caoa Chery",
    modelo: "Tiggo 7",
    ano_fabricacao: 2021,
    ano_modelo: 2021,
    cor: "Azul",
    quilometragem: 76303,
    preco: 133300.00,
    categoria: "SUV",
    opcionais: ["faróis de LED", "vidros elétricos", "sensor de ré", "teto solar", "central multimídia"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Caoa Chery Tiggo 7 turbo automático, esportivo e econômico"
  },
  {
    marca: "Kia",
    modelo: "Sportage",
    ano_fabricacao: 2014,
    ano_modelo: 2015,
    cor: "Preto",
    quilometragem: 23084,
    preco: 73000.00,
    categoria: "SUV",
    opcionais: ["vidros elétricos", "bluetooth", "piloto automático", "teto solar", "start-stop"],
    num_donos_anteriores: 3,
    status: "disponivel",
    descricao: "Kia Sportage diesel 4x4, robusto e bem equipado, laudo aprovado"
  },
  {
    marca: "Mitsubishi",
    modelo: "ASX",
    ano_fabricacao: 2019,
    ano_modelo: 2020,
    cor: "Verde",
    quilometragem: 63885,
    preco: 130600.00,
    categoria: "SUV",
    opcionais: ["tração 4x4", "bluetooth", "direção hidráulica", "couro"],
    num_donos_anteriores: 2,
    status: "disponivel",
    descricao: "Mitsubishi ASX seminovo, praticamente zero, garantia de fábrica"
  }
])
```

### Parte 3 - Veículos esportivos e retrôs (10 documentos)

```javascript
db.veiculos.insertMany([
  {
    marca: "Ford",
    modelo: "Mustang",
    ano_fabricacao: 2018,
    ano_modelo: 2018,
    cor: "Vermelho",
    quilometragem: 35000,
    preco: 285000.00,
    categoria: "esportivo",
    opcionais: ["ar-condicionado", "couro", "bluetooth", "câmera de ré", "rodas de liga", "modo de condução esportivo", "escapamento esportivo"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Mustang GT 5.0 V8 fastback, som inconfundível, revisado e impecável, raridade no mercado"
  },
  {
    marca: "Chevrolet",
    modelo: "Camaro",
    ano_fabricacao: 2019,
    ano_modelo: 2019,
    cor: "Amarelo",
    quilometragem: 28000,
    preco: 320000.00,
    categoria: "esportivo",
    opcionais: ["ar-condicionado", "couro", "bluetooth", "câmera de ré", "rodas de liga", "modo de condução esportivo", "teto removível"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Camaro SS 2SS V8 automático, conversível, único dono, estado de showroom"
  },
  {
    marca: "Honda",
    modelo: "Civic Si",
    ano_fabricacao: 2020,
    ano_modelo: 2020,
    cor: "Preto",
    quilometragem: 22000,
    preco: 175000.00,
    categoria: "esportivo",
    opcionais: ["ar-condicionado", "couro", "bluetooth", "câmera de ré", "rodas de liga", "modo de condução esportivo", "bancos esportivos"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Civic Si turbo com câmbio manual, extremamente esportivo e responsivo, sem modificações"
  },
  {
    marca: "Toyota",
    modelo: "Supra",
    ano_fabricacao: 2021,
    ano_modelo: 2021,
    cor: "Azul",
    quilometragem: 14000,
    preco: 420000.00,
    categoria: "esportivo",
    opcionais: ["ar-condicionado", "couro", "bluetooth", "câmera de ré", "rodas de liga", "modo de condução esportivo", "head-up display", "bancos esportivos"],
    num_donos_anteriores: 1,
    status: "reservado",
    descricao: "GR Supra 3.0 turbo, lenda reencarnada, praticamente zero, todas as revisões na Toyota"
  },
  {
    marca: "Volkswagen",
    modelo: "Golf GTI",
    ano_fabricacao: 2022,
    ano_modelo: 2022,
    cor: "Cinza",
    quilometragem: 11000,
    preco: 210000.00,
    categoria: "esportivo",
    opcionais: ["ar-condicionado", "couro", "bluetooth", "câmera de ré", "rodas de liga", "modo de condução esportivo", "bancos esportivos", "teto solar"],
    num_donos_anteriores: 1,
    status: "disponivel",
    descricao: "Golf GTI Mk8 com apenas 11 mil km, o hot hatch mais completo do mercado, impecável"
  },
  {
    marca: "Volkswagen",
    modelo: "Fusca",
    ano_fabricacao: 1974,
    ano_modelo: 1974,
    cor: "Bege",
    quilometragem: 98000,
    preco: 42000.00,
    categoria: "retro",
    opcionais: ["rádio vintage", "rodas esportivas"],
    num_donos_anteriores: 3,
    status: "disponivel",
    descricao: "Fusca 1300 original, pintura de fábrica preservada, motor recondicionado, peça de colecionador"
  },
  {
    marca: "Chevrolet",
    modelo: "Opala",
    ano_fabricacao: 1988,
    ano_modelo: 1988,
    cor: "Branco",
    quilometragem: 112000,
    preco: 68000.00,
    categoria: "retro",
    opcionais: ["ar-condicionado", "rádio vintage", "bancos em couro"],
    num_donos_anteriores: 2,
    status: "disponivel",
    descricao: "Opala Comodoro 6cc último ano de fabricação, interior original preservado, clássico brasileiro"
  },
  {
    marca: "Ford",
    modelo: "Corcel II",
    ano_fabricacao: 1981,
    ano_modelo: 1981,
    cor: "Amarelo",
    quilometragem: 87000,
    preco: 28000.00,
    categoria: "retro",
    opcionais: ["rádio vintage"],
    num_donos_anteriores: 4,
    status: "disponivel",
    descricao: "Corcel II sedan em bom estado de conservação, motor original funcionando bem, raridade"
  },
  {
    marca: "Volkswagen",
    modelo: "Brasília",
    ano_fabricacao: 1978,
    ano_modelo: 1978,
    cor: "Verde",
    quilometragem: 76000,
    preco: 35000.00,
    categoria: "retro",
    opcionais: ["rádio vintage", "rodas esportivas"],
    num_donos_anteriores: 3,
    status: "disponivel",
    descricao: "Brasília original com pintura restaurada, mecânica revisada, ícone do design brasileiro"
  },
  {
    marca: "Chevrolet",
    modelo: "Chevette",
    ano_fabricacao: 1992,
    ano_modelo: 1992,
    cor: "Vermelho",
    quilometragem: 65000,
    preco: 22000.00,
    categoria: "retro",
    opcionais: ["rádio vintage"],
    num_donos_anteriores: 2,
    status: "disponivel",
    descricao: "Chevette último ano de fabricação, motor revisado, lataria sem amassados, colecionável"
  }
])
```

---

## BLOCO 5 - Coleção `avaliacoes` (80 documentos)

> **Importante:** Esta inserção usa `db.colecao.findOne({nome: "..."})._id` para buscar os IDs reais de clientes e mecânicos em tempo real. Isso garante referências corretas entre as coleções.

```javascript
db.avaliacoes.insertMany([
  {
    cliente_id: db.clientes.findOne({nome: "Ana Paula Ferreira"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Honda", modelo: "Fit", ano: 2016, quilometragem: 88000, condicao_geral: "regular" },
    valor_proposto_cliente: 35000.00,
    valor_ofertado_loja: 28000.00,
    aprovada: true,
    data_avaliacao: new Date("2023-01-10"),
    observacoes: "Veículo com desgaste no banco do motorista e arranhões na lataria lateral"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Diego Albuquerque"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Chevrolet", modelo: "Cobalt", ano: 2018, quilometragem: 61000, condicao_geral: "bom" },
    valor_proposto_cliente: 52000.00,
    valor_ofertado_loja: 46000.00,
    aprovada: true,
    data_avaliacao: new Date("2023-02-14"),
    observacoes: "Veículo em bom estado, pequeno amassado no para-choque traseiro"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Felipe Monteiro"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Fox", ano: 2014, quilometragem: 102000, condicao_geral: "ruim" },
    valor_proposto_cliente: 22000.00,
    valor_ofertado_loja: 12000.00,
    aprovada: false,
    data_avaliacao: new Date("2023-03-05"),
    observacoes: "Motor com vazamento de óleo, lataria com múltiplos amassados, reparo inviável economicamente"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Henrique Barros"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Etios", ano: 2017, quilometragem: 74000, condicao_geral: "bom" },
    valor_proposto_cliente: 42000.00,
    valor_ofertado_loja: 37000.00,
    aprovada: true,
    data_avaliacao: new Date("2023-04-18"),
    observacoes: "Veículo bem conservado, pneus desgastados precisam de troca"
  },
  {
    cliente_id: db.clientes.findOne({nome: "João Pedro Melo"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    veiculo_descricao: { marca: "Fiat", modelo: "Uno", ano: 2015, quilometragem: 95000, condicao_geral: "regular" },
    valor_proposto_cliente: 18000.00,
    valor_ofertado_loja: 13000.00,
    aprovada: true,
    data_avaliacao: new Date("2023-05-22"),
    observacoes: "Suspensão dianteira com folga, lataria em estado aceitável"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Marcos Vinícius Prado"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    veiculo_descricao: { marca: "Renault", modelo: "Sandero", ano: 2019, quilometragem: 53000, condicao_geral: "bom" },
    valor_proposto_cliente: 48000.00,
    valor_ofertado_loja: 43000.00,
    aprovada: true,
    data_avaliacao: new Date("2023-06-10"),
    observacoes: "Veículo em ótimo estado, revisões em dia, apenas desgaste natural de uso"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Natália Souza"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Ford", modelo: "Ka", ano: 2020, quilometragem: 39000, condicao_geral: "bom" },
    valor_proposto_cliente: 55000.00,
    valor_ofertado_loja: 49000.00,
    aprovada: true,
    data_avaliacao: new Date("2023-07-03"),
    observacoes: "Veículo muito bem conservado, sem avarias, revisões feitas na concessionária"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Otávio Ramos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    veiculo_descricao: { marca: "Hyundai", modelo: "HB20", ano: 2016, quilometragem: 87000, condicao_geral: "regular" },
    valor_proposto_cliente: 31000.00,
    valor_ofertado_loja: 24000.00,
    aprovada: false,
    data_avaliacao: new Date("2023-08-15"),
    observacoes: "Caixa de câmbio com problema, custo de reparo supera margem de lucro viável"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Priscila Andrade"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Chevrolet", modelo: "Prisma", ano: 2018, quilometragem: 66000, condicao_geral: "bom" },
    valor_proposto_cliente: 47000.00,
    valor_ofertado_loja: 41000.00,
    aprovada: true,
    data_avaliacao: new Date("2023-09-20"),
    observacoes: "Sedan em bom estado, ar-condicionado precisando de recarga de gás"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Carla Nunes Rodrigues"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Nissan", modelo: "March", ano: 2017, quilometragem: 71000, condicao_geral: "regular" },
    valor_proposto_cliente: 29000.00,
    valor_ofertado_loja: 22000.00,
    aprovada: true,
    data_avaliacao: new Date("2023-10-08"),
    observacoes: "Pintura opaca necessitando polimento, mecânica em ordem"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Mateus Vieira Teixeira"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Etios", ano: 2019, quilometragem: 54936, condicao_geral: "ruim" },
    valor_proposto_cliente: 67400.00,
    valor_ofertado_loja: 60800.00,
    aprovada: false,
    data_avaliacao: new Date("2025-08-17"),
    observacoes: "Veículo bem conservado, apenas desgaste natural de uso"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Júlia Holanda Fernandes"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    veiculo_descricao: { marca: "Fiat", modelo: "Siena", ano: 2019, quilometragem: 120918, condicao_geral: "bom" },
    valor_proposto_cliente: 40500.00,
    valor_ofertado_loja: 35100.00,
    aprovada: true,
    data_avaliacao: new Date("2025-12-26"),
    observacoes: "Suspensão com folga dianteira, lataria aceitável"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Júlia Barbosa Lima"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Fiat", modelo: "Siena", ano: 2016, quilometragem: 55328, condicao_geral: "bom" },
    valor_proposto_cliente: 53700.00,
    valor_ofertado_loja: 42500.00,
    aprovada: false,
    data_avaliacao: new Date("2024-12-05"),
    observacoes: "Documentação em dia, revisões feitas na concessionária"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Manuela Ribeiro Barbosa"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Ford", modelo: "Fiesta", ano: 2019, quilometragem: 123296, condicao_geral: "regular" },
    valor_proposto_cliente: 42400.00,
    valor_ofertado_loja: 36600.00,
    aprovada: true,
    data_avaliacao: new Date("2025-11-06"),
    observacoes: "Documentação em dia, revisões feitas na concessionária"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Breno Cardoso Padilha"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    veiculo_descricao: { marca: "Renault", modelo: "Sandero", ano: 2012, quilometragem: 87059, condicao_geral: "regular" },
    valor_proposto_cliente: 47100.00,
    valor_ofertado_loja: 38600.00,
    aprovada: false,
    data_avaliacao: new Date("2024-03-07"),
    observacoes: "Pintura opaca necessitando polimento, mecânica ok"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Tomás Gomes Lima"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    veiculo_descricao: { marca: "Hyundai", modelo: "i30", ano: 2019, quilometragem: 104054, condicao_geral: "bom" },
    valor_proposto_cliente: 48100.00,
    valor_ofertado_loja: 41900.00,
    aprovada: true,
    data_avaliacao: new Date("2023-10-01"),
    observacoes: "Pneus desgastados precisam de troca, restante conservado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Lucas Sales Wanderley"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    veiculo_descricao: { marca: "Nissan", modelo: "March", ano: 2021, quilometragem: 104921, condicao_geral: "regular" },
    valor_proposto_cliente: 17100.00,
    valor_ofertado_loja: 14000.00,
    aprovada: true,
    data_avaliacao: new Date("2025-02-19"),
    observacoes: "Pequeno amassado no para-choque, mecânica em ordem"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Lara Santos Tavares"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Chevrolet", modelo: "Prisma", ano: 2019, quilometragem: 111611, condicao_geral: "bom" },
    valor_proposto_cliente: 65800.00,
    valor_ofertado_loja: 56300.00,
    aprovada: true,
    data_avaliacao: new Date("2024-02-24"),
    observacoes: "Pneus desgastados precisam de troca, restante conservado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Júlia Holanda Fernandes"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    veiculo_descricao: { marca: "Nissan", modelo: "March", ano: 2019, quilometragem: 55386, condicao_geral: "bom" },
    valor_proposto_cliente: 72300.00,
    valor_ofertado_loja: 66500.00,
    aprovada: true,
    data_avaliacao: new Date("2023-12-19"),
    observacoes: "Veículo bem conservado, apenas desgaste natural de uso"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Vanessa Lacerda Araújo"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Fiat", modelo: "Siena", ano: 2012, quilometragem: 114720, condicao_geral: "ruim" },
    valor_proposto_cliente: 56500.00,
    valor_ofertado_loja: 47500.00,
    aprovada: true,
    data_avaliacao: new Date("2025-05-20"),
    observacoes: "Documentação em dia, revisões feitas na concessionária"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Sofia Carvalho Cunha"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    veiculo_descricao: { marca: "Renault", modelo: "Sandero", ano: 2020, quilometragem: 129037, condicao_geral: "regular" },
    valor_proposto_cliente: 36200.00,
    valor_ofertado_loja: 33200.00,
    aprovada: true,
    data_avaliacao: new Date("2023-07-02"),
    observacoes: "Suspensão com folga dianteira, lataria aceitável"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Camila Vasconcelos Galvão"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Fiat", modelo: "Uno", ano: 2018, quilometragem: 104154, condicao_geral: "bom" },
    valor_proposto_cliente: 61000.00,
    valor_ofertado_loja: 55000.00,
    aprovada: true,
    data_avaliacao: new Date("2025-11-09"),
    observacoes: "Pintura opaca necessitando polimento, mecânica ok"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Talita Wanderley Magalhães"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    veiculo_descricao: { marca: "Ford", modelo: "Fiesta", ano: 2020, quilometragem: 76467, condicao_geral: "ruim" },
    valor_proposto_cliente: 44600.00,
    valor_ofertado_loja: 35300.00,
    aprovada: true,
    data_avaliacao: new Date("2024-08-11"),
    observacoes: "Caixa de câmbio com ruído, custo de reparo elevado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Davi Wanderley Barbosa"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    veiculo_descricao: { marca: "Honda", modelo: "Fit", ano: 2013, quilometragem: 110048, condicao_geral: "bom" },
    valor_proposto_cliente: 71900.00,
    valor_ofertado_loja: 63900.00,
    aprovada: true,
    data_avaliacao: new Date("2023-07-27"),
    observacoes: "Pneus desgastados precisam de troca, restante conservado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Júlio Dias Ramos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    veiculo_descricao: { marca: "Citroën", modelo: "C3", ano: 2014, quilometragem: 114205, condicao_geral: "bom" },
    valor_proposto_cliente: 32600.00,
    valor_ofertado_loja: 26900.00,
    aprovada: true,
    data_avaliacao: new Date("2024-11-25"),
    observacoes: "Veículo com desgaste no banco do motorista e arranhões na lataria"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Eduarda Lima Santos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    veiculo_descricao: { marca: "Chevrolet", modelo: "Cobalt", ano: 2014, quilometragem: 97840, condicao_geral: "bom" },
    valor_proposto_cliente: 21500.00,
    valor_ofertado_loja: 18700.00,
    aprovada: true,
    data_avaliacao: new Date("2023-07-07"),
    observacoes: "Motor com pequeno vazamento de óleo, reparo simples"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Talita Wanderley Magalhães"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    veiculo_descricao: { marca: "Nissan", modelo: "March", ano: 2016, quilometragem: 50803, condicao_geral: "ruim" },
    valor_proposto_cliente: 25400.00,
    valor_ofertado_loja: 22900.00,
    aprovada: true,
    data_avaliacao: new Date("2025-11-06"),
    observacoes: "Veículo com desgaste no banco do motorista e arranhões na lataria"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Emanuela Dias Moreira"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    veiculo_descricao: { marca: "Ford", modelo: "Fiesta", ano: 2013, quilometragem: 52475, condicao_geral: "regular" },
    valor_proposto_cliente: 56000.00,
    valor_ofertado_loja: 46100.00,
    aprovada: true,
    data_avaliacao: new Date("2023-08-03"),
    observacoes: "Motor com pequeno vazamento de óleo, reparo simples"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Carla Nunes Rodrigues"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Yaris", ano: 2013, quilometragem: 95353, condicao_geral: "bom" },
    valor_proposto_cliente: 29800.00,
    valor_ofertado_loja: 25400.00,
    aprovada: true,
    data_avaliacao: new Date("2024-02-08"),
    observacoes: "Pintura opaca necessitando polimento, mecânica ok"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Kléber Lobo Cunha"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Fox", ano: 2014, quilometragem: 90164, condicao_geral: "bom" },
    valor_proposto_cliente: 62900.00,
    valor_ofertado_loja: 56200.00,
    aprovada: false,
    data_avaliacao: new Date("2025-11-05"),
    observacoes: "Pequeno amassado no para-choque, mecânica em ordem"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Lourenço Mendes Cunha"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    veiculo_descricao: { marca: "Renault", modelo: "Logan", ano: 2015, quilometragem: 122323, condicao_geral: "bom" },
    valor_proposto_cliente: 51900.00,
    valor_ofertado_loja: 40500.00,
    aprovada: true,
    data_avaliacao: new Date("2024-10-22"),
    observacoes: "Ar-condicionado precisando de recarga de gás"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Beatriz Souza Martins"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    veiculo_descricao: { marca: "Ford", modelo: "Ka", ano: 2018, quilometragem: 86076, condicao_geral: "bom" },
    valor_proposto_cliente: 20700.00,
    valor_ofertado_loja: 18700.00,
    aprovada: false,
    data_avaliacao: new Date("2024-03-08"),
    observacoes: "Suspensão com folga dianteira, lataria aceitável"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Pedro Cardoso Cunha"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Fox", ano: 2016, quilometragem: 66928, condicao_geral: "regular" },
    valor_proposto_cliente: 31300.00,
    valor_ofertado_loja: 26800.00,
    aprovada: true,
    data_avaliacao: new Date("2025-09-07"),
    observacoes: "Pintura opaca necessitando polimento, mecânica ok"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Viviane Macedo Coutinho"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    veiculo_descricao: { marca: "Nissan", modelo: "March", ano: 2018, quilometragem: 54777, condicao_geral: "bom" },
    valor_proposto_cliente: 57300.00,
    valor_ofertado_loja: 45100.00,
    aprovada: true,
    data_avaliacao: new Date("2024-11-20"),
    observacoes: "Pequeno amassado no para-choque, mecânica em ordem"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Lara Ítalo Costa"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Renault", modelo: "Logan", ano: 2018, quilometragem: 114498, condicao_geral: "bom" },
    valor_proposto_cliente: 73200.00,
    valor_ofertado_loja: 67100.00,
    aprovada: true,
    data_avaliacao: new Date("2024-09-22"),
    observacoes: "Motor com pequeno vazamento de óleo, reparo simples"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Breno Magalhães Cardoso"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Citroën", modelo: "C3", ano: 2016, quilometragem: 68277, condicao_geral: "regular" },
    valor_proposto_cliente: 77600.00,
    valor_ofertado_loja: 71300.00,
    aprovada: false,
    data_avaliacao: new Date("2023-07-17"),
    observacoes: "Suspensão com folga dianteira, lataria aceitável"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Manuela Vieira Ribeiro"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    veiculo_descricao: { marca: "Renault", modelo: "Logan", ano: 2020, quilometragem: 120746, condicao_geral: "bom" },
    valor_proposto_cliente: 65300.00,
    valor_ofertado_loja: 54700.00,
    aprovada: true,
    data_avaliacao: new Date("2024-02-10"),
    observacoes: "Pequeno amassado no para-choque, mecânica em ordem"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Rodrigo Falcão Maciel"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    veiculo_descricao: { marca: "Renault", modelo: "Logan", ano: 2018, quilometragem: 116865, condicao_geral: "regular" },
    valor_proposto_cliente: 75400.00,
    valor_ofertado_loja: 61000.00,
    aprovada: true,
    data_avaliacao: new Date("2024-12-14"),
    observacoes: "Pneus desgastados precisam de troca, restante conservado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Larissa Maciel Gomes"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    veiculo_descricao: { marca: "Chevrolet", modelo: "Cobalt", ano: 2021, quilometragem: 47212, condicao_geral: "ruim" },
    valor_proposto_cliente: 31000.00,
    valor_ofertado_loja: 24600.00,
    aprovada: true,
    data_avaliacao: new Date("2025-12-22"),
    observacoes: "Motor com pequeno vazamento de óleo, reparo simples"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Davi Araújo Santos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Etios", ano: 2017, quilometragem: 108551, condicao_geral: "regular" },
    valor_proposto_cliente: 15800.00,
    valor_ofertado_loja: 13900.00,
    aprovada: true,
    data_avaliacao: new Date("2025-05-06"),
    observacoes: "Veículo bem conservado, apenas desgaste natural de uso"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Júlia Barbosa Lima"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Fiat", modelo: "Uno", ano: 2017, quilometragem: 96272, condicao_geral: "ruim" },
    valor_proposto_cliente: 64100.00,
    valor_ofertado_loja: 57000.00,
    aprovada: true,
    data_avaliacao: new Date("2025-02-09"),
    observacoes: "Caixa de câmbio com ruído, custo de reparo elevado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Viviane Tavares Nunes"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Fox", ano: 2014, quilometragem: 88193, condicao_geral: "bom" },
    valor_proposto_cliente: 47500.00,
    valor_ofertado_loja: 40100.00,
    aprovada: true,
    data_avaliacao: new Date("2024-02-19"),
    observacoes: "Pequeno amassado no para-choque, mecânica em ordem"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Diego Albuquerque"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Hyundai", modelo: "HB20", ano: 2012, quilometragem: 101835, condicao_geral: "ruim" },
    valor_proposto_cliente: 63500.00,
    valor_ofertado_loja: 54100.00,
    aprovada: false,
    data_avaliacao: new Date("2024-03-06"),
    observacoes: "Veículo com desgaste no banco do motorista e arranhões na lataria"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Eduardo Freitas Fernandes"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Hyundai", modelo: "i30", ano: 2017, quilometragem: 72540, condicao_geral: "bom" },
    valor_proposto_cliente: 67600.00,
    valor_ofertado_loja: 61400.00,
    aprovada: true,
    data_avaliacao: new Date("2025-06-09"),
    observacoes: "Pequeno amassado no para-choque, mecânica em ordem"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Otávio Ramos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Yaris", ano: 2015, quilometragem: 107603, condicao_geral: "regular" },
    valor_proposto_cliente: 39400.00,
    valor_ofertado_loja: 31400.00,
    aprovada: true,
    data_avaliacao: new Date("2024-02-15"),
    observacoes: "Suspensão com folga dianteira, lataria aceitável"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Kléber Lobo Cunha"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Nissan", modelo: "March", ano: 2016, quilometragem: 113899, condicao_geral: "ruim" },
    valor_proposto_cliente: 36400.00,
    valor_ofertado_loja: 28800.00,
    aprovada: true,
    data_avaliacao: new Date("2025-10-08"),
    observacoes: "Ar-condicionado precisando de recarga de gás"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Carolina Teixeira Barbosa"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Voyage", ano: 2015, quilometragem: 59735, condicao_geral: "regular" },
    valor_proposto_cliente: 53800.00,
    valor_ofertado_loja: 49300.00,
    aprovada: true,
    data_avaliacao: new Date("2024-01-08"),
    observacoes: "Documentação em dia, revisões feitas na concessionária"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Davi Lacerda Andrade"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Voyage", ano: 2018, quilometragem: 80306, condicao_geral: "regular" },
    valor_proposto_cliente: 56700.00,
    valor_ofertado_loja: 50900.00,
    aprovada: true,
    data_avaliacao: new Date("2023-09-08"),
    observacoes: "Pintura opaca necessitando polimento, mecânica ok"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Iara Rocha Macedo"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    veiculo_descricao: { marca: "Citroën", modelo: "C3", ano: 2012, quilometragem: 70339, condicao_geral: "regular" },
    valor_proposto_cliente: 78000.00,
    valor_ofertado_loja: 61500.00,
    aprovada: true,
    data_avaliacao: new Date("2024-12-12"),
    observacoes: "Ar-condicionado precisando de recarga de gás"
  },
  {
    cliente_id: db.clientes.findOne({nome: "César Costa Andrade"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Fox", ano: 2021, quilometragem: 114425, condicao_geral: "regular" },
    valor_proposto_cliente: 53100.00,
    valor_ofertado_loja: 42100.00,
    aprovada: false,
    data_avaliacao: new Date("2024-11-05"),
    observacoes: "Pneus desgastados precisam de troca, restante conservado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "César Costa Andrade"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    veiculo_descricao: { marca: "Nissan", modelo: "March", ano: 2017, quilometragem: 99343, condicao_geral: "ruim" },
    valor_proposto_cliente: 32100.00,
    valor_ofertado_loja: 28900.00,
    aprovada: true,
    data_avaliacao: new Date("2023-02-07"),
    observacoes: "Motor com pequeno vazamento de óleo, reparo simples"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Ivan Ramos Bezerra"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Yaris", ano: 2018, quilometragem: 55825, condicao_geral: "regular" },
    valor_proposto_cliente: 22100.00,
    valor_ofertado_loja: 17700.00,
    aprovada: false,
    data_avaliacao: new Date("2024-04-15"),
    observacoes: "Suspensão com folga dianteira, lataria aceitável"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Marina Ribeiro Ramos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    veiculo_descricao: { marca: "Peugeot", modelo: "207", ano: 2012, quilometragem: 68183, condicao_geral: "ruim" },
    valor_proposto_cliente: 32400.00,
    valor_ofertado_loja: 29100.00,
    aprovada: false,
    data_avaliacao: new Date("2023-02-23"),
    observacoes: "Pneus desgastados precisam de troca, restante conservado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Juliana Cunha Lacerda"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Voyage", ano: 2012, quilometragem: 93004, condicao_geral: "bom" },
    valor_proposto_cliente: 41000.00,
    valor_ofertado_loja: 34900.00,
    aprovada: true,
    data_avaliacao: new Date("2025-12-18"),
    observacoes: "Pneus desgastados precisam de troca, restante conservado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Beatriz Souza Martins"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Etios", ano: 2012, quilometragem: 69135, condicao_geral: "bom" },
    valor_proposto_cliente: 45300.00,
    valor_ofertado_loja: 36000.00,
    aprovada: true,
    data_avaliacao: new Date("2023-07-12"),
    observacoes: "Pequeno amassado no para-choque, mecânica em ordem"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Felipe Monteiro"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Yaris", ano: 2015, quilometragem: 124670, condicao_geral: "bom" },
    valor_proposto_cliente: 53400.00,
    valor_ofertado_loja: 43600.00,
    aprovada: true,
    data_avaliacao: new Date("2023-02-28"),
    observacoes: "Veículo bem conservado, apenas desgaste natural de uso"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Sofia Carvalho Cunha"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Etios", ano: 2018, quilometragem: 105028, condicao_geral: "regular" },
    valor_proposto_cliente: 17800.00,
    valor_ofertado_loja: 16200.00,
    aprovada: false,
    data_avaliacao: new Date("2024-11-14"),
    observacoes: "Motor com pequeno vazamento de óleo, reparo simples"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Manuela Cardoso Gomes"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Voyage", ano: 2012, quilometragem: 120492, condicao_geral: "regular" },
    valor_proposto_cliente: 29100.00,
    valor_ofertado_loja: 26400.00,
    aprovada: true,
    data_avaliacao: new Date("2025-04-21"),
    observacoes: "Suspensão com folga dianteira, lataria aceitável"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Igor Ribeiro Brandão"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    veiculo_descricao: { marca: "Citroën", modelo: "C3", ano: 2018, quilometragem: 57987, condicao_geral: "bom" },
    valor_proposto_cliente: 42000.00,
    valor_ofertado_loja: 38000.00,
    aprovada: true,
    data_avaliacao: new Date("2023-11-26"),
    observacoes: "Documentação em dia, revisões feitas na concessionária"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Eduarda Lima Santos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    veiculo_descricao: { marca: "Hyundai", modelo: "HB20", ano: 2017, quilometragem: 102873, condicao_geral: "regular" },
    valor_proposto_cliente: 56300.00,
    valor_ofertado_loja: 51700.00,
    aprovada: true,
    data_avaliacao: new Date("2024-06-19"),
    observacoes: "Documentação em dia, revisões feitas na concessionária"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Adriano Martins Lacerda"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Fiat", modelo: "Palio", ano: 2016, quilometragem: 47679, condicao_geral: "bom" },
    valor_proposto_cliente: 40500.00,
    valor_ofertado_loja: 33100.00,
    aprovada: false,
    data_avaliacao: new Date("2025-06-25"),
    observacoes: "Caixa de câmbio com ruído, custo de reparo elevado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Viviane Macedo Coutinho"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    veiculo_descricao: { marca: "Hyundai", modelo: "HB20", ano: 2020, quilometragem: 47328, condicao_geral: "bom" },
    valor_proposto_cliente: 78800.00,
    valor_ofertado_loja: 63200.00,
    aprovada: true,
    data_avaliacao: new Date("2025-07-12"),
    observacoes: "Motor com pequeno vazamento de óleo, reparo simples"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Enzo Nunes Costa"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    veiculo_descricao: { marca: "Renault", modelo: "Sandero", ano: 2012, quilometragem: 86095, condicao_geral: "regular" },
    valor_proposto_cliente: 30500.00,
    valor_ofertado_loja: 26300.00,
    aprovada: true,
    data_avaliacao: new Date("2025-03-19"),
    observacoes: "Pneus desgastados precisam de troca, restante conservado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Talita Wanderley Magalhães"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Citroën", modelo: "C3", ano: 2015, quilometragem: 118861, condicao_geral: "bom" },
    valor_proposto_cliente: 50500.00,
    valor_ofertado_loja: 41600.00,
    aprovada: true,
    data_avaliacao: new Date("2023-09-16"),
    observacoes: "Veículo com desgaste no banco do motorista e arranhões na lataria"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Geovana Cardoso Carvalho"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Fiat", modelo: "Palio", ano: 2017, quilometragem: 47806, condicao_geral: "regular" },
    valor_proposto_cliente: 75200.00,
    valor_ofertado_loja: 65100.00,
    aprovada: true,
    data_avaliacao: new Date("2023-10-23"),
    observacoes: "Motor com pequeno vazamento de óleo, reparo simples"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Joana Maciel Nunes"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Etios", ano: 2018, quilometragem: 116810, condicao_geral: "regular" },
    valor_proposto_cliente: 70500.00,
    valor_ofertado_loja: 60200.00,
    aprovada: true,
    data_avaliacao: new Date("2024-05-11"),
    observacoes: "Motor com pequeno vazamento de óleo, reparo simples"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Caio Andrade Barbosa"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    veiculo_descricao: { marca: "Renault", modelo: "Sandero", ano: 2014, quilometragem: 113659, condicao_geral: "regular" },
    valor_proposto_cliente: 63000.00,
    valor_ofertado_loja: 57500.00,
    aprovada: true,
    data_avaliacao: new Date("2024-04-22"),
    observacoes: "Caixa de câmbio com ruído, custo de reparo elevado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Bruno Siqueira Lobo"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Renault", modelo: "Sandero", ano: 2012, quilometragem: 115082, condicao_geral: "bom" },
    valor_proposto_cliente: 39800.00,
    valor_ofertado_loja: 32800.00,
    aprovada: true,
    data_avaliacao: new Date("2025-01-06"),
    observacoes: "Caixa de câmbio com ruído, custo de reparo elevado"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Téo Albuquerque Nunes"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    veiculo_descricao: { marca: "Fiat", modelo: "Palio", ano: 2019, quilometragem: 58434, condicao_geral: "ruim" },
    valor_proposto_cliente: 75400.00,
    valor_ofertado_loja: 67300.00,
    aprovada: true,
    data_avaliacao: new Date("2025-02-08"),
    observacoes: "Veículo bem conservado, apenas desgaste natural de uso"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Davi Lacerda Andrade"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    veiculo_descricao: { marca: "Fiat", modelo: "Palio", ano: 2012, quilometragem: 74761, condicao_geral: "bom" },
    valor_proposto_cliente: 26000.00,
    valor_ofertado_loja: 22600.00,
    aprovada: true,
    data_avaliacao: new Date("2023-12-03"),
    observacoes: "Veículo bem conservado, apenas desgaste natural de uso"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Elaine Moreira Falcão"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    veiculo_descricao: { marca: "Chevrolet", modelo: "Prisma", ano: 2018, quilometragem: 61802, condicao_geral: "bom" },
    valor_proposto_cliente: 66600.00,
    valor_ofertado_loja: 53000.00,
    aprovada: false,
    data_avaliacao: new Date("2024-07-12"),
    observacoes: "Documentação em dia, revisões feitas na concessionária"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Sabrina Brandão Justino"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Ford", modelo: "Fiesta", ano: 2014, quilometragem: 99151, condicao_geral: "regular" },
    valor_proposto_cliente: 21600.00,
    valor_ofertado_loja: 19400.00,
    aprovada: true,
    data_avaliacao: new Date("2023-05-01"),
    observacoes: "Veículo bem conservado, apenas desgaste natural de uso"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Caio Gomes Dias"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Chevrolet", modelo: "Prisma", ano: 2013, quilometragem: 111702, condicao_geral: "regular" },
    valor_proposto_cliente: 77400.00,
    valor_ofertado_loja: 61500.00,
    aprovada: true,
    data_avaliacao: new Date("2024-10-20"),
    observacoes: "Ar-condicionado precisando de recarga de gás"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Olívia Ribeiro Souza"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    veiculo_descricao: { marca: "Honda", modelo: "Fit", ano: 2012, quilometragem: 53272, condicao_geral: "ruim" },
    valor_proposto_cliente: 43300.00,
    valor_ofertado_loja: 39500.00,
    aprovada: false,
    data_avaliacao: new Date("2023-04-14"),
    observacoes: "Documentação em dia, revisões feitas na concessionária"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Joana Fernandes Brandão"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Hyundai", modelo: "i30", ano: 2018, quilometragem: 114943, condicao_geral: "regular" },
    valor_proposto_cliente: 32400.00,
    valor_ofertado_loja: 28300.00,
    aprovada: true,
    data_avaliacao: new Date("2024-03-02"),
    observacoes: "Veículo bem conservado, apenas desgaste natural de uso"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Isadora Vieira Lima"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    veiculo_descricao: { marca: "Honda", modelo: "Fit", ano: 2013, quilometragem: 43373, condicao_geral: "bom" },
    valor_proposto_cliente: 43000.00,
    valor_ofertado_loja: 34100.00,
    aprovada: true,
    data_avaliacao: new Date("2023-11-10"),
    observacoes: "Pequeno amassado no para-choque, mecânica em ordem"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Adriano Araújo Santos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    veiculo_descricao: { marca: "Citroën", modelo: "C3", ano: 2016, quilometragem: 51945, condicao_geral: "regular" },
    valor_proposto_cliente: 70300.00,
    valor_ofertado_loja: 56000.00,
    aprovada: true,
    data_avaliacao: new Date("2024-03-12"),
    observacoes: "Pintura opaca necessitando polimento, mecânica ok"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Ivan Ramos Bezerra"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Voyage", ano: 2015, quilometragem: 75200, condicao_geral: "regular" },
    valor_proposto_cliente: 27200.00,
    valor_ofertado_loja: 22900.00,
    aprovada: true,
    data_avaliacao: new Date("2023-03-25"),
    observacoes: "Pequeno amassado no para-choque, mecânica em ordem"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Marina Costa Pinto"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    veiculo_descricao: { marca: "Volkswagen", modelo: "Fox", ano: 2012, quilometragem: 90738, condicao_geral: "regular" },
    valor_proposto_cliente: 58800.00,
    valor_ofertado_loja: 48700.00,
    aprovada: true,
    data_avaliacao: new Date("2024-09-22"),
    observacoes: "Ar-condicionado precisando de recarga de gás"
  },
  {
    cliente_id: db.clientes.findOne({nome: "Amanda Magalhães Fernandes"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    veiculo_descricao: { marca: "Toyota", modelo: "Yaris", ano: 2020, quilometragem: 114870, condicao_geral: "regular" },
    valor_proposto_cliente: 72800.00,
    valor_ofertado_loja: 59200.00,
    aprovada: true,
    data_avaliacao: new Date("2025-11-20"),
    observacoes: "Motor com pequeno vazamento de óleo, reparo simples"
  }
])
```

---

## BLOCO 6 - Coleção `servicos` (120 documentos)

> **Importante:** Esta inserção usa `db.colecao.findOne(...)` para buscar os IDs reais de veículos e mecânicos em tempo real.

```javascript
db.servicos.insertMany([
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Gol"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão completa de 50 mil km, troca de óleo, filtros e correia dentada",
    pecas_utilizadas: ["filtro de óleo", "filtro de ar", "correia dentada", "velas de ignição"],
    custo: 850.00,
    data_inicio: new Date("2023-01-05"),
    data_conclusao: new Date("2023-01-06"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Onix"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "elétrica",
    descricao: "Substituição do sistema de som e instalação de central multimídia",
    pecas_utilizadas: ["central multimídia", "chicote elétrico", "alto-falantes"],
    custo: 1200.00,
    data_inicio: new Date("2023-01-10"),
    data_conclusao: new Date("2023-01-11"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Corolla"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento técnico, cristalização da pintura e higienização completa do interior",
    pecas_utilizadas: ["cera de polimento", "cristalizador", "produto de higienização"],
    custo: 650.00,
    data_inicio: new Date("2023-02-03"),
    data_conclusao: new Date("2023-02-03"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Ranger"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de amortecedores dianteiros e traseiros e alinhamento e balanceamento",
    pecas_utilizadas: ["amortecedor dianteiro esquerdo", "amortecedor dianteiro direito", "amortecedor traseiro esquerdo", "amortecedor traseiro direito"],
    custo: 1800.00,
    data_inicio: new Date("2023-02-15"),
    data_conclusao: new Date("2023-02-17"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Jeep", modelo: "Compass"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de amassado no para-lama dianteiro direito e repintura parcial",
    pecas_utilizadas: ["massa plástica", "tinta automotiva", "verniz"],
    custo: 2200.00,
    data_inicio: new Date("2023-03-01"),
    data_conclusao: new Date("2023-03-04"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Duster"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral, troca de óleo e filtros, verificação de freios e suspensão",
    pecas_utilizadas: ["óleo do motor", "filtro de óleo", "filtro de ar", "filtro de combustível"],
    custo: 720.00,
    data_inicio: new Date("2023-03-20"),
    data_conclusao: new Date("2023-03-21"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "S10"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "motor",
    descricao: "Limpeza de bicos injetores, substituição de velas e bobinas de ignição",
    pecas_utilizadas: ["velas de ignição", "bobinas de ignição", "produto de limpeza de injetores"],
    custo: 1450.00,
    data_inicio: new Date("2023-04-10"),
    data_conclusao: new Date("2023-04-12"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "Creta"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás do ar-condicionado, limpeza do evaporador e troca do filtro de cabine",
    pecas_utilizadas: ["gás R134a", "filtro de cabine", "produto de limpeza de evaporador"],
    custo: 480.00,
    data_inicio: new Date("2023-05-08"),
    data_conclusao: new Date("2023-05-08"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Mustang"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio dianteiros e traseiros",
    pecas_utilizadas: ["pastilha dianteira", "pastilha traseira", "disco dianteiro esquerdo", "disco dianteiro direito"],
    custo: 1100.00,
    data_inicio: new Date("2023-06-14"),
    data_conclusao: new Date("2023-06-15"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Camaro"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "estetica",
    descricao: "Higienização completa, impermeabilização de bancos e polimento de faróis",
    pecas_utilizadas: ["produto de higienização", "impermeabilizante", "produto de polimento de faróis"],
    custo: 550.00,
    data_inicio: new Date("2023-07-02"),
    data_conclusao: new Date("2023-07-02"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Tracker"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de buchas de bandeja e barra estabilizadora dianteira",
    pecas_utilizadas: ["bucha de bandeja dianteira", "bucha de barra estabilizadora"],
    custo: 920.00,
    data_inicio: new Date("2023-07-18"),
    data_conclusao: new Date("2023-07-19"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "Civic Si"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "motor",
    descricao: "Substituição da correia dentada, tensor e bomba d'água preventiva",
    pecas_utilizadas: ["correia dentada", "tensor de correia", "bomba d'água"],
    custo: 1650.00,
    data_inicio: new Date("2023-08-05"),
    data_conclusao: new Date("2023-08-07"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "Kicks"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de riscos profundos na porta traseira esquerda e polimento geral",
    pecas_utilizadas: ["massa plástica", "lixa", "tinta automotiva", "verniz"],
    custo: 1350.00,
    data_inicio: new Date("2023-09-11"),
    data_conclusao: new Date("2023-09-13"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Supra"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão de 10 mil km, troca de óleo sintético e verificação geral",
    pecas_utilizadas: ["óleo sintético 5W30", "filtro de óleo"],
    custo: 420.00,
    data_inicio: new Date("2023-10-03"),
    data_conclusao: new Date("2023-10-03"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Jeep", modelo: "Renegade"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "elétrica",
    descricao: "Diagnóstico e reparo de falha no módulo de injeção eletrônica",
    pecas_utilizadas: ["módulo de injeção eletrônica"],
    custo: 2800.00,
    data_inicio: new Date("2023-10-20"),
    data_conclusao: new Date("2023-10-24"),
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "Kicks"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["pastilha traseira", "pastilha dianteira"],
    custo: 700.00,
    data_inicio: new Date("2023-01-14"),
    data_conclusao: new Date("2023-01-14"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Mustang"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["produto de higienização", "cristalizador", "cera de polimento", "impermeabilizante"],
    custo: 550.00,
    data_inicio: new Date("2025-07-18"),
    data_conclusao: new Date("2025-07-20"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Camry"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral com troca de óleo e filtros",
    pecas_utilizadas: ["velas de ignição", "filtro de combustível", "óleo do motor", "filtro de óleo"],
    custo: 530.00,
    data_inicio: new Date("2023-10-19"),
    data_conclusao: new Date("2023-10-23"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Pulse"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "elétrica",
    descricao: "Reparo elétrico e instalação de componentes",
    pecas_utilizadas: ["módulo", "alto-falantes", "central multimídia"],
    custo: 1530.00,
    data_inicio: new Date("2024-11-16"),
    data_conclusao: new Date("2024-11-20"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Kwid"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["tinta automotiva", "verniz", "lixa"],
    custo: 980.00,
    data_inicio: new Date("2024-06-23"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Chevette"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["bomba d'água", "bobinas de ignição"],
    custo: 1120.00,
    data_inicio: new Date("2024-08-23"),
    data_conclusao: new Date("2024-08-23"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "Creta"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["lixa", "tinta automotiva", "verniz", "massa plástica"],
    custo: 2140.00,
    data_inicio: new Date("2025-02-07"),
    data_conclusao: new Date("2025-02-10"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Citroën", modelo: "C4 Cactus"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["disco dianteiro", "pastilha dianteira", "disco traseiro", "pastilha traseira"],
    custo: 820.00,
    data_inicio: new Date("2025-09-13"),
    data_conclusao: new Date("2025-09-14"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "X-Trail"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral com troca de óleo e filtros",
    pecas_utilizadas: ["filtro de óleo", "velas de ignição"],
    custo: 440.00,
    data_inicio: new Date("2023-01-15"),
    data_conclusao: new Date("2023-01-15"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Nivus"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["bobinas de ignição", "velas de ignição", "bomba d'água"],
    custo: 1740.00,
    data_inicio: new Date("2023-11-01"),
    data_conclusao: new Date("2023-11-02"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Etios"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["produto de higienização", "cristalizador", "cera de polimento"],
    custo: 480.00,
    data_inicio: new Date("2025-12-03"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Mitsubishi", modelo: "L200 Triton"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["amortecedor traseiro", "bucha de bandeja"],
    custo: 1120.00,
    data_inicio: new Date("2024-11-14"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "Accord"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["cristalizador", "produto de higienização", "cera de polimento", "impermeabilizante"],
    custo: 480.00,
    data_inicio: new Date("2025-05-23"),
    data_conclusao: new Date("2025-05-25"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "CrossFox"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["pastilha traseira", "disco traseiro", "disco dianteiro"],
    custo: 1190.00,
    data_inicio: new Date("2025-10-13"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Captur"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["bobinas de ignição", "bomba d'água", "tensor de correia", "correia dentada"],
    custo: 1290.00,
    data_inicio: new Date("2023-06-09"),
    data_conclusao: new Date("2023-06-11"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Fastback"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["tinta automotiva", "verniz"],
    custo: 1390.00,
    data_inicio: new Date("2023-10-13"),
    data_conclusao: new Date("2023-10-15"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Fastback"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["disco dianteiro", "pastilha traseira", "disco traseiro"],
    custo: 900.00,
    data_inicio: new Date("2025-01-19"),
    data_conclusao: new Date("2025-01-23"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Peugeot", modelo: "208"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["mola", "bucha de bandeja", "amortecedor traseiro", "amortecedor dianteiro"],
    custo: 1050.00,
    data_inicio: new Date("2025-09-06"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Citroën", modelo: "C4 Cactus"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["tinta automotiva", "verniz", "lixa", "massa plástica"],
    custo: 1360.00,
    data_inicio: new Date("2024-04-24"),
    data_conclusao: new Date("2024-04-26"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Prisma"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["verniz", "tinta automotiva", "massa plástica", "lixa"],
    custo: 1010.00,
    data_inicio: new Date("2025-10-19"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "Tucson"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "elétrica",
    descricao: "Reparo elétrico e instalação de componentes",
    pecas_utilizadas: ["bateria", "alto-falantes", "central multimídia", "chicote elétrico"],
    custo: 1070.00,
    data_inicio: new Date("2023-04-11"),
    data_conclusao: new Date("2023-04-14"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Tracker"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["tensor de correia", "correia dentada", "bobinas de ignição", "bomba d'água"],
    custo: 1450.00,
    data_inicio: new Date("2023-06-21"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Camaro"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["cristalizador", "impermeabilizante", "cera de polimento", "produto de higienização"],
    custo: 660.00,
    data_inicio: new Date("2024-11-14"),
    data_conclusao: new Date("2024-11-17"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Equinox"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral com troca de óleo e filtros",
    pecas_utilizadas: ["velas de ignição", "filtro de óleo"],
    custo: 760.00,
    data_inicio: new Date("2023-06-25"),
    data_conclusao: new Date("2023-06-28"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Cronos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["bucha de bandeja", "amortecedor traseiro"],
    custo: 960.00,
    data_inicio: new Date("2023-07-17"),
    data_conclusao: new Date("2023-07-21"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "HB20"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["lixa", "verniz", "tinta automotiva"],
    custo: 1790.00,
    data_inicio: new Date("2025-03-11"),
    data_conclusao: new Date("2025-03-14"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Virtus"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["gás R134a", "compressor"],
    custo: 1040.00,
    data_inicio: new Date("2023-04-24"),
    data_conclusao: new Date("2023-04-24"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "Kicks"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["correia dentada", "velas de ignição", "bomba d'água", "tensor de correia"],
    custo: 1590.00,
    data_inicio: new Date("2025-10-02"),
    data_conclusao: new Date("2025-10-06"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Fastback"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral com troca de óleo e filtros",
    pecas_utilizadas: ["óleo do motor", "filtro de combustível"],
    custo: 830.00,
    data_inicio: new Date("2024-02-18"),
    data_conclusao: new Date("2024-02-20"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Camaro"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral com troca de óleo e filtros",
    pecas_utilizadas: ["filtro de combustível", "óleo do motor", "filtro de ar"],
    custo: 660.00,
    data_inicio: new Date("2025-10-23"),
    data_conclusao: new Date("2025-10-24"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "ix35"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "elétrica",
    descricao: "Reparo elétrico e instalação de componentes",
    pecas_utilizadas: ["chicote elétrico", "módulo", "central multimídia"],
    custo: 1260.00,
    data_inicio: new Date("2025-04-25"),
    data_conclusao: new Date("2025-04-27"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Cruze"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["gás R134a", "compressor", "filtro de cabine"],
    custo: 510.00,
    data_inicio: new Date("2025-08-11"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Polo"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["pastilha dianteira", "disco dianteiro"],
    custo: 580.00,
    data_inicio: new Date("2025-12-04"),
    data_conclusao: new Date("2025-12-06"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Tiguan"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["massa plástica", "lixa", "verniz"],
    custo: 980.00,
    data_inicio: new Date("2024-06-26"),
    data_conclusao: new Date("2024-06-28"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "Civic"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral com troca de óleo e filtros",
    pecas_utilizadas: ["filtro de óleo", "velas de ignição"],
    custo: 720.00,
    data_inicio: new Date("2024-08-20"),
    data_conclusao: new Date("2024-08-22"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Prisma"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["correia dentada", "velas de ignição"],
    custo: 1210.00,
    data_inicio: new Date("2024-05-13"),
    data_conclusao: new Date("2024-05-16"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Polo"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["cera de polimento", "impermeabilizante", "produto de higienização", "cristalizador"],
    custo: 650.00,
    data_inicio: new Date("2024-10-22"),
    data_conclusao: new Date("2024-10-25"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Kia", modelo: "Cerato"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["correia dentada", "tensor de correia", "velas de ignição", "bomba d'água"],
    custo: 920.00,
    data_inicio: new Date("2024-08-02"),
    data_conclusao: new Date("2024-08-02"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Onix"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["bucha de bandeja", "mola", "amortecedor dianteiro", "amortecedor traseiro"],
    custo: 1210.00,
    data_inicio: new Date("2024-06-22"),
    data_conclusao: new Date("2024-06-25"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Fusion"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral com troca de óleo e filtros",
    pecas_utilizadas: ["filtro de óleo", "filtro de combustível"],
    custo: 890.00,
    data_inicio: new Date("2023-02-25"),
    data_conclusao: new Date("2023-02-28"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Nivus"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral com troca de óleo e filtros",
    pecas_utilizadas: ["filtro de óleo", "filtro de combustível", "velas de ignição", "óleo do motor"],
    custo: 460.00,
    data_inicio: new Date("2024-08-26"),
    data_conclusao: new Date("2024-08-28"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Etios"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["velas de ignição", "correia dentada"],
    custo: 900.00,
    data_inicio: new Date("2024-07-02"),
    data_conclusao: new Date("2024-07-06"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Fiesta"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["tinta automotiva", "verniz", "lixa", "massa plástica"],
    custo: 1640.00,
    data_inicio: new Date("2023-04-15"),
    data_conclusao: new Date("2023-04-17"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Ka"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["disco dianteiro", "disco traseiro", "pastilha traseira", "pastilha dianteira"],
    custo: 600.00,
    data_inicio: new Date("2025-04-01"),
    data_conclusao: new Date("2025-04-03"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "Versa"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["correia dentada", "bobinas de ignição", "velas de ignição", "tensor de correia"],
    custo: 940.00,
    data_inicio: new Date("2025-12-24"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Mustang"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["mola", "amortecedor dianteiro"],
    custo: 1640.00,
    data_inicio: new Date("2023-12-11"),
    data_conclusao: new Date("2023-12-11"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Mobi"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    tipo_servico: "elétrica",
    descricao: "Reparo elétrico e instalação de componentes",
    pecas_utilizadas: ["bateria", "central multimídia", "módulo"],
    custo: 470.00,
    data_inicio: new Date("2025-12-02"),
    data_conclusao: new Date("2025-12-06"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "CR-V"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["cristalizador", "produto de higienização", "cera de polimento", "impermeabilizante"],
    custo: 550.00,
    data_inicio: new Date("2025-10-20"),
    data_conclusao: new Date("2025-10-22"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Joy"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["mola", "amortecedor traseiro", "bucha de bandeja"],
    custo: 1630.00,
    data_inicio: new Date("2023-03-14"),
    data_conclusao: new Date("2023-03-18"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Jetta"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["bobinas de ignição", "tensor de correia", "correia dentada", "bomba d'água"],
    custo: 1440.00,
    data_inicio: new Date("2025-05-22"),
    data_conclusao: new Date("2025-05-24"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Jeep", modelo: "Wrangler"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["produto de higienização", "impermeabilizante", "cera de polimento", "cristalizador"],
    custo: 640.00,
    data_inicio: new Date("2024-10-19"),
    data_conclusao: new Date("2024-10-22"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Taos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["compressor", "gás R134a"],
    custo: 320.00,
    data_inicio: new Date("2024-03-02"),
    data_conclusao: new Date("2024-03-02"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Taos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["massa plástica", "verniz"],
    custo: 1500.00,
    data_inicio: new Date("2023-09-02"),
    data_conclusao: new Date("2023-09-04"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Fusion"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["mola", "amortecedor dianteiro", "amortecedor traseiro", "bucha de bandeja"],
    custo: 1480.00,
    data_inicio: new Date("2024-07-26"),
    data_conclusao: new Date("2024-07-28"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Onix"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["lixa", "massa plástica"],
    custo: 2200.00,
    data_inicio: new Date("2025-12-21"),
    data_conclusao: new Date("2025-12-23"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Citroën", modelo: "C4 Cactus"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["amortecedor traseiro", "mola", "bucha de bandeja", "amortecedor dianteiro"],
    custo: 850.00,
    data_inicio: new Date("2023-03-24"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Corolla Cross"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["verniz", "massa plástica", "lixa", "tinta automotiva"],
    custo: 910.00,
    data_inicio: new Date("2024-08-23"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Ka"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral com troca de óleo e filtros",
    pecas_utilizadas: ["velas de ignição", "filtro de ar", "filtro de óleo", "filtro de combustível"],
    custo: 450.00,
    data_inicio: new Date("2025-06-17"),
    data_conclusao: new Date("2025-06-18"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Duster"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["impermeabilizante", "cera de polimento", "cristalizador"],
    custo: 460.00,
    data_inicio: new Date("2023-11-11"),
    data_conclusao: new Date("2023-11-13"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Caoa Chery", modelo: "Tiggo 7"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["pastilha dianteira", "disco traseiro", "pastilha traseira", "disco dianteiro"],
    custo: 750.00,
    data_inicio: new Date("2025-10-20"),
    data_conclusao: new Date("2025-10-21"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Spin"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "elétrica",
    descricao: "Reparo elétrico e instalação de componentes",
    pecas_utilizadas: ["alto-falantes", "módulo", "chicote elétrico"],
    custo: 2570.00,
    data_inicio: new Date("2024-09-26"),
    data_conclusao: new Date("2024-09-28"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Tiguan"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["amortecedor dianteiro", "mola", "bucha de bandeja"],
    custo: 1800.00,
    data_inicio: new Date("2025-01-21"),
    data_conclusao: new Date("2025-01-21"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Logan"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["gás R134a", "filtro de cabine"],
    custo: 960.00,
    data_inicio: new Date("2023-12-22"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Ranger"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "elétrica",
    descricao: "Reparo elétrico e instalação de componentes",
    pecas_utilizadas: ["chicote elétrico", "central multimídia"],
    custo: 1480.00,
    data_inicio: new Date("2025-02-19"),
    data_conclusao: new Date("2025-02-20"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Equinox"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["disco traseiro", "pastilha traseira", "disco dianteiro", "pastilha dianteira"],
    custo: 900.00,
    data_inicio: new Date("2025-02-18"),
    data_conclusao: new Date("2025-02-18"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Duster"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "revisao",
    descricao: "Revisão geral com troca de óleo e filtros",
    pecas_utilizadas: ["óleo do motor", "filtro de ar", "filtro de combustível", "velas de ignição"],
    custo: 680.00,
    data_inicio: new Date("2025-05-20"),
    data_conclusao: new Date("2025-05-20"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Spin"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["filtro de cabine", "gás R134a"],
    custo: 850.00,
    data_inicio: new Date("2023-03-24"),
    data_conclusao: new Date("2023-03-27"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Tiguan"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["produto de higienização", "cera de polimento", "impermeabilizante"],
    custo: 410.00,
    data_inicio: new Date("2023-01-19"),
    data_conclusao: new Date("2023-01-23"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "S10"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["verniz", "massa plástica"],
    custo: 1740.00,
    data_inicio: new Date("2025-09-05"),
    data_conclusao: new Date("2025-09-06"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Corcel II"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["amortecedor traseiro", "bucha de bandeja"],
    custo: 1860.00,
    data_inicio: new Date("2023-09-15"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Corcel II"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    tipo_servico: "elétrica",
    descricao: "Reparo elétrico e instalação de componentes",
    pecas_utilizadas: ["módulo", "bateria"],
    custo: 1800.00,
    data_inicio: new Date("2024-03-22"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Duster"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["mola", "amortecedor traseiro", "bucha de bandeja"],
    custo: 1330.00,
    data_inicio: new Date("2025-10-05"),
    data_conclusao: new Date("2025-10-09"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Corolla Cross"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["produto de higienização", "cera de polimento"],
    custo: 460.00,
    data_inicio: new Date("2025-12-21"),
    data_conclusao: new Date("2025-12-24"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "Creta"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["velas de ignição", "bobinas de ignição", "tensor de correia"],
    custo: 1590.00,
    data_inicio: new Date("2024-08-18"),
    data_conclusao: new Date("2024-08-18"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "S10"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["tinta automotiva", "lixa"],
    custo: 2180.00,
    data_inicio: new Date("2023-12-03"),
    data_conclusao: new Date("2023-12-03"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "EcoSport"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["gás R134a", "filtro de cabine"],
    custo: 860.00,
    data_inicio: new Date("2025-08-21"),
    data_conclusao: new Date("2025-08-22"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Mitsubishi", modelo: "ASX"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["lixa", "verniz"],
    custo: 1940.00,
    data_inicio: new Date("2023-07-12"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Fusion"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["cristalizador", "impermeabilizante", "cera de polimento", "produto de higienização"],
    custo: 640.00,
    data_inicio: new Date("2025-11-05"),
    data_conclusao: new Date("2025-11-08"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Supra"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["pastilha dianteira", "pastilha traseira"],
    custo: 880.00,
    data_inicio: new Date("2023-01-22"),
    data_conclusao: new Date("2023-01-23"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Equinox"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["pastilha dianteira", "disco traseiro", "pastilha traseira"],
    custo: 600.00,
    data_inicio: new Date("2025-09-21"),
    data_conclusao: new Date("2025-09-23"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "EcoSport"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Fábio Cavalcante"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["impermeabilizante", "cristalizador", "cera de polimento"],
    custo: 610.00,
    data_inicio: new Date("2024-07-08"),
    data_conclusao: new Date("2024-07-12"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "ZR-V"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["pastilha dianteira", "disco dianteiro", "disco traseiro", "pastilha traseira"],
    custo: 670.00,
    data_inicio: new Date("2023-02-17"),
    data_conclusao: new Date("2023-02-19"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Mitsubishi", modelo: "L200 Triton"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Paulo Henrique Dias"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["correia dentada", "tensor de correia", "velas de ignição", "bomba d'água"],
    custo: 1540.00,
    data_inicio: new Date("2023-08-22"),
    data_conclusao: new Date("2023-08-25"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Mitsubishi", modelo: "L200 Triton"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["gás R134a", "compressor"],
    custo: 430.00,
    data_inicio: new Date("2025-10-06"),
    data_conclusao: new Date("2025-10-07"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "March"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Wellington Gomes"})._id,
    tipo_servico: "estetica",
    descricao: "Polimento, cristalização e higienização completa",
    pecas_utilizadas: ["cristalizador", "impermeabilizante"],
    custo: 440.00,
    data_inicio: new Date("2025-07-20"),
    data_conclusao: new Date("2025-07-24"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "S10"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["mola", "amortecedor traseiro", "amortecedor dianteiro"],
    custo: 1150.00,
    data_inicio: new Date("2024-10-05"),
    data_conclusao: new Date("2024-10-09"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Toro"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["verniz", "tinta automotiva"],
    custo: 2120.00,
    data_inicio: new Date("2025-02-08"),
    data_conclusao: new Date("2025-02-11"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Corolla"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["mola", "amortecedor dianteiro", "bucha de bandeja", "amortecedor traseiro"],
    custo: 1670.00,
    data_inicio: new Date("2025-10-02"),
    data_conclusao: new Date("2025-10-06"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Hilux"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["pastilha traseira", "disco dianteiro", "pastilha dianteira", "disco traseiro"],
    custo: 1030.00,
    data_inicio: new Date("2024-06-02"),
    data_conclusao: new Date("2024-06-06"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Mitsubishi", modelo: "ASX"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["compressor", "gás R134a", "filtro de cabine"],
    custo: 440.00,
    data_inicio: new Date("2024-08-25"),
    data_conclusao: new Date("2024-08-26"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Taos"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["gás R134a", "compressor", "filtro de cabine"],
    custo: 890.00,
    data_inicio: new Date("2025-02-17"),
    data_conclusao: new Date("2025-02-17"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Oroch"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["bomba d'água", "correia dentada", "velas de ignição"],
    custo: 1240.00,
    data_inicio: new Date("2025-10-09"),
    data_conclusao: new Date("2025-10-11"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "X-Trail"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["bomba d'água", "velas de ignição", "correia dentada", "tensor de correia"],
    custo: 1360.00,
    data_inicio: new Date("2025-08-06"),
    data_conclusao: new Date("2025-08-08"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Corcel II"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["verniz", "lixa", "tinta automotiva", "massa plástica"],
    custo: 2250.00,
    data_inicio: new Date("2023-12-08"),
    data_conclusao: new Date("2023-12-11"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "Civic"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["mola", "amortecedor traseiro", "amortecedor dianteiro", "bucha de bandeja"],
    custo: 1500.00,
    data_inicio: new Date("2025-01-26"),
    data_conclusao: new Date("2025-01-26"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Ka"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["gás R134a", "filtro de cabine"],
    custo: 530.00,
    data_inicio: new Date("2024-02-20"),
    data_conclusao: new Date("2024-02-20"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Fusion"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Sérgio Batista"})._id,
    tipo_servico: "funilaria",
    descricao: "Reparo de lataria e repintura parcial",
    pecas_utilizadas: ["massa plástica", "lixa", "tinta automotiva", "verniz"],
    custo: 920.00,
    data_inicio: new Date("2023-11-26"),
    data_conclusao: new Date("2023-11-28"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Ka"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Alexandre Pereira"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["amortecedor traseiro", "bucha de bandeja", "amortecedor dianteiro", "mola"],
    custo: 1190.00,
    data_inicio: new Date("2025-01-06"),
    data_conclusao: new Date("2025-01-06"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Cruze"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Edmilson Santos"})._id,
    tipo_servico: "ar-condicionado",
    descricao: "Recarga de gás e manutenção do ar-condicionado",
    pecas_utilizadas: ["compressor", "gás R134a", "filtro de cabine"],
    custo: 1050.00,
    data_inicio: new Date("2025-02-03"),
    data_conclusao: new Date("2025-02-07"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "EcoSport"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Luciano Ferraz"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["bomba d'água", "tensor de correia", "bobinas de ignição"],
    custo: 1790.00,
    data_inicio: new Date("2023-08-13"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Celta"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Bruno Cardoso"})._id,
    tipo_servico: "elétrica",
    descricao: "Reparo elétrico e instalação de componentes",
    pecas_utilizadas: ["chicote elétrico", "alto-falantes", "central multimídia", "módulo"],
    custo: 2550.00,
    data_inicio: new Date("2024-09-26"),
    data_conclusao: new Date("2024-09-28"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Spin"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "freios",
    descricao: "Substituição de pastilhas e discos de freio",
    pecas_utilizadas: ["disco dianteiro", "pastilha traseira"],
    custo: 1200.00,
    data_inicio: new Date("2024-10-01"),
    data_conclusao: null,
    status: "em andamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Spin"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["amortecedor traseiro", "mola", "bucha de bandeja", "amortecedor dianteiro"],
    custo: 1760.00,
    data_inicio: new Date("2025-01-23"),
    data_conclusao: new Date("2025-01-25"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Montana"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Tiago Moreira"})._id,
    tipo_servico: "motor",
    descricao: "Serviço de motor com substituição de peças",
    pecas_utilizadas: ["bobinas de ignição", "tensor de correia"],
    custo: 1290.00,
    data_inicio: new Date("2024-06-07"),
    data_conclusao: new Date("2024-06-11"),
    status: "concluido"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "Fit"})._id,
    mecanico_id: db.mecanicos.findOne({nome: "Rogério Nascimento"})._id,
    tipo_servico: "suspensao",
    descricao: "Troca de componentes de suspensão e alinhamento",
    pecas_utilizadas: ["amortecedor traseiro", "mola"],
    custo: 1120.00,
    data_inicio: new Date("2023-04-08"),
    data_conclusao: new Date("2023-04-12"),
    status: "concluido"
  }
])
```

---

## BLOCO 7 - Coleção `vendas` (70 documentos)

> **Importante:** Esta inserção usa `db.colecao.findOne(...)` para buscar os IDs reais de veículos, clientes e vendedores em tempo real.

```javascript
db.vendas.insertMany([
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Gol"})._id,
    cliente_id: db.clientes.findOne({nome: "Bruno Cavalcanti"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Carlos Mendonça"})._id,
    preco_final: 36500.00,
    forma_pagamento: "financiamento",
    parcelas: 48,
    data_venda: new Date("2023-02-10"),
    observacoes: "Cliente financiou pelo banco do bradesco com entrada de 8 mil reais"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Corolla"})._id,
    cliente_id: db.clientes.findOne({nome: "Felipe Monteiro"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 93000.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2023-03-15"),
    observacoes: "Cliente pagou à vista com desconto de 2 mil reais negociado"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "HB20"})._id,
    cliente_id: db.clientes.findOne({nome: "João Pedro Melo"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Tatiane Oliveira"})._id,
    preco_final: 61000.00,
    forma_pagamento: "financiamento",
    parcelas: 36,
    data_venda: new Date("2023-04-20"),
    observacoes: "Financiamento pela Caixa Econômica, entrada de 10 mil reais"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "S10"})._id,
    cliente_id: db.clientes.findOne({nome: "Diego Albuquerque"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 145000.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-05-08"),
    observacoes: "Cliente deu Cobalt 2018 avaliado em 46 mil como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Hilux"})._id,
    cliente_id: db.clientes.findOne({nome: "Henrique Barros"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Carlos Mendonça"})._id,
    preco_final: 208000.00,
    forma_pagamento: "financiamento",
    parcelas: 60,
    data_venda: new Date("2023-05-25"),
    observacoes: "Financiamento pelo Itaú com entrada de 50 mil reais"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Polo"})._id,
    cliente_id: db.clientes.findOne({nome: "Marcos Vinícius Prado"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Juliana Bezerra"})._id,
    preco_final: 70500.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2023-06-12"),
    observacoes: "Pagamento à vista via transferência bancária, sem desconto adicional"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Argo"})._id,
    cliente_id: db.clientes.findOne({nome: "Eduarda Lima Santos"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 43500.00,
    forma_pagamento: "financiamento",
    parcelas: 24,
    data_venda: new Date("2023-07-03"),
    observacoes: "Primeira compra do cliente, financiamento aprovado pelo Santander"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Yaris"})._id,
    cliente_id: db.clientes.findOne({nome: "Gabriela Vasconcelos"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Patrícia Wanderley"})._id,
    preco_final: 74000.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2023-07-19"),
    observacoes: "Cliente negociou desconto de 1 mil reais, pagamento via PIX"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Camaro"})._id,
    cliente_id: db.clientes.findOne({nome: "Natália Souza"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Juliana Bezerra"})._id,
    preco_final: 318000.00,
    forma_pagamento: "financiamento",
    parcelas: 60,
    data_venda: new Date("2023-08-14"),
    observacoes: "Financiamento pelo Bradesco com entrada de 80 mil reais, cliente fidelizado"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Jeep", modelo: "Renegade"})._id,
    cliente_id: db.clientes.findOne({nome: "Priscila Andrade"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 110000.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-09-05"),
    observacoes: "Cliente deu Renegade 2020 como parte do pagamento avaliado em 112 mil"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Golf GTI"})._id,
    cliente_id: db.clientes.findOne({nome: "Isabela Correia"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 207000.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2023-09-22"),
    observacoes: "Cliente pagou à vista com desconto de 3 mil reais, transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Tracker"})._id,
    cliente_id: db.clientes.findOne({nome: "Larissa Freitas"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Juliana Bezerra"})._id,
    preco_final: 120500.00,
    forma_pagamento: "financiamento",
    parcelas: 48,
    data_venda: new Date("2023-10-10"),
    observacoes: "Financiamento pelo Itaú aprovado, entrada de 25 mil reais"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Toro"})._id,
    cliente_id: db.clientes.findOne({nome: "Manuela Ribeiro Barbosa"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Tatiane Oliveira"})._id,
    preco_final: 160700.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2024-12-25"),
    observacoes: "Pagamento à vista com desconto negociado, via PIX"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "City"})._id,
    cliente_id: db.clientes.findOne({nome: "Iara Rocha Macedo"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Patrícia Wanderley"})._id,
    preco_final: 135000.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2023-10-05"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Corolla Cross"})._id,
    cliente_id: db.clientes.findOne({nome: "Marina Costa Pinto"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 209800.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2025-05-26"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Joy"})._id,
    cliente_id: db.clientes.findOne({nome: "Heitor Bezerra Tavares"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Rafael Souza"})._id,
    preco_final: 81400.00,
    forma_pagamento: "financiamento",
    parcelas: 60,
    data_venda: new Date("2024-01-06"),
    observacoes: "Financiamento pelo Caixa Econômica com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Jeep", modelo: "Commander"})._id,
    cliente_id: db.clientes.findOne({nome: "Júlio Gomes Lima"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Juliana Bezerra"})._id,
    preco_final: 65200.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2024-05-09"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Peugeot", modelo: "208"})._id,
    cliente_id: db.clientes.findOne({nome: "Natália Souza"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Anderson Lima"})._id,
    preco_final: 178900.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-12-06"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Captur"})._id,
    cliente_id: db.clientes.findOne({nome: "Joana Fernandes Brandão"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Patrícia Wanderley"})._id,
    preco_final: 154900.00,
    forma_pagamento: "financiamento",
    parcelas: 36,
    data_venda: new Date("2025-06-09"),
    observacoes: "Financiamento pelo Santander com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Sandero"})._id,
    cliente_id: db.clientes.findOne({nome: "Nicole Galvão Macedo"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 176900.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2024-01-14"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Voyage"})._id,
    cliente_id: db.clientes.findOne({nome: "Sabrina Brandão Justino"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Rafael Souza"})._id,
    preco_final: 82200.00,
    forma_pagamento: "financiamento",
    parcelas: 48,
    data_venda: new Date("2024-06-11"),
    observacoes: "Financiamento pelo Banco do Brasil com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Spin"})._id,
    cliente_id: db.clientes.findOne({nome: "Caio Andrade Barbosa"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Patrícia Wanderley"})._id,
    preco_final: 163800.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-07-20"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "CR-V"})._id,
    cliente_id: db.clientes.findOne({nome: "Heitor Bezerra Tavares"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Rafael Souza"})._id,
    preco_final: 195600.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2025-06-14"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Mobi"})._id,
    cliente_id: db.clientes.findOne({nome: "Sofia Carvalho Cunha"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Anderson Lima"})._id,
    preco_final: 190500.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-02-06"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "Fit"})._id,
    cliente_id: db.clientes.findOne({nome: "Lara Ítalo Costa"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 112200.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2025-05-20"),
    observacoes: "Pagamento à vista com desconto negociado, via PIX"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "CrossFox"})._id,
    cliente_id: db.clientes.findOne({nome: "Manuela Ribeiro Dias"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Patrícia Wanderley"})._id,
    preco_final: 133700.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2024-12-19"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Trailblazer"})._id,
    cliente_id: db.clientes.findOne({nome: "Bruna Araújo Bezerra"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Rafael Souza"})._id,
    preco_final: 148000.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-01-05"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Amarok"})._id,
    cliente_id: db.clientes.findOne({nome: "Tatiane Gomes Dias"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 91500.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-03-13"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "Tucson"})._id,
    cliente_id: db.clientes.findOne({nome: "Júlio Dias Ramos"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Carlos Mendonça"})._id,
    preco_final: 154000.00,
    forma_pagamento: "financiamento",
    parcelas: 24,
    data_venda: new Date("2023-07-17"),
    observacoes: "Financiamento pelo Bradesco com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Stepway"})._id,
    cliente_id: db.clientes.findOne({nome: "Vinícius Andrade Nascimento"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 192000.00,
    forma_pagamento: "financiamento",
    parcelas: 24,
    data_venda: new Date("2025-07-10"),
    observacoes: "Financiamento pelo Santander com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Cruze"})._id,
    cliente_id: db.clientes.findOne({nome: "Bruno Siqueira Lobo"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Rafael Souza"})._id,
    preco_final: 146200.00,
    forma_pagamento: "financiamento",
    parcelas: 36,
    data_venda: new Date("2025-03-01"),
    observacoes: "Financiamento pelo Santander com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Etios"})._id,
    cliente_id: db.clientes.findOne({nome: "Ivan Ramos Bezerra"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 154800.00,
    forma_pagamento: "financiamento",
    parcelas: 48,
    data_venda: new Date("2025-08-05"),
    observacoes: "Financiamento pelo Santander com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "March"})._id,
    cliente_id: db.clientes.findOne({nome: "Norberto Teixeira Nascimento"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Patrícia Wanderley"})._id,
    preco_final: 171400.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2025-12-21"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "i30"})._id,
    cliente_id: db.clientes.findOne({nome: "Fábio Lima Fernandes"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 144000.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2024-08-18"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "Versa"})._id,
    cliente_id: db.clientes.findOne({nome: "Murilo Gomes Wanderley"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Anderson Lima"})._id,
    preco_final: 110700.00,
    forma_pagamento: "financiamento",
    parcelas: 24,
    data_venda: new Date("2024-03-10"),
    observacoes: "Financiamento pelo Caixa Econômica com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Peugeot", modelo: "2008"})._id,
    cliente_id: db.clientes.findOne({nome: "Carolina Moreira Barbosa"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Juliana Bezerra"})._id,
    preco_final: 228800.00,
    forma_pagamento: "financiamento",
    parcelas: 24,
    data_venda: new Date("2024-08-18"),
    observacoes: "Financiamento pelo Banco do Brasil com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "RAV4"})._id,
    cliente_id: db.clientes.findOne({nome: "Carla Nunes Rodrigues"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Anderson Lima"})._id,
    preco_final: 108500.00,
    forma_pagamento: "financiamento",
    parcelas: 60,
    data_venda: new Date("2024-10-08"),
    observacoes: "Financiamento pelo Caixa Econômica com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Prisma"})._id,
    cliente_id: db.clientes.findOne({nome: "Aline Almeida Nunes"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Anderson Lima"})._id,
    preco_final: 137900.00,
    forma_pagamento: "financiamento",
    parcelas: 48,
    data_venda: new Date("2024-04-06"),
    observacoes: "Financiamento pelo Itaú com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Cronos"})._id,
    cliente_id: db.clientes.findOne({nome: "Emanuela Albuquerque Albuquerque"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Anderson Lima"})._id,
    preco_final: 223200.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-05-03"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Montana"})._id,
    cliente_id: db.clientes.findOne({nome: "Manuela Ribeiro Dias"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 165400.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2025-12-18"),
    observacoes: "Pagamento à vista com desconto negociado, via PIX"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Taos"})._id,
    cliente_id: db.clientes.findOne({nome: "Breno Magalhães Cardoso"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Rafael Souza"})._id,
    preco_final: 79300.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2023-05-04"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "X-Trail"})._id,
    cliente_id: db.clientes.findOne({nome: "Breno Cardoso Padilha"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 149400.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2025-10-16"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Territory"})._id,
    cliente_id: db.clientes.findOne({nome: "Natália Souza"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Carlos Mendonça"})._id,
    preco_final: 69900.00,
    forma_pagamento: "financiamento",
    parcelas: 48,
    data_venda: new Date("2023-02-10"),
    observacoes: "Financiamento pelo Bradesco com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Uno"})._id,
    cliente_id: db.clientes.findOne({nome: "Lourenço Mendes Cunha"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Carlos Mendonça"})._id,
    preco_final: 217500.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2023-02-05"),
    observacoes: "Pagamento à vista com desconto negociado, via PIX"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "ZR-V"})._id,
    cliente_id: db.clientes.findOne({nome: "Eduardo Freitas Fernandes"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 119600.00,
    forma_pagamento: "financiamento",
    parcelas: 60,
    data_venda: new Date("2024-06-15"),
    observacoes: "Financiamento pelo Itaú com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Jetta"})._id,
    cliente_id: db.clientes.findOne({nome: "Letícia Costa Barbosa"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 38300.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-01-09"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Fox"})._id,
    cliente_id: db.clientes.findOne({nome: "Adriano Araújo Santos"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Rafael Souza"})._id,
    preco_final: 172400.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2023-05-27"),
    observacoes: "Pagamento à vista com desconto negociado, via PIX"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Equinox"})._id,
    cliente_id: db.clientes.findOne({nome: "Viviane Rocha Almeida"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Anderson Lima"})._id,
    preco_final: 62000.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2024-04-24"),
    observacoes: "Pagamento à vista com desconto negociado, via PIX"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Honda", modelo: "Accord"})._id,
    cliente_id: db.clientes.findOne({nome: "Joana Fernandes Brandão"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Tatiane Oliveira"})._id,
    preco_final: 222800.00,
    forma_pagamento: "financiamento",
    parcelas: 36,
    data_venda: new Date("2024-07-22"),
    observacoes: "Financiamento pelo Caixa Econômica com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Ka"})._id,
    cliente_id: db.clientes.findOne({nome: "Larissa Freitas"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 71600.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2024-08-21"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "Elantra"})._id,
    cliente_id: db.clientes.findOne({nome: "Otávio Ramos"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Tatiane Oliveira"})._id,
    preco_final: 124500.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2023-04-21"),
    observacoes: "Pagamento à vista com desconto negociado, via PIX"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Cobalt"})._id,
    cliente_id: db.clientes.findOne({nome: "Débora Cavalcante Oliveira"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 33900.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2025-02-13"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Jeep", modelo: "Wrangler"})._id,
    cliente_id: db.clientes.findOne({nome: "Eduardo Santos Cavalcante"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Rafael Souza"})._id,
    preco_final: 182300.00,
    forma_pagamento: "financiamento",
    parcelas: 24,
    data_venda: new Date("2024-02-08"),
    observacoes: "Financiamento pelo Bradesco com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Chevrolet", modelo: "Celta"})._id,
    cliente_id: db.clientes.findOne({nome: "Kléber Pereira Teixeira"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Carlos Mendonça"})._id,
    preco_final: 209800.00,
    forma_pagamento: "financiamento",
    parcelas: 60,
    data_venda: new Date("2023-06-21"),
    observacoes: "Financiamento pelo Bradesco com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "Frontier"})._id,
    cliente_id: db.clientes.findOne({nome: "Emanuela Dias Moreira"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Juliana Bezerra"})._id,
    preco_final: 157900.00,
    forma_pagamento: "financiamento",
    parcelas: 24,
    data_venda: new Date("2025-11-25"),
    observacoes: "Financiamento pelo Itaú com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Oroch"})._id,
    cliente_id: db.clientes.findOne({nome: "Olívia Pinto Albuquerque"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Carlos Mendonça"})._id,
    preco_final: 222200.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2025-07-12"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "SW4"})._id,
    cliente_id: db.clientes.findOne({nome: "Tatiane Gomes Dias"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Carlos Mendonça"})._id,
    preco_final: 65300.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2024-12-15"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Renault", modelo: "Logan"})._id,
    cliente_id: db.clientes.findOne({nome: "Lara Santos Tavares"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Patrícia Wanderley"})._id,
    preco_final: 107300.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-10-06"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Toyota", modelo: "Camry"})._id,
    cliente_id: db.clientes.findOne({nome: "Camila Vasconcelos Galvão"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Patrícia Wanderley"})._id,
    preco_final: 121100.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2024-10-28"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "ix35"})._id,
    cliente_id: db.clientes.findOne({nome: "Breno Magalhães Cardoso"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Rafael Souza"})._id,
    preco_final: 72000.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2024-05-27"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Tiguan"})._id,
    cliente_id: db.clientes.findOne({nome: "Ana Paula Ferreira"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Anderson Lima"})._id,
    preco_final: 149000.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2025-03-01"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Nissan", modelo: "Sentra"})._id,
    cliente_id: db.clientes.findOne({nome: "Viviane Macedo Coutinho"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Juliana Bezerra"})._id,
    preco_final: 125400.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2025-02-22"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Fiat", modelo: "Fastback"})._id,
    cliente_id: db.clientes.findOne({nome: "Amanda Sales Vieira"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Patrícia Wanderley"})._id,
    preco_final: 131600.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2025-03-20"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Nivus"})._id,
    cliente_id: db.clientes.findOne({nome: "Camila Vasconcelos Galvão"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 137400.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2023-09-22"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "EcoSport"})._id,
    cliente_id: db.clientes.findOne({nome: "Isabela Correia"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Tatiane Oliveira"})._id,
    preco_final: 76800.00,
    forma_pagamento: "financiamento",
    parcelas: 24,
    data_venda: new Date("2023-08-07"),
    observacoes: "Financiamento pelo Itaú com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Hyundai", modelo: "Santa Fe"})._id,
    cliente_id: db.clientes.findOne({nome: "Emanuela Albuquerque Albuquerque"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Patrícia Wanderley"})._id,
    preco_final: 198200.00,
    forma_pagamento: "financiamento",
    parcelas: 24,
    data_venda: new Date("2025-10-23"),
    observacoes: "Financiamento pelo Banco do Brasil com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Fiesta"})._id,
    cliente_id: db.clientes.findOne({nome: "Natália Souza"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Juliana Bezerra"})._id,
    preco_final: 97100.00,
    forma_pagamento: "troca",
    parcelas: 1,
    data_venda: new Date("2023-10-23"),
    observacoes: "Cliente entregou veículo usado como parte do pagamento"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Ford", modelo: "Fusion"})._id,
    cliente_id: db.clientes.findOne({nome: "Tomás Gomes Lima"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 201900.00,
    forma_pagamento: "financiamento",
    parcelas: 24,
    data_venda: new Date("2024-11-02"),
    observacoes: "Financiamento pelo Itaú com entrada negociada"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Saveiro"})._id,
    cliente_id: db.clientes.findOne({nome: "Priscila Andrade"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Marcelo Figueiredo"})._id,
    preco_final: 126700.00,
    forma_pagamento: "à vista",
    parcelas: 1,
    data_venda: new Date("2025-01-24"),
    observacoes: "Pagamento à vista com desconto negociado, via transferência bancária"
  },
  {
    veiculo_id: db.veiculos.findOne({marca: "Volkswagen", modelo: "Up"})._id,
    cliente_id: db.clientes.findOne({nome: "Júlio Gomes Lima"})._id,
    vendedor_id: db.vendedores.findOne({nome: "Fernanda Lira"})._id,
    preco_final: 86600.00,
    forma_pagamento: "financiamento",
    parcelas: 48,
    data_venda: new Date("2023-12-08"),
    observacoes: "Financiamento pelo Bradesco com entrada negociada"
  }
])
```

---

## Resumo do povoamento

| Coleção | Quantidade de documentos |
|---|---|
| `clientes` | 150 |
| `vendedores` | 8 |
| `mecanicos` | 10 |
| `veiculos` | 100 |
| `avaliacoes` | 80 |
| `servicos` | 120 |
| `vendas` | 70 |
| **Total** | **538 documentos** |

## Ordem obrigatória de execução

1. `clientes` — independente
2. `vendedores` — independente
3. `mecanicos` — independente
4. `veiculos` — independente
5. `avaliacoes` — depende de `clientes` e `mecanicos`
6. `servicos` — depende de `veiculos` e `mecanicos`
7. `vendas` — depende de `veiculos`, `clientes` e `vendedores`