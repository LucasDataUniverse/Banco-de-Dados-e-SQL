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
- [10 Filtrando valores NULOS](#parte10)
- [11 UPDATE](#parte11)
- [12 DELETE](#parte12)
- [13 MODELAGEM PRIMEIRA FORMA NORMAL](#parte13)



## <a name=parte1> Objetivos do curso</a>
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
- LIKE para procurar no texto do campo cargo a palavra Engineer e o % foi utilizando para indicar qualquer coisa antes da palavra Engineer.

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
# Exemplo

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

## <a name=parte10>Filtrando Valores NULOS</a>

```sql
mysql> SELECT nome, sexo, email from funcionarios
    -> WHERE email IS NULL;
```
- o comando irar retornar a tupla que contenha o campo email NULO.

[Voltar ao Índice](#indice)

## <a name=parte11>UPDATE</a>

- Cuidado com esse comando.
- Utilize sempre o WHERE
- O exemplo a seguir demonstra a utilização de um comando UPDATE 
```sql
mysql> update funcionarios
    -> set email = 'alterado@alterado.com.br'
    -> where nome = 'Kennedy'
    -> and email = 'lkennedyrq@edublogs.org';
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0
```

[Voltar ao Índice](#indice)

## <a name=parte12>DELETE</a>

- Cuidado com esse comando.
- Utilize sempre o WHERE
- O exemplo a seguir demonstra a utilização de um comando DELETE
```sql
mysql> delete from funcionarios
    -> where nome = 'Kennedy'
    -> and email = 'alterado@alterado.com.br';
Query OK, 1 row affected (0.01 sec)
```

## <a name=parte13>MODELAGEM PRIMEIRA FORMA NORMAL</a>

- 01 Todo campo vetorizado se tornará outra TABELA.
- 02 Todo campo multivalorado se tornará outra TABELA.
- 03 Toda tabela necessita de pelo menos um campo que identifique todo o registro como senco único.

```sql
mysql> select * from cliente;
+----------+------+--------------------------+-------------+--------------+---------------------------------------------+
| nome     | sexo | email                    | cpf         | telefone     | endereco
|
+----------+------+--------------------------+-------------+--------------+---------------------------------------------+
| Joao     | M    | JOAO@JOAO.COM.BR         | 13633544228 | 27991654709  | Rua AMELIA - GOIABEIRA - PEDRA - PERNAMBUCO |
| VICTOR   | M    | VICTOR@VICTOR.COM.BR     | 14533544228 | 1255254709   | Rua AMELIA - GOIABEIRA - PEDRA - PERNAMBUCO |
| Cláudia  | F    | Cláudia@Cláudia.COM.BR   | 15633544228 | 78945654709  | Rua AMELIA - GOIABEIRA - PEDRA - PERNAMBUCO |
| matheus  | M    | matheus@matheus.COM.BR   | 16633544228 | 909955654709 | Rua JOAO - BEBERIBI - PEDRA - PERNAMBUCO    |
| HIAGO    | M    | HIAGO@HIAGO.COM.BR       | 02263544228 | 70991654709  | Rua DR.CARLOS - CENTRO - PEDRA - PERNAMBUCO |
| FERNANDO | M    | FERNANDO@FERNANDO.COM.BR | 09677544228 | 13991654709  | Rua DRa.ALEXA - AMAZON - PEDRA - PERNAMBUCO |
+----------+------+--------------------------+-------------+--------------+---------------------------------------------+
6 rows in set (0.00 sec)
```

- APLICANDO A PRIMEIRA FORMA NA TABELA CLIENTE.

![This is an image](Img\Forma01.png)


- Em relacionamentos 1 x 1 a chave estrangeira fica na tabela mais fraca.
- Em relacionamentos 1 x N a chave estrangeira fica sempre na  cardinalidade N.

- Criando a tablema CLIENTE.
```sql
mysql> CREATE TABLE CLIENTE(
    ->  IDCLIENTE INT PRIMARY KEY AUTO_INCREMENT,
    ->  NOME VARCHAR(30) NOT NULL,
    ->  SEXO ENUM('M', 'F') NOT NULL,
    ->  EMAIL VARCHAR(50) UNIQUE,
    ->  CPF VARCHAR(15) UNIQUE
    -> );
Query OK, 0 rows affected (0.01 sec)
```
- Criando a tabela ENDERECO.
```sql
mysql> CREATE TABLE ENDERECO(
    ->  IDENDERECO INT PRIMARY KEY AUTO_INCREMENT,
    ->  RUA VARCHAR(30) NOT NULL,
    ->  BAIRRO VARCHAR(30) NOT NULL,
    ->  CIDADE VARCHAR(30) NOT NULL,
    ->  ESTADO CHAR(2) NOT NULL,
    ->  ID_CLIENTE INT UNIQUE,
    ->  FOREIGN KEY (ID_CLIENTE)
    ->  REFERENCES CLIENTE(IDCLIENTE)
    -> );
Query OK, 0 rows affected (0.02 sec)
```

- Criando a tabela TELEFONE.
```sql
mysql> CREATE TABLE TELEFONE(
    ->  IDTELEFONE INT PRIMARY KEY AUTO_INCREMENT,
    ->  TIPO ENUM('RES', 'COM', 'CEL') NOT NULL,
    ->  NUMERO VARCHAR(10) NOT NULL,
    ->  ID_CLIENTE INT,
    ->  FOREIGN KEY (ID_CLIENTE)
    ->  REFERENCES CLIENTE(IDCLIENTE)
    -> );
Query OK, 0 rows affected (0.02 sec)
```

- Inserindo dados em na tablema CLIENTE.
```sql
mysql> INSERT INTO CLIENTE VALUES(NULL, 'LUCAS', 'M','LUCAS@LUCAS.COM.BR', '77777777777');
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO CLIENTE VALUES(NULL, 'CARLOS', 'M','CARLOS@CARLOS.COM.BR', '88888888888');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO CLIENTE VALUES(NULL, 'TIRINGA', 'M','TIRINGA@TIRINGA.COM.BR', '22222222222');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO CLIENTE VALUES(NULL, 'EMANUELY', 'M','EMANUELY@EMANUELY.COM.BR', '33333333333');
Query OK, 1 row affected (0.00 sec)
/* -----------------------------------------------------*/
mysql> SELECT * FROM CLIENTE;
+-----------+----------+------+--------------------------+-------------+
| IDCLIENTE | NOME     | SEXO | EMAIL                    | CPF         |
+-----------+----------+------+--------------------------+-------------+
|         1 | LUCAS    | M    | LUCAS@LUCAS.COM.BR       | 77777777777 |
|         2 | CARLOS   | M    | CARLOS@CARLOS.COM.BR     | 88888888888 |
|         3 | TIRINGA  | M    | TIRINGA@TIRINGA.COM.BR   | 22222222222 |
|         4 | EMANUELY | F    | EMANUELY@EMANUELY.COM.BR | 33333333333 |
+-----------+----------+------+--------------------------+-------------+
4 rows in set (0.00 sec)
```

- Inserindo dados em na tablema ENDERECO.
```sql
mysql> INSERT INTO ENDERECO VALUES(NULL, 'RUA ANTONIO SA', 'CENTRO', 'PEDRA', 'PE', 1);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO ENDERECO VALUES(NULL, 'RUA PEDRO SA', 'MACABIRA', 'PEDRA', 'PE', 2);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO ENDERECO VALUES(NULL, 'RUA JOSE SA', 'CENTRO', 'PEDRA', 'PE', 3);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO ENDERECO VALUES(NULL, 'RUA ANTONIO SA', 'CENTRO', 'PEDRA', 'PE', 4);
Query OK, 1 row affected (0.01 sec)
/* -----------------------------------------------------*/
mysql> SELECT * FROM ENDERECO;
+------------+----------------+----------+--------+--------+------------+
| IDENDERECO | RUA            | BAIRRO   | CIDADE | ESTADO | ID_CLIENTE |
+------------+----------------+----------+--------+--------+------------+
|          1 | RUA ANTONIO SA | CENTRO   | PEDRA  | PE     |          1 |
|          2 | RUA PEDRO SA   | MACABIRA | PEDRA  | PE     |          2 |
|          3 | RUA JOSE SA    | CENTRO   | PEDRA  | PE     |          3 |
|          4 | RUA ANTONIO SA | CENTRO   | PEDRA  | PE     |          4 |
+------------+----------------+----------+--------+--------+------------+
4 rows in set (0.00 sec)
```
- Inserindo dados em na tablema TEFELONE.
```sql
mysql> INSERT INTO TELEFONE VALUES(NULL, 'COM', '991745698', 3);
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO TELEFONE VALUES(NULL, 'CEL', '991658938', 2);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO TELEFONE VALUES(NULL, 'RES', '991790134', 3);
Query OK, 1 row affected (0.01 sec)
/* -----------------------------------------------------*/
mysql> SELECT * FROM TELEFONE;
+------------+------+-----------+------------+
| IDTELEFONE | TIPO | NUMERO    | ID_CLIENTE |
+------------+------+-----------+------------+
|          1 | COM  | 991745698 |          3 |
|          2 | CEL  | 991658938 |          2 |
|          3 | RES  | 991790134 |          3 |
+------------+------+-----------+------------+
3 rows in set (0.00 sec)
```
[Voltar ao Índice](#indice)