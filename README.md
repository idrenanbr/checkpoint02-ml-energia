# Casos de Uso de ML — Energia Eólica e Solar (CP02)

Este pacote contém os arquivos prontos para os checkpoints **CP02_001** e **CP02_002**.

## Estrutura
```
notebooks/
  CP02_001.ipynb  # Appliances (regressão) + Smart Grid (classificação)
  CP02_002.ipynb  # Solar (classificação, 70/30, alvo=mediana) + Wind (regressão, 80/20)
orange/
  CP02_001_regressao_appliances.ows
  CP02_001_classificacao_smartgrid.ows
  CP02_002_classificacao_solar.ows
  CP02_002_regressao_wind.ows
data/
  appliances/energydata_complete.csv
  smart_grid/smart_grid_stability.csv
  solar/solar_radiation.csv
  wind/wind_turbine_scada.csv
```

> **Observação**: os notebooks possuem *fallback* sintético apenas para demonstrar o pipeline quando os CSV reais não estão presentes. Para avaliações finais, **use os datasets reais** nos caminhos acima.

## Requisitos específicos que este pacote atende
- CP02_001:
  - Regressão (Appliances): Linear, Tree, RandomForest; métricas **R², RMSE, MAE**.
  - Classificação (Smart Grid): DecisionTree, **KNN**, LogisticRegression; métricas **acurácia, F1, matriz de confusão**.
- CP02_002:
  - **Solar** (classificação): alvo **Alta/Baixa** pela **mediana**; **split 70/30**; modelos **DecisionTree, RandomForest, SVM (com StandardScaler)**; **acurácia + matriz de confusão**.
  - **Wind** (regressão): **split 80/20**; modelos **Linear, Tree, RandomForest**; métricas **RMSE + R²**.

## Orange Data Mining
Fornecemos fluxos `.ows` (formato Orange) para cada tarefa. Abra o Orange → *File* → *Open* → selecione o `.ows` desejado → ajuste o caminho do arquivo *File* widget para o CSV correspondente → Execute.
- Em **Classificação**: ver *Test & Score*, *Confusion Matrix*.
- Em **Regressão**: ver *Test & Score* para **R²** e **RMSE**.

Versões sugeridas: Orange 3.36+.

## Datasets
- Appliances: UCI — `energydata_complete.csv`
- Smart Grid: versão CSV com coluna alvo (`stabf`/`stable`/etc.).
- Solar Radiation: Kaggle (ajustar nome da coluna de radiação no código, caso difira).
- Wind Turbine SCADA: Kaggle (colunas típicas: `LV ActivePower (kW)`, `Wind Speed (m/s)`, `Theoretical_Power_Curve (kWh)`).

## Como rodar
1. Coloque os CSVs reais nos caminhos em `data/` conforme listado.
2. Abra os notebooks da pasta `notebooks/` e execute as células.
3. (Opcional) Abra os `.ows` no Orange para reproduzir os fluxos gráficos.
