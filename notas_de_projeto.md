# Projeto Steam Data

Esse projeto foi feito com um dataset do kaggle, ao qual estarei utilizando um da steam onde está bagunçado e o objetivo é a limpeza e analise dessdes dados. Esse bloco de notas visa anotar todos os erros com que lidei e como resolvi ao longo do tempo.

## Erro 1
Estava dando erro em todo o restante do código por conta de que esqueci de colocar o %b e por conta da uma , depois do %d,%Y.

```python
df_steam['ReleaseDate'] = pd.to_datetime(df_steam['ReleaseDate'], format='%d,%Y', errors='coerce')
df_steam.dropna(subset=['ReleaseDate'], inplace=True)
df_steam.info()
```
Solução:

```python
df_steam['ReleaseDate'] = pd.to_datetime(df_steam['ReleaseDate'], format='%b %d, %Y', errors='coerce')
df_steam.dropna(subset=['ReleaseDate'], inplace=True)
df_steam.info()
```
Nota-se que no código acima que está correto agora o '%b %d, %Y' está correto fazendo o código funcionar corretamente e sem erros.

##Erro 2
O código estava dando erro pois os preços tinha um $ então eu escrevi o seguinte código:

```python
df_steam['price'] = df_steam['price'].str.replace('$', '', regex=False).astype(float)
```
Porem mesmo assim ainda estava dando erro. Então resolvi pesquisar como resolver e escrevi o código assim:

```python
# Converte a coluna price para conseguir ser lido.
df_steam['price'] = pd.to_numeric(
    df_steam['price'].astype(str)
        .str.replace(r'[^0-9.,]', '', regex=True)   
        .str.replace(',', '.', regex=False),        
    errors='coerce'                                 
)
condicao_year = (df_steam['ReleaseDate'].dt.year >= 2020) & (df_steam['ReleaseDate'].dt.year <= 2025)
condicao_price = (df_steam['price'] > 49.99)
condicao_review_player = (df_steam['PositiveReview'] > df_steam['NegativeReview'])

df_gamefilter_aaa = df_steam.loc[condicao_year & condicao_price & condicao_review_player]

print(f"Total de jogos filtrados (AAA): {len(df_gamefilter_aaa)}")
```
A função principal que engloba tudo é o pd.to_numeric(), que serve para forçar a conversão de qualquer coisa para um número. Mas, antes de o dado chegar nele, mas antes ele precisa passar por uma limpeza que seria:

```df_steam['price'].astype(str)```
O que faz? Transforma todos os valores da coluna em Texto (String).
Por que tive que usar isso? uma coluna de preço veio bagunçada, como alguns valores podem ser o número 49.99 (float), outros podem ser o texto "Free" (string), e outros "69.99$" (string). Se tento usar uma função de texto (como o .str.replace) em uma linha que já é um número, o Python trava. O .astype(str) garante que tudo vire texto.

```.str.replace(r'[^0-9.,]', '', regex=True)```
O que faz? Esse é o coração da limpeza, usando Expressão Regular (Regex).
Símbolos: O símbolo ^ dentro dos colchetes [] significa NÃO. Então, estou dizendo ao Python: Encontre qualquer caractere que NÃO seja um número de 0 a 9, NÃO seja um ponto e NÃO seja uma vírgula. Quando achar, apague."
Resultado prático: Se o preço for "$ 59.99 USD", ele arranca o cifrão, os espaços e as letras. Sobra apenas 59.99. Se for "Free", ele apaga todas as letras e a string fica vazia "".

```.str.replace(',', '.', regex=False)```
O que faz? Troca todas as vírgulas por pontos.
Por que é necessário: O Python segue o padrão americano, significa que ele só entende casas decimais separadas por ponto (49.99). Se um jogo europeu ou brasileiro vier custando "49,99". Essa linha vai padronizar tudo para o padrão americano.

```errors='coerce' (Dentro do to_numeric)```
O que faz? Ele força o código a funcionar devidamente.
Por que é necessário: O que estava como"Free" virou uma string vazia "" . Quando o pd.to_numeric tentar transformar valores em branco em número, ele não vai conseguir. Se não uso o errors='coerce', o código dá um erro fatal de ValueError. usando esse comando ele irá substituir por: NaN (Not a Number / Nulo) no lugar e siga em frente."

```.fillna(0.0)```
O que faz? Já que o erros=’coerce’ irá substituir valores em brancos por NaN (Not a Number / Nulo) usei o .fillna(0.0) para substituir os NaN por 0.0.

Otimização
Antes:

```python
df_steam['Tags'] = df_steam['Tags'].fillna('Arcade')
df_steam['Requirement'] = df_steam['Requirement'].fillna('Windows 11')
df_steam['MemoryRequirement'] = df_steam['MemoryRequirement'].fillna('8 GB RAM')
df_steam['CpuRequirement'] = df_steam['CpuRequirement'].fillna('Intel Core i5-6600K or AMD Ryzen R5 1600')
Notei que estava com muitas repetições no código então resolvi otimizar para não ficar tão poluído e redundante.
```
Depois:

```python
substituicao_dados = {
    'Tags': 'Indie',
    'OsRequirement': 'Windows 11',
    'MemoryRequirement': '8 GB RAM',
    'CpuRequirement': 'Intel Core i5-3570K or AMD Ryzen 3 2200G'
}

df_steam.fillna(value=substituicao_dados, inplace=True)
```
Criei uma variável para os dados que quero alterar pois estavam em branco(NaN) depois chamei o data frame e apliquei o comando fillna para substituir pelos dados da variável que modifiquei.
