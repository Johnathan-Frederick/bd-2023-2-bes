### Exercícios

1. Em consultas escritas em SQL, quando há pelo menos um NULL no predicado da cláusula WHERE, o resultado da avaliação é "desconhecido" (exceto quando são explicitamente empregados IS NULL ou IS NOT NULL); por exemplo, o resultado da avaliação de **(3 + NULL > 7)** é "desconhecido". Portanto, "verdadeiro", "falso" e "desconhecido" são os resultados possíveis na avaliação de predicados da cláusula WHERE. A regra geral é que são selecionadas apenas as combinações de _tuplas_ em que o predicado é avaliado como “verdadeiro”. Seja a relação R que possui quatro tuplas – (12, 15, 5100), (13, NULL, 3500), (14, NULL, NULL) e (15, 12, NULL) – em que o primeiro, o segundo e o terceiro valores em cada _tupla_ referem-se aos atributos **at1**, **at2** e **at3**, respectivamente. Os comandos a seguir representam consultas sobre R:<br>
&nbsp;&nbsp;&nbsp;&nbsp;(C1) SELECT * FROM R WHERE (at2<12) OR (at3<3000)<br>
&nbsp;&nbsp;&nbsp;&nbsp;(C2) SELECT * FROM R WHERE (at2>12) OR NOT (at2>12)<br>
&nbsp;&nbsp;&nbsp;&nbsp;(C3) SELECT * FROM R WHERE (NOT at2<at2) AND (at3>at2)<br>
A quantidade de _tuplas_ retornadas pelas execuções dos comandos (C1), (C2) e (C3), respectivamente, é:<br>
&nbsp;&nbsp;(a) zero, um e dois.<br>
&nbsp;&nbsp;(b) um, dois e um.<br>
&nbsp;&nbsp;(c) um, dois, dois.<br>
&nbsp;&nbsp;(d) zero, dois e dois.<br>
&nbsp;&nbsp;(e) dois, dois e um.<br>

2. A partir da [*ilustração para o BD Empresa*](../media/fig-mr-2.jpg), escreva a seguinte consulta em SQL (use JUNÇÃO EXTERNA):<br>
_Para cada funcionário, liste o primeiro nome e o último nome e, se o funcionário tiver dependentes, liste também o nome dos seus dependentes_.
~~~sql
SELECT pnome,unome, nome_dependente
FROM funcionario RIGHT JOIN 
	(SELECT fcpf,nome_dependente FROM
     dependente) ON cpf=fcpf
~~~
