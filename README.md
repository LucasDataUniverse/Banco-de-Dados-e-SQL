# O Banco de Dados e SQL


---

## <a name="indice">Índice</a>
- [1 Objetivos do curso](#parte1) 
- [2 Criando o Banco de Dados e conectando ao Banco](#parte2)  
- [3 Criando a Tabela](#parte3) 
- [4 Descobrindo Banco de Dados e Tabelas](#parte4) 
- [5 Visualizando estrutura do Banco de Dados](#parte5) 
- [6 Sintaxe Básica de Inserção](#parte6) 
- [7 Comando Select](#parte7) 
- [8 Seleção com Where](#parte8) 
- [9 Base de conhecimento para Performace com Operadores Lógicos](#parte9) 

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


## <a name="parte4">4 Descobrindo Banco de Dados e Tabelas</a>

```sql
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| projeto            |
| sakila             |
| sys                |
| world              |
+--------------------+
7 rows in set (0.01 sec)

mysql> use projeto;
Database changed
mysql> show tables;
+-------------------+
| Tables_in_projeto |
+-------------------+
| funcionarios      |
+-------------------+
1 row in set (0.00 sec)
```
[Voltar ao Índice](#indice)

## <a name="parte5">5 Visualizando estrutura do Banco de Dados</a>

```sql
mysql> desc funcionarios;
+---------------+--------------+------+-----+---------+-------+
| Field         | Type         | Null | Key | Default | Extra |
+---------------+--------------+------+-----+---------+-------+
| idFuncionario | int          | YES  |     | NULL    |       |
| nome          | varchar(100) | YES  |     | NULL    |       |
| email         | varchar(200) | YES  |     | NULL    |       |
| sexo          | varchar(10)  | YES  |     | NULL    |       |
| departamento  | varchar(100) | YES  |     | NULL    |       |
| admissao      | varchar(10)  | YES  |     | NULL    |       |
| salario       | int          | YES  |     | NULL    |       |
| cargo         | varchar(100) | YES  |     | NULL    |       |
| idRegiao      | int          | YES  |     | NULL    |       |
+---------------+--------------+------+-----+---------+-------+
9 rows in set (0.00 sec)

```
[Voltar ao Índice](#indice)


## <a name="parte6">Sintaxe Básica de Inserção</a>

```sql
insert into funcionarios values
    -> (
    -> 1,
    -> 'Kelley',
    -> 'rkelley0@icloud.com',
    -> 'Feminino',
    -> 'Computadores',
    -> '10/2/2019',
    -> 67470,
    -> 'Structural Engineer',
    -> 2
    -> );
Query OK, 1 row affected (0.01 sec)


insert into funcionarios(idFuncionario, nome, email, sexo, departamento, admissao, salario, cargo, idRegiao)
    -> values (2,'Armstrong','sarmstrong1@infoseek.co.jp','Masculino','Esporte','3/31/2008',71869,'Financial Advisor',2);
Query OK, 1 row affected (0.01 sec)

```
[Voltar ao Índice](#indice)

## <a name="parte7">Comando Select</a>

- O Select é um comando de projeção não apenas para consultar valores em uma tabela. Com ele podemos modificar as Querys.

```sql
select now();
+---------------------+
| now()               |
+---------------------+
| 2023-04-13 09:05:24 |
+---------------------+
1 row in set (0.00 sec)

mysql> select now() as Data_Hora;
+---------------------+
| Data_Hora           |
+---------------------+
| 2023-04-13 09:06:14 |
+---------------------+
1 row in set (0.00 sec)

mysql> select idFuncionario, nome, email from funcionarios;
+---------------+-----------+----------------------------+
| idFuncionario | nome      | email                      |
+---------------+-----------+----------------------------+
|             1 | Kelley    | rkelley0@icloud.com        |
|             2 | Armstrong | sarmstrong1@infoseek.co.jp |
+---------------+-----------+----------------------------+
2 rows in set (0.00 sec)
```
[Voltar ao Índice](#indice)

## <a name="parte8">Seleção com Where</a>

- Utilizei os comandos LIKE e Where para consulta nesses exercícios.
- WHERE é onde na tabela eu quero realizar o filtro.
- LIKE ir procurar no texto do campo cargo a palavra Engineer e o % foi utilizando para indicar qualquer coisa antes da palavra Engineer.

```sql
SELECT nome, email from funcionarios
    -> WHERE sexo = 'Feminino';
+--------+---------------------+
| nome   | email               |
+--------+---------------------+
| Kelley | rkelley0@icloud.com |
+--------+---------------------+
1 row in set (0.01 sec)

select nome, email from funcionarios
    -> WHERE cargo LIKE '%Engineer';
+--------+---------------------+
| nome   | email               |
+--------+---------------------+
| Kelley | rkelley0@icloud.com |
+--------+---------------------+
1 row in set (0.00 sec)
```

[Voltar ao Índice](#indice)

## <a name="parte9">Base de conhecimento para Performace com Operadores Lógicos</a>

- Contando a quantidade de registros para realizar as Querys.
- Utilizei Count(*) e Group By.

```sql
mysql> select count(*) from funcionarios;
+----------+
| count(*) |
+----------+
|        2 |
+----------+
1 row in set (0.00 sec)

mysql> select sexo, count(sexo) from funcionarios group by sexo;
+-----------+-------------+
| sexo      | count(sexo) |
+-----------+-------------+
| Feminino  |           1 |
| Masculino |           1 |
+-----------+-------------

```
# Exempo

## Em uma base de dados de trabalhadores com 1 milhão de registros onde 100 mil trabalham com jogos e 30 mil trabalham com vendas 70% são mulheres e 30% são homens.
<br/>

### Utilizando OR.

- Para a tabela verdade do OU(OR) coloquei a situação com maior quantidade de registros que possibilita com que a segunda situação não precise ser checada aumentando a performace da consulta.

### (01) - O gestor precisa encaminhar um e-mail para todos os funcionários que trabalham no setor de jogos ou com vendas.

```sql
select nome, email
    -> from funcionarios
    -> where trabalho = 'jogos'
    -> or trabalho = 'vendas';
```

### Utilizando AND

- Para a tabela verdade do E(END) coloquei a situação que contenha a menor quantidade de registros, como na tabela verdade para ser verdadeiro todas as condicionais precisão ser verdadeiras utilizando a situação com a menor quantidade basta que uma delas seja falsa para evitar a consulta da segunda otimizando a performace da consulta.

### (02) Um outro gestor solicitou o nome e email de todas as funciárias que trabalhem no departamento de jogos ou vendas.

```sql
mysql> select nome, email
    -> from funcionarios
    -> where
    -> (departamento = 'jogos' and sexo = 'Feminino')
    -> or
    -> (departamento = 'vendas'and sexo = 'Feminino');
```

[Voltar ao Índice](#indice)