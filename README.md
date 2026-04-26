# People Analytics — IBM HR Analytics Dataset

> Análise completa de turnover, performance e engajamento com modelo preditivo XGBoost para identificar colaboradores em risco de saída.


---

## Sobre o Projeto

Este projeto aplica técnicas de **People Analytics** sobre o dataset real da IBM disponível no Kaggle, combinando análise exploratória de dados (EDA), visualizações e um modelo preditivo de machine learning para responder à pergunta:

> **"Quais colaboradores têm maior risco de deixar a empresa — e por quê?"**

O resultado é um pipeline completo: da limpeza dos dados até um score de risco individual por colaborador, com recomendações estratégicas orientadas a negócio.

---

## Resultados Principais

| Métrica | Valor |
|---|---|
| Taxa de turnover geral | 16,1% (237 colaboradores) |
| Turnover com overtime | 30,5% vs 10,4% sem overtime |
| Turnover nível júnior (N1) | 26,3% vs 4,7% no nível sênior (N4) |
| Turnover entre 18–25 anos | 35,8% |
| ROC-AUC do modelo | 0,784 |
| Colaboradores com satisfação baixa | 39% (scores 1–2) |

---

## Estrutura do Repositório

```
people-analytics-ibm/
│
├── people_analytics.ipynb                       # Notebook principal com análise completa
├── people_analytics.html                        # Página web interativa (GitHub Pages)
├── WA_Fn-UseC_-HR-Employee-Attrition.csv        # Dataset IBM HR Analytics
└── README.md
```

---

## O que está no Notebook

### 1. Carregamento e Limpeza
- Remoção de colunas constantes sem valor preditivo (`EmployeeCount`, `Over18`, `StandardHours`, `EmployeeNumber`)
- Verificação de valores nulos — dataset 100% limpo
- Criação do `EngagementScore` composto (média de 5 dimensões de satisfação)

### 2. Análise Exploratória (EDA)
- Distribuição demográfica (idade, gênero, estado civil)
- Salário mediano por nível hierárquico
- Análise de satisfação nas 4 dimensões (trabalho, ambiente, relacionamento, work-life balance)

### 3. Análise de Turnover
- Turnover por departamento, nível, estado civil, faixa etária e frequência de viagens
- Comparativo overtime vs. sem overtime
- Distribuição de renda: colaboradores que ficaram vs. que saíram

### 4. Performance e Engajamento
- Distribuição de performance rating
- Boxplot de engajamento por departamento
- Heatmap de correlação entre as dimensões de satisfação
- Impacto de stock options e job involvement na retenção

### 5. Modelo Preditivo XGBoost
- Pré-processamento com `LabelEncoder`
- Split treino/teste estratificado (80/20)
- Treinamento do `XGBClassifier` (200 estimadores, profundidade 4)
- Curva ROC, Matriz de Confusão e Feature Importance
- Validação cruzada 5-fold

### 6. Score de Risco Individual
- Geração de probabilidade de saída para cada colaborador
- Segmentação em baixo, médio e alto risco
- Perfil dos colaboradores de alto risco

---

## Modelo Preditivo

**Algoritmo:** XGBoost Classifier  
**ROC-AUC:** 0,784 (validação cruzada 5-fold)

### Top 5 Features de Importância

| Feature | Importância | Interpretação |
|---|---|---|
| `TotalWorkingYears` | 0,071 | Maturidade de carreira — veteranos saem menos |
| `OverTime` | 0,067 | Horas extras aumentam risco de burnout e saída |
| `EngagementScore` | 0,058 | Bem-estar tem peso maior que fatores financeiros |
| `StockOptionLevel` | 0,054 | Benefícios de longo prazo retêm talentos |
| `JobLevel` | 0,053 | Júniors têm risco 5x maior que sêniores |

### Perfil de Máximo Risco
- Faz horas extras
- Solteiro(a), entre 18 e 25 anos
- Nível hierárquico 1 (júnior)
- Sem stock options (level 0)
- Satisfação igual ou menor que 2/4

---

## Recomendações Estratégicas

| Prioridade | Ação | Impacto Esperado |
|---|---|---|
| Alta | Revisar política de overtime | Redução imediata do principal preditor de turnover |
| Alta | Trilhas de desenvolvimento para nível 1 | Reduzir turnover júnior de 26% para ~15% |
| Média | Expandir stock options para níveis 1 e 2 | Redução de até 54% no turnover desse grupo |
| Média | Pesquisa de clima trimestral (eNPS) | Monitorar os 5 pilares de engajamento |
| Longo prazo | Deploy do modelo no HRIS | Triagem mensal e ação preventiva de RH |

---

## Stack Técnica

- **Python 3.12**
- **Pandas** — manipulação e análise de dados
- **NumPy** — operações numéricas
- **Matplotlib e Seaborn** — visualizações
- **Scikit-learn** — pré-processamento e métricas
- **XGBoost** — modelo preditivo

---

## Dataset

**IBM HR Analytics Employee Attrition & Performance**  
Disponível no Kaggle: [pavansubhasht/ibm-hr-analytics-attrition-dataset](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)

- 1.470 colaboradores reais
- 35 variáveis originais (31 utilizadas após limpeza)
- Target: `Attrition` (Yes/No)

---

## Como Reproduzir

### No Kaggle (recomendado):
1. Acesse o notebook no Kaggle
2. Adicione o dataset IBM HR Analytics via **"+ Add Input"**
3. Execute todas as células

### Localmente:
```bash
git clone https://github.com/seu-usuario/people-analytics-ibm
cd people-analytics-ibm
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
jupyter notebook people_analytics.ipynb
```
# People Analytics — IBM HR Analytics Dataset

**Visualizar projeto:** [Clique aqui para acessar a página do projeto](https://alessandrasgoncalves23-cpu.github.io/People-Analytics/index.html)
---

## Autora

**Alessandra Souza Gonçalves** — Estudante de Ciência de Dados (CEUB, formatura jul/2026)  
Focada em projetos de dados com impacto real em negócios.
