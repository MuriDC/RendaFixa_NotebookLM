# RendaFixa_NotebookLM
--Objetivo:
Criar um Notebook LM da google treinado para ser um especialista em Renda Fixa. 

--Fontes:
Para um vídeo básico explicando o que é renda fixa - https://www.youtube.com/watch?v=LLG2RrpMwkA&pp=ygUdY3Vyc28gZGUgcmVuZGEgZml4YSBhdmFuw6dhZG8%3D
Para um livro que traz temas avançados de renda fixa no Brasil - https://pt.scribd.com/document/697111556/O-mercado-de-renda-fixa-no-Brasil
Pesquisando mais no youtube encontrei cursos do MIT de mercado financeiro que abrange a renda fixa - https://ocw.mit.edu/courses/18-642-topics-in-mathematics-with-applications-in-finance-fall-2024/resources/mit18_642_f24_lec01_1_pdf/
Encontrei cursos avançados no youtube para o CFA - https://www.youtube.com/watch?v=AjiHnr_7V3Y&list=PLzsMtRJ44d8wxolmA9vUVYaC0-88ORUFZ

--Teste  de prompts:
# Pergunta:
Como calcular o preço PUPar de uma renda fixa? Qual a diferença de calcular o preço MtM?

# Resposta:
O cálculo do Preço Unitário ao Par (PU Par) e do Preço a Mercado (MtM - Mark-to-Market) representam duas formas distintas de avaliar um título de renda fixa, baseando-se em perspectivas de "carregamento" versus "liquidação".
Como calcular o preço PU Par
O PU Par (também chamado de preço "na curva") representa o valor do título considerando apenas as condições pactuadas no momento da emissão ou compra
. Para calculá-lo:
Valor Nominal Atualizado (VNA): Inicia-se com o valor nominal de emissão, subtraindo-se eventuais amortizações de principal já ocorridas
.
Apropriação de Juros (Accrual): Adiciona-se a remuneração acumulada desde a data do último evento (ou da emissão) até a data atual, utilizando a taxa de cupom contratual ou a Taxa Interna de Retorno (TIR) de aquisição
.
[...]

# Pergunta:
Como fazer o cálculo de risco de uma renda fixa?

# Resposta:
O cálculo de risco em renda fixa é um processo quantitativo que busca medir a sensibilidade do preço de um título a variações nas taxas de juros (risco de mercado) e a probabilidade de perdas por inadimplência (risco de crédito)
.
De acordo com as fontes, os principais métodos e métricas para realizar esses cálculos são:
1. Mensuração do Risco de Mercado (Sensibilidade a Juros)
O risco de mercado é a possibilidade de perda no valor de um título devido à oscilação das taxas de juros (ETTJ)
. Para calculá-lo, utilizam-se:
Duration (Duração): É a medida de primeira ordem que indica o tempo médio para recuperar o capital investido
.
Macaulay Duration: Prazo médio ponderado dos fluxos de caixa
.
Modified Duration (Duração Modificada): Mede a variação percentual aproximada do preço para cada 1% de mudança na taxa de juros
.
Effective Duration (Duração Efetiva): Essencial para títulos com opções embutidas (como títulos resgatáveis), pois leva em conta que os fluxos de caixa podem mudar com a taxa
.
Convexity (Convexidade): Mede a "curvatura" da relação preço-taxa. É uma medida de segunda ordem que ajusta a estimativa da Duration, tornando-a mais precisa para grandes oscilações de juros
.
[...]

# Pergunta:
Qual a diferença entre Duration de Macaulay e Modificada?

# Resposta:
A principal diferença entre a Duration de Macaulay e a Duration Modificada reside na sua natureza e finalidade: a primeira é uma medida teórica de tempo, enquanto a segunda é uma medida prática de sensibilidade de preço
.
Duration de Macaulay
Definição: É o prazo médio ponderado até que um investidor receba o fluxo de caixa total de um título (cupons e principal)
.
Cálculo: Representa o "centro de gravidade" dos fluxos de caixa, onde cada período de tempo é ponderado pelo valor presente do seu respectivo fluxo em relação ao preço total do título
.
Unidade: É expressa em anos
.
Caso Especial: Para títulos zero-cupom, a Duration de Macaulay é exatamente igual ao tempo remanescente até o vencimento
.
Duration Modificada
Definição: É uma extensão que quantifica a volatilidade do preço de um título frente a mudanças nas taxas de juros
.
Cálculo: Baseia-se na primeira derivada da função de preço do título em relação ao seu rendimento (yield)
.
Aplicação: Indica a variação percentual aproximada no preço para cada mudança de 1% (100 pontos-base) nas taxas de juros
. Por exemplo, um título com duration modificada de 8 anos verá seu preço cair aproximadamente 8% se as taxas subirem 1%
.
Relação Matemática
[...]

# Pergunta:
Faça um passo a passo de como calcular o risco de mercado de uma renda fixa.

# Resposta:
O cálculo do risco de mercado em renda fixa foca na sensibilidade do preço de um título às oscilações das taxas de juros (risco pré)
. Para realizá-lo de forma sistemática, siga este passo a passo baseado nas fontes:
1. Realize a Marcação a Mercado (MtM)
O primeiro passo é determinar o valor provável de realização do título hoje
.
Projete todos os fluxos de caixa futuros (cupons e principal)
.
Desconte esses fluxos para o valor presente utilizando a Estrutura a Termo de Taxas de Juros (ETTJ) atual do mercado para cada respectivo prazo
.
2. Calcule a Duration (Sensibilidade de Primeira Ordem)
A duration mede quão sensível é o preço do título a mudanças nas taxas de juros
.
Duration de Macaulay: Calcule o prazo médio ponderado dos fluxos de caixa, onde os pesos são os valores presentes de cada fluxo em relação ao preço total
.
Duration Modificada: Divida a Duration de Macaulay por (1+y), onde y é a taxa interna de retorno (TIR)
. Ela indica a variação percentual aproximada no preço para cada 1% de mudança na taxa de juros
.
3. Calcule a Convexidade (Refinamento de Segunda Ordem)
Como a relação entre preço e taxa é curva (não linear), a duration falha em grandes oscilações
.
Calcule a convexidade, que representa a segunda derivada do preço em relação à taxa
.
Utilize a Expansão de Taylor para somar o efeito da duration e da convexidade, obtendo uma estimativa muito mais precisa da variação do preço
.
4. Determine o DV01 (Risco em Valor Monetário)
Para uma gestão prática, calcule o DV01 (ou PV01), que traduz a sensibilidade percentual em dinheiro vivo
.
Fórmula: DV01=DurationModificada×Pre 
c
\c
​
 o×0,0001
.
Isso revela quanto o portfólio perde ou ganha em reais (ou dólares) para cada 1 ponto-base (0,01%) de movimento na curva de juros
.
5. Calcule o Value at Risk (VaR)
O VaR consolida o risco indicando a perda máxima esperada em condições normais de mercado
.
Mapeamento em Vértices: Aloque o valor de mercado (MtM) do título em vértices padronizados (ex: 21, 252, 504 dias úteis), distribuindo o valor proporcionalmente com base na proximidade dos prazos
.
Aplicação de Volatilidade e Correlação: Utilize a matriz de variância-covariância (volatilidade histórica dos juros e correlação entre os vértices da curva) para calcular o risco da carteira combinada
.
Modelo Paramétrico: Multiplique a exposição em cada vértice pelo desvio padrão (volatilidade) e pelo fator de confiança (ex: 2,33 para 99% de confiança)

[...]

# Pergunta:
Descreva melhor o passo 5. Como que devo dividir em vértices?

# Resposta:
A divisão de uma carteira de renda fixa em vértices é um procedimento fundamental para o cálculo do VaR (Value at Risk) paramétrico. Esse mapeamento permite simplificar o cálculo, agregando diversos títulos com vencimentos variados em prazos padronizados
.
De acordo com as fontes, aqui está o detalhamento de como realizar essa divisão:
1. Por que usar vértices?
O cálculo de risco operação por operação seria computacionalmente exaustivo e exigiria uma matriz de covariância gigante
. Ao agrupar os valores em vértices, você foca nos pontos onde a informação sobre a expectativa de juros é mais líquida (taxas forward) e padroniza os fatores de risco
.
2. Escolha dos Vértices Padronizados
Os vértices são intervalos de tempo fixos (geralmente em dias úteis). Os prazos comuns adotados pelo mercado e por órgãos reguladores como o Banco Central incluem:
Curtíssimo prazo: 1, 21, 42, 63, 84 dias úteis
.
Médio prazo: 126, 252 (1 ano), 504 (2 anos), 756 (3 anos) dias úteis
.
Longo prazo: 1.008, 1.260, 2.520 dias úteis e assim por diante
.
3. Regras de Alocação (Mapeamento)
A alocação do valor de mercado (MtM) de um título entre os vértices adjacentes baseia-se no conceito de duration, buscando criar uma exposição equivalente entre os prazos padronizados
.
[...]

# O que é o Notebook?
É uma forma de treinar a IA com fontes para um tema específico. O modelo de IA utilizado é o Gemini.
Na versão não paga é possível adicionar 50 fontes, sendo essas fontes de qualqer fortado (vídeos, documentos, sites, arquivos, etc...)

A partir dessas fontes é possívvel fazer perguntas na linguagem natural e ter as respostas embasadas por estas fontes. Também é possível criar slides, resumos em audio, mapa mental e assim por diante.

# Criando o Notebook
O passo a passo para criar o modelo é:
1- Entrar no site notebooklm.google.com.
2-Alimentar com as fontes. (canto superior esquerdo)
2.1-No meu caso utilizei vídeos do youtube e URLs contendo livro e cursos.
2.2-Após adicionar as fontes, ainda no canto superior esquerdo, fiz uma busca "deep research" escrevendo "Advanced fixed income". Ali foram trazidos outras fontes de informação, selecionei no checkbox as que eu queria utilizar, desmarcando as outras que não queria incluir. 
3-Fazer testes. (Perguntas no chat, criar mapas mentais, etc..) 
4-Analisar o resultado. Com base nas respostas, entender se o modelo foi treinado de forma correta.

# Notebook LM
A versão final pode ser encontrada aqui: https://notebooklm.google.com/notebook/b10adf54-5978-44fa-b065-bc3699500272
