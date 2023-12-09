### Exercício

1. Em relação ao BD Empresa, escreva em SQL a consulta "Qual o primeiro e último nomes dos funcionários que possuem dois ou mais dependentes e que trabalham em dois ou mais projetos?"<br>O comando SQL deve:<br>■ usar pelo menos uma das operações UNIÃO, INTERSEÇÃO e DIFERENÇA, necessariamente conforme a sintaxe apresentada no tópico;<br>■ usar a cláusula HAVING.

~~~SQL
SELECT F.Pnome, F.Unome
from FUNCIONARIO as F
JOIN(
	  SELECT D.Fcpf, COUNT(D.Nome_dependente) AS Qtd_Dep
    FROM DEPENDENTE AS D
    GROUP BY D.Fcpf
    HAVING COUNT(D.Nome_dependente) >= 2
	) AS D
    ON F.Cpf = D.Fcpf
JOIN(
  SELECT T.Fcpf, COUNT(T.Pnr) AS Qtd_Pnr
  FROM TRABALHA_EM AS T
  GROUP BY T.Fcpf
  HAVING COUNT(T.Pnr) >= 2
  ) AS T
  ON F.Cpf = T.Fcpf
~~~
