# Lab08 - Modelo Lógico e Análise de Dados em Grafos

# Equipe CSVac - JHGMA
* Maria Angélica Lobo Alves Paulino - 183465
* Gabriella Serrano Santana - 216698
* José Henrique Dioz Récio - 176622

## Modelo Lógico Combinado do Banco de Dados de Grafos
![Modelo Lógico de Grafos](images/modelo-logico-grafos.png)

## Perguntas de Pesquisa/Análise Combinadas e Respectivas Análises

### Pergunta/Análise 1
* Quais municípios possuem mais unidades de saúde com leitos destinados aos pacientes confirmados de COVID-19? Essa análise ajuda na determinação de quais municípios necessitam de mais insumos hospitalares com foco no COVID-19. 
  * A análise será feita verificando quais municípios possuem mais arestas conectadas à unidades de saúde. Modalidade de análise: centralidade. 

### Pergunta/Análise 2
* Quais unidades de saúde possuem mais leitos destinados aos pacientes confirmados de COVID-19? Essa análise ajuda na identificação de sobrecargas hospitalares e no planejamento de distribuição de leitos. 
  * A análise será feita verificando quais unidades de saúde possuem mais arestas conectadas aos leitos. Modalidade de análise: centralidade. 
  
### Pergunta/Análise 3
* Quais locais de vacinação disponibilizaram mais doses de vacina de COVID-19? Essa análise ajuda na determinação dos locais de vacinação que mais precisam de insumos hospitalares e de maiores equipes de vacinação. 
   * A análise será feita verificando quais locais de vacinação possuem mais arestas conectadas às vacinas. Modalidade de análise: centralidade.  

### Pergunta/Análise 4
* Se o local de vacinação que mais disponibilizou doses de vacina de COVID-19 não existisse, qual seria a eficiência da campanha de vacinação em comparação com a real?
  * A análise será feita contabilizando as arestas de conexão entre o local de vacinação que mais disponibilizou doses e vacinas, e calculando a porcentagem que esse valor presenta em relação ao total de arestas entre locais de vacinação e vacinas. Modalidade de análise: vulnerabilidade. 
 
### Pergunta/Análise 5
*  Se o local de vacinação que mais disponibilizou doses de vacina de COVID-19 não existisse, onde essas vacinas seriam oferecidas?
   * A análise será verificando qual é o segundo local de vacinação que mais disponibiliza dose de vacina de COVID-19. Isso também poderia ser determinado com base no local de vacinação mais próximo daquele que supostamente não existiria mais, porém a análise de localização é muito mais complexa e não condiz com a proposta do trabalho em questão. Modalidade de análise: predição de links.     

