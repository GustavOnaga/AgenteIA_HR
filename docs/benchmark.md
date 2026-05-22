## Benchmark de Perguntas — HR Analytics AI Agent

Este documento contém exemplos de perguntas analíticas utilizadas para validação do agente de IA especializado em dados de RH.

---

### 1. Funcionários com mais tempo de empresa possuem menor turnover?

```sql
SELECT
  CASE
    WHEN YearsAtCompany < 2 THEN '0-1 anos'
    WHEN YearsAtCompany BETWEEN 2 AND 5 THEN '2-5 anos'
    WHEN YearsAtCompany BETWEEN 6 AND 10 THEN '6-10 anos'
    ELSE '10+ anos'
  END AS tenure_group,
  COUNT(*) AS total_employees,
  SUM(
    CASE
      WHEN Attrition = 'Yes' THEN 1
      ELSE 0
    END
  ) AS attrition_count,
  ROUND(
    100.0
      * SUM(
        CASE
          WHEN Attrition = 'Yes' THEN 1
          ELSE 0
        END
      )
      / COUNT(DISTINCT EmployeeNumber),
    2
  ) AS turnover_rate
FROM
  hr.hr_employee_attrition
GROUP BY
  tenure_group
ORDER BY
  turnover_rate DESC;
```

---

### 2. Qual departamento possui mais funcionários?

```sql
SELECT
  Department,
  COUNT(DISTINCT EmployeeNumber) AS total_attrition
FROM
  hr.hr_employee_attrition
GROUP BY
  Department
ORDER BY
  total_attrition DESC
LIMIT 1;
```

---

### 3. Funcionários com baixo work-life balance possuem maior turnover?

```sql
SELECT
  `WorkLifeBalance`,
  try_divide(
    COUNT(DISTINCT
      CASE
        WHEN `Attrition` = 'Yes' THEN `EmployeeNumber`
      END
    )
      * 1.0,
    COUNT(DISTINCT `EmployeeNumber`)
  ) AS turnover_rate
FROM
  `workspace`.`hr`.`hr_employee_attrition`
WHERE
  `WorkLifeBalance` IS NOT NULL
GROUP BY
  `WorkLifeBalance`
ORDER BY
  `WorkLifeBalance`;
```

---

### 4. Qual nível de cargo possui maior turnover?

```sql
SELECT
  JobLevel,
  ROUND(
    100.0
      * SUM(
        CASE
          WHEN Attrition = 'Yes' THEN 1
          ELSE 0
        END
      )
      / COUNT(DISTINCT EmployeeNumber),
    2
  ) AS turnover_rate
FROM
  hr.hr_employee_attrition
GROUP BY
  JobLevel
ORDER BY
  turnover_rate DESC
LIMIT 1;
```

---

### 5. Qual departamento possui maior salário médio?

```sql
WITH ranked_departments AS (
  SELECT
    Department,
    AVG(MonthlyIncome) AS avg_salary,
    RANK() OVER (ORDER BY AVG(MonthlyIncome) DESC) AS rnk
  FROM
    `workspace`.`hr`.`hr_employee_attrition`
  WHERE
    Department IS NOT NULL
    AND MonthlyIncome IS NOT NULL
  GROUP BY
    Department
)
SELECT
  Department,
  avg_salary
FROM
  ranked_departments
WHERE
  rnk = 1;
```

---

### 6. Qual faixa etária possui maior número de desligamentos? Faça o agrupamento começando em até 20, depois em faixas de 5 e em 5 anos, finalizando acima de 65 anos. 

```sql
SELECT
  CASE
    WHEN Age <= 20 THEN 'Menos de 20'
    WHEN Age BETWEEN 20 AND 25 THEN '20-25'
    WHEN Age BETWEEN 25 AND 30 THEN '25-30'
    WHEN Age BETWEEN 30 AND 35 THEN '30-35'
    WHEN Age BETWEEN 35 AND 40 THEN '35-40'
    WHEN Age BETWEEN 40 AND 45 THEN '40-45'
    WHEN Age BETWEEN 45 AND 50 THEN '45-50'
    WHEN Age BETWEEN 50 AND 55 THEN '50-55'
    WHEN Age BETWEEN 55 AND 60 THEN '55-60'
    WHEN Age BETWEEN 60 AND 65 THEN '60-65'
    ELSE '65+'
  END AS age_group,
  COUNT(DISTINCT EmployeeNumber) AS attrition_count
FROM
  hr.hr_employee_attrition
WHERE
  Attrition = 'Yes'
GROUP BY
  age_group
ORDER BY
  attrition_count DESC
LIMIT 1;
```

---

### 7. Funcionários que fazem hora extra possuem maior turnover?

```sql
SELECT
  OverTime,
  try_divide(
    COUNT(DISTINCT EmployeeNumber)
      FILTER ( WHERE Attrition = 'Yes' )
      * 1.0,
    COUNT(DISTINCT EmployeeNumber)
  ) AS turnover
FROM
  `workspace`.`hr`.`hr_employee_attrition`
WHERE
  OverTime IS NOT NULL
  AND Attrition IS NOT NULL
GROUP BY
  OverTime
```

---

### 8.  Existe diferença de turnover entre homens e mulheres?

```sql
SELECT
  Gender,
  try_divide(
    COUNT(DISTINCT EmployeeNumber)
      FILTER ( WHERE Attrition = 'Yes' )
      * 1.0,
    COUNT(DISTINCT EmployeeNumber)
  ) AS turnover
FROM
  workspace.hr.hr_employee_attrition
WHERE
  Gender IS NOT NULL
  AND Attrition IS NOT NULL
GROUP BY
  Gender;
```

---

### 9. Qual cargo possui maior número de desligamentos?

```sql
SELECT
  JobRole,
  COUNT(DISTINCT EmployeeNumber) AS total_attrition
FROM
  hr.hr_employee_attrition
WHERE
  Attrition = 'Yes'
GROUP BY
  JobRole
ORDER BY
  total_attrition DESC
limit 1;
```

---

### 10. Preciso do turnover médio

```sql
SELECT
  try_divide(
    count(distinct `EmployeeNumber`)
      FILTER ( WHERE `Attrition` = 'Yes' )
      * 1.0,
    count(distinct `EmployeeNumber`)
  ) AS turnover_medio
FROM
  `workspace`.`hr`.`hr_employee_attrition`
```
