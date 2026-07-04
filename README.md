# MVP – Machine Learning & Analytics
## Forecasting da Taxa de Mortalidade Infantil (Under-Five Mortality Rate – U5MR)

Este repositório contém o MVP desenvolvido para a disciplina **Machine Learning & Analytics**, cujo objetivo é construir e avaliar um modelo de aprendizado de máquina capaz de prever a taxa de mortalidade de crianças menores de cinco anos (Under-Five Mortality Rate – U5MR) a partir de dados históricos publicados pelo UNICEF.

O projeto utiliza técnicas de **forecasting supervisionado**, comparando diferentes modelos de regressão e aplicando o modelo selecionado para projetar a evolução da U5MR entre **2025 e 2030**, em apoio à análise da Meta 3.2 dos Objetivos de Desenvolvimento Sustentável (ODS).

---

## Objetivo

Construir um modelo de Machine Learning capaz de:

- prever a U5MR anual por país;
- comparar diferentes modelos candidatos;
- selecionar o modelo com melhor desempenho;
- gerar projeções para o período de 2025–2030;
- analisar quais países tendem a atingir a meta global de **25 mortes por 1.000 nascidos vivos** até 2030.

---

## Dataset

**Fonte:**

UNICEF – Under-five mortality rate dataset

https://data.unicef.org/resources/dataset/under-five-mortality-data/

O notebook utiliza a versão pública do arquivo hospedada neste repositório para garantir a reprodutibilidade.

---

## Modelos avaliados

- Baseline (Dummy Regressor)
- Regressão Linear
- Gradient Boosting Regressor
- Random Forest Regressor

O Random Forest otimizado foi selecionado como modelo final após comparação utilizando:

- MAPE
- MAE
- RMSE
- R²

---

## Estrutura do projeto

O notebook segue o fluxo clássico de um projeto de Ciência de Dados:

1. Definição do problema
2. Preparação do ambiente
3. Coleta e preparação dos dados
4. Análise exploratória (EDA)
5. Pré-processamento
6. Modelagem e inferência
7. Pós-processamento
8. Apresentação dos resultados
9. Conclusão e geração de valor

---

## Tecnologias utilizadas

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Plotly

---

## Executando o projeto

Basta abrir o notebook no Google Colab.

Notebook original:

https://colab.research.google.com/drive/1WKRB1xiQJ2c2XZLCvP-ERBh54pmgrD1O?usp=sharing

---

## Autor

**Rodrigo de Sousa Araujo**

MVP desenvolvido para a disciplina **Machine Learning & Analytics**.
