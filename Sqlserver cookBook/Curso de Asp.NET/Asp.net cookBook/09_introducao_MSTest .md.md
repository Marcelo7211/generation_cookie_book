﻿﻿﻿<h1>Teste de Software - MSTest - Introdução</h1>

O teste de software é uma forma de avaliar a qualidade da aplicação e reduzir os riscos de falhas no código ao ser colocado  em operação (Produção). Testar não se resume apenas em executar testes e verificar os resultados. **Executar** testes é apenas umas das atividades. Planejamento, análise, modelagem e implementação dos testes,  relatórios de progresso, resultado e avaliação da qualidade, também são  partes de um **processo de testes**.
Testar software não é somente **verificar** se os requisitos foram atendidos, atribui-se ao teste de software também a **validação**, ou  seja, verificar se o sistema atenderá às necessidades do usuário e de outras partes interessadas em seu(s) ambiente(s) operacional(is).

<h2>1. A Pirâmide de Testes</h2>

A **Pirâmide de Testes** é uma representação gráfica que nos diz para agrupar testes de software em diferentes tipos. A pirâmide ilustra de forma implícita a quantidade de testes que devem ser realizados em tipo, os custos e o tempo de duração.

<div align="center"><img src="https://i.imgur.com/seQZN6f.png" title="source: imgur.com" width="75%"/></div>

Observe que os testes na base são mais rápidos e baratos do que os testes no topo da pirâmide.

Existem três tipos de teste:

- Teste de Unidade
- Teste de Integração
- Teste End to End (E2E)

<h3>1.1. Teste de unidade</h3>

Uma unidade pode ser uma função, uma classe, um pacote ou um subsistema. Portanto, o termo teste de unidade refere-se à prática de testar pequenas unidades do seu código, para garantir que funcionem conforme o esperado.

O Teste de Unidade é o teste mais comum, porquê além de ser muito rápido é o teste mais barato porquê pode ser criado pela própria pessoa desenvolvedora durante o processo de codificação.

<h3>1.2. Teste de integração</h3>

Teste de Integração é a fase do teste de software em que os módulos são combinados e testados em conjunto, para checar como os módulos se comportam quando interagem entre sí.

O Teste de Integração é um pouco mais lento e um pouco mais caro do que o Teste de Unidade porquê aumenta a complexidade.

<h3>1.3. Teste End to End</h3>

O Teste de ponta a ponta é uma metodologia de teste de software para  testar um fluxo de aplicativo do início ao fim. O objetivo deste teste é simular um cenário real do usuário e validar o sistema em teste e seus componentes para integração e integridade dos dados.

O Teste End to End é mais lento (depende de pessoas para testarem o software como um todo em produção ou versão beta), o que o torna muito mais caro do que os Testes de Unidade e Integração, o que explica serem realizados em menor quantidade.

<h3>1.4. O que deve ser testado?</h3>

A prioridade sempre será escrever testes para as partes mais complexas ou críticas de seu código, ou seja, aquilo que é essencial para que o código traga o resultado esperado. **Exemplo:** Em um e-commerce a finalização da compra é um ponto crítico da aplicação.

<h2>2. .NET Testing</h2>

O .NET Testing é parte integrante do .NET e oferece suporte a testes de unidade e testes de integração, utilizando alguns Frameworks de Teste C#. 
Ao criar um projeto com o .NET, automaticamente as dependências de testes já são inseridas no projeto como veremos adiante.

<div align="left"> <a href="https://docs.microsoft.com/pt-br/dotnet/core/testing/" target="_blank"><b>Documentação Oficial</b></a>



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

​    


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
<br /><br /><br /><br /><br />

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


| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="150px"/> | <p align="justify">**DICA:** *Ao escrever testes, sempre verifique se a importação dos pacotes do MSTest na Classe de testes estão corretos.</p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br /><br /><br /><br /><br /><br /><br />

<h2>5. Quais testes faremos?</h2>

Vamos criar testes nas Camadas Repository e Controller do Recurso Usuário do Blog Pessoal.
Para executarmos os testes;
Antes de prosseguir, assegure que o seu projeto Blog Pessoal não esteja em execução no Visual Studio.



