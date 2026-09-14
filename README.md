# Estimação de Níveis de Obesidade — Projeto de Aprendizagem de Máquina (IESB)

Projeto da disciplina **Aprendizagem de Máquina** (Prof. Rodrigo Gonçalves, IESB, 2026/2).

## Dataset

**Estimation of Obesity Levels Based On Eating Habits and Physical Condition**
UCI Machine Learning Repository — <https://archive.ics.uci.edu/dataset/544>
DOI: [10.24432/C5H31Z](https://doi.org/10.24432/C5H31Z) · Licença CC BY 4.0

> Palechor, F. M., & de la Hoz Manotas, A. (2019). Dataset for estimation of obesity levels
> based on eating habits and physical condition in individuals from Colombia, Peru and
> Mexico. *Data in Brief*, 25, 104344.

2.111 registros, 16 atributos (categóricos e numéricos) + variável-alvo `NObeyesdad` (7 classes).
O arquivo `data/ObesityDataSet_raw_and_data_sinthetic.csv` já está incluído no repositório.

## Estrutura

```
.
├── data/
│   └── ObesityDataSet_raw_and_data_sinthetic.csv
├── notebooks/
│   └── 01_eda_preprocessamento_baseline.ipynb   # Marco 1
├── reports/                                     # gráficos exportados pela EDA
├── requirements.txt
├── AUTORES.md
└── README.md
```

## Como reproduzir

### No Google Colab (mais simples)

1. Acesse [colab.research.google.com](https://colab.research.google.com)
2. `Arquivo → Fazer upload de notebook` e selecione
   `notebooks/01_eda_preprocessamento_baseline.ipynb`
3. `Ambiente de execução → Executar tudo`

A primeira célula do notebook baixa o CSV sozinha (não precisa subir o `data/` junto) — todas as
bibliotecas usadas (`pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`) já vêm instaladas
por padrão no Colab.

### Localmente

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/01_eda_preprocessamento_baseline.ipynb
```

Rode as células em ordem (Cell → Run All). O notebook já fixa `RANDOM_STATE = 42` em todas as
etapas com componente aleatório, então o resultado é reprodutível a cada execução — no Colab ou
localmente.

## Marco 1 — o que este notebook entrega

1. **Ficha do dataset** — origem, licença, dicionário de atributos e definição da variável-alvo.
2. **Análise exploratória** — 6 gráficos, cada um com a leitura correspondente.
3. **Pré-processamento justificado** — tratamento de categóricas (binária / ordinal / one-hot) e
   padronização das numéricas, com a razão de cada decisão registrada.
4. **Protocolo experimental** — split treino/validação/teste estratificado, checagem de
   vazamento de dados, escolha e justificativa da métrica (F1-macro).
5. **Baseline** — `DummyClassifier` e `LogisticRegression` sem tuning, referência para os
   modelos do Marco 2.

## Marco 2 (próximos passos)

- k-means (k escolhido por cotovelo + silhueta) e interpretação dos grupos.
- Árvore de decisão/regressão, k-NN, Naive Bayes e Rede Neural Multicamada.
- Validação cruzada k-fold estratificada em todos os modelos supervisionados.
- Quadro comparativo final contra o baseline e recomendação fundamentada.
