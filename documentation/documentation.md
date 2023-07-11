# Projeto II

## Parte 1

### Desafios

**Problema:**

-O cliente precisa de atualizar o armazenamento de roupa em cada loja para Outubro de 2019.

**Objetivo:**

-Prever com precisão as vendas semanais considerando sazonalidade,tendência e variáveis explicativas. Para complementar, deverá ser feito uma análise dos dados que serão utilizados no modelo.


## Parte 2

### Desafios

**Problema:**

-O cliente não conhece os dados que estão nas bases de dados e o potêncial dos mesmos.

**Objetivo:**

-Devem criar uma ideia única e criativa que aproveite os dados disponíveis. Isso pode envolver o desenvolvimento de novas funcionalidades, identificação de tendências ou proposta de soluções orientadas por dados para abordar desafios ou aproveitar oportunidades específicas.

## Dados 

Os dados recolhidos para a elaboração deste trabalho são três ficheiros em formato .csv:

- cities.csv (2 KB)
- product.csv (47 KB)
- sales.csv (648.3 MB)

Estes dados foram carregados para este repositório podendo ser consultados [aqui](https://github.com/E-man85/projectII/tree/e1519f1e689a5757204705d12d98928aa223f916/data).

**Nota:** 
O ficheiro ***sales.csv***, devido à sua dimensão, foi disponibilizado no git usando a [extensão do git 'LFS'](https://git-lfs.com/).

1. git lfs install (instalar extensão)
2. git lfs track "*.psd" ( selecionar ficheiro onde usar o GIT LFS)
3. git add .gitattributes ( verificar o ficheiro rastreado )
4. git add file.psd (fazer o commit e push normalmente)
    git commit -m "Add design file"
    git push origin main

## Data Understanding

A exploração dos 3 ficheiros de dados está disponível no [dataUnderstanding]([aqui)](https://github.com/E-man85/projectII/blob/main/dataExploration/productExploration.ipynb).

### product.csv

<details>
<summary><span style="color: red;">Ver understanding product.csv</span></summary>



O ficheiro tem 10 colunas com 699 registos

-***product_id***

Coluna com valores do tipo 'object', de 4 catacteres alfanuméricos e valores exclusivos.

-***product_length, product_depth,	product_width***

Colunas que representam as dimensões dos produtos, do tipo float64.
Existem produtos sem esta informação.

-***cluster_id***

Do tipo 'object',com 10 valores distintos de clusters_id, sendo que alguns registos não têm esta informação preenchida.

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
<summary><span style="color: red;">Ver understanding cities.csv</span></summary>

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

Coluna de um valor exclusivo, do tipo 'object' que refere o pais .

-***city_code***

Coluna com dados do tipo 'object' que refere o nome da cidade.

A configuração usada neste ambiente não está de acordo com a codificação dos caracteres do ficheiro
Por essa razão  dados alguns nomes das cidades têm problemas de visualização:

ex: 'Sanl?urfa', 'Adapazar?'

</details>

</details>


### sales.csv

<details>
<summary><span style="color: red;">Ver understanding sales.csv</span></summary>

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
Existem 302296  registos com valores Nan, que analisados representam o mês 10 do ano 2019.

-***revenue***

Coluna do tipo 'float64', que refere ao revenue dos produtos vendidos (sales*price)-desconto ou impostos

-***stock***

Coluna do tipo 'float64', que refere a quantidade existente do produto .

-***price***

Coluna do tipo 'float64', que refere o preço unitário do produto.
O preço dos produtos pode variar para diferentes lojas.


-***promo_type_1***

Coluna  tipo 'object', com valores alfanuméricos e com 17 valores distintos.
Refere-se ao tipo1 de promoção .

-***promo_type_2***

Coluna  tipo 'object', com valores alfanuméricos e com 4 valores distintos.
Refere-se ao tipo2 de promoção .


-***promo_bin_1***

Coluna do tipo 'object', e valores e 5 valores distintos, classificando a intensidade da promoção.['verylow', 'moderate', 'low', 'high', 'veryhigh']

Esta coluna tem 7653515 nan e 1232543 com a classificação da intensidade.

-***promo_bin_2***
Coluna do tipo 'object', e valores e 3 valores distintos, classificando a intensidade da promoção.['verylow', 'high', 'veryhigh']

Esta coluna tem 8873337 nan e 12721 com a classificação da intensidade.

-***promo_discont_2***

Coluna do tipo 'float64', de 6 valores distintos[ 20., 16., 35., 50., 40., 33.].

Esta coluna tem 8873337 nan e 12721 com a classificação da intensidade.

-***promo_discont_type_2***

Coluna do tipo 'object', de  valores distintos ['PR04', 'PR02', 'PR01', 'PR03']

Esta coluna tem 8873337 nan e 12721 com a classificação da intensidade.

</details>


### Diagrama das tabelas

![diagram_turkiye_stores](https://raw.githubusercontent.com/E-man85/projectII/e1519f1e689a5757204705d12d98928aa223f916/images/diagram_turkiye_stores.png?token=GHSAT0AAAAAACBQIYY4MURVKFOLEJKPX4EIZEQOE2Q )

As três tabelas foram agrupadas numa tabela 'flatTable'.

## Data Exploration

