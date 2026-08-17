# Análise de Dados: Mercado de Jogos da Steam

Projeto de análise de dados utilizando um dataset de jogos da Steam, com foco em tratamento, análise exploratória e visualização de dados.

---

## Sobre o projeto

O projeto começou como uma análise exploratória de um dataset bruto da Steam. Durante o desenvolvimento, os dados passaram por diferentes etapas de tratamento e validação para corrigir inconsistências e preparar as informações para análise.

Atualmente, o projeto está sendo revisado e ampliado com novas análises e um dashboard desenvolvido no Power BI.

---

## Estrutura do projeto

```text
analise-steam/
├── SteamGames.csv                  # Dataset bruto original
├── SteamGames_clean.csv            # Dataset tratado
├── limpeza_e_tratamento.ipynb      # Limpeza e tratamento dos dados
├── analise.ipynb                   # Análise exploratória
├── notas_de_projeto.md             # Anotações e decisões técnicas
└── README.md                       # Documentação do projeto
```

---

## Tecnologias utilizadas

* **Python**
* **Pandas** — tratamento e análise dos dados
* **Matplotlib** — visualização de dados
* **Jupyter Notebook** — análise e documentação
* **Power BI** — criação do dashboard

---

## Etapas do projeto

### 1. Tratamento dos dados

* [x] Tratamento de valores ausentes
* [x] Correção de inconsistências nos dados
* [x] Tratamento da coluna de preços
* [x] Padronização dos tipos de dados
* [x] Remoção de colunas sem utilidade para a análise
* [x] Criação da métrica `TotalReviews`
* [x] Geração do dataset tratado `SteamGames_clean.csv`

### 2. Análise exploratória

* [x] Análise da distribuição de preços
* [x] Análise de avaliações positivas e negativas
* [x] Análise de `TotalReviews`
* [x] Ranking de publishers
* [x] Análise por gênero
* [ ] Novas análises e aprofundamento dos insights

### 3. Power BI

* [x] Importação do dataset tratado
* [x] Tratamento complementar dos dados
* [x] Correção da escala dos preços
* [ ] Criação do dashboard
* [ ] Organização e refinamento dos visuais
* [ ] Revisão final do dashboard

### 4. Revisão da análise

Após a conclusão do dashboard, o projeto será revisitado no Jupyter Notebook para aprofundar as análises e explorar novos padrões encontrados nos dados.

* [ ] Revisar a análise exploratória
* [ ] Criar novas análises
* [ ] Explorar relações entre preço, avaliações e popularidade
* [ ] Analisar diferenças entre gêneros
* [ ] Analisar desempenho das publishers
* [ ] Revisar e documentar os principais insights

### 5. Documentação e publicação

* [x] Atualizar o README
* [ ] Documentar as decisões e alterações realizadas no projeto
* [ ] Organizar os arquivos finais
* [ ] Atualizar o projeto no GitHub
* [ ] Publicar a versão revisada no LinkedIn

---

## Sobre a métrica `TotalReviews`

O dataset não disponibiliza o número real de unidades vendidas pelos jogos.

Por isso, o projeto não trata o número de avaliações como vendas. A métrica `TotalReviews` é calculada pela soma das avaliações positivas e negativas:

```python
df_steam['TotalReviews'] = (
    df_steam['PositiveReview'] + df_steam['NegativeReview']
)
```

Essa métrica é utilizada como um indicador de **popularidade e engajamento**, e não como uma estimativa oficial de vendas.

---

## Dashboard

O projeto contará com um dashboard desenvolvido no Power BI para apresentar os principais indicadores e insights encontrados durante a análise.

**Status:** Em desenvolvimento.

---

## Autor

**Enuk Nogueira**

Estudante de Análise e Desenvolvimento de Sistemas com foco em Dados, Python e Machine Learning.

[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge\&logo=linkedin\&logoColor=white)](https://www.linkedin.com/in/enuknogueira/)

[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge\&logo=github\&logoColor=white)](https://github.com/EnukNogueira)

