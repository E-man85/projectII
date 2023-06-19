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
O ficheiro ***sales.csv***, devido à sua dimensão, foi disponibilizado no git usando a [extensão do git 'lfs'](https://git-lfs.com/).

1. git lfs install (instalar extensão)
2. git lfs track "*.psd" ( selecionar ficheiro onde usar o GIT LFS)
3. git add .gitattributes ( verificar o ficheiro rastreado )
4. git add file.psd (fazer o commit e push normalmente)
    git commit -m "Add design file"
    git push origin main

## Exploração de dados

A exploração dos 3 ficheiros de dados está disponível no [dataExploration] (falta o link).

### product.csv

<details>
<summary>Ver resumo exploraçáo product.csv</summary>

O ficheiro tem 10 colunas com 699 registos

-***product_id***

Do tipo 'object', com 4 catacteres alfanuméricos, de valores exclusivos.

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





### Diagrama das tabelas

![diagram_turkiye_stores](https://raw.githubusercontent.com/E-man85/projectII/e1519f1e689a5757204705d12d98928aa223f916/images/diagram_turkiye_stores.png?token=GHSAT0AAAAAACBQIYY4MURVKFOLEJKPX4EIZEQOE2Q )
