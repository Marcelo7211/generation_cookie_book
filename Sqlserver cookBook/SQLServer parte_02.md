<h1>Banco de Dados com SQL Server</h1>

O que veremos por aqui:

1. Introdução ao SQL Server
2. Entendendo: Comandos e Conceitos Básicos



<h2>0.1. Instalando SQL Server e SQL Server Management Studio </h2>

### Faça o download do  SQL Server Management Studio no link abaixo	

<div align="center"><img src="https://i.imgur.com/TPfWZKL.png" title="source: imgur.com" width="90%"/>
</div>

​		

<div align="left"> <a href="https://docs.microsoft.com/pt-br/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15" target="_blank"><b>Baixar o SQL Server Management Studio (SSMS)</i></b></a>

Instale o o SQL Server Management Studio no seu computador

### Faça o download do  SQL Server  no link abaixo no modo desenvolvedor como descrito na imagem a abaixo	

<div align="center"><img src="https://i.imgur.com/ZP22N8m.png" title="source: imgur.com" width="90%"/>
</div>

​		

<div align="left"><a href="https://www.microsoft.com/pt-br/sql-server/sql-server-downloads" target="_blank"><b>Baixar o SQL Server</i></b></a>

Instale o o SQL Server Management Studio no seu computador como no tutorial das imagens abaixo

<div align="center"><img src="https://i.imgur.com/mYwH90J.png" title="source: imgur.com" width="90%"/>
</div>		

instale a versão Básico.

<div align="center"><img src="https://i.imgur.com/mYwH90J.png" title="source: imgur.com" width="90%"/>
</div>		

​						

<div align="center"><img src="https://i.imgur.com/EeBBUub.png" title="source: imgur.com" width="90%"/>
</div>		

#### Reinicie o seu computador

<h2>1. SQL Server</h2>

O Microsoft SQL Server é um sistema gerenciador de Banco de dados relacional desenvolvido pela Sybase em parceria com a Microsoft. Esta parceria durou até 1994, com o lançamento da versão para Windows NT e desde então a Microsoft mantém a manutenção do produto.

<div align="left"><a href="https://www.microsoft.com/pt-br/sql-server/sql-server-downloads" target="_blank"><b>Site Oficial: <i>SQL Server</i></b></a>


| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="80px"/> | **DICA:** *Caso você tenha alguma dúvida quanto a instalação do SQL Server, consulte o Guia de Instalação do SQL Server. |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<h3>1.1. Entendendo: Comandos e Conceitos Básicos</h3>

<div align="center">A IDE que utilizaremos para criar e manipular o nosso banco de dados será o SQL Server Management Studio</div>

<div align="center"><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTQRpvJjKPsZ7utFp26mk4KvNgOZRg12rKCZGWi5HCt2CsqcEYwX8veMqnwe9BPYMuaREE&usqp=CAU" title="source: imgur.com" width="90%"/>
</div>



<h3>1.2. Criando nosso primeiro Banco de Dados</h3>



1. Uma vez que estamos o SQL Server Management Studio  aberto, precisamos criar uma conexão local. Portanto,  digite no nome do servidor localhost , defina o tipo de servidor mecanismo de banco de Dados e defina a autenticação para autenticação do Windows.

<div align="center"><img src="https://i.imgur.com/i9i1GhX.png" title="source: imgur.com" width="90%"/></div>

<h3>1.3. Executando consultas noSQL Server Management Studio</h3>



Para escrever o código SQL das nossas Queries, utilize a aba **Query** do SQL Server Management Studio.

Para executar a Query existem duas maneiras:

|                                                              | Descrição                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| <img src="https://i.imgur.com/k8lDead.png" title="source: imgur.com" /> | Executa todas as linhas ou apenas as linhas selecionadas de uma vez só na sequência. |
|                                                              |                                                              |



<h3>1.4. Banco de Dados - Exemplo</h3>



Utilizaremos como Banco de dados guia para testarmos as SQL Queries no SQL Servero Banco **db_quitanda**. Primeiro vamos criar a tabela **tb_produtos**, que possui estrutura abaixo:

<div align="center"><img src="https://i.imgur.com/sH0OsaD.png" title="source: imgur.com" width="25%"/></div>



<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/>Criar o Banco de dados</h3>



Na aba **Query**, digite e execute a query abaixo utilizando o segundo raio <img src="https://i.imgur.com/9FtJQlk.png" title="source: imgur.com" width="30px"/>:

<h4>CREATE DATABASE</h4>

```sql
CREATE DATABASE db_quitanda;
```
Ao executar a query, será criado o **Banco de Dados** e no campo de Output aparecerá o log/mensagem informando que a operação foi efetuada com sucesso.

<div align="center"><img src="https://i.imgur.com/f1PsAQB.png" title="source: imgur.com" width="70%"/></div>

<div align="center"><img src="https://i.imgur.com/N3FCB4M.png" title="source: imgur.com" width="70%"/></div>

<div align="left"><img src="https://i.imgur.com/Mh2KzWe.png" title="source: imgur.com" width="25px"/> <a href="https://www.w3schools.com/sql/sql_create_db.asp" target="_blank"><b>Documentação: <i>Create database - W3Schools</i></b></a>

<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/>Selecionando o Banco de Dados</h3>



Antes de criarmos nossa primeira tabela, é necessário indicar ao SQL Server qual banco de dados queremos trabalhar. Para isso utilize a query abaixo, e em seguida execute a query abaixo utilizando o segundo raio <img src="https://i.imgur.com/9FtJQlk.png" title="source: imgur.com" width="30px"/>.

<h4>USE</h4>

```sql
USE [db_quitanda]
```

Ao executar a query, aparecerá no log/mensagem do campo de Output a seguinte mensagem:

<div align="center"><img src="https://i.imgur.com/f1PsAQB.png" title="source: imgur.com" width="70%"/></div>

<div align="left"> <a href="https://www.tutorialsteacher.com/sqlserver/create-database/" target="_blank"><b>Documentação: <i>create database SQL Server Tutorial</i></b></a>




<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/> Criando nossa primeira Tabela</h3>



O processo para criação de uma tabela é bem simples, basta inserir a query abaixo, e em seguida execute a query abaixo utilizando o segundo raio <img src="https://i.imgur.com/9FtJQlk.png" title="source: imgur.com" width="30px"/>.

<h4>CREATE TABLE</h4>

```sql
CREATE TABLE db_quitanda.dbo.tb_produtos (
  id              bigint           NOT NULL    IDENTITY    PRIMARY KEY,
  nome           VARCHAR(255)  NOT NULL,
  quantidade  int,
  preco decimal not null,
);
```

Caso a query tenha sido executada corretamente, no canto esquerdo na aba das **Tabelas** aparecerá a tabela criada: 

<div align="center"><img src="https://i.imgur.com/JZrUCcM.png" title="source: imgur.com" width="70%"/></div>

E aparecerá no log/mensagem do campo de Output a seguinte mensagem:

<div align="center"><img src="https://i.imgur.com/f1PsAQB.png" title="source: imgur.com" width="70%"/></div>

<div align="left"><a href="https://www.tutorialsteacher.com/sqlserver/create-tablee" target="_blank"><b>Documentação: <i>Create Table</i></b></a>




<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/> Inserindo dados na Tabela</h3>



Uma vez que já temos a tabela criada, precisamos popula-la, ou seja, inserir dados. Para tal digite o código abaixo seguindo a sintaxe/estrutura de código abaixo e em seguida selecione as 6 linhas e execute a query utilizando o primeiro raio <img src="https://i.imgur.com/xH6Ei9O.png" title="source: imgur.com" />.

<h4>INSERT INTO</h4>

```sql
USE [db_quitanda]
GO

INSERT INTO [dbo].[tb_produtos] ([nome] ,[quantidade] ,[preco]) VALUES ('tomate',100, 8.00);
INSERT INTO [dbo].[tb_produtos] ([nome] ,[quantidade] ,[preco]) VALUES ('maçã',20, 5.00);
INSERT INTO [dbo].[tb_produtos] ([nome] ,[quantidade] ,[preco]) VALUES ('laranja',50, 10.00);
INSERT INTO [dbo].[tb_produtos] ([nome] ,[quantidade] ,[preco]) VALUES ('banana',200, 12.00);
INSERT INTO [dbo].[tb_produtos] ([nome] ,[quantidade] ,[preco]) VALUES ('uva',1200, 30.00);
INSERT INTO [dbo].[tb_produtos] ([nome] ,[quantidade] ,[preco]) VALUES ('pêra',500, 3.99);

GO

```



Feito isto os dados dos produtos Tomate, Maçã, Laranja e das outras frutas serão inseridos na tabela. 



| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="180px"/> | **IMPORTANTE:** Como definimos que o campo `id` será chave primária (`PRIMARY KEY`) e será atualizado automaticamente de um em um a cada registro inserido, através do código `auto_increment`, não inserimos nenhum valor nesse campo. |
| ------------------------------------------------------------ | :----------------------------------------------------------- |

<div align="left"> <a href="https://www.tutorialsteacher.com/sqlserver/insert-data" target="_blank"><b>Documentação: <i>Insert Into </i></b></a>




<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/> Selecionando dados da Tabela</h3>



Agora vamos fazer a nossa primeira consulta no bando para ver se os dados foram devidamente inseridos na tabela. Para isto basta fazer um `Select ` na tabela:

<h4>SELECT</h4>

```sql
SELECT * FROM tb_produtos;
```

Ao executar a query, aparecerá o console com a seguinte tabela:

<div align="center"><img src="https://i.imgur.com/8Nztii5.png" title="source: imgur.com" width="60%"/></div>

Caso seja necessário selecionar apenas um atributo como por exemplo o nome, basta substituir o ( * ) **asterisco** pelo nome do atributo desejado.

```sql
SELECT nome FROM tb_produtos;
```

Ao executar a query, aparecerá o console com a seguinte tabela:

<div align="center"><img src="https://i.imgur.com/d2e0jxo.png" title="source: imgur.com" width="50%"/></div>

Caso seja necessário mostrar mais de um atributo, **devemos separa-los por vírgula.**

```sql
SELECT nome, preco FROM tb_produtos;
```

Ao executar a query, aparecerá no log/mensagem do campo de Output a seguinte tabela:

<div align="center"><img src="https://i.imgur.com/ro88asD.png" title="source: imgur.com" width="60%"/></div>



<div align="left"><img src="https://i.imgur.com/Mh2KzWe.png" title="source: imgur.com" width="25px"/> <a href="https://www.w3schools.com/sql/sql_select.asp" target="_blank"><b>Documentação: <i>Select - W3Schools</i></b></a>


<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/> Selecionando dados da Tabela com critérios</h3>



Caso haja a necessidade de retornar apenas uma linha especifica, utilizarmos a cláusula `WHERE` seguido do atributo que queremos filtrar. **Exemplo**: desejamos retornar todas as informações do Produto cujo `id` é igual 1. Nesse caso executamos a seguinte query: 

<h4>WHERE</h4>

```sql
SELECT * FROM tb_produtos WHERE id = 1;
```

Ao executar a query, teremos o seguinte resultado:

<div align="center"><img src="https://i.imgur.com/m80d0aH.png" title="source: imgur.com" width="70%"/></div>

<div align="left"><img src="https://i.imgur.com/Mh2KzWe.png" title="source: imgur.com" width="25px"/> <a href="https://www.tutorialsteacher.com/sqlserver/where-clause" target="_blank"><b>Documentação: <i>Where</i></b></a>




<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/>Selecionando dados com os Operadores Relacionais</h3>



Caso haja a necessidade de retornar registro com base em comparações, basta utilizarmos o código `WHERE` junto com os Operadores Relacionais, informando o campo/coluna que será utilizado na comparação. 

| Operador | Descrição              |
| -------- | ---------------------- |
| >        | Maior do que           |
| >=       | Maior do que ou  igual |
| <        | Menor do que           |
| <=       | Menor do que ou igual  |
| =        | igual                  |
| <>       | diferente              |

**Exemplo**: desejamos retornar todos os produtos que tenham preço acima de R$ 5,00. Nesse caso executamos a seguinte query:

<h4>WHERE com Operados Relacionais</h4>

```sql
SELECT * FROM tb_produtos WHERE preco > 5.00;
```

Ao executar a query, teremos o seguinte resultado:



<div align="center"><img src="https://i.imgur.com/1TcltPx.png" title="source: imgur.com" width="70%"/></div>






<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/>Selecionando dados com os Operadores Lógicos</h3>



Caso haja a necessidade de retornar um registro com base em um resultado lógico (VERDADEIRO ou FALSO), basta utilizarmos o código `WHERE` junto com os Operadores Lógicos, informando o atributo que será utilizado na comparação. 

| Operador | Descrição                                                  |
| -------- | ---------------------------------------------------------- |
| AND      | Verdadeiro somente se todas as condições forem verdadeiras |
| OR       | Verdadeiro se 1 condição for verdadeira                    |
| NOT      | Negação                                                    |

**Exemplo**: desejamos retornar todos os produtos que tenham preço acima de R$5,00 **E** quantidade menor do que 100. Nesse caso executamos a seguinte query:

<h4>WHERE com Operadores Lógicos</h4>

```sql
SELECT * FROM tb_produtos WHERE preco > 5.00 AND quantidade < 100;
```

Ao executar a query, teremos o seguinte resultado:

<div align="center"><img src="https://i.imgur.com/1vTlRmw.png" title="source: imgur.com" width="70%"/></div>




<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/> Atualizando dados na Tabela</h3>



Para atualizar os dados da tabela devemos utilizar o comando `Update` no registro que queremos atualizar. **Exemplo**: queremos alterar o preço do produto Tomate para R$5,00. 

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="300px"/> | **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao construir essa Query, pois obrigatoriamente você DEVE COLOCAR o comando WHERE, pois caso contrário o MySQL Workbench irá atualizar TODOS OS REGISTROS, sem a possibilidade de desfazer a atualização errônea de maneira simples.* |
| ------------------------------------------------------------ | :----------------------------------------------------------- |

Antes de Executar a query, execute o comando abaixo:
```sql
SET SQL_SAFE_UPDATES = 0;
```
A linha de comando acima **desabilita o modo de atualização segura** do MySQL, ou seja, é um modo que impede, por exemplo, de executar os famosos **UPDATE sem WHERE** (modifica todos o registros da tabela) e o **DELETE sem WHERE** (apaga todos o registros da tabela).

Voltando ao exemplo acima, vamos executar a seguinte query:

<h4>UPDATE</h4>

```sql
UPDATE tb_produtos SET preco = 5.00 WHERE id = 1;
```

Ao executar a query, aparecerá no log/mensagem do campo de Output uma mensagem que a alteração foi concluída, e para visualizar o produto alterado basta executa a seguinte query:

```sql
SELECT * FROM tb_produtos WHERE id = 1;
```

Logo você terá a seguinte imagem:

<div align="center"><img src="https://i.imgur.com/RdbiTfT.png" title="source: imgur.com" width="50%"/></div>

<div align="left"> <a href="https://www.tutorialsteacher.com/sqlserver/update-data" target="_blank"><b>Documentação: <i>Update </i></b></a>




<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/> Atualizando dados na Tabela</h3>



Para apagar um ou mais registros da tabela, utilizamos o comando `DELETE`. **Exemplo**: queremos apagar o produto que tenha o id igual a 2. 

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="300px"/> | **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao construir essa Query, pois obrigatoriamente você DEVE COLOCAR o comando WHERE, pois caso contrário o MSQL Server Management Studio irá APAGAR TODOS OS REGISTROS, sem a possibilidade de desfazer a operação.* |
| ------------------------------------------------------------ | :----------------------------------------------------------- |

Nesse caso executamos a seguinte query: 

<h4>DELETE</h4>

```sql
DELETE FROM tb_produtos WHERE id = 2;
```

Ao executar a query, aparecerá no log/mensagem do campo de Output uma mensagem que a exclusão foi concluída, e para visualizar se o produto foi realmente excluído basta executa a seguinte query para listar os produtos:

```sql
SELECT * FROM tb_produtos;
```

Logo você terá a seguinte imagem:

<div align="center"><img src="https://i.imgur.com/474irKi.png" title="source: imgur.com" width="50%"/></div>

<div align="left"> <a href="https://www.tutorialsteacher.com/sqlserver/delete-data" target="_blank"><b>Documentação: <i>Delete </i></b></a>




<h3><img src="https://i.imgur.com/ZL3AFqF.png" title="source: imgur.com" width="30px"/> Modificando a Estrutura da Tabela</h3>



Esse comando é usado para adicionar, excluir ou modificar as colunas (atributos), em uma tabela existente, além de poder adicionar ou excluir restrições de uma tabela, como chaves primárias e/ou chaves estrangeiras. 

**Exemplo 01:** Queremos modificar/atualizar o tipo de um Atributo/Coluna, fazendo com que o campo preco tenha 6 dígitos, sendo que 2 deles são casas decimais (1000.50). Nesse caso executamos a seguinte query: 

<h4>ALTER TABLE - ALTER COLUMN</h4>

```sql
ALTER TABLE tb_produtos ALTER COLUMN preco decimal(6,2);
```

Observe que após esta alteração o atributo preco será exibido com as casas decimais:

```sql
SELECT * FROM tb_produtos;
```

<div align="center"><img src="https://i.imgur.com/wCtLLKY.png" title="source: imgur.com" width="60%"/></div>




| <img src="https://i.imgur.com/L338M2G.png" title="source: imgur.com" width="120px"/> | **DESAFIO:** *Observe que mesmo corrigindo as casas decimais, o preço da pêra continua arredondado para R$ 4.00. Como podemos corrigir o valor deste produto?* |
| ------------------------------------------------------------ | :----------------------------------------------------------- |

**Exemplo 02:** Queremos adiciona um novo Atributo/Coluna na  Tabela. Nesse caso executamos a seguinte query: 

<h4>ALTER TABLE - ADD</h4>

```sql
ALTER TABLE tb_produtos ADD descricao varchar(255);
```

**Exemplo 03:** Queremos remover um Atributo/Coluna da tabela. Nesse caso executamos a seguinte query: 

<h4>ALTER TABLE - DROP</h4>

```sql
USE [db_quitanda]
GO
ALTER TABLE [dbo].[tb_produtos] DROP COLUMN [descricao]
GO
```

**Exemplo 04:** Queremos alterar o nome de um Atributo/Coluna da tabela. Nesse caso executamos a seguinte query: 

<h4>sp_rename</h4>

```
sp_rename 'tb_produtos.nome', 'nomeproduto', 'COLUMN';
```

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="80px"/> | **DICA:** *Após executar as consultas, execute um <code>select * from tb_produtos;</code> e veja as alterações.* |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<div align="left"><a href="https://www.tutorialsteacher.com/sqlserver/alter-table-add-columns" target="_blank"><b>Documentação: <i>Alter Table </i></b></a>
