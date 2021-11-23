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

## Modelo Conceitual
![ER CSVac](https://github.com/josehenriquerecio/projeto-mc536/blob/main/final/assets/conceitual.png)

## Modelos Lógicos 
### Relacional

Vacinação(_cidade_, _data_, qtd_0a17anos,  qtd_18a35anos,  qtd_36a59anos, qtd_60+, qtd_mulheres, qtd_homens) VERIFICARRRRRRRRRRR
<br>
&nbsp; &nbsp; &nbsp; cidade chave estrangeira -> Município(nome)
</br>
  
Local_de_Vacinação(_nome_, cnes, cidade, qtd_vacina)

Leitos(_cnes_, _mes_, ocupaçãoConfirmadoCli, ocupaçãoConfirmadoUti, saidaConfirmadaObitos, saidaConfirmadaAltas)
<br>
&nbsp; &nbsp; &nbsp; cnes chave estrangeira -> Unidade_de_saúde(cnes)
 </br>
 
Unidade_de_saúde(_cnes_, cidade, nome_fantasia, logradouro)
<br>
&nbsp; &nbsp; &nbsp; cidade chave estrangeira -> Município(nome)
</br>
  
Município(_nome_, população, idhm, escolarização, ruralidade, pop_0a19anos,  pop_20a39anos,  pop_40a59anos, pop_60+)
  
### Grafos de propriedades
![Modelo Lógico de Grafos](https://github.com/josehenriquerecio/projeto-mc536/blob/main/final/assets/grafo_de_propriedade.PNG)

## Dataset Publicado

título do arquivo/base | link | breve descrição
----- | ----- | -----
leitos_final | [Link do arquivo leitos_final.csv](https://github.com/josehenriquerecio/projeto-mc536/blob/main/final/data/processed/leitos_final.csv) | Esse arquivo modelo csv apresenta o número de leitos clínicos e de UTI ocupados por pacientes com COVID-19, além do número de óbitos e de altas registrados por mês em cada unidade de saúde de Sergipe.
locais_vacina | [Link do arquivo locais_vacina.csv](https://github.com/josehenriquerecio/projeto-mc536/blob/main/final/data/processed/locais_vacina.csv) | Esse arquivo modelo csv apresenta a quantidade de vacinas aplicadas em cada local de vacinação e seu respectivo munícipio.
municipios_final(1)| [Link do arquivo municipios_final(1).csv](https://github.com/josehenriquerecio/projeto-mc536/blob/main/final/data/processed/municipios_final%20(1).csv) | Esse arquivo modelo csv apresenta a população total e dividida por faixa etária, a ruralidade, o IDHM e a escolaridade de cada munícipio de Sergipe.
ubs-se| [Link do arquivo ubs-se.csv](https://github.com/josehenriquerecio/projeto-mc536/blob/main/final/data/processed/ubs-se.csv) | Esse arquivo modelo csv apresenta o nome, o endereço, o cnes e a cidade de cada unidade de saúde de Sergipe.

## Bases de Dados

Título da base | Link | Descrição
----- | ----- | -----
Campanha Nacional de Vacinação contra Covid-19 | [Link da Campanha Nacional de Vacinação contra Covid-19](https://opendatasus.saude.gov.br/dataset/covid-19-vacinacao) | Essa base de dados registra todos os dados referentes a vacinação, sendo estas: informações do paciente, local de vacinação, data, marca da vacina, tipo de dose.
Registro de Ocupação Hospitalar COVID-19 | [Link do Registro de Ocupação Hospitalar COVID-19](https://opendatasus.saude.gov.br/dataset/registro-de-ocupacao-hospitalar) | Esse banco de dados controla os leitos hospitalares de COVID-19, registrando altas, óbitos e ocupação dos leitos em cada unidade de saúde do país.
Base de dados do CNES | [Link da Base de dados do CNES](https://opendatasus.saude.gov.br/dataset/cadastro-nacional-de-estabelecimentos-de-saude-cnes/resource/015d095b-01fe-45ec-9c21-6b6a7476a04f) | Essa base de dados armazena o cadastro nacional de estabelecimentos de saúde e suas informações principais, como nome, cidade, endereço e horario de funcionamento.
Censo Demográfico 2010 Sergipe via TABnet DATASUS | [Link do Censo Demográfico 2010 Sergipe](http://tabnet.datasus.gov.br/cgi/deftohtm.exe?ibge/cnv/popSE.def) | Esse site permitiu gerar uma tabela (.csv) com os dados demográficos de Sergipe, com a quantidade de população por faixa etária em cada município do estado.

## Detalhamento do Projeto
Aqui estarão detalhas as principais etapas na construção deste dataset.

A construção desse dataset foi feita utilizando Jupyter Notebooks com a linguagem Python. Dentro do ambiente, foram utilizadas as seguintes bibliotecas, instaladas previamente:
~~~python
import pandas as pd
import numpy as np
from datetime import datetime
~~~

Para importar os arquivos .csv das bases de terceiro referenciadas nesse projeto, utilizamos o trecho abaixo com uso da biblioteca pandas e alguns parâmetros que variam de acordo com o .csv, como o de separados, ou especificação de campos com data.

~~~python
df = pd.read_csv('../data/external/nomedoarquivo.csv', sep=';')
~~~

### Construção de vacinação-se.csv

FALTA ISSO AQUI

### Construção de leitos_final.csv
Para a construção do .csv de leitos tivemos que importar o registro de leitos do dataset original disponibilizado no datasus, e utilizar métodos da biblioteca pandas para padronizar e selecionar somente o mês da coluna referente as datas de registros. Em seguida, selecionamos apenas as colunas desejadas agrupando por CNES e por mês, somando as ocupaçoes, óbitos e altas, conforme abaixo.
~~~python
df['dataNotificacao'] = pd.to_datetime(df['dataNotificacao'], format="%Y-%m-%dT%H:%M:%S.%f", errors='coerce')
df['mes'] = pd.to_datetime(df['dataNotificacao']).dt.month 
leitos_final = df.groupby(['cnes','mes'],as_index=False)[['ocupacaoConfirmadoCli', 'ocupacaoConfirmadoUti','saidaConfirmadaObitos','saidaConfirmadaAltas']].sum()
~~~

### Construção de ubs-se.csv
Para construir o .csv das unidades de saúde de Sergipe, tomamos o dataset original com todas as unidades de saúde do país. No original havia uma coluna IBGE com o código do município em que a UBS se localiza, então utilizamos o trecho de código abaixo para substituir cada código dos municípios de Sergipe [listados aqui](https://pt.wikipedia.org/wiki/Lista_de_munic%C3%ADpios_de_Sergipe) pelo nome do município e em seguida selecionamos apenas as UBS do estado SE (código 28).

~~~python
df['Municipio'] = df['IBGE'].astype(str) 
df["Municipio"].replace({'280010':'Amparo de São Francisco',"280030":"Aracaju",'280020':'Aquidabã','280040':'Arauá',
'280050':'Areia Branca','280060':'Barra dos Coqueiros','280067':'Boquim','280070':'Brejo Grande','280100':'Campo do Brito','280110':'Canhoba','280120':'Canindé de São Francisco','280130':'Capela','280140':'Carira','280150':'Carmópolis', '...':'...'}, inplace=True)
temp = df[df["UF"] == 28]
~~~

### Construção de municipios.csv
A construção dessa tabela consistiu apenas no join de duas outras tabelas: municipio_intermed.csv (df2) e população_faixa_etaria.csv (df).

~~~python
result = df2.join(df[['0 a 19', '20 a 39', '40 a 59', '60+']])
~~~

### Construção de locais_vacina.csv

Do dataset de vacinação nacional obtido do datasus, extraímos algumas informações como: nome, cnes e cidade. Além disso, somamos a ocorrência de cada local na tabela para assim saber quantas vacinas foram ali aplicadas, e registrando o total em uma nova coluna denominada 'total_vacinas'.

~~~python
final = df.groupby(['estalecimento_nofantasia','estabelecimento_valor','estabelecimento_municipio_nome']).estalecimento_nofantasia.count().reset_index(name="total_vacinas")
~~~


## Evolução do Projeto
> Relatório de evolução, descrevendo as evoluções na modelagem do projeto, dificuldades enfrentadas, mudanças de rumo, melhorias e lições aprendidas. Referências aos diagramas, modelos e recortes de mudanças são bem-vindos.
> Podem ser apresentados destaques na evolução dos modelos conceitual e lógico. O modelo inicial e intermediários (quando relevantes) e explicação de refinamentos, mudanças ou evolução do projeto que fundamentaram as decisões.
> Relatar o processo para se alcançar os resultados é tão importante quanto os resultados.

> acho que da pra detalhar mais e acrescentar coisas
> 
Inicialmente, o projeto CSVac iria relacionar os dados de vacinação e registro de leitos apenas. Porém nossas perguntas e análises seriam muito limitadas e então com incentivo do professor acrescentamos novos bancos externos como referência e novos fatores que seriam considerados: dados populacionais, IDH, escolarização e ruralidade fornecidos pelo IBGE.

Tendo isso em mente, nossos modelos conceitual e lógicos (relacional e grafos) sofreram grandes modificações. 

DETALHAR MUDANÇAS AQUI - (COMPARAR IMAGENS ANTIGAS E NOVAS DO MODELO ??) - 

Com esse grande volume de dados enfrentamos algumas dificuldades. Aprender alguns recursos da biblioteca pandas para manipulação dos arquivos .csv já iria tomar um tempo, e o tamanho de alguns arquivos externos obtidos dificultavam muito seu processamento, gastando então mais tempo nos testes do código da construção do nosso dataset. Além disso, alguns bancos de dados apresentavam dados desorganizados ou mal coletados, como campos que deveriam ser numéricos com conteúdo em texto, e vice-versa, dados faltantes, etc.


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
