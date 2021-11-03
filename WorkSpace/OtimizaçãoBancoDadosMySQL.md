# Otimização de Banco de dados no MySQL

## Esse artigo mostra o processo de otimização do banco de dados MySQL. Aprenda com abordagens à otimização de consultas, SGBD e ajustes de Sistema Operacional.

Este artigo tem como objetivo apresentar o processo de otimização do banco de dados [MySQL](http://www.devmedia.com.br/curso/curso-completo-de-mysql/281), bem como introduzir os aspectos que devem ser considerados durante o ajuste deste **SGBD** (**Sistema Gerenciador de Banco de Dados**). Este é o primeiro artigo de uma série que discutirá possibilidades de otimização do MySQL, abordando a otimização de consultas, a otimização do SGBD propriamente dito, e o ajuste do Sistema Operacional (SO) e do hardware que suportarão o seu sistema como um todo. Os artigos seguintes apresentarão os detalhes envolvidos em cada uma das partes apresentadas anteriormente.

Para a otimização de um SGBD precisamos eliminar os possíveis problemas de desempenho existentes em todos os níveis do sistema, isto é, precisamos identificar as consultas lentas que eventualmente são submetidas ao banco. Precisamos ainda melhorar as configurações do servidor de banco de dados, do sistema operacional, e finalmente o hardware que suportará toda o sistema. Alguns aspectos da otimização não se aplicam somente ao MySQL, e sim a todos os SGBDs, por isto algumas metodologias apresentadas aqui podem, em alguns casos, ser aplicadas também a outros SGBDs disponíveis no mercado.

Antes de explorarmos os itens apresentados anteriormente é necessário ressaltar que o processo de otimização não é trivial, visto que é preciso medir todos os aspectos do seu sistema para o entendimento preciso do funcionamento da sua aplicação. Assim, pode-se obter o ajuste que seja mais adequado à sua necessidade, por exemplo, o ajuste do SGBD para aplicações de leitura é diferente daquele onde prevalecerão escritas. Além disto, as medições de desempenho do seu sistema são imprescindíveis dado que estas servirão de referência para determinar se uma alteração realizada no SGBD teve efeitos positivos ou não.

O primeiro ponto a ser discutido é a otimização das consultas SQL. A interface da aplicação com o SGBD é feita a partir de consultas SQL, ou seja, esta é a linguagem que permite a extração das informações armazenadas pelo SGBD. Portanto, durante o processo de projeto da sua base de dados, é preciso vislumbrar os tipos de consultas que serão mais comuns e criar a base de forma que o processo de extração de dados seja facilitado. Além disto, é preciso escrever as consultas de forma que as mesmas sejam executadas no menor tempo possível. Mas, também é preciso monitorar as consultas lentas que eventualmente existam, e eliminá-las, seja pela reescrita da consulta ou até mesmo através da alteração da sua aplicação de forma a fazer um acesso mais eficiente ao banco. Este deve ser um ponto de averiguação constante, já que em ambiente onde há um número elevado de consultas e estas consomem muito tempo de serem processadas, isto criará uma deficiência considerável em termos de desempenho. Para a otimização de consultas é preciso entender a forma como as mesmas são processadas pelo MySQL, e assim, deve-se tentar atuar em cada etapa visando a redução do tempo de processamento das mesmas, gerando um ganho global considerável. No próximo serão discutidas as etapas de execução de uma consulta, bem como técnicas para o monitoramento destas consultas e da visualização do plano de execução das mesmas.

Uma vez eliminados os problemas relativos às consultas SQL, pode-se modificar as configurações do MySQL de forma a fazer um uso mais apropriado dos recursos disponíveis no SO, melhorando assim o desempenho do banco. Para isto é preciso entender como o MySQL funciona internamente, isto significa dizer que precisamos entender como o MySQL utiliza memória e disco, bem como quais são os principais parâmetros que podemos alterar para atingir este ganho. O MySQL apresenta um conjunto de ferramentas para o monitoramento do servidor de forma a detectar quais são os gargalos do seu sistema, e assim permitindo a eliminação dos mesmos. Estes aspectos serão abordados em detalhes nos terceiro artigo referente à otimização do MySQL.

Finalmente, precisamos aferir e monitorar o desempenho do SO que suportará todo o sistema, além do hardware e suas configurações. No sistema operacional podemos utilizar recursos mais apropriados para o banco, tais como sistema de arquivos mais eficientes, processos e threads nativas, além da escolha de um SO mais apropriado ao MySQL. Esta escolha pode, em alguns casos, gerar ganhos de desempenho em torno de 50%. Por último, mas não menos importante, é a escolha do hardware adequado. Por exemplo, ao utilizar-se de um processador de 64 bits é possível a utilização de arquivos grandes, além de permitir a alocação de uma quantidade maior de memória. Isto, possibilita a configuração de buffers de memória maiores para o MySQL, melhorando consideravelmente o desempenho.

A seguir vamos conhecer o processo de execução de consultas no MySQL, visando assim possibilitar a elaboração das [consultas SQL](http://www.devmedia.com.br/sql-select-guia-para-iniciantes/29530) de forma a serem executadas no menor tempo possível.

O processo de execução de uma consulta no MySQL consiste de várias etapas que são o parser, otimização, execução e retorno dos dados. A **Figura 1** apresenta uma visão geral deste processo.

![Etapas da execução de consultas SQL](https://www.devmedia.com.br/imagens/sqlmagazine/ago2005/Eber_OtimizaMySQL_Fig01.jpg)

**Figura 1:** Etapas da execução de consultas SQL

Durante o parser o MySQL faz a leitura do comando SQL enviado pelo cliente, converte o comando para um formato binário interno e então o envia ao otimizador. Neste caso, este processo será executado para cada consulta enviada ao servidor, portanto, é necessário reduzir este tempo para produzir um ganho de desempenho. Uma alternativa interessante é a utilização dos Prepared Statements, disponíveis a partir da versão 4.1. Este recurso permite a criação de um comando no qual será realizado o parser e o binário dele será armazenado no servidor. Desta forma, este comando poderá ser executado várias vezes tendo sido feito apenas um procedimento de parser, o que certamente implicará em redução no tempo de execução. Os Prepared Statements não serão abordados neste artigo, ficando fora do escopo deste texto.

A segunda etapa é a otimização da consulta, onde o otimizador decide a ordem de leitura das tabelas, qual o índice ele irá utilizar, caso exista o índice, e finalmente o tipo de leitura que será realizada na tabela, ou seja, o algoritmo de busca dos dados. As decisões tomadas pelo otimizador são baseadas em estatísticas que o próprio servidor armazena. Por exemplo, ele avalia a quantidade de registros por tabela, a quantidade de dados duplicados para cada chave existente, e assim optará pelo plano de execução que gerar o menor custo e tempo para ser executado. Vale ressaltar, que o processo de otimização se baseia em heurísticas e nem sempre o caminho percorrido é o melhor. Por isto, existem dicas que podem ser dadas para o otimizador de forma a induzir o MySQL a escolher o plano de execução que você desejar. Por exemplo, se você sabe que as tabelas devem ser lidas na ordem A,B e não B,A, você pode utilizar o STRAIGHT_JOIN para forçar a ordem de leitura. A mesma lógica pode ser utilizada para os índices, você pode forçar o MySQL a utilizar ou ignorar um determinado índice. Portanto, se você conhece qual a melhor forma de executar a sua consulta informe isto para o otimizador e desta forma você minimizará o tempo para a geração do plano de execução, já que nenhuma decisão será delegada para o otimizador, isto novamente acarretará um ganho no tempo de resposta.

Uma vez determinado o plano de execução, o MySQL deverá extrair os dados armazenados no disco. Portanto, se você possui áreas de memória grandes, os dados poderão ser mantidos nestes buffers e o acesso aos discos, que em geral é mais lento, será evitado e o tempo para a busca da informação será reduzido. Vale lembrar que o MySQL trabalha com o esquema de Storage Engines (Tipos de tabelas), e para cada tabela utilizada caberão otimizações específicas. Estas configurações serão abordadas com mais detalhes em outro artigo.

Finalmente, uma vez que os dados foram recuperados da memória ou disco, estes devem ser enviados para o cliente através da conexão que foi estabelecida entre ele e o servidor. Neste caso, quanto maior o seu resultado maior será o tempo para envio dos dados. Assim, algumas práticas podem ajudar a minimizar este tempo, por exemplo, evitar o uso de SELECT *. Liste somente os dados necessários, caso você precise de duas colunas especifique-as em seu comando, assim nenhuma informação desnecessária será enviada. Além disto, você poderá reduzir o tamanho dos dados através do uso do LIMIT, que permite obter apenas as primeiras linhas de dados ou até mesmo deslocamentos no resultado. Por exemplo, um SELECT ... LIMIT 10, 20 retornará 20 registros a partir do décimo primeiro registro do seu conjunto resultante. Por último, no MySQL 4.1 você poderá fazer uso do protocolo binário, que permite o tráfego de informações compactadas entre o cliente e o servidor, reduzindo o volume a ser transmitido através desta conexão, reduzindo assim o tempo para envio do resultado e por conseqüência o tempo de execução do comando.

Veremos agora técnicas para a detecção das consultas lentas e métodos para a avaliação do plano de execução de uma consulta.

O MySQL possui um log chamado “slow log”, onde são armazenadas todas as consultas cujo tempo de execução seja maior que o parâmetro long-query-time, que por padrão é 10 segundos. Além disto, pode-se configurar este log para armazenar também as consultas que não utilizam índices ou que realizam um SELECT *. Por padrão este log vem desabilitado, e pode ser ativado através do parâmetro log-slow-queries. Ao executar o comando STATUS, o MySQL irá exibir dentre outras informações o SLOW QUERIES, que é o número de consultas lentas recebidas pelo servidor, contado desde um o início da execução do MySQL, ou desde o último FLUSH STATUS. Caso o slow log esteja ativo, o que é recomendado, estas consultas serão gravadas neste arquivo e possibilitarão a identificação dos comandos que são os gargalos do seu sistema.

Uma vez detectadas as consultas lentas é preciso avaliar como o MySQL está executando estes comandos. Para isto faz-se uso do comando EXPLAIN, que deve ser colocado antes do comando SELECT a ser estudado. Este comando irá exibir o plano de execução escolhido pelo otimizador. O exemplo da **Listagem 1** ilustra este recurso para avaliar uma consulta que lista os países da região Nórdica e suas respectivas capitais.

**Listagem 1:** EXPLAIN de uma consulta feita no MySQL

```
mysql> EXPLAIN SELECT co.name, ci.name FROM City AS ci, Country AS co WHERE ci.id = co.capital
-> AND co.region LIKE 'Nordic%'\G
*************************** 1. row ***************************
id: 1
select_type: SIMPLE
table: co
type: ALL
possible_keys: NULL
key: NULL
key_len: NULL
ref: NULL
rows: 239
Extra: Using where
*************************** 2. row ***************************
id: 1
select_type: SIMPLE
table: ci
type: eq_ref
possible_keys: PRIMARY
key: PRIMARY
key_len: 4
ref: world.co.Capital
rows: 1
Extra:
2 rows in set (0.01 sec)
```

As tabelas são lidas pelo otimizador na ordem em que elas aparecem no retorno do EXPLAIN. No exemplo da **Listagem 1**, o MySQL optou por ler primeiro a tabela Country e depois a tabela City, perceba que a ordem em que as tabelas aparecem no FROM não foi seguida pelo otimizador. Por isto, quando for desejado que a ordem do FROM seja preservada, é preciso utilizar-se o STRAIGHT_JOIN para induzir o otimizador neste sentido.

Existem diversas informações apresentadas pelo EXPLAIN, a primeira delas é o SELECT_TYPE que mostra o tipo de consulta que está sendo processada. Estas podem ser consultas simples ou sem sub-consultas (SIMPLE) e SUB_QUERY ou UNION para comando que possuem consultas aninhadas. Além disto, o EXPLAIN fornece quais os índices estão disponíveis para a execução do comando (coluna POSSIBLE_KEYS), e o índice que ele está utilizando para a leitura do dados aparece na coluna KEY (NULL, caso não esteja fazendo uso de índices).

Vale destacar, que será utilizado apenas um índice para cada tabela lida pelo MySQL, por isto a criação do índice deve ser feita com critério, isto é, sempre compondo as colunas que serão empregadas no WHERE.

A coluna ROWS fornece o número de linhas lidas pelo MySQL para buscar o resultado, idealmente este número deve ser igual ao número de linhas retornadas pelo comando. A coluna REF indica a coluna utilizada para referenciar tabelas em JOIN (perceba a tabela City), e o EXTRA fornece informações adicionais sobre a execução, tais como, o uso de tabelas temporárias, ordenação, dentre outros.

A coluna TYPE exibe o algoritmo de busca utilizado para a leitura dos dados, a **Tabela 1** apresenta os valores possíveis para esta coluna, indo do melhor para o pior tipo.

| **Type**           | **Significado**                                              |
| ------------------ | ------------------------------------------------------------ |
| System             | Tabela apresenta apenas 1 registro.                          |
| Const              | Leitura de apenas um registro da tabela (busca pela chave primária). |
| Eq_ref             | Apenas uma linha desta tabela será lida para cada linha da tabela anterior (JOIN de tabelas 1:1). |
| Ref ou Ref_or_null | Leitura de vários registros desta tabela para cada registro lido da tabela anterior (JOIN 1:N), ou pesquisas por faixas de dados utilizando a chave primária. |
| Unique_subquery    | Sub-consulta utilizada dentro do IN e esta retorna apenas valores únicos na tabela externa. |
| Index_subquery     | Mesmo que o anterior, mas os valores retornados não são únicos na tabela externa. |
| Range              | Leitura de faixas de dados (>, <, BETWEEN, etc.).            |
| Index              | Leitura completa nos índices.                                |
| ALL                | Leitura completa dos dados da tabela.                        |

**Tabela 1:** Valores possíveis para a coluna TYPE

Percebe-se que no exemplo da **Listagem 1**, o MySQL está fazendo um ALL (leitura completa) na tabela de países, e então faz um EQ_REF com a tabela de cidades, indicando um relacionamento 1:1. Precisamos evitar sempre o ALL, já que a leitura completa na tabela pode ser muito lento e oneroso, especialmente se a tabela contém muitos registros. Além disto, se queremos apenas os países de uma região temos que ler apenas estes dados e não a tabela inteira. Na verdade o ALL ocorre por que não há um índice na coluna region da tabela de países, assim para resolver o problema desta consulta seria necessário criar um índice nesta coluna, fazendo com que o MySQL faça um RANGE, o que seria mais rápido.

Abaixo estão algumas dicas de otimização que devem estar sempre à mente durante um processo de melhoria de planos de execução de consultas:

- Reescreva a sua consulta de forma a percorrer um menor caminho, por exemplo, utilize as dicas para o otimizador ou sempre utilize campos indexados na cláusula WHERE, ou ainda evite SELECT *;
- Altere a ordem de leitura das tabelas de forma a ler sempre a tabela com menos registros;
- Induza o MySQL a sempre utilizar um índice;
- Indexe novos campos se necessário;
- Compare sempre as colunas indexadas com valores constantes e nunca aplique funções ou expressões ao índice, pois desta forma ele não será utilizado.

Esta foi uma visão geral do mecanismo de otimização de consultas do MySQL, maiores informações a respeito do comando EXPLAIN e do uso de índices podem ser encontradas em [www.mysql.com/documentation](https://www.devmedia.com.br/otimizacao-de-banco-de-dados-no-mysql/www.mysql.com/documentation).

Este é o processo de execução do MySQL, podemos ver que é possível reduzir o tempo de execução através de pequenas alterações em nosso processo de elaboração de consultas.