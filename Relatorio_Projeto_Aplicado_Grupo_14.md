
# Projeto Aplicado III – Grupo 14

## 📘 Descrição Geral

Este projeto visa aplicar técnicas de **aprendizado supervisionado** para prever o comportamento de alunos em cursos online, utilizando um dataset extraído do Kaggle: [Online Course Student Engagement Metrics](https://www.kaggle.com/datasets/thedevastator/online-course-student-engagement-metrics).

---

## 🧾 Etapas do Projeto

### 1. 📦 Importação de Bibliotecas

As bibliotecas utilizadas incluem:
- `pandas`, `numpy`: Manipulação de dados
- `matplotlib`, `seaborn`: Visualização
- `sklearn`: Pré-processamento, modelagem, validação e métricas

---

### 2. 🗃️ Carregamento e Análise Inicial dos Dados

- Leitura do arquivo `Courses.csv`.
- Remoção direta de colunas categóricas.
- Cálculo da porcentagem de valores ausentes por coluna.

```python
df = pd.read_csv("Courses.csv")
df = df.drop(columns=df.select_dtypes(include=['object']).columns)
```

---

### 3. ⚙️ Pré-Processamento

#### Técnicas aplicadas:
- Imputação de valores ausentes: média (`SimpleImputer`)
- Normalização: `MinMaxScaler`
- Pipeline montado com `sklearn.pipeline.Pipeline`

---

### 4. 🤖 Modelagem e Avaliação

Modelos utilizados:
- **Random Forest Classifier**
- **Logistic Regression**

Avaliação feita com:
- `accuracy_score`
- `precision_score`
- `recall_score`
- `f1_score`

Busca de hiperparâmetros com `RandomizedSearchCV` e validação cruzada com `StratifiedKFold`.

---

## 📈 Técnicas Utilizadas – Explicação

| Técnica | Finalidade | Observações |
|--------|-------------|-------------|
| `SimpleImputer` | Preencher valores ausentes | Usa média por coluna |
| `MinMaxScaler` | Normalizar atributos numéricos | Mantém valores entre 0 e 1 |
| `RandomForestClassifier` | Classificação robusta | Reduz risco de overfitting |
| `LogisticRegression` | Classificação linear simples | Interpretável, mas menos flexível |
| `StratifiedKFold` | Validação cruzada com classes balanceadas | Preserva distribuição da variável-alvo |
| `RandomizedSearchCV` | Otimização de hiperparâmetros | Mais rápido que grid search |

---

## ✅ Pontos Fortes

- Uso de pipeline (`Pipeline`) para organizar o fluxo de pré-processamento.
- Aplicação de duas abordagens de modelagem com comparação de métricas.
- Emprego de validação cruzada estratificada, o que aumenta a confiabilidade dos resultados.

---

## 🛠️ Possíveis Melhorias

1. **Tratamento de variáveis categóricas**
   - As colunas `object` foram removidas sem análise.
   - Sugerido: aplicar `OneHotEncoder` ou `OrdinalEncoder` para aproveitamento dessas variáveis.

2. **Análise de desbalanceamento**
   - O código não informa se a variável-alvo está balanceada.
   - Sugerido: usar `df['target'].value_counts(normalize=True)`.

3. **Visualização de correlações**
   - Incluir mapa de calor (`sns.heatmap`) ou análise de correlações para inspeção de multicolinearidade.

4. **Mais modelos para comparação**
   - Incluir `XGBoost`, `GradientBoosting`, `SVM` ou `KNN`.

5. **Importância de variáveis**
   - Plotar `feature_importances_` do RandomForest para interpretar os principais atributos.

6. **Ajuste de métricas**
   - Para problemas desbalanceados, focar em `F1-score` e `AUC`, além da acurácia.

---

## 🧠 Conclusão

O trabalho apresenta uma abordagem funcional para a classificação de engajamento estudantil. O uso de pipelines e validação cruzada é adequado, mas pode ser enriquecido com:

- Melhor exploração de dados categóricos
- Avaliação da distribuição da variável alvo
- Inclusão de modelos e técnicas mais robustas

Essas melhorias podem elevar a performance e interpretabilidade dos modelos aplicados.

---

