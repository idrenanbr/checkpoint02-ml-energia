# Casos de Uso de Machine Learning — Energia Eólica e Energia Solar

Este repositório contém a entrega da disciplina **Soluções em Energias Renováveis e Sustentáveis** da FIAP.  Aqui são explorados casos de regressão e classificação aplicados a dados energéticos, utilizando Python (pandas e scikit‑learn) e fluxos montados no Orange Data Mining.  O trabalho está dividido em duas partes principais (Previsão de consumo de eletrodomésticos e Estabilidade de rede inteligente) e em dois exercícios específicos envolvendo radiação solar e turbinas eólicas.

## Estrutura do repositório

- `notebook_energia.ipynb` – Notebook Jupyter com todo o código de exploração, pré‑processamento, treinamento de modelos e avaliação das tarefas de regressão e classificação.  Para cada parte do enunciado são apresentados diferentes modelos (Regressão Linear, Árvore de Regressão, Random Forest, KNN, Regressão Logística, SVM etc.), as métricas pertinentes (R², RMSE, MAE, acurácia, matriz de confusão, F1‑score) e uma discussão dos resultados obtidos.
- `data/` – Pasta destinada a armazenar os datasets (`energydata_complete.csv`, `smart_grid_stability.csv`, `SolarPrediction.csv` e `wind_scada.csv`).  Os arquivos não são disponibilizados diretamente neste repositório por restrições de licenciamento; consulte a seção **Datasets** para orientações de download.
- `orange/` – Pasta opcional para salvar os fluxos (.ows) criados no [Orange Data Mining](https://orangedatamining.com/).  Os fluxos replicam as etapas principais do notebook (carregamento dos dados, pré‑processamento, seleção de atributos, treinamento e validação de modelos) de forma visual.

## Datasets

As atividades utilizam quatro conjuntos de dados diferentes.  Certifique‑se de baixá‑los e colocá‑los na pasta `data/` antes de executar o notebook.

### 1. Appliances Energy Prediction (UCI)

* **Link:** [UCI Machine Learning Repository – Appliances Energy Prediction](https://archive.ics.uci.edu/dataset/374/appliances+energy+prediction)
* **Descrição:** trata‑se de uma série temporal de 4,5 meses registrada a cada 10 minutos em uma casa de baixo consumo energético.  Sensores ZigBee registraram temperatura e umidade em diversos cômodos (cozinha, sala, lavanderia, escritório etc.), cujos valores foram depois agregados em intervalos de 10 minutos.  Os dados climáticos (temperatura, pressão, vento e umidade externos) vieram de uma estação meteorológica próxima e foram sincronizados pela coluna de data/hora.  Duas variáveis randômicas foram incluídas no conjunto para fins de controle 【722290714644327†L46-L54】.  A variável alvo `Appliances` representa o consumo energético (Wh) dos eletrodomésticos, enquanto as outras colunas (`T1`, `RH_1`, `T2`, `RH_2`, …, `rv1`, `rv2`) descrevem temperaturas (°C), umidades (%), pressão (mm Hg), velocidade do vento (m/s) e outras medições ambientais 【722290714644327†L93-L109】.
* **Utilização no trabalho:** usada na **Parte 1** para prever o consumo de energia a partir de variáveis ambientais.  É um problema de regressão.

### 2. Smart Grid Stability

* **Link:** (substitua pelo endereço do dataset disponibilizado pela disciplina ou outro dataset de estabilidade de rede elétrica)
* **Descrição:** conjunto de dados simulados de uma rede elétrica inteligente contendo grandezas elétricas (potência ativa e reativa, tensão, corrente etc.) e um rótulo que indica se a rede está estável ou instável.  Este dataset não está hospedado publicamente; utilize a versão fornecida pelos professores ou adaptada de um projeto similar.
* **Utilização no trabalho:** usado na **Parte 2** para classificar a estabilidade da rede.  É um problema de classificação binária.

### 3. Solar Radiation Prediction

* **Link:** [Solar Radiation Prediction Dataset – Kaggle](https://www.kaggle.com/datasets/dronio/solarenergy)
* **Descrição:** registros históricos de irradiância solar e variáveis meteorológicas (temperatura, umidade, pressão, velocidade do vento, cobertura de nuvens etc.) em diferentes intervalos de tempo.  No notebook, a variável alvo foi criada a partir da coluna de radiação solar, dividindo o conjunto em **Alta Radiação** e **Baixa Radiação** com base na mediana.  A tarefa consiste em treinar classificadores como árvore de decisão, Random Forest e SVM para identificar períodos de alta irradiância.
* **Utilização no trabalho:** usado no **Exercício 1** de classificação.

### 4. Wind Turbine Scada Dataset

* **Link:** [Wind Turbine Scada Dataset – Kaggle](https://www.kaggle.com/datasets/berkerisen/wind-turbine-scada-dataset)
* **Descrição:** dados de SCADA de uma turbina eólica na Turquia registrados em intervalos de 10 minutos durante 2018.  O arquivo inclui variáveis como `Date/Time`, **LV ActivePower (kW)** (potência elétrica real gerada), **Wind Speed (m/s)** (velocidade do vento na altura do rotor), **Theoretical_Power_Curve (kWh)** (potência teórica calculada a partir da velocidade do vento) e **Wind Direction (°)**, entre outras.  Estas variáveis permitem analisar o desempenho da turbina ao longo do tempo e construir modelos de regressão para prever potência ativa a partir das condições de vento.  Uma captura da página do Kaggle mostrando a descrição do conjunto pode ser vista em【435699542643837†screenshot】.
* **Utilização no trabalho:** usado no **Exercício 2** de regressão para prever a potência gerada por turbinas eólicas.

## Instruções para execução

1. **Clonar o repositório no GitHub** ou baixar os arquivos manualmente.
2. Criar a pasta `data/` e copiar os conjuntos de dados mencionados acima para dentro dela.  O notebook assume nomes de arquivo como `energydata_complete.csv`, `smart_grid_stability.csv`, `SolarPrediction.csv` (ou `SolarEnergy.csv`) e `wind_scada.csv`.  Ajuste o caminho nos blocos de código se utilizar nomes diferentes.
3. Abrir o notebook `notebook_energia.ipynb` no Jupyter Notebook ou outro ambiente compatível e executar as células em ordem.  Nas primeiras células há testes para verificar se os arquivos estão presentes; caso não estejam, scripts de exemplo geram dados sintéticos para ilustrar os modelos, mas recomenda‑se o uso dos dados reais para obter resultados significativos.
4. (Opcional) Abra o Orange Data Mining e recrie os fluxos descritos no notebook: carregue o dataset, aplique normalização, divida em treino/teste, escolha os algoritmos desejados (p.ex. **Tree**, **Random Forest**, **Logistic Regression** ou **SVM**), conecte o widget **Test & Score** para avaliar e compare as métricas.  Salve o arquivo `.ows` na pasta `orange/` caso deseje compartilhar.

## Observações

* O notebook foi desenvolvido em ambiente Python 3 com as bibliotecas `pandas`, `numpy`, `scikit‑learn`, `matplotlib` e `seaborn`.  Todas as dependências podem ser instaladas com `pip install -r requirements.txt` (arquivo não incluído, pois as bibliotecas são comuns em ambientes de ciência de dados).
* Por limitações de acesso a alguns servidores, os datasets não acompanham este repositório.  Se preferir automatizar o download, utilize ferramentas como `kaggle api` (exige conta Kaggle) ou `wget` apontando para os links de download fornecidos nos sites oficiais.
* O trabalho buscou ilustrar a aplicação prática de técnicas de machine learning em problemas de energia solar e eólica, discutindo vantagens, desvantagens e interpretação das métricas.  Resultados podem variar ao utilizar parâmetros diferentes ou realizar engenharia de atributos adicional.
