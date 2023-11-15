### Exercício 1

Veja o conteúdo do arquivo [empresa.sql](../data/empresa.sql):
- O conteúdo do arquivo possui comandos para a **definição** (criação das estruturas de dados) e **construção** (carga inicial) do **BD Empresa**.
- Há comandos DDL da SQL: CREATE TABLE e ALTER TABLE.
- Há comandos DML da SQL: INSERT.

Vamos executar o conteúdo do arquivo [empresa.sql](../data/empresa.sql), tal que possamos ter um banco de dados em nosso estudo sobre a SQL. Os passos abaixo se referem à ferramenta _SQLiteOnline_, entretanto você pode usar outra ferramenta de sua preferência.

1. Iniciar a _interface_ em https://sqliteonline.com/.
1. Selecionar um SGBD: **MariaDB** ou **PostgreSQL**.
1. Conectar-se ao SGBD selecionado (clique em **_click to connect_**).
1. Copiar o conteúdo do arquivo [empresa.sql](../data/empresa.sql) e colar na área de comandos SQL (parte central da _interface_).
1. Clicar em **&#x27A4;Run** (no _menu_ superior), para executar o conteúdo do arquivo.
1. Checar no menu à esquerda (no SGBD selecionado) se as relações (tabelas) do **BD Empresa** foram criadas.
1. Limpar a área de comandos SQL (parte central da _interface_).

Pronto, o **BD Empresa** foi criado e está pronto para ser manipulado (usado).<br>
**Qual o conteúdo de cada relação (tabela)?**
- Para cada relação do **BD Empresa**, execute o comando SQL<br>&nbsp;&nbsp;&nbsp;&nbsp;**SELECT * FROM _<nome_relação>_;**
  - substitua _<nome_relação>_ por:
    - FUNCIONARIO, DEPARTAMENTO, LOCALIZACAO_DEP, PROJETO, TRABALHA_EM, DEPENDENTE.

Este é o conteudo presente no arquivo empresa.sql:
~~~sql
CREATE TABLE FUNCIONARIO (
  Pnome VARCHAR(20) NOT NULL,
  Minicial CHAR(1) NOT NULL,
  Unome VARCHAR(20) NOT NULL,
  Cpf CHAR(11) NOT NULL,
  Datanasc DATE NOT NULL,
  Endereco VARCHAR(40) NOT NULL,
  Sexo CHAR(1) NOT NULL,
  Salario numeric(20,2) NOT NULL,
  Cpf_supervisor CHAR(11) NULL,
  Dnr INT NOT NULL,
  PRIMARY KEY (Cpf)
);

CREATE TABLE DEPARTAMENTO (
  Dnome VARCHAR(20) NOT NULL,
  Dnumero INT NOT NULL,
  Cpf_gerente CHAR(11) NOT NULL,
  Data_inicio_gerente DATE NOT NULL,
  PRIMARY KEY (Dnumero),
  UNIQUE(Dnome),
  FOREIGN KEY (Cpf_gerente)          -- Restrição de Integridade Referencial
    REFERENCES FUNCIONARIO(Cpf)
);

CREATE TABLE LOCALIZACAO_DEP (
  Dnumero INT NOT NULL,
  Dlocal VARCHAR(20) NOT NULL,
  PRIMARY KEY (Dnumero, Dlocal),
  FOREIGN KEY(Dnumero)              -- Restrição de Integridade Referencial
    REFERENCES DEPARTAMENTO(Dnumero)
);

CREATE TABLE PROJETO (
  Projnome VARCHAR(20) NOT NULL,
  Projnumero INT NOT NULL,
  Projlocal VARCHAR(20) NOT NULL,
  Dnum INT NOT NULL,
  PRIMARY KEY (Projnumero),
  UNIQUE (Projnome),
  FOREIGN KEY (Dnum)                      -- Restrição de Integridade Referencial
    REFERENCES DEPARTAMENTO (Dnumero)
);

CREATE TABLE TRABALHA_EM (
Fcpf CHAR(11) NOT NULL,
Pnr INT NOT NULL,
Horas numeric(3,1) NULL,
PRIMARY KEY(Fcpf,Pnr),
FOREIGN KEY (Fcpf)                      -- Restrição de Integridade Referencial
  REFERENCES FUNCIONARIO (Cpf),
FOREIGN KEY (Pnr)
  REFERENCES PROJETO(Projnumero)        -- Restrição de Integridade Referencial
);

CREATE TABLE DEPENDENTE (
Fcpf CHAR(11) NOT NULL,
Nome_dependente VARCHAR(20) NOT NULL,
Sexo CHAR(1) NOT NULL,
Datanasc DATE NOT NULL,
Parentesco VARCHAR(7) NOT NULL,
PRIMARY KEY(Fcpf, Nome_dependente),
FOREIGN KEY (Fcpf)                    -- Restrição de Integridade Referencial
  REFERENCES FUNCIONARIO (Cpf)
);

INSERT INTO FUNCIONARIO VALUES('Joao', 'B', 'Silva', '12345678966', '1965-01-09', 'Rua das Flores, 751, Sao Paulo, SP', 'M', '30000', '33344555587', '5');
INSERT INTO FUNCIONARIO VALUES('Fernando', 'T', 'Wong', '33344555587', '1955-12-08', 'Rua da Lapa, 34, Sao Paulo, SP', 'M', '40000', '88866555576', '5');
INSERT INTO FUNCIONARIO VALUES('Alice', 'J', 'Zelaya', '99988777767', '1968-01-19', 'Rua Souza Lima, 54, Curtiba, PR', 'F', '25000', '98765432168', '4');
INSERT INTO FUNCIONARIO VALUES('Jeniffer', 'S', 'Souza', '98765432168', '1941-06-20', 'Av. Arthur de Lima, 54, Santo André, SP', 'F', '43000', '88866555576', '4');
INSERT INTO FUNCIONARIO VALUES('Ronaldo', 'K', 'Lima', '66688444476', '1962-09-15', 'Rua Reboucas, 65, Piracicaba, SP', 'M', '38000', '33344555587', '5');
INSERT INTO FUNCIONARIO VALUES('Joice', 'A', 'Leite', '45345345376', '1972-07-31', 'Av. Lucas Obes, 74, Sao Paulo, SP', 'F', '25000', '33344555587', '5');
INSERT INTO FUNCIONARIO VALUES('Andre', 'V', 'Pereira', '98798798733', '1969-03-29', 'Rua Timbira, 35, Sao Paulo, SP', 'M', '25000', '98765432168', '4');
INSERT INTO FUNCIONARIO VALUES('Jorge', 'E', 'Brito', '88866555576', '1937-11-10', 'Rua do Horto, 35, Sao Paulo, SP', 'M', '55000', NULL, '1');

INSERT INTO DEPARTAMENTO VALUES('Pesquisa', '5', '33344555587', '1988-05-22');
INSERT INTO DEPARTAMENTO VALUES('Administracao', '4', '98765432168', '1995-01-01');
INSERT INTO DEPARTAMENTO VALUES('Matriz', '1', '88866555576', '1981-06-19');

ALTER TABLE FUNCIONARIO
ADD CONSTRAINT FUNCIONARIO_FK_TRABALHA_PARA
FOREIGN KEY(Dnr) REFERENCES DEPARTAMENTO(Dnumero);

ALTER TABLE FUNCIONARIO
ADD CONSTRAINT FUNCIONARIO_FK_SUPERVISAO
FOREIGN KEY (Cpf_supervisor) REFERENCES FUNCIONARIO(Cpf);

INSERT INTO LOCALIZACAO_DEP VALUES('1', 'Sao Paulo');
INSERT INTO LOCALIZACAO_DEP VALUES('4', 'Maua');
INSERT INTO LOCALIZACAO_DEP VALUES('5', 'Santo Andre');
INSERT INTO LOCALIZACAO_DEP VALUES('5', 'Itu');
INSERT INTO LOCALIZACAO_DEP VALUES('5', 'Sao Paulo');

INSERT INTO PROJETO VALUES('ProdutoX', '1', 'Santo Andre', '5');
INSERT INTO PROJETO VALUES('ProdutoY', '2', 'Itu', '5');
INSERT INTO PROJETO VALUES('ProdutoZ', '3', 'Sao Paulo', '5');
INSERT INTO PROJETO VALUES('Informatizacao', '10', ' Maua', '4');
INSERT INTO PROJETO VALUES('Reorganizacao', '20', 'Sao Paulo', '1');
INSERT INTO PROJETO VALUES('Novosbeneficios', '30', 'Maua', '4');

INSERT INTO DEPENDENTE VALUES('33344555587', 'Alicia', 'F', '1986-04-05', 'Filha');
INSERT INTO DEPENDENTE VALUES('33344555587', 'Tiago', 'M', '1983-10-25', 'Filho');
INSERT INTO DEPENDENTE VALUES('33344555587', 'Janaina', 'F', '1958-05-03', 'Esposa');
INSERT INTO DEPENDENTE VALUES('98765432168', 'Antonio', 'M', '1942-02-28', 'Marido');
INSERT INTO DEPENDENTE VALUES('12345678966', 'Michael', 'M', '1988-01-04', 'Filho');
INSERT INTO DEPENDENTE VALUES('12345678966', 'Alicia', 'F', '1988-12-30', 'Filha');
INSERT INTO DEPENDENTE VALUES('12345678966', 'Elizabeth', 'F', '1967-05-05', 'Esposa');

INSERT INTO TRABALHA_EM VALUES('12345678966', '1', '32.5');
INSERT INTO TRABALHA_EM VALUES('12345678966', '2', '7.5');
INSERT INTO TRABALHA_EM VALUES('66688444476', '3', '40.0');
INSERT INTO TRABALHA_EM VALUES('45345345376', '1', '20.0');
INSERT INTO TRABALHA_EM VALUES('45345345376', '2', '20.0');
INSERT INTO TRABALHA_EM VALUES('33344555587', '2', '10.0');
INSERT INTO TRABALHA_EM VALUES('33344555587', '3', '10.0');
INSERT INTO TRABALHA_EM VALUES('33344555587', '10', '10.0');
INSERT INTO TRABALHA_EM VALUES('33344555587', '20', '10.0');
INSERT INTO TRABALHA_EM VALUES('99988777767', '30', '30.0');
INSERT INTO TRABALHA_EM VALUES('99988777767', '10', '10.0');
INSERT INTO TRABALHA_EM VALUES('98798798733', '10', '35.0');
INSERT INTO TRABALHA_EM VALUES('98798798733', '30', '5.0');
INSERT INTO TRABALHA_EM VALUES('98765432168', '30', '20.0');
INSERT INTO TRABALHA_EM VALUES('98765432168', '20', '15.0');
INSERT INTO TRABALHA_EM VALUES('88866555576', '20', NULL);
~~~

### Exercício 2

Seja o arquivo [agricultura.relax](../data/agricultura.relax), para a criação de um _dataset_ na ferramente _RelaX_, referente ao **BD Agricultura**.

Baseado no conteúdo do arquivo [agricultura.relax](../data/agricultura.relax):
1. Escreva em DDL a definição do **BD Agricultura**:
   - Incluir as restrições de integridade de chave, integridade de domínio, integridade de entidade e integridade referencial.
   - Os comandos DDL devem ser executáveis no SGBD PostgreSQL.
2. Escreva em álgebra relacional a consulta "que produtos estão entre os três preços por quilo mais elevados":
   - Não utilize funções agregadas, agrupamento, e consultas aninhadas.

### Exercício 3

Seja o arquivo [photodb.relax](../data/photodb.relax), para a criação de um _dataset_ na ferramente _RelaX_, referente ao **BD Fotografia**.

Baseado no conteúdo do arquivo [photodb.relax](../data/photodb.relax):
1. Escreva em DDL a definição do **BD Fotografia**:
   - Incluir as restrições de integridade de chave, integridade de domínio, integridade de entidade e integridade referencial.
   - Os comandos DDL devem ser executáveis no SGBD PostgreSQL.
