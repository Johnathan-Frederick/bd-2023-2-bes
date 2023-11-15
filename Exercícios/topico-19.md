### Exercício

1. Baseado na [ilustração do BD Empresa](../media/fig-mr-2.jpg), escreva em SQL a consulta:<br>
Para cada dependente, apresente o nome do dependente e o primeiro e último nomes do funcionário responsável pelo dependente, mas restrito aos dependentes em que:
- as duas primeiras letras do primeiro nome do dependente ou do empregado responsável são as mesmas do seu primeiro nome (se refere a você, que é discente da disciplina), e
- as duas últimas letras do primeiro nome do dependente ou do empregado responsável são as mesmas do seu primeiro nome (se refere a você, que é discente da disciplina), e
- o tamanho do primeiro nome do dependente ou do empregado responsável é o mesmo que o tamanho do seu primeiro nome (se refere a você, que é discente da disciplina) 
- obs.: use a função **CHAR_LENGTH(att)** para calcular o tamanho da cadeia (valor) para o atributo _att_.

