<h1>Introdução de JAVA</h1>



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

<img src="C:\Users\Home\Documents\Generation\cookbook_java-main\JavaVirtualMachine2.jpg" alt="JVM" style="zoom: 67%;" />

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

  <img src="C:\Users\Home\Documents\Generation\cookbook_java-main\5su8kepzlgmz6bxs2fhu.png" alt="Java IDEs (of March) - DEV Community 👩‍💻👨‍💻" style="zoom:50%;" />



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



<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>
