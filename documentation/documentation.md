![alt text](https://raw.githubusercontent.com/E-man85/projectII/main/images/dataScienceProject.webp )

# Projeto II

## Parte 1

**Problema:**

-O cliente precisa de atualizar o armazenamento de roupa em cada loja para Outubro de 2019.

**Objetivo:**

-Prever com precisão as vendas semanais considerando sazonalidade,tendência e variáveis explicativas. 

-Análise dos dados que serão utilizados no modelo.

## Data

Os dados recolhidos para a elaboração deste trabalho são três ficheiros em formato .csv:

- cities.csv (2 KB)
- product.csv (47 KB)
- sales.csv (648.3 MB)

Estes dados foram carregados para este repositório podendo ser consultados abaixo:

![logoLink](https://raw.githubusercontent.com/E-man85/projectII/main/images/link.png)

[cities.csv](https://github.com/E-man85/projectII/tree/main/rawData)

[product.csv](https://github.com/E-man85/projectII/tree/main/rawData)

[sales.csv](https://github.com/E-man85/projectII/tree/main/raw_data)

**Nota:** 
O ficheiro ***sales.csv***, devido à sua dimensão, foi disponibilizado no git usando a [extensão do git 'LFS'](https://git-lfs.com/).

1. git lfs install (instalar extensão)
2. git lfs track "*.psd" ( selecionar ficheiro onde usar o GIT LFS)
3. git add .gitattributes ( verificar o ficheiro rastreado )
4. git add file.psd (fazer o commit e push normalmente)
    git commit -m "Add design file"
    git push origin main

## Data Understanding

Foi feita a exploração dos 3 ficheiros de dados, que está disponível em [dataUnderstanding](https://github.com/E-man85/projectII/tree/main/dataUnderstanding).

### product.csv

<details>
<summary><span >Ver product.csv understanding </span></summary>
>
  
O ficheiro tem 10 colunas com 699 registos.

-***product_id***

Coluna com valores do tipo 'object', de 4 catacteres alfanuméricos e valores exclusivos.

-***product_length, product_depth, product_width***

Colunas que representam as dimensões dos produtos, do tipo float64, contêm valores ausentes.

-***cluster_id***

Do tipo 'object',com 10 valores distintos de clusters_id, contêm valores ausentes.

-***hierarchy1_id, hierarchy2_id, hierarchy3_id, hierarchy4_id, hierarchy5_id***

Do tipo 'object', são colunas com as hierarquias do produto.

A primeira hierarquia tem 3 caracteres alfanumérios, sendo que à medida que consultamos nova hierarquia, acrescenta 2  caracteres numéricos à anterior para o mesmo produto.
Podemos ter uma distinção com mais ou menos promenor do produto à medida que acrescentamos mais hierarquias.

exemplo
 (product P0002)

-hierarchy1_id-H03

-hierarchy2_id-H0315

-hierarchy3_id-H031508

-hierarchy4_id-H03150800

-hierarchy5_id-H0315080028

</details>

### cities.csv

<details>
<summary><span>Ver cities.csv understanding</span></summary>
>

O ficheiro tem 6 colunas com 63 registos.

-***store_id***

Coluna com valores do tipo 'object', de 5 catacteres alfanuméricos e valores exclusivos.

-***storetype_id***

Coluna com 4 valores distintos alfanuméricos, atribuindo um tipo a cada store. 
Pode existir o mesmo storetype_id, para diferentes store_id.

-***store_size***

Coluna com valores do tipo 'int64', que representam a dimensão de cada store.

-***city_id_old***

Coluna com valores alfanumericos de 4 caracteres do tipo 'object', reprensentando um id de codigo da city.

-***country_id***

Coluna de um valor exclusivo, do tipo 'object' que refere o pais "TURKEY" .

-***city_code***

Coluna com dados do tipo 'object' que refere o nome da cidade.

A configuração usada neste ambiente não está de acordo com a codificação dos caracteres do ficheiro, e  por essa razão alguns nomes das cidades têm problemas de visualização:

ex: 'Sanl?urfa', 'Adapazar?'

</details>

</details>

### sales.csv

<details>
<summary><span >Ver sales.csv understanding</span></summary>
>

O ficheiro tem 14 colunas com 8886058 registos.

-***Unnamed: 0***

Coluna com valores exclusivos do tipo 'int64', não duplicados e com sequência correta.

-***store_id***

Coluna com valores do tipo 'object', de 5 catacteres alfanuméricos.

-***product_id***

Coluna com valores do tipo 'object', de 4 catacteres alfanuméricos.

-***date***

Coluna do tipo 'object', que se refere à data do transação no formato yyyy-mm-dd.

-***sales***

Coluna do tipo 'float64', que refere a quantidade vendida de um produto.

Existem registos com valores Nan, que analisados representam o mês 10 do ano 2019.

-***revenue***

Coluna do tipo 'float64', que refere ao revenue dos das transações diárias por produto.

Os valores NaN  representam o mês 10 de 2019.

-***stock***

Coluna do tipo 'float64', que refere a quantidade existente do produto .

Os valores NaN  representam o mês 10 de 2019.

-***price***

Coluna do tipo 'float64', que refere o preço unitário do produto.

O preço dos produtos pode variar para diferentes lojas.

Existem valores NaN em diferentes periodos.

-***promo_type_1***

Coluna  tipo 'object', com valores alfanuméricos e com 17 valores distintos.

Refere-se ao tipo1 de promoção .

-***promo_type_2***

Coluna  tipo 'object', com valores alfanuméricos e com 4 valores distintos.

Refere-se ao tipo2 de promoção .

-***promo_bin_1***

Coluna do tipo 'object', e valores e 5 valores distintos, classificando a intensidade da  promoção.['verylow', 'moderate', 'low', 'high', 'veryhigh'].

Esta coluna tem 7653515 NaN e 1232543 com a classificação da intensidade.

-***promo_bin_2***
Coluna do tipo 'object', e valores e 3 valores distintos, classificando a intensidade da promoção.['verylow', 'high', 'veryhigh']

Esta coluna tem 8873337 NaN e 12721 com a classificação da intensidade.

-***promo_discount_2***

Coluna do tipo 'float64', de 6 valores distintos[ 20., 16., 35., 50., 40., 33.], referente à percentagem de desconto do produto na data.

-***promo_discount_type_2***

Coluna do tipo 'object', de  valores distintos ['PR04', 'PR02', 'PR01', 'PR03'], referente ao type2 de promo discount.

</details>

## Raw diagram

<img src="https://raw.githubusercontent.com/E-man85/projectII/main/images/diagram_turkiye_stores.png " alt="Data Schema" width="900" height="400">

## Data Preparation raw files

Cada ficheiro dos dados originais foi preparado individualmente.

![logoLink](https://raw.githubusercontent.com/E-man85/projectII/main/images/link.png)

[dimProduct](https://github.com/E-man85/projectII/blob/main/dataPreparation/dataPreparationProduct.ipynb) 

[dimCities](https://github.com/E-man85/projectII/blob/main/dataPreparation/dataPreparationCities.ipynb) 

[factSales](https://github.com/E-man85/projectII/blob/main/dataPreparation/dataPreparationSales.ipynb)

O objetivo foi tratar valores ausentes de cada variável ter o maximo de dados disponíveis.

### dimProduct

<details>
<summary><span >Ver dimProduct preparation</span></summary>
>

-***cluster_id***

A Coluna apresenta 50 valores NaN, e foi usado um modelo RandomForestClassifier, para gerar valores em falta. 

-***product_width, product_depth, product_length***

Os valores NaN destas variáveis foram tratados com modelos de RandomForestRegressor.

Foi criado um novo ficheiro dimProduct.csv, sem valores NaN e exportado para [dataStaging](https://github.com/E-man85/projectII/blob/main/dataStaging/dimProduct.csv).

</details>

### dimCities

<details>
<summary><span >Ver dimCities preparation</span></summary>
>

-***city_code***

A variável com os mones das cidades tem caracteres incorretos, possivelmente causados pelo codeficação da captação de dados.

Criamos um dicionário com os nomes em codificação correta e foi feta a substituição em toda a variável city_code.

-***latitude, longitude***

Para visualização e analise, foram acrescentadas duas novas variáveis, as coordenadas geográficas latitude e longitude.

Foi criado um novo ficheiro dimCities.csv e exportado para [dataStaging](https://github.com/E-man85/projectII/blob/main/dataStaging/dimCities.csv).
</details>

### factSales

<details>
<summary><span >Ver factSales preparation</span></summary>
>

-***sales***

Foram retirados todos os registos onde a variável sales apresenta NaN. Estes correspondem ao periodo mês 10 de 2019, que não têm importancia para o nosso estudo.

A consequência desta transformação for a não existência de NaN , nas variáveis revenue e stock.

-***price***

Esta variável contêm NaN, que foram substituidos com o valor médio de preços de cada loja.

-***promo_bin_1, promo_bin_2 , promo_discount_2 , promo_discount_type_2***

Todos os NaN destas variáveis foram substituidos usando expressões condicionais.

Foi criado um novo ficheiro factSales.csv e exportado para [dataStaging](https://github.com/E-man85/projectII/blob/main/dataStaging/factSales.csv).

</details>

### Entity Relationship (ER) Diagram

<img src="https://raw.githubusercontent.com/E-man85/projectII/main/images/diagram_turkiye_clothes_dim_fact.png" alt="Data Schema" width="900" height="400">

## Data Modeling 

Com os dados das 3 tabelas preparados, fizemos o agrupamento de dados numa só tabela 'flatTable'.
[dataModeling](https://github.com/E-man85/projectII/blob/main/dataModeling/dataModeling.ipynb).

Foi criado um novo ficheiro flatTable.csv e exportado para [dataStaging](https://github.com/E-man85/projectII/blob/main/dataStaging/flatTable.csv).

## Data Exploration

A exploração de dados pode ser consultada aqui.

## Data Preparation- Revenue Forecast

Nesta preparação o objetivo é disponibilizar os dados em granularidade semanal, e acrescentar variáveis exógenas. [dataModeling](https://github.com/E-man85/projectII/blob/main/dataPreparation/grainWeekMultipleVariables.ipynb)

### grainWeekMultipleVariables

<details>
<summary><span >Ver grainWeekMultipleVariables preparation</span></summary>
>

-***group by day***

A primeira transformação, depois de carregada a flatTabel foi agrupar os dados em grão dia.

-***missing data***

Verificamos que a frequência dos dados na variável "date", estava em falta nas lojas "S0072" e "S0136", foi feita a inserção das datas em falta , com o revenue ==0.

-***temperature***

Criamos uma nova variável com a temperatura média semanal e adicionamos aos nossos dados.

-***group by week***

Fizemos um novo agrupamento em granularidade semanal.

-***season***

Criamos uma nova varíavel season, relativo às estações do ano.

-***holiday***

Criamos nova variável holiday , considerando os principais feriados da turquia.

-***number month & number week***

Acrescentamos ainda as variáveis numero do mês e semana.

Com os dados na granularidade desejada e com variáveis exógenas, foi criado um novo ficheiro grainWeekMultipleVariables.csv e exportado para [dataStaging](https://github.com/E-man85/projectII/blob/main/dataStaging/grainWeekMultipleVariables.csv), desta forma teremos sempre os dados disponiveis para consulta, sempre que necessário.

</details>

## Modeling

### Simple forecasting methods

Foram criados vários modelos simples, que servem de referência para a seleção de modelos.

[simpleMethods](https://github.com/E-man85/projectII/blob/main/modeling/simpleForecastingMethods.ipynb)

<details>
<summary><span>Ver simpleMethods modeling</span></summary>
>

- Average method

- Naïve method

- Seasonal naïve method

- Random Walk with Drift (RWD)

- Average Models

Foram feitas duas exportação de resultados, as [previsões](https://github.com/E-man85/projectII/blob/main/dataStaging/resultSimpleMethods.csv) dos vários modelos em dados teste, e as várias métricas da função [accuracy](https://github.com/E-man85/projectII/blob/main/dataStaging/accuracySimpleMethods.csv).
</details>

### Exponential smoothing

Fizemos várias previsões com modelos de suavização exponencial. 

[etsModels](https://github.com/E-man85/projectII/blob/main/modeling/etsModels.ipynb)

<details>
<summary><span>Ver etsModels modeling</span></summary>
>

- Simple exponential smoothing

- Holt’s linear trend method

- Damped trend methods

- ETS (Error, Trend, Seasonality)
  
- STLF (Seasonal and Trend decomposition using Loess and Fourier)

Foram feitas duas exportação de resultados, as [previsões](https://github.com/E-man85/projectII/blob/main/dataStaging/resultEtsModels.csv) dos vários modelos em dados teste, e as várias métricas da função [accuracy](https://github.com/E-man85/projectII/blob/main/dataStaging/accuracyEtsModels.csv).
</details>

### Simple Linear Regression

Usamos a regressão linear para fazer previsões. 

[simpleLinearRegression](https://github.com/E-man85/projectII/blob/main/modeling/simpleLinearRegressionModels.ipynb)

<details>
<summary><span>Ver simpleLinearRegression modeling</span></summary>
>

- TSLM (Time Series Linear Model)

- LM (Linear Model)

Foram feitas duas exportação de resultados, as [previsões](https://github.com/E-man85/projectII/blob/main/dataStaging/resultSimpleLineaRegressionModels.csv) dos vários modelos em dados teste, e as várias métricas da função [accuracy](https://github.com/E-man85/projectII/blob/main/dataStaging/accuracySimpleLineaRegressionModels.csv).
</details>

### Auto Arima & Sarima

Usamos os modelos Auto Arima e Sarima para fazer previsões. 

[autoArimaSarima](https://github.com/E-man85/projectII/blob/main/modeling/autoArimaSarimaModels.ipynb)

<details>
<summary><span>Ver AutoArimaSarima modeling</span></summary>
>

- AutoArima 

- Sarima

Foram feitas duas exportação de resultados, as [previsões](https://github.com/E-man85/projectII/blob/main/dataStaging/resultAutoArimaSarimaModels.csv) dos vários modelos em dados teste, e as várias métricas da função [accuracy](https://github.com/E-man85/projectII/blob/main/dataStaging/accuracyArimaXregModels.csv).
</details>

### ARIMA (+ XREG)

Usamos os modelos Arima com variáveis exógenas para gerar previsões. 

[arimaXreg](https://github.com/E-man85/projectII/blob/main/modeling/arimaXreg.ipynb)

<details>
<summary><span>Ver ArimaXreg modeling</span></summary>
<>

- Arima (+ XREG)

Foram feitas duas exportação de resultados, as [previsões](https://github.com/E-man85/projectII/blob/main/dataStaging/resultArimaXregModels.csv) dos vários modelos em dados teste, e as várias métricas da função [accuracy](https://github.com/E-man85/projectII/blob/main/dataStaging/accuracyArimaXregModels.csv).
</details>


## Evaluation 

[evaluation](https://github.com/E-man85/projectII/blob/main/evaluation/finalPredictions.ipynb)


Com as métricas dos modelos para cada loja, foi criado um data frame para analise e seleção do melhor modelo.

Das várias méticas disponíveis a nossa escolha foi pela ***RMSE (Root Mean Squared Error)***.

**Formula**: 
RMSE = sqrt((1/n) * Σ(y_observed - y_predicted)^2)

-n é o número total de observações.  
-y_observed são os valores reais ou observados.  
-y_predicted são os valores previstos pelo modelo.  

RMSE mede a dispersão dos erros entre os valores previstos e os valores reais.

Tendo o foco na precisão da previsão o uso da media  RMSE penaliza erros maiores de forma mais significativa, é sensivel a outliers e a grandes desvios, mostrando a sua utilidade quando erros maiores são penalisados de forma desproporcional.

Depois de verificado o melhor RMSE para cada loja, podemos verificar o numero de lojas por modelo:

| Models | Number Stores|
|-|-|
| Average method| 10
| ETS | 1 |
| Holt Damped | 4
|Linear Model | 26
| Sasonal Naïve | 3
| STLF | 2
| TSLM | 16
| Arima ( +XREG) | 1

As previsõres foram exportadas para [finalPredictionsModels.csv](https://github.com/E-man85/projectII/blob/main/dataStaging/finalPredictionsModels.csv)

## Parte 2


**Problema:**

-O cliente não conhece os dados que estão nas bases de dados e o potêncial dos mesmos.

**Objetivo:**

-Criar uma ideia única e criativa que aproveite os dados disponíveis. 

### Query Library

- Informação Geográfica

- Análise Gráfica






















































