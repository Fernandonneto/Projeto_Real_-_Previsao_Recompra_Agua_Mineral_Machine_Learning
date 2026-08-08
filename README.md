# 🧠 Previsão de Recompra de Água Mineral com Machine Learning

Projeto de Ciência de Dados desenvolvido a partir de um **problema real de negócio**, com o objetivo de compreender e posteriormente prever o comportamento de recompra de clientes de água mineral.

A proposta é utilizar dados históricos de pedidos para identificar padrões de consumo e estimar a probabilidade de um cliente realizar uma nova compra em até **15 dias**.

A solução poderá apoiar decisões como:

- identificação de clientes com maior probabilidade de recompra;
- criação de ações de reativação e relacionamento;
- antecipação de demanda;
- planejamento operacional e logístico;
- melhor direcionamento das entregas.

> 🚧 **Status:** projeto em desenvolvimento.  
> A etapa de tratamento, engenharia de atributos e Análise Exploratória de Dados (EDA) já foi realizada. A próxima etapa será a construção e avaliação do modelo de Machine Learning.

---

## 🎯 Objetivo do Projeto

Responder à seguinte questão de negócio:

> **"É possível utilizar o histórico de compras para antecipar quais clientes possuem maior probabilidade de realizar uma nova compra de água mineral nos próximos 15 dias?"**

Para isso, o projeto busca compreender:

- como os clientes realizam suas compras;
- quais são seus padrões de recorrência;
- como o volume adquirido se relaciona com a recompra;
- como o intervalo entre pedidos influencia o comportamento futuro;
- se existem padrões sazonais;
- quais variáveis apresentam maior potencial preditivo.

---

# 🗂️ Etapas do Projeto

## 1. Estruturação e digitalização dos dados

Os dados utilizados no projeto foram originalmente registrados manualmente em agendas físicas utilizadas na operação diária.

Como primeira etapa, essas informações foram digitalizadas e estruturadas em planilhas eletrônicas, possibilitando a criação de uma base adequada para análise e posteriormente para modelagem preditiva.

---

## 2. Anonimização e adequação à LGPD

Antes da utilização dos dados para análise, foi realizada a anonimização das informações dos clientes.

Foram adotadas as seguintes medidas:

- substituição dos nomes dos clientes por identificadores (`id_cliente`);
- remoção de informações pessoais desnecessárias para a análise;
- utilização exclusivamente de dados anonimizados na base analítica.

Dessa forma, o projeto preserva a identidade dos clientes e reduz a exposição de informações pessoais.

---

## 3. Tratamento e preparação dos dados

A base passou por etapas de preparação para garantir maior consistência e qualidade dos dados.

Foram realizadas:

- importação e estruturação da base;
- adequação dos tipos de dados;
- padronização das datas;
- criação de variáveis temporais;
- tratamento de valores ausentes;
- verificação de inconsistências;
- análise de possíveis valores extremos;
- validação da consistência das variáveis.

---

# ⚙️ 4. Engenharia de Atributos

Foram criadas variáveis derivadas com o objetivo de representar melhor o comportamento histórico dos clientes.

### Variáveis temporais

- `dt_semana` — dia da semana do pedido;
- `dt_estacao` — estação do ano;
- `dt_ano` — ano do pedido;
- `dt_mes` — mês do pedido.

### Variáveis comportamentais

- `cli_dias_desde_ultimo_pedido` — dias desde a última compra;
- `cli_intervalo_medio` — intervalo médio entre compras;
- `cli_frequencia_pedidos` — frequência histórica de pedidos;
- `cli_media_aguas_por_pedido` — média de águas adquiridas por pedido;
- `cli_total_pedidos` — quantidade total de pedidos realizados.

### Variáveis relacionadas à recompra

- `target_dt_proxima_compra` — data estimada/observada da próxima compra;
- `target_dias_ate_recompra` — quantidade de dias até a próxima compra;
- `target_vai_comprar_15d` — variável alvo que indica se o cliente realizou uma nova compra dentro de 15 dias.

A criação dessas variáveis permite transformar o histórico bruto de pedidos em informações capazes de representar o comportamento de compra dos clientes.

---

# 📊 5. Análise Exploratória de Dados (EDA)

Após o tratamento e a engenharia de atributos, foi realizada uma Análise Exploratória de Dados com foco no comportamento de consumo e na recompra.

A EDA foi estruturada em quatro etapas principais:

### 5.1 Perfil geral dos pedidos

Foram analisados:

- distribuição da quantidade de águas entregues;
- evolução dos pedidos ao longo do tempo;
- distribuição dos pedidos por dia da semana.

**Objetivo:** compreender o comportamento geral da operação e identificar padrões temporais e de volume.

### 5.2 Perfil dos clientes

Foram analisados:

- total de pedidos por cliente;
- intervalo médio entre compras;
- média de águas por pedido.

**Objetivo:** identificar diferentes padrões de consumo e recorrência entre os clientes.

### 5.3 Relação entre variáveis e recompra

Foram realizados cruzamentos entre variáveis comportamentais e a variável relacionada à próxima compra.

Entre as principais análises:

- quantidade de águas × dias até recompra;
- intervalo médio × dias até recompra;
- frequência de pedidos × dias até recompra;
- total de pedidos × dias até recompra;
- estação do ano × dias até recompra.

**Objetivo:** identificar possíveis fatores associados ao comportamento de recompra.

### 5.4 Correlação entre variáveis

Foi construída uma matriz de correlação para avaliar as relações entre as principais variáveis numéricas.

A análise permitiu identificar variáveis com maior associação com a recompra e também possíveis redundâncias entre variáveis explicativas.

Um exemplo importante identificado foi a correlação entre:

`cli_frequencia_pedidos` × `cli_total_pedidos`

que apresentou forte redundância e deverá ser considerada na etapa de modelagem.

---

# 🔎 6. Principais Insights da EDA

A análise exploratória permitiu identificar alguns padrões relevantes:

### 🛒 Volume dos pedidos

A maior parte dos pedidos está concentrada em volumes menores, especialmente entre 1 e 2 unidades, indicando um padrão de consumo recorrente de baixo volume.

### 📅 Comportamento temporal

A quantidade de pedidos apresenta variações ao longo do período analisado e entre os dias da semana, indicando a existência de padrões temporais que podem ser relevantes para previsão de demanda.

### 🔄 Comportamento de recompra

Foi observada concentração significativa das recompras em intervalos curtos, especialmente nos primeiros 15 dias após um pedido.

### 👥 Perfil dos clientes

A base apresenta diferentes níveis de recorrência, desde clientes com poucos pedidos até clientes com histórico elevado de compras, caracterizando diferentes perfis de consumo.

### ⏱️ Intervalo entre compras

O intervalo médio histórico entre pedidos apresentou relação relevante com o intervalo observado até a próxima compra, sugerindo que o comportamento passado pode contribuir para antecipar o próximo pedido.

### 🌦️ Sazonalidade

Foram observadas diferenças no comportamento de recompra entre períodos sazonais, indicando que fatores temporais podem contribuir para explicar parte da variação na demanda.

---

# 🤖 7. Machine Learning — Próxima Etapa

Com a EDA concluída, a próxima etapa será desenvolver um modelo de **Machine Learning supervisionado** para classificação.