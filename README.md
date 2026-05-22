## 🤖 HR Analytics AI Agent — Databricks Genie

Agente de IA especializado em analytics de RH utilizando o Databricks Genie Space para responder perguntas em linguagem natural sobre indicadores organizacionais. 


### 📌 Sobre o Projeto

Este projeto tem como objetivo democratizar o acesso a dados de RH através de um agente conversacional capaz de interpretar perguntas em linguagem natural e transformá-las em análises acionáveis.

A solução foi construída utilizando uma camada Gold analítica previamente estruturada, com foco na especialização semântica do agente.


### 🚀 Objetivo

Permitir que usuários de negócio realizem perguntas como:

- “Qual área possui maior turnover?”
- “Qual departamento teve crescimento de headcount?”
- “Como está a diversidade por liderança?”
- “Quais cargos possuem mais desligamentos?”

Sem necessidade de conhecimento técnico em SQL ou modelagem de dados.


### 📂 Dataset

Dataset público de RH utilizado como fonte para o projeto: https://www.kaggle.com/code/bfne00/limpando-dados-de-rh/input


### 🏗️ Arquitetura da Solução

```text
Dataset RH
    ↓
Camada Gold Analítica
    ↓
Unity Catalog
    ↓
Camada Semântica
    ↓
Databricks Genie Space
    ↓
Usuário de Negócio
```
### ✅ Resultados

Utilizando a aba de benchmark, o agenete obteve uma acurácia de **90%**.

### 🎞️ Demonstração

#### Quantidade de headcount


https://github.com/user-attachments/assets/f917a8c5-1d58-4ca6-9071-dff19c5497f6




