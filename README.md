

https://github.com/user-attachments/assets/2ee2986a-8785-4290-a3c4-846d098324ab

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

<p align="center">
  <video width="900" controls>
    <source src="midia/headcount.mp4" type="video/mp4">
  </video>
</p>

<p align="center">
    <video width="900" controls>
    <source src="https://raw.githubusercontent.com/GustavOnaga/AgenteIA_HR/main/midia/Headcount.mp4" type="video/mp4">
    </video>
</p>




https://github.com/user-attachments/assets/06008905-8df1-4b32-b454-4c1b2cefe850

