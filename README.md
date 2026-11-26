# PRATO — Painel de Rentabilidade e Análise Técnica Operacional

Sistema web de **ficha técnica e margem de lucro** para restaurantes, construído
em torno do CMV (Custo de Mercadoria Vendida).

🔗 **Sistema no ar:** https://prato-restaurante.setaisst.workers.dev

---

## O problema

Restaurante pequeno define o preço do prato no olho: olha o que o concorrente
cobra, arredonda e pronto. O resultado é que o dono não sabe quanto cada prato
deixa de lucro — e muitas vezes o prato mais vendido da casa é justamente o que
menos dá retorno.

O indicador que o setor usa para medir isso é o **CMV**: quanto do preço de venda
vai embora só em ingrediente. A referência de mercado é de 30% a 35%. Acima disso,
o prato come a margem; muito abaixo, normalmente o preço está acima do que o
cliente aceita pagar.

O PRATO calcula o CMV de cada prato a partir da ficha técnica — a lista de
insumos com a quantidade exata usada — e mostra quais pratos sustentam a casa e
quais estão furando a margem.

## Funcionalidades

- **Painel de rentabilidade** — CMV da casa, pratos fora da faixa, margem de
  contribuição do mês e o cruzamento entre volume de vendas e CMV
- **Cardápio** — os pratos ordenados por CMV, não por preço
- **Ficha técnica** — uma página por prato, com a lista de insumos, o custo de
  cada um e a barra de composição do custo
- **Precificação** — o preço que cada prato teria que ter para fechar no CMV alvo
- **Insumos** — tabela de compras com preço, unidade e fornecedor
- **Cadastro de prato e de insumo** — com validação nativa de formulário
- **Telas de confirmação** — retorno após cada cadastro
- **Layout responsivo** — menu lateral no desktop, barra no topo no celular

## Tecnologias

Desenvolvido exclusivamente com **HTML5 e CSS3**, sem JavaScript, frameworks ou
bibliotecas externas — restrição definida pelo enunciado do trabalho.

| Recurso | Onde foi aplicado |
|---|---|
| HTML semântico | `aside`, `header`, `nav`, `main`, `footer` |
| Validação nativa | `required`, `min`, `max`, `step`, `maxlength` |
| Flexbox | Layout de duas colunas, cards, barra de composição e formulários |
| Barra de composição | Flex com largura percentual por insumo |
| Media queries | Pontos de quebra em 900px e 540px |
| Pseudo-elemento `::before` | Faixa colorida na lateral dos cards |
| Google Fonts | Tipografia Inter, com Arial como alternativa |

Hospedagem em **Cloudflare Workers**, servindo os estáticos de `public/`.

## Estrutura

```
prato-restaurante/
├── public/
│   ├── index.html             # painel de rentabilidade
│   ├── cardapio.html          # pratos ordenados por CMV
│   ├── ficha-p01.html         # ficha técnica — Carne de Sol com Macaxeira
│   ├── ficha-p02.html         # ficha técnica — Escondidinho de Carne de Sol
│   ├── ficha-p03.html         # ficha técnica — Peixada Paraibana
│   ├── ficha-p04.html         # ficha técnica — Baião de Dois
│   ├── ficha-p05.html         # ficha técnica — Galinha de Capoeira
│   ├── ficha-p06.html         # ficha técnica — Feijoada da Casa
│   ├── precificacao.html      # preço sugerido por CMV alvo
│   ├── insumos.html           # tabela de compras
│   ├── cadastrar-prato.html   # cadastro de prato com ficha técnica
│   ├── cadastrar-insumo.html  # cadastro de insumo
│   ├── sucesso-prato.html     # confirmação
│   ├── sucesso-insumo.html    # confirmação
│   └── estilo.css             # folha de estilo compartilhada
├── DEPLOY.md
├── package.json
└── wrangler.toml
```

## Como executar

Sem instalar nada, basta abrir `public/index.html` no navegador — o sistema não
depende de servidor.

Para rodar com o ambiente de publicação:

```bash
npm install
npm run dev      # http://localhost:8787
npm run deploy   # publica no Cloudflare Workers
```

Os passos completos de publicação estão em [DEPLOY.md](DEPLOY.md).

## Limitações da versão atual

- Os dados são fixos no HTML, para demonstrar o funcionamento das telas
- Os cálculos de CMV e margem foram feitos fora do sistema e escritos nas páginas;
  sem JavaScript não há como recalcular na tela
- Os formulários validam e confirmam o envio, mas não gravam o registro
- A persistência e o recálculo automático poderiam ser implementados em uma
  próxima etapa com PHP e MySQL, aproveitando a mesma interface

## Equipe

| Integrante | Responsabilidade |
|---|---|
| Carlos Daniel | Painel de rentabilidade, precificação e folha de estilo |
| Henrique Dantas | Cardápio e fichas técnicas |
| Gustavo Nascimento | Cadastro de pratos, insumos e tabela de compras |

---

Trabalho de Desenvolvimento Web — Ciência da Computação — 2026
