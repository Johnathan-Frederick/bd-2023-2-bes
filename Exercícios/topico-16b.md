Escreva em álgebra relacional as seguintes consultas:

1. Qual o nome dos projetos que o funcionário "João B Silva" trabalha em?<br>
~~~relax
DadosJ = σ Pnome='Joao'∧Minicial='B'∧Unome='Silva' (FUNCIONARIO)
DADOS = DadosJ ⨝Cpf=Fcpf (TRABALHA_EM ⨝Pnr=Projnumero PROJETO)
π Projnome DADOS
~~~
2. Qual o nome das pessoas que trabalham em pelo menos um dos projetos que o funcionário "João B Silva" trabalha em?<br>
~~~relax
DadosJ = σ Pnome='Joao'∧Minicial='B'∧Unome='Silva' (FUNCIONARIO ⨝Cpf=Fcpf TRABALHA_EM)
Dados = FUNCIONARIO ⨝Cpf=Fcpf (TRABALHA_EM)

DJ = ρDJ DadosJ
D = ρ D Dados

RESULT = D ⨝D.Pnr=DJ.Pnr DJ
πD.Pnome,D.Unome RESULT
~~~
1. Qual o nome das pessoas que não trabalham em qualquer dos projetos que o funcionário "João B Silva" trabalha em? Pessoas que não trabalham em qualquer projeto ESTÃO INCLUÍDAS no resultado da consulta.<br>
1. Qual o nome das pessoas em que todos os projetos que trabalham em estão entre os projetos que o funcionário "João B Silva" trabalha em? Pessoas que não trabalham em qualquer projeto NÃO ESTÃO INCLUÍDAS no resultado da consulta.<br>
