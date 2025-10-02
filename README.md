# Checkpoint 02 - Machine Learning em Energias Renováveis

## 👥 Integrante
- Renan Mano Otero - RM 554911

## 📋 Descrição do Projeto

Este repositório contém a implementação completa do Checkpoint 02 da disciplina **Soluções em Energias Renováveis e Sustentáveis**. O projeto aplica técnicas de Machine Learning (regressão e classificação) em datasets relacionados a energia solar, eólica, consumo residencial e estabilidade de redes elétricas.

## 🗂️ Estrutura do Repositório

```
checkpoint02-ml-energia/
│
├── data/                          # Datasets
│   ├── appliances/
│   │   └── energydata_complete.csv
│   ├── smart_grid/
│   │   └── smart_grid_stability.csv
│   ├── solar/
│   │   └── SolarPrediction.csv
│   └── wind/
│       └── wind_turbine_scada.csv
│
├── notebooks/                     # Notebooks Jupyter
│   └── CP02_completo.ipynb       # Notebook principal com todas as análises
│
├── orange/                        # Workflows Orange Data Mining
│   ├── CP02_001_regressao_appliances.ows
│   ├── CP02_001_classificacao_smartgrid.ows
│   ├── CP02_002_classificacao_solar.ows
│   └── CP02_002_regressao_wind.ows
│
├── requirements.txt               # Dependências Python
├── .gitignore                     # Arquivos ignorados pelo Git
└── README.md                      # Este arquivo
```

## 📊 Datasets Utilizados

### 1. Appliances Energy Prediction
- **Fonte**: UCI Machine Learning Repository
- **Descrição**: Dados de consumo de energia de eletrodomésticos com variáveis ambientais
- **Tarefa**: Regressão
- **Split**: 70/30

### 2. Smart Grid Stability
- **Fonte**: UCI / Kaggle
- **Descrição**: Dados simulados de estabilidade de rede elétrica
- **Tarefa**: Classificação (Estável/Instável)
- **Split**: 70/30

### 3. Solar Radiation Prediction
- **Fonte**: [Kaggle - Solar Energy Dataset](https://www.kaggle.com/datasets/dronio/SolarEnergy)
- **Descrição**: Previsão de radiação solar baseada em condições climáticas
- **Tarefa**: Classificação (Alta/Baixa radiação pela mediana)
- **Split**: 70/30

### 4. Wind Turbine SCADA
- **Fonte**: [Kaggle - Wind Turbine Dataset](https://www.kaggle.com/datasets/berkerisen/wind-turbine-scada-dataset)
- **Descrição**: Dados operacionais de turbinas eólicas
- **Tarefa**: Regressão (Prever potência gerada em kW)
- **Split**: 80/20

## 🚀 Como Executar

### Pré-requisitos

- Python 3.8+
- Jupyter Notebook ou Google Colab
- Git

### Instalação Local

```bash
# Clonar o repositório
git clone https://github.com/idrenanbr/checkpoint02-ml-energia.git
cd checkpoint02-ml-energia

# Instalar dependências
pip install -r requirements.txt

# Iniciar Jupyter Notebook
jupyter notebook
```

### Executar no Google Colab

1. Acesse o [Google Colab](https://colab.research.google.com/)
2. Faça upload do notebook `CP02_completo.ipynb`
3. Faça upload dos datasets na sessão do Colab
4. Execute: Runtime → Run all

## 📈 Resultados Obtidos

### ✅ Parte 1 - Regressão: Appliances Energy Prediction

**Objetivo**: Prever consumo de energia de eletrodomésticos

**Modelos Testados**:
- Regressão Linear
- Decision Tree Regressor
- Random Forest Regressor

**Resultados**:

| Modelo | R² | RMSE | MAE |
|--------|-----|------|-----|
| **Random Forest** | **0.537** | **68.04** | **32.60** |
| Decision Tree | 0.180 | 90.60 | 38.87 |
| Linear Regression | 0.169 | 91.17 | 52.55 |

**Melhor Modelo**: Random Forest Regressor
- **R²**: 0.537 - O modelo explica 53.7% da variância dos dados
- **RMSE**: 68.04 Wh - Erro médio de previsão
- **MAE**: 32.60 Wh - Erro absoluto médio

**Análise**: O Random Forest superou os outros modelos devido à sua capacidade de capturar relações não-lineares entre as variáveis ambientais e o consumo de energia.

---

### ✅ Parte 2 - Classificação: Smart Grid Stability

**Objetivo**: Classificar estabilidade da rede elétrica (Estável/Instável)

**Modelos Testados**:
- Decision Tree Classifier
- K-Nearest Neighbors (KNN)
- Logistic Regression

**Resultados**:

| Modelo | Acurácia | F1-Score |
|--------|----------|----------|
| **Decision Tree** | **1.000** | **1.000** |
| Logistic Regression | 0.9995 | 0.9995 |
| KNN | 0.818 | 0.816 |

**Melhor Modelo**: Decision Tree Classifier
- **Acurácia**: 100% - Classificação perfeita
- **F1-Score**: 1.000 - Equilíbrio perfeito entre precisão e recall
- **Matriz de Confusão**: 6522 verdadeiros negativos, 11478 verdadeiros positivos, 0 erros

**Análise**: O Decision Tree alcançou desempenho perfeito, sugerindo que os dados possuem padrões bem definidos para classificação de estabilidade. A Logistic Regression também apresentou excelente desempenho (99.95%), enquanto o KNN teve performance inferior devido à sensibilidade a dados de alta dimensionalidade.

---

### ✅ Exercício 1 - Classificação: Solar Radiation

**Objetivo**: Classificar períodos de Alta/Baixa radiação solar

**Modelos Testados**:
- Decision Tree Classifier
- Random Forest Classifier
- Support Vector Machine (SVM)

**Configuração**:
- Split: 70/30 (treino/teste)
- Normalização: StandardScaler aplicado
- Alvo: Criado pela mediana da radiação solar

**Resultados**:

| Modelo | Acurácia |
|--------|----------|
| **Random Forest** | **98.01%** |
| Decision Tree | 97.20% |
| SVM | 95.66% |

**Melhor Modelo**: Random Forest Classifier
- **Acurácia**: 98.01% - Excelente capacidade de classificação
- **Características**: Ensemble de árvores que reduz overfitting e melhora generalização

**Análise**: O Random Forest obteve o melhor desempenho ao combinar múltiplas árvores de decisão, capturando melhor as relações complexas entre variáveis meteorológicas e radiação solar. O SVM, mesmo com normalização, teve desempenho ligeiramente inferior, possivelmente devido à não-linearidade dos dados.

---

### ✅ Exercício 2 - Regressão: Wind Turbine Power

**Objetivo**: Prever potência gerada por turbina eólica (kW)

**Modelos Testados**:
- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor

**Configuração**:
- Split: 80/20 (treino/teste)
- Variável alvo: LV ActivePower (kW)

**Resultados**:

| Modelo | R² | RMSE |
|--------|-----|------|
| **Linear Regression** | **0.901** | **411.71** |
| Random Forest | 0.900 | 412.36 |
| Decision Tree | 0.830 | 538.79 |

**Melhor Modelo**: Linear Regression
- **R²**: 0.901 - O modelo explica 90.1% da variância dos dados
- **RMSE**: 411.71 kW - Erro médio de previsão

**Análise**: Surpreendentemente, a Regressão Linear teve o melhor desempenho, indicando que a relação entre velocidade do vento e potência gerada é aproximadamente linear (ou já bem capturada pela potência teórica). O Random Forest teve desempenho muito similar (R² = 0.900), enquanto a Decision Tree individual sofreu com overfitting.

---

## 🎯 Principais Aprendizados

1. **Diferenciação entre Regressão e Classificação**: 
   - Regressão para valores contínuos (energia, potência)
   - Classificação para categorias discretas (estável/instável, alta/baixa radiação)

2. **Importância da Normalização**: 
   - Crucial para algoritmos baseados em distância (KNN, SVM)
   - Menos relevante para modelos baseados em árvores

3. **Ensemble Methods (Random Forest)**:
   - Geralmente superam modelos únicos
   - Reduzem overfitting através da agregação de múltiplos modelos

4. **Contexto dos Dados**:
   - Modelos simples (Linear Regression) podem ser suficientes quando relações são lineares
   - Modelos complexos (Random Forest) brilham em relações não-lineares

5. **Métricas Apropriadas**:
   - R² e RMSE para regressão avaliam capacidade de previsão numérica
   - Acurácia, F1-score e matriz de confusão para classificação avaliam capacidade de discriminação entre classes

## 🛠️ Tecnologias Utilizadas

- **Python 3.8+**
- **Pandas** - Manipulação de dados
- **NumPy** - Computação numérica
- **Scikit-learn** - Algoritmos de ML
- **Matplotlib/Seaborn** - Visualização
- **Jupyter Notebook / Google Colab** - Ambiente de desenvolvimento
- **Orange Data Mining** - Workflows visuais

## 📝 Observações

- Os notebooks incluem geração de dados sintéticos como fallback quando os CSVs reais não estão disponíveis
- Para resultados autênticos, utilize os datasets originais baixados dos links fornecidos
- Os workflows Orange (arquivos .ows) requerem ajuste manual dos caminhos dos arquivos
- Todos os modelos usam `random_state=42` para garantir reprodutibilidade

## 🔗 Links Úteis

- [Documentação Scikit-learn](https://scikit-learn.org/)
- [Orange Data Mining](https://orangedatamining.com/)
- [Kaggle Datasets](https://www.kaggle.com/datasets)
- [UCI ML Repository](https://archive.ics.uci.edu/)

## 📧 Contato

**Renan Mano Otero**  
RM: 554911  
GitHub: [@idrenanbr](https://github.com/idrenanbr)

---

**Disciplina**: Soluções em Energias Renováveis e Sustentáveis  
**Professor**: André Tritiack  
**Data de Entrega**: 24 de setembro de 2025
