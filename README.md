# Amazon Review Spam Detection

## 1. Introdução

No âmbito da unidade curricular de Processamento e Modelação de Big Data, integrada no mestrado em Ciência de Dados, foi proposto a realização do presente projeto. Para a elaboração do mesmo foi selecionada uma base de dados da Amazon, que contém reviews de produtos na categoria "Clothing, Shoes, and Jewelry". 

O objetivo deste projeto é desenvolver e implementar uma solução computacional para responder a um problema de análise de dados em larga escala, especificamente focado na distinção entre reviews autênticas e tentativas de manipulação (spam). A análise preliminar dos dados foi essencial para identificar as variáveis mais relevantes, com base nas quais foram desenvolvidos e testados vários modelos em amostras reduzidas.

O projeto incluiu a modelação de diferentes algoritmos de aprendizagem supervisionada, tais como Regressão Logística, Support Vector Machine, Árvores de Decisão, Florestas Aleatórias e Gradient-Boosted Trees. Cada modelo foi treinado e avaliado utilizando métricas de desempenho como a accuracy, precision e recall, a fim de determinar qual a abordagem que oferece a melhor capacidade de distinguir entre reviews autênticas e de spam.

## 2. Formulação do Problema

O problema central deste projeto é desenvolver e implementar um modelo computacional eficaz na identificação de reviews de produtos da Amazon classificadas como spam. 

### Abordagens Principais:

- **Processamento de Texto**: Pipeline personalizada incluindo tokenização, remoção de stop words, HashingTF e cálculo do IDF.
- **Feature Engineering**: Seleção e transformação de colunas relevantes como ‘helpfulTotalRatio’, ‘reviewUpVotes’, ‘reviewLength’, ‘isWeekend’, entre outras.

## 3. Base de Dados

A base de dados escolhida para este projeto, extraída do Kaggle e intitulada "Clothing_Shoes_and_Jewelry", compreende aproximadamente 5.504.331 reviews de produtos. Cada registo na base de dados é composto por múltiplos campos fundamentais para a análise e modelação dos dados.

### 3.1 Valores Omissos

Foram eliminadas 13.180 observações devido à ausência de informação no campo 'reviewerName', resultando num conjunto de dados final com 5.491.151 observações.

### 3.2 Transformação e Criação de Variáveis

Transformações e criações de variáveis fundamentais enriquecem a análise e a performance do modelo preditivo:

- **Comprimento das reviews**.
- **Média das avaliações e popularidade dos produtos**.
- **Variável helpful**: Transformada em helpfulTotalRatio e categorizada.
- **Variável containsQuestion**: Identificação de perguntas nas reviews.
- **Variável hasLink**: Identificação de links nas reviews.
- **Variáveis de tempo**: Conversão da coluna reviewTime para formato de data e criação de isWeekend.
- **Nº de reviews por user**.

### 3.3 Balanceamento dos Dados

Aplicou-se a técnica de undersampling para ajustar o desequilíbrio entre as classes da variável target.

### 3.4 Relações entre Variáveis

Construção de uma matriz de correlação para otimizar os modelos preditivos e compreender melhor as inter-relações entre as variáveis.

### 3.5 Variáveis Irrelevantes

Remoção de colunas consideradas irrelevantes para o problema em análise, como category, asin, reviewerID, reviewerName, id, unixReviewTime, reviewTime e summary.

## 4. Modelação

Após a preparação e transformação dos dados, foram implementados modelos de aprendizagem supervisionada utilizando PySpark:

- **Primeira Abordagem (Text Processing)**: Pipeline de pré-processamento de texto.
- **Segunda Abordagem (Feature Engineering)**: Seleção de colunas relevantes e utilização do VectorAssembler.

Modelos implementados: Regressão Logística, Support Vector Machine (SVM), Árvores de Decisão, Florestas Aleatórias e Gradient-Boosted Trees.

## 5. Resultados

### Primeira Abordagem (Text Processing)

- **Logistic Regression**: Accuracy de 74%.
- **Support Vector Machine**: Melhor desempenho com accuracy de 79%.
- **Árvores de Decisão**: Accuracy de 67%.
- **Florestas Aleatórias**: Accuracy de 61%.
- **Gradient-Boosted Trees**: Accuracy de 72%.

### Segunda Abordagem (Feature Engineering)

- **Logistic Regression**: Accuracy de 71%.
- **Support Vector Machine**: Accuracy de 71%.
- **Árvores de Decisão**: Accuracy de 72%.
- **Florestas Aleatórias**: Accuracy de 73%.
- **Gradient-Boosted Trees**: Accuracy de 73%.

## 6. Conclusão

Os modelos desenvolvidos possuem uma capacidade específica em distinguir entre reviews genuínas e spam. A abordagem de processamento de texto foi a mais eficaz, com o SVM se destacando como o melhor modelo.

## Melhorias Futuras

- **Técnicas Avançadas de Processamento de Linguagem Natural (NLP)**.
- **Ajuste de Hiperparâmetros**: Utilização de Grid Search, Random Search ou Bayesian Optimization.
- **Modelos Ensemble**: Combinação de diferentes modelos preditivos através de técnicas de ensemble learning como Stacking.

## 7. Bibliografia

- Naveed, H. N. (n.d.). Amazon Product Review Spam and Non-Spam. Kaggle. Disponível em: [https://www.kaggle.com/datasets/naveedhn/amazon-product-review-spam-and-non-spam?select=Clothing_Shoes_and_Jewelry](https://www.kaggle.com/datasets/naveedhn/amazon-product-review-spam-and-non-spam?select=Clothing_Shoes_and_Jewelry)
- Hussain, N., Mirza, H. T., Hussain, I., Iqbal, F., & Memon, I. (2020). Review Detection Using the Linguistic and Spammer Behavioral Methods. IEEE. Disponível em: [https://www.researchgate.net/publication/339821179_Spam_Review_Detection_Using_the_Linguistic_and_Spammer_Behavioral_Methods](https://www.researchgate.net/publication/339821179_Spam_Review_Detection_Using_the_Linguistic_and_Spammer_Behavioral_Methods)
- Sampath, A. (n.d.). Amazon Review Spam Detection. Kaggle. Disponível em: [https://www.kaggle.com/code/abhilashsampath/amazon-review-spam-detection](https://www.kaggle.com/code/abhilashsampath/amazon-review-spam-detection)
