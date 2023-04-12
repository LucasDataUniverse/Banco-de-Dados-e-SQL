# O curso completo de Banco de Dados e SQL, sem mistérios!


---

## <a name="indice">Índice</a>
- [1 Objetivos do curso](#parte1) 
- [2 Criando o Banco de Dados e conectando ao Banco](#parte2)  
- [3 Criando a Tabela](#parte3) 



## <a name=parte1> Objetivos do curso<a>
- Entender a diferença entre um Administrador de Dados e um DBA;
- Criar bancos de dados consistentes do ponto de infraestrutura e modelagem;
- Instalar o Banco de Dados MySql;
- Executar a linguagem SQL - Structured Query Language, ou Linguagem de Consulta Estruturada em QUALQUER banco de dados;
- Entender todo o ambiente trasacional e optar por continuar seus estudos em ambientes analíticos de Business Intelligence;
- Instalar o Banco de Dados Oracle;
- Instalar o Banco de Dados SQL Server;
- Modelar a base de dados para qualquer sistema transacional;
- Programar em Banco de Dados;
- Realizar Backups e Restores dos seus Bancos de Dados;
- Aplicar Constraints de qualquer natureza em suas tabelas;
- Aplicar as Formas Normais;
- Criar Triggers, Procedures, Functions e Views;
- Escolher as funções nativas de qualquer banco de dados, de acordo com a sua necessidade;
- Utilizar o Dicionário de Dados;
- Estar seguro na disciplina Banco de Dados;
- Realizar downloads de softwares relacionados a banco de dados;
- Utilizar softwares de modelagem;
- Aplicar seguramente os relacionamentos 1 x 1 , 1 x N, N x N.


## <a name="parte2">Criando o Banco de Dados e conectando ao Banco</a>

```sql

mysql> create database projeto;
Query OK, 1 row affected (0.01 sec)

mysql> use projeto;
Database changed

```
[Voltar ao Índice](#indice)

## <a name="parte3">3 Criando a Tabela</a>

```sql

mysql> CREATE TABLE funcionarios
    -> (
    ->  idFuncionario INTEGER,
    ->  nome VARCHAR(100),
    ->  email VARCHAR(200),
    ->  sexo VARCHAR(10),
    ->  departamento VARCHAR(100),
    ->  admissao VARCHAR(10),
    ->  salario INTEGER,
    ->  cargo VARCHAR(100),
    ->  idRegiao int
    ->  );
Query OK, 0 rows affected (0.01 sec)

```
[Voltar ao Índice](#indice)