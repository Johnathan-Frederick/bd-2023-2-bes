### Exercícios

Seja o banco de dados de uma empresa varejista, em que há a relação PRODUTO com o seguinte esquema:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**PRODUTO (<ins>CodProduto</ins>, Nome, PrecoUnitario)**<br>
Suponha que há dezenas de preços unitários distintos nos produtos que a empresa vende.

1. Escreva em SQL, use subconsulta(s) independente(s):<br>
_Qual o código e o nome dos produtos que possuem os **N** preços unitários mais caros_?<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**N** é o número de letras do seu primeiro nome.<br>
Por exemplo, se o seu primeiro nome for 'Maria':<br>
&#8718; _Qual o código e o nome dos produtos que possuem os cinco preços unitários mais caros_?

~~~SQL
SELECT CodProduto, Nome
FROM PRODUTO
WHERE PrecoUnitario IN(
  SELECT DISTINCT PrecoUnitario
  FROM PRODUTO
  ORDER BY PrecoUnitario DESC
  LIMIT 5
  )
~~~

2. Escreva em SQL, use subconsulta(s) correlata(s):<br>
_Qual o código e o nome dos produtos que possuem os **N** preços unitários mais baratos_?<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**N** é o número de letras do seu primeiro nome.<br>
Por exemplo, se o seu primeiro nome for 'Maria', então:<br>
&#8718; _Qual o código e o nome dos produtos que possuem os cinco preços unitários mais baratos_?

~~~SQL
SELECT P1.CodProduto, P1.Nome
FROM PRODUTO AS P1
WHERE 5 > (
  SELECT COUNT(P2.PrecoUnitario)
  FROM PRODUTO AS P2
  WHERE P1.PrecoUnitario > P2.PrecoUnitario
  )
~~~
