# PUC Rio - MVP Sprint III
# Pós-graduação em Data Science & Analytics
## Franncisco das Chagas Alves Freitas
## SUMÁRIO

- OBJETIVOS
- DETALHAMENTO
  - Busca pelos Dados
  - Coleta
  - Modelagem
  - Carga
      - a) Qualidade dos Dados
      - b) Solução do Problema
- APÊNDICES
  - A - Sobre o Dota 2

## OBJETIVOS
### Objetivo Geral
Caracterizar um rank detalhado com os três heróis com o maior número de *kills* no jogo **Dota 2**;

### Objetivos Específicos
- Identificar os três Heróis com a maior contagem de kills ordenados do maior para o menor;
- Inferir a quantidade de usuários que utilizaram os heróis com maior pontuação de kills;
- Inferir a quantidade de vezes em que os heróis obtiveram vitória em um dos lados da arena do jogo.

## DETALHAMENTO

### 1. Busca pelos Dados

Para a realização deste trabalho os dados necessários para a análise foram retirados do repositório [Dota 2 Matches](https://www.kaggle.com/datasets/devinanzelmo/dota-2-matches) localizado na plataforma Kaggle.

![](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2023-47-00.png)

### 2. Coleta

Após a seleção dos conjuntos de arquivos - *players.csv*, *heroes.csv* e *matches.csv*, o download destes foi realizado para o computador local. Em seguida foi criado um **S3 Bucket** na **Amazon AWS**, onde o upload dos arquivos citados anteriormente foram armazenados por meio de upload.

![](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2023-00-52.png)

### 3. Modelagem
Nesta etapa foi utilziado o **AWS Glue**, o qual ficou responsável pela extração, transformação e carga dos dados. Durante este processo, foi configurado um banco de dados **Redshift** sem servidor.

![](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2023-57-26.png)

### 4. Carga

![Resultado Final](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2022-59-55.png)


![](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2023-00-02.png)

#### 4.1. Qualidade dos Dados

Os dados adquiridos no repositório [Dota 2 Matches](https://www.kaggle.com/datasets/devinanzelmo/dota-2-matches) a princípio não apresentou problemas de qualidade dos dados. Porém, o campo 
**radiant_win**, que seria utilizado para calcular a quantidade de vitórias em um dos lados da arena do jogo, está definido com os valores True e False mas estão armazenados como strings.
![Resultado Final](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2022-58-39.png)
#### 4.2. Solução do Problema

![Resultado Final](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2022-58-39.png)

## APÊNDICES

### A - Sobre o Dota 2

Lorem ipsum...
