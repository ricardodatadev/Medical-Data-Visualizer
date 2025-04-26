# Medical Data Visualizer

Este projeto visa **visualizar e analisar dados médicos** de pacientes para explorar a relação entre **doenças cardíacas** e fatores como **colesterol**, **glicose**, **hábitos de vida** e **medições corporais**.

## Objetivo

- Gerar dois gráficos principais:
  1. Catplot: Mostra a distribuição de variáveis como colesterol, glicose, tabagismo, atividade física, entre pacientes com e sem doenças cardíacas.
  2. Heatmap: Exibe as correlações entre variáveis como peso, altura, pressão arterial, etc.

![Imagem](catplot.png)
![Imagem](heatmap.png)

## Bibliotecas Usadas

- pandas: Manipulação e análise de dados.
- seaborn e matplotlib: Geração de gráficos.
- numpy: Cálculos matemáticos.

## Arquivo medical_data_visualizer.py

## Importação das bibliotecas

O código começa com a importação das bibliotecas necessárias: pandas, seaborn, matplotlib e numpy

---

## Carregamento dos dados

Os dados médicos são carregados a partir do arquivo `medical_examination.csv` usando **pandas**.  
Este arquivo contém informações como **idade, peso, altura, pressão arterial, colesterol, glicose**, entre outros dados dos pacientes.

---

## Adição da coluna overweight

A partir das informações de peso e altura, é calculado o Índice de Massa Corporal (IMC) de cada paciente.  
Se o IMC for maior que 25, o paciente é classificado como "sobrepeso" (valor 1), caso contrário, o valor é 0.

---

## Normalização das variáveis cholesterol e gluc

As variáveis cholesterol e gluc são normalizadas da seguinte forma:
- Valor 1 (normal) → 0
- Valor 2 ou 3 (acima do normal) → 1


## Função draw_cat_plot()

A função draw_cat_plot é responsável por gerar o gráfico categórico (Catplot)

- Os dados são reorganizados com pd.melt() para facilitar a contagem das ocorrências de cada variável como colesterol glicose, tabagismo, atividade física, etc.
- O gráfico é gerado usando `sns.catplot()` e apresenta a contagem dessas variáveis em pacientes com e sem doenças cardíacas

---

## Função draw_heat_map()

A função draw_heat_map gera o mapa de calor (Heatmap) com base nas correlações entre as variáveis.

- Antes de gerar o gráfico, os dados são limpos, removendo registros com:
  - Pressão diastólica (ap_lo) maior que a sistólica (ap_hi)
  - Altura ou peso fora dos limites do intervalo entre o 2.5% e 97.5%
- A matriz de correlação é calculada e visualizada com `sns.heatmap()`, com máscara para ocultar a metade superior do gráfico.



## Geração e salvamento dos gráficos

Os gráficos são salvos automaticamente no diretório do projeto:

-  catplot.png: gráfico categórico.
-  heatmap.png: mapa de calor com as correlações.



## Instalação

Para rodar o projeto localmente, instale as dependências:

```bash
pip install pandas seaborn matplotlib numpy
