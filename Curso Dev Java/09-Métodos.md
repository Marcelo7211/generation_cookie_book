<h1>Métodos</h1>



As informações passadas neste documento norteia os conceitos da Oracle e podemos encontrar através deste link:

<div align="left"><a href="https://www.oracle.com/br/technical-resources/articles/java/consume-classes-java-in-database.html"><img src="https://i.imgur.com/DYnNz6q.png" title="source: imgur.com" width="10%"/>Oracle</a></div>



Um Método é uma função associada à Classe, ou seja uma ação. Os Métodos permitem a pessoa desenvolvedora modularizar os programas, separando suas tarefas em unidades autocontidas. O Métodos são inspirados na conhecida Técnica do *“dividir para conquistar”*. Outra grande vantagem do uso de Método é que eles são reutilizáveis em futuros programas, evitando a repetição de código.

**Exemplos:**

- **Carro:** Acelerar, Frear, Virar, Parar
- **Conta Bancária:** Sacar, Depositar, Trasnferir

Para promover a capacidade de reutilização de software, todos os métodos devem estar limitados à realização de uma única tarefa bem definida. O nome do método também deve ser assertivo e expressar essa tarefa efetivamente. Os métodos tornam mais fácil as tarefas de escrever, depurar, manter e modificar programas, pelo simples fato de **um método que realiza apenas uma tarefa é mais fácil de testar e depurar do que um método maior que realiza muitas tarefas**.

Os métodos são essencialmente procedimentos que podem manipular atributos de objetos para os quais o método foi definido e receber **parâmetros por valor** através da **lista de argumentos** presentes na sua assinatura.

Antes de detalharmos como se declara um Método, é importante reforçar o conceito de pacotes, ou packages:

<h2>1. Pacotes</h2>

No desenvolvimento de pequenas aplicações Java, pode ser viável manter todo o código em um mesmo diretório. Entretanto, para aplicações maiores, colocar todos os arquivos em um mesmo local, sem uma organização, pode aumentar significativamente a possibilidade de conflitos de classes (classes com o mesmo nome no mesmo escopo) e dificultar a localização de um determinado código, método ou criar problemas de visibilidade, que veremos mais adiante.

Em Java, a solução para esses problemas está na organização das classes em **pacotes**. Um **Pacote** ou **Package** na    tecnologia Java nada mais é do que um conjunto de classes localizadas na mesma estrutura hierárquica de pastas.    Usualmente, são colocadas em um **Pacote** todas as classes relacionadas, construídas com um propósito comum para    promover a reutilização de código. Na imagem abaixo, vemos um projeto Java estruturado em Pacotes:

<div align="center"><img src="https://i.imgur.com/agW7FRa.png" title="source: imgur.com" /></div>

O próprio código base da tecnologia Java está todo estruturado em pacotes, como pode ser observado na especificação    da API (*Application Programming Interface*, ou Interface de Programação de Aplicações) da plataforma Java SE, apresentada parcialmente na tabela abaixo:

| **Pacote API** | **Suporta**                                                  |
| -------------- | ------------------------------------------------------------ |
| java.awt       | **Recursos gráficos**: botão, barra, caixas de texto, janela, etc.  Em outras palavras: recursos GUI (Graphical User Interface). |
| java.io        | Input e output de dados (entrada e saída)                    |
| java.lang      | Recursos de linguagem                                        |
| java.math      | **Operações matemáticas**                                    |
| java.net       | Rede                                                         |
| java.security  | Segurança                                                    |
| java.text      | **Recursos de texto**                                        |
| java.util      | Miscelânea de recursos utilitários                           |
| javax.swing    | Complemento ao pacote awt                                    |

<h3>1.1 Criando um Pacote no Eclipse</h3>

1. Crie um novo Projeto Java no Eclipse (menu: **File 🡪 New 🡪 Java Project**)
2. O nome do projeto será **aula_metodos**, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/bhYdYFT.png" title="source: imgur.com" /></div>

3. Clique no botão **Finish** para continuar.

4. No lado esquerdo superior, na Guia **Package explorer**, clique com o botão direito do mouse sobre a pasta **src**, como indicado na figura abaixo:

<div align="center"><img src="https://i.imgur.com/DZj7Qic.png" title="source: imgur.com" /></div>

5. Na sequência, clique na opção **New 🡪 Package**.

<div align="center"><img src="https://i.imgur.com/VOeZmF2.png" title="source: imgur.com" /></div>

6. Na janela **New Java Package**, no item **Name**, acrescente no final do nome do projeto **.pacote1**, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/QId6tbt.png" title="source: imgur.com" /></div>

7. Clique no botão **Finish** para concluir.

A estrutura de pacotes da aplicação ficará igual a figura abaixo:

<div align="center"><img src="https://i.imgur.com/fHVWGxr.png" title="source: imgur.com" /></div>

Observe na imagem acima, que o **pacote1** está com o seu ícone na cor branca porque no momento não foi criada nenhuma Classe dentro do pacote.

<h2>2. Declarando Métodos</h2>



<div align="center"><img src="https://i.imgur.com/IJNtFZp.png" title="source: imgur.com" /></div>

<h3>2.1. Modificador</h3>

É um item opcional na definição do Método. O Escopo é uma combinação de: 

<h4>2.2.2. Modificadores de Acesso</h4>

Determina como o Método será manipulado no decorrer do desenvolvimento do programa, ou seja, qual (is) Classes podem chamar o Método. Na tabela abaixo temos os Modificadores de visibildade:

| **Modificador** | **Descrição**                                                |
| --------------- | ------------------------------------------------------------ |
| **padrão**      | Um Método padrão (identificado pela ausência de modificadores) poderá ser acessado por todas as classes que estiverem **no mesmo pacote**, que a classe que possui o Atributo. |
| **public**      | Um Método poderá ser acessado por qualquer classe em qualquer pacote. O  acesso a um método só é permitido se você tiver primeiro acesso à classe (Pública). |
| **protected**   | Um Método protected é protegido e pode ser chamado por todas as classes que compõe o pacote  **package**. A grande diferença para o modificador padrão é que uma classe (mesmo que esteja fora do pacote), que estende a Classe com o Atributo ou o Método protected, ela terá acesso a ele, logo o acesso é por pacote e por herança. |
| **private**     | Um Método private possui o acesso restrito. Somente a Classe que o definiu pode acessá-lo, ou seja, um  método privado só poderá ser acessado dentro da classe que o definiu. |

Independentemente do moderador escolhido, um método pode ser chamado, a partir de qualquer outro método contido na mesma classe.

Nas imagens abaixo podemos visualizar o funcionamento dos modificadores com Métodos em 3 situações diferentes:

<h5>Métodos da mesma Classe</h5>

<div align="center"><img src="https://i.imgur.com/kE0Q3cL.png" title="source: imgur.com" /></div>

*Observe que um Método consegue acessar todos os Métodos que estão dentro da Classe, independente do Modificador de Visibilidade.*

<h5>Métodos de Classes diferentes e no mesmo Pacote</h5>

<div align="center"><img src="https://i.imgur.com/8u5Ovz3.png" title="source: imgur.com" /></div>

*Observe que um Método da Classe 01, conseguirá acessar apenas os Métodos Friendly, Protected e Public que estão dentro da Classe 02, no mesmo Pacote da Classe 01.*

<h5>Métodos de Classes e Pacotes diferentes</h5>

<div align="center"><img src="https://i.imgur.com/pMwNgCO.png" title="source: imgur.com" /></div>

*Observe que um Método da Classe 01, conseguirá acessar apenas os Métodos Public que estão dentro da Classe 03, no Pacote 01. (pacotes diferentes)*

<div align="center"><img src="https://i.imgur.com/NdEp3gV.png" title="source: imgur.com" /></div>

A imagem acima mostra o nível de visibilidade de um Método, do nível de acesso mais restrito (Private) ao nível de acesso total e irrestrito (Public). Na tabela abaixo temos um resumo:

| Modificador   | Classe | Pacote | Sub Classe | Mundo |
| ------------- | :----: | :----: | :--------: | :---: |
| **public**    |   ✔    |   ✔    |     ✔      |   ✔   |
| **protected** |   ✔    |   ✔    |     ✔      |   ❌   |
| **padrão**    |   ✔    |   ✔    |     ❌      |   ❌   |
| **private**   |   ✔    |   ❌    |     ❌      |   ❌   |

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <div align="left"> **ATENÇÃO:** *Modificadores de acesso de um Método definem como o Método será acessado por outro Método da sua própria Classe e de outras Classes, ou seja, não confunda com direitos de acesso a aplicação ou segurança da informação.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<h4>2.1.2. Modificadores do Método</h4>

O modificador do método permite especificar algumas propriedades, determinando como as classes derivadas podem ou não redefinir ou alterar o método, e de que forma esse método será visível. 

| Modificador  | Descrição                                                    |
| ------------ | ------------------------------------------------------------ |
| **abstract** | Um  método abstrato não implementa nenhuma funcionalidade, somente assina o  método e faz com que a primeira subclasse concreta seja obrigada a  implementar o método. Uma classe que possua um método abstrato deve  obrigatoriamente ser abstrata. |
| **final**    | Um  método final define que não pode ser sobreposto.         |
| **static**   | Um  método static é  compartilhado por todos os objetos instanciados a partir da mesma Classe. Ele  não pode acessar qualquer variável declarada dentro da classe (exceto se a  variável for **static**),  pois não é capaz de discernir entre os diferentes objetos que compartilham  esse método. Um bom exemplo de Método Static é o Main().<br />Na execução de uma programa Java, a JVM (Java Virtual Machine) tenta  chamar o método main da classe que foi especificada. Quando declarado o  método main como static, ele permite que a JVM invoque o método main sem criar uma instância da classe, ou seja, a classe é  conhecida como classe principal, que efetuará os  testes e chamadas das classes para a execuções dos programas. |

**Observações importantes:**

- Os modificadores de acesso (padrão, public, private e protected) nunca poderão ser combinados 
- Um método nunca poderá ser abstract e final
- Um método nunca poderá ser abstract e private
- Um método final nunca poderá ser sobreposto
- Um método abstrato nunca poderá ser implementado
- Se um método for abstrato a classe também será abstrata

<h3>2.2. Tipo</h3>

É o indicador do valor de retorno do Método (int, String, double, float e etc). Caso utilize o indicador **void** o método **não terá um valor de retorno**.

| **Tipo**    | **Tamanho**                 | **Wrapper** |
| ----------- | --------------------------- | ----------- |
| **boolean** | *true* ou *false*           | Boolean     |
| **char**    | 16  bits                    | Character   |
| **byte**    | 08  bits                    | Byte        |
| **short**   | 16  bits                    | Short       |
| **int**     | 32  bits                    | Integer     |
| **long**    | 64  bits                    | Long        |
| **float**   | 32  bits                    | Float       |
| **double**  | 64  bits                    | Double      |
| **void**    | Não  retorna valor          | Void        |
| **String**  | **Não é um tipo primitivo** |             |

> **Wrapper:** Vem do verbo inglês “wrap” que significa envolver. São Classes que adicionam funcionalidades aicionais aos tipos primitivos. A Classe Wrapper transforma um primitivo em um Objeto e adiciona Métodos. 
>
> **Exemplo:**
>
> ```java
> Integer numeroInteiro = Integer.valueOf(2);
> ```
>
> Neste exemplo está sendo criado um **Objeto da Classe wrapper Integer**, chamado **numeroInteiro**, contendo valor 2.

<h3>2.3. Nome</h3>

É nome do método. Por padrão o nome do Método começa com letras minúsculas e caso seja composto, a partir da segunda palavra utiliza-se a primeira letra maiúscula (camelCase). O nome do Método deve ser assertivo e indicar exatamente o que ele faz. Veja abaixo alguns exemplos:

- somar
- calcularArea

<h3>2.4. Argumentos</h3>

São os parâmetros do Método. São representados por uma **lista de parâmetros** (variáveis) separados por vírgulas, onde cada parâmetro obedece a forma: **tipo** **nome**

<h2>3. Exemplo 1: Visibilidade dos Métodos</h2>

Através deste exemplo, vamos entender na prática como funcionam os Modificadores de Visibilidade no Java. Utilizando o projeto **aula_metodos**, criado no tópico **Pacotes**, vamos criar 3 Classes:

- **TestaMetodos** - Classe Principal no pacote aula_metodos
- **Classe1** - no pacote aula_metodos
- **ClassePacote1** - no pacote Pacote1

<h3>3.1. Classe TestaMetodos - Visibilidade dentro da Classe</h3>

1. No lado esquerdo superior, na Guia **Package explorer**, clique com o botão direito do mouse sobre a pasta **src**, como indicado na figura abaixo:

<div align="center"><img src="https://i.imgur.com/9mSJOUP.png" title="source: imgur.com" /></div>

2. Na sequência, clique na opção **New 🡪 Class**.

<div align="center"><img src="https://i.imgur.com/l9Blwhg.png" title="source: imgur.com" /></div>

3. Na janela **New Java Class**, no item **Package**, altere para **aula_metodos** (pacote principal). No item **Name**, digite o nome da Classe **TestaMetodos** e marque a opção **public static void main(String[] args)**, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/lV3XKrN.png" title="source: imgur.com" /></div>

4. Clique no botão **Finish** para concluir.

A estrutura de pacotes da aplicação ficará igual a figura abaixo:

<div align="center"><img src="https://i.imgur.com/XSq0zi3.png" title="source: imgur.com" /></div>

Insira o código abaixo na Classe TestaMetodos:

```java
package aula_metodos;

public class TestaMetodos {

	public static void main(String[] args) {

//	        Chamadas dos Métodos criados na Classe TestaMétodos
	        metodoPublico();
	        metodoFriendly();
	        metodoProtegido();
	        metodoPrivado();

	}

//	Métodos da Classe TestaMétodos
    
    //Método Public
	public static void metodoPublico(){
        System.out.println("Método Público");
    }

    //Método Friendly
    static void metodoFriendly(){
        System.out.println("Método Friendly");
    }

    //Método Protected
    protected static void metodoProtegido(){
        System.out.println("Método Protegido");
    }

    //Método Private
    private static void metodoPrivado(){
        System.out.println("Método Privado");
    }
    
}
```

Execute o Projeto e observe que todos os Métodos serão executados e não será exibido nenhum erro no código, porque todos os Métodos estão na mesma Classe e no mesmo Pacote.

<h3>3.2. Classe1 - Visibilidade entre Classes</h3>

1. No lado esquerdo superior, na Guia **Package explorer**, clique com o botão direito do mouse sobre o pacote **aula_metodos**, como indicado na figura abaixo:

<div align="center"><img src="https://i.imgur.com/aA6vfmO.png" title="source: imgur.com" /></div>

5. Na sequência, clique na opção **New 🡪 Class**.

<div align="center"><img src="https://i.imgur.com/O3Chd1o.png" title="source: imgur.com" /></div>

6. Na janela **New Java Class**, no item **Package**, altere para **aula_metodos** (pacote principal). No item **Name**, digite o nome da Classe **Classe1** e desmarque a opção **public static void main(String[] args)**, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/vuOUaqJ.png" title="source: imgur.com" /></div>

7. Clique no botão **Finish** para concluir.

A estrutura de pacotes da aplicação ficará igual a figura abaixo:

<div align="center"><img src="https://i.imgur.com/B3GGWnR.png" title="source: imgur.com" /></div>

Insira o código abaixo na Classe **Classe1**:

```java
package aula_metodos;

public class Classe1 {

	public static void metodoPublico1(){
        System.out.println("Método Público da Classe 01");
    }

    static void metodoFriendly1(){
        System.out.println("Método Friendly da Classe 01");
    }

    protected static void metodoProtegido1(){
        System.out.println("Método Protegido da Classe 01");
    }

	private static void metodoPrivado1(){
        System.out.println("Método Privado da Classe 01");
    }
    
}
```

Altere o Método **main**, da Classe **TestaMetodos**:

```java
package aula_metodos;

public class TestaMetodos {

	public static void main(String[] args) {

//	        Chamadas dos Métodos criados na Classe TestaMétodos
	        metodoPublico();
	        metodoFriendly();
	        metodoProtegido();
	        metodoPrivado();

//	        Chamadas dos Métodos criados na Classe Classe1
	        Classe1.metodoPublico1();
	        Classe1.metodoFriendly1();
	        Classe1.metodoProtegido1();
        
	        // Erro: Método Private não pode ser acessado por outra Classe
	        Classe1.metodoPrivado1(); 
	}

//	Métodos da Classe TestaMétodos
    
    //Método Public
	public static void metodoPublico(){
        System.out.println("Método Público");
    }

    //Método Friendly
    static void metodoFriendly(){
        System.out.println("Método Friendly");
    }

    //Método Protected
    protected static void metodoProtegido(){
        System.out.println("Método Protegido");
    }

    //Método Private
    private static void metodoPrivado(){
        System.out.println("Método Privado");
    }
    
}
```

Para chamar os Métodos de outra Classe, localizadas no mesmo Pacote, é necessário informar o nome da Classe, seguido por um ponto e o nome do Método. **Exemplo:** *Classe1.metodoPublico1();*

Observe que ao inserir as chamadas para os Métodos da Classe1, no Método main da Classe TestaMetodos, **será exibido um erro na chamada do Método Privado1**, indicando que ele não está acessível por se tratar de um **Método Private**, acessível apenas na Classe onde foi criado. Comente esta linha e você verá que os demais Métodos serão executados e não será exibido nenhum erro no código.

<h3>3.3. ClassePacote1 - Visibilidade entre Classes em Pacotes diferentes</h3>

1. No lado esquerdo superior, na Guia **Package explorer**, clique com o botão direito do mouse sobre o pacote **aula_metodos.pacote1**, como indicado na figura abaixo:

<div align="center"><img src="https://i.imgur.com/f34fGSj.png" title="source: imgur.com" /></div>

5. Na sequência, clique na opção **New 🡪 Class**.

<div align="center"><img src="https://i.imgur.com/oo4DL7q.png" title="source: imgur.com" /></div>

6. Na janela **New Java Class**, no item **Name**, digite o nome da Classe **ClassePacote1** e desmarque a opção **public static void main(String[] args)**, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/l3EvWeb.png" title="source: imgur.com" /></div>

7. Clique no botão **Finish** para concluir.

A estrutura de pacotes da aplicação ficará igual a figura abaixo:

<div align="center"><img src="https://i.imgur.com/Y6PwaYb.png" title="source: imgur.com" /></div>

Insira o código abaixo na Classe **ClassePacote1**:

```java
package aula_metodos.pacote1;

public class ClassePacote1 {

	public static void metodoPublicoPacote1(){
        System.out.println("Método Público da Classe ClassePacote1");
    }

    static void metodoFriendlyPacote1(){
        System.out.println("Método Friendly da Classe ClassePacote1");
    }

    protected static void metodoProtegidoPacote1(){
        System.out.println("Método Protegido da Classe ClassePacote1");
    }

    private static void metodoPrivadoPacote1(){
        System.out.println("Método Privado da Classe ClassePacote1");
    }
    
}
```

Altere o Método **main**, da Classe **TestaMetodos**:

```java
package aula_metodos;

import static aula_metodos.pacote1.ClassePacote1.*;

public class TestaMetodos {

	public static void main(String[] args) {

//	        Chamadas dos Métodos criados na Classe TestaMétodos
	        metodoPublico();
	        metodoFriendly();
	        metodoProtegido();
	        metodoPrivado();

//	        Chamadas dos Métodos criados na Classe Classe1
	        Classe1.metodoPublico1();
	        Classe1.metodoFriendly1();
	        Classe1.metodoProtegido1();
        
        	// Erro: Método Private não pode ser acessado por outra Classe
	        Classe1.metodoPrivado1();
        
//	        Chamadas dos Métodos criados na Classe ClassePacote1
	        metodoPublicoPacote1();
        
        	// Erro: Método Friendly não pode ser acessado por uma Classe em outro Pacote
	        metodoFriendlyPacote1(); 
        
        	// Erro: Método Protected não pode ser acessado por uma Classe em outro Pacote
	        metodoProtegidoPacote1();
        
        	// Erro: Método Private não pode ser acessado por outra 
        	// Classe independente do Pacote
	        metodoPrivadoPacote1(); 
	}

//	Métodos da Classe TestaMétodos
    
    //Método Public
	public static void metodoPublico(){
        System.out.println("Método Público");
    }

    //Método Friendly
    static void metodoFriendly(){
        System.out.println("Método Friendly");
    }

    //Método Protected
    protected static void metodoProtegido(){
        System.out.println("Método Protegido");
    }

    //Método Private
    private static void metodoPrivado(){
        System.out.println("Método Privado");
    }
    
}
```

Para acessar os Métodos de uma Classe, localizada em outro pacote, é necessário importar o Pacote, através do comando **import**, como vemos no código acima, na segunda linha (**import static aula_metodos.pacote1.ClassePacote1.*;**).

Observe que ao inserir as chamadas para os Métodos da ClassePacote1, no Método main da Classe TestaMetodos, **será exibido um erro na chamada dos Métodos FriendlyPacote1, ProtectedPacote1 e PrivadoPacote1**, indicando que eles não estão acessíveis por não se tratarem de **Métodos Public**. Uma Classe ao chamar os Métodos de uma outra Classe em Pacotes diferentes, terá acesso apenas aos Métodos Public. Comente as 3 linhas e você verá que os demais Métodos serão executados e não será exibido nenhum erro no código.

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <div align="left"> **ATENÇÃO:** *Através do exemplo acima, vimos na prática como o Java trata os Métodos em relação aos Modificadores de Visibilidade. Os Modificadores do Método, serão vistos conforme avançarmos nos próximos temas.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h2> 4. Sobrecarga de Métodos</h2>

Sobrecarregar métodos significa ter vários métodos com nomes iguais, mas assinaturas diferentes. Veja o exemplo abaixo:

```java
	public static void imprimeOperacao(String operacao, int resultado) {
		System.out.println("\nO resultado da " + operacao + " é: " + resultado);
	}

	public static void imprimeOperacao(String operacao, float resultado) {
		System.out.println("\nO resultado da " + operacao + " é: " + resultado);
	}
```

Observe que foram criados 2 Métodos com o mesmo nome, entretanto as assinaturas dos Métodos são diferentes:

- O primeiro possui 1 parâmetro String e 1 parâmetro int.
- O segundo possui 1 parâmetro String e 1 parâmetro float.

Graças a Sobrecarga de Métodos é possível ter várias versões de um mesmo Método recebendo diferentes tipos de parâmetros. Você pode aplicar a Sobrecarga em qualquer Método da sua Classe, **exceto o Método Main**.

<h2>5. Exemplo 2: Calculadora Completo</h2>

Vamos adaptar o exemplo da Calculadora, utilizando Métodos para realizar as operações matemáticas:

```java
package calculadora;

import java.util.Scanner;

public class Calculadora {

	private static Scanner leia = new Scanner(System.in);
	
	public static void main(String[] args){
				
		int a, b = 0;
		
		System.out.println("Digite o primeiro numero: ");
		a = leia.nextInt();
		System.out.println("Digite o segundo numero: ");
		b = leia.nextInt();
		
		// Executa o Método imprimeOperacao com 2 parâmetros
		// Nome da operação e o Método inteiro que executa a operação
		imprimeOperacao( "Soma", soma(a, b));
		imprimeOperacao( "Subtração", subtracao(a, b));
		imprimeOperacao( "Multiplicação", multiplicacao(a, b));
		imprimeOperacao( "Divisão", divisao(a, b));
         
         // Executa o Método imprimeOperacao com 2 parâmetros
		// Nome da operação e o Método float que executa a operação
		imprimeOperacao( "Soma", soma(100.0f, 50.0f));
		
        // Executa o Método turma()
		turma();
	}
	
	// Método soma com 2 parâmetros inteiros
	public static int soma(int s1, int s2) {
		return s1 + s2;
	}
	
	// Método soma com 2 parâmetros float
	public static float soma(float s1, float s2) {
		return s1 + s2;
	}
	
	// Método subtracao com 2 parâmetros inteiros
	public static int subtracao(int a, int b) {
		return a - b;
	}

	// Método multiplicacao com 2 parâmetros inteiros
	public static int multiplicacao(int a, int b) {
		return a * b;
	}

	// Método divisao com 2 parâmetros inteiros
	public static int divisao(int a, int b) {
		return a / b;
	}
	
	// Método imprimeOperacao do tipo void com 
	// 1 parâmetro String e 1 parâmetro inteiro
	public static void imprimeOperacao(String operacao, int resultado) {
		System.out.println("\nO resultado da " + operacao + " é: " + resultado);
	}
	
	// Método imprimeOperacao do tipo void com 
	// 1 parâmetro String e 1 parâmetro float
	public static void imprimeOperacao(String operacao, float resultado) {
		System.out.println("\nO resultado da " + operacao + " é: " + resultado);
	}

	// Método turma() do tipo void
	public static void turma() {
		System.out.println("\nCalculadora da Turma!!!!");
	}
	
}
```

> **Porquê utilizamos 0.0f em variáveis float?**
>
> O **'f'** indica que você está inserindo um numero do tipo **float**. Se você escrever um número decimal sem o sufixo **'f'**, o Java entenderá que é um número de precisão dupla (double). Exemplos:
>
> 0 é  int
> 0f é float
> 0.0 é double
> 0.0f é float 		

<br /><br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>	
