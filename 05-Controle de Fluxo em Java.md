# **Controle de Fluxo em Java**



## Instruções de controle de fluxo Java

Na linguagem Java existem várias palavras-chave que são usadas para alterar o fluxo do programa. As instruções podem ser executadas várias vezes ou apenas sob uma condição específica. As instruções `if`, `else`e `switch` são usadas para testar condições, as instruções `while`and `for`para criar ciclos e as instruções `break`and `continue`para alterar um loop.

Quando o programa é executado, as instruções são executadas de cima para baixo no arquivo de origem. Um por um.

## Java - declaração if

A declaração `if` tem a seguinte forma geral:

```java
if (expressão) {

    declaração;
}
```

A palavra chave `if` é usada para verificar se uma expressão é verdadeira. Se for verdade, uma instrução é executada. A instrução pode ser uma instrução simples ou uma instrução composta. Uma instrução composta consiste em várias instruções delimitadas por um bloco. Um bloco é um código entre colchetes. Os colchetes são opcionais se tivermos apenas uma instrução no corpo.

```java
package com.generation;

import java.util.Random;

public class IfStatement {

    public static void main(String[] args) {

        Aleatório r = new Aleatório();
        int num = r.nextInt();

        if (num > 0) {

            System.out.println("O número é positivo");
        }
    }
}
```

Um número aleatório é gerado. Se o número for maior que zero, imprimimos uma mensagem no terminal.

```java
Aleatório r = new Aleatório();
int num = r.nextInt();
```

Essas duas linhas geram um inteiro aleatório. O número pode ser positivo ou negativo.

```java
if (num > 0) {

    System.out.println("O número é positivo");
}
```

Usando a palavra-chave `if`, verificamos se o número gerado é maior que zero. A palavra-chave `if` é seguida por um par de colchetes. Dentro dos colchetes, colocamos uma expressão. A expressão resulta em um valor booleano. Se o valor booleano for true, o bloco entre duas chaves será executado. No nosso caso, a string "O número é positivo" é impressa no terminal. Se o valor aleatório for negativo, nada é feito. As chaves são opcionais se tivermos apenas uma expressão.

## Palavra-chave Java else

Podemos usar a palavra-chave `else` para criar uma ramificação simples. Se a expressão dentro dos colchetes após a palavra-chave `if`  for avaliada como false, a instrução após a palavra-chave `else`  será executada automaticamente.



```java
package com.generation;

import java.util.Random;

public class Filial {

    public static void main(String[] args) {

        Aleatório r = new Aleatório();
        int num = r.nextInt();

        if (num > 0) {

            System.out.println("O número é positivo");

        } else {

            System.out.println("O número é negativo");
        }
    }
}
```

Ou o bloco que segue a palavra-chave `if` ou o bloco que segue a palavra-chave `else` é executado.

```java
if (num > 0) {

    System.out.println("O número é positivo");

} else {

    System.out.println("O número é negativo");
}
```

A palavra-chave `else` segue a chave direita do bloco `if`. Ele tem seu próprio bloco delimitado por um par de colchetes.

```java

O número é positivo

O número é negativo

O número é negativo
```

Executamos o exemplo três vezes. Esta é uma saída de amostra.

## Várias ramificações com if else

Podemos criar várias ramificações usando a palavra-chave `else if`. A palavra-chave `else if` testa outra condição se e somente se a condição anterior não for atendida. Observe que podemos usar várias palavras-chave `else if` em nossos testes.

O programa anterior tinha um pequeno problema. Zero foi dado para valores negativos. O programa a seguir irá corrigir isso.



```java
package com.generation;

import java.util.Scanner;

public class MultipleBranches {

    public static void main(String[] args) {

        System.out.print("Digite um inteiro:");

        Scanner sc = new Scanner(System.in);
        int num = sc.nextInt();

        if (num < 0) {

            System.out.println("O inteiro é negativo");
        } else if (num == 0) {

            System.out.println("O inteiro é igual a zero");
        } else {

            System.out.println("O inteiro é positivo");
        }
    }
}
```

Recebemos um valor do usuário testá-lo se for um número negativo ou positivo, ou se for igual a zero.

```java
System.out.print("Digite um inteiro:");
```

Um prompt para inserir um número inteiro é gravado na saída padrão.

```java
Scanner sc = new Scanner(System.in);
int num = sc.nextInt();
```

Usando a `Scanner`classe do pacote `java.util`, lemos um valor inteiro da entrada padrão.

```java
if (num < 0) {

    System.out.println("O inteiro é negativo");
} else if (num == 0) {

    System.out.println("O inteiro é igual a zero");
} else {

    System.out.println("O inteiro é positivo");
}
```

Se a primeira condição for verdadeira, por exemplo, o valor inserido for menor que zero, o primeiro bloco será executado e os dois blocos restantes serão ignorados. Se a primeira condição não for atendida, a segunda condição após as palavras-chave  `if else`  será verificada. Se a segunda condição for verdadeira, o segundo bloco será executado. Caso contrário, o terceiro bloco após a palavra-chave `else` é executado. O bloco `else`é sempre executado se as condições anteriores não forem atendidas.

```java

Digite um número inteiro:4
O inteiro é positivo

Digite um número inteiro:0
O inteiro é igual a zero

Digite um número inteiro:-3
O inteiro é negativo
```

Executamos o exemplo três vezes para que todas as condições sejam testadas. O zero é tratado corretamente.

## Instrução de switch Java

A instrução `switch`é uma instrução de fluxo de controle de seleção. Ele permite que o valor de uma variável ou expressão controle o fluxo de execução de um programa por meio de uma ramificação multidirecional. Ele cria várias ramificações de maneira mais simples do que usar a combinação de instruções `if`e `else if` . Cada ramo é finalizado com a palavra-chave `break`.

Usamos uma variável ou uma expressão. A palavra-chave `switch` é usada para testar um valor da variável ou a expressão em uma lista de valores. A lista de valores é apresentada com a palavra-chave `case`. Se os valores corresponderem, a instrução após o `case`será executada. Há uma `default`declaração opcional. Ele é executado se nenhuma outra correspondência for encontrada.



```java
package com.generation;

import java.util.Scanner;

public class SwitchStatement {

    public static void main(String[] args) {

        System.out.print("Digite um domínio:");

        Scanner sc = new Scanner(System.in);
        String dominio = sc.nextLine();

        domínio = dominio.trim().toLowerCase();

        switch (dominio) {

            case "us":
                System.out.println("Estados Unidos");
                break;

            case "de":
                System.out.println("Alemanha");
                break;

            case "sk":
                System.out.println("Eslováquia");
                break;

            case "hu":
                System.out.println("Hungria");
                break;

            default:
                System.out.println("Desconhecido");
                
        }
    }
}
```

O usuário é solicitado a inserir um nome de domínio. O nome de domínio é lido e armazenado em uma variável. A variável é testada com a palavra-chave `switch`  em uma lista de opções. Em nosso programa, temos uma variável de domínio. Lemos um valor para a variável na linha de comando. Usamos a `case`instrução para testar o valor da variável. Existem várias opções. Se o valor for igual, por exemplo, a "us", a string "United States" será impressa no console.

```java
Scanner sc = new Scanner(System.in);
String domínio = sc.nextLine();
```

A entrada do usuário é lida no console.

```java
dominio = dominio.trim().toLowerCase();
```

O `trim`método remove a variável de possíveis espaços em branco à esquerda e à direita. O `toLowerCase`converte os caracteres para minúsculas. Agora, "us", "US" ou "us" são opções viáveis para o nome de domínio us.

```java
switch (dominio) {
    ...
}
```

Nos colchetes, a `switch`palavra-chave recebe uma entrada que será testada. A entrada pode ser do tipo `byte`, `short`, `char`, `int`, `enum`, ou `String` dados. O corpo da palavra-chave `switch` é colocado dentro de um par ou colchetes. Dentro do corpo, podemos colocar várias opções `case` . Cada opção é finalizada com a palavra-chave `break`.

```java
case "us":
    System.out.println("Estados Unidos");
    break;
```

Nesta opção de caso, testamos se a variável de domínio é igual à string "us". Se true, imprimimos uma mensagem no console. A opção é finalizada com a palavra-chave `break`. Se uma das opções for avaliada com sucesso, a palavra-chave `break` finaliza o `switch`bloco.

```java
default:
    System.out.println("Desconhecido");
   
```

A palavra-chave `default` é opcional. Se nenhuma das `case` opções for avaliada, a seção `default` será executada.

```java

Digite um domínio: us
Estados Unidos
```

Esta é uma saída de amostra.

## Expressão de troca de Java

A expressão switch Java simplifica a instrução switch original. Foi introduzido no Java 12 e aprimorado no Java 13.

Expressões de switch Java suportam o uso de vários rótulos de maiúsculas e minúsculas. Eles podem retornar valores via palavra-chave `yield`.



```java
package com.generation;

import java.util.Scanner;

public class SwitchExpression {

    public static void main(String[] args) {
        System.out.print("Digite um domínio:");

        Scanner sc = new Scanner(System.in);
        String dominio = sc.nextLine();

        dominio = dominio.trim().toLowerCase();

        switch (dominio) {

            case "us" -> System.out.println("Estados Unidos");
            case "de" -> System.out.println("Alemanha");
            case "sk" -> System.out.println("Eslováquia");
            case "hu" -> System.out.println("Hungria");
            default -> System.out.println("Desconhecido");
        }
    }
}
```

O exemplo de instrução switch anterior foi reescrito usando a expressão switch.

------



# **Projeto Java**

Sempre é muito importante entender os vários recursos que o Java nos disponibiliza para fazermos determinadas funções dentro da sua programação em situações reais.

Pensando exatamente nesses situações de implementação real que teremos, o nosso projeto nos traz uma situação bem interessante onde no seu menu teremos que escolher, por exemplo, qual o tipo de conta que queremos visualizar. Em uma situação como poderemos implementar o bloco de decisão switch()...case da seguinte forme:

```java
public void visualizar() {

String tipo = "";

	switch(this.tipo) {

		case 1:

			tipo = "Conta Corrente";

		break;

		case 2:

			tipo = "Conta Poupança";

		break;

}
```

E neste exemplo percebemos exatamente o quanto é importante a implementação de um laço switch()...case dentro do método visualizar. Através do seu tipo nós conseguimos saber se o cliente deseja fazer a visualização da "Conta Corrente" ou da "Conta Poupança".

