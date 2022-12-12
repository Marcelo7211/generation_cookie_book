<h1>Optional</h1>

As informações passadas neste documento norteia os conceitos da Oracle e podemos encontrar através deste link:

<div align="left"><a href="https://docs.oracle.com/javase/8/docs/api/"><img src="https://i.imgur.com/DYnNz6q.png" title="source: imgur.com" width="10%"/>Oracle</a></div>

*Optional* é uma classe que foi implementada no Java 8, que tem o objetivo de  simplificar os códigos, facilitando a vida dos desenvolvedores.

O *Optional* nos ajuda a evitar os erros do tipo *NullPointerException*, eliminando a necessidade da verificação se um Objeto é nulo (null), além de escrever um código com menos linhas e mais elegante.

<h2>Principais Métodos  da Classe Optional</h2>

| Método            | Descrição                                                    |
| ----------------- | ------------------------------------------------------------ |
| **empty()**       | Retorna uma instância do `Optional` vazia.                   |
| **of()**          | Retorna um `Optional` com o valor fornecido, mas o valor não pode ser nulo. |
| **ofNullable()**  | Se um valor estiver presente, retorna um `Optional` com o valor, caso contrário, retorna um `Optional` vazio. Este é um dos métodos mais indicados para criar um `Optional`, principalmente quando não se tem a certeza de que o Objeto está ou estará presente. |
| **filter()**      | Se um valor estiver presente e o valor corresponder ao critério de filtragem, ele retorna um `Optional` com o valor, se não, retorna um `Optional` vazio. |
| **isPresent()**   | Checa se um valor está presente. Se estiver retorna `true`, se não, retorna `false`. |
| **get()**         | Se um valor estiver presente, ele retorna o valor, caso contrário, lança a exceção `NoSuchElementException`, logo para usar o `get` é preciso ter certeza de que o `Optional` não está vazio. |
| **ifPresent()**   | Se um valor estiver presente, executa uma ação no valor, caso contrário, não faz nada. |
| **map()**         | Se um valor estiver presente retorna um `Optinal` com o resultado da aplicação da função de mapeamento no valor, caso contrário, retorna um `Optional` vazio. Geralmente utilizamos o Optional em conjunto com as Expressões Lambda. |
| **flatMap()**     | Semelhante ao `map`, se um valor estiver presente, retorna o resultado da aplicação da função de mapeamento no valor, caso contrário retorna um `Optional` vazio. A diferença é que o `flatMap` pode ser aplicado a um mapeamento que também retorna um `Optional`. |
| **orElse()**      | Geralmente utilizado em conjunto com o **método map()** ou com o **método flatMap()**, se o resultado do **método map()** ou do **método flatMap()** for falso, ele retorna o valor definido no parâmetro do método **orElse()**. |
| **orElseGet()**   | Geralmente utilizado em conjunto com o **método map()** ou com o **método flatMap()**, se o resultado do **método map()** ou do **método flatMap()** for falso, retorna o resultado produzido pelo parâmetro. |
| **orElseThrow()** | Geralmente utilizado em conjunto com o **método map()** ou com o **método flatMap()**, se o resultado do **método map()** ou do **método flatMap()** for falso, lança uma exceção informada no parâmetro. |

<h2>Exemplos</h2>

**Exemplo 01**

Primeiro vamos criar o código abaixo, que irá causar um erro do tipo **NullPointerException**, sem o **Optional**:

```java
package com.generation.optional01;

public class Optional01 {

	public static void main(String[] args) {
        
		String[] palavras = new String[10];
		String palavra = palavras[5].toLowerCase();
		System.out.println(palavra);
        
	}
}
```

No console será exibido o erro abaixo:

```java
Exception in thread "main" java.lang.NullPointerException
```

Na sequência, vamos evitar o erro implementando o Optional:

```java
package com.generation.optional01;

import java.util.Optional;

public class Optional01 {

	public static void main(String[] args) {

		String[] palavras = new String[10];

		Optional<String> checaNulo = Optional.ofNullable(palavras[5]);

		if (checaNulo.isPresent()) {
			String palavra = palavras[5].toLowerCase();
			System.out.print(palavra);
		} else
			System.out.println("A palavra é nula!");
	}

}
```

No console será exibida a mensagem abaixo:

```java
A palavra é nula!
```



**Exemplo 02 - Métodos empty(), get() e IsPresent()** 

Neste exemplo vamos utilizar os Métodos **empty(), get() e IsPresent()**:

```java
package com.generation.optional02;

import java.util.Optional;

public class Optional02 {

	public static void main(String[] args) {

		frases[2] = "Generation Brasil";
		
		Optional<String> vazio = Optional.empty();
		System.out.println(vazio);

		Optional<String> valor_indice_02 = Optional.of(frases[2]);
		System.out.println(valor_indice_02);
		System.out.println(valor_indice_02.get());
		System.out.println(valor_indice_02.isPresent());

	}

}
```

No console será exibida a mensagem abaixo:

```java
Optional.empty
Optional[Generation Brasil]
Generation Brasil
true
```

<br /><br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>	
