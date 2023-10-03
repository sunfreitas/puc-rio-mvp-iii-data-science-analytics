# PUC Rio - MVP Sprint III
# Pós-graduação em Data Science & Analytics
## Franncisco das Chagas Alves Freitas
## SUMÁRIO

- [OBJETIVOS](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/tree/main#objetivos)
- [DETALHAMENTO](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/tree/main#detalhamento)
  - [Busca pelos Dados](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/README.md#1-busca-pelos-dados)
  - [Coleta](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/README.md#2-coleta)
  - [Modelagem](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/README.md#3-modelagem)
  - [Carga](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/README.md#4-carga)
      - a) [Qualidade dos Dados](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/README.md#41-qualidade-dos-dados)
      - b) [Solução do Problema](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/README.md#42-solu%C3%A7%C3%A3o-do-problema)
- [APÊNDICES](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/README.md#ap%C3%AAndices)
  - A - [Sobre o Dota 2](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/README.md#a---sobre-o-dota-2)

## OBJETIVOS
### Objetivo Geral
Caracterizar um rank detalhado com os três heróis com o maior número de *kills* no jogo **Dota 2** (Vide Apêndice A);

### Objetivos Específicos
- Identificar os três Heróis com a maior contagem de kills ordenados do maior para o menor;
- Inferir a quantidade de usuários que utilizaram os heróis com maior pontuação de kills;
- Inferir a quantidade de vezes em que os heróis obtiveram vitória em um dos lados da arena do jogo.

## DETALHAMENTO

### 1. Busca pelos Dados

Para a realização deste trabalho os dados necessários para a análise foram retirados do repositório [Dota 2 Matches](https://www.kaggle.com/datasets/devinanzelmo/dota-2-matches) localizado na plataforma Kaggle.

![](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2023-47-00.png)
**Imagem 1. Repositório de dados Dota 2 Matches localizado no Kaggle.**

### 2. Coleta

Após a seleção dos conjuntos de arquivos - *players.csv*, *heroes.csv* e *matches.csv*, o download destes foi realizado para o computador local. Em seguida foi criado um **S3 Bucket** na **Amazon AWS**, onde o upload dos arquivos citados anteriormente foram armazenados por meio de upload.

![](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2023-00-52.png)
**Imagem 2. Bucket S3 com os arquivos matches.csv, heroes.csv e players.csv.**

### 3. Modelagem
Nesta etapa foi utilziado o **AWS Glue**, o qual ficou responsável pela extração, transformação e carga dos dados. Durante este processo, foi configurado um banco de 
dados **Redshift** sem servidor. O modelo proposto para obter a tabela **fato** foi o *estrela*, levando em consideração as dimensões **heróis** e **matches**. Para cada fonte de dados (os três arquivos CSV) armazenados no bucket s3 foi realizada a transformação dos dados (Imagem 4), e em seguida a carga destes em três tabelas no Redshift.

![](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2023-57-26.png)
**Imagem 3. Criação do job utilizando AWS Glue Studio.**

### 4. Carga

Segue abaixo as imagens dos campos que foram removidos, deixando apenas os que são necessários para resolver o fato proposto nos objetivos, assim como a alteração do tipos de dados destes campos.

![Resultado Final](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2022-59-55.png)
**Imagem 4. Remoção de atributos e modificação dos tipos de dados na camada de transformação do job.**


![](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2023-00-02.png)
**Imagem 5. Atributos da tabela 'heroes' a serem transformados no job.**

#### 4.1. Qualidade dos Dados

Os dados adquiridos no repositório [Dota 2 Matches](https://www.kaggle.com/datasets/devinanzelmo/dota-2-matches) a princípio não apresentou problemas de qualidade dos dados. Porém, o campo 
**radiant_win**, que seria utilizado para calcular a quantidade de vitórias em um dos lados da arena do jogo, está definido com os valores True e False mas estão armazenados como strings.

![](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-02%2000-01-15.png)
**Imagem 6. Visualização da tabela matches com o campo 'radiant_win' com valores booleanos mas tipados como string.**

#### 4.2. Solução do Problema

Abaixo segue uma imagem da query realizada para criar o rank de heróis com mais kills, acompanhados da quantidade de kills e o número de jogadores que utilizaram o herói.

![Resultado Final](https://github.com/sunfreitas/puc-rio-mvp-iii-data-science-analytics/blob/main/Screenshot%20from%202023-10-01%2022-58-39.png)
**Imagem 7. Query sendo executada e a tabela fato logo abaixo.**

## APÊNDICES

### A - Sobre o Dota 2

Mais informações sobre o jogo podem ser encontradas no site oficial [https://www.dota2.com/home](https://www.dota2.com/home).
