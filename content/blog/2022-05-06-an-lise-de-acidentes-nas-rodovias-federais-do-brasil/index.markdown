---
title: Analisando os acidentes nas Rodovias Federais 
author: ''
date: '2022-05-18'
slug: []
excerpt: "A atenção no trânsito é algo de extrema importância na vida de toda a população a fim de evitar que acidentes aconteçam. Infelizmente, as estatísticas ainda mostram um grande número de mortes no trânsito, ocasionadas por diversos fatores."
categories:
  - Python
  - Análise de dados
layout: single # single or single-sidebar  
---


---
A atenção no trânsito é algo de extrema importância na vida de toda a população a fim de evitar que acidentes aconteçam. Infelizmente, as estatísticas ainda mostram um grande número de mortes no trânsito, ocasionadas por diversos fatores.

Os dados utilizados para esta análise foram retirados do Ministério da Justiça e Segurança Pública - Polícia Rodoviária Federal: [Acidentes](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-acidentes). 

Para entender em qual contexto ocorrem mais acidentes, algumas perguntas serão respondidas ao longo desta análise:

* Quais são o estados/municípios com maior número de acidentes?

* Quais são os principais motivos dos acidentes nas rodovias?

* Quais os dias da semana com o maior número de acidentes?

* Quais são os tipos de veículos que mais se envolveram em acidentes?

* Qual o total de óbitos, feridos graves/leves e ilesos?

* Qual o número de acidentes por mês?



```r
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```


```r
detran = pd.read_csv(r'dados.csv', encoding='ISO-8859-1',sep=' ')
```


```r
df_detran = pd.DataFrame(detran)
df_detran
```


```r
sns.set_style("dark")
ax = sns.countplot(y = 'uf', data = df_detran, color = 'cornflowerblue', 
                   order= df_detran['uf'].value_counts().head(10).index)
ax.set(xlabel=None)
ax.set(xticklabels=[])
plt.title("Número de acidentes por Estados")
plt.xlabel("Acidentes")
plt.ylabel("Estados")
plt.show()
```

![](img/uf.png)


```r
# filtrando df para top 10 municipios
df_municipios = df_detran['municipio'].value_counts().head(10)
df_municipios
```


```r
#plot para os municipios
sns.set_style("dark")
ax = sns.countplot(y = 'municipio', data = df_detran, color = 'cornflowerblue', order= df_detran['municipio'].value_counts().head(10).index)
ax.set(xlabel=None)
ax.set(xticklabels=[])
plt.title("Número de casos por Munícipios")
plt.xlabel("Acidentes")
plt.ylabel("Municípios")
plt.show()
```

![](img/mun.png)



```r
#plot para os dias da semana
sns.set_style("dark")
ax = sns.countplot(y = 'dia_semana', data = df_detran, color = 'cornflowerblue', order= df_detran['dia_semana'].value_counts().head(7).index)
ax.set(xlabel=None)
ax.set(xticklabels=[])
plt.title("Número de acidentes em cada dia")
plt.xlabel("Acidentes")
plt.ylabel("Dias da Semana")
plt.show()
```

![](img/dia.png)


```r
# filtrando df para top 15 causas
df_causa = df_detran['causa_acidente'].value_counts().head(15)
df_causa
```



```r
#plot para os tipos de acidentes
#plot para as causas
sns.set_style("dark")
ax = sns.countplot(y = 'tipo_acidente', data = df_detran, color = 'cornflowerblue', order= df_detran['tipo_acidente'].value_counts().head(7).index)
ax.set(xlabel=None)
ax.set(xticklabels=[])
plt.title("Número de acidentes por causa")
plt.xlabel("Acidentes")
plt.ylabel("Causas")
plt.show()
```

![](img/causa.png)





