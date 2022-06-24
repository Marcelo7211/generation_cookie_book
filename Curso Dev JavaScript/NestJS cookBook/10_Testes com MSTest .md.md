﻿﻿<h1>Projeto - TesteBlogPessoal </h1>



<h2>1. O Projeto TesteBlogPessoal</h2>

O Projeto TesteBlogPessoal será o nosso teste que verificará a integridade das funcionalidades  do projeto BlogPessoal, neste tutorial verificaremos a funcionalidade de getAllTemas.



 <h2>👣 Passo 01 - Criando um projeto de teste para o Blog pessoal</h2>

1. Clique com um botão direito sobre a solution do projeto e clique em criar um novo projeto.

<div align="center"><img src="https://i.imgur.com/XMID3zN.png" title="source: imgur.com" /></div>

2. Pesquise por mstest e clique em Projeto de Teste MSTest.

<div align="center"><img src="https://i.imgur.com/XKtNcBj.png" title="source: imgur.com" /></div>

3. Determine o nome do seu projeto como **TesteBlogPessoal**.

<div align="center"><img src="https://i.imgur.com/c0nNeVl.png" title="source: imgur.com" /></div>

4. Determine a versão do framework como  .NET 5.0 (atual)

<div align="center"><img src="https://i.imgur.com/wO4v7LJ.png" title="source: imgur.com" /></div>

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes para determinar a versão do .NET 5.0, caso crie o projeto errado deverá criar o projeto novamente.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

9. Clique em criar e pronto, o projeto esta criado.

<br />

<h2>👣 Passo 02 - Configurarando o projeto
1. Exclua o arquivo UnityTest1.cs clicando com botão direito sobro o arquivo e clicando em deletar.

<div align="center"><img src="https://i.imgur.com/xDNfC6R.png" title="source: imgur.com" /></div>    

<br />

2.  Crie 2 novos arquivos para o projeto **TemaRepositoryFake.cs** e **TestTemaController**

<div align="center"><img src="https://i.imgur.com/VIaGV7t.png" title="source: imgur.com" /></div>    

<br />

<h2>👣 Passo 03 - referenciando o projeto blogPessoal para o projeto de teste

1. Clique com botão direito sobre o projeto TesteBlogPessoal.
2. Clique em referencia de projeto

<div align="center"><img src="https://i.imgur.com/d7mzDAe.png" title="source: imgur.com" /></div>    

<br />

3. Selecione o projeto blogPessoal e clique em ok.

<div align="center"><img src="https://i.imgur.com/Zq8wDil.png" title="source: imgur.com" /></div>    

<br />

<h2>👣 Passo 04 - Editando as camadas de repository e controller do projeto de teste</h2>

### Editando **TemaRepositoryFake.cs**

Criaremos um repository Fake onde terá como função simular um banco de dados com conexão a ele.  

1. Edite o arquivo **TemaRepositoryFake.cs** como o código abaixo:


```c#
using blogPessoal.Model;
using blogPessoal.Repository;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace TesteBlogPessoal
{
    public class TemaRepositoryFake : ITemaRepository
    {
        private readonly List<Tema> _temas;
        public TemaRepositoryFake()
        {
            _temas = new List<Tema>()
            {
                new Tema() { Id = 1, Descricao = "Asp.net"},
                new Tema() { Id = 2, Descricao = "CSharp"},
                new Tema() { Id = 3, Descricao = "React"},
                new Tema() { Id = 4, Descricao = "SqlServer"},
                new Tema() { Id = 5, Descricao = "JavaScript"},

            };
        }

        public Tema Create(Tema tema)
        {
            tema.Id = GeraId();
            _temas.Add(tema);
            return tema;
        }

        public void Delete(int id)
        {
            throw new System.NotImplementedException();
        }

        public Tema Get(int Id)
        {
            return _temas.Where(a => a.Id == Id)
               .FirstOrDefault();
        }

        public List<Tema> GetAll()
        {
            return _temas;
        }

        public List<Tema> GetByDescricao(string descricao)
        {
            throw new System.NotImplementedException();
        }

        public Tema Update(Tema tema)
        {
            throw new System.NotImplementedException();
        }
        static int GeraId()
        {
            Random random = new Random();
            return random.Next(1, 100);
        }
    }
}
```

<br />

2.  Simularemos os registros do banco de Dados através de um List.
3.  O método Create chama o método Add da List para adicionar um novo objeto a List.
4.  O método Get chama o método Where onde é procurado o objeto Tema dentro da List através do  id
5.  O método GetAll retorna todos os Itens da List.
6. O método GeraId gera id de forma aletória de um até 100 através do objeto Random.

<br />

### Editando **TestTemaController.cs**

Criaremos um Controller Fake onde terá como função simular o comportamento de um Controller real para validarmos situaçõs que podem ocorrer com as funcionalidade da api. As situações a serem testas serão:  

**GetIsPresent()** Se o repository fake está prenchido com alguma registro.

**Get_TotalIgualACinco()** Se o total de registros cadastrados é igual a 5.

**Get_UltimoIgualAJavaScript()** Se o ultimo registro preenchido tem como descrição **JavaScript**.

**Get_UltimoIgualASqlServer()** Se o ultimo registro preenchido tem como descrição **SqlServer**.



1. Edite o arquivo **TestTemaController.cs** como o código abaixo:


```c#
using blogPessoal.Controllers;
using blogPessoal.Repository;
using Microsoft.VisualStudio.TestTools.UnitTesting;


namespace TesteBlogPessoal
{
    [TestClass]
    public class TestTemaController
    {
        blogPessoal.Controllers.TemaController _controller;
        ITemaRepository _service;
        public TestTemaController()
        {
            _service = new TemaRepositoryFake();
            _controller = new blogPessoal.Controllers.TemaController(_service);
        }
        [TestMethod]
        public void GetIsPresent()
        {
            // Act
            var okResult = _controller.GetAllTemas();
            // Assert
            Assert.IsNotNull(okResult);
        }
        [TestMethod]
        public void Get_TotalIgualACinco()
        {
            // Act
            var okResult = _controller.GetAllTemas().Count;
            // Assert

            Assert.AreEqual(5, okResult);
        }

        [TestMethod]
        public void Get_UltimoIgualAJavaScript()
        {
            // Act
            var okResult = _controller.GetAllTemas();
            // Assert

            Assert.AreEqual("JavaScript", okResult[4].Descricao);
        }

        [TestMethod]
        public void Get_UltimoIgualASqlServer()
        {
            // Act
            var okResult = _controller.GetAllTemas();
            // Assert

            Assert.AreEqual("SqlServer", okResult[4].Descricao);
        }

    }

}
```

<br />


<h3>3.1. Anotações do MSTest</h3>

<table width=100%>
	<tr>
        <td width=15%><b>MSTest </b></td>
		<td width=70%><b>Descrição</td>
	</tr>
	<tr>
		<td><i> [TestClass] </i></td>
        <td>A anotação MSTest  indica que a classe deve ser executado como um teste.</td>
	</tr>
	<tr>
		<td><i>[TestMethod]</i></td>
        <td>A anotação MSTest  indica que o método deve ser executado como um teste.</td>
	</tr>



<h3>3.2. Asserções - MSTest</h3>

Asserções (Assertions) são métodos utilitários para testar afirmações em testes (1 é igual a 1, por exemplo).

<table width=100%>
	<tr>
        <td width=30%><b>Assertion</b></td>
		<td width=70%><b>Descrição</b></td>
	</tr>
	<tr>
		<td><i>Assert.AreEqual(expected value, actual value)</i></td>
        <td>Afirma que dois valores são iguais.</td>
	</tr>
	<tr>
		<td><i>Assert.IsTrue(boolean condition)</i></td>
        <td>Afirma que uma condição é verdadeira.</td>
	</tr>
	<tr>
		<td><i>Assert.IsFalse(boolean condition)</i></td>
		<td>Afirma que uma condição é falsa.</td>
	</tr>
	<tr>
		<td><i>Assert.IsNotNull()</i></td>
		<td>Afirma que um objeto não é nulo.</td>
	</tr>
	<tr>
		<td><i>Assert.IsNull(Object object)</i></td>
		<td>Afirma que um objeto é nulo.</td>
	</tr>
	<tr>
		<td><i>Assert.AreSame(Object expected, Object
            actual)</i></td>
		<td>Afirma que dois objetos referem-se ao mesmo objeto.</td>
	</tr>
	<tr>
		<td><i>Assert.AreNotSame(Object expected, Object
actual)</i></td>
		<td>Afirma que dois objetos não se referem ao mesmo objeto.</td>
	</tr>
	<tr>
		<td><i>Assert.Equals(expectedArray, resultArray)</i></td>
		<td>Afirma que array esperado e o array resultante são  iguais.</td>
	</tr>
</table>

<br />



<h2>👣 Passo 05 - Executando os testes



Clique com botão direito sobre o projeto TestBlogPessoal e em seguida clique em executar Testes.

<div align="center"><img src="https://i.imgur.com/jo10XUp.png" title="source: imgur.com" /></div>    

<br />



<div align="center"><img src="https://i.imgur.com/l1NEXow.png" title="source: imgur.com" /></div>    

<br />

Repare que todos os testes conferem ao que está registrado na List menos Get_UltimoIgualASqlServer(), porque o ultimo registro esta cadastrado  **JavaScript** e não **SqlServer**.




<h2>3. O framework MSTest </h2>

O MSTest é um Framework de testes de código aberto para a linguagem C#, que é usado para escrever e executar testes automatizados e repetitivos, para que possamos ter certeza que nosso código funciona conforme o esperado. 

O MSTest fornece:

• Asserções para testar os resultados esperados.
• Recursos de teste para compartilhar dados de teste comuns.
• Conjuntos de testes para organizar e executar testes facilmente.
• Executa testes gráficos e via linha de comando.

O MSTest é usado para testar:

• Um objeto inteiro
• Parte de um objeto, como um método ou alguns métodos de interação
• Interação entre vários objetos

<div align="left"> <a href="https://docs.microsoft.com/pt-br/dotnet/core/testing/unit-testing-with-mstest" target="_blank"><b>Documentação: MSTest </b></a>

<div align="left"><img src="https://i.imgur.com/bQGvf3h.png" title="source: imgur.com" width="30px"/> <a href="https://github.com/Marcelo7211/blog-pessoal-aspnet-core/tree/CG-89-construcao-cook-book-asp-net-core-testes-unitarios" target="_blank"><b>Código fonte do projeto</b></a>

​    

