---
title: Usando Web Scraping para extrair tabelas
author: ''
date: '2022-07-17'
slug: []
excerpt: "Neste post eu apresento uma maneira de extrair tabelas de site no Python"
categories:
  - Python
  - Web Scraping
layout: single 
---


```r
import requests
from bs4 import BeautifulSoup
import pandas as pd

url = 'https://pt.wikipedia.org/wiki/Lista_de_munic%C3%ADpios_do_Esp%C3%ADrito_Santo_por_popula%C3%A7%C3%A3o'

site = requests.get(url)

print(site)


soup = BeautifulSoup(site.text, 'html.parser')

print(soup.prettify())


tabela = soup.find_all('table', {'class': 'wikitable'})

print(tabela)


tabela = tabela[0]

titulos = [i.text for i in tabela.find_all('th')]

print(titulos)

titulos[2] = 'População'

# Criando o dataframe
df = pd.DataFrame(columns = titulos)

df


print(tabela.find_all('tr'))

print([type(item) for item in list(tabela.children)])

print([item for item in list(tabela.children)])

print(tabela.find_all('tr')[1].find_all('td'))

print([i.text for i in tabela.find_all('tr')[1].find_all('td')])



for j in tabela.find_all('tr')[1:]:
    row_data = j.find_all('td')
    row = [i.text for i in row_data]
    length = len(df)
    df.loc[length] = row



df = df.replace({r'[\n\[2\]\.\s]':''}, regex=True)

df.head(20)


df.to_csv('dados.csv', index = False)import requests
from bs4 import BeautifulSoup
import pandas as pd

url = 'https://pt.wikipedia.org/wiki/Lista_de_munic%C3%ADpios_do_Esp%C3%ADrito_Santo_por_popula%C3%A7%C3%A3o'

site = requests.get(url)

print(site)


soup = BeautifulSoup(site.text, 'html.parser')

print(soup.prettify())


tabela = soup.find_all('table', {'class': 'wikitable'})

print(tabela)


tabela = tabela[0]

titulos = [i.text for i in tabela.find_all('th')]

print(titulos)

titulos[2] = 'População'

# Criando o dataframe
df = pd.DataFrame(columns = titulos)

df


print(tabela.find_all('tr'))

print([type(item) for item in list(tabela.children)])

print([item for item in list(tabela.children)])

print(tabela.find_all('tr')[1].find_all('td'))

print([i.text for i in tabela.find_all('tr')[1].find_all('td')])



for j in tabela.find_all('tr')[1:]:
    row_data = j.find_all('td')
    row = [i.text for i in row_data]
    length = len(df)
    df.loc[length] = row



df = df.replace({r'[\n\[2\]\.\s]':''}, regex=True)

df.head(20)


df.to_csv('dados.csv', index = False)
```

