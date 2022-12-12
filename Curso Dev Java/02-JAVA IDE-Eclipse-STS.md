<h1><center>JAVA IDE- Eclipse</center></h1>



## Eclipse IDE Para Desenvolvedores Java

O Eclipse IDE (ambiente de desenvolvimento integrado) fornece forte suporte para desenvolvedor Java. Em 2022, o Eclipse IDE tem aproximadamente um milhão de downloads por mês, o que o torna um dos principais IDEs para desenvolvimento Java.

O Eclipse pode ser estendido com componentes de software adicionais chamados plug-ins. As distribuições pré-empacotadas do Eclipse fornecem um conjunto consistente de funcionalidades.

[Os downloads do Eclipse IDE](https://eclipse.org/downloads/packages/) fornecem distribuições do Eclipse para diferentes casos de uso.

A distribuição *Eclipse IDE for Java Developers foi projetada para oferecer suporte ao desenvolvimento Java padrão.* Inclui suporte para o sistema de compilação Maven e Gradle e suporte para o sistema de controle de versão Git.

Outras ferramentas IDE também estão reutilizando componentes, como o poderoso editor de código Visual Studio Code (Code) da Microsoft, que usa o compilador Eclipse Java para seu suporte a Java. Além disso, o Eclipse IDE reutiliza ferramentas projetadas para código com base no protocolo de servidor de linguagem definido pela Microsoft.



## Recursos do Eclipse IDE

- Quase tudo no Eclipse é um plugin.
- Podemos estender a funcionalidade do Eclipse IDE adicionando plugins ao IDE, talvez para linguagem de programação adicional ou sistema de controle de versão ou UML.
- Suporta várias ferramentas de conhecimento de origem, como navegação de dobra e hiperlink, classificação, navegador de definição de macro, edição de código com realce de sintaxe.
- Fornece excelente ferramenta de depuração de código visual para depurar o código.
- O Eclipse tem uma interface de usuário maravilhosa com recurso de arrastar e soltar para design de interface do usuário.
- Suporta desenvolvimento de projeto e estrutura administrada para diferentes cadeias de ferramentas, estrutura de criação clássica e navegação de origem.
- Java Eclipse IDE tem um recurso JavaDoc com o qual podemos criar automaticamente documentação para classes em nosso aplicativo.

## Introdução à linguagem de programação Java

Uma breve introdução ao Java: Java é uma linguagem de programação de computador moderna rica em recursos. É uma linguagem de uso geral que oferece todos os recursos necessários para implementar um novo sistema. Java é apelidado de “gravar uma vez, executar em qualquer lugar”, pois não depende da arquitetura do computador, graças à Java Virtual Machine (JVM). Java Bytecode é compilado e executado na máquina JVM para fins de portabilidade. James Gosling o desenvolveu na Sun Microsystem em 1995. A partir daí, ele se fortaleceu a cada dia que passava. Principalmente, é usado para desenvolver aplicativos de nível empresarial e aplicativos da Web cliente-servidor. Também é extremamente popular entre os desenvolvedores com mais de 9 milhões de desenvolvedores usando as linguagens de programação. O Java também é famoso por ensinar codificação para iniciantes, pois é frequentemente escolhido como a linguagem de escolha para alunos iniciantes.

## Histórico de Java

A história do Java é rica e vibrante. Tudo começou com Patrick Naughton, James Gosling e Mike Sheridan quando eles começaram a trabalhar em um projeto em junho de 1991. A linguagem foi projetada para a televisão interativa. Inicialmente, a língua foi nomeada Oak por causa do carvalho do lado de fora deste escritório. Com uma mudança de nome de “Green”, foi finalmente nomeado para Java. O nome final é derivado do café Java.

A linguagem de programação Java é inspirada no estilo [C/C++](https://www.liveedu.tv/learn/c-cplusplus/) de acordo com Gosling. O objetivo era criar uma linguagem de programação independente da arquitetura de máquina subjacente.

A primeira versão pública do Java aconteceu em 1995 como Java 1.0. Novas versões foram lançadas com o tempo. Java também se tornou o código aberto em 13 de novembro de 2006. Foi lançado sob os termos GNU General Public License (GPL). Java é uma linguagem de programação poderosa e é usada em quase todos os lugares, desde pequenos microchips até supercomputadores poderosos.

## Histórico de versões do Java

| VERSÃO          | **DATA DE** **LANÇAMENTO**       |
| :-------------- | :------------------------------- |
| JDK Alfa e Beta | 1995                             |
| JDK 1.0         | Janeiro de 1996                  |
| JDK 1.1         | Fevereiro de 1997                |
| J2SE 1.2        | Dezembro de 1998                 |
| J2SE 1.3        | Maio de 2000                     |
| J2SE 1.4        | Fevereiro de 2002                |
| Java SE 5       | Setembro de 2004                 |
| Java SE 6       | Dezembro de 2006                 |
| Java SE 7       | julho de 2011                    |
| Java SE 8       | Março 2014                       |
| Java SE 9       | setembro de 2017                 |
| Java SE 10      | março de 2018                    |
| Java SE 11      | setembro de 2018                 |
| Java SE 12      | março de 2019                    |
| Java SE 13      | setembro de 2019                 |
| Java SE 14      | março de 2020                    |
| Java SE 15      | setembro de 2020                 |
| Java SE 16      | março de 2021                    |
| Java SE 17      | setembro de 2021                 |
| Java SE 18      | março de 2022                    |
| Java SE 19      | será lançado em setembro de 2022 |
| Java SE 20      | será lançado em março de 2023    |
| Java SE 21      | será lançado em setembro de 2023 |

## Terminologia Java

Antes de começarmos a aprender Java, vamos nos familiarizar com os termos comuns de Java.

**Java Virtual Machine (JVM)**
Geralmente é referido como JVM. Antes, discutimos sobre a JVM, vamos ver as fases de execução do programa. As fases são as seguintes: escrevemos o programa, depois compilamos o programa e por fim executamos o programa.

1) A escrita do programa é obviamente feita por programadores java como você e eu.
2) A compilação do programa é feita pelo compilador javac, javac é o compilador java primário incluído no kit de desenvolvimento java (JDK). Ele recebe o programa java como entrada e gera o bytecode java como saída.
3) Na terceira fase, a JVM executa o bytecode gerado pelo compilador. Isso é chamado de fase de execução do programa.

Então, agora que entendemos que a função primária da JVM é executar o bytecode produzido pelo compilador. **Cada sistema operacional possui uma JVM diferente, porém a saída que eles produzem após a execução do bytecode é a mesma em todos os sistemas operacionais** . É por isso que chamamos java de linguagem independente de plataforma.

**bytecode**
Conforme discutido acima, o compilador javac do JDK compila o código-fonte java em bytecode para que possa ser executado pela JVM. O bytecode é salvo em um arquivo .class pelo compilador.

<a href="https://imgur.com/wNzt45f"><img src="https://i.imgur.com/wNzt45f.jpg" title="source: imgur.com" style="zoom: 67%;" align=center></a>

**Java Development Kit (JDK)**
Ao explicar JVM e bytecode, usei o termo JDK. Vamos discutir sobre isso. Como o nome sugere, este é um kit completo de desenvolvimento java que inclui JRE (Java Runtime Environment), compiladores e várias ferramentas como JavaDoc, depurador Java etc.
Para criar, compilar e executar o programa Java, você precisa do JDK instalado em seu computador.

**Java Runtime Environment (JRE)**
JRE faz parte do JDK, o que significa que o JDK inclui o JRE. Quando você tiver o JRE instalado em seu sistema, poderá executar um programa java, mas não poderá compilá-lo. JRE inclui JVM, plugins de navegador e suporte a applets. Quando você só precisa executar um programa java em seu computador, você precisa apenas do JRE.



## Ferramentas Java

As ferramentas são universais para qualquer linguagem de programação que você usa. Java não é diferente. Tem algumas ferramentas que você deve usar para tirar o máximo proveito da linguagem de programação Java. Usar a ferramenta certa ajudará você a melhorar sua produtividade e fluxo de trabalho. Então, quais ferramentas você deve escolher? Vamos passar por algumas das melhores ferramentas Java!

- [Gradle:](http://gradle.org/) Uma ferramenta de construção simples para projetos Java. Ele permite que você publique, teste, crie, implemente e gerencie seu projeto. É uma ferramenta obrigatória para programadores Java.

- [Eclipse:](http://www.eclipse.org/) Eclipse é um IDE de código aberto popular para Java e é usado por centenas e milhares de programadores Java.

- [Spring Tools 4: ](https://spring.io/tools) é a próxima geração de ferramentas Spring para seu ambiente de codificação favorito. Em grande parte reconstruído do zero, ele fornece suporte de classe mundial para o desenvolvimento de aplicativos corporativos baseados em Spring, se você preferir Eclipse, Visual Studio Code ou Theia IDE.

- [IntelliJ:](http://www.jetbrains.com/idea/) IntelliJ é mais um IDE para linguagem de programação Java. Ele é construído pela JetBrains e está disponível na edição da comunidade. Você também pode optar por obter a edição comercial que vem com melhores recursos e suporte.

- [YourKit:](https://www.yourkit.com/) Yourkit é um criador de perfil Java simples. Ele funciona combinando a análise poderosa e a criação de perfis sob demanda. Ele pode ser usado tanto em produção quanto em desenvolvimento e parece ótimo para integração de servidores de aplicativos.

- [Clover:](https://www.atlassian.com/software/clover/overview) Clover é uma cobertura de código desenvolvida pela Atlassian. Ele é executado dentro do seu IDE e ajuda você a fazer integração contínua. Além disso, permite que você faça a otimização de teste para obter um melhor desempenho do aplicativo.

- [Mockito:](https://code.google.com/archive/p/mockito/) Mockito é uma biblioteca simulada de código aberto que permite criar simulações com sucesso. Você pode fazer todas as etapas, incluindo verificação, criação e stub.

- [Jetty:](http://www.eclipse.org/jetty/) Você está procurando um servidor de aplicativos leve e incorporável, Jetty é a sua resposta!

- [Hibernate:](http://hibernate.org/) Hibernate implementa a Java Persistence API e é um mapeador objeto-relacional.

- [VisualVM:](http://visualvm.java.net/) JVM pode ser uma coisa complexa de gerenciar. Com o VisualVM, você pode solucionar o problema e garantir a máxima eficiência.

- [JUnit:](http://junit.org/junit4/) O teste de unidade é importante e as ferramentas podem ajudá-lo a fazer isso. Com JUnit, framework de teste unitário, você pode testar seu aplicativo e progredir no ambiente TDD.

- [Jenkins:](http://jenkins-ci.org/) Jenkins é uma ferramenta obrigatória para programadores Java. É uma ferramenta de integração contínua e pode ser personalizada com centenas de plugins disponíveis.

- [Guava:](https://code.google.com/p/guava-libraries/) Guava é uma biblioteca de utilitários. A biblioteca contém centenas de bibliotecas principais usadas pelo Google. As bibliotecas principais só podem ser usadas para projetos baseados em Java. Por exemplo, pode ser usado em suporte a primitivos, anotações comuns, processamento de strings, etc.

- [FindBugs:](http://findbugs.sourceforge.net/) Encontrar bugs é uma parte importante da programação. Com o Fingbugs, você pode encontrar um bug em seu código usando o analisador de código estático. Ele classifica os bugs em diferentes níveis, como assustadores, preocupantes, mais assustadores ou **“preocupantes”** . Ele também pode ser usado no IDE como plugins ou como um programa autônomo.

- [Jackson:](https://github.com/FasterXML/jackson) Jackson é um analisador JSON. É leve, ergonômico e rápido de usar, comparado ao JSON simples.

  <a href="https://imgur.com/D7B7YBh"><img src="https://i.imgur.com/D7B7YBh.png" title="source: imgur.com" /></a>



## Principais recursos do JAVA

### Java é uma linguagem independente de plataforma.

Compiler(javac) converte o código-fonte (arquivo .java) para o código de byte (arquivo .class). Como mencionado acima, a JVM executa o bytecode produzido pelo compilador. Este código de byte pode ser executado em qualquer plataforma, como Windows, Linux, Mac OS etc. O que significa que um programa compilado no Windows pode ser executado no Linux e vice-versa. Cada sistema operacional tem uma JVM diferente, no entanto, a saída que eles produzem após a execução do bytecode é a mesma em todos os sistemas operacionais. É por isso que chamamos java de linguagem independente de plataforma.

### Java é uma linguagem orientada a objetos

A programação orientada a objetos é uma maneira de organizar programas como uma coleção de objetos, cada um dos quais representa uma instância de uma classe.

4 conceitos principais da programação orientada a objetos são:

1. Abstração
2. Encapsulamento
3. Herança
4. Polimorfismo

### Simples

Java é considerada uma linguagem simples porque não possui recursos complexos como sobrecarga de operadores, herança múltipla, ponteiros e alocação de memória explícita.

### Linguagem robusta

Robusto significa confiável. A linguagem de programação Java é desenvolvida de uma forma que coloca muita ênfase na verificação antecipada de possíveis erros, é por isso que o compilador Java é capaz de detectar erros que não são fáceis de detectar em outras linguagens de programação. As principais características do java que o tornam robusto são coleta de lixo, manipulação de exceções e alocação de memória.

### Seguro

Não temos ponteiros e não podemos acessar arrays fora do limite (você obtém ArrayIndexOutOfBoundsException se tentar fazer isso) em java. É por isso que várias falhas de segurança, como corrupção de pilha ou estouro de buffer, são impossíveis de explorar em Java.

### Java é distribuído

Usando a linguagem de programação java, podemos criar aplicativos distribuídos. RMI (Remote Method Invocation) e EJB (Enterprise Java Beans) são usados para criar aplicativos distribuídos em java. Em palavras simples: Os programas java podem ser distribuídos em mais de um sistema que está conectado entre si usando conexão com a internet. Objetos em uma JVM (máquina virtual java) podem executar procedimentos em uma JVM remota.

### Multithreading

Java suporta multithreading. Multithreading é um recurso Java que permite a execução simultânea de duas ou mais partes de um programa para utilização máxima da CPU.

### Portátil

Conforme discutido acima, o código Java escrito em uma máquina pode ser executado em outra máquina. O código de byte independente de plataforma pode ser transportado para qualquer plataforma para execução que torne o código Java portátil.

## Instalando o Eclipse Java IDE

Você pode instalar o Eclipse Java IDE por meio de um instalador ou de um download empacotado. Usando o instalador normalmente é mais rápido e fácil.

### Usando o instalador

Baixe o instalador via `https://eclipse.org/downloads/packages/`.



![java ide oomph04](https://www.vogella.com/tutorials/Eclipse/img/java-ide-oomph04.png)

No Linux, você precisa descompactá-lo antes de iniciá-lo. No Mac, o instalador é fornecido como um aplicativo empacotado e pode ser instalado e iniciado por meio de procedimentos regulares de instalação do Mac. No Windows e Mac, você pode executá-lo diretamente por meio do aplicativo executável / pacote fornecido.

Escolha *Eclipse IDE for Java Developers* na lista e execute a instalação.

![java ide oomph10](https://www.vogella.com/tutorials/Eclipse/img/java-ide-oomph10.png)

![java ide oomph20](https://www.vogella.com/tutorials/Eclipse/img/java-ide-oomph20.png)

Você pode ter que confirmar alguns contratos de licença.

Após a instalação, você pode iniciar o IDE diretamente. Lembre-se da pasta de instalação, nesta pasta você encontra a instalação do Eclipse para iniciá-la novamente.

![java ide oomph40](https://www.vogella.com/tutorials/Eclipse/img/java-ide-oomph40.png)



### Usando um download empacotado

Caso não queira usar o instalador, você também pode baixar diretamente o pacote *Eclipse IDE for Java Developers em:*`https://www.eclipse.org/downloads/packages/`

Pressione o link ao lado da descrição do pacote. Os links exibidos dependem do seu sistema operacional.

![Página de download do Eclipse](https://www.vogella.com/tutorials/Eclipse/img/eclipsedownload10.png)

O download depende da sua plataforma, é um arquivo compactado de vários arquivos ou um aplicativo empacotado (Mac).

Depois de fazer download do arquivo com a distribuição do Eclipse, descompacte-o em um diretório local ou siga o procedimento de instalação no Mac.

| <a href="https://imgur.com/TOY6T3k"><img src="https://i.imgur.com/TOY6T3k.png" title="source: imgur.com" style="zoom: 67%;" /></a> | Como desenvolvedor, você provavelmente sabe como extrair um arquivo compactado ou como instalar aplicativos no Mac.Mas em caso de dúvida, pesquise no google por "Como extrair um zip no Windows" ou "Como descompactar um arquivo no Linux" ou "Como instalar um arquivo dmg no Mac" |
| ------------------------------------------------------------ | ------------------------------------------------------------ |



## Começando a usar o Eclipse IDE

Clique duas vezes no `eclipse.exe`arquivo (Microsoft Windows) ou `eclipse`(Linux/Mac) em seu diretório de instalação para iniciar o Eclipse IDE.

| <a href="https://imgur.com/TOY6T3k"><img src="https://i.imgur.com/TOY6T3k.png" title="source: imgur.com" style="zoom: 67%;" /></a> | O que fazer se o Eclipse IDE não iniciarO Eclipse IDE (pelo menos partes dele) requer Java 17 para ser executado. Se o Eclipse não iniciar, verifique sua versão do Java. A versão do Eclipse instalada com o instalador normalmente já contém um tempo de execução Java adequado. |
| ------------------------------------------------------------ | ------------------------------------------------------------ |



### Escolhendo um espaço de trabalho

O Eclipse IDE solicita um espaço de *trabalho* para armazenar sua configuração. Selecione um diretório vazio e clique no botão**OK**botão.

![Selecionando o espaço de trabalho](https://www.vogella.com/tutorials/Eclipse/img/starteclipse10.png)

O Eclipse inicia e mostra a página de boas- *vindas* . Feche esta página clicando no *x* ao lado de Bem- *vindo* .

![Fechando a tela de boas-vindas do Eclipse](https://www.vogella.com/tutorials/Eclipse/img/starteclipse20.png)

Depois de fechar a tela de boas-vindas, o aplicativo deve ser semelhante à captura de tela a seguir.

![Fechando a tela de boas-vindas do Eclipse](https://www.vogella.com/tutorials/Eclipse/img/starteclipse30.png)



### Aparência

Por padrão, o Eclipse é fornecido em uma configuração leve, se preferir, você pode alternar para um tema escuro via **Window** **Preferências** **Em geral** Menu de **aparência .** A *seleção de Tema* permite alternar para o *tema Escuro* do Eclipse.

![Mudando o tema](https://www.vogella.com/tutorials/Eclipse/img/starteclipse40.png)

| <a href="https://imgur.com/TOY6T3k"><img src="https://i.imgur.com/TOY6T3k.png" title="source: imgur.com" style="zoom:25%;" /></a> | **Reinicie** seu IDE depois, algumas funcionalidades nativas de estilo do SO requerem uma reinicialização. |
| ------------------------------------------------------------ | ------------------------------------------------------------ |



## Terminologia importante do Eclipse

### Área de trabalho e projetos

A área de *trabalho* é o local físico (caminho do arquivo) para armazenar metadados e (opcional) seus artefatos de desenvolvimento. Os metadados armazenados para o espaço de trabalho contêm configurações de preferências, metadados específicos de plug-ins, logs, etc.

Você pode escolher a área de trabalho durante a inicialização do Eclipse ou através do **arquivo** **Alternar área de trabalho** **Outros** entrada do menu.

Seus projetos, arquivos de origem, imagens e outros artefatos podem ser armazenados dentro ou fora do seu espaço de trabalho. Por exemplo, se você usa o Git como sistema de controle de versão, normalmente armazena os repositórios Git fora do espaço de trabalho.

###  Visão geral da interface do usuário

O Eclipse fornece *visualizações* e *editores* para navegar e alterar o conteúdo. A visualização e os editores podem ser agrupados em *perspectivas* .

<details style="box-sizing: border-box; display: block; margin-bottom: 1.25em;"><summary class="title" style="box-sizing: border-box; cursor: pointer; display: list-item; outline: none; margin-bottom: 0.75em; color: rgb(33, 86, 165); text-decoration: underline;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;">Mais sobre perspectivas</font></font></summary><div class="content" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font><font style="box-sizing: border-box; vertical-align: inherit;"></font><font style="box-sizing: border-box; vertical-align: inherit;"></font></font><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></em><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></em><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><span class="menuseq" style="box-sizing: border-box; color: rgb(0, 0, 0); word-spacing: -0.02em;"><b class="menu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="submenu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="menuitem" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b></span></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"></em><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"></em></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><span class="menuseq" style="box-sizing: border-box; color: rgb(0, 0, 0); word-spacing: -0.02em;"><b class="menu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="submenu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="menuitem" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b></span></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"></em><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"></em></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><span class="menuseq" style="box-sizing: border-box; color: rgb(0, 0, 0); word-spacing: -0.02em;"><b class="menu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="submenu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="menuitem" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b></span></p></div><div class="imageblock" style="box-sizing: border-box; margin: 0px 0px 1.25em; padding: 0px; direction: ltr;"><div class="content" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><img src="https://www.vogella.com/tutorials/Eclipse/img/eclipseide_perspective10.png" alt="Alternando perspectivas no Eclipse IDE" loading="lazy" style="box-sizing: border-box; border: 0px; max-width: 100%; height: auto; display: inline-block; vertical-align: middle;"></div></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"></em></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><code style="box-sizing: border-box; font-family: Overpass-mono, monospace; font-size: 0.9375em; font-weight: 400; color: rgba(0, 0, 0, 0.9); overflow-wrap: break-word; letter-spacing: 0px; padding: 0.1em 0.5ex; word-spacing: -0.15em; background: rgb(232, 234, 237); border-radius: 4px; line-height: 1.45; text-rendering: optimizespeed; font-style: normal !important;"></code><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"></em></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"></em></p></div><div class="imageblock" style="box-sizing: border-box; margin: 0px 0px 1.25em; padding: 0px; direction: ltr;"><div class="content" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><img src="https://www.vogella.com/tutorials/Eclipse/img/eclipse_java.png" alt="Perspectiva Java do Eclipse" loading="lazy" style="box-sizing: border-box; border: 0px; max-width: 100%; height: auto; display: inline-block; vertical-align: middle;"></div></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"></em></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><span class="menuseq" style="box-sizing: border-box; color: rgb(0, 0, 0); word-spacing: -0.02em;"><b class="menu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="submenu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="menuitem" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b></span></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><span class="menuseq" style="box-sizing: border-box; color: rgb(0, 0, 0); word-spacing: -0.02em;"><b class="menu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="submenu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="menuitem" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></b></span><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font><font style="box-sizing: border-box; vertical-align: inherit;"></font></font><em style="box-sizing: border-box; font-style: italic; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></em><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></p></div><div class="imageblock" style="box-sizing: border-box; margin: 0px 0px 1.25em; padding: 0px; direction: ltr;"><div class="content" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><img src="https://www.vogella.com/tutorials/Eclipse/img/ide_showview10.png" alt="Mostrar caixa de diálogo de visualização" loading="lazy" style="box-sizing: border-box; border: 0px; max-width: 100%; height: auto; display: inline-block; vertical-align: middle;"></div></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font><span class="menuseq" style="box-sizing: border-box; color: rgb(0, 0, 0); word-spacing: -0.02em;"><b class="menu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="menuitem" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></b></span><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></p></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font><span class="menuseq" style="box-sizing: border-box; color: rgb(0, 0, 0); word-spacing: -0.02em;"><b class="menu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="menuitem" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></b></span><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></p></div><div class="imageblock" style="box-sizing: border-box; margin: 0px 0px 1.25em; padding: 0px; direction: ltr;"><div class="content" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><img src="https://www.vogella.com/tutorials/Eclipse/img/eclipseide_saveperspective10.png" alt="Salve sua configuração de perspectiva" loading="lazy" style="box-sizing: border-box; border: 0px; max-width: 100%; height: auto; display: inline-block; vertical-align: middle;"></div></div><div class="paragraph" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><p style="box-sizing: border-box; margin: 0px 0px 1.25rem; padding: 0px; direction: ltr; font-family: inherit; font-weight: 400; font-size: 1.0625rem; line-height: 1.58; text-rendering: optimizelegibility; letter-spacing: -0.003em; font-style: normal;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font><span class="menuseq" style="box-sizing: border-box; color: rgb(0, 0, 0); word-spacing: -0.02em;"><b class="menu" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></b><i class="fa fa-angle-right caret" style="box-sizing: border-box; font-style: normal; line-height: 1; display: inline-block; font-variant: normal; font-weight: bold; font-stretch: normal; font-family: FontAwesome; font-size: inherit; text-rendering: auto; -webkit-font-smoothing: antialiased; text-align: center; width: 0.45em;"></i><b class="menuitem" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></b></span><font style="box-sizing: border-box; vertical-align: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font><span class="menuseq" style="box-sizing: border-box; color: rgb(0, 0, 0); word-spacing: -0.02em;"><b class="menuitem" style="box-sizing: border-box; font-weight: inherit; line-height: inherit;"><font style="box-sizing: border-box; vertical-align: inherit;"></font></b></span><font style="box-sizing: border-box; vertical-align: inherit;"></font></font></p></div><div class="imageblock" style="box-sizing: border-box; margin: 0px 0px 1.25em; padding: 0px; direction: ltr;"><div class="content" style="box-sizing: border-box; margin: 0px; padding: 0px; direction: ltr;"><img src="https://www.vogella.com/tutorials/Eclipse/img/perspective_customize10.png" alt="Personalizar perspectiva" loading="lazy" style="box-sizing: border-box; border: 0px; max-width: 100%; height: auto; display: inline-block; vertical-align: middle;"></div></div></div></details>

Uma visualização é normalmente usada para exibir dados estruturados e permitir modificá-los diretamente.

Por exemplo, a visualização *Project Explorer* permite navegar e modificar arquivos de projetos Eclipse. Se você renomear um arquivo por meio do *Project Explorer,* o nome do arquivo será alterado diretamente sem precisar salvar.



Os editores são normalmente usados para modificar um único elemento de dados, por exemplo, um arquivo de texto. Para aplicar essas alterações ao modo de dados subjacente, você precisa selecionar salvar no menu ou na barra de ferramentas. Um editor com dados não salvos (um editor sujo) é marcado com um asterisco à esquerda do nome do arquivo modificado.

![Editor marcado como sujo](https://www.vogella.com/tutorials/Eclipse/img/dirtyeditor10.png)

### Projetos Eclipse

Um projeto Eclipse contém arquivos de origem, configuração e binários relacionados a uma determinada tarefa. Ele os agrupa em unidades edificáveis e reutilizáveis. Um projeto Eclipse pode ter *naturezas* atribuídas a ele que descrevem o propósito deste projeto. Por exemplo, a *natureza* Java define um projeto como projeto Java. Os projetos podem ter múltiplas naturezas combinadas para modelar diferentes aspectos técnicos.

*As naturezas* de um projeto são definidas através do arquivo *.project* no diretório do projeto.



## A perspectiva Java do Eclipse

A descrição a seguir é uma pequena introdução a elementos importantes da perspectiva Java. Sinta-se à vontade para pular este capítulo, pois ele só pode ser usado como referência.



### Visualização do Explorador de Pacotes

A visualização *Package Explorer* permite que você navegue na estrutura de seus projetos e abra arquivos em um *editor* com um clique duplo no arquivo.

Também é usado para alterar a estrutura do seu projeto. Por exemplo, você pode renomear arquivos ou mover arquivos e pastas por meio de arrastar e soltar. Um clique com o botão direito do mouse em um arquivo ou pasta mostra as opções disponíveis.

![Explorador de Pacotes](https://www.vogella.com/tutorials/Eclipse/img/packageexplorerview20.png)



###  Vista de destaques

A visualização *Esboço* mostra a estrutura do arquivo de origem selecionado no momento.

![Vista de destaques](https://www.vogella.com/tutorials/Eclipse/img/outlineview10.png)

### Visualização de problemas

A visualização *Problemas* mostra erros e mensagens de aviso. Mais cedo ou mais tarde, você terá problemas com seu código ou com a configuração do seu projeto. Para visualizar os problemas em seu projeto, você pode usar a visualização *Problemas* , que faz parte da *perspectiva* Java padrão . Se esta visualização estiver fechada, você poderá abri-la via **Janela** **Mostrar visualização** **Problemas** .

![Erros na visualização do problema](https://www.vogella.com/tutorials/Eclipse/img/problemsview10.png)

As mensagens exibidas na visualização *Problemas* podem ser configuradas através do menu suspenso da visualização. Por exemplo, para exibir os problemas do projeto atualmente selecionado, selecione *Configure Contents* e defina o Scope como *On any element in the same project* .

![Menu suspenso da visualização de problemas](https://www.vogella.com/tutorials/Eclipse/img/problemsview20.png)

![Personalização](https://www.vogella.com/tutorials/Eclipse/img/problemsview30.png)

A visualização de *Problemas* também permite acionar uma *correção rápida* clicando com o botão direito do mouse em várias mensagens selecionadas.

![Personalização](https://www.vogella.com/tutorials/Eclipse/img/problemsview40.png)



### Visualização Javadoc

A visualização *Javadoc* mostra a documentação do elemento selecionado no *editor* Java .

![Visualização Javadoc](https://www.vogella.com/tutorials/Eclipse/img/javadocview12.png)



### Editor Java

*O editor* Java é usado para modificar o código-fonte Java. Cada arquivo de origem Java é aberto em um *editor* separado .

<a href="https://imgur.com/b9YNAO2"><img src="https://i.imgur.com/b9YNAO2.png" title="source: imgur.com" /></a>

Se você clicar na coluna esquerda do editor, poderá configurar suas propriedades, por exemplo, que o número da linha deve ser exibido.

![image-20221031144421359](C:\Users\Home\AppData\Roaming\Typora\typora-user-images\image-20221031144421359.png)



## Crie seu primeiro programa Java

###  Criar projeto

Selecionar **arquivo** **Novo** **Projeto Java** no menu.

<a href="https://imgur.com/MoTE4ql"><img src="https://i.imgur.com/MoTE4ql.png" title="source: imgur.com" /></a>

Um novo projeto é criado e exibido como uma pasta.

| <a href="https://imgur.com/TOY6T3k"><img src="https://i.imgur.com/TOY6T3k.png" title="source: imgur.com" /></a> | O projeto geralmente é nomeado da mesma forma que o pacote Java de nível superior no projeto. Isso torna mais fácil encontrar um projeto relacionado a um pedaço de código. |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
|                                                              |                                                              |

###  Criar pacote

| <a href="https://imgur.com/TOY6T3k"><img src="https://i.imgur.com/TOY6T3k.png" title="source: imgur.com" /></a> | Uma boa convenção de nomenclatura é usar o mesmo nome para o pacote de nível superior e o projeto. Por exemplo, se você nomear seu projeto, `com.example.javaproject`você também deve usar `com.example.javaproject`como o nome do pacote de nível superior. |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
|                                                              |                                                              |

Crie o `com.eclipse.primeiro.programa`pacote selecionando a `src`pasta, clique com o botão direito nele e selecione **Novo** **Pacote** .

<a href="https://imgur.com/LE9rnWD"><img src="https://i.imgur.com/LE9rnWD.png" title="source: imgur.com" /></a>

aperte o**Terminar**botão.

<a href="https://imgur.com/W60yJpy"><img src="https://i.imgur.com/W60yJpy.png" title="source: imgur.com" /></a>

### Criar classe Java

Clique com o botão direito do mouse em seu pacote e selecione **Novo** **Classe** para criar uma classe Java.

<a href="https://imgur.com/24Q3NOb"><img src="https://i.imgur.com/24Q3NOb.png" title="source: imgur.com" /></a>

Digite `MinhaPrimeiraClasse`como o nome da classe e marque a caixa de seleção *public static void main (String[] args)* .

![image-20221031145714231](C:\Users\Home\AppData\Roaming\Typora\typora-user-images\image-20221031145714231.png)

aperte o**Terminar**botão.

Isso cria um novo arquivo e abre o editor Java. Altere a classe com base na listagem a seguir.

```java
package com.eclipse.primeiro.programa;

public class MinhaPrimeiraClasse {

  public static void main(String[] args) {
    System.out.println("Hello Eclipse!");
  }

}
```

Você também pode criar novos pacotes diretamente através desta caixa de diálogo. Se você inserir um novo pacote nesta caixa de diálogo, ele será criado automaticamente.

### Execute o código do aplicativo a partir do IDE

Agora execute seu código. Clique com o botão direito do mouse em sua classe Java no *Package Explorer* ou clique com o botão direito na classe Java e selecione **Executar como** **Aplicativo Java** .

<a href="https://imgur.com/W28wc8a"><img src="https://i.imgur.com/W28wc8a.png" title="source: imgur.com" /></a>

O Eclipse executará seu programa Java. Você deve ver a saída na visualização do *console* .

![Resultado do aplicativo em execução](https://www.vogella.com/tutorials/Eclipse/img/xfirstgany70.png.pagespeed.ic.PRtmZ2mZ3W.webp)

Parabéns! Você criou seu primeiro projeto Java, um pacote, uma classe Java e executou este programa dentro do Eclipse.

### Execute seu programa fora do Eclipse

Abra um shell de comando, por exemplo, em Microsoft Windows selecione **Iniciar** **Execute** e digite`cmd`e pressione a tecla Enter. Isso deve abrir uma janela do console.

Alterne para o diretório que contém o arquivo *JAR* , digitando `cd path`. Por exemplo, se seu *JAR* estiver localizado em *c:\temp* , use o comando a seguir.

```
cd c:\temp
```

Para executar este programa, inclua o arquivo *JAR* em seu *classpath* . O *classpath* define quais classes Java estão disponíveis para o Java Runtime. Você pode incluir um arquivo *JAR* no caminho de classe com a opção *-classpath* .

```
java -classpath meuprograma.jar com.eclipse.MyFirstClass
```

Digite o comando acima no diretório que você usou para a exportação e você verá a mensagem "Hello Eclipse!" saída em seu shell de comando.

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>
