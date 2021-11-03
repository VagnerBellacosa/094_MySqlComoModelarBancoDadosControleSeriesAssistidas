# Dicas para otimizar seu MySQL

*11:51* *Turbosite*

Suas consultas estáo demorando muito tempo? Está gerando filas de conexões? Todas as operações de banco estão sofrendo lentidão? Se respondeu sim para qualquer uma das perguntas, então está na hora de otimizar seu Banco de Dados. A equipe da [Turbosite](https://www.turbosite.com.br/) compartilha nesse artigo algumas dicas para otimização de seu Banco de Dados. Utilizando poucas funções **MySQL**, o resultado no desempenho de seu sistema pode ser surpreendente.

Dos três modos de otimização (configuração de hardware do servidor, configuração de rede do servidor e otimização de código), apresentamos aqui métodos para otimização por código MySQL.

 

## MYSQLREPORT

Como primeiro passo, você pode usar o comando **MYSQLREPORT** para gerar relatórios sobre bancos de dados que estão atingindo o limite de sua capacidade de uso  e estabelecer um patamar para operações e usos adicionais. Talvez também você se veja obrigado a modificar arquivo de configuração (my.cnf) para registrar o log de consultas lentas. Identifique as consultas que estão processando muito devagar e as possíveis causas.

Para acessar a documentação completa do MYSQLREPORT, recomendamos esse link: [man.he.net/man1/mysqlreport](http://man.he.net/man1/mysqlreport).

 

## EXPLAIN

Aplique o comando **EXPLAIN** antes do script *SELECT* para o MySQL retornar um registro contendo a análise do script para aquela tabela consultada. Esse método retorna algumas informações, como *ID*, *SELECT_TYPE*, *TABLE*, *TYPE*, *KEY_LEN*, *REF*, sendo que as informações que você vai querer para avaliar o desempenho do código são:

- ***POSSIBLE_KEYS\*:** mostra os índices disponíveis para serem utilizados naquela consulta;
- ***KEY\*:** mostra o índice escolhido pelo MySQL para realizar a consulta;
- ***ROW\*:** número estimado de linhas percorridas para encontrar o resultado do *SELECT;*
- ***EXTRA\*:** sugestões de otimização em índices da consultas, como usar *DISTINCT*, *NOT* *EXIST*, *USING* *INDEX*, entre outras.

```
EXPLAIN SELECT * FROM funcionarios;
```

 

## **ANALYZE**

Use o comando **ANALYZE** para gerar uma distribuição de chaves, para a tabela a ser utilizada pelo otimizador de consultas do MySQL, para decidir quais índices serão melhores se utilizados em uma consulta.

```
ANALYZE TABLE funcionarios;
```

 

## **OPTIMIZE** 

Se há grandes quantidades de inserções/exclusões em uma tabela, principalmente se a tabela conter muitos campos do tipo *varchar*, *text* e *blob*, o disco será comprometido à várias fragmentações. O comando **OPTIMIZE** deve ser usado com freqüência para esse tipo de situação. O comando ira otimizar a movimentação da cabeça de leitura e gravação do disco durante a recuperação de dados, implementando a desfragmentação do disco causada por campos de comprimento variável.

 

```
OPTIMIZE TABLE funcionarios;
```

 

## **LOAD DATA INFILE**

Para a importação de dados para uma tabela, o comando **LOAD DATA INFILE**, no lugar do comando *SELECT*, irá apresentar um desempenho até 20 vezes melhor.

```
LOAD DATA INFILE 'filedata.dat' INTO TABLE funcioanrios (col1,col2,...,colM) FIELDS TERMINATED BY '|'");
```

 

## **TRUNCATE**

O comando *DELETE* deleta linha por linha, enquanto **TRUNCATE** deleta todas as linhas de uma só vez. Portanto, se você não estiver interessado no número de linhas suprimidas de uma tabela, como resultado do comando *DELETE*, utilize o comando *TRUNCATE* com a seguinte sintaxe:

```
TRUNCATE TABLE funcionarios;
```

 

## **Prioridade dos comandos**

Se há mais consultas do que inserções de dados, você pode ter uma **prioridade** mais baixa do comando *INSERT* utilizando

```
INSERT LOW_PRIORITY
```

ou

```
SELECT HIGH_PRIORITY
```

Se o cliente não está interessado nos resultados do comando *INSERT*, então esta operação já pode imediatamente utilizar menos os recursos do sistema, utilizando-se o seguinte comando:

```
INSERT DELAYED
```

Isso torna o sistema mais rápido porque acumula as inserções em lotes.

 

## Permissões no MySQL

Além de incrementar na segurança da conexão, criar usuários com permissões específicas reduzem o *overhead* das verificações das permissões em todos os comandos realizados no MySQL, melhorando assim no desempenho do sistema. Como exemplo, um leitor do blog apenas tem interesse na leitura de postagem, leitura e inserção de comentários. Criar um usuário de nome “leitor”, com acesso apenas a leitura da tabelas ‘postagens’, e acesso a leitura e escrita à tabela ‘comentarios’, será de fato uma boa prática. A segurança será incrementada, já que aquele usuário não terá permissão de acessar, modificar ou deletar outros registros que não são de seu respeito, como também o desempenho, já que o *overhead* do usuário constará suas propriedades de acessos de antemão.

```
GRANT Oper1,...,OperN ON db_name.tb_name TO user_name@computer_name IDENTIFIED BY password;
```

 

## **BENCHMARK**

Por fim, para saber quanto tempo uma determinada função ou expressão MySQL está demorando, use a função MySQL embutida:

```
SELECT BENCHMARK ( 10000, ( SELECT col1 FROM funcionarios LIMIT 1 ) );
```

Lembrando que, para passar consultas na função *BENCHMARK*, obrigatoriamente a *query* deve retornar 1 linha com 1 coluna.

 

##  Outras dicas corriqueiras

- Utilize **ORDER BY** sempre na primeira tabelas, de preferência em índices, quando estiver realizando uma consulta em várias tabelas interligadas;
- Utilize **LIMIT**, o MySQL irá primeiro avaliar o comando *LIMIT* para depois executar funções como *ORDER BY* e *GROUP BY*;
- Realize **UPDATE** e **INSERT** em um lote inteiro de registros, de uma só vez, além de realizar uma ação por cada registro;
- Remova parênteses desnecessários na cláusula WHERE.

 

Referências: [Como otimizar consultas MySQL](http://www.comofazertudo.com.br/computadores-e-internet/como-otimizar-consultas-mysql), [Using EXPLAIN to Write Better MySQL Queries](http://www.sitepoint.com/using-explain-to-write-better-mysql-queries/), [Como otimizar consultas no MySQL-Análise das queries](http://www.webgoal.com.br/como-otimizar-consultas-no-mysql/).



*Categoria: [Dicas](https://www.turbosite.com.br/blog/categoria/dicas), [MySQL](https://www.turbosite.com.br/blog/categoria/mysql)* *| Tags: [Dicas](https://www.turbosite.com.br/blog/tag/dicas), [MySQL](https://www.turbosite.com.br/blog/tag/mysql)*