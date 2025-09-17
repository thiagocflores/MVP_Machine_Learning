# MVP_Machine_Learning - Previsão de Churn em Telecom
Projeto de conclusão do sprint Machine Learning e Analytics do curso de Pós Graduação em Ciência de Dados e Analytics da PUC-Rio

## 📌 Contexto do Problema

A retenção de clientes é um dos maiores desafios em empresas de telecomunicações. A perda de clientes (churn) gera custos elevados de aquisição de novos usuários e impacto direto na receita.  
O objetivo deste projeto é **desenvolver modelos de Machine Learning capazes de prever quais clientes têm maior propensão a cancelar o serviço**, permitindo à empresa adotar estratégias proativas de retenção.

---

## 🎯 Objetivo

Construir um MVP de ciência de dados que:  
- Analise dados de clientes da Telco.  
- Modele e compare diferentes algoritmos de machine learning.  
- Identifique as variáveis mais relevantes para prever o churn.  
- Entregue insights que possam apoiar a tomada de decisão.  

---

## 🗂️ Dataset

Utilizamos o dataset público **Telco Customer Churn**, disponível originalmente no Kaggle.  

- **Observações:** 7.043 clientes.  
- **Atributos:** informações demográficas, serviços contratados, uso de internet/telefone, tipo de contrato, método de pagamento e faturamento mensal.  
- **Variável alvo:** `Churn` (indica se o cliente cancelou ou não o serviço).  

📎 [Link para o dataset no GitHub](https://github.com/thiagocflores/MVP_Machine_Learning/blob/main/WA_Fn-UseC_-Telco-Customer-Churn.csv)

---

## 🛠️ Preparação de Dados

- Remoção de valores ausentes e ajustes de tipos de variáveis.  
- Transformação de variáveis categóricas em dummies (One-Hot Encoding).  
- Normalização de variáveis numéricas.  
- Separação em **treino (70%)** e **teste (30%)**.  
- Não foi utilizada validação cruzada, pois o dataset já possui amostra balanceada e suficiente para treino/teste.  

---

## 🤖 Modelagem e Treinamento

Três algoritmos foram avaliados:

1. **Logistic Regression (baseline):** modelo linear simples, usado como referência.  
2. **Random Forest:** modelo de árvore com capacidade de capturar relações não lineares.  
3. **XGBoost:** modelo avançado baseado em boosting, eficiente em problemas de classificação binária.  

### Ajustes iniciais
- Hiperparâmetros básicos foram ajustados para cada modelo.  
- Foi verificado risco de *underfitting* com Logistic Regression.  
- Foi realizada otimização de hiperparâmetros com GridSearchCV para Random Forest e XGBoost.  

---

## 📈 Avaliação de Resultados

As métricas utilizadas foram: **Acurácia, Precisão, Recall, F1-score e AUC-ROC**.

| Modelo              | Acurácia | Precisão | Recall | F1-score | AUC  |
|---------------------|----------|----------|--------|----------|------|
| Logistic Regression | 0.80     | 0.72     | 0.65   | 0.68     | 0.84 |
| Random Forest       | 0.83     | 0.76     | 0.71   | 0.73     | 0.87 |
| XGBoost             | 0.85     | 0.78     | 0.73   | 0.75     | 0.89 |

📌 **Melhor resultado:** **XGBoost**, que obteve o maior desempenho em todas as métricas.  

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

MVP_Machine_Learning/
│── WA_Fn-UseC_-Telco-Customer-Churn.csv # Dataset
│── mvp_churn_template_v2.ipynb # Notebook no Google Colab
│── README.md # Este arquivo

---

## 👨‍💻 Autor

**Thiago Cardozo Flores**  
Pós-graduação em Ciência de Dados e Analytics - PUC-Rio  

