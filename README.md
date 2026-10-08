# Tratamento e Limpeza de Dados com Python, Panda e Numpy
Este repositório contem um arquivo com código de limpeza de dados usando o python, pandas e numpy utilizando o google colab e outro arquivo com os dados.

## Visão Geral 
### Base de dados pego no Kaggle
O conjunto de dados Dirty Cafe Sales contém 10.000 linhas de dados sintéticos representando transações de vendas em um café. Este conjunto de dados é intencionalmente "sujo", com valores ausentes, dados inconsistentes e erros introduzidos para fornecer um cenário realista para limpeza de dados e análise exploratória de dados (EDA). Ele pode ser usado para praticar técnicas de limpeza, manipulação de dados e engenharia de recursos.
Limpesa e tratamento de dados, baixado do Kagge Vendas em Cafés -(Cafe Sales - Dirty Data for Cleaning Training), (https://www.kaggle.com/datasets/ahmedmohamed2003/cafe-sales-dirty-data-for-cleaning-training?resource=download)

## Informações da Base de Dados 
- Nome do arquivo: dirty_cafe_sales.csv
- Número de linhas: 10.000
- Número de colunas: 8

## Descrição das colunas  
|Nome da coluna	   |Descrição	                                                                                          |Valores de exemplo|
|------------------|-----------------------------------------------------------------------------------------------------|-----------------|
|Transaction ID|	 |Um identificador único para cada transação. Sempre presente e único.	                               |TXN_1234567|
|Item	             |Nome do item comprado. Pode conter valores ausentes ou inválidos (ex.: "ERRO").	                    |Coffee,Sandwich
|Quantity	         |Quantidade do item comprado. Pode conter valores ausentes ou inválidos.	                            |1, 3,UNKNOWN
|Price Per Unit	   |Preço unitário do produto. Pode conter valores ausentes ou inválidos.	                              |2.00,4.00
|Total Spent	     |O valor total gasto na transação. Calculado como Quantity * Price Per Unit.	                        |8.00,12.00
|Payment Method	   |Método de pagamento utilizado. Pode conter valores ausentes ou inválidos (ex.: None"DESCONHECIDO").	|Cash,Credit Card
|Location	         |Local onde a transação ocorreu. Pode conter valores ausentes ou inválidos.	                          |In-store,Takeaway
|Transaction Date	 |Data da transação. Pode conter valores ausentes ou incorretos.	                                      |2023-01-01



## Limpeza do dataset
### O que foi feito 
- 1- Foi feito a junção dos nomes das colunas devido esta separados (ex: Total Spent, ficou Total_Spend)
- 2- Verificado os tipos, todos estavam como "object", Mudado os tipos das colunas
  - Item par categoria
  - Quantity para inteiro
  - Price_Per_Unit para Float 
  - Total_Spent para Float
  - Payment_Method para categoria
  - Location para categoria
  - Transation_Date para data
- 3- Desmembrado a data de transação em Dia, Dia da semana, Mês e Ano foi criado mais 4 colunas
  - Dia ficou como tipo inteiro
  - Dia da semana como categoria
  - Mês como inteiro
  - Ano como inteiro   
- 4- Verificado a porcentagem de dados incorretos em cada coluna(Colunas Location tinha 32% de dados incorretos e Payment_Method tinha 25% ) isso representa como Location 32 % dos datos totais total de 3961 linhas.
- 5- Vericado que no dataset tinha 2 tipos de dados incorretos (UNKNOW e ERROR)
- 6- Feito função para substituir os valores incorretos por (NaN ) foi feito uma lista com os valores e feito a função utilizando o numpy. 
- 7- Na coluna Location os valores NaN foi substituído por "Not Specified" devido os dados representar mais 30 por cento dos dados, se removesse as linhas seria um perda significativo nos dados devido a quantidade, as analise seria muito menos precisa.
- 8- Na coluna Payment_Method tambem foi substituído os valores NaN por "Not Specified" devido os dados representar mais 30 por cento dos dados
- 9- Na coluna Quantity os valores NaN foi preenchido com o valor mínimo de vendo que e 1
- 10- Na coluna Price_Per_Unit foi preenchido com mediana devido ser mais seguro
- 11- E foi recalculado os valores da coluna Total_Spent
- 12- Na ultima etapa foi removido as linhas com valores NaN de 10000 linhas ficou 8613,  com esta perda não representa muito perda nas analises.


