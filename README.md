# 🧠 Projeto Real: Previsão de Recompra de Água Mineral com Machine Learning

Este projeto tem como objetivo desenvolver um modelo de Machine Learning capaz de prever a próxima compra de vasilhame de água mineral realizada pelos clientes, permitindo antecipar demandas, otimizar a logística de entrega e apoiar a tomada de decisão baseada em dados.

A iniciativa surgiu de uma necessidade real de negócio: identificar clientes com alta probabilidade de realizar um novo pedido em determinado período, possibilitando contato proativo, melhor planejamento operacional e aumento da eficiência no atendimento.

## 🧩 Etapas Desenvolvidas

**1. Estruturação e digitalização dos dados:** \
Os dados utilizados não estavam originalmente em formato digital, sendo registrados manualmente em agendas físicas utilizadas na operação diária.

Como primeira etapa, foi realizada a digitalização e estruturação dessas informações em planilhas eletrônicas, criando uma base de dados adequada para análise e modelagem.

**2. Adequação à LGPD:** \
Antes do início das análises, foi realizado um processo de anonimização dos dados para garantir conformidade com a Lei Geral de Proteção de Dados (LGPD).

Foram adotadas as seguintes medidas:

- Substituição dos nomes dos clientes por identificadores únicos (id_cliente);
- Remoção de informações pessoais da base analítica;
- Preservação da privacidade dos clientes por meio da utilização exclusiva de dados anonimizados.

**3. Tratamento inicial dos dados:** 
- Importação da base para ambiente de análise;
- Conversão e adequação dos tipos de dados;
- Padronização de datas e variáveis categóricas;
- Estruturação da base para análises futuras.

**4. Engenharia de Atributos (Feature Engineering):** \
Foram desenvolvidas novas variáveis para capturar padrões de comportamento dos clientes, incluindo:

- Ano do pedido;
- Mês do pedido;
- Estação do ano;
- Dias desde a última compra;
- Frequência de compra;
- Intervalo médio entre pedidos;
- Média de unidades adquiridas por cliente;
- Total de pedidos realizados;
- Próxima data de compra;
- Dias até a próxima compra;
- Variável alvo indicando recompra nos próximos 15 dias.

**5. Qualidade dos Dados:** \
Atualmente estão sendo realizadas análises relacionadas a:

- Valores nulos;
- Dados faltantes;
- Registros inconsistentes;
- Identificação de possíveis outliers.

## 📊 Análises Planejadas

Nas próximas etapas serão realizadas análises exploratórias para identificar:

- Padrões de consumo;
- Frequência de recompra;
- Sazonalidade das vendas;
- Comportamento dos clientes;
- Relações entre variáveis explicativas e a recompra.

## 🤖 Modelagem Preditiva

Serão avaliados diferentes algoritmos de Machine Learning, tais como:

- Regressão Logística;
- Árvore de Decisão;
- Random Forest;
- Gradient Boosting;
- Outros modelos adequados ao problema.

Os modelos serão comparados por meio de métricas de classificação, buscando selecionar a solução com maior capacidade preditiva.

## 📈 Resultados Esperados

- Previsão antecipada de novos pedidos;
- Identificação de clientes com maior probabilidade de recompra;
- Melhoria do planejamento logístico;
- Otimização das rotas de entrega;
- Redução do tempo de atendimento;
- Aumento da satisfação e fidelização dos clientes.

## 🚀 Evolução do Projeto

Este é um projeto real e encontra-se em desenvolvimento contínuo. Novas variáveis, análises e modelos serão incorporados conforme a evolução da base de dados e a validação dos resultados obtidos.

O objetivo é transformar registros históricos de vendas em informações estratégicas capazes de apoiar decisões operacionais e comerciais de forma mais eficiente e inteligente.

## ✅ Conclusão

O projeto demonstra a aplicação prática da Ciência de Dados e do Machine Learning em um contexto real de negócio. A partir da digitalização, tratamento e modelagem dos dados, busca-se construir uma solução capaz de prever o comportamento de compra dos clientes, gerando ganhos operacionais, melhorando a experiência do consumidor e contribuindo para uma gestão mais orientada por dados.