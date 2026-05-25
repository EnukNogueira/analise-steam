# Steam: Análise e Tratamento de Dados

##  Sobre o Projeto
Este projeto foi desenvolvido para explorar e extrair inteligência de dados do mercado de jogos da Steam. Através de um pipeline de dados, transformamos dados brutos em insights estratégicos sobre performance de mercado, comportamento de precificação e posicionamento de grandes distribuidoras.

##  Etapas do Desenvolvimento
O projeto foi estruturado em duas fases principais:

1. **Limpeza e Engenharia de Dados (`limpeza_e_tratamento.ipynb`)**:
   * Limpeza de registros brutos e tratamento de valores ausentes.
   * Criação de indicadores de desempenho (**KPIs**), como a métrica `Total_de_Vendas`, consolidando avaliações positivas e negativas.
   * Geração do dataset curado `SteamGames_clean.csv`.

2. **Análise Exploratória (EDA) (`analise.ipynb`)**:
   * **Distribuição de Preços:** Histograma para identificar padrões de precificação e identificar *outliers*.
   * **Top 10 Publishers:** Gráfico de barras horizontais rankeando os líderes de mercado, com formatação avançada de valores (`k` e `M`).
   * **Market Share:** Gráfico de pizza para visualizar a participação das principais distribuidoras no ecossistema da Steam.

##  Visualizações Estratégicas
O projeto utiliza técnicas de visualização profissional com `Matplotlib` e `Pandas`, incluindo:
* Formatação de eixos com escalas dinâmicas para grandes volumes.
* Configurações de layout responsivas para melhor leitura de nomes e categorias.
* Uso de grids e paletas de cores para facilitar a interpretação dos dados.

##  Tecnologias Utilizadas
* **Linguagem:** Python
* **Bibliotecas:** Pandas (Manipulação de dados), Matplotlib (Visualização)
* **Ambiente:** Jupyter Notebook

##  Conclusão
O projeto demonstra a capacidade de transformar dados brutos em ferramentas de suporte à decisão, permitindo identificar quais distribuidoras dominam o mercado e como o comportamento de precificação afeta o engajamento dos jogos.
