# Lista 3 - Parte I

## Comparando funcionalidades de Excel e R

### Data de entrega (segunda-feira) dia 18 de setembro de 2023
---
O objetivo desta lista é o de fazer o mesmo execício em dois ambientes
para a formação de opinião sobre os ambientes. Para deixar bem claro, 
usem como referência os exercícios resolvidos da _Lista 1 - Excel_ 
disponibilizado no _e-class_. A entrega é para ser feita em Excel (Exercício 1) 
e RMarkdown (demais exercícios).

**Exercícios - Parte I**

1. Refaça a _Lista 1 - Excel_ para a qual vocês já tem o gabarito parcial. 
1. Antes de iniciar os exercícios em R será necessário saber importar conjuntos de dados 
para o R. Para isso temos duas alternativas simples:
	- Exportar os dados do _Excel_ no formato `.csv` e utilizar a biblioteca `readr` 
	-- [capítulo 8](https://r4ds.hadley.nz/data-import) do livro _R for Data Science_; ou
	- Importar o arquivo com extensão `.xls` utilizando a biblioteca `readxl`
	-- [capítulo 21](https://r4ds.hadley.nz/spreadsheets) do livro _R for Data Science_. 
	> **_NOTA:_**: Apenas os dados da planilha _Excel_ são importados para o R. Todas as formatações, 
	figuras e fórmulas são ignoradas (o mesmo acontece ao exportar um `.csv`).
	a. Importe os dados `FORMATORADIO.xls`, `NASCIDOSFORA.xls`, `CUIDASAUDE.xls` 
	e `FACCUSTO.xls`, utilizados na _Lista 1 - Excel_ para reutilizar no R.

1. Dados `FORMATORADIO.xls`: Refaça o exercício 3 da _Lista 1 - Excel_ (_Você Ouve Rádio?_) no R. 
	Neste exercício é solicitado que se faça um gráfico de barras e um gráfico de setores.
	Disversas estratégias são possíveis para produzir as imagens, sugiro fortemente que 
	sigam investindo no `ggplot`. Exemplos de gráficos de setores 
	[pie-chart](https://r-charts.com/part-whole/pie-chart-ggplot2/)
	em
	[donut-chart](https://r-charts.com/part-whole/donut-chart-ggplot2/).
	> **_NOTA:_**: Observe o conceito de interpretar o gráfico setores como sendo uma 
	barra em coordenadas polares e experimente com coordenadas cartesianas convencionais!
	
	```
	ggplot(df, aes(x = "", y = value, fill = group)) +
		geom_col() +
		coord_polar(theta = "y")
	```
1. Dados `NASCIDOSFORA.xls`: Refaça os exercícios 4 e 5 da _Lista 1 - Excel_ no R.
	O objetivo é o de produzir histogramas, aqui está uma 
	[referência](https://ggplot2.tidyverse.org/reference/geom_histogram.html). 
	Explorem os parâmetros de de quantidade e largura dos intervalos.

1. Dados `CUIDASAUDE.xls`: Refaça o exercício 6 da _Lista 1 - Excel_ no R. 
	> **_NOTA:_**: O diagrama _Ramo-e-folhas (Stem and Leaf)_ 
	pode ser produzido de forma muito simples utilizando a função `stem()`do 
	R Base ([exemplo](https://www.geeksforgeeks.org/r-stem-and-leaf-plots/)). 

1. Dados `FACCUSTO.xls`: Refaça o exercício 7 da _Lista 1 - Excel_ sobre Séries temporais.
	Gráfico de linhas `geom_line()`. Aqui está uma boa
	[referência](https://r-charts.com/evolution/time-series-ggplot2/)
	para enriquecer o seu gráfico final.
	
1. **Considerações gerais**: Faça comentários sobre as suas impressões de usabilidade de 
	cada um dos dois ambientes utilizados: R e Excel.

