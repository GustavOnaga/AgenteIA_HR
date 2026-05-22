## 📁 Estrutura da Documentação — HR Analytics AI Agent

Este diretório contém os principais artefatos utilizados na construção do projeto **HR Analytics AI Agent**, desenvolvido utilizando Databricks Genie Space, Unity Catalog e engenharia semântica aplicada a analytics de RH.

---

### 📂 benchmark.md

Contém o conjunto de perguntas utilizadas para validação do agente de IA. O objetivo deste arquivo é:

- testar a qualidade das respostas do Genie
- validar a interpretação semântica
- verificar consistência analítica
- avaliar as queries geradas automaticamente

---

### 📂 prompt-design.md

Documenta a estratégia de engenharia de prompt utilizada para especializar o agente de IA. Este arquivo descreve:

- contexto fornecido ao agente
- regras de interpretação
- direcionamentos analíticos
- limitações de resposta
- comportamento esperado

---

### 📂 sql-expressions.md

Contém expressões SQL reutilizáveis utilizadas na camada analítica. O objetivo deste arquivo é centralizar cálculos e métricas padronizadas para garantir consistência nas análises.

---

### 📂 sql-queries.md

Arquivo contendo queries SQL completas utilizadas pelo projeto. As queries representam exemplos de análises realizadas pelo agente de IA sobre os dados de RH.

---

### 📂 unity-catalog.md

Documentação da camada semântica construída no Unity Catalog. Este arquivo descreve:

- tabelas
- colunas
- descrições técnicas
- definições de negócio
