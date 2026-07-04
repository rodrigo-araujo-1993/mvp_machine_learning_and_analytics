# Perguntas Frequentes (FAQ)

## Definição do problema

**Qual é a descrição do problema?**
Prever a taxa de mortalidade de crianças menores de cinco anos (Under-Five Mortality Rate – U5MR) em cada país até 2030.

**Qual é o objetivo do modelo?**
Construir um modelo de Machine Learning capaz de prever a U5MR anual e de gerar projeções para o período de 2025–2030.

**Que tipo de problema foi tratado?**
Forecasting supervisionado com algoritmos de regressão para séries temporais.

**Por que esse problema pode ser resolvido com Machine Learning?**
Porque a U5MR apresenta padrões temporais históricos que o modelo pode aprender para estimar valores futuros.

**Quais hipóteses foram consideradas?**
- A série histórica contém padrões capazes de apoiar previsões futuras.
- O período de 2000–2024 é representativo para fins de treinamento.
- Fatores externos não modelados (como conflitos, pandemias e mudanças nas políticas públicas) podem limitar a precisão das projeções.

**Quais restrições foram consideradas?**
Foram utilizadas apenas as estimativas *Median* do UNICEF, restringindo a análise ao período de 2000–2024.


## Dados

**Qual dataset foi utilizado?**
UNICEF – Under-five Mortality Rate (U5MR).

**Qual é a fonte dos dados?**
UNICEF / UN Inter-agency Group for Child Mortality Estimation (UN IGME).

**Como os dados foram carregados?**
Por meio de um arquivo .xls disponibilizado em um repositório público.

**Qual o tamanho da base?**
Após o pré-processamento, há aproximadamente **5.000 instâncias** distribuídas entre cerca de **200 países**.

**Quais são os principais atributos?**
- Country.Name
- ISO.Code
- SDG.Region
- Year
- Under_Five_Mortality_Rate

**Existe variável-alvo?**
Sim. A variável **target_next_year** corresponde à U5MR do ano seguinte.

**Quais limitações o dataset apresenta?**
Não considera fatores socioeconômicos, conflitos, pandemias ou políticas públicas, limitando-se a estimativas anuais de mortalidade infantil.


## Preparação dos dados

**Como os dados foram preparados?**
- Conversão da base de formato *wide* para *tidy*;
- Remoção de atributos desnecessários;
- Criação de variáveis temporais (*lags* e média móvel);
- Construção da variável-alvo para o ano seguinte.

**Como os valores ausentes foram tratados?**
Foram removidas apenas as linhas que não possuíam histórico suficiente para construção das variáveis temporais.

**Quais transformações foram aplicadas?**
- One-Hot Encoding para a variável categórica **SDG.Region**;
- Pipeline de pré-processamento utilizando Scikit-learn.

**Houve preocupação com vazamento de dados?**
Diversas medidas foram adotadas ao longo do projeto para evitar vazamento de dados (*data leakage*):
- A divisão entre treinamento e teste foi realizada por **ordem temporal (Temporal Holdout)**, preservando a cronologia da série e impedindo que informações futuras fossem utilizadas para prever anos anteriores.
- O ano de **2024** foi excluído dos conjuntos de treinamento e de teste, sendo reservado exclusivamente como condição inicial do forecasting recursivo para as projeções de 2025–2030.
- A variável-alvo (`target_next_year`) foi construída apenas com base no valor observado no ano seguinte, evitando incorporar informações futuras às variáveis explicativas.
- Os atributos temporais (*lags* e média móvel) foram calculados exclusivamente a partir de observações passadas, garantindo que cada registro utilizasse apenas as informações disponíveis até aquele momento.
- Todo o pré-processamento (codificação One-Hot e demais transformações) foi encapsulado em um **Pipeline** do Scikit-learn, garantindo que os parâmetros das transformações fossem aprendidos apenas com o conjunto de treinamento e posteriormente aplicados ao conjunto de teste.
- A otimização de hiperparâmetros por meio do **RandomizedSearchCV** foi realizada exclusivamente no conjunto de treinamento, mantendo o conjunto de teste completamente isolado para a avaliação final.
- O conjunto de teste foi utilizado apenas uma vez, ao final do processo de modelagem, para estimar a capacidade de generalização do modelo.
---

## Divisão dos dados

**Como foi realizada a divisão treino/teste?**
Foi utilizada uma divisão temporal (*Temporal Holdout*).

- Treinamento: **2003–2022**
- Teste: **2023**

O ano de **2024** foi reservado para iniciar o forecasting recursivo.

**Foi utilizada validação cruzada?**
Sim. Os modelos foram avaliados por meio de validação cruzada durante o treinamento.

**A ordem temporal foi respeitada?**
Sim. Não houve embaralhamento dos dados.

---

## Modelagem

**Qual foi o baseline?**
Persistance Model

**Quais modelos foram avaliados?**
- Regressão Linear
- Gradient Boosting Regressor
- Random Forest Regressor

**Por que esses modelos foram escolhidos?**
Porque representam diferentes níveis de complexidade, permitindo comparar modelos lineares e não lineares adequados ao problema.

**Os modelos foram comparados de forma justa?**
Sim. Todos utilizaram o mesmo conjunto de treino, teste, pipeline e métricas de avaliação.

**Foi observado overfitting?**
Não. O modelo final apresentou boa capacidade de generalização.

---

## Otimização

**Foi realizado ajuste de hiperparâmetros?**
Sim, para o Random Forest.

**Qual estratégia foi utilizada?**
RandomizedSearchCV.

**A otimização melhorou o desempenho?**
Sim. O modelo otimizado apresentou redução dos erros e melhora das métricas em relação à versão original.

---

## Avaliação

**Quais métricas foram utilizadas?**
- MAPE
- MAE
- RMSE
- R²

**Qual foi o melhor modelo?**
Random Forest otimizado.

**Os resultados foram consistentes?**
Sim. O modelo superou o baseline, preservou as tendências históricas e gerou projeções coerentes para o período de 2025–2030.

**Quais são as principais limitações?**
- Ausência de variáveis socioeconômicas;
- Forecast recursivo sujeito ao acúmulo de erros;
- Dependência da continuidade das tendências históricas.

---

## Conclusão

**Qual foi a melhor solução encontrada?**
Random Forest otimizado aplicado a um processo de previsão recursiva.

**O objetivo do MVP foi atingido?**
Sim. O modelo foi treinado, validado, comparado ao baseline e utilizado para projetar a U5MR até 2030.

**Quais são os próximos passos?**
- Incorporar variáveis socioeconômicas e demográficas;
- Avaliar modelos específicos para séries temporais (XGBoost, LightGBM, Prophet e LSTM);
- Construir intervalos de previsão;
- Desenvolver dashboards para monitoramento contínuo das projeções.
