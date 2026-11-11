# Brasileirão Analytics ⚽📊

Projeto de análise exploratória de dados do Campeonato Brasileiro de Futebol, desenvolvido com Python, Pandas, NumPy e Matplotlib.

O objetivo é investigar padrões históricos da competição, analisar o desempenho das equipes e explorar possíveis relações entre estatísticas de finalização e resultados das partidas.

O projeto também contempla uma etapa de auditoria da qualidade dos dados, buscando identificar possíveis inconsistências antes de realizar as análises comparativas.

## Objetivos

- Investigar a evolução da média de gols por partida ao longo das temporadas.
- Analisar a distribuição dos resultados e a vantagem de jogar em casa.
- Comparar o desempenho ofensivo e defensivo das equipes.
- Identificar equipes com melhores médias de gols marcados, gols sofridos e saldo de gols.
- Investigar a relação entre finalizações e resultados das partidas.
- Identificar possíveis inconsistências na base de dados e documentar as decisões de tratamento.

## Base de dados

O projeto utiliza o conjunto de dados **Campeonato Brasileiro de Futebol**, disponibilizado no Kaggle pelo usuário **adaoduque**.

**Fonte original:** [Campeonato Brasileiro de Futebol — Kaggle](https://www.kaggle.com/datasets/adaoduque/campeonato-brasileiro-de-futebol)

A base reúne informações históricas sobre partidas do Campeonato Brasileiro, incluindo datas, equipes, placares, gols, cartões e estatísticas de desempenho.

O conjunto utilizado contempla as temporadas de **2003 a 2025**, totalizando 9.165 partidas no arquivo principal.

### Arquivos utilizados

| Arquivo | Descrição |
|---|---|
| `campeonato-brasileiro-full.csv` | Informações das partidas, datas, equipes e placares. |
| `campeonato-brasileiro-estatisticas-full.csv` | Estatísticas das equipes, como chutes, posse de bola, passes, faltas e cartões. |
| `campeonato-brasileiro-gols.csv` | Registros de gols e informações relacionadas aos atletas. |
| `campeonato-brasileiro-cartoes.csv` | Registros de cartões aplicados aos atletas. |

O arquivo `Legenda.txt`, disponibilizado junto à base, também pode ser consultado para compreender as colunas.

### Disponibilidade dos dados e licenciamento

Os arquivos originais da base de dados não são distribuídos neste repositório. Para reproduzir as análises, é necessário obtê-los diretamente na publicação original do Kaggle.

Essa decisão considera os direitos de terceiros e as condições de utilização e redistribuição dos dados.

A publicação original indica a licença **GNU General Public License v2.0 (GPL-2.0)**.

- [Publicação original no Kaggle](https://www.kaggle.com/datasets/adaoduque/campeonato-brasileiro-de-futebol)
- [Texto da licença GNU GPL v2.0](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

A licença MIT presente neste repositório refere-se ao código desenvolvido para o projeto e não substitui nem modifica as condições de licenciamento da base de dados original.

## Análises desenvolvidas

### 1. Evolução da média de gols por partida

Análise da quantidade média de gols por partida ao longo das temporadas, buscando identificar variações no comportamento ofensivo do campeonato.

**Principais resultados:**

- A média geral foi de aproximadamente **2,56 gols por partida**.
- A maior média anual ocorreu em 2005, com aproximadamente **3,14 gols por partida**.
- A menor média foi registrada em 2018, com aproximadamente **2,18 gols por partida**.
- Em 2025, a média chegou a aproximadamente **2,52 gols por partida**.

### 2. Distribuição dos resultados e vantagem de jogar em casa

Investigação da frequência de vitórias dos mandantes, empates e vitórias dos visitantes.

**Distribuição geral dos resultados:**

| Resultado | Quantidade | Percentual |
|---|---:|---:|
| Vitória do mandante | 4.550 | 49,65% |
| Empate | 2.421 | 26,42% |
| Vitória do visitante | 2.194 | 23,94% |
| **Total** | **9.165** | **100%** |

Os resultados indicam uma predominância de vitórias das equipes mandantes ao longo do período analisado.

Também foi realizada uma comparação entre os períodos pré-pandemia, durante a pandemia e pós-pandemia, observando as alterações na distribuição dos resultados.

### 3. Desempenho ofensivo e defensivo das equipes

Comparação do desempenho dos clubes a partir dos gols marcados, gols sofridos e saldo de gols.

Foram utilizados indicadores totais e médias por partida, permitindo uma comparação mais equilibrada entre equipes com diferentes quantidades de jogos.

Para os rankings, foi estabelecido um critério mínimo de 100 partidas disputadas.

**Destaques da análise:**

| Equipe | Média de gols marcados | Média de gols sofridos | Saldo médio |
|---|---:|---:|---:|
| Palmeiras | 1,485 | 1,119 | +0,367 |
| São Paulo | 1,408 | 1,084 | +0,324 |
| Flamengo | 1,463 | 1,153 | +0,310 |
| Cruzeiro | 1,424 | 1,182 | +0,242 |
| Internacional | 1,329 | 1,104 | +0,225 |

Entre as equipes que atenderam ao critério estabelecido, o Palmeiras apresentou o maior saldo médio de gols.

### 4. Auditoria da qualidade das estatísticas de finalização

Antes de investigar a relação entre finalizações e resultados, foi realizada uma análise da consistência dos registros estatísticos.

Foram identificadas proporções elevadas de valores iguais a zero na coluna de chutes no alvo nas temporadas de 2015 e 2016:

| Temporada | Registros com zero chutes no alvo | Total de registros | Percentual |
|---|---:|---:|---:|
| 2015 | 720 | 760 | 94,74% |
| 2016 | 728 | 758 | 96,04% |

Também foram investigadas as partidas de 2019 nas quais as duas equipes apresentavam simultaneamente zero chutes totais e zero chutes no alvo.

Essa investigação identificou **23 partidas suspeitas**, correspondentes a 46 observações de equipes.

Esses registros foram considerados possíveis sinais de ausência ou incompletude das estatísticas. Entretanto, a presença de zeros, isoladamente, não comprova a causa da inconsistência.

### 5. Relação entre finalizações e resultados das partidas

Foi realizada uma comparação entre as médias de chutes totais e chutes no alvo das equipes, considerando três categorias: vitória, empate e derrota.

Para essa análise, foi utilizada uma amostra tratada, com as seguintes decisões metodológicas:

- Exclusão das temporadas de 2015 e 2016, devido às proporções anormais de zeros identificadas.
- Inclusão das temporadas de 2017 a 2023 e de 2025.
- Exclusão das 23 partidas suspeitas de 2019, nas quais ambas as equipes apresentavam zero chutes totais e zero chutes no alvo.

Após os filtros, a amostra final foi composta por **6.034 observações de equipes**.

**Distribuição da amostra:**

| Resultado | Observações |
|---|---:|
| Vitória | 2.187 |
| Empate | 1.660 |
| Derrota | 2.187 |
| **Total** | **6.034** |

**Médias de finalizações por resultado:**

| Resultado | Média de chutes totais | Média de chutes no alvo |
|---|---:|---:|
| Derrota | 12,25 | 3,50 |
| Empate | 12,90 | 3,97 |
| Vitória | 13,52 | 5,28 |

As equipes vencedoras apresentaram as maiores médias de chutes totais e chutes no alvo na amostra analisada.

Também foi calculada a razão entre a média de chutes no alvo e a média de chutes totais de cada grupo:

| Resultado | Razão entre as médias |
|---|---:|
| Derrota | 28,61% |
| Empate | 30,77% |
| Vitória | 39,09% |

Os resultados indicam uma associação entre o desempenho nas finalizações e os resultados das partidas. Entretanto, não permitem afirmar que o aumento das finalizações necessariamente causa uma vitória.

## Tecnologias utilizadas

| Tecnologia | Aplicação |
|---|---|
| Python 3.13 | Linguagem de programação. |
| Pandas | Manipulação, limpeza e análise dos dados. |
| NumPy | Operações numéricas. |
| Matplotlib | Construção de gráficos e visualizações. |
| Jupyter Notebook | Desenvolvimento e documentação das análises. |
| Git e GitHub | Versionamento e gerenciamento do projeto. |

## Estrutura do projeto

```text
brasileirao-analytics/
│
├── data/
│   ├── raw/
│   │   └── .gitkeep
│   │
│   └── processed/
│       └── .gitkeep
│
├── notebooks/
│   ├── .gitkeep
│   └── 01_exploracao_inicial.ipynb
│
├── src/
│   └── .gitkeep
│
├── .gitignore
├── LICENSE
└── README.md
```

**Descrição dos diretórios:**

- `data/raw/`: destinado ao armazenamento local dos arquivos originais da base de dados.
- `data/processed/`: destinado aos dados resultantes de etapas de processamento.
- `notebooks/`: contém os notebooks utilizados no desenvolvimento das análises.
- `src/`: reservado para módulos e códigos reutilizáveis do projeto.
- `LICENSE`: licença do código desenvolvido.

Os arquivos CSV originais não fazem parte dos arquivos versionados no GitHub.

## Como executar o projeto

### 1. Clonar o repositório

```bash
git clone <URL_DO_REPOSITORIO>
```

Entre no diretório:

```bash
cd brasileirao-analytics
```

### 2. Obter os dados

Acesse a publicação original no Kaggle:

[Campeonato Brasileiro de Futebol — Kaggle](https://www.kaggle.com/datasets/adaoduque/campeonato-brasileiro-de-futebol)

Faça o download da base e extraia os arquivos necessários para a pasta:

```text
data/raw/
```

Os arquivos esperados são:

```text
campeonato-brasileiro-full.csv
campeonato-brasileiro-estatisticas-full.csv
campeonato-brasileiro-gols.csv
campeonato-brasileiro-cartoes.csv
Legenda.txt
```

### 3. Criar um ambiente virtual

```bash
python -m venv .venv
```

No Windows PowerShell, ative o ambiente:

```powershell
.venv\Scripts\Activate.ps1
```

### 4. Instalar as dependências

```bash
pip install pandas numpy matplotlib jupyter
```

### 5. Executar o notebook

Inicie o Jupyter Notebook:

```bash
jupyter notebook
```

Abra o arquivo:

```text
notebooks/01_exploracao_inicial.ipynb
```

Execute as células em ordem, utilizando preferencialmente a opção **Restart & Run All**, para reproduzir as análises, tabelas e gráficos.

## Limitações e considerações

- A qualidade das estatísticas de finalização varia entre as temporadas.
- Os anos de 2015 e 2016 apresentam proporções muito elevadas de zeros em chutes no alvo.
- Em 2019, foram identificadas partidas nas quais ambas as equipes apresentavam zero chutes totais e zero chutes no alvo.
- A identificação de valores suspeitos não comprova, isoladamente, que a fonte original esteja incorreta.
- A exclusão de temporadas e partidas é uma decisão metodológica adotada para a análise comparativa, não uma comprovação de que todos os registros removidos sejam inválidos.
- A análise histórica reúne equipes, formatos de competição e quantidades de partidas diferentes.
- O critério mínimo de 100 partidas utilizado nos rankings é uma escolha metodológica.
- As relações identificadas entre finalizações e resultados são observacionais e não demonstram causalidade.
- A razão entre as médias de chutes no alvo e chutes totais não representa a média das taxas individuais de precisão das equipes.

## Licenciamento

O código desenvolvido para este projeto está disponibilizado sob a licença **MIT**, conforme descrito no arquivo `LICENSE`.

A base de dados utilizada pertence à sua publicação original no Kaggle e possui condições próprias de licenciamento. Sua utilização deve respeitar os termos definidos pelo autor e pela licença indicada na fonte.

**Referências:**

- Duque, A. *Campeonato Brasileiro de Futebol*. Kaggle. [https://www.kaggle.com/datasets/adaoduque/campeonato-brasileiro-de-futebol](https://www.kaggle.com/datasets/adaoduque/campeonato-brasileiro-de-futebol).
- Free Software Foundation. *GNU General Public License, version 2*. [https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html).

---

Projeto desenvolvido para fins acadêmicos, aprendizado e construção de portfólio na área de Análise de Dados.