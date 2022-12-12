# **Laços de repetição em Java**



### Necessidade de loops em Java

Durante a programação, às vezes, ocorre uma situação em que precisamos executar um bloco de código várias vezes. Em geral, essas instruções são executadas de maneira sequencial: a primeira instrução em uma função é executada primeiro, seguida pela segunda e assim por diante.

Mas isso torna o processo muito complicado, além de demorado e, portanto, demorado. Portanto, as linguagens de programação fornecem várias estruturas de controle que permitem instruções de execução tão complexas.

Antes de avançar para os tipos de loops, discutiremos primeiro a sintaxe geral de um loop com a ajuda de elementos que controlam um loop.

### Loops Java

Em Java, existem três tipos de loops: o loop **for** , o loop **while** e o loop **do-** **while**. Todas essas três construções de loop de Java executam um conjunto de instruções repetidas enquanto uma condição especificada permanecer verdadeira.

Essa condição específica é geralmente conhecida como controle de loop. Para todas as três instruções de loop, uma condição verdadeira é aquela que retorna um valor booleano verdadeiro e a condição falsa é aquela que retorna o valor booleano falso.

### Elementos em um loop Java

Cada loop tem seus elementos ou ***variáveis*** que governam sua execução. Geralmente, um loop tem quatro elementos que têm propósitos diferentes, que são:

- Expressão(ões) de Inicialização
- Expressão de teste (condição)
- Atualizar expressão(ões)
- Corpo do laço

Vamos discutir cada um dos elementos acima para uma melhor compreensão do funcionamento dos loops.

#### 1. Expressão(ões) de Inicialização

Antes de entrar em um loop, devemos inicializar sua variável de controle. A inicialização da variável de controle ocorre sob a expressão de inicialização. Ele inicializa as variáveis de loop com seu primeiro valor. A expressão de inicialização é executada apenas uma vez no início do loop.

#### 2. Expressão de Teste

A expressão de teste é uma expressão cujo valor de verdade (booleano) decide se o corpo do loop será executado ou não. A execução ou término do loop depende da expressão de teste que também é chamada de condição de saída ou condição de teste.

Se a expressão de teste for avaliada como verdadeira, ou seja, 1, o corpo do loop será executado, caso contrário, o loop será encerrado.

Em um **loop controlado por entrada** , a expressão de teste é avaliada antes de entrar em um loop, enquanto que, no **loop controlado por saída** , a expressão de teste é avaliada antes de sair do loop. Em Java, o loop **for e** **while** são loops controlados por entrada, e o loop **do-** while é um loop **controlado por saída** .

#### 3. Atualizar expressão(ões)

A(s) expressão(ões) de atualização altera os valores das variáveis de loop. A expressão de atualização é executada no final do loop após a execução do corpo do loop. Por exemplo, uma expressão de atualização pode ser instruções de incremento ou decremento.

#### 4. O Corpo do Loop

As instruções que são executadas repetidamente (desde que a expressão de teste seja diferente de zero) formam o corpo do loop. O código dentro do corpo do loop será executado ou não, depende do valor da expressão de teste.

Se o valor for avaliado como verdadeiro, o corpo do loop será executado repetidamente, caso contrário, será encerrado.

O diagrama a seguir explica uma iteração ou uma construção de loop:

<a href="https://imgur.com/8SuL451"><img src="https://i.imgur.com/8SuL451.png" title="source: imgur.com" /></a>

## Tipos de loops em Java

## **Loop For**

O loop **for** em Java é um loop controlado por entrada que permite ao usuário executar um bloco de uma(s) instrução(ões) repetidamente com um número fixo de vezes com base na expressão de teste ou condição de teste. Este é o mais fácil de entender os loops Java.

Todos os seus elementos de controle de loop são reunidos em um lugar, no topo do loop dentro dos colchetes(), enquanto nas outras construções de loop de Java, os elementos de loop estão espalhados pelo programa.

**A sintaxe ou forma geral do loop for é:**



```java
for ( expressão de inicialização ( s ) ; expressão de teste ; expressão de atualização ( s )) 

{

  corpo do laço ;

}
```

**Por exemplo:**

```java
int x = 0 ;

for ( x = 1 ; x < = 10 ; x++ )  

{

  System.out.println ("Valor de x: "+x ) ;

}
```

**Trecho de código para ilustrar o uso de instrução/loop:**

```java
package com.generation;

public class ForLoopDemo

{

  public static void main ( String args []) 

  {

    int;

    for ( i = 10 ; i > = 1 ; i-- )

    {

      System.out.println ( "O valor de i é: " +i ) ;

    }

  }

}
```

**Resultado:**

```java
O valor de i é: 10
O valor de i é: 9
O valor de i é: 8
O valor de i é: 7
O valor de i é: 6
O valor de i é: 5
O valor de i é: 4
O valor de i é: 3
O valor de i é: 2
O valor de i é: 1
```

*A figura a seguir descreve o funcionamento de um loop for:*

 

<a href="https://imgur.com/ZKzccT1"><img src="https://i.imgur.com/ZKzccT1.png" title="source: imgur.com" style="zoom:150%;" /></a>

Agora que você está familiarizado com o funcionamento de um loop for, vamos dar outro exemplo onde existem ***várias instruções no corpo do loop:***

**Código:**

```java
package com. generation.loopsDemo ;

public class ForLoopDemo

{

  public static **void** main ( String args []) 

  {

    int, soma;

    for ( i = 1 , soma = 0 ; i < = 10 ; ++i )

    {

      System.out.println ( "O valor de i é: " +i ) ; 

      soma = soma + i;

    }

    System.out.println ( "A soma dos 10 primeiros números é: " +sum ) ; 

  }

}
```

**Resultado:**

```java
O valor de i é: 1
O valor de i é: 2
O valor de i é: 3
O valor de i é: 4
O valor de i é: 5
O valor de i é: 6
O valor de i é: 7
O valor de i é: 8
O valor de i é: 9
O valor de i é: 10
A soma dos 10 primeiros números é: 55
```

No programa acima, existem 2 expressões de inicialização: i = 1 e sum = 0 separadas por vírgula. A parte de inicialização pode conter tantas expressões, mas elas devem ser separadas por vírgulas. A parte de inicialização deve ser seguida por um ponto e vírgula(;). Ambas as variáveis **i** e **soma** obtêm seus primeiros valores 1 e 0, respectivamente.

**Dica:** Use o loop for quando precisar repetir um bloco de instruções um número específico de vezes.

##### As variações do loop for

Java oferece diversas variações no loop que aumentam a flexibilidade e aplicabilidade do loop **for .** As diferentes variações do loop for são discutidas abaixo:

**Várias inicializações e expressões de atualização**

Um loop for pode conter várias inicializações e/ou expressões de atualização. Essas várias expressões devem ser separadas por vírgulas. Já vimos um exemplo de várias expressões de inicialização no programa anterior.

O loop for desse programa pode ser escrito alternativamente da seguinte forma:

```java
for ( i = 1 , soma = 0 ; i < = 10 ; soma +=i, ++i )  

System.out.println ( i ) ;
```

O código acima contém duas expressões de inicialização **i = 1 e sum = 0** e duas expressões de atualização **sum += i** e **++i** . Essas várias expressões são executadas em sequência.

**Dica:** O operador vírgula em um loop for é essencial sempre que precisarmos de mais de um índice.

**Expressões Opcionais**

Em um loop for, expressões de inicialização, expressões de teste e expressões de atualização são opcionais, ou seja, você pode pular qualquer uma ou todas essas expressões.

Digamos, por exemplo, que você já inicializou as variáveis de loop e deseja raspar a expressão de inicialização, então você pode escrever for loop da seguinte forma:

```java
for( ; expressão-teste ; expressão(ões) de atualização)
corpo do loop
```

Veja, mesmo se você pular a expressão de inicialização, o ponto e vírgula (;) deve estar seguindo.

O fragmento de código a seguir ilustra o conceito acima:

```java
package com.generation. loopsDemo ;

public class ForLoopDemo

{

  public static **void** main ( String args []) 

  {

    int i = 1 , soma = 0 ; 

    for ( ; i < = 10 ; soma +=i, ++i )  

      System.out.println ( i ) ;

    System.out.println ( "A soma dos 10 primeiros números é: " +sum ) ; 

  }

}
```

**Resultado:**

```java
1
2
3
4
5
6
7
8
9
10
A soma dos 10 primeiros números é: 55
```

Da mesma forma, também podemos pular ou omitir as expressões de teste e expressões de atualização.

**Por exemplo,**

```java
for ( j = 0 ; j!= 224 ; )   

j+= 11 ;
```

Se a variável j já foi inicializada, então podemos escrever o laço acima como,

```java
for ( ; j != 224 ; )   

j+= 11 ;
```

**Dica:** As expressões de controle de loop em uma instrução de loop for são opcionais, mas o ponto e vírgula deve ser escrito.

**Loop infinito**

Um loop infinito pode ser criado pulando a expressão de teste como mostrado abaixo:

```java
package com.generation. loopsDemo ;

public class ForLoopDemo

{

  public static **void** main ( String args []) 

  {

    int x;

    for ( x = 25 ; ; x-- )  

      System.out.println ( " Este é um loop infinito" ) ;

  }

}
```

**Resultado:**

```java
Este é um loop infinito…
```

Da mesma forma, também podemos pular todas as três expressões para criar um loop infinito:

```java
for ( ; ; ; )    

corpo do laço
```

**Loop Vazio**

Quando não há nenhuma instrução no corpo do loop, ele é chamado de loop vazio. Nesses casos, um loop Java contém uma instrução vazia, ou seja, uma instrução nula. A seguir, o loop for é um exemplo de um loop vazio:

```java
for(j = 20 ; j >=0 ; j–- ); // Veja, o corpo do loop contém uma declaração nula
```

Um loop for vazio tem suas aplicações no loop de atraso de tempo onde você precisa aumentar ou diminuir o valor de alguma variável sem fazer mais nada, apenas para introduzir algum atraso.

**Declaração de variáveis dentro de loops**

Quando declaramos qualquer variável dentro do loop for, não podemos acessar a variável após o término da instrução do loop. A razão é que, à medida que a variável é declarada dentro de um bloco de instrução, seu escopo se torna o corpo do loop. Portanto, não podemos acessá-lo fora do corpo do loop.

O código a seguir explica esse conceito:

```java
package com.generation. loopsDemo ;

public class ForLoopDemo

{

  public static **void** main ( String args []) 

  {

    for ( int x = 25 ; x > = 0 ; x -= 5 ) 

    {

      System.out.println ( "Dentro do loop" ) ;

    }

    System.out.println ( x ) ; //Acessar x após o corpo do loop dá um erro

  }

}
```

**Resultado:**

Exceção no encadeamento “principal” java.lang.Error: Problema de compilação não resolvido:

```java
x não pode ser resolvido para uma variável
em project1/com.generation.loopsDemo.ForLoopDemo.main(ForLoopDemo.java:11)
```

*No programa acima, a instrução System.out.println(x); é inválido, pois o escopo de x acabou. Uma variável não está acessível fora de seu escopo, por isso há um erro.*



## **Loop While ()**

É uma instrução de fluxo de controle que permite que o código seja executado repetidamente com base em uma determinada condição booleana. O loop while pode ser considerado uma instrução if de repetição.

<a href="https://imgur.com/9wIYz5P"><img src="https://i.imgur.com/9wIYz5P.png" title="source: imgur.com" /></a>

**Sintaxe:**

```java
while (teste_expressão)
{
   // statements
 
  atualiza_expressão;
}
```

As várias **partes do loop While** são:

1. Expressão de teste:

    

   Nesta expressão, temos que testar a condição. Se a condição for avaliada como verdadeira, executaremos o corpo do loop e atualizaremos a expressão. Caso contrário, sairemos do loop while.

   Exemplo:

   ```java
   i <= 10
   ```

2. Expressão de atualização

    Após executar o corpo do loop, esta expressão aumenta / diminui a variável do loop em algum valor.

   Exemplo:

   ```java
   i ++;
   ```

**Como um loop While é executado?**

1. O controle cai no loop while.
2. O fluxo salta para a condição
3. A condição é testada.
   1. Se a Condição resultar verdadeira, o fluxo vai para o Corpo.
   2. Se a Condição resultar em falso, o fluxo sai do loop
4. As instruções dentro do corpo do loop são executadas.
5. A atualização ocorre.
6. O controle retorna à Etapa 2.
7. O loop do-while terminou e o fluxo saiu.

**Exemplo:** Este programa tentará imprimir “Hello World” 5 vezes.

```java
// Programa em java para demonstrar o funcionamento do laço while.
  
class whileLoopDemo {
    public static void main(String args[])
    {
        // inicializando a expressão
        int i = 1;
  
        // testando a expressão
        while (i < 6) {
            System.out.println("Hello World");
  
            // atualizando a expressão
            i++;
        }
    }
}
```

**Saída:**

```java
Olá Mundo
Olá Mundo
Olá Mundo
Olá Mundo
Olá Mundo
```

Este programa encontrará a soma dos números de 1 a 10.

```java
// Programa em java para demonstrar o funcionamento do laço while.
  
class whileLoopDemo {
    public static void main(String args[])
    {
        int x = 1, sum = 0;
  
        // Sair quando x se tornar maior que 4
        while (x <= 10) {
            // Processando x
            sum = sum + x;
  
            // Incremente o valor de x para a próxima iteração
            x++;
        }
        System.out.println("Somatório: " + sum);
    }
}
```

**Saída:**

```java
Soma: 55
```



## **O loop do-while**

Ao contrário dos loops for e while, o loop do-while é um loop controlado por saída, o que significa que um loop do-while avalia sua expressão de teste ou condição de teste na parte inferior do loop após executar as instruções no corpo do loop.

Isso significa que o loop do-while sempre é executado pelo menos uma vez !!

### **Necessidade de loop do-while:**

Nos loops **for** e **while** , a condição é avaliada antes de executar o corpo do loop. O corpo do loop nunca é executado se a expressão de teste for avaliada como false pela primeira vez.

Mas em algumas situações, queremos que o corpo do loop seja executado pelo menos uma vez, não importa qual seja o estado inicial da expressão de teste. Nesses casos, o loop **do- while é a melhor opção.**

**A sintaxe ou forma geral do loop do-while é:**

**

```java
do
{
    declaração ( ões ) ;
} while ( expressão de teste ) ;
```

 

As chaves **{}** não são necessárias quando o corpo do loop contém uma única instrução.

O código a seguir mostra o funcionamento de um loop do-while:

**Trecho de código para ilustrar o loop do-while:**

```java
//programa para imprimir todas as letras maiúsculas

package com.generation. loopsDemo ;

public class DoWhileLoopDemo

{

  public static **void** main ( String args []) 

  {

    char ch = 'A' ; 

    do

    {

      System.out.println ( ch+ " " ) ; 

      ch++;

    } while ( ch < = 'Z' ) ; 

  }

}
```

**Resultado:**

```java
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
```

O código acima imprime caracteres de 'A' em diante até que a condição ch<= 'Z' se torne falsa.



#### Loops aninhados em Java

Quando um loop contém outro loop em seu corpo, ele é chamado de loop aninhado. Mas em um loop aninhado, o loop interno deve terminar antes do loop externo. Veja a seguir um exemplo de loop for “aninhado”:

**Código para ilustrar o loop for aninhado:**

```java
package com.generation. loopsDemo ;

public class NestedLoopDemo

{

  public static void main ( String args []) 

  {

    int, j;

    for ( i = 1 ; i < = 5 ; ++i )  

    { //loop externo          

      System.out.println () ;

      for ( j = 1 ; j < = i ; ++j ) // loop interno   

      System.out.println ( " * " ) ;  

    }

  }

}
```

**Resultado:**

```java
*
* *
* * * *
* * * *
* * * *
```

------



# **Projeto Java**

Agora que verificamos a utilização dos três laços de repetição dentro da linguagem de programação Java, podemos implementar dentro do nosso projeto.

Então neste momento começamos a pensar nos clientes, nas contas e como que faremos para dar um loop e verificar todas essas informações. Neste momento é que entramos com os nossos laços de repetição.

Lembrando que os nossos laços podem ser criados juntos com outras estruturas do Java, como por exemplo, laços condicionais.

Segue uma implementação bem interessante dentro de um modelo real:

```java
do {
    System.out.println("Digite o Tipo da Conta (1-CC ou 2-CP): ");
    tipo = leia.nextInt();
}while(tipo < 1 && tipo > 2);
```

Neste caso estamos utilizando o laço de repetição do...while() para fazer a verificação do tipo de conta, neste caso ele só vai aceitar os valores 1 e 2, pois são os números dos tipos de contas.

Na condição do while, ele indica que esse número enquanto estiver < que 1 e > que 2 ele vai entrar no laço novamente e pedir para digitar o número correspondente ao tipo de conta, e só ira sair caso digite ou o número 1 ou o número 2.

E agora vamos pensar nas soluções que podemos criar utilizando os laços de repetição.

Boa sorte!!! 