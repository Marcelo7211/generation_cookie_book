
<h1>Projeto 02 - Blog Pessoal - CRUD 01</h1>

O que veremos por aqui:

1. Apresentação do Projeto 
2. Criar o Projeto no Spring Initializr
2. Conhecer o arquivo pom.xml
3. Configurar o Banco de dados da aplicação
   
<h2>1. O Projeto Blog Pessoal</h2>

O Projeto Blog Pessoal será o nosso Projeto Guia no aprendizado do Framework Spring e suas principais funcionalidades. Todo o código que implementarmos no projeto Blog Pessoal servirá de base para a construção do Projeto Integrador, que sempre receberá novas funcionalidades depois que você adquirir os conhecimentos necessários através do Blog Pessoal.Veja o Diagrama de Classes do Projeto Blog Pessoal na figura abaixo:

<div align="center"><img src="https://i.imgur.com/G71SCJ0.png" title="source: imgur.com" /></div>

<br />

O Projeto será composto por 3 Recursos (Conjunto de Classes e Interfaces responsáveis por mapear um tipo de Objeto e persistir no Banco de dados Relacional) e uma Classe auxiliar:

| Classe           | Descrição                                                    |
| ---------------- | ------------------------------------------------------------ |
| **Postagem**     | Recurso responsável por definir  Objeto Postagem (posts) do Blog Pessoal |
| **Tema**         | Recurso responsável por classificar as postagens através do Objeto Tema |
| **Usuario**      | Recurso responsável por definir o Objeto Usuário, que poderá acessar e criar postagens no Blog Pessoal |
| **UsuarioLogin** | Classe auxiliar, que será utilizada para efetuar login no Blog Pessoal |

Os Recursos irão gerar tabelas no Banco de dados da aplicação. A Classe auxiliar não irá gerar uma tabela no Banco de dados da aplicação, ela servirá de Classe auxiliar na implementação da Segurança da aplicação. Os recursos serão implementados na mesma sequência da tabela acima.

Antes de começar a criar as nossas Classes, vamos criar o nosso Projeto Spring Boot no gerador de templates Spring Initializr e configurar o Banco de dados da aplicação.





 <h2>👣 Passo 01 - Abrindo o Visual Studio</h2>

1. Abra o seu Visual Studio e clique em criar projeto.

<div align="center"><img src="https://i.imgur.com/8yH2gBz.png" title="source: imgur.com" /></div>

2. Pesquise por Api na barra de pesquisa e selecione a opção de API Web do Asp.net Core e clique em proximo.

<div align="center"><img src="https://i.imgur.com/Bj8qVJa.png" title="source: imgur.com" /></div>

3. Determine o nome do seu projeto como **Hello World**.

<div align="center"><img src="https://i.imgur.com/RLnFWhS.png" title="source: imgur.com" /></div>

4. determine a versão do framework como  .NET 5.0 (atual)
5. determine autenticação como nenhuma.
6. desmarque a opção para HTTPS
7. desabilite a opção do Docker
8. Habilite  o suporte a OpenApi

<div align="center"><img src="https://i.imgur.com/6AK3TTz.png" title="source: imgur.com" /></div>

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes para determinar a versão do .NET 5.0 desabilitar HTTPS e Docker e Habilitar o suporte OpenAPI, caso crie o projeto errado deverá criar o projeto novamente.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

9. Clique em criar e pronto projeto esta criado.

<br />

<h2>👣 Passo 02 - Configurarando e instalando as dependências 

​    Agora vamos instalar as dependências necessárias para  realizarmos a comunicação do asp.net com o banco de dados sql server:

1. clique com botão direito sobre dependência 
2. clique em gerenciar pacotes do Nuget

<div align="center"><img src="https://i.imgur.com/biUST6C.png" title="source: imgur.com" /></div>    

<br />

3. procure por Microsoft.EntityFrameworkCore e instale a versão 5.0.13

<div align="center"><img src="https://i.imgur.com/udc8nsV.png" title="source: imgur.com" /></div>    

<br />

4. procure por Microsoft.EntityFrameworkCore.SqlServer e instale a versão 5.0.13

<div align="center"><img src="https://i.imgur.com/shQoF2E.png" title="source: imgur.com" /></div>    

<br />

5. procure por Microsoft.EntityFrameworkCore.Tools e instale a versão 5.0.13

<div align="center"><img src="https://i.imgur.com/rbi0IvG.png" title="source: imgur.com" /></div>    

<br />

6. Cerifique se as bibliotecas estão instaladas em instalado

<div align="center"><img src="https://i.imgur.com/LnciBSS.png" title="source: imgur.com" /></div>    

<br />

<h2>👣 Passo 03 - Configurar a Conexão com o Banco de dados</h2>

Diferente do Projeto Hello World, no Projeto Blog Pessoal vamos utilizar um Banco de dados para persistir os nossos Objetos, ou seja, gravar dados nas Tabelas. 

Antes de iniciarmos o processo de Desenvolvimento do código das nossa Classes, precisamos configurar o o acesso ao nosso Banco de dados, caso contrário ao executar o projeto receberemos uma mensagem de erro no Console, informando que o não foi configurado o acesso ao Banco de dados:



Crie a estrutura de pasta como descrito na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/zDnJfwO.png" title="source: imgur.com" /></div>    

<div align="center"><img src="https://i.imgur.com/l1geQoe.png" title="source: imgur.com" /></div>    

Crie uma pasta **Data -> com arquivo AppContext.cs**

Crie uma pasta **Model -> com arquivo Tema.cs**

**Para criar um nova classe clique na pasta que desejaa criar com botão direito clique em adicionar novo item**

### Configurando o appsetting.json

```
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=DESKTOP-8KO7ED6;Initial Catalog=db_blog_pessoal;Integrated Security=True"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

<br />



| Item                  | Descrição                                                    |
| --------------------- | ------------------------------------------------------------ |
| **ConnectionStrings** | cria uma string de conexão                                   |
| **DefaultConnection** | determina o nome da string de conexeção como DefaultConnection |
| **Server**            | Determina o endereço a ser conectado do servidor no caso local |
| **Initial Catalog**   | Determina o banco a ser criado ou conectado                  |
| **Security**          | determina que essa conexão será feita de forma segura        |
| **Logging**           | determina as configurações do log no console                 |

<h2>Observações importantes:</h2>

- O Nome do banco de dados deve seguir o padrão **db_nome-do-banco**. O prefixo **db** indica que se trata de um Database (Banco de dados). O nome do banco é recomendado que seja **o mesmo do projeto** (blogpessoal), em **letras minúsculas**, **sem espaços em branco ou caracteres especiais e acentos**. Para separar as palavras em um nome composto, utilize o _ (underline). **Exemplo:** db_blog_pessoal.
- O endereço **localhost** é o endereço local, ou seja, o seu próprio computador. Quando a aplicação estiver na nuvem, o endereço do Banco de dados será alterado para um endereço remoto.
- Para fins de aprendizagem, estamos utilizando no SGBD SQLServer o usuário **root**. Vale ressaltar que no mercado de trabalho, uma aplicação em produção, jamais utilizará o usuário root, por se tratar do usuário administrador do SGBD, que tem plenos poderes sobre o Servidor. Em geral, o DBA (Database Administrator), cria um usuário apenas com os direitos de acesso que a aplicação irá precisar.

<br /><br />

<h2>Anexo I - Modos de inicialização do Banco de dados</h2>



| Forma               | Descrição                                                    |
| ----------------------- | ------------------------------------------------------------ |
| **update**              | O modelo de objeto criado com base nos mapeamentos (Anotações na Classe Model), é comparado com o esquema existente, e então o EF core atualiza o esquema de acordo com as diferenças. Ele nunca exclui as tabelas ou colunas existentes, mesmo que não sejam mais exigidas pelo aplicativo. Nesta opção os dados persistidos não são apagados. |
| **create**              | O EF core primeiro elimina todas as tabelas existentes no Banco de dados e então cria novas tabelas. Com esta opção todos os seus dados serão perdidos a cada inicialização do projeto. |
| **create-drop**         | Semelhante ao create, com a adição de que o EF core irá descartar o banco de dados depois que todas as operações forem concluídas. Esta opção é normalmente utilizada para testes de unidade. |
| **validate**            | Verifica apenas se a estrutura do Banco de dados corresponde às entidades definidas na **Classe Model**. Se o esquema não corresponder, a inicialização do aplicativo lançará um erro (Exception). |
| **none**                | Desativa a inicialização do Banco de dados.                  |

<br />

<h3>Entity FrameworkCore</h3>

O **EF core** é um framework para o mapeamento objeto-relacional escrito na linguagem C$ , cujo objetivo é diminuir a complexidade entre os programas C#, baseado no modelo orientado a objeto, que precisam trabalhar com um banco de dados do modelo relacional (presente na maioria dos SGBDs). Em especial, no desenvolvimento de consultas e atualizações dos dados.

<div align="left"> <a href="https://docs.microsoft.com/pt-br/ef/" target="_blank"><b>Site Oficial: Entity FrameworkCore</b></a>
<br />
<div align="left"><img src="https://i.imgur.com/bQGvf3h.png" title="source: imgur.com" width="30px"/> <a href="https://github.com/Marcelo7211/blog-pessoal-aspnet-core/tree/CG-87-construcao-cook-book-asp-net-core-crud" target="_blank"><b>Código fonte do projeto</b></a>
