# Análise de Dados: Mercado de Jogos da Steam

Pipeline de dados em Python para limpeza, tratamento e análise exploratória (EDA) de um dataset bruto de jogos da Steam, com foco em padrões de precificação, performance de distribuidoras e market share.

---

## Sobre o projeto

Este projeto transforma dados brutos do catálogo da Steam em inteligência de mercado. O trabalho foi dividido em duas fases distintas: primeiro a limpeza e engenharia de atributos, depois a análise exploratória com visualizações estratégicas. O resultado são insights sobre comportamento de preços, ranking de publishers e distribuição do ecossistema.

---

## Estrutura do repositório

```
analise-steam/
├── SteamGames.csv                  # Dataset bruto original
├── SteamGames_clean.csv            # Dataset curado após limpeza
├── limpeza_e_tratamento.ipynb      # Fase 1: limpeza e feature engineering
├── analise.ipynb                   # Fase 2: EDA e visualizações
└── notas_de_projeto.md             # Anotações e decisões técnicas
```

---

## Tecnologias utilizadas

- **Python 3**
- **Pandas** — manipulação, limpeza e agregação de dados
- **Matplotlib** — visualizações estratégicas com formatação profissional
- **Jupyter Notebook** — ambiente de desenvolvimento e documentação

---

## Fases do projeto

### Fase 1 — Limpeza e Engenharia de Dados (`limpeza_e_tratamento.ipynb`)

- Tratamento de valores ausentes e registros inconsistentes no dataset bruto
- Criação do KPI `Total_de_Vendas`, consolidando avaliações positivas e negativas em uma métrica unificada de desempenho
- Geração do dataset curado `SteamGames_clean.csv` para uso na fase de análise

### Fase 2 — Análise Exploratória (`analise.ipynb`)

- **Distribuição de preços** — histograma para identificar padrões de precificação e outliers no catálogo
- **Top 10 Publishers** — ranking dos líderes de mercado com formatação de eixos em escala dinâmica (K e M)
- **Market Share** — gráfico de pizza com participação das principais distribuidoras no ecossistema da Steam

---

## Técnicas de visualização aplicadas

- Formatação de eixos com escalas dinâmicas para volumes altos
- Layout responsivo para nomes e categorias longas
- Grids e paletas de cores para facilitar a leitura e comparação entre categorias

---

## Como executar

```bash
# Clone o repositório
git clone https://github.com/EnukNogueira/analise-steam.git
cd analise-steam

# Instale as dependências
pip install pandas matplotlib jupyter

# Execute os notebooks na ordem
# 1. limpeza_e_tratamento.ipynb
# 2. analise.ipynb
jupyter notebook
```

---

## Autor

**Enuk Nogueira** — Desenvolvedor focado em Engenharia de Dados e Automação de Processos

[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/enuknogueira/)
[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/EnukNogueira)
