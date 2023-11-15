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

'''sql

'''

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
