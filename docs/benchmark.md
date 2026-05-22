## Benchmark de Perguntas — HR Analytics AI Agent

Este documento contém exemplos de perguntas analíticas utilizadas para validação do agente de IA especializado em dados de RH.

---

### 1. Preciso do turnover médio

```sql
SELECT
  try_divide(
    count(distinct `EmployeeNumber`)
      FILTER ( WHERE `Attrition` = 'Yes' )
      * 1.0,
    count(distinct `EmployeeNumber`)
  ) AS turnover_medio
FROM
  `workspace`.`hr`.`hr_employee_attrition`;
```

---

### 2. Qual cargo possui maior número de desligamentos?

```sql
SELECT
    JobRole,
    COUNT(DISTINCT EmployeeNumber) AS total_attrition
FROM hr.hr_employee_attrition
WHERE Attrition = 'Yes'
GROUP BY JobRole
ORDER BY total_attrition DESC;
```

---

### 3. Existe diferença de turnover entre homens e mulheres?

```sql
SELECT
    Gender,
    COUNT(*) AS total_employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS attrition_count,
    ROUND(
        100.0 * SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(DISTINCT EmployeeNumber),
        2
    ) AS turnover_rate
FROM hr.hr_employee_attrition
GROUP BY Gender;
```

---

### 4. Funcionários que fazem hora extra possuem maior turnover?

```sql
SELECT
    OverTime,
    COUNT(*) AS total_employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS attrition_count,
    ROUND(
        100.0 * SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) /  COUNT(DISTINCT EmployeeNumber),
        2
    ) AS turnover_rate
FROM hr.hr_employee_attrition
GROUP BY OverTime;
```

---

### 5. Qual faixa etária possui maior número de desligamentos?

```sql
SELECT
    CASE
        WHEN Age < 30 THEN 'Menos de 30'
        WHEN Age BETWEEN 30 AND 39 THEN '30-39'
        WHEN Age BETWEEN 40 AND 49 THEN '40-49'
        ELSE '50+'
    END AS age_group,
    COUNT(DISTINCT EmployeeNumber) AS attrition_count
FROM hr.hr_employee_attrition
WHERE Attrition = 'Yes'
GROUP BY age_group
ORDER BY attrition_count DESC;
```

---

### 6. Qual departamento possui maior salário médio?

```sql
SELECT
    Department,
    ROUND(AVG(MonthlyIncome), 2) AS avg_salary
FROM hr.hr_employee_attrition
GROUP BY Department
ORDER BY avg_salary DESC;
```

---

### 7. Qual nível de cargo possui maior turnover?

```sql
SELECT
    JobLevel,
    COUNT(*) AS total_employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS attrition_count,
    ROUND(
        100.0 * SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(DISTINCT EmployeeNumber),
        2
    ) AS turnover_rate
FROM hr.hr_employee_attrition
GROUP BY JobLevel
ORDER BY turnover_rate DESC;
```

---

### 8. Funcionários com baixo work-life balance possuem maior turnover?

```sql
SELECT
    WorkLifeBalance,
    COUNT(*) AS total_employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS attrition_count,
    ROUND(
        100.0 * SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(DISTINCT EmployeeNumber),
        2
    ) AS turnover_rate
FROM hr.hr_employee_attrition
GROUP BY WorkLifeBalance
ORDER BY WorkLifeBalance;
```

---

### 9. Qual área possui mais funcionários?

```sql
SELECT
    Department,
    COUNT(DISTINCT EmployeeNumber) AS headcount
FROM hr.hr_employee_attrition
GROUP BY Department
ORDER BY headcount DESC;
```

---

### 10. Funcionários com mais tempo de empresa possuem menor turnover?

```sql
SELECT
    CASE
        WHEN YearsAtCompany < 2 THEN '0-1 anos'
        WHEN YearsAtCompany BETWEEN 2 AND 5 THEN '2-5 anos'
        WHEN YearsAtCompany BETWEEN 6 AND 10 THEN '6-10 anos'
        ELSE '10+ anos'
    END AS tenure_group,
    COUNT(*) AS total_employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS attrition_count,
    ROUND(
        100.0 * SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(DISTINCT EmployeeNumber),
        2
    ) AS turnover_rate
FROM hr.hr_employee_attrition
GROUP BY tenure_group
ORDER BY turnover_rate DESC;
```
