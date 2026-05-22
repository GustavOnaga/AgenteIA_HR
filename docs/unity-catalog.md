# 🧠 Unity Catalog — Semantic Layer Documentation

Este documento apresenta a estrutura semântica utilizada no projeto **HR Analytics AI Agent**, detalhando as descrições adicionadas às colunas da camada Gold para melhorar a interpretação do agente de IA no Databricks Genie.

---

### 📂 Tabela Principal

```text
hr_gold.hr_employee_attrition
```

### 📑 Dicionário de Dados

Descrição:

```text
Tabela de People Analytics contendo dados demográficos, organizacionais e de clima sobre atrito (attrition) e retenção de colaboradores. Inclui atributos como idade, departamento, cargo e fatores de satisfação/equilíbrio de vida. Ideal para análises de turnover, diagnóstico de perda de talentos e desenvolvimento de estratégias de engajamento do RH.
```


| Coluna                   | Descrição                                                                                                                                 |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Age                      | Representa a idade do funcionário, útil para analisar tendências demográficas dentro da força de trabalho.                                |
| Attrition                | Indica se o funcionário deixou a empresa (`Yes` / `No`).                                                                                  |
| BusinessTravel           | Frequência de viagens a negócios (`Non-Travel`, `Travel_Rarely`, `Travel_Frequently`).                                                    |
| DailyRate                | Taxa de remuneração diária do funcionário, útil para análises financeiras e orçamento.                                                    |
| Department               | Identifica o departamento em que o funcionário trabalha, permitindo avaliações de desempenho departamental.                               |
| DistanceFromHome         | Mede a distância entre a residência do funcionário e o local de trabalho, potencialmente afetando a satisfação com o deslocamento.        |
| Education                | Indica o nível de educação alcançado pelo funcionário.                                                                                    |
| EducationField           | Especifica a área de estudo do histórico educacional do funcionário, útil para entender conjuntos de habilidades.                         |
| EmployeeCount            | Representa o número total de funcionários na organização, útil para planejamento da força de trabalho e análises de atrito.               |
| EmployeeNumber           | Identificador único para cada funcionário, essencial para o acompanhamento dos registros de emprego.                                      |
| EnvironmentSatisfaction  | Reflete o nível de satisfação do funcionário com o ambiente de trabalho, impactando estratégias de retenção.                              |
| Gender                   | Indica o gênero do funcionário, útil para estatísticas de diversidade e inclusão.                                                         |
| HourlyRate               | Representa a taxa de pagamento por hora do funcionário, importante para análises de custos de mão de obra.                                |
| JobInvolvement           | Mede o envolvimento do funcionário em seu trabalho, o que pode influenciar a satisfação geral e a retenção.                               |
| JobLevel                 | Indica o nível do funcionário dentro da organização, relevante para análises de hierarquia e promoção.                                    |
| JobRole                  | Especifica o cargo do funcionário, facilitando análises de atrito e fatores de satisfação específicos por função.                         |
| JobSatisfaction          | Reflete o nível de satisfação do funcionário com seu trabalho, um indicador crucial para retenção.                                        |
| MaritalStatus            | Descreve o estado civil do funcionário, que pode se relacionar com satisfação no trabalho e equilíbrio entre vida pessoal e profissional. |
| MonthlyIncome            | Ganhos mensais totais do funcionário, importante para análises financeiras e benchmarking salarial.                                       |
| MonthlyRate              | Representa a taxa de pagamento mensal do funcionário, relevante para folha de pagamento e orçamento.                                      |
| NumCompaniesWorked       | Indica o número de empresas em que o funcionário trabalhou anteriormente, podendo informar tendências de rotatividade.                    |
| Over18                   | Identifica se o funcionário é maior de 18 anos, significativo para considerações legais e de conformidade.                                |
| OverTime                 | Indica se o funcionário realiza horas extras, impactando satisfação no trabalho e equilíbrio de vida.                                     |
| PercentSalaryHike        | Representa o percentual de aumento salarial, útil para avaliações de desempenho e retenção.                                               |
| PerformanceRating        | Indica a avaliação de desempenho do funcionário, essencial para entender produtividade e desenvolvimento de carreira.                     |
| RelationshipSatisfaction | Mede a satisfação do funcionário com seus relacionamentos no trabalho, importante para moral e retenção.                                  |
| StandardHours            | Representa as horas padrão que o funcionário deve trabalhar, útil para análise de jornada e horas extras.                                 |
| StockOptionLevel         | Indica o nível de opções de ações disponíveis ao funcionário, relevante para estratégias de compensação e retenção.                       |
| TotalWorkingYears        | Reflete o total de anos de experiência profissional do funcionário.                                                                       |
| TrainingTimesLastYear    | Indica quantas vezes o funcionário participou de treinamentos no último ano, relacionado ao desenvolvimento de habilidades.               |
| WorkLifeBalance          | Mede a percepção do funcionário sobre equilíbrio entre vida pessoal e profissional, podendo influenciar o turnover.                       |
| YearsAtCompany           | Representa o número de anos que o funcionário está na empresa, importante para análise de permanência.                                    |
| YearsInCurrentRole       | Indica há quanto tempo o funcionário está na posição atual, relevante para planejamento de sucessão.                                      |
| YearsSinceLastPromotion  | Representa o número de anos desde a última promoção do funcionário, útil para análises de desenvolvimento de carreira.                    |
| YearsWithCurrManager     | Rastreia há quantos anos o funcionário trabalha com o gerente atual, podendo impactar satisfação e retenção.                              |
| _rescued_data            | Contém dados adicionais capturados durante ingestão que podem exigir validação ou tratamento adicional.                                   |
