﻿<h1>Primeiros passos com Asp.net core</h1>

O Asp.net core é uma ferramenta que visa facilitar o processo de  configuração e publicação de aplicações que utilizem o ecossistema  Dot.net. 

O Asp.net core fornece a maioria dos componentes baseados no Dot.net, necessários em aplicações de maneira pré-configurada, tornando  possível termos uma aplicação rodando em produção rapidamente e com o  esforço mínimo de configuração e implantação.  

<div align="left"><a href="https://docs.microsoft.com/pt-br/aspnet/core/?view=aspnetcore-6.0" target="_blank"><b>Documentação do Asp.net</b></a>

<h2>1. Microsoft NuGet</h2>

No Universo C#, o NuGet é uma ferramenta usada para construir e gerenciar qualquer projeto C#, tornando o trabalho diário dos desenvolvedores mais fácil, além de simplificar a compreensão de qualquer projeto baseado na linguagem C#. 

<div align="left"><a href="https://docs.microsoft.com/pt-br/nuget/" target="_blank"><b> Documentação: NuGet</b></a></div>

Entre as principais características do C#, destaca-se:

<h3>1.1 Gerenciador de dependências</h3>

O Nuget é responsável por fazer o download das bibliotecas que você vai precisar no seu projeto. Para efetuar esta tarefa, o Nuget utiliza o arquivo **.csproj**, onde você precisa declarar todas as dependências necessárias para o seu projeto.

<h3>1.2 Repositório central</h3>

Todas as ferramentas e bibliotecas utilizadas nos projetos Asp.NET Boot estão disponíveis em um único servidor na nuvem chamado **Nuget Package**. O Nuget Package facilita e centraliza o download de todas as dependências independente de serem as oficiais do Asp.net ou Desenvolvidas por outras Empresas ou Pessoas Desenvolvedoras ,  dispensando a necessidade de procurar as dependências no Google, por exemplo.

<div align="left"> <a href="https://www.nuget.org/packages" target="_blank"><b>Site Oficial: Nuget Package</b></a></div>

<br />
 <div align="center"><img src="https://i.imgur.com/uspCfpr.png" title="source: imgur.com" /></div>

<h3>1.3 Automatizador de tarefas</h3>

Um projeto que possui muitas bibliotecas e muitas dependências gera alguns problemas no dia a dia, tais como: manter todas atualizadas, fazer o build da sua aplicação, realizar alguns testes e etc. O **NuGet** auxilia nestes e outros processos através dos seus scripts prontos que automatizam todas estas tarefas.

<br /><br />

<h2>2. Como funciona um projeto Asp.net core?</h2>

1. A Classe Principal, que possui o método main, inicia um servidor WEB (Internet Information Services), que vai gerenciar todas as URL's (Endpoints) disponíveis na API.
2. Cada URL deve ser mapeada para um determinado método de uma classe. 
3. A execução desse método retornará uma resposta quando acionamos a URL. 
3. A partir daí, criamos nossos objetos que implementarão todas as lógicas necessárias.

<div align="left"><a href="https://www.iis.net/" target="_blank"><b>Site Oficial: Internet Information Services</b></a></div>

<h3>2.1 Como planejar um projeto Asp.net core?</h3>

Quais ENDPOINTS vamos oferecer? (Um Endpoint é uma URL associada a um método do protocolo HTTP: GET, POST, PUT, DELETE).

Em geral, temos 1 Endpoint para cada método HTTP (podemos ter mais de um desde que os endereços sejam diferentes), em cada objeto do nosso modelo de negócios:

Objeto de Negócios: **PRODUTO**

- URL para recuperar dados de um produto (GET) 
- URL para inserir novo produto (POST)
- URL para atualizar dados de um produto (PUT)
- URL para remover um produto do sistema (DELETE)

Como estes ENDPOINTS estarão estruturados no nosso sistema? Vamos discutir isto Mais adiante...

<br /><br />

<h1>Projeto 01 - Hello World!</h1>

 <h2>👣 Passo 01 - Abrindo o Visual Studio</h2>

1. Abra o seu Visual Studio e clique em criar projeto.

<div align="center"><img src="https://i.imgur.com/8yH2gBz.png" title="source: imgur.com" /></div>

2. Pesquise por Api na barra de pesquisa e selecione a opção de API Web do Asp.net Core e clique em proximo.

<div align="center"><img src="https://i.imgur.com/Bj8qVJa.png" title="source: imgur.com" /></div>

3. Determine o nome do seu projeto como **Hello World**.

<div align="center"><img src="https://i.imgur.com/f8nr0f6.png" title="source: imgur.com" /></div>

4. determine a versão do framework como  .NET 5.0 (atual)
5. determine autenticação como nenhuma.
6. desmarque a opção para HTTPS
7. desabilite a opção do Docker
8. Habilite  o suporte a OpenApi

<div align="center"><img src="https://i.imgur.com/6AK3TTz.png" title="source: imgur.com" /></div>

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes para determinar a versão do .NET 5.0 desabilitar HTTPS e Docker e Habilitar o suporte OpenAPI, caso crie o projeto errado deverá criar o projeto novamente.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

9. Clique em criar e pronto projeto esta criado.

<div align="center"><img src="https://i.imgur.com/rJHWPSZ.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 02 Entendendo a Estrutura do nosso projeto</h2>

<div align="center"><img src="https://i.imgur.com/rJHWPSZ.png" title="source: imgur.com" /></div>

| Item                     | Descrição                                                    |
| ------------------------ | ------------------------------------------------------------ |
| **Startup.cs**           | Classe responsavel por inicializar o projeto Asp.net         |
| **appsettings.json**     | **application.properties** É o responsável por manter as configurações de Data, Hora, Fuso-horário, Banco de Dados, entre outras. |
| **Dependecies**          | Responsável por gerenciar as dependências a ser instalada em um projeto asp.net |
| **Program.cs**           | A classe de program.cs é a classe  onde podemos criar um host para a aplicação web. |
| **Solution Hello World** | É o arquivo principal de configuração do **Asp.net**. É um arquivo XML que contém informações sobre o projeto e detalhes de configuração usados pelo NuGet para construir o projeto. <br /> **Não apague este arquivo e ao fazer alterações tenha muito cuidado para manter a estrutura do arquivo**. |

<h2>👣 Passo 03 - Criando a primeira Classe Controller</h2>

Primeiramente precisamos apagar 2 arquivos do nosso projeto.

1. WeatherForecast.cs
2. WeatherForecastController.cs

<div align="center"><img src="https://i.imgur.com/rJHWPSZ.png" /></div>

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes para apagar os arquivos certos, descritos no tema acima* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

Primeiro vamos criar  a classe **Controller**.

1. Clique com o botão direito do mouse sobre a pasta controller
2. Na sequência, clique na opção **Adicionar 🡪 Controlador**

<div align="center"><img src="https://i.imgur.com/GCszrVU.png" title="source: imgur.com" /></div>

<br /><br /><br /><br />

3. Selecione a opção **Controlador MVC - Vazio ** e clique em adicionar

<div align="center"><img src="https://i.imgur.com/5s8htgX.png" title="source: imgur.com" /></div>

<br /><br /><br />

4. Na sequência, clique na opção **Controlador MVC - Vazio **, escolha o nome de HomeController e clique em adicionar

<div align="center"><img src="https://i.imgur.com/0xrRRz3.png" title="source: imgur.com" width="85%"/></div>

5. E pronto a estrutura básica de um controlador foi criada.

<div align="center"><img src="https://i.imgur.com/cx7nU11.png" title="source: imgur.com" width="380px"/></div>

 Agora vamos criar o código da Classe Controladora **HomeController **, igual a figura abaixo:

```c#
using Microsoft.AspNetCore.Mvc;

namespace HelloWorld.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class HomeController : Controller
    {

        [HttpGet]
        public string HelloWorld()
        {
            return "Ola Mundo";
        }

    }
}

```

Na **** a anotação **[ApiController]** deﬁne que a classe é do tipo controladora rest, que receberá requisições que serão compostas por:

- **URL:** Endereço da requisição (/hello-world)
- **Verbo:** Define qual método HTTP será acionado na Classe controladora.
- **Corpo da requisição (Request Body):** Objeto que contém os dados que serão criados ou atualizados. 

Após receber e processar a requisição, a Classe Controladora Responderá a estas requisições com:

- Um **Código de Status HTTP** pertinente a operação que está sendo realizada
- O resultado do processamento (Dados de uma consulta, por exemplo) inserido diretamente no corpo da resposta (**Response Body**)

A anotação **[Route("api/[controller]")]** é usada para determinar a rota a ser acessada no controller ou seja http://localhost:5000/api{nome do controller} ou seja http://localhost:5000/api/HomeController.

A herança**: Controller** define que a classe se comportara como um controller asp.net.


A anotação **[HttpGet]** mapeia solicitações HTTP GET para métodos de tratamento específicos, ou seja, indica que o método helloWorld() responderá a todas as requisições do tipo **HTTP GET**, enviadas no endereço **http://localhost:5000/api/HomeController**, do recurso hello-world.

O método **helloWorld()** retorna uma mensagem de boas vindas, ou seja, quando o endereço for enviado via Postman ou via Browser (Navegador), será exibida a mensagem de boas vindas **"Ola Mundo!"**

Para concluir, não esqueça de Salvar o código (**File 🡪 Save All**)

<div align="left"><img src="https://i.imgur.com/cDPH4tl.png" title="source: imgur.com" width="25px"/> <a href=" https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods" target="_blank"><b>Documentação: HTTP Methods Request</b></a></div>

<div align="left"><img src="https://i.imgur.com/cDPH4tl.png" title="source: imgur.com" width="25px"/> <a href=" https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status" target="_blank"><b>Documentação: HTTP Status Code</b></a></div>

<div align="left"><a href="https://docs.microsoft.com/pt-br/dotnet/api/system.web.http.apicontroller?view=aspnetcore-2.2" target="_blank"><b>Documentação: <i>@RestController</i></b></a></div>

<div align="left"> <a href="https://docs.spring.io/spring-framework/docs/5.0.13.RELEASE/spring-framework-reference/web.html#mvc-ann-requestmapping" target="_blank"><b>Documentação: <i>[ApiController]</i></b></a></div>

<div align="left"><a href="https://docs.microsoft.com/pt-br/aspnet/core/mvc/controllers/routing?view=aspnetcore-6.0" target="_blank"><b>Documentação: <i>[HttpGet]</i></b></a></div>

<div align="left"><img src="https://i.imgur.com/bQGvf3h.png" title="source: imgur.com" width="30px"/> <a href="https://github.com/Marcelo7211/.NetCore-Hello-World" target="_blank"><b>Código fonte do projeto</b></a>





<h2>👣 Passo 06 - Executar o Projeto</h2>

1. modifique a escolha de servidor de IIS para HelloWorld

 <div align="center"><img src="https://i.imgur.com/uTsotmg.png" /></div>

<br />

 <div align="center"><img src="https://i.imgur.com/EZk1Ubp.png" /></div>

2 - Execute o projeto clicando no botão play verde

<div align="center"><img src="https://i.imgur.com/bIooLQO.png" /></div>

3. Neste momento o Visual studio  varre todo o seu projeto procurando por **TODAS** as Classes até chegar ao controller.

 <div align="center"><img src="https://i.imgur.com/5wSWSN1.png" title="source: imgur.com" /></div>

7. Perceba que o projeto esta em execução no seguinte link http://localhost:5000 (executando de forma local na sua maquina na porta 5000):



<h2>👣 Passo 07 - Testar no Postman</h2>

Para testar a aplicação, utilizaremos um aplicativo chamado Postman. 

<div align="left"><img src="https://i.imgur.com/S6QFsr1.png" title="source: imgur.com" width="27px" /><a href="https://www.postman.com/" target="_blank"><b> Site Oficial: Postman</b></a></div>
<br />

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="100px"/> | <div align="left"> **DICA:** *Caso você tenha alguma dúvida quanto a instalação do Postman, consulte o Guia de Instalação do Postman.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

O Postman é um API Client que facilita a vida da pessoa desenvolvedora no processo de desenvolvimento do Backend de uma aplicação WEB. O Postman permite criar, compartilhar, testar e documentar aplicações WEB de forma simples e prática. Isso é feito, permitindo aos  usuários criar e salvar requisições **HTTP e HTTPS** (Request) desde as mais simples até as mais complexas, bem como ler as suas respostas (Response).

Para testar a nossa API, vamos criar uma requisição do Tipo GET, onde iremos indicar o servidor (no nosso caso, servidor local, portanto localhost), na porta padrão do Asp.NET  (porta 8080, que pode ser alterada) e o endereço do recurso (neste caso /hello-world).

1. Na janela **My Workspace**, clique no botão **+** para criar uma nova requisição.

<div align="center"><img src="https://i.imgur.com/bucLyoQ.png" title="source: imgur.com" /></div>



2. Configure a requisição conforme a figura abaixo:

 <div align="center"><img src="https://i.imgur.com/rWnYF3J.png" title="source: imgur.com" /></div>

3. No item marcado em azul na imagem acima, informe o verbo da Requisição. Como estamos fazendo uma consulta, utilize o verbo **GET**.

4. No item marcado em verde na imagem acima, informe o destino (caminho) da Requisição. A requisição **Hello World** foi configurada da seguinte maneira:

- A primeira parte do endereço (http://localhost:5000) é o endereço do nosso servidor local. Se a API estivesse na nuvem, ele seria substituído pelo endereço da aplicação na nuvem.
- A segunda parte do endereço é o **Endpoint** configurado na anotação ***[Route("api/[controller]")]***, em nosso caso  **/api/Home**. 

5. Para testar a requisição, com a aplicação rodando, clique no botão **Send** (em azul).
6. O resultado será exibido na área marcada na cor laranja.

Se a mensagem de boas vindas: **Ola mundo** for exibida, a sua primeira aplicação Asp.NET Boot está funcionando corretamente.

