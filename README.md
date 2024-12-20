#- README: Análise de RFM para E-commerce


Este README detalha o processo de desenvolvimento para calcular os indicadores RFM (Recência, Frequência e Ticket Médio) a partir de um conjunto de dados de um e-commerce.

*Objetivo

  - Gerar um arquivo CSV contendo a identificação dos clientes e as métricas RFM:
  - Recency (R): Tempo em dias desde a última compra do cliente.
  - Frequency (F): Quantidade de compras realizadas pelo cliente.
  - Monetary (M): Ticket médio, ou seja, a média do valor total gasto por pedido para cada cliente.

* Descrição dos Dados

A tabela fornecida contém informações de compras realizadas em 37 países. As colunas principais incluem:

  - CustomerID: Código de identificação do cliente.
  - Description: Descrição do produto.
  - InvoiceNo: Código da fatura.
  - StockCode: Código de estoque do produto.
  - Quantity: Quantidade do produto.
  - InvoiceDate: Data do faturamento.
  - UnitPrice: Preço unitário do produto.
  - Country: País onde a compra foi realizada.

***Etapas de Desenvolvimento***

  Etapa 01:Leitura e Inspeção dos Dados
  
  - Importar o dataset para o ambiente de desenvolvimento (ex.: Google Colab).
  - Utilizar describe() para verificar a distribuição dos dados.
  - Analisar os tipos de dados presentes no dataset.

  Etapa 02: Tratamento de Valores Faltantes

  - Verificar valores nulos nas colunas com isna().sum().
  - Remover observações com valores nulos utilizando dropna().

  Etapa 03: Filtragem de Valores Inválidos

  - Verificar se há preços unitários (“UnitPrice”) iguais ou inferiores a 0. Se existirem, removê-los.
  - Verificar se há quantidades (“Quantity”) iguais ou inferiores a 0. Se existirem, removê-las.

  Etapa 04: Remoção de Linhas Duplicadas

  - Verificar duplicatas com duplicated().
  - Remover linhas duplicadas utilizando drop_duplicates().

  Etapa 05: Correção dos Tipos de Dados

  - Ajustar os tipos de dados das colunas conforme o esperado:
  - InvoiceNo, StockCode, Description, Country: str
  - Quantity: int
  - InvoiceDate: datetime
  - UnitPrice: float
  - CustomerID: int

  Etapa 06: Tratamento de Outliers

  - Visualizar outliers nas colunas de quantidade e preço unitário.
  - Remover valores extremos:
  - Quantidade superior a 10.000.
  - Preço unitário superior a 5.000.

  Etapa 07: Criação de Coluna Adicional

  - Criar uma nova coluna chamada TotalPrice multiplicando Quantity por UnitPrice.

  Etapa 08: Cálculo da Data da Última Compra

  - Utilizar a função max() para calcular a data mais recente no dataset.
  - Esta data será usada como referência para o cálculo da recência.

  Etapa 09: Visualização de Gráficos

  - Top 10 países com maior valor em vendas.
  - Top 10 produtos mais vendidos.
  - Valor total de vendas por mês.
  - Valor total de vendas por mês e por país (apenas para os 10 principais países).

  Etapa 10: Cálculo do RFM

  Agrupar os dados por cliente e por fatura (InvoiceNo):

  - Obter a data da fatura e o valor total da compra.

  Agrupar os dados novamente apenas por cliente:
  
  - Recência (R): Diferença, em dias, entre a última compra do cliente e a data mais recente do dataset.
  - Frequência (F): Quantidade de compras feitas pelo cliente.
  - Monetário (M): Média do valor total gasto por pedido.

***Resultado***

  O código deve gerar um arquivo CSV contendo as seguintes colunas:

  CustomerID: Identificação do cliente.
  R (Recency): Recência.
  F (Frequency): Frequência.
  M (Monetary): Ticket médio.

***Requisitos***

  - Linguagem: Python.
  - Bibliotecas recomendadas: pandas, numpy, matplotlib, seaborn.
  - Ambiente sugerido: Google Colab.
  - Siga as etapas descritas para garantir a qualidade e consistência dos dados antes do cálculo final.

