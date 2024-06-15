# desafio_powerbi_analytics
Projeto feito para conclusao do curso de Python data analytics

## Algumas Queries utilizadas

#Verificação de valores nulos

SELECT * FROM employee WHERE Fname IS NULL OR Lname IS NULL OR Ssn IS NULL OR Dno IS NULL;
SELECT * FROM departament WHERE Dname IS NULL OR Dnumber IS NULL OR Mgr_ssn IS NULL;
SELECT * FROM dept_locations WHERE Dnumber IS NULL OR Dlocation IS NULL;
SELECT * FROM project WHERE Pname IS NULL OR Pnumber IS NULL OR Dnum IS NULL;
SELECT * FROM works_on WHERE Essn IS NULL OR Pno IS NULL OR Hours IS NULL;
SELECT * FROM dependent WHERE Essn IS NULL OR Dependent_name IS NULL;

#Selecionar colaboradores que não possuem gerente, excluindo os gerentes
SELECT e.*
FROM employee e
LEFT JOIN departament d ON e.Ssn = d.Mgr_ssn
WHERE e.Super_ssn IS NULL
AND d.Mgr_ssn IS NULL;


# Selecionar departamentos que não possuem gerente 
SELECT *
FROM departament d
LEFT JOIN employee e ON d.Mgr_ssn = e.Ssn
WHERE e.Ssn IS NULL;


## Verificar o número total de horas trabalhadas em cada projeto
SELECT Pno, SUM(Hours) AS Total_Hours
FROM works_on
GROUP BY Pno;

# Criar a tabela combinada com informações dos empregados e nomes dos departamentos
SELECT 
    e.Fname,
    e.Minit,
    e.Lname,
    e.Ssn,
    e.Bdate,
    e.Address,
    e.Sex,
    e.Salary,
    e.Super_ssn,
    e.Dno,
    d.Dname AS Department_Name
FROM 
    employee e
LEFT JOIN 
    departament d ON e.Dno = d.Dnumber;

# Criar a tabela combinada com informações dos empregados e nomes dos gerentes
SELECT 
    e.Fname AS Employee_Fname,
    e.Minit AS Employee_Minit,
    e.Lname AS Employee_Lname,
    e.Ssn AS Employee_Ssn,
    e.B

Mescla de departamentos e localizaçoes feita no Power BI



