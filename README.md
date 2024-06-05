# Análise de Séries Temporais dos Principais Índices de Mercado

## Introdução

Este projeto visa a análise de séries temporais de preços de ações de quatro importantes índices de mercado: FTSE (Financial Times Stock Exchange), NIKKEI (Japão), S&P 500 (EUA) e DAX (Alemanha). Utilizando dados históricos abrangendo o período de 1994 a 2018, buscamos entender o comportamento e as tendências dos mercados financeiros ao longo do tempo.

## Dados Utilizados

Os dados foram obtidos do Kaggle e incluem:

- **Período**: 1994 a 2018
- **Índices**:
  - **S&P 500 (spx)**: Índice das 500 maiores empresas dos EUA.
  - **DAX (dax)**: Principal índice de ações da Alemanha.
  - **FTSE (ftse)**: Índice das 100 maiores empresas listadas na Bolsa de Valores de Londres.
  - **NIKKEI (nikkei)**: Principal índice de ações do Japão.

### Estrutura do Conjunto de Dados

O conjunto de dados contém as seguintes colunas:

- **date**: Data dos registros.
- **spx**: Preços diários do índice S&P 500.
- **dax**: Preços diários do índice DAX.
- **ftse**: Preços diários do índice FTSE.
- **nikkei**: Preços diários do índice NIKKEI.

## Objetivos do Projeto

1. Importar e visualizar os dados.
2. Analisar a estrutura e tipos de dados.
3. Realizar análise exploratória para identificar padrões e tendências.
4. Converter a coluna de datas para o formato apropriado.
5. Criar visualizações para facilitar a interpretação dos dados.

## Importação e Visualização dos Dados

### Passos para Importação

Utilizamos a biblioteca `pandas` para ler e manipular os dados:

```python
import pandas as pd

# Caminho para os dados
url = '/content/drive/MyDrive/Séries Temporais/Index2018.csv'

# Leitura dos dados
df = pd.read_csv(url)

# Visualizando as primeiras linhas do DataFrame
df.head()
```

### Estrutura e Tipos de Dados

Verificamos a presença de dados ausentes e tipos de dados das colunas:

```python
print('Dados ausentes:', df.isnull().sum().sum())
print('Tipo de dados da coluna date:', df['date'].dtypes)
print('Tipos de dados das colunas de índices:\n', df[['spx','dax','ftse','nikkei']].dtypes)
```

### Conversão da Coluna de Data

A coluna `date` foi convertida para o formato `datetime` para facilitar a análise:

```python
df['date'] = pd.to_datetime(df['date'], format='%d/%m/%Y')
print('Tipo de dados após conversão:', df['date'].dtypes)
```

## Análise Exploratória de Dados

Realizamos uma análise estatística e visual das variáveis, utilizando histogramas e boxplots:

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Estatísticas descritivas
print(df.describe())

# Plotando histogramas
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
sns.histplot(df['spx'], bins=30, kde=True, ax=axes[0,0]).set_title('Distribuição do S&P 500')
sns.histplot(df['dax'], bins=30, kde=True, ax=axes[0,1]).set_title('Distribuição do DAX')
sns.histplot(df['ftse'], bins=30, kde=True, ax=axes[1,0]).set_title('Distribuição do FTSE')
sns.histplot(df['nikkei'], bins=30, kde=True, ax=axes[1,1]).set_title('Distribuição do NIKKEI')
plt.tight_layout()
plt.show()

# Plotando boxplots
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
sns.boxplot(data=df, y='spx', ax=axes[0,0]).set_title('Boxplot do S&P 500')
sns.boxplot(data=df, y='dax', ax=axes[0,1]).set_title('Boxplot do DAX')
sns.boxplot(data=df, y='ftse', ax=axes[1,0]).set_title('Boxplot do FTSE')
sns.boxplot(data=df, y='nikkei', ax=axes[1,1]).set_title('Boxplot do NIKKEI')
plt.tight_layout()
plt.show()
```

## Análise de Séries Temporais

Plotamos gráficos de linha para visualizar as tendências dos índices ao longo do tempo:

```python
plt.figure(figsize=(14, 7))
plt.plot(df['date'], df['spx'], label='S&P 500')
plt.plot(df['date'], df['dax'], label='DAX')
plt.plot(df['date'], df['ftse'], label='FTSE')
plt.plot(df['date'], df['nikkei'], label='NIKKEI')
plt.xlabel('Data')
plt.ylabel('Preço do Índice')
plt.title('Tendência dos Índices')
plt.legend()
plt.show()
```

## Conclusão

O conjunto de dados oferece uma rica oportunidade para análise de séries temporais, possibilitando uma compreensão aprofundada das tendências e comportamentos dos mercados financeiros globais. Através da análise exploratória e visualizações, identificamos padrões importantes que podem auxiliar na tomada de decisões informadas no mercado financeiro.

## Requisitos

- Python 
- pandas
- matplotlib
- seaborn

## Como Usar

1. Clone este repositório.
2. Instale as dependências listadas em `requirements.txt`.
3. Execute o script Jupyter Notebook para visualizar e analisar os dados.

## Contato

Para mais informações, entre em contato através do paparellilucas1@gmail.com 

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------


# Time Series Analysis of Major Market Indices

## Introduction

This project aims to analyze the time series of stock prices of four major market indices: FTSE (Financial Times Stock Exchange), NIKKEI (Japan), S&P 500 (USA), and DAX (Germany). Using historical data covering the period from 1994 to 2018, we seek to understand the behavior and trends of financial markets over time.

## Data Used

The data was obtained from Kaggle and includes:

- **Period**: 1994 to 2018
- **Indices**:
  - **S&P 500 (spx)**: Index of the 500 largest companies in the USA.
  - **DAX (dax)**: Main stock index of Germany.
  - **FTSE (ftse)**: Index of the 100 largest companies listed on the London Stock Exchange.
  - **NIKKEI (nikkei)**: Main stock index of Japan.

### Dataset Structure

The dataset contains the following columns:

- **date**: Date of the records.
- **spx**: Daily prices of the S&P 500 index.
- **dax**: Daily prices of the DAX index.
- **ftse**: Daily prices of the FTSE index.
- **nikkei**: Daily prices of the NIKKEI index.

## Project Objectives

1. Import and visualize the data.
2. Analyze the structure and data types.
3. Perform exploratory analysis to identify patterns and trends.
4. Convert the date column to the appropriate format.
5. Create visualizations to facilitate data interpretation.

## Data Import and Visualization

### Import Steps

We use the `pandas` library to read and manipulate the data:

```python
import pandas as pd

# Path to the data
url = '/content/drive/MyDrive/Séries Temporais/Index2018.csv'

# Reading the data
df = pd.read_csv(url)

# Viewing the first rows of the DataFrame
df.head()
```

### Structure and Data Types

We check for missing data and data types of the columns:

```python
print('Missing data:', df.isnull().sum().sum())
print('Data type of the date column:', df['date'].dtypes)
print('Data types of the index columns:\n', df[['spx','dax','ftse','nikkei']].dtypes)
```

### Date Column Conversion

The `date` column is converted to the `datetime` format to facilitate analysis:

```python
df['date'] = pd.to_datetime(df['date'], format='%d/%m/%Y')
print('Data type after conversion:', df['date'].dtypes)
```

## Exploratory Data Analysis

We perform statistical and visual analysis of the variables using histograms and boxplots:

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Descriptive statistics
print(df.describe())

# Plotting histograms
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
sns.histplot(df['spx'], bins=30, kde=True, ax=axes[0,0]).set_title('Distribution of S&P 500')
sns.histplot(df['dax'], bins=30, kde=True, ax=axes[0,1]).set_title('Distribution of DAX')
sns.histplot(df['ftse'], bins=30, kde=True, ax=axes[1,0]).set_title('Distribution of FTSE')
sns.histplot(df['nikkei'], bins=30, kde=True, ax=axes[1,1]).set_title('Distribution of NIKKEI')
plt.tight_layout()
plt.show()

# Plotting boxplots
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
sns.boxplot(data=df, y='spx', ax=axes[0,0]).set_title('Boxplot of S&P 500')
sns.boxplot(data=df, y='dax', ax=axes[0,1]).set_title('Boxplot of DAX')
sns.boxplot(data=df, y='ftse', ax=axes[1,0]).set_title('Boxplot of FTSE')
sns.boxplot(data=df, y='nikkei', ax=axes[1,1]).set_title('Boxplot of NIKKEI')
plt.tight_layout()
plt.show()
```

## Time Series Analysis

We plot line charts to visualize the trends of the indices over time:

```python
plt.figure(figsize=(14, 7))
plt.plot(df['date'], df['spx'], label='S&P 500')
plt.plot(df['date'], df['dax'], label='DAX')
plt.plot(df['date'], df['ftse'], label='FTSE')
plt.plot(df['date'], df['nikkei'], label='NIKKEI')
plt.xlabel('Date')
plt.ylabel('Index Price')
plt.title('Trends of the Indices')
plt.legend()
plt.show()
```

## Conclusion

The dataset provides a rich opportunity for time series analysis, enabling a deep understanding of the trends and behaviors of global financial markets. Through exploratory analysis and visualizations, we identified important patterns that can aid in making informed decisions in the financial market.

## Requirements

- Python 
- pandas
- matplotlib
- seaborn

## How to Use

1. Clone this repository.
2. Install the dependencies listed in `requirements.txt`.
3. Run the Jupyter Notebook script to view and analyze the data.

## Contact

For more information, contact us at paparellilucas1@gmail.com
