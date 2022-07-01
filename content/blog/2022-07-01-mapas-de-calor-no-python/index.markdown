---
title: Mapas de calor no Python
author: ''
date: '2022-07-01'
slug: []
excerpt: "Neste post, eu fiz mapas de calor nos dados da covid e da influenza no Python."
categories:
  - Python
tags: []
---


```r
import numpy as np
```


```r
import matplotlib.pyplot as plt
```


```r
covid = open("covid.fasta").read()
print(covid[98:])
```


```r
influenza = open("influenza.fasta").read()
print(influenza[104:])
```


```r
covid = covid.replace("\n", "")
pares1 = []
for i in range(len(covid)-1):
 pares1.append(covid[i] + covid[i+1])
 
print(pares1)covid = covid.replace("\n", "")
```


```r
influenza = influenza.replace("\n", "")
pares2 = []
for i in range(len(influenza)-1):
 pares2.append(influenza[i] + influenza[i+1])
 
print(pares2)
```


```r
## Contar frequencia
from collections import Counter
contagem = Counter(pares)
print(contagem)
```


```r
matriz1 = np.array([AA,AT,AC,AG,TA,TT,TC,TG,CA,CT,CC,CG,GA,GT,GC,GG])
print(matriz1)
```


```r
matriz2 = np.array([AAc,ATc,ACc,AGc,TAc,TTc,TCc,TGc,CAc,CTc,CCc,CGc,GAc,GTc,GCc,GGc])
print(matriz2)
```


```r
matriz3 = matriz1.reshape(4,4)
print(matriz3)
```


```r
matriz4 = matriz2.reshape(4,4)
print(matriz4)
```


```r
plt.imshow(matriz3, cmap = 'Blues', origin="lower")
plt.xlabel('Índice da linha'); plt.ylabel('Índice da coluna')
plt.xticks((0,1,2,3),['A','T','C','G'])
plt.yticks([3, 2, 1, 0],['G','C','T','A'])
plt.title("Influenza A")
_ = plt.colorbar()
```


```r
plt.imshow(matriz4, cmap = 'Blues', origin="lower")
plt.xlabel('Índice da linha'); plt.ylabel('Índice da coluna')
plt.xticks((0,1,2,3),['A','T','C','G'])
plt.yticks([3, 2, 1, 0],['G','C','T','A'])
plt.title("Covid-19")
_ = plt.colorbar()
```












