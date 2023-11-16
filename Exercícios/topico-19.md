### Exercício

1. Baseado na [ilustração do BD Empresa](../media/fig-mr-2.jpg), escreva em SQL a consulta:<br>
Para cada dependente, apresente o nome do dependente e o primeiro e último nomes do funcionário responsável pelo dependente, mas restrito aos dependentes em que:
- as duas primeiras letras do primeiro nome do dependente ou do empregado responsável são as mesmas do seu primeiro nome (se refere a você, que é discente da disciplina), e
~~~sql
SELECT nome_dependente,pnome,unome
	FROM (funcionario AS F JOIN dependente AS D ON F.cpf = D.fcpf)
		WHERE (D.nome-dependente LIKE 'Jo%' OR F.pnome LIKE 'Jo%')

~~~

- as duas últimas letras do primeiro nome do dependente ou do empregado responsável são as mesmas do seu primeiro nome (se refere a você, que é discente da disciplina), e
~~~sql
SELECT nome_dependente,pnome,unome
	FROM (funcionario AS F JOIN dependente AS D ON F.cpf = D.fcpf)
		WHERE (D.nome-dependente LIKE 'Jo%' OR F.pnome LIKE 'Jo%')
			AND (D.nome_dependente LIKE '%an' OR F.pnome LIKE '%an')
~~~
- o tamanho do primeiro nome do dependente ou do empregado responsável é o mesmo que o tamanho do seu primeiro nome (se refere a você, que é discente da disciplina) 
~~~sql
SELECT D.nome_dependente, F.pnome, F.unome
	FROM funcionario AS F JOIN dependente AS D ON F.cpf = D.fcpf
	WHERE (D.nome_dependente LIKE 'Jo%' OR F.pnome LIKE 'Jo%')
		AND (D.nome_dependente LIKE '%an' OR F.pnome LIKE '%an')
		AND (CHAR_LENGTH(D.nome_dependente) = CHAR_LENGTH('Jonathan') OR CHAR_LENGTH(F.pnome) = CHAR_LENGTH('Jonathan'));
~~~
- obs.: use a função **CHAR_LENGTH(att)** para calcular o tamanho da cadeia (valor) para o atributo _att_.
