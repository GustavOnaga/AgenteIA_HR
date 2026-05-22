## 📊 Metricas de SQL

### Quantidade de funcionarios
- Synonyms: headcount, quantidade de profissionais
```sql
count(distinct hr.hr_employee_attrition.EmployeeNumber) as headcount
```

### Quantidade de funcionario ativos
- Synonyms: Headcount Ativo
```sql
count(distinct hr_employee_attrition.EmployeeNumber) filter(where hr_employee_attrition.Attrition = 'No') as headcountAtivo
```

### Quantidade de funcionarios desligados
- Synonyms: Headcount inativo
```sql
count(distinct hr_employee_attrition.EmployeeNumber) filter(where hr_employee_attrition.Attrition = 'Yes') as headcountAtivo
```

### Turnover
- Synonyms: rotatividade
```sql
count(distinct hr_employee_attrition.EmployeeNumber) filter(where hr_employee_attrition.Attrition = 'Yes') 
/count(distinct hr_employee_attrition.EmployeeNumber)
```
