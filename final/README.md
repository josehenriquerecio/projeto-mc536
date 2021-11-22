# Projeto CSVac

# Equipe CSVac - JHGMA
* José Henrique Dioz Récio - RA: 176622
* Maria Angélica Lobo Alves Paulino - RA: 183465
* Gabriella Serrano Santana - RA: 216698

## Resumo do Projeto
Diante a pandemia de COVID-19 declarada em março de 2020 e que se estende até os dias atuais, surgiu a necessidade do gerenciamento dos dados de ocupação de leitos, crescimento da doença e vacinação pelo Ministério da Saúde. Eles são disponibilizados no DATASUS com a finalidade de compreender melhor a situação do país e otimizar a gestão de recursos.

Nosso projeto consiste em analisar majoritariamente os seguintes bancos de dados:

* Campanha Nacional de Vacinação contra Covid-19;
* Registro de Ocupação Hospitalar COVID-19;
* Base de dados do CNES;
* Censo Demográfico 2010 Sergipe.

Nossa proposta é relacionar a vacinação contra a COVID-19, a ocupação de leitos, escolaridade, ruralidade, entre outros aspectos que consideramos relevantes e serão detalhados ao longo do projeto. Consideramos essa análise muito importante para combater a desinformação e promover a ciência e seus impactos no bem estar da população. Ademais, fizemos um recorte dessa análise para o estado de Sergipe.

## Slides da Apresentação
[Link dos slides](link)

## Modelo Conceitual Preliminar
![ER CSVac](link)

## Modelos Lógicos Preliminares
### Relacional

Vacinação(_cidade_, _data_, qtd_0a17anos,  qtd_18a35anos,  qtd_36a59anos, qtd_60+, qtd_mulheres, qtd_homens)

    cidade chave estrangeira -> Município(nome)
  
Local_de_Vacinação(_nome_, cnes, cidade, qtd_vacina)

Leitos(_cnes_, _mes_, ocupaçãoConfirmadoCli, ocupaçãoConfirmadoUti, saidaConfirmadaObitos, saidaConfirmadaAltas)
  
    cnes chave estrangeira -> Unidade_de_saúde(cnes)
  
Unidade_de_saúde(_cnes_, cidade, nome_fantasia, logradouro)
  
    cidade chave estrangeira -> Município(nome)
  
Município(_nome_, população, idhm, escolarização, ruralidade, pop_0a19anos,  pop_20a39anos,  pop_40a59anos, pop_60+)
  
### Grafos de propriedades
![Modelo Lógico de Grafos](link)

## Dataset Publicado
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
Censo Demográfico 2010 Sergipe via TABnet DATASUS | [Link da Sinopse do Censo Demográfico 2010 Sergipe](http://tabnet.datasus.gov.br/cgi/deftohtm.exe?ibge/cnv/popSE.def) | `<breve descrição do arquivo/base>`

## Detalhamento do Projeto
> Apresente aqui detalhes do processo de construção do dataset e análise. Nesta seção ou na seção de Perguntas podem aparecer destaques de código como indicado a seguir. Note que foi usada uma técnica de highlight de código, que envolve colocar o nome da linguagem na abertura de um trecho com `~~~`, tal como `~~~python`.
> Os destaques de código devem ser trechos pequenos de poucas linhas, que estejam diretamente ligados a alguma explicação. Não utilize trechos extensos de código. Se algum código funcionar online (tal como um Jupyter Notebook), aqui pode haver links. No caso do Jupyter, preferencialmente para o Binder abrindo diretamente o notebook em questão.

~~~python
df = pd.read_excel("/content/drive/My Drive/Colab Notebooks/dataset.xlsx");
sns.set(color_codes=True);
sns.distplot(df.Hemoglobin);
plt.show();
~~~

> Se usar Orange para alguma análise, você pode apresentar uma captura do workflow, como o exemplo a seguir e descrevê-lo:
![Workflow no Orange](images/orange-zombie-meals-prediction.png)

> Coloque um link para o arquivo do notebook, programas ou workflows que executam as operações que você apresentar.

> Aqui devem ser apresentadas as operações de construção do dataset:
* extração de dados de fontes não estruturadas como, por exemplo, páginas Web
* agregação de dados fragmentados obtidos a partir de API
* integração de dados de múltiplas fontes
* tratamento de dados
* transformação de dados para facilitar análise e pesquisa

> Se for notebook, ele estará dentro da pasta `notebook`. Se por alguma razão o código não for executável no Jupyter, coloque na pasta `src` (por exemplo, arquivos do Orange ou Cytoscape). Se as operações envolverem queries executadas atraves de uma interface de um SGBD não executável no Jupyter, como o Cypher, apresente na forma de markdown.

## Evolução do Projeto
> Relatório de evolução, descrevendo as evoluções na modelagem do projeto, dificuldades enfrentadas, mudanças de rumo, melhorias e lições aprendidas. Referências aos diagramas, modelos e recortes de mudanças são bem-vindos.
> Podem ser apresentados destaques na evolução dos modelos conceitual e lógico. O modelo inicial e intermediários (quando relevantes) e explicação de refinamentos, mudanças ou evolução do projeto que fundamentaram as decisões.
> Relatar o processo para se alcançar os resultados é tão importante quanto os resultados.

## Perguntas de Pesquisa/Análise Combinadas e Respectivas Análises

> Liste aqui as perguntas de pesquisa/análise e respectivas análises.
> Nem todas as perguntas precisam de queries que as implementam.
> É possível haver perguntas em que a solução é apenas descrita para
> demonstrar o potencial da base.

### Pergunta/Análise 1
* Municípios com boa escolaridade possuem maiores índices de vacinação? Tendo isso em vista, pode-se afirmar que uma boa educação ajuda na conscientização da necessidade de tomar vacinas? 
  
   * Explicação sucinta da análise que será feita ou conjunto de queries que
     responde à pergunta.

### Pergunta/Análise 2
 * O índice de ruralidade do município influencia nos óbitos e na velocidade/aderência da vacinação?
   
   * Explicação sucinta da análise que será feita ou conjunto de queries que
     responde à pergunta.

### Pergunta/Análise 3
 * O IDHM (IDH do município) tem alguma relação com o índice de pessoas vacinadas? E de mortalidade?
   
   * Explicação sucinta da análise que será feita ou conjunto de queries que
     responde à pergunta.

### Pergunta/Análise 4
 * Qual é a média de pessoas que são internadas na UTI por COVID-19 e saem vivas? Qual é a chance de uma pessoa internada na UTI por consequência da COVID-19 sair com vida? 
   
   * Explicação sucinta da análise que será feita ou conjunto de queries que
     responde à pergunta.

### Pergunta/Análise 5
 * Qual é a diferença entre a porcentagem de mulheres que tomaram a vacina e homens que tomaram a vacina? Sabendo isso, essa diferença é relevante? Existe a necessidade de uma campanha de conscientização de vacinação mais direcionada por gênero?
   
   * Explicação sucinta da análise que será feita ou conjunto de queries que
    responde à pergunta.

### Pergunta/Análise 6
 * Qual o percentual por faixa etária de pessoas que foram vacinadas em um determinado período de tempo em determinada cidade? Com base nisso, qual deve ser o maior público alvo da campanha de vacinação durante esse período?
   
   * Explicação sucinta da análise que será feita ou conjunto de queries que
     responde à pergunta.

### Pergunta/Análise 7
 * Quais municípios possuem mais unidades de saúde com leitos destinados aos pacientes confirmados de COVID-19? 
   
  * Explicação sucinta da análise que será feita ou conjunto de queries que
     responde à pergunta.

### Pergunta/Análise 8
 * Quais unidades de saúde possuem mais leitos destinados aos pacientes confirmados de COVID-19?
   
   * Explicação sucinta da análise que será feita ou conjunto de queries que
     responde à pergunta.

### Pergunta/Análise 9
 * Quais locais de vacinação disponibilizaram mais doses de vacina de COVID-19? 
   
   * Explicação sucinta da análise que será feita ou conjunto de queries que
     responde à pergunta.

### Pergunta/Análise 10
 * Se o local de vacinação que mais disponibilizou doses de vacina de COVID-19 não existisse, qual seria a eficiência da campanha de vacinação em comparação com a real?
   
   * Explicação sucinta da análise que será feita ou conjunto de queries que
     responde à pergunta.

### Pergunta/Análise 11
 * Se o local de vacinação que mais disponibilizou doses de vacina de COVID-19 não existisse, onde essas vacinas seriam oferecidas?
   
   * Explicação sucinta da análise que será feita ou conjunto de queries que
     responde à pergunta.
