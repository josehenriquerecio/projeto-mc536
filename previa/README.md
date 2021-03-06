# Projeto CSVac

# Equipe CSVac - JHGMA
* José Henrique Dioz Récio - RA: 176622
* Maria Angélica Lobo Alves Paulino - RA: 183465
* Gabriella Serrano Santana - RA: 216698

## Resumo do Projeto
Diante a pandemia de COVID-19 declarada em março de 2020 e que se estende até os dias atuais, surgiu a necessidade do gerenciamento dos dados de ocupação de leitos, crescimento da doença e vacinação pelo Ministério da Saúde e disponibilizados no DATASUS com a finalidade de compreender melhor a situação do país e otimizar a gestão de recursos.

Nosso projeto consiste em analisar majoritariamente os seguintes bancos de dados:

* Campanha Nacional de Vacinação contra Covid-19
* Registro de Ocupação Hospitalar COVID-19
* Base de dados do CNES
* Sinopse do Censo Demográfico 2010 Sergipe

Nossa proposta é relacionar a vacinação contra a COVID-19, a ocupação de leitos, escolaridade, ruralidade, entre outros aspectos que consideramos relevantes e serão detalhados ao longo do projeto. Consideramos essa análise muito importante para combater a desinformação e promover a ciência e seus impactos no bem estar da população. Ademais, fizemos um recorte dessa análise para o estado de Sergipe.

## Slides da Apresentação
[Link dos slides](https://github.com/josehenriquerecio/projeto-mc536/blob/main/previa/slides/CSVac_final.pdf)

## Modelo Conceitual Preliminar
![ER CSVac](images/conceitual.png)

## Modelos Lógicos Preliminares
### Relacional

Vacinação(_cidade_, _data_, qtd_0a17anos,  qtd_18a35anos,  qtd_36a59anos, qtd_60+, qtd_mulheres, qtd_homens)

    cidade chave estrangeira -> Município(nome)
  
Local_de_Vacinação(_nome_, cnes, cidade, qtd_vacina)

Leitos(_cnes_, _data_, ocupação_leitos_clinico, ocupação_leitos_uti, saida_obitos, saida_altas)
  
    cnes chave estrangeira -> Unidade_de_saúde(cnes)
  
Unidade_de_saúde(_cnes_, nome_fantasia, endereço, cidade)
  
    cidade chave estrangeira -> Município(nome)
  
Município(_nome_, idh, escolaridade, ruralidade, pop_0a17anos,  pop_18a35anos,  pop_36a59anos, pop_60+)
  
### Grafos de propriedades
![Modelo Lógico de Grafos](images/grafo_propriedades.PNG)

## Dataset Preliminar a ser Publicado
> Elencar os arquivos/bases preliminares dos datasets serão publicados publicados.

título do arquivo/base | link | breve descrição
----- | ----- | -----
`<título da base>` | `<link para a página da base>` | `<breve descrição da base>`

## Bases de Dados

Título da base | Link | Descrição
----- | ----- | -----
Campanha Nacional de Vacinação contra Covid-19 | [Link da Campanha Nacional de Vacinação contra Covid-19](https://opendatasus.saude.gov.br/dataset/covid-19-vacinacao) | `<breve descrição do arquivo/base>`
Registro de Ocupação Hospitalar COVID-19 | [Link do Registro de Ocupação Hospitalar COVID-19](https://opendatasus.saude.gov.br/dataset/registro-de-ocupacao-hospitalar) | `<breve descrição do arquivo/base>`
Base de dados do CNES | [Link da Base de dados do CNES](https://opendatasus.saude.gov.br/dataset/cadastro-nacional-de-estabelecimentos-de-saude-cnes/resource/015d095b-01fe-45ec-9c21-6b6a7476a04f) | `<breve descrição do arquivo/base>`
Sinopse do Censo Demográfico 2010 Sergipe | [Link da Sinopse do Censo Demográfico 2010 Sergipe](https://censo2010.ibge.gov.br/sinopse/index.php?dados=26&uf=28)  | `<breve descrição do arquivo/base>`


## Operações realizadas para a construção do dataset

> Coloque um link para o arquivo do notebook, programas ou workflows que executam as operações de construção do dataset:
* extração de dados de fontes não estruturadas como, por exemplo, páginas Web
* agregação de dados fragmentados obtidos a partir de API
* integração de dados de múltiplas fontes
* tratamento de dados
* transformação de dados para facilitar análise e pesquisa

> Se for notebook, ele estará dentro da pasta `notebook`. Se por alguma razão o código não for executável no Jupyter, coloque na pasta `src`. Se as operações envolverem queries executadas atraves de uma interface de um SGBD não executável no Jupyter, como o Cypher, apresente na forma de markdown.

## Perguntas de Pesquisa/Análise Combinadas e Respectivas Análises

> Liste aqui as perguntas de pesquisa/análise e respectivas análises.
> Nem todas as perguntas precisam de queries que as implementam.
> É possível haver perguntas em que a solução é apenas descrita para
> demonstrar o potencial da base.
>
### Pergunta/Análise 1
> * Municípios com boa escolaridade possuem maiores índices de vacinação? Tendo isso em vista, pode-se afirmar que uma boa educação ajuda na conscientização da necessidade de tomar vacinas? 
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.

### Pergunta/Análise 2
> * O índice de ruralidade do município influencia nos óbitos e na velocidade/aderência da vacinação?
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.

### Pergunta/Análise 3
> * O IDHM (IDH do município) tem alguma relação com o índice de pessoas vacinadas? E de mortalidade?
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.

### Pergunta/Análise 4
> * Qual é a média de pessoas que são internadas na UTI por COVID-19 e saem vivas? Qual é a chance de uma pessoa internada na UTI por consequência da COVID-19 sair com vida? 
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.

### Pergunta/Análise 5
> * Qual é a diferença entre a porcentagem de mulheres que tomaram a vacina e homens que tomaram a vacina? Sabendo isso, essa diferença é relevante? Existe a necessidade de uma campanha de conscientização de vacinação mais direcionada por gênero?
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.

### Pergunta/Análise 6
> * Qual o percentual por faixa etária de pessoas que foram vacinadas em um determinado período de tempo em determinada cidade? Com base nisso, qual deve ser o maior público alvo da campanha de vacinação durante esse período?
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.

### Pergunta/Análise 7
> * Quais municípios possuem mais unidades de saúde com leitos destinados aos pacientes confirmados de COVID-19? 
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.

### Pergunta/Análise 8
> * Quais unidades de saúde possuem mais leitos destinados aos pacientes confirmados de COVID-19?
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.

### Pergunta/Análise 9
> * Quais locais de vacinação disponibilizaram mais doses de vacina de COVID-19? 
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.

### Pergunta/Análise 10
> * Se o local de vacinação que mais disponibilizou doses de vacina de COVID-19 não existisse, qual seria a eficiência da campanha de vacinação em comparação com a real?
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.

### Pergunta/Análise 11
> * Se o local de vacinação que mais disponibilizou doses de vacina de COVID-19 não existisse, onde essas vacinas seriam oferecidas?
>   
>   * Explicação sucinta da análise que será feita ou conjunto de queries que
>     responde à pergunta.


> Coloque um link para o arquivo do notebook que executa o conjunto de queries. Ele estará dentro da pasta `notebook`. Se por alguma razão o código não for executável no Jupyter, coloque na pasta `src`. Se as queries forem executadas atraves de uma interface de um SGBD não executável no Jupyter, como o Cypher, apresente na forma de markdown.
