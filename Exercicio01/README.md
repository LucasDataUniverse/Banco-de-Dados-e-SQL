# Exercício 01


## Criando o Banco de dados para o exercício

```sql
mysql> create table funcionarios
    -> (
    -> idFuncionario integer,
    -> nome varchar(100),
    -> email varchar(200),
    -> sexo varchar(10),
    -> departamento varchar(100),
    -> admissao varchar(10),
    -> salario integer,
    -> cargo varchar(100),
    -> idRegiao int
    -> );
Query OK, 0 rows affected (0.01 sec)

```
## Os dados para o exercício utilizei o documento Base de Dados Funcionarios.
<br/>

## (01) Traga os funcionários que trabalhem no departamento de filmes OU no depatarmento de roupas.
<br/>

- Analisando o Banco

```sql
mysql> select count(*) from funcionarios;
+----------+
| count(*) |
+----------+
|      975 |
+----------+
1 row in set (0.00 sec)

mysql> select departamento, count(*) from funcionarios group by departamento order by 2;
+---------------+----------+
| departamento  | count(*) |
+---------------+----------+
| Filmes        |       21 |
| Joalheria     |       36 |
| Música        |       37 |
| Crianças      |       38 |
| Ferramentas   |       39 |
| Esporte       |       40 |
| Brinquedos    |       41 |
| Calçados      |       43 |
| Bebês         |       45 |
| Automotivo    |       46 |
| Alimentícios  |       46 |
| Saúde         |       46 |
| Industrial    |       47 |
| Jardim        |       47 |
| Books         |       47 |
| Outdoors      |       48 |
| Games         |       49 |
| Eletronicos   |       49 |
| Computadores  |       52 |
| Lar           |       52 |
| Roupas        |       53 |
| Beleza        |       53 |
+---------------+----------+
22 rows in set (0.00 sec)
```

- Filmes | 21  -  Roupas | 53

- Otimizando a Query utilizando o OR. Como estamos trabalhando com OR colocamos na primeiro posição quem tem mais chances de ser verdadeiro no caso coloquei 'Roupas'em primeiro.

```sql 
mysql> select nome, departamento from funcionarios
    -> where (departamento = 'Roupas' OR departamento = 'Filmes');
+------------+--------------+
| nome       | departamento |
+------------+--------------+
| Black      | Roupas       |
| Price      | Roupas       |
| Hawkins    | Roupas       |
| Oliver     | Roupas       |
| Cunningham | Roupas       |
| Perkins    | Roupas       |
| Freeman    | Roupas       |
| Nguyen     | Roupas       |
| Washington | Roupas       |
| Fisher     | Roupas       |
| Ferguson   | Roupas       |
| Watson     | Roupas       |
| Day        | Roupas       |
| Gonzales   | Filmes       |
| Rose       | Roupas       |
| Snyder     | Filmes       |
| Gordon     | Filmes       |
| Richardson | Roupas       |
| Cooper     | Filmes       |
| Berry      | Roupas       |
| Arnold     | Roupas       |
| Jordan     | Roupas       |
| Wright     | Roupas       |
| Spencer    | Filmes       |
| Gonzales   | Roupas       |
| Young      | Roupas       |
| White      | Roupas       |
| Marshall   | Roupas       |
| Ortiz      | Roupas       |
| Roberts    | Filmes       |
| Boyd       | Roupas       |
| Gray       | Roupas       |
| Little     | Filmes       |
| Griffin    | Filmes       |
| Gomez      | Roupas       |
| Williamson | Roupas       |
| Richards   | Roupas       |
| Kelley     | Filmes       |
| Kim        | Roupas       |
| James      | Roupas       |
| Taylor     | Roupas       |
| Lynch      | Roupas       |
| Arnold     | Filmes       |
| Greene     | Roupas       |
| Alexander  | Roupas       |
| Phillips   | Roupas       |
| Warren     | Filmes       |
| Reid       | Roupas       |
| Price      | Roupas       |
| Clark      | Filmes       |
| Roberts    | Roupas       |
| Hill       | Roupas       |
| Johnson    | Filmes       |
| Murray     | Roupas       |
| Richards   | Roupas       |
| Elliott    | Roupas       |
| Elliott    | Filmes       |
| Olson      | Roupas       |
| Weaver     | Filmes       |
| James      | Roupas       |
| Sims       | Roupas       |
| Gomez      | Filmes       |
| Knight     | Filmes       |
| Rice       | Filmes       |
| Knight     | Roupas       |
| Roberts    | Roupas       |
| Price      | Filmes       |
| Kelley     | Roupas       |
| Bishop     | Filmes       |
| Rice       | Roupas       |
| Marshall   | Roupas       |
| Burton     | Roupas       |
| Richards   | Roupas       |
| Walker     | Filmes       |
+------------+--------------+
74 rows in set (0.00 sec)

```


## (02) O gestor de marketing pediu a lista das funcionárias que tabalhem no departamento de filmes ou no departamento lar. Ele precisa enviar um email para as colaboradoras desses dois setores.

- Analisando o Banco

```sql
mysql> select sexo, count(sexo) from funcionarios group by sexo;
+-----------+-------------+
| sexo      | count(sexo) |
+-----------+-------------+
| Feminino  |         491 |
| Masculino |         484 |
+-----------+-------------+
2 rows in set (0.00 sec)

mysql> select departamento, count(*) from funcionarios group by departamento order by 2;
+---------------+----------+
| departamento  | count(*) |
+---------------+----------+
| Filmes        |       21 |
| Joalheria     |       36 |
| Música        |       37 |
| Crianças      |       38 |
| Ferramentas   |       39 |
| Esporte       |       40 |
| Brinquedos    |       41 |
| Calçados      |       43 |
| Bebês         |       45 |
| Automotivo    |       46 |
| Alimentícios  |       46 |
| Saúde         |       46 |
| Industrial    |       47 |
| Jardim        |       47 |
| Books         |       47 |
| Outdoors      |       48 |
| Games         |       49 |
| Eletronicos   |       49 |
| Computadores  |       52 |
| Lar           |       52 |
| Roupas        |       53 |
| Beleza        |       53 |
+---------------+----------+
22 rows in set (0.00 sec)
```

- Filmes | 21  -  Lar | 52
- Otimizando a Query utilizando o AND. Como vou trabalhar com AND coloquei na primeiro posição quem tem o menor número de ocorrências no banco para evitar a consulta da outra condicional uma vez que no AND todos tem que ser verdadeiro encontrando na primeiro condicional um false a Query não pula para a segunda condicional.
```sql
mysql> select nome, sexo, departamento, email from funcionarios
    -> where
    -> (departamento = 'Lar' AND sexo = 'Feminino')
    -> OR
    -> (departamento = 'Filmes' AND sexo = 'Feminino');
+------------+----------+--------------+-----------------------------------+
| nome       | sexo     | departamento | email                             |
+------------+----------+--------------+-----------------------------------+
| Porter     | Feminino | Lar          | vporterp@yelp.com                 |
| Owens      | Feminino | Lar          | cowensq@shareasale.com            |
| Cruz       | Feminino | Lar          | rcruz10@blinklist.com             |
| Washington | Feminino | Lar          | jwashington21@squidoo.com         |
| Gilbert    | Feminino | Lar          | hgilbert29@xrea.com               |
| Montgomery | Feminino | Lar          | rmontgomery3n@chicagotribune.com  |
| Diaz       | Feminino | Lar          | sdiaz64@disqus.com                |
| Freeman    | Feminino | Lar          | gfreeman74@bloomberg.com          |
| Gordon     | Feminino | Filmes       | egordon7k@yellowbook.com          |
| Cooper     | Feminino | Filmes       | icooper85@w3.org                  |
| Gibson     | Feminino | Lar          | bgibson8o@pen.io                  |
| Crawford   | Feminino | Lar          | mcrawford8u@parallels.com         |
| Campbell   | Feminino | Lar          | pcampbell9b@istockphoto.com       |
| Gonzales   | Feminino | Lar          | jgonzales9s@sourceforge.net       |
| Payne      | Feminino | Lar          | jpayneal@comsenz.com              |
| Cooper     | Feminino | Lar          | scooperb1@cmu.edu                 |
| Chapman    | Feminino | Lar          | schapmanb6@nhs.uk                 |
| Williams   | Feminino | Lar          | swilliamsbc@bing.com              |
| Morales    | Feminino | Lar          | dmoralesbl@mit.edu                |
| Berry      | Feminino | Lar          | jberrybr@discuz.net               |
| Little     | Feminino | Filmes       | dlittlecp@usatoday.com            |
| Cox        | Feminino | Lar          | ncoxe1@1und1.de                   |
| Morris     | Feminino | Lar          | rmorriseu@yahoo.com               |
| Walker     | Feminino | Lar          | kwalkerf2@vinaora.com             |
| Myers      | Feminino | Lar          | dmyersfq@amazon.com               |
| Olson      | Feminino | Lar          | folsong9@acquirethisname.com      |
| Evans      | Feminino | Lar          | aevansgg@wordpress.org            |
| Warren     | Feminino | Filmes       | awarrenht@addthis.com             |
| Mendoza    | Feminino | Lar          | rmendozajl@g.co                   |
| Ferguson   | Feminino | Lar          | gfergusonka@geocities.jp          |
| Gonzales   | Feminino | Lar          | rgonzaleskv@meetup.com            |
| Burke      | Feminino | Lar          | eburkel4@newsvine.com             |
| Murray     | Feminino | Lar          | cmurraylx@icio.us                 |
| Gomez      | Feminino | Filmes       | tgomezm8@ucoz.ru                  |
| Knight     | Feminino | Filmes       | dknightm9@quantcast.com           |
| Rice       | Feminino | Filmes       | jricemp@columbia.edu              |
| Carpenter  | Feminino | Lar          | rcarpenterov@pagesperso-orange.fr |
| Bishop     | Feminino | Filmes       | kbishoppi@ovh.net                 |
| Jones      | Feminino | Lar          | djonesq1@tamu.edu                 |
| Walker     | Feminino | Filmes       | swalkerr0@sina.com.cn             |
| Sanchez    | Feminino | Lar          | tsanchezr7@lycos.com              |
+------------+----------+--------------+-----------------------------------+
41 rows in set (0.00 sec)
```