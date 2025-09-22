# 📊 MVP_Machine_Learning - Previsão de Churn em Telecom
Projeto de conclusão do sprint Machine Learning e Analytics do curso de Pós Graduação em Ciência de Dados e Analytics da PUC-Rio. Este projeto visa prever a evasão de clientes (**churn**) em uma empresa de telecomunicações, utilizando o dataset público **Telco Customer Churn**.

[Link para o notebook no Google Colab](https://colab.research.google.com/drive/1Z3Tf1gCn4uGICX2xcx5czdReTvmtW2Tg?usp=sharing)

---

## 📝 Definição do Problema

**Objetivo:**  
Prever se um cliente de telecomunicações irá cancelar o serviço (**churn**) com base em dados demográficos, contratuais e de uso.

**Descrição do problema:**  
A evasão de clientes representa uma grande perda financeira para empresas de telecomunicações. Antecipar quais clientes têm maior chance de sair permite desenvolver estratégias de retenção personalizadas.

**Premissas / Hipóteses:**  
- Clientes com contratos mensais têm maior chance de churn.  
- A ausência de serviços adicionais (TV, Internet, telefone) pode aumentar o risco de cancelamento.  
- Diferenças de faixa etária e renda influenciam a probabilidade de churn.  

**Restrição na seleção dos dados:**  
- Utilização apenas do dataset original sem enriquecimento externo.  
- Remoção de colunas irrelevantes (ex.: CustomerID).  

**Descrição do dataset:**  
- **Fonte:** Kaggle – [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn/)
- **Tamanho:** 7043 clientes, 21 atributos  
- **Variável alvo:** `Churn` (Yes / No)  
- **Atributos principais:**  
  - Dados demográficos: `gender`, `SeniorCitizen`, `Partner`, `Dependents`  
  - Serviços contratados: `PhoneService`, `InternetService`, `StreamingTV`, etc.  
  - Dados contratuais: `Contract`, `PaymentMethod`, `tenure`, `MonthlyCharges`, `TotalCharges`

---

## ⚙️ Preparação dos Dados

1. Divisão em **treino (80%)** e **teste (20%)**.  
2. Validação cruzada foi aplicada para otimização de hiperparâmetros.  
3. Transformações aplicadas:  
   - Codificação de variáveis categóricas (`LabelEncoder`).  
   - Padronização de atributos numéricos (`StandardScaler`).  
4. Feature Selection: variáveis como `customerID` foram removidas por não contribuírem para a previsão.  

---

## 🤖 Modelagem e Treinamento

- **Algoritmos utilizados:**  
  - Logistic Regression (baseline, interpretável)  
  - Random Forest (bom para capturar interações e variáveis categóricas)  
  - XGBoost (modelo avançado e robusto para classificação tabular)  

- **Ajustes iniciais:**  
  - Hiperparâmetros otimizados com **GridSearchCV** para RF e XGB.  

---

## 📈 Avaliação dos Resultados

**Métricas utilizadas:**  
- **Accuracy** (acurácia geral)  
- **Precision** (taxa de acertos entre positivos previstos)  
- **Recall** (capacidade de identificar clientes que realmente cancelaram)  
- **F1-score** (média harmônica entre Precision e Recall)  
- **ROC AUC** (área sob a curva ROC, medida geral de desempenho do modelo)  

### 📊 Resultados Reais

#### Logistic Regression
- **Accuracy:** 0.80  
- **Precision (churn):** 0.64  
- **Recall (churn):** 0.55  
- **F1 (churn):** 0.59  
- **ROC AUC:** 0.84  

#### Random Forest  
- **Melhores parâmetros:** `{'max_depth': 5, 'n_estimators': 100}`  
- **Accuracy:** 0.80  
- **Precision (churn):** 0.69  
- **Recall (churn):** 0.43  
- **F1 (churn):** 0.53  
- **ROC AUC:** 0.84  

#### XGBoost  
- **Melhores parâmetros:** `{'learning_rate': 0.1, 'max_depth': 3, 'n_estimators': 100}`  
- **Accuracy:** 0.81  
- **Precision (churn):** 0.67  
- **Recall (churn):** 0.53  
- **F1 (churn):** 0.59  
- **ROC AUC:** 0.84  

---

### 📊 Comparação Geral

| Modelo                | Accuracy | Precision (churn) | Recall (churn) | F1   | ROC AUC |
|------------------------|----------|-------------------|----------------|------|---------|
| Logistic Regression    | 0.80     | 0.64              | 0.55           | 0.59 | 0.84    |
| Random Forest          | 0.80     | 0.69              | 0.43           | 0.53 | 0.84    |
| XGBoost                | 0.81     | 0.67              | 0.53           | 0.59 | 0.84    |

👉 Esses resultados são salvos automaticamente em `metrics_results.csv`.

📌 **Melhor solução encontrada:**  
- Apesar de **Random Forest** apresentar maior **precision**, ele perde em **recall**.  
- O **XGBoost** se destacou como o modelo mais **equilibrado** entre as métricas.  

---

## 🔍 Principais Insights

- **Variáveis mais importantes para prever churn:**  
  - Tipo de contrato (mensal aumenta risco de churn).  
  - Tempo de permanência do cliente (`tenure`).  
  - Faturamento mensal (`MonthlyCharges`).  
  - Método de pagamento (cartão virtual e boleto apresentam maior churn).  

- **Padrões identificados:**  
  - Clientes com contratos anuais têm **menor propensão ao churn**.  
  - Clientes com altas cobranças mensais são mais propensos a cancelar.  

---

## ✅ Conclusão

O MVP demonstrou que é possível prever churn com boa precisão utilizando modelos de Machine Learning.  
O **XGBoost** apresentou melhor desempenho e pode ser adotado como modelo principal.  

Este projeto pode ser expandido com:  
- Testes com técnicas de balanceamento de classes (SMOTE).  
- Avaliação de ensembles mais complexos.  
- Integração do modelo em um sistema de CRM para monitoramento em tempo real.  

---

## 📂 Estrutura do Repositório

```bash
MVP_Machine_Learning/
├── WA_Fn-UseC_-Telco-Customer-Churn.csv   # Dataset utilizado
├── mvp_churn.ipynb                        # Notebook principal com análise e modelagem
├── metric_results.csv                     # Métricas de desempenho dos modelos
├── README.md                              # Documentação do projeto
```
---

## 👨‍💻 Autor

**Thiago Cardozo Flores**  
Pós-graduação em Ciência de Dados e Analytics - PUC-Rio  

