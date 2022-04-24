---
title: Criando um blog com blogdown (em construção)
author: 
date: '2022-04-19'
slug: []
excerpt: "Este primeiro post é um tutorial de como se faz um blog utilizando o pacote blogdown."
categories:
  - R
  - Tutorial
layout: single # single or single-sidebar
---

Existem algumas formas de criar sites utilizando o R, neste primeiro post eu criei um tutorial construindo um blog utilizando o pacote `blogdown`. 



```r
install.packages("blogdown")
```


```r
blogdown::install_hugo()
```


```r
blogdown::new_site("pasta", theme = "usuario/repositorio")
```

* `Temas:` [HUGO](https://themes.gohugo.io/).


```r
blogdown::serve_site()
```

Continua..
