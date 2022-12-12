<h1>Tratamento de erros no Java - Exceptions</h1>

As informações passadas neste documento norteia os conceitos da Oracle e podemos encontrar através deste link:

<div align="left"><a href="https://docs.oracle.com/javase/8/docs/api/"><img src="https://i.imgur.com/DYnNz6q.png" title="source: imgur.com" width="10%"/>Oracle</a></div>

Componentes de software podem ter problemas durante a execução e gerar erros como:

- Terminar o programa;
- Retornar uma mensagem de erro indicando uma falha;
- Retornar e ignorar o problema;
- Chamar um método para tratar o erro, entre outras.

Os problemas mais comumente encontrados são:

- Falha na aquisição de um recurso (new, open...);
- Tentativa de fazer algo impossível (divisão por zero, índice de um array inválido...);
- Outras condições inválidas (lista vazia, overflow...).

Para contornar estes empecilhos, utilizamos o recurso chamado **Exceções (Exceptions)**.

<h2>1. Exceptions</h2>

As Exceções (Exceptions) são uma indicação de um problema que ocorre durante a execução de um programa. Em Java é possível tratar as exceções que poderiam ocorrer para que o programa continue ou termine de forma elegante. As Exceções são Objetos criados a partir de classes especiais, que são “disparados” quando ocorrem condições excepcionais. 

<h3>1.2 Tipos de erros</h2>

Os erros que acontecem nas aplicações Java estão classificados em 3 categorias:

1. **Erros de lógica:** Esta categoria abrange erros na construção do Algoritmo. Este tipo de erro devem ser corrigidos pelo programador

- **Exemplos:** Limites do vetor ultrapassados, divisão por zero, entre outros;

2. **Erros devido a condições do ambiente de execução:** Esta categoria abrange erros na infraestrutura onde a aplicação está sendo executada. Este tipo de erro foge do controle do programador, mas podem ser contornados em tempo de execução;

- **Exemplos:** arquivo não encontrado, rede fora do ar, entre outros;

3. **Erros graves:** São erros que simplesmente travam o sistema e não há nada o que fazer. Este tipo de erro foge do controle do programador e não podem ser contornados;

- **Exemplo:** falta de memória, erro interno do Java, entre outros.

Veja o exemplo abaixo:

```java
package com.generation.exc_divisao;

import java.util.Scanner;

public class Divisao {

	static Scanner ler = new Scanner(System.in);
	
	public static void main(String[] args) {
		
		int dividendo = 0;
		int divisor = 0;
			
		System.out.println("Digite o Dividendo: ");
		dividendo = ler.nextInt();
				
		System.out.println("Digite o Divisor: ");
		divisor = ler.nextInt();
				
		divide(dividendo, divisor);

	}

	public static void divide(int dividendo, int divisor) {
		System.out.println("Divisão = " + (dividendo / divisor));
	}

}
```

Experimente fazer uma divisão por zero. Você verá o resultado abaixo no seu console:

<div align="center"><img src="https://i.imgur.com/aTXz9R1.png" title="source: imgur.com" /></div>

Experimente inserir uma String ao invés de um numero no divisor. Você verá o resultado abaixo no seu console:

<div align="center"><img src="https://i.imgur.com/IT55yyi.png" title="source: imgur.com" /></div>

Observe que nos 2 exemplos o Java retornou **mensagens de erro diferentes**. 

Quando uma exceção é lançada, ela interrompe o **fluxo normal** do programa, ou seja, o fluxo do programa **segue** a exceção. Se o método onde ela ocorrer não a capturar a exceção ela será **propagada** para o método que chamar esse método e assim por diante. Se **ninguém** capturar a exceção, ela causará o término da aplicação. Agora se em algum lugar ela for capturada, **o controle pode ser recuperado**.

Um bom **Sistema de Tratamento de Exceções** procura sempre: 

- Se antecipar aos problemas (uma das tarefas da pessoa desenvolvedora);
- Reverter situações de erro que podem ser revertidas;
- Buscar a **Solução ideal** para o tratamento de problemas separado do código principal.

Com o tratamento de exceções, o programa captura e trata, isto é, lida com a exceção. Para capturar e lidar com as exceções utilizaremos a estrutura **Try -Catch**.

<h3>1.3. Estrutura try-catch</h3>

A estrutura de como tratar um erro ou exceção é composta por 3 estruturas básicas:

- **try:** é usada para indicar um bloco de código que possa lançar (throw) uma exceção.
- **catch:** serve para manipular as exceções, ou seja, tratar o erro.
- **finally:** sempre será executado depois do bloco try/catch.

Na imagem abaixo, vemos a sintaxe da estrutura try-catch dentro do código Java:

<div align="center"><img src="https://i.imgur.com/Uwvqs3q.png" title="source: imgur.com" /></div>

O **Bloco try** contém o código que pode lançar (throw) uma exceção. Ele consiste na palavra – chave try seguida por um bloco de código entre chaves.

O **Bloco Catch** captura e trata uma exceção. Ele começa com a palavra-chave catch. Dentro dos parênteses deve ser inserido o parâmetro de exceção, que identifica o tipo da exceção. O bloco de código entre as chaves será executado quando uma exceção do tipo adequado ao parâmetro ocorre.

O **Bloco Finally** é opcional em uma instrução try. Se estiver presente, ele será colocado depois do último bloco Catch. Ele será executado somente se uma exceção for lançada no bloco try correspondente ou qualquer um dos seus blocos catch correspondentes. Em geral, ele contém código de liberação de recursos do sistema.

Na imagem abaixo, vemos a sintaxe da estrutura try-catch-finally dentro do código Java:

<div align="center"><img src="https://i.imgur.com/hORZemU.png" title="source: imgur.com" /></div>

<h2>2. Implementando a captura de exceções na Classe Divisao</h2>

Veja a implementação abaixo:

```java
package com.generation.exc_divisao;

import java.util.InputMismatchException;
import java.util.Scanner;

public class Divisao {

	static Scanner ler = new Scanner(System.in);
	
	public static void main(String[] args) {
		
		int dividendo = 0;
		int divisor = 0;
		boolean loop = true;
		
		do {
			
			try {
				System.out.println("Digite o Dividendo: ");
				dividendo = ler.nextInt();
						
				System.out.println("Digite o Divisor: ");
				divisor = ler.nextInt();
						
				divide(dividendo, divisor);
				
				loop = false;
				
			}catch(InputMismatchException e){
				System.err.println("\nExceção: " + e);
				ler.nextLine();
				System.out.println("\nDigite valores inteiros!");
			}catch(ArithmeticException e){
				System.err.println("\nExceção: " + e);
				ler.nextLine();
				System.out.println("\nDigite Numeros inteiros positivos!");
			}finally{
                System.out.println("\nSempre serei executada!");
            }
		
		}while (loop);
	}

	public static void divide(int dividendo, int divisor) {
		System.out.println("Divisão = " + (dividendo / divisor));
	}

}
```

A variável e recebe o tipo de exceção que aconteceu. A sua exibição na tela é opcional. Na sequência é exibida uma mensagem de alerta e o programa é reiniciado, como podemos ver na imagem abaixo, indicado pelas setas coloridas:

<div align="center"><img src="https://i.imgur.com/l0YECYu.png" title="source: imgur.com" /></div>

<br />

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/tutorial/essential/exceptions/handling.html" target="_blank"><b>Documentação: Try..Catch..Finally</b></a>

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/7/docs/api/java/util/InputMismatchException.html" target="_blank"><b>Documentação: Classe InputMismatchException</b></a>

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/7/docs/api/java/lang/ArithmeticException.html" target="_blank"><b>Documentação: Classe ArithmeticException</b></a>

<br />

<h2>3. Throws e Throw</h2>

A **cláusula throws** especifica as **exceções que um método pode lançar**. Ele é inserida na assinatura do Método, depois da lista de parâmetros do método e antes do corpo do método. A cláusula throws contém uma lista separada por vírgulas das exceções. As exceções podem ser lançadas pelas instruções no corpo do método ou pelos métodos chamados. Veja o exemplo abaixo:

```java
	public static void divide(int dividendo, int divisor) throws ArithmeticException {
		System.out.println("Divisão = " + (dividendo / divisor));
	}
```

A **cláusula throw lança uma exceção em qualquer ponto do código**, mas não exige que ela seja tratada por seus chamadores. Ela transfere o  controle do fluxo para os métodos chamadores. Ela usa o que se chama  **unckecked exception**, ou seja, uma exceção é lançada mas nada obriga ela  ser tratada. Veja o exemplo abaixo:

1. Vamos criar um novo projeto. 
1. Dentro do Projeto, vamos criar uma Classe chamada **ExcecaoSimples**, contendo uma Exception personalizada:

```java
package array_exception.exception;

public class ExcecaoSimples extends Exception {

	private static final long serialVersionUID = 1L;
	
	public ExcecaoSimples () {}
    
	public ExcecaoSimples (String mensagem) {
		super(mensagem);
	}
}
```

Observe que foi definido na **Classe ExcecaoSimples** o Atributo ` private static final long serialVersionUID = 1L `. Este Atributo  é um identificador usado para serializar e desserializar um Objeto de uma Classe Serializable. **Simplificando, usamos o atributo serialVersionUID para lembrar as versões de uma classe Serializable para verificar se uma classe carregada e o objeto serializado são compatíveis.** Na prática, esse número seria a versão da sua classe. 

> **Serialização**
>
> É o processo onde o Java pega o valor de  cada atributo e gera uma sequência de bytes. Junto com essa sequência de bytes é acrescentado o `serialVersionUID`, que é um código de identificação da versão da Classe.
>
> **Desserialização** 
>
> É o processo inverso, ou seja, o Java pega uma sequência  de bytes e coloca nos atributos de um novo objeto. Antes de fazer isso,  ele verifica se o `serialVersionUID` salvo é igual ao do serial do novo objeto que está sendo criado. Esse número é utilizado para garantir que uma classe  carregada corresponde exatamente a um objeto serializado. Se nenhuma  correspondência do objeto for encontrada, então é lançada uma **InvalidClassException**.
>
> Em tese, isso permite você salvar uma "fotografia" de um Objeto, por  exemplo, num arquivo em disco e depois restaurar o objeto com os mesmos  valores posteriormente.
>
> **Por que o Eclipse emite um aviso?**
>
> Para um objeto ser serializado ele precisa ser marcado com a interface `java.io.Serializable`. Se o Eclipse (ou alguma outra ferramenta que analisa o código), encontrar uma Classe que implementa `Serializable` direta ou indiretamente, ele entende que é uma boa prática especificar um `serialVersionUID`.
>
> Isso pode ocorrer se a classe:
>
> - Implementa `Serializable`;
> - Implementa uma interface que estende `Serializable`;
> - Estende uma classe que implementa `Serializable`.
>
> No exemplo acima, a **Classe Exception** estende a **Classe Throwable**, que implementa a **Classe Serializable**. Por isso que o Eclipse exige a inserção deste Atributo na Classe.

Na sequência, foram criados 2 Métodos Construtores, herdados da Classe Exception, onde o primeiro é um Construtor vazio e o segundo é um Construtor com o parâmetro **mensagem**, que permite personalizar a mensagem de erro. A Classe Exception possui outros Métodos Construtores com outros parâmetros.

<br />

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/7/docs/api/java/lang/Throwable.html" target="_blank"><b>Documentação: Classe Throwable</b></a>

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/7/docs/api/java/lang/Exception.html" target="_blank"><b>Documentação: Classe Exception</b></a>

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/7/docs/api/java/io/Serializable.html" target="_blank"><b>Documentação: Interface Serializable</b></a>

<br />
<br />

3. Insira a **Classe TestaArray**, como mostra o código abaixo:

```java
package array_exception;

import array_exception.exception.ExcecaoSimples;

public class TestaArray {

	public static void main(String[] args) throws ExcecaoSimples{
		
		String nomes [] = {"João", "Maria", "Pedro", "Manuela"};
		
		try {
			for (int i=0;i<nomes.length;i++) {
				System.out.println(nomes[i]);
			}
		}catch (ArrayIndexOutOfBoundsException e) {
			System.err.println("\nExceção: " + e);
			System.out.println("\nPosição Inválida");
		}
		
		throw new ExcecaoSimples("Exceção Simples!");
	
	}
	
}
```

Observe que o final do código, na linha **throw new ExcecaoSimples("Exceção Simples!")**, estamos lançando a exceção criada na **Classe ExcecaoSimples**, independente ter acontecido um erro. Veja o resultado no console abaixo:

<div align="center"><img src="https://i.imgur.com/dZ2rsnQ.png" title="source: imgur.com" /></div>

<br />

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/tutorial/essential/exceptions/declaring.html" target="_blank"><b>Documentação: Throws</b></a>

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/tutorial/essential/exceptions/throwing.html" target="_blank"><b>Documentação: Throw</b></a>

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/7/docs/api/java/lang/ArrayIndexOutOfBoundsException.html" target="_blank"><b>Documentação: Classe ArrayIndexOutOfBoundsException</b></a>

<br />

<h2>4. Hierarquia das Exceptions</h2>

<div align="center"><img src="https://www.oracle.com/technetwork/es/images/img1-5928057.png" title="source: imgur.com" /></div>

- **Throwable:** É a mãe de todas as exceções.
- **Error:** Não são exceções, e sim erros que jamais poderiam ter acontecido, como estouro da memória, por exemplo.
- **Exception:** São as classes que deveriam aqui, lançar exceções e não erros de programação. Exemplo: tentar abrir um arquivo que não existe. Então, é lançada uma exceção verificada, porque a classe de leitura de arquivos deriva de Exception.
- **RuntimeException**: São exceções que indicam erros de programas (não de lógica, pois senão não passaria pelo compilador). Esse tipo de exceção é conhecida como não verificada. 

<br />

## 🔑**Pontos chave:**

1. **Exceções** em Java são classes especiais utilizadas para manipular erros que podem surgir durante a execução.
2. *O* **bloco try/catch/finally** permite capturar exceções que podem ocorrer quando uma parcela de código ou função é executada.
3. A **cláusula throws** especifica as **exceções que um método pode lançar**. Ele é inserida na assinatura do Método, depois da lista de parâmetros do método e antes do corpo do método. A cláusula throws contém uma lista separada por vírgulas das exceções. As exceções podem ser lançadas pelas instruções no corpo do método ou pelos métodos chamados. 
4. A **cláusula throw lança uma exceção em qualquer ponto do código**, mas não exige que ela seja tratada por seus chamadores. Ela transfere o  controle do fluxo para os métodos chamadores. Ela usa o que se chama  **unckecked exception**, ou seja, uma exceção é lançada mas nada obriga ela  ser tratada.
5. Você também pode criar e lançar exceções personalizadas.

<br />

------

<h1>Projeto Conta Bancária</h1>

Nesta etapa, vamos implementar o **Método keyPress()** na Classe Menu. Este Método tem por Objetivo exigir que a tecla enter seja pressionada para finalizar uma opção do Menu. No estágio atual, quando você seleciona uma opção do Menu, ele mostra a mensagem e recarrega o Menu novamente. Com o Método keyPress(), o Menu será recarregado somente depois de pressionar a tecla enter.

1. Abra a Classe Menu;
2. Adicione o Método **keyPress()**;
3. Adicione chamadas para o Método keyPress() em todas as opções do Switch Case do Menu;
4. O código completo da Classe Menu, você confere abaixo:

```java
package conta;

import java.io.IOException;
import java.util.InputMismatchException;
import java.util.Scanner;

import contabancaria.model.ContaCorrente;
import contabancaria.model.ContaPoupanca;
import contabancaria.util.Cores;

public class Menu {

	public static Scanner leia = new Scanner(System.in);

	public static void main(String[] args) {

		int opcao = 0;

		// Teste da Classe Conta Corrente
		ContaCorrente cc1 = new ContaCorrente(1, 123, 1, "Adriana", 10000.0f, 1000.0f);
		cc1.visualizar();
		cc1.sacar(12000.0f);
		cc1.visualizar();
		cc1.depositar(5000.0f);
		cc1.visualizar();

		// Teste da Classe Conta Poupança
		ContaPoupanca cp1 = new ContaPoupanca(2, 123, 2, "Victor", 100000.0f, 15);
		cp1.visualizar();
		cp1.sacar(1000.0f);
		cp1.visualizar();
		cp1.depositar(5000.0f);
		cp1.visualizar();

		while (true) {

			System.out.println(Cores.TEXT_YELLOW + Cores.ANSI_BLACK_BACKGROUND
					+ "*****************************************************");
			System.out.println("                                                     ");
			System.out.println("                BANCO DO BRAZIL COM Z                ");
			System.out.println("                                                     ");
			System.out.println("*****************************************************");
			System.out.println("                                                     ");
			System.out.println("            1 - Criar Conta                          ");
			System.out.println("            2 - Listar todas as Contas               ");
			System.out.println("            3 - Buscar Conta por Numero              ");
			System.out.println("            4 - Atualizar Dados da Conta             ");
			System.out.println("            5 - Apagar Conta                         ");
			System.out.println("            6 - Sacar                                ");
			System.out.println("            7 - Depositar                            ");
			System.out.println("            8 - Transferir valores entre Contas      ");
			System.out.println("            9 - Sair                                 ");
			System.out.println("                                                     ");
			System.out.println("*****************************************************");
			System.out.println("Entre com a opção desejada:                          ");
			System.out.println("                                                     " + Cores.TEXT_RESET);
			
			try {
				opcao = leia.nextInt();
			}catch(InputMismatchException e){
				System.out.println("\nDigite valores inteiros!");
				leia.nextLine();
			}finally {
				opcao=0;
			}

			if (opcao == 9) {
				System.out.println("\nBanco do Brazil com Z - O seu futuro começa aqui!");
				leia.close();
				System.exit(0);
			}

			switch (opcao) {
			case 1:
				System.out.println("\n Criar Conta");

				keyPress();
				break;
			case 2:
				System.out.println("\n Listar todas as Contas");

				keyPress();
				break;
			case 3:
				System.out.println("\n Buscar Conta por número");

				keyPress();
				break;
			case 4:
				System.out.println("\n Atualizar dados da Conta");

				keyPress();
				break;
			case 5:
				System.out.println("\n Apagar Conta");

				keyPress();
				break;
			case 6:
				System.out.println("\n Sacar");

				keyPress();
				break;
			case 7:
				System.out.println("\n Depositar");

				keyPress();
				break;
			case 8:
				System.out.println("\n Transferir");

				keyPress();
				break;
			default:
				System.out.println("\nOpção Inválida" + Cores.TEXT_RESET);
				
				keyPress();
				break;
			}
		}
	}

	public static void keyPress() {

		try {

			System.out.println(Cores.TEXT_RESET + "\n\nPressione Enter para Continuar...");
			System.in.read();

		} catch (IOException e) {

			System.out.println("Você pressionou uma tecla diferente de enter!");

		}
	}
}
```

Observe que a estrutura **Try...Catch** foi implementada na entrada de dados via teclado da variável **opcao** (recebe o numero do item do menu) e no Método **keyPress()** para capturar eventuais erros.

O método **System.in.read()** indica a leitura de um dispositivo de entrada padrão (teclado), lendo as teclas que foram processadas. Quando for digitada tecla <Enter>, os dados do buffer nativo são transferidos para a JVM e o primeiro byte digitado é retornado ao  usuário e retirado do buffer. Porém se o buffer nativo estiver vazio, o  método retorna -1. No caso do Método **keyPress()**, ao pressionar a tecla <Enter>, automaticamente o Menu é reiniciado.

> **Buffer** de dados é uma região de memória física utilizada para armazenar temporariamente os dados enquanto eles estão sendo movidos de  um lugar para outro. Ao pressionar a tecla <Enter>, os dados são enviados para a JVM.

<br /><br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>
