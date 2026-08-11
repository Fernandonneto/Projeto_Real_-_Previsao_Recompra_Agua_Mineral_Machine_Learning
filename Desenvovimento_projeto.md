# DESENVOLVIMENTO DO PROJETO

## Tratamento de dados
[✔️] - **Verificar os tipos de dados das colunas (data, str, int, ...), se precisar, formatar para o padrão certo;**

    [✔️] - Criar uma coluna somente com os anos (yyyy);
    [✔️] - Criar uma coluna somente com os meses (mm);
    [✔️] - Buscar identificar quais são os meses de cada estação e criar uma coluna com eles; 
    [✔️] - Desenvolver colunas como dias desde a última compra, a frequência de compra, o intervalo médio entre pedidos, a média de águas adquiridas por clientes, o total de pedidos realizados e a informação sobre a próxima compra;

[✔️] - **Verificar valores ausentes, nulos e outliers e tráta-los;**

    [✔️] - Tratamento de valore ausentes e nulos;
    [✔️] - Tratamento de outliers;

[✔️] - **Padronizar base de dados.** 

    [✔️] - Padronizar o nome das colunas; 
    [✔️] - Padronizar a númeração do ID, colocando 4 digitos como padrão;

## Análise Exploratória de Dados (EDA)
[✔️] - **Informações iniciais da base de dados;**

[✔️] - **Planejamento da EDA;**

[✔️] - **Execução;**

    [✔️] - 1 Etapa;
    [✔️] - 2 Etapa;
    [✔️] - 3 Etapa;
    [✔️] - 4 Etapa; 
    [✔️] - Conclusão;

## Machine Learnig 
[✔️] - **Tratamento dos dados para ML;**

    [✔️] - Transformar as colunas texto "obs_pedido" e "dt_estacao" em binária;
    [✔️] - Transformar a coluna texto "dt_semana" com One-Hot Encoding e excluir variável;
    [✔️] - Na coluna "cli_intervalo_medio" imputar a mediana para os clientes novos;
    [✔️] - Exclusão da coluna "cli_frequencia_pedidos";
    [✔️] - Transformar a variável "qtd_aguas_ticket" em registro válido

[ ] - **ML - Para duelo;**

    [✔️] - Preparação de ML para duelo;
        [✔️] - Sepração de X e y;
        [✔️] - Separação da base de treino e teste;
    [ ] - Regressão Linear; ⬅️
    [ ] - Árvore de Decisão;
    [ ] - Random Forest;

## Dashboard para acompanhamento de KPI's
[ ] - **Desenvoler a "Régua de relacionamento por ciclo de vida do LTV", informado na EDA 2º-A;**
[ ] - **Desenvolver a "Automação de gatilhos logísticos preditivos de recompra", informado na EDA 2º-B;**
[ ] - **Desenvoler a "Régua de recompra para transição de faixa e ciclo de vida (LTV)", informado na EDA 2º-D, para dar mais forças a EDA 2º-A;**
[ ] - **Desenvolver a "Modulação sazonal de modelo preditivo (Ajuste de clima)", informado na EDA 3º-E;**

## Melhoria do README
[ ] - **Desenvolver - "ML que será utilizado também será aplicado e servira na melhoria da lógistica, pois sabendo se o cliente realmente vai querer a água no próximo dia ou no mesmo dia (pois a mensagem sera enviada um dia antes), da para planejar rotas de entregas mais eficientes, assim como preparar o estoque para a demanda, sem deixar faltar água."**

OBS:
[ ] - Levar em consideração a "Modulação sazonal de modelo preditivo (Ajuste de clima)", informado na EDA 3º-E;