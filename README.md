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

## ⚙️ 4. Engenharia de atributos

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

## 📊 5. Análise Exploratória de Dados (EDA)

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

## 🔎 6. Principais Insights da EDA

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

## 🤖 7. Machine Learning — Modelagem Preditiva

Com a conclusão da etapa de Análise Exploratória de Dados (EDA), iniciou-se a construção dos modelos de Machine Learning com o objetivo de prever a quantidade de dias até a próxima recompra (`target_dias_ate_recompra`).

Por se tratar de uma variável numérica contínua, o problema foi estruturado como uma tarefa de regressão supervisionada.

Antes do treinamento, foram realizadas etapas adicionais de preparação da base, incluindo:

- transformação de variáveis categóricas;
- tratamento de valores ausentes;
- remoção de variáveis com potencial de data leakage;
- análise e remoção de atributos redundantes;
- separação entre variáveis preditoras (X) e variável alvo (y);
- divisão da base em treino e teste.

A preocupação com data leakage foi especialmente importante para garantir que o modelo utilizasse apenas informações que estariam disponíveis no momento em que a previsão fosse realizada.

---

### 7.1 Modelos avaliados

Foram testadas diferentes abordagens de regressão para identificar aquela com melhor capacidade de generalização:

- Regressão Linear;
- Árvore de Decisão;
- Random Forest;
- Regressão Ridge;
- Regressão Lasso.

Os modelos foram comparados utilizando principalmente:

- MAE (Mean Absolute Error);
- RMSE (Root Mean Squared Error);
- R² (Coeficiente de Determinação).

O **MAE** foi definido como a principal métrica de avaliação, pois permite interpretar diretamente o erro médio das previsões em dias.

---

### 7.2 Validação cruzada

Além da avaliação utilizando os conjuntos de treino e teste, foi aplicada Cross Validation com 5 folds.

A validação cruzada permitiu avaliar o comportamento dos modelos em diferentes divisões dos dados, reduzindo a dependência de uma única separação entre treino e teste.

Para a comparação dos modelos, o **MAE médio da validação cruzada** foi utilizado como um dos principais critérios de seleção, buscando identificar uma solução com menor erro e maior estabilidade.

---

### 7.3 Comparação dos modelos

A comparação inicial demonstrou que a Regressão Linear apresentou maior estabilidade e melhor capacidade de generalização para a base utilizada.

Embora modelos mais complexos, como Árvore de Decisão e Random Forest, tenham apresentado bom desempenho nos dados de treinamento, foi observada uma diferença maior entre treino e teste, indicando menor estabilidade na generalização.

Dessa forma, a Regressão Linear foi selecionada como ponto de partida para as etapas seguintes de otimização.

---

### 7.4 Otimização do modelo

Após a seleção da Regressão Linear, foram realizadas novas estratégias para verificar se era possível melhorar sua capacidade preditiva.

---

### 7.4.1 Teste de diferentes conjuntos de variáveis

Foram avaliadas diferentes combinações de atributos para verificar quais conjuntos apresentavam melhor desempenho na previsão dos dias até a recompra.

Essa etapa buscou reduzir informações pouco relevantes e evitar que variáveis redundantes prejudicassem a capacidade de generalização do modelo.

A comparação foi realizada utilizando principalmente o MAE, complementado por RMSE e R².

---

### 7.4.2 Teste de interações

Também foram testadas novas variáveis construídas a partir da interação entre atributos comportamentais.

Foram criados:

- `int_indice_urgencia` — combinação entre os dias desde o último pedido e o intervalo médio entre compras;
- `int_consumo_acumulado` — combinação entre a média de águas por pedido e o total de pedidos realizados.

O objetivo foi representar relações que não seriam capturadas individualmente pelas variáveis originais.

A inclusão dessas interações apresentou melhora no erro de previsão.

O modelo passou a apresentar aproximadamente:

- **MAE CV:** 7,71 dias;
- **MAE Teste:** 9,84 dias;
- **R² Teste:** 0,29;
- **RMSE Teste:** 32,91 dias.

O resultado indica que, em média, o modelo apresenta erro de aproximadamente 9,84 dias no conjunto de teste.

A diferença entre MAE e RMSE também indica a presença de alguns erros de maior magnitude, associados principalmente a clientes que apresentam intervalos de recompra muito superiores ao comportamento predominante da base.

---

### 7.5 Modelos regularizados

Após os testes de variáveis e interações, foram avaliadas técnicas de regularização aplicadas à regressão linear:

**Ridge Regression**

A Regressão Ridge foi utilizada com padronização das variáveis e busca do parâmetro `alpha` por validação cruzada.

**Lasso Regression**

Também foi aplicada a Regressão Lasso, utilizando padronização e busca de hiperparâmetros por meio de GridSearchCV.

A utilização dessas técnicas teve como objetivo controlar possíveis efeitos de multicolinearidade, melhorar a estabilidade do modelo e avaliar se a regularização poderia produzir uma solução com melhor capacidade de generalização.

---

### 7.6 Seleção do modelo final

A comparação entre Ridge e Lasso apresentou resultados muito próximos no conjunto de teste.

Ambos apresentaram:

- **MAE Teste:** aproximadamente 9,84 dias;
- **RMSE Teste:** aproximadamente 32,91 dias;
- **R² Teste:** aproximadamente 0,29.

A principal diferença ocorreu na validação cruzada:

- **Ridge:** MAE CV ≈ 7,7148 dias;
- **Lasso:** MAE CV ≈ 7,7121 dias.

Apesar da diferença ser pequena, o Lasso apresentou o menor MAE médio na validação cruzada e, por isso, foi selecionado como modelo final.

---

### 7.7 Ajuste dos hiperparâmetros

Após a seleção do Lasso, foi realizada uma busca mais detalhada dos hiperparâmetros utilizando `GridSearchCV` com validação cruzada de 5 folds.

Foram avaliados diferentes valores de:

- `alpha`;
- `max_iter`;
- `tol`.

A melhor configuração encontrada foi:

alpha = 0,02 \
max_iter = 5000 \
tol = 0,001

Essa configuração apresentou MAE médio de validação cruzada de aproximadamente 7,7112 dias.

Embora a melhoria em relação à configuração anterior tenha sido pequena, essa combinação apresentou o menor erro médio entre as configurações testadas e, portanto, foi definida como a configuração final do modelo.

No conjunto de teste, entretanto, as métricas permaneceram praticamente inalteradas, demonstrando que o ajuste dos hiperparâmetros trouxe pouca diferença prática para a capacidade preditiva do modelo.

---

### 7.8 Resultado final

O modelo final selecionado foi uma Regressão Linear com regularização Lasso, utilizando as variáveis e interações definidas durante o processo de otimização.

Os principais resultados no conjunto de teste foram:


Métrica	Resultado
MAE	9,84 dias
RMSE	32,91 dias
R²	0,29

|Métrica|   |   |   |Resultado   |
|---|---|---|---|---|
|MAE|   |   |   |9,84 dias|
|RMSE|   |   |   |32,91 dias   |
|R²|   |   |   |0,29|

O MAE de 9,84 dias indica que o modelo apresenta, em média, uma diferença de aproximadamente dez dias entre a previsão e o intervalo observado até a recompra.

O R² de aproximadamente 0,29 indica que o modelo consegue explicar parte da variabilidade existente no intervalo entre as compras, mas ainda existe uma parcela relevante do comportamento que não é explicada pelas variáveis atualmente disponíveis.

Portanto, o modelo deve ser interpretado como uma ferramenta de apoio à decisão, e não como uma previsão exata da data de recompra.

---

## 💡 10. Aplicação no Negócio

Mesmo com as limitações atuais, a previsão pode ser utilizada como apoio para estratégias de relacionamento com clientes.

Por exemplo, a empresa poderá utilizar a estimativa de recompra para:

- identificar clientes próximos do período esperado de nova compra;
- realizar contatos proativos;
- enviar lembretes de recompra;
- planejar antecipadamente as entregas;
- identificar clientes com comportamento de recompra mais previsível.

A utilização do modelo dessa forma permite transformar o histórico de pedidos em uma ferramenta de apoio à tomada de decisão operacional e comercial.

---

## 🔎 11. Limitações Identificadas

Os resultados também evidenciaram algumas limitações importantes.

O comportamento de recompra possui elevada variabilidade, principalmente entre clientes que permanecem longos períodos sem realizar novos pedidos. Esses casos contribuem para o aumento do RMSE e demonstram que parte do comportamento não pode ser explicada apenas pelo histórico atualmente disponível.

Além disso, o conjunto de dados foi construído a partir de registros históricos da operação, o que limita a quantidade e variedade de informações disponíveis para o modelo.

Dessa forma, a evolução da solução depende também da incorporação de novas informações capazes de representar melhor o comportamento dos clientes.

---

## 🚀 12. Próximas Melhorias

A etapa atual encerra o desenvolvimento inicial do modelo preditivo. Futuramente, o projeto poderá receber novas melhorias, incluindo:

- análise mais especifica dos tipos de clientes (K-means);
- inclusão de novas variáveis comportamentais;
- criação de novos atributos de engenharia de dados;
- incorporação de informações relacionadas ao histórico de clientes;
- avaliação de outros algoritmos de Machine Learning;
- novos testes de hiperparâmetros;
- experimentação de modelos mais complexos;
- novas estratégias de validação;
- comparação entre diferentes abordagens de previsão;
- acompanhamento do desempenho do modelo ao longo do tempo (Dashboards).

## ✅ Conclusão

O projeto evoluiu de uma base de pedidos registrada manualmente para uma solução de análise e previsão baseada em Machine Learning. O processo contemplou a digitalização e anonimização dos dados, tratamento, engenharia de atributos, análise exploratória, seleção de variáveis, avaliação de diferentes algoritmos e otimização do modelo.

Após a comparação entre diferentes abordagens, a Regressão Linear com regularização Lasso foi selecionada como modelo final por apresentar o melhor equilíbrio entre erro, estabilidade e capacidade de generalização para a base utilizada.

Embora o modelo ainda apresente limitações e não explique toda a variabilidade do comportamento de recompra, os resultados demonstram potencial para apoiar ações de relacionamento, planejamento operacional e antecipação de pedidos.

Neste momento, o projeto é considerado concluído em sua primeira versão de Machine Learning. Futuramente, novas variáveis, técnicas de engenharia de atributos e algoritmos poderão ser incorporados para buscar melhorias na capacidade preditiva e aproximar a solução das necessidades reais do negócio.