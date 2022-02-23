﻿<h1>Entity Framework</h1>

Vamos conhecer o Entity Framework, parte integrante do Asp.net, responsável por criar e manipular o Banco de dados da aplicação.

<h2>1. O que é Entity Framework?</h2>

# Documentação do Entity Framework

O Entity Framework Core é um mapeador moderno de banco de dados de objeto para .NET. Ele dá suporte a consultas LINQ, controle de alterações, atualizações e migrações de esquema. O EF Core funciona com muitos bancos de dados, incluindo o Banco de Dados SQL (local e do Azure), o SQLite, o MySQL, o PostgreSQL e o Azure Cosmos DB.

<h3>1.1 Mapeamento Objeto Relacional</h3>

**Mapeamento Objeto Relacional** é a representação de uma Tabela de um Banco de dados Relacional (MySQL, PostgreSQL, Oracle, SQL Server e etc), através de Classes C#, que dentro do contexto Asp.NET e seguindo o Modelo MVC, são implementadas na Camada Model. Essa técnica de mapeamento também é conhecida como **ORM** ou *Object Relational Mapping*.

<br /><br />

Na prática, o Mapeamento cria a Relação de equivalência abaixo:

| Banco de dados |       | Linguagem Orientada a Objetos |
| -------------- | ----- | ----------------------------- |
| Tabela         | **🡪** | Classe                        |
| Coluna         | **🡪** | Atributo                      |
| Registro       | **🡪** | Objeto                        |

Enquanto que no banco de dados temos Tabelas, Colunas e Registros, em uma linguagem Orientada a Objetos, como o C# , temos o equivalente com Classes, Atributos e Objetos. Além dessa equivalência, o Entity Framework utiliza algumas anotações que adicionarão metadados (Chave Primária, Nome da Tabela, Auto Incremento e etc), às classes e permitirão os frameworks ORM, como o Entity Framework,  entrarem em ação na geração das tabelas dentro do nosso Banco de dados.

<br />

<h3>Por quê utilizar Entity Framework?</h3>

Escrever SQL para consultas, inserções e atualizações, por mais que não seja complexo, é uma tarefa repetitiva e chata.

A primeira vantagem é que o Entity Framework trás códigos SQL para consultas, inserções e atualizações básicas prontas. 

A segunda vantagem é que para criarmos consultas personalizadas podemos utilizar as **Select Methods**, que a partir da combinação de palavras chave, que substituem as instruções SQL, podemos criar consultas de forma rápida.

A terceira vantagem é a simplificação do  código-fonte da aplicação. Como muita coisa é automatizada, bem menos  código é escrito para as mesmas funções.

