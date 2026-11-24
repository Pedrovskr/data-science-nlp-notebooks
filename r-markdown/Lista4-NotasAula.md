# Notas de aulas - 18 e 20 de setembro

## Cap 3 e Cap 4 - [Livro Healy](https://kjhealy.github.io/socviz/)

Para poder executar tos exercícios do livro será necessário instalar 
a biblioteca com os dados utilizados pelo autor.

```
install.packages("socviz")
```
O **capítulo 2** do livro, introduziu os ambientes _RStudio_ e _RMarkdown_.
Para quem ainda tiver dúvidas, sugiro revisar o capítulo.

## Formato dos dados de _entrada_ e gráficos como _saída_

O **capítulo 3** introduz o `ggplot` com gráficos básicos.  Uma vez que vocês 
já sabem fazer gráficos básicos em `ggplot`, 
vamos focar a atenção em dois pontos:

### Formato _wide_ vs. formato _long_
Biblioteca `tidyr` funções: `pivot_longer()` e `pivot_wider()`.
Já fiz um comentário sobre isso anteriormente com o exercício de 
visualizar o Quarteto de Anscombe. Aqui vamos discutir a questão um pouco mais.

Vejam uma referência [aqui](https://tidyr.tidyverse.org/articles/pivot.html).
 

### Uso da função  

`ggsave()` e 
[seus parâmetros](https://ggplot2.tidyverse.org/reference/ggsave.html).

Exemplo _gapminder_: 
```{r}
library(tidyverse)
library(gapminder)

p<- ggplot(gapminder, aes(x = gdpPercap, y = lifeExp)) +
	geom_point(aes(color= log(pop))) +
	scale_x_log10()
p

# Exemplo em .png
ggsave("meu_grafico.png", p, height  =8, width = 10, units = "cm")

# Exemplo em .svg
ggsave("meu_grafico.svg", p, device = "svg", height  =8, width = 10, units = "cm")
```

Para entender o conceito de uma especificação SVG, sugiro fazerem o 
exercício proposto neste 
[link](https://observablehq.com/@aslamedeiros/parametros-de-figuras-em-um-svg-simples).


## Organizando o racicocínio para a produção de gráficos em `ggplot`.

[Capítulo 10 do livro _R for Data Science_](https://r4ds.hadley.nz/layers)

Exemplo enfatizando um subconjunto dos dados:

```
p <- ggplot(mpg, aes(x = displ, y = hwy)) + 
  geom_point() + 
  geom_point(
    data = mpg |> filter(class == "2seater"), 
    color = "red"
  ) +
  geom_point(
    data = mpg |> filter(class == "2seater"), 
    shape = "circle open", size = 3, color = "red"
  )
  
p   
```

## Ampliando as possibilidades

O **capítulo 4** amplia os recursos para usso do `ggplot`. Exemplo:

```{r}
library(tidyverse)
library(socviz)
glimpse(gss_sm)

p<- ggplot(gss_sm, aes(x = age, y = childs)) +
	geom_point(alpha = 0.2) +
	geom_smooth() +
	facet_grid(sex ~ race)
	
p
```

Títulos, legendas e comentários não são informações de menor importância. 
Servem para informar o contexto dos dados e guiar a leitura do gráfico.

Complete o exemplo abaixo (da seção 4.3 do Healy) no seu ambiente:

```
p <- ggplot(gapminder, aes(x= year, y= gdpPercap)) +
  geom_line(color= "gray70", aes(group = country)) +
  scale_y_log10(labels=scales::dollar)+
  facet_wrap(~continent, ncol = 5)+
  labs(x = "Ano",
       y = "Pib per Capta",
       title = "Pib per Capta nos 5 continentes")
p   
```

> **NOTA**: Vamos reproduzir os exemplos de Histogramas e curvas de densidade. 
As curvas de densidade são discutidas no **capítulo 3 do livro do Moore**.
Como comentei em aula, curvas de densidade, para serem estudadas com 
maior rigor, precisam de um ferramental de cálculo. Aqui discutiremos 
apenas a interpretação gráfica das curvas de densidade, do mesmo modo
que é feito no livro de referência.


## Lista de Exercícios

1. Fazer análise unidimensional das variáveis da base _gapminder_. 

1. Ao longo do Capítulo 3 do livro do Healy, o autor produz 
gráficos com os dados da base de dados _gapminder_. Escolha 
variáveis de sua preferência e produza um gráfico utilizando
a base _gapminder_. Lembre-se dos vídeos que vimos no início 
do curso, você pode reproduzir um daqueles gráficos!

1. Grave o gráfico produzido no exercício anterior, utilizando a 
função `ggsave()`. Grave em formato `.png`e `.svg`. Em que situações 
você escolheria utilizar o formato `.svg`?

1. Reproduza a ideia de enfatizar um subconjunto dos dados 
(como no exemplo), agora utilizando os dados _gapminder_ e produzindo
uma versão de sua escolha. 

1. Recursos de facetamento são muito utilizados em análise exploratória
de dados para observar e comparar aspectos entre categorias. O recurso
do `ggplot`que implementa o facetamento é o  `facet_wrap`. 
Reproduza os exemplos da seção 4.3 do Capítulo 4 do livro do Healy
e faça modificações explorando os conhecimentos já adquiridos 
anteriormente de `ggplot`. Use a base _gapminder_ também para este exercício.
