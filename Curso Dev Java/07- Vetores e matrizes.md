

# **Java Array**



## O que é um array em Java?

Normalmente, um array é uma coleção de tipos semelhantes de elementos que possuem localização de memória contígua.

O array Java é um objeto que contém elementos de um tipo de dados semelhante. Além disso, os elementos de uma matriz são armazenados em um local de memória contíguo. É uma estrutura de dados onde armazenamos elementos semelhantes. Podemos armazenar apenas um conjunto fixo de elementos em um array Java.

O array em Java é baseado em índice, o primeiro elemento do array é armazenado no 0º índice, o 2º elemento é armazenado no 1º índice e assim por diante.

Ao contrário do C/C++, podemos obter o comprimento do array usando o membro length. Em C/C++, precisamos usar o operador sizeof.

Em Java, array é um objeto de uma classe gerada dinamicamente. O array Java herda a classe Object e implementa as interfaces Serializable e Cloneable. Podemos armazenar valores primitivos ou objetos em um array em Java. Também podemos criar arrays unidimensionais ou multidimensionais em Java.

Além disso, Java fornece o recurso de arrays anônimos que não está disponível em C/C++.

<a href="https://imgur.com/KvEZ7l4" align="center"><img src="https://i.imgur.com/KvEZ7l4.gif" title="source: imgur.com" /> </a>



## Qual a sintaxe do Java array?

Em Java, quando utilizamos um array, escrevemos sua representação com o uso de chaves — “[elemento1, elemento2 …]”. Podemos definir uma array sem número especificado, apenas indicando que aquela variável é um array. A sintaxe é a seguinte:

```java
tipo do objeto, como String, Integer, etc. [] nome de nosso array
```

Para facilitar o entendimento, veja um exemplo aplicado:

```java
String[] nomes;
```

No exemplo acima, apenas definimos um array — sem determinar elementos ou número de posições para serem ocupadas. Poderemos preencher esses espaços no array apenas os designando durante o desenvolvimento do código. Assim:

```java
String[] nomes = {"Luis", "Cris", "Lucas", "Marcelo"}
```

Quando precisarmos acessar alguns desses elementos pertencentes às mesmas variáveis, buscamos diretamente a variável do array “nome”. Vamos a um exemplo prático, bem simples, para ajudar no entendimento:

```java
public class Main {
  public static void main(String[] args) {
   String[] carros = {"Creta", "Pajero", "HRV"};
   System.out.println(carros[0]);
  }
}
```

O primeiro elemento de um array começa sempre a ser contado em 0. Nesse caso, quando pedimos a posição zero (“[0]”) do array “carros”, a saída no console desse código será:

```java
Creta
```

### Instanciando um Array em Java

Quando um array é declarado, apenas uma referência de um array é criada. Para criar ou dar memória ao array, você cria um array como este: A forma geral de *new* como se aplica a arrays unidimensionais aparece da seguinte forma: 

```
var_name = new type [tamanho];
```

Aqui, *type* especifica o tipo de dado que está sendo alocado, *tamanho* determina o número de elementos no array e *var-name* é o nome da variável do array que está vinculada ao array. Para usar *new* para alocar uma matriz, **você deve especificar o tipo e o número de elementos a serem alocados.**

**Exemplo:** 

```java
int intArray[]; //declarando array
intArray = new int[20]; // alocando memoria para array
```

OU 

```java
int[] intArray = new int[20]; // combinando as duas instruções em uma
```

> **Observação:** 
>
> 
>
> Os elementos no array alocados por *new* serão inicializados automaticamente com **zero** (para tipos numéricos), **false** (para boolean) ou **null** (para tipos de referência). 
>
> A obtenção de uma matriz é um processo de duas etapas. Primeiro, você deve declarar uma variável do tipo de array desejado. Segundo, você deve alocar a memória para armazenar o array, usando new, e atribuí-lo à variável do array. Assim, **em Java** , **todos os arrays são alocados dinamicamente.**

### Array Literal

Em uma situação em que o tamanho do array e as variáveis do array já são conhecidos, podem ser usados literais de array. 

```java
int[] intArray = new int[]{ 1,2,3,4,5,6,7,8,9,10 };
 // Declarando o literal do array
```

- O comprimento desta matriz determina o comprimento da matriz criada.
- Não há necessidade de escrever a nova parte int[] nas versões mais recentes do Java.

### Acessando elementos Java Array usando for Loop

Cada elemento na matriz é acessado por meio de seu índice. O índice começa com 0 e termina em (tamanho total do array)-1. Todos os elementos do array podem ser acessados usando Java for Loop.

```java
// acessando os elementos do array especificado
for (int i = 0; i < arr.length; i++)
  System.out.println("Elemento no índice " + i +
                                " : "+ arr[i]);
```

**Implementação:**

```java
	class GFG {
	public static void main(String[] args)
	{
	// declara um array de inteiros.
	int[] arr;
	// alocando memória para 5 inteiros
	arr = new int[5];

	// inicializando os primeiros elementos do array
	arr[0] = 10;

	// inicializando o segundo elemento do array
	arr[1] = 20;

	// os próximos elementos...
	arr[2] = 30;
	arr[3] = 40;
	arr[4] = 50;

	// acessando os elementos do array especificado
	for (int i = 0; i < arr.length; i++)
		System.out.println("Element at index " + i
						+ " : " + arr[i]);
}
}
```


**Resultado**

```java
Elemento no índice 0 : 10
Elemento no índice 1: 20
Elemento no índice 2: 30
Elemento no índice 3: 40
Elemento no índice 4: 50
```



## Arrays unidimensionais

Arrays de uma única dimensão **são vetores que têm um único índice como identificador para cada elemento contido em um array**. No caso do exemplo de que falamos logo acima, a forma que usamos para declarar um array sem determinar seus elementos, mas apenas as posições que serão ocupadas, será da seguinte maneira:

```java
public class MyClass {
   public static void main(String args[]) {
       int[] array_de_uma_dimensão = new int[5];    
   }
}
```

Repare que, nesse exemplo, criamos um array com o nome de “array_de_uma_dimensão”, e percebemos que ele terá 5 posições possíveis de serem ocupadas. **Mas será que podemos criar objetos como tabelas, com mais de uma linha de índices?** É sobre isso que falaremos, a seguir.

## Arrays multidimensionais

Saiba que também podemos operar com arrays de mais de uma dimensão. **É possível compará-los a tabelas**. Isso porque você pode enumerar múltiplos índices em um mesmo array, formando, assim, diversas linhas e colunas, com cada espaço sendo pertencente a um elemento. Para declararmos um array multidimensional, fazemos dessa forma:

```java
public class MyClass {
   public static void main(String args[]) {
       int[][] array_multimensão = new int[5][5];
   }
}
```

Aqui, temos a aplicação de um novo array, mas com duas dimensões — ou dois índices. Eles acabam formando uma tabela 5 X 5, com 25 posições possíveis, nesse caso.



## Como descobrir o tamanho de um array?

Como já era de se esperar, há diversas maneiras de se contabilizar os elementos contidos em um array. A mais óbvia, para aquelas pessoas já familiarizadas ao mundo da programação, **é a criação de uma** [**variável**](https://blog.betrybe.com/php-array/), **e usar um laço de repetição para modificá-la a cada elemento**. Ficaria dessa maneira:

```java
public class Main {
   public static void main(String[] args) {
           int contador = 0;
           String[] carros = {"Fusca", "Kombi", "Gol", "Ferrari"};
               for (String i : carros) {
                       contador = ++contador;
}
       System.out.println(contador);
               }
    
}
```

Veja que, nesse exemplo, temos como resultado a impressão do número 4 no console, indicando a presença de 4 elementos. Perceba que a contagem se deu a partir do laço for utilizado na variável “contador”.

Outra maneira possível e bastante optada pelas pessoas desenvolvedoras é usar o método length(). Com ele, acessamos diretamente a informação referente à quantidade de posições ocupadas em um array. Trazemos um exemplo para facilitar seu entendimento:

```java
public class Main {
  public static void main(String[] args) {
   String[] carros = {""Fusca", "Kombi", "Gol", "Ferrari"};
   System.out.println(carros.length);
  }
}
```

A saída será a mesma da anterior:

```java
4
```



## **For-each Loop para Java Array**

Também podemos imprimir o array Java usando o loop for-each. O loop for-each Java imprime os elementos do array um por um. Ele contém um elemento de matriz em uma variável e, em seguida, executa o corpo do loop.

A sintaxe do loop for-each é dada abaixo:

```java
for ( tipo_dados variável : array ){ 

//corpo do loop 

} 
```

Vejamos o exemplo de imprimir os elementos do array Java usando o loop for-each:

```java
//Programa Java para imprimir o array de elementos utilizando o loop for-each 

class Testarray1{ 

public static void main(String args[]){ 

int arr[]={33,3,4,5}; 

//imprimindo o array usando o loop for-each 

for(int i:arr) 

System.out.println(i); 

}} 
```

Saída:

```java
33

3

4

5
```

------

# **Projeto Java**

Revisando o nosso conteúdo, então aprendemos a criar, popular e manipular os nossos arrays dentro da linguagem java. Isso se torna muito importante para o nosso projeto java, pois agora podemos gerar vários conteúdos e guardar dentro de um único repositório, onde a sua busca será sempre pelo seu index(índice).

Sabendo disso, podemos começar a desenvolver algumas funcionalidades que serão de grande importância para o nosso projeto. Por exemplo, podemos começar a criar as nossas contas, os nossos usuários e guardar dentro dos arrays. Assim podemos por exemplo verificar o maior valor de cada conta ou mesmo de qual cliente que são as contas que estão com o saldo negativo.

Então vamos começar a programar... 

<a href="https://imgur.com/zfUhH0Q"><img src="https://i.imgur.com/zfUhH0Q.gif" title="source: imgur.com" /></a>