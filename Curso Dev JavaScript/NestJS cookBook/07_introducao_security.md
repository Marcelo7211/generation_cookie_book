﻿<h1>Microsoft.AspNetCore.Authentication</h1>



No mundo da tecnologia, em especial da Internet, nenhuma aplicação em execução na Nuvem pode ficar sem algum tipo de Segurança habilitada, devido aos inúmeros perigos existentes no mundo virtual como ataques Hackers, invasões de Servidores, roubos de dados, entre outros. No ecossistema Asp.net, isso é feito com a ajuda da **Dependência Microsoft.AspNetCore.Authentication**.

Vamos adicionar a **Dependência Microsoft.AspNetCore.Authentication** no Projeto Blog Pessoal, 

```xml
<ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Authentication" Version="2.2.0" />
    <PackageReference Include="Microsoft.AspNetCore.Authentication.JwtBearer" Version="5.0.13" />
 </ItemGroup>
```

Instale via Nuget as dependencias:

​			**Microsoft.AspNetCore.Authentication**

<div align="center"><img src="https://i.imgur.com/uWSEu9g.png" title="source: imgur.com" width="90%"/></div>



​			**Microsoft.AspNetCore.Authentication.JwtBearer**

<div align="center"><img src="https://i.imgur.com/uWSEu9g.png" title="source: imgur.com" width="90%"/></div>




<h2>1. Segurança da Aplicação</h2>

Antes de estudarmos a Microsoft.AspNetCore.Authentication, vamos compreender 3 conceitos importantes da Segurança da Informação:

<h3>1.1. Autenticação</h3>

<div align="center"><img src="https://i.imgur.com/j6XK5if.png" title="source: imgur.com" width="90%"/></div>

É o primeiro processo da Segurança da Informação, popularmente conhecido como Login no sistema. É o momento em que o usuário informa o seu usuário de acesso (e-mail) e a sua senha (criptografada), e o sistema fará a checagem se estas informações estão corretas.

<br /><br /><br /><br /><br /><br /><br /><br />

<h3>1.2. Autorização</h3>



<div align="center"><img src="https://i.imgur.com/MoeD7tK.png" title="source: imgur.com" width="90%"/></div>

É o segundo processo da Segurança da Informação, popularmente conhecido como Direitos de acesso (Roles) no sistema. É o momento em que o sistema checará o que o usuário pode e não pode fazer no sistema, ou seja, as suas permissões dentro do sistema (Quais Recursos e Endpoints podem ser acessados?).


<h3>1.3. Filtros de Servlet</h3>

<div align="center"><img src="https://i.imgur.com/69yJ98D.png" title="source: imgur.com"  width="65%"/></div>

Qualquer aplicativo da web Asp.Net é apenas um **Servlet** (é uma Classe Java usada para criar aplicações WEB), que redireciona todas as Requisições HTTP recebidas (por exemplo, do Front-end Angular ou React), para as suas respectivas Classes Controladoras (**[ApiController]**). 

Como nestas requisições não existe uma segurança e a autenticação e a autorização devem ser efetuadas antes das Requisições HTTP, a Microsoft.AspNetCore.Authentication oferece como solução para este problema os **Filtros**, que na prática são Objetos que interceptam toda e qualquer Requisição HTTP recebida antes de chegarem ao controlador. Por isso que o seu Blog Pessoal está "trancado" após a inserção da Dependência Microsoft.AspNetCore.Authentication.

A figura acima, ilustra o filtro **Microsoft.AspNetCore.Authentication** checando o Token de Autorização do Usuário enviado no cabeçalho da requisição. Como ele está dentro do padrão Basic, o filtro libera o envio da requisição para a Classe Controladora específica.

 <br /><br />

<h2>2. Microsoft.AspNetCore.Authentication</h2>

Analisando nossos projetos podemos perceber que nossa API, até este momento, não possuía nenhuma segurança, ou seja, qualquer pessoa poderia acessar todos os nossos endpoints e ter acesso à todos os recursos livremente. Precisamos entender que algumas aplicações contém informações vitais como: dados pessoais, dados bancários, usuário e senha de acesso, e portanto precisamos garantir que a nossa API e estes dados estejam devidamente protegidos. E para isto podemos contar com a dependência do Asp.net chamada **Microsoft.AspNetCore.Authentication<** (adicionada acima).

A **Microsoft.AspNetCore.Authentication** é um framework para Java, que provê autenticação, autorização, filtros e diversas outras funcionalidades para aplicações corporativas, com o objetivo de proteger a nossa aplicação contra acessos indevidos.

O esquema de autenticação que utilizaremos em nosso projeto é o **HTTP Basic**, onde entraremos com o **e-mail (usuário) e a senha** do usuário e através de um endpoint liberado, o Microsoft.AspNetCore.Authentication irá criptografar a senha e fazer uma consulta no nosso Banco de dados para saber se o usuário já existe. Esta checagem será feita através da Camada de Serviço (service) da aplicação. Se a consulta encontrar o usuário e a senha,  a Microsoft.AspNetCore.Authentication devolverá como resposta um Authorization com o prefixo Basic + token. Este token ficará registrado na nossa aplicação na camada de Security, e apenas por meio dele que o usuário poderá consumir a API.

Para melhor compreensão deste sistema, é necessário dividi-lo em 2 ecossistemas: **Usuário** e **Segurança**, que veremos mais a frente.

<h2>3. Conhecendo HTTP authentication</h2>

O **IETF (*Internet Engineering Task Force*)** tem como missão identificar e propor soluções para as questões/problemas relacionados à utilização da Internet, além de propor a padronização das tecnologias e protocolos envolvidos. O mesmo define a estrutura de autenticação HTTP que pode ser usada por um servidor para definir uma solicitação do cliente. O servidor responde ao cliente com uma mensagem do tipo **HTTP Status 401(Não autorizado)** e fornece informações de como autorizar com um cabeçalho de resposta **WWW-Authenticate** contendo ao menos uma solicitação. Um cliente que deseja autenticar-se com um servidor pode fazer isso incluindo um campo de cabeçalho de solicitação **WWW-Authenticate** com as credenciais. No Diagrama de Sequência abaixo pode se observar este relacionamento:

<div align="center"><img src="https://i.imgur.com/PAQBkKK.jpg" title="source: imgur.com" /></div>

No caso de uma **autorização “Basic”** (como a mostra a figura acima), a troca deve acontecer por meio de uma conexão HTTP (TLS) para ser segura. Se um servidor recebe credenciais válidas, mas que não são adequadas para ter acesso a um determinado recurso, o servidor responderá com o código de status **HTTP Status 403 (Proibido!)** . Ao contrário de **HTTP Status 401(Não autorizado)**, a autenticação é impossível para este usuário. O cabeçalho de requisição **Authorization** contém as credenciais para autenticar um agente de usuário com um servidor. Aqui o tipo é novamente necessário, seguido pelas credenciais, que podem ser codificadas ou criptografadas dependendo do esquema de autenticação usado. No caso acima foi utilizado o esquema de autenticação Basic que será explicado na sequencia.

<div align="left"><img src="https://i.imgur.com/cDPH4tl.png" title="source: imgur.com" width="30px"/> <a href="https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status/401" target="_blank"><b>Documentação: HTTP Status Code 401 - Unauthorized</b></a></div>

<div align="left"><img src="https://i.imgur.com/cDPH4tl.png" title="source: imgur.com" width="30px"/> <a href="https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status/403" target="_blank"><b>Documentação: HTTP Status Code 403 - Forbidden</b></a></div>

<div align="left"><img src="https://i.imgur.com/cDPH4tl.png" title="source: imgur.com" width="30px"/> <a href="https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Headers/WWW-Authenticate" target="_blank"><b>Documentação: Cabeçalho HTTP WWW-Authenticate</b></a></div>

<div align="left"><img src="https://i.imgur.com/cDPH4tl.png" title="source: imgur.com" width="30px"/> <a href="https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Headers/Authorization" target="_blank"><b>Documentação: Cabeçalho de Requisição HTTP Authorization</b></a></div>

<br />

<h3>3.1. Esquema de autenticação Basic</h3>

A estrutura geral de autenticação HTTP é usado por vários esquemas de autenticação. Os esquemas podem divergir na força da segurança e na disponibilidade do software cliente ou servidor. O esquema mais comum de autenticação é o “Basic”, mas existem outros esquemas oferecidos por serviços de hospedagem, como Amazon AWS, Google ou Microsoft. Os esquemas de autenticação mais comuns são:

|<img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="350px"/>  | <div align="left">**ATENÇÃO:** Para melhor compreensão no momento, vamos focar apenas no entendimento do formato Basic, que é considerado o principal esquema para compreender os demais meios de autorização. Vale mencionar que para aprender os demais é necessário tempo e muita dedicação.</div> |
| ----------------------------------------------------- | ------------------------------------------------------------ |

O esquema **Basic**, segundo sua documentação, consiste em um conjunto de caracteres que posicionados após a palavra **"Basic "** no formato **“email:senha”** codificados utilizando o modelo **Base64**, formando um token ***Authorization*** para ser passado ao sistema. Abaixo veremos um exemplo de código para gerar a estrutura em Java:



