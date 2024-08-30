# Datathon-PANDA-Serasa

Em novembro de 2023, durante a XI Secomp, o PANDA junto da Serasa Experian realizaram um Datathon de 6 horas. Este repositório contém a solução implementada pelo time abaixo, que infelizmente não foi vencedora.

- **[Ana Ellen Silva](https://github.com/AnaEren)**
- **[Gabrielly Castilho](https://github.com/gabscastilho)**
- **[João Pedro Trevisan](https://github.com/JPChowder)**
- **[Vinícius G. Perillo](https://github.com/ViniciusPerillo)**

Os dados estão na pasta `data`, os slides, tanto do desafio quanto da apresentação final estão na pasta `slides` e por fim, na pasta `notebooks` existem os colabs parciais feitos durante as poucas 6 horas, no qual a gente tentou explorar conceitos, estretanto a versão final esta na root.

# Problema 

## Contexto
Contexto: O Brasil possui 5570 municípios segundo o IBGE. Cada município possui diversas Secretarias Municipais, responsáveis pela gestão de diversos aspectos das cidades.
Seguem alguns exemplos de secretárias da cidade de São Carlos

O secretário municipal é o responsável pela gestão da secretaria. Por ser uma figura importante dentro do município, ele é considerado uma Pessoa Exposta Politicamente.
As Pessoas Expostas Politicamente(PEP) estão sujeitas a resolução do COAF, que determina algumas regras que devem ser observadas por bancos e outras instituições.
Neste sentido, é importante possuir uma base atualizada e com boa cobertura.

## Desafio
Obter o maior número de Secretários Municipais

- Capturar os dados (acessar os sites das prefeituras)
- Com aprendizado de máquina criar essas capturas para todas prefeituras refletindo suas atualizações
- Padronizar as informações em uma nomenclatura padrão
- Fazer a ingestão dos dados em uma base de dados
- Realizar análise exploratória dos dados
- Montar um notebook com a análise

Insumo: O IBGE disponibiliza um download dos aniversários das cidades, com o nome e UF de todas cidades
https://cidades.ibge.gov.br/

# Nossa Solução

Nossa Solução foi estruturada em 3 etapas:

- Estruturação das URLs
- Raspagem das seções de secretárias
- Raspagem dos secretários

## Estruturação das URLs

Primeiramente, atrvés do site de aniversários das cidades identificou-se um a padrão de URL que dava acesso a maioria das cidades

`www.nomedacidade.uf.gov.br`

Mesmo não acessando todas as cidade ele foi definido como que mais abrangia no tempo apertado que se tinha e através de validações de URL os que não funcionvam eram ignorados.

## Raspagem das seções de secretárias

Durante uma breve análise dos sites de algumas prefeitura percebemos que todas que tinha-mos acessado tinha a secretária de educação. A partir disso teve-se a ideia de usar a secretária de educação para descobrir o padrão no HTML para encontrar as outras secretárias considerando que as secretárias seguem um mesmo padrão dentro do site. Dessa forma utilizou-se o BeautifulSoup para fazer a raspagem dos HTMLs das páginas das prefeituras. Após isso procura-se a sessão de secretárias dentro da página e fazia-se sua raspagem caso fosse em outro HTML. Dentro da página que continha as secretárias procurava-se a palavra educação e quando extraia-se toda a estrutura daquela tag que continha a palavra, além disso era extraído o texto e removida toda a estrutura comum entre várias sercetárias, exemplo:

Secretária da Educação -> Secretária d*

A partir dessa estruturas extraídas eram encontradas as outras secretárias e armazenadas em um cvs.

## Raspagem dos secretáios

Devido ao tempo essa etapa mal foi explorada, apenas algumas ideias de usar LLMs ou alguma outra forma de filtrar melhor esse nomes já que a página de cada secretária têm muito menos padrões que as anteriores, dificultando a obtenção de uma solução geral. No fim utilizou-se o spacy pra ver se conseguiamos fazer uma tokenização da página para extrair alguma coisa

# Resultado

Como o objetivo era conseguir a maior quantidade de nomes não foi possível vencer a competição, já que haviamos extraído apenas 1 nome. Entretanto, nossa solução foi elogiada pela capacidade de genarilzação. Nosso grupo acredita que com mais tempo para polir cada etapa, tratar os erros e dar mais atenção para a última etapa a solução possa ser viável e escalável para todo o Brasil. 






