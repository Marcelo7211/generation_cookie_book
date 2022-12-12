<h1><center>JAVA - Operadores</center></h1>



## Operadores em Java e seus tipos

Java suporta os seguintes tipos de operadores:

- Operadores aritméticos
- Operadores de Atribuição
- Operadores lógicos
- Operadores Relacionais
- Operadores Unários
- Operadores bit a bit
- Operadores Ternários

## Operadores Aritméticos Java

Os operadores aritméticos são usados para realizar operações aritméticas em variáveis e dados. Por exemplo,

```
a + b;
```

Aqui, o `+`operador é usado para adicionar duas variáveis (a e b). Da mesma forma, existem vários outros operadores aritméticos em Java.

| Operador | Operação                                  |
| -------- | ----------------------------------------- |
| `+`      | Adição                                    |
| `-`      | Subtração                                 |
| `*`      | Multiplicação                             |
| `/`      | Divisão                                   |
| `%`      | Operação Módulo (Restante após a divisão) |

### Exemplo 1: Operadores aritméticos

```java
class Main {
  public static void main(String[] args) {
    
    // declaração das variáveis
    int a = 12, b = 5;

    // operador adição
    System.out.println("a + b = " + (a + b));

    // operador subtração
    System.out.println("a - b = " + (a - b));

    // operador multiplicação
    System.out.println("a * b = " + (a * b));

    // operador divisão
    System.out.println("a / b = " + (a / b));

    // operador módulo
    System.out.println("a % b = " + (a % b));
  }
}
```

Quando executamos o código acima o resultado esperado é o seguinte:

**Resultado**

```java
a + b = 17
a - b = 7
a * b = 60
a/b = 2
a % b = 2
```



## Operadores de atribuição em Java

Um *operador de atribuição* é um *operador* usado para *atribuir* um novo valor a uma variável. Suponha A = 10 e B = 20 para a tabela abaixo.

<a href="https://imgur.com/y1iHuQg" align="center"><img src="https://i.imgur.com/y1iHuQg.png" title="source: imgur.com" /></a>

Considere o exemplo abaixo:

```java
pacote  Edureka;public  class  JavaOperators { 
       public  static  void  main(String[] args) { 
              int  a = 10; 
              intb  =20; 
              intc  ; 
              System.out.println(c = a); // Output =10 
              System.out.println(b += a);// Output=30 
              System.out.println(b -= a);// Output=20 
              System.out.println(b *= a) ;// Output=200 
              System.out.println(b /= a);// Output=2 
              System.out.println(b %= a);// Output=0 
              System.out.println(b ^= a ); // Saída=0 
       } 
}
```



## Operadores Relacionais em Java

Esses operadores comparam os valores de cada lado deles e decidem a relação entre eles. Suponha A = 10 e B = 20.

<a href="https://imgur.com/CZ0AVC9"><img src="https://i.imgur.com/CZ0AVC9.png" title="source: imgur.com" /></a>

Considere o exemplo abaixo:

```java
pacote  Edureka;public  class  JavaOperators { 
        public  static  void  main(String[] args) { 
               int  a = 10; 
               intb  =20; 
               System.out.println(a == b); // retorna false porque 10 não é igual a 20 
               System.out.println(a != b); // retorna true porque 10 não é igual a 20 
                System.out.println(a > b); // retorna falso 
                System.out.println(a < b); // retorna true 
                System.out.println(a >= b); // retorna falso 
                System.out.println(a <= b); // retorna verdadeiro        }}
```

Em seguida, vamos nos concentrar nos operadores lógicos em Java.

## Operadores Lógicos Java

Os operadores lógicos são usados para verificar se uma expressão é `true`ou `false`. Eles são usados na tomada de decisões.

| Operador        | Exemplo                        | Significado                                          |
| :-------------- | :----------------------------- | :--------------------------------------------------- |
| `&&`(E lógico)  | expressão1 **&&** expressão2   | `true`somente se ambosexpressão1eexpressão2são`true` |
| `||`(OU lógico) | expressão1 **\|\|** expressão2 | `true`se tambémexpressão1ouexpressão2é`true`         |
| `!`(NÃO Lógico) | **!** expressão                | `true`E seexpressãoé `false`e vice-versa             |

### Exemplo : Operadores lógicos

```java
class Main {
  public static void main(String[] args) {

    // && operator
    System.out.println((5 > 3) && (8 > 5));  // true
    System.out.println((5 > 3) && (8 < 5));  // false

    // || operator
    System.out.println((5 < 3) || (8 > 5));  // true
    System.out.println((5 > 3) || (8 < 5));  // true
    System.out.println((5 < 3) || (8 < 5));  // false

    // ! operator
    System.out.println(!(5 == 3));  // true
    System.out.println(!(5 > 3));  // false
  }
}
```

**Funcionamento do Programa**

- `(5 > 3) && (8 > 5)`retorna `true`porque ambos `(5 > 3)`e `(8 > 5)`são `true`.
- `(5 > 3) && (8 < 5)`retorna `false`porque a expressão `(8 < 5)`é `false`.
- `(5 < 3) || (8 > 5)`retorna `true`porque a expressão `(8 > 5)`é `true`.
- `(5 > 3) || (8 < 5)`retorna `true`porque a expressão `(5 > 3)`é `true`.
- `(5 < 3) || (8 < 5)`retorna `false`porque ambos `(5 < 3)`e `(8 < 5)`são `false`.
- `!(5 == 3)`retorna true porque `5 == 3`é `false`.
- `!(5 > 3)`retorna false porque `5 > 3`é `true`.



## Operadores Unários Java

Operadores unários são usados com apenas um operando. Por exemplo, `++`é um operador unário que aumenta o valor de uma variável em **1** . Ou seja, `++5`retornará **6** .

Diferentes tipos de operadores unários são:

| Operador | Significado                                                  |
| :------- | :----------------------------------------------------------- |
| `+`      | **Mais unário** : não é necessário usar, pois os números são positivos sem usá-lo |
| `-`      | **Menos unário** : inverte o sinal de uma expressão          |
| `++`     | **Operador** de incremento: incrementa o valor em 1          |
| `--`     | **Operador** de decremento: decrementa o valor em 1          |
| `!`      | **Operador de complemento lógico** : inverte o valor de um booleano |



## Operadores de incremento e decremento

Java também fornece operadores de incremento e decremento: `++`e `--`respectivamente. `++`aumenta o valor do operando em **1** , enquanto `--`o diminui em **1** . Por exemplo,

```java
int num = 5;

// incrementa 1 na variável
++num;
```

Aqui, o valor do número é aumentado para **6** de seu valor inicial de **5** .

------

### Exemplo : Operadores de Incremento e Decremento

```java
class Main {
  public static void main(String[] args) {
    
    // declaração das variáveis
    int a = 12, b = 12;
    int result1, result2;

    // valor original
    System.out.println("Valor de a: " + a);

    // operador incremento
    result1 = ++a;
    System.out.println("After increment: " + result1);

    System.out.println("Valor de b: " + b);

    // operador decremento
    result2 = --b;
    System.out.println("After decrement: " + result2);
  }
}
```

**Resultado**

```java
Valor de a: 12
Após o incremento: 13
Valor de b: 12     
Após decremento: 11
```

No programa acima, usamos o operador ++ e -- como **prefixos (++a, --b)** . Também podemos usar esses operadores como **postfix (a++, b++)** .

Há uma pequena diferença quando esses operadores são usados como prefixo versus quando são usados como pós-fixo.

## Operadores Java Bitwise

Operadores bit a bit em Java são usados para realizar operações em bits individuais. Por exemplo,

```java
Operação de Compelento bit a bit de 35

35 = 00100011 (In Binary)

~ 00100011 
  ________
   11011100  = 220 (In decimal)
```

Aqui, `~`é um operador bit a bit. Inverte o valor de cada bit ( **0** para **1** e **1** para **0** ).

Os vários operadores bit a bit presentes em Java são:

| Operador | Descrição                           |
| :------- | :---------------------------------- |
| `~`      | Complemento bit a bit               |
| `<<`     | Desvio à esquerda                   |
| `>>`     | Deslocamento para a direita         |
| `>>>`    | Deslocamento à direita não assinado |
| `&`      | E bit a bit                         |
| `^`      | OU exclusivo bit a bit              |

Esses operadores geralmente não são usados em Java.

------

## Outros operadores

Além desses operadores, existem outros operadores adicionais em Java.

### Java instanceof Operator

O `instanceof`operador verifica se um objeto é uma instância de uma determinada classe. Por exemplo,

```java
class Main {
  public static void main(String[] args) {

    String str = "Programiz";
    boolean result;

    // checks if str is an instance of
    // the String class
    result = str instanceof String;
    System.out.println("Is str an object of String? " + result);
  }
}
```



**Resultado**

```java
str é um objeto de String? verdadeiro
```

Aqui,stré uma instância da `String`classe. Assim, o `instanceof`operador retorna `true`. 



### Operador Ternário Java

O operador ternário (operador condicional) é um atalho para a `if-then-else`instrução. Por exemplo,

```java
variável = Expressão ? expressão1: expressão2
```

Aqui está como funciona.

- Se o `Expression`é `true`, `expression1`é atribuído a variável.
- Se o `Expression`é `false`, `expression2`é atribuído a variável.

Vejamos um exemplo de operador ternário.

```java
class Java {
  public static void main(String[] args) {

    int februaryDays = 29;
    String result;

    // ternary operator
    result = (februaryDays == 28) ? "Not a leap year" : "Leap year";
    System.out.println(result);
  }
}
```



**Resultado**

```java
Ano bissexto
```

No exemplo acima, usamos o operador ternário para verificar se o ano é bissexto ou não.

------

# **Projeto Java**

Neste momento vamos começar a desenvolver alguns conceitos vistos neste conteúdo dentro de um projeto do primeiro módulo.

A ideia é termos um desenvolvimento contínuo, conforme iremos adicionando conteúdos ao nosso bootcamp neste primeiro bloco do treinamento.

E com isso começamos pela utilização dos operadores dentro do nosso projeto. 

Em muitos momentos serão necessários utilizá-los para poder gerar algumas soluções dentro do contexto do projeto. Por exemplo:

```java
public boolean sacar(float valor){

		if(this.getSaldo() < valor){

			System.out.println("\n Saldo insuficiente! ");

			return false;

		}

		this.setSaldo(this.getSaldo() - valor);

		return true;

}
```

Neste trecho de código podemos perceber a utilização dos operadores relacionais e aritméticos para fazer a ação de verificar se o valor é menor que o saldo e para extrair o valor do saldo.

Agora é com vocês. Vamos implementar os operadores no projeto.

Boa sorte !!!



<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>
