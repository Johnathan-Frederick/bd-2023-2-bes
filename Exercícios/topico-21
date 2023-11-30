### Exercícios

1. Seja o comando SQL:<br>&nbsp;&nbsp;SELECT Salario<br>&nbsp;&nbsp;FROM FUNCIONARIO<br>&nbsp;&nbsp;WHERE Salario >= 13000 + ( SELECT MIN(Salario) FROM FUNCIONARIO )<br>Considere que na relação FUNCIONARIO:<br>■ há 4 (quatro) _tuplas_;<br>■ os salários 10000, 20000, 30000, 25000.<br>Qual a soma dos salários que são retornados pela consulta?

1. Seja o comando SQL:<br>
SELECT Salario FROM FUNCIONARIO WHERE Salario > <br>
&nbsp;&nbsp;( SELECT MIN(Salario) FROM FUNCIONARIO WHERE Salario < <br>
&nbsp;&nbsp;&nbsp;&nbsp;( SELECT MAX(Salario) FROM FUNCIONARIO WHERE Salario < <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;( SELECT MAX(Salario) FROM FUNCIONARIO ) ) ) <br>

Se a relação FUNCIONARIO possui 6 (seis) valores distintos de salário, então '_Salário 1_' é o menor salário e '_Salário 6_' é o maior salário. Some as sentenças verdadeiras:<br>(01) **Salário 1** está no resultado da consulta.<br>(02) **Salário 2** está no resultado da consulta.<br>(04) **Salário 3** está no resultado da consulta.<br>(08) **Salário 4** está no resultado da consulta.<br>(16) **Salário 5** está no resultado da consulta.<br>(32) **Salário 6** está no resultado da consulta.
