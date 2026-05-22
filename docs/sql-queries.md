## 📊 SQL Queries

Exemplos de perguntas e queries que o agende deve utilizar como aprendizado.

### Me retorne a quantidade de headcount da empresa

```sql
select 
    count(distinct EmployeeNumber)
from workspace.hr.hr_employee_attrition
```

### Preciso da quantidade de funcionario que estão ativos, e que apresentam um nivel de satisfação maior que 2
```sql
select 
    count(distinct EmployeeNumber)
from workspace.hr.hr_employee_attrition
where Attrition = 'Yes'
and RelationshipSatisfaction > 2;
```

### me forneça a quantidade de profissionais ativos, distribuidos pela distancia do trabalho. Faça a visão em agrupando a distancia em 10 e 10
```sql
SELECT
  CASE
    WHEN `DistanceFromHome` BETWEEN 0 AND 9 THEN '0-9 km'
    WHEN `DistanceFromHome` BETWEEN 10 AND 19 THEN '10-19 km'
    WHEN `DistanceFromHome` BETWEEN 20 AND 29 THEN '20-29 km'
    WHEN `DistanceFromHome` >= 30 THEN '30+ km'
  END as faixa_distancia,
  COUNT(DISTINCT `EmployeeNumber`) as quantidade_profissionais_ativos
FROM
  `workspace`.`hr`.`hr_employee_attrition`
WHERE
  `Attrition` = 'No'
GROUP BY
  faixa_distancia
ORDER BY
  faixa_distancia
  ```


