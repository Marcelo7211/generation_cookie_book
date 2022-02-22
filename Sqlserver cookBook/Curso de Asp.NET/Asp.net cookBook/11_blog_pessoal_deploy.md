<h1>Deploy do Back-end no Heroku</h1>

<h2>O que é Deploy?</h2>

O verbo **deploy**, em inglês, significa **implantar**.

Em programação, seu sentido está intimamente relacionado à sua tradução literal: fazer um deploy, em termos práticos, significa colocar no ar alguma aplicação que teve seu desenvolvimento concluído.
Quando um site é finalizado por um desenvolvedor e, após seus testes, é finalmente hospedado na nuvem e colocado no ar, ele passa pelo processo de deploy.
De mesmo modo, quando um sistema sofre alguma melhoria ou alteração em seu código-fonte, implementar essa alteração ao sistema que está no ar também é um tipo de deploy.

<h2>O que veremos por aqui?</h2>

Esse documento é um passo a passo para você enviar a sua aplicação SPRING, gratuitamente para a nuvem (Deploy). Este processo irá gerar um link de acesso a sua aplicação, que poderá ser acessado de qualquer lugar, a partir de qualquer dispositivo com acesso a Internet. 
Para efetuar o Deploy vamos precisar fazer algumas modificações em nosso projeto, que serão detalhadas nas próximas páginas.

<h2>👣 Passo 01 - Criar a Documentação da API</h2>

Para criar a Documentação da API no Swagger, utilize o **Guia de Configuração do SPringDoc**.

<br /><br /><br /><br />

<h2 id="local">👣Passo 02 - Testar a API no seu computador</h2>

1. Execute a sua aplicação localmente pelo STS

2. Abra o endereço: **http://localhost:8080/** no seu navegador

3. A sua aplicação deverá exibir a tela de **Login (Usuário e Senha)**. Utilize o teste o **usuário: *root*** e a **Senha: *root***, que foram criados em memória na **Classe BasicSecurityConfig**.

<div align="center"><img src="https://i.imgur.com/mBRxYd8.png" title="source: imgur.com" width="50%"/></div>

4. Caso a aplicação **não** solicite o **Usuário** e a **Senha**, feche todas as janelas abertas do seu Navegador da Internet,  abra novamente o Navegador e acesse novamente o endereço: **http://localhost:8080/**.
5. Verifique se após o login o **Swagger** está inicializando automaticamente sem a necessidade de digitar o endereço do Swagger.
6. Teste todos os Endpoints, de todos os Recursos da aplicação no **Postman** (postagens, temas e usuarios) e verifique se todos estão funcionando. 
7. Em especial, verifique se o Método logar está devolvendo o Token.
8. Antes de continuar o Deploy, não esqueça de **parar a execução do Projeto no STS**.

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="128px"/> | <p align="justify"> **IMPORTANTE:**  *Não altere a senha do usuário root. Os instrutores da sua turma utilizarão este usuário para abrir, testar e corrigir a sua aplicação*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |



| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="200px"/> | <p align="justify"> **ATENÇÃO:**  *Lembre-se que antes de fazer o Deploy é fundamental que a API esteja rodando e sem erros*. Não faça os testes via Swagger porquê o usuário root (em memória, não utiliza os recursos da Spring Security.</p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |





<h2>👣 Passo 03 - Criar uma conta grátis no Heroku</h2>



1) Acesse o endereço: **https://www.heroku.com**

<div align="center"><img  src="https://i.imgur.com/9lFOzru.png" title="source: imgur.com" width="90%"/></div>

2. Crie a sua conta grátis no Heroku clicando no botão **SIGN UP FOR FREE**.
3. Preencha os dados do formulário e clique no botão **CREATE FREE ACCOUNT**.

   <div align="center"><img src="https://i.imgur.com/yp46vWx.png" title="source: imgur.com" width="80%"/></div>

4. Será exibida a mensagem abaixo informando que você receberá uma mensagem no seu e-mail para ativar a sua conta no Heroku. Acesse o seu e-mail e ative a sua conta.

   <div align="center"><img src="https://i.imgur.com/d1YV3RK.png" title="source: imgur.com" width="80%"/></div>

5. O e-mail que você receberá será semelhante a imagem abaixo. Clique no link indicado em vermelho para ativar a sua nova conta

   <div align="center"><img src="https://i.imgur.com/cgeQPVF.png" title="source: imgur.com" width="85%"/></div>

6. Será aberta a janela abaixo para criar a senha da sua conta. Crie uma senha e clique no botão **SET PASSWORD AND LOGIN**.

   <div align="center"><img src="https://i.imgur.com/j3hWcWD.png" title="source: imgur.com" width="80%"/></div>

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="70px"/> | <p align="justify"> **ATENÇÃO:**  *A senha deve ter no mínimo 8 caracteres e pelo menos 1 letra maiúscula, 1 caracter especial e 1 numero*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

7. Será exibida a tela de Boas Vindas. Clique no botão **CLICK HERE TO PROCEED**.

   <div align="center"><img src="https://i.imgur.com/0RtgWeI.png?1" title="source: imgur.com" /></div>

8. Na próxima tela, concorde com os termos de uso da plataforma clicando no botão **Accept**.

   <div align="center"><img src="https://i.imgur.com/0pRIHhl.png" title="source: imgur.com" /></div>

9. Você será redirecionado para o **Dashboard do Heroku**. Agora você está pronto para criar as suas aplicações na Nuvem do Heroku.

   <div align="center"><img src="https://i.imgur.com/MtxGolw.png" title="source: imgur.com" /></div>

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="70px"/> | <p align="justify"> **ATENÇÃO:**  *Conclua todas etapas do processo de criação da conta no Heroku antes de avançar para o próximo passo do Deploy*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br /><br /><br />

10. Caso o Heroku exiba a mensagem abaixo, solicitando a ativação do **MFA (Multi-Factor Authentication)**, não habilite esta opção. Clique no link **Later**, como mostra a figura abaixo, no item marcado em vermelho.

    <div align="center">
    <img src="https://i.imgur.com/OejMn66.png" title="source: imgur.com" /></div>



| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="200px"/> | <p align="justify"> **ATENÇÃO:**  *Não habilite em sua conta no Heroku a opção MFA (Multi-Factor Authentication), ou seja, o login em 2 etapas. Em alguns servidores não é possível efetuar login via Heroku Client com o MFA habilitado*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br /><br />

<h2>👣 Passo 04 - Instalação do Node.js</h2>



1) Acesse o endereço: **https://nodejs.org/en/**

<div align="center"><img src="https://i.imgur.com/t6mCAGb.png" title="source: imgur.com" /></div>

2. Faça o download da última versão LTS disponível do Node.js e instale no seu computador. 

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="120px"/> | <p align="justify"> **ATENÇÃO:** No momento em que este e-book foi escrito, a versão LTS mais atual do Node.js era a versão 16.13.0. Hoje pode ser que a versão mais atual seja outra* </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |



| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="72px"/> | <p align="justify"> **DICA:** *Caso você tenha alguma dúvida quanto a instalação do Node.js, consulte o Guia de Instalação do Node. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br /><br /><br /><br /><br /><br /><br />

<h2>👣 Passo 05 - Instalação do Heroku Client</h2>



Para instalar e executar os comandos do Heroku Client usaremos o **Prompt de comando do Windows (cmd)**. 

1) Para instalar, execute o atalho <img width="50" src="https://i.imgur.com/JpqKaVh.png" title="source: imgur.com" /> para abrir a janela **Executar**.

<div align="center"><img src="https://i.imgur.com/uDHCB0H.png" title="source: imgur.com" width=55%"/></div>

2) Digite o comando **cmd** para abrir o **Prompt de comando do Windows**

3) Antes de instalar o **Heroku Client**, verifique se o Node já está instalado através do comando: 

```bash
npm -version
```

<div align="justify"><img src="https://i.imgur.com/sfHThTC.png" title="source: imgur.com" /></div>
** A versão pode ser diferente da imagem*

4) Caso não esteja instalado, volte ao passo **Instalação do Node.js**. 
5) Para instalar o **Heroku Client** digite o comando: 

```bash
npm i -g heroku
```

<div align="center"><img  src="https://i.imgur.com/rcsDAZ0.png" title="source: imgur.com" /></div>

6) Confirme a instalação do Heroku Client através do comando: 

```bash
heroku version
```

<div align="center"><img src="https://i.imgur.com/MO23QyV.png" title="source: imgur.com" /></div>

**A versão pode ser diferente da imagem*

<br />

<h2>👣 Passo 06 - Criar o arquivo system.properties</h2>

O arquivo **system.properties**, tem o objetivo de informar ao Heroku qual a versão a do Java ele deve utilizar para gerar o seu projeto e criar o arquivo executável (.jar).

1. Na **raiz do seu projeto**, na pasta **blogpessoal** (como mostra a figura abaixo), crie o arquivo **system.properties**.

<div align="center"><img width="230px" src="https://i.imgur.com/MSsuQzt.png" title="source: imgur.com" /></div>



| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="250px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes ao criar o arquivo system.properties. Um erro muito comum é não criar o arquivo na pasta raíz do projeto. Outro erro comum é digitar o nome do arquivo errado.* </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br /><br />

2. Na Guia **Package explorer**, clique com o botão direito do mouse sobre a pasta do projeto e clique na opção **New 🡢 File**.

3. Em **File name**, digite: **system.properties** e clique no botão **Finish**.

<div align="center"><img width="65%" src="https://i.imgur.com/BRDFhtJ.png" title="source: imgur.com" /></div>


4) No arquivo **system.properties** indique a versão do Java que será utilizada pelo Heroku através da linha abaixo:

```properties
java.runtime.version=11
```


| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="108px"/> | <p align="justify"> **ATENÇÃO:** *A versão do Java informada no arquivo system.properties deve ser a mesma informada no arquivo pom.xml.* </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="250px"/> | **DICA:** *Durante o Deploy, caso o Heroku não reconheça a versão correta do Java (Exemplo: informei a versão 16 e o Heroku reconheceu a versão 1.8), apague o arquivo system.properties, recrie o arquivo na raíz do projeto e tente fazer o Deploy novamente.* |
| ------------------------------------------------------------ | :----------------------------------------------------------- |

<br /><br />

<h2>👣 Passo 07 - Adicionar a Dependência do PostgreSQL no pom.xml</h2>


O Heroku, na sua versão gratuita, utiliza o **PostgreSQL** como **SGBD**. No Bloco 02 estamos utilizando o **MySQL** para desenvolver o Blog Pessoal. Ambos são Banco de dados Relacionais e graças ao **Spring Data JPA**, não será necessário realizar nenhuma alteração no código do nosso aplicativo. A única mudança necessária, além de adicionar a **Dependência no pom.xml**,  é configurar a aplicação para utilizar o PostgreSQL. 

<div align="left"><img src="https://i.imgur.com/b3khcJI.png" title="source: imgur.com" width="25px"/> <a href="https://www.postgresql.org/" target="_blank"><b>Site Oficial: PostgreSQL</b></a></div>

No arquivo, **pom.xml**, vamos adicionar as linhas abaixo, com a dependência do **PostgreSQL**:

```xml
<dependency>
	<groupId>org.postgresql</groupId>
	<artifactId>postgresql</artifactId>
</dependency> 

```


<h2>👣 Passo 08 - Configurar o Banco de Dados na Nuvem</h2>


A Configuração do Banco de dados Local é diferente da configuração que será utilizada no Heroku. 

No passo anterior, adicionamos a Dependência do PostgreSQL no arquivo pom.xml, neste passo vamos configurar a aplicação para acessar o Banco de dados remoto no Heroku.

Para simplificar o processo, vamos utilizar um recurso do Spring chamado **Profiles** (perfis), que nada mais é do que criar um modelo de configuração para cada situação, ou seja, uma configuração para usar localmente (**application-dev.properties**)  e outra para usar na nuvem (**application-prod.properties**). 

O grande benefício dos Profiles é simplificar a troca entre a configuração Local para o Desenvolvimento da aplicação (**MySQL**) e a configuração Remota para o Deploy (**PostgreSQL**). 

1) Na Source Folder **src/main/resources**, crie os arquivos **application-dev.properties** (Configuração do Banco de dados local) e **application-prod.properties** (Configuração do Banco de dados na nuvem).

<div align="center"><img src="https://i.imgur.com/Gj3UbgY.png" title="source: imgur.com" width="230px"/></div>


2. Vamos criar o primeiro arquivo. No lado esquerdo superior, na Guia **Package explorer**, na Source Folder **src/main/resources**, clique com o botão direito do mouse e clique na opção **New 🡢 File**.


3) Em **File name**, digite o nome do primeiro arquivo (**application-dev.properties**) e clique no botão **Finish**.

<div align="center"><img src="https://i.imgur.com/UPomYW2.png" title="source: imgur.com" width="65%"/></div>

4. Vamos criar o segundo arquivo. No lado esquerdo superior, na Guia **Package explorer**, na Source Folder **src/main/resources**, clique com o botão direito do mouse e clique na opção **New 🡢 File**.

5. Em **File name**, digite o nome do primeiro arquivo (**application-prod.properties**) e clique no botão **Finish**.

   <div align="center"><img src="https://i.imgur.com/Mcm8hwz.png" title="source: imgur.com" width="70%"/></div>

Agora vamos configurar os 3 arquivos:

1. Abra o arquivo **application.properties**, **apague todo o conteúdo da configuração do Banco de dados**, insira a linha: **spring.profiles.active=prod** e salve o arquivo. O arquivo application.properties ficará com o seguinte conteúdo abaixo:

```properties
spring.profiles.active=prod


springdoc.api-docs.path=/v3/api-docs
springdoc.swagger-ui.path=/swagger-ui.html
springdoc.swagger-ui.operationsSorter=method
springdoc.swagger-ui.disable-swagger-default-url=true
springdoc.swagger-ui.use-root-path=true
springdoc.packagesToScan=com.generation.blogpessoal.controller
```

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="250px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes ao configurar o arquivo application.properties. Cuidado para não apagar a configuração do Swagger (SpringDoc).* </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

2. Abra o arquivo **application-dev.properties**, insira as linhas abaixo e salve o arquivo. **Não esqueça de alterar a senha do usuário root caso a sua senha não seja root**.

<div align="center"><img src="https://i.imgur.com/a69IptD.png" title="source: imgur.com" /></div>


3. No arquivo, **application-prod.properties**,  insira as linhas abaixo e salve o arquivo:

```properties
spring.jpa.generate-ddl=true
spring.datasource.url=${JDBC_DATASOURCE_URL}
spring.jpa.show-sql=true

spring.jackson.date-format=yyyy-MM-dd HH:mm:ss
spring.jackson.time-zone=Brazil/East
```

4. Para alternar entre as configurações Local e Remota, abra o arquivo **application.properties** e utilize uma das 2 opções abaixo:

<b><code>spring.profiles.active=dev</code> </b> 🡢 O Spring executará a aplicação com a configuração do Banco de dados local (MySQL)

<b><code>spring.profiles.active=prod</code> </b> 🡢 O Spring executará a aplicação com a configuração do Banco de dados na nuvem (Heroku)

Para o Deploy, devemos deixar a linha **spring.profiles.active** configurada com a opção **prod**.



| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="400px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes ao criar os perfis do Banco de Dados. Um erro muito comum é tentar executar o seu projeto no STS (http://localhost:8080/) com o Perfil prod habilitado no arquivo application.properties. Para executar localmente, abra o arquivo application.properties e altere a 1º linha para dev.* </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |



<div align="left"><img src="https://i.imgur.com/bQGvf3h.png" title="source: imgur.com" width="25px"/> <a href="https://github.com/conteudoGeneration/blog-pessoal/tree/Heroku" target="_blank"><b>Código fonte: Projeto Finalizado</b></a> 
</div>



<h2>👣 Passo 09 - Deploy com o Git</h2>

Vamos preparar o nosso repositório local para subir a aplicação para o Heroku utilizando o Git.

1. Na pasta do projeto, clique com o botão direito do mouse e na sequência clique na opção: **Show in 🡢 System Explorer**

2. Será aberta a pasta Workspace onde o Eclipse/STS grava os seus projetos: 
3. Copie a pasta da API: **_blogpessoal_** (o nome da sua pasta pode ser diferente)    

<div align="left"><img src="https://i.imgur.com/9nYx79c.png?1" title="source: imgur.com" /></div>

4. Cole a pasta no mesmo diretório

<div align="left"><img src="https://i.imgur.com/c7bkyZB.png" title="source: imgur.com" /></div>

<br /><br /><br />

5. Renomeie a pasta para **deploy_blogpessoal**

<div align="left"><img width="700px" src="https://i.imgur.com/Ppu5mnF.png" title="source: imgur.com" /></div>

6. Abra a pasta **deploy_blogpessoal** e verifique se existe uma pasta chamada **.git**. Caso ela exista, apague esta pasta. **Esta pasta estará presente <u>APENAS</u> se você inicializou o git dentro da pasta do projeto.**

<div align="left"><img src="https://i.imgur.com/2vzoKD4.png" title="source: imgur.com" /></div>

7. Caso esta pasta não esteja sendo exibida, na janela do Windows Explorer, clique na **Guia Exibir** e na sequência no botão **Opções**. Na janela **Opções de Pasta**, na **Guia Modo de Exibição**, no item **Configurações avançadas**, localize a opção: **Pastas e arquivos ocultos** e marque a opção **Mostrar arquivos, pastas e unidades ocultas** (como mostra a figura abaixo). Em seguida clique em **OK** para concluir.

<div align="center"><img width="340px" src="https://i.imgur.com/n8hQu12.png" title="source: imgur.com" /></div>

8. Execute o atalho <img width="80" src="https://i.imgur.com/JpqKaVh.png" title="source: imgur.com" /> para abrir a janela Executar

<div align="center"><img src="https://i.imgur.com/ISBwaaK.png" title="source: imgur.com" /></div>

9. Digite o comando abaixo para abrir o **Prompt de Comando do Windows**:

```
cmd
```
10. Na pasta **deploy_blogpessoal**, no **Windows Explorer**, copie o caminho da pasta conforme a figura abaixo:

<div align="center"><img src="https://i.imgur.com/yI6at9T.png" title="source: imgur.com" /></div>

11. No Prompt de comando do Windows digite o comando cd e cole na frente do comando o caminho copiado: 

```
cd C:\Users\seu usuario\Documents\
workspace-spring-tool-suite-4-4.11.0.RELEASE\deploy_blogpessoal
```
**o nome da pasta pode ser diferente*

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao iniciar o Deploy pelo Git. A partir deste ponto, todos os comandos do Git e do Heroku Client devem ser executados via Prompt de Comando do Windows (CMD), dentro da pasta deploy-blogpessoal.* |
| ------------------------------------------------------------ | :----------------------------------------------------------- |

12. Digite a sequência de comandos abaixo para inicializar o seu repositório local para efetuar o Deploy no Heroku:

```
git init
git add .
git commit -m “Deploy inicial - Blog Pessoal”
```
<br />

<div align="left"><img src="https://i.imgur.com/bQGvf3h.png" title="source: imgur.com" width="25px"/> <a href="https://github.com/rafaelq80/deploy_blogpessoal" target="_blank"><b>Código fonte: Projeto finalizado</b></a>


<h2>👣 Passo 10 - Login no Heroku</h2>

1. Digite o comando: 

```
heroku login
```
<div><img src="https://i.imgur.com/pvygxsZ.png" title="source: imgur.com" /></div>

<br /><br /><br /><br /><br /><br />

2. Será aberta a janela abaixo. Clique no botão **Log in**

<div align="center"><img src="https://i.imgur.com/PXR6hFW.png" title="source: imgur.com" /></div>

3. Após efetuar o login na sua conta, será exibida a janela abaixo. 

<div align="center"><img src="https://i.imgur.com/i6VMoMp.png" title="source: imgur.com" /></div>

4. Volte para o Prompt de comando para continuar o Deploy.

<div align="center"><img src="https://i.imgur.com/IjyMzrH.png" title="source: imgur.com" /></div>

<br /><br />

<h2>👣 Passo 11 - Criar um novo projeto no Heroku</h2>



Para criar um novo projeto na sua conta do Heroku, digite o comando abaixo, onde o **nomedoprojeto** deve ser substituído por um nome (escolhido por você), que esteja disponível no Heroku.

```
heroku create nomedoprojeto
```

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="200px"/> | <p align="justify"> **ATENÇÃO:** *O NOME DO PROJETO NÃO PODE CONTER LETRAS MAIUSCULAS, NUMEROS OU CARACTERES ESPECIAIS. ALÉM DISSO ELE PRECISA SER ÚNICO DENTRO DA PLATAFORMA HEROKU. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

Se o nome escolhido já existir, será exibida a mensagem abaixo:

<div><img src="https://i.imgur.com/L7ayFaz.png" title="source: imgur.com" /></div>

Se o nome escolhido for aceito, será exibida a mensagem abaixo:

<div><img src="https://i.imgur.com/P0KazWd.png" title="source: imgur.com" /></div>



<h2>👣 Passo 12 - Adicionar o Banco de dados no Heroku</h2>



Para adicionar um Banco de Dados PostgreSQL no seu projeto, digite o comando:

```bash
heroku addons:create heroku-postgresql:hobby-dev -a nomedoprojeto
```

<div><img src="https://i.imgur.com/edhMr8x.png" title="source: imgur.com" /></div>

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="100px"/> | <p align="justify"> **ATENÇÃO:** *O processo do Deploy enviará apenas a sua aplicação para a nuvem, logo o Banco de dados que será criado nesta etapa estará vazio. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |



<h2>👣Passo 13 - Efetuar o Deploy</h2>



1. Para concluir o Deploy, digite o comando: 

```
git push heroku master
```

2. Ao finalizar o Deploy, será exibida a mensagem **BUILD SUCESS** (destacado em verde na imagem) e será exibido o endereço (**https://nomedoprojeto.herokuapp.com**) para acessar a API na Internet (destacado em amarelo na imagem)

<div align="center"><img src="https://i.imgur.com/gEUe301.png?1" title="source: imgur.com" /></div>


<h2>👣 Passo 14 - Configurar o fuso horário</h2>

1. Após concluir o Deploy (Passo 13 não apresentou nenhum problema), antes de testar a aplicação, digite o comando abaixo para configurar o fuso horário do servidor: 

```
heroku config:add TZ="America/Sao_Paulo" --app nomedoprojeto
```

Este comando configura o fuso horário do Servidor do Heroku, para garantir que a hora que será gravada  no Banco de dados PostgreSQL esteja no fuso horário de São Paulo (horário de Brasília).

<br /><br /><br />

<h2>👣 Passo 15 - Testar o link e a aplicação</h2>



1) Abra o navegador e digite o endereço a sua aplicação (**https://nomedoprojeto.herokuapp.com**).

2) Será solicitado o **Usuário e a Senha**. Digite **root** para ambos.

3) Sua aplicação abrirá o **Swagger**. 

4) Utilize o **Checklist do Blog Pessoal** para verificar se o projeto está completo e testar a aplicação.



<h2 id="update">Atualizar o Deploy no Heroku </h2>

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes e a persistência. Este item você utilizará apenas se você alterou alguma coisa no seu projeto Spring e necessite atualizar  a aplicação na nuvem*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

1. Para fazer alterações no código do projeto e executar localmente, volte para o STS e altere o arquivo, **application.properties** conforme o código abaixo:

```properties
spring.profiles.active=dev
```

2. Faça as alterações necessárias no seu projeto, execute localmente e verifique se está tudo funcionando.
3. Antes de refazer o Deploy, altere o arquivo, **application.properties** conforme o código abaixo:

```properties
spring.profiles.active=prod
```

4.  Na pasta do projeto, clique com o botão direito do mouse e na sequência clique na opção: **Show in 🡢 System Explorer**

5. Será aberta a pasta Workspace onde o STS grava os seus projetos. Abra a pasta do projeto (**blogpessoal**).
6. Selecione todo o conteúdo da pasta do projeto (**blogpessoal**)e faça uma cópia do conteúdo (**CTRL + C**).
7. Abra a pasta do Deploy (**deploy_blogpessoal**) e cole o conteúdo (**CTRL + V**) dentro da pasta para atualizar a pasta do Deploy.
8. Execute o atalho <img width="50" src="https://i.imgur.com/JpqKaVh.png" title="source: imgur.com" /> para abrir a janela Executar.

<div align="center"><img src="https://i.imgur.com/uDHCB0H.png" title="source: imgur.com" width=60%"/></div>

9. Digite o comando abaixo para abrir o **Prompt de Comando do Windows**:

```
cmd
```

10. Na pasta do Deploy do seu projeto, no Windows explorer, copie o caminho da pasta **deploy_blogpessoal** conforme a figura abaixo:

<div align="center"><img src="https://i.imgur.com/yI6at9T.png" title="source: imgur.com" /></div>

11. No Prompt de comando do Windows digite o comando cd e cole na frente do comando o caminho copiado: 

```
cd C:\Users\seu usuario\Documents\
workspace-spring-tool-suite-4-4.11.0.RELEASE\deploy_blogpessoal
```

**o nome da pasta pode ser diferente*

12. Atualize o Deploy utilizando a sequência de comandos abaixo: 

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao atualizar o Deploy pelo Git. A partir deste ponto, todos os comandos do Git e do Heroku Client devem ser executados via Prompt de Comando do Windows (CMD), dentro da pasta deploy-blogpessoal.* |
| ------------------------------------------------------------ | :----------------------------------------------------------- |

```
git add .
git commit -m “Atualização do Deploy - Blog Pessoal”
git push heroku master
```

13.  Ao finalizar a atualização do Deploy, será exibida a mensagem **BUILD SUCESS** e será exibido o endereço (**https://nomedoprojeto.herokuapp.com**) para acessar a API na Internet.

14. Caso ocorra algum erro de vinculação (link), verifique se a pasta está vinculada ao Heroku utilizando o comando abaixo:

```
git remote
```

15. Caso não apareça o resultado **heroku**, utilize o comando abaixo para vincular a pasta com o projeto no heroku.

```
heroku git:remote -a project
```
16. Caso o comando acima falhe, inicialize o repositório git e refaça a vinculação.

```
git init
heroku git:remote -a project
```
17. Para atualizar o Deploy, utilize os comandos baixo:

```
git add .
git commit -m “Atualização do Deploy - Blog Pessoal”
git push heroku master
```
18. Caso o ultimo comando falhe, acrescente a opção -f para forçar o Deploy.

```
git push -f heroku master
```
19. Se todas as opções acima falharem, verifique se o erro não está na aplicação.
