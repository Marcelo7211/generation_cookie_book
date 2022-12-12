# **Stream em Java**

> Os stream Java permitem operações de estilo funcional em fluxos de elementos. Um stream é uma abstração de uma coleção não mutável de funções aplicadas em alguma ordem aos dados. Um stream não é uma coleção onde você pode armazenar elementos.

As informações passadas neste documento norteia os conceitos da Oracle e podemos encontrar através deste link:

<div align="left"><a href="https://www.oracle.com/br/technical-resources/articles/java-stream-api.html"><img src="https://i.imgur.com/DYnNz6q.png" title="source: imgur.com" width="10%"/>Oracle</a></div>

A diferença mais importante entre um stream e uma estrutura é que um stream não contém os dados. Por exemplo, você não pode apontar para um local no stream onde existe um determinado elemento. Você só pode especificar as funções que operam nesses dados. E ao realizar operações em um stream, isso afetará o fluxo original.

Como observação, os streams não devem ser confundidos com fluxos no pacote de E/S Java como InputStream, OutputStream, etc.

Os recursos do stream Java são :

- Um stream não é uma estrutura de dados, mas recebe a entrada das coleções, matrizes ou canais de E/S.
- Os streams não alteram a estrutura de dados original, eles apenas fornecem o resultado de acordo com os métodos em pipeline.
- Cada operação intermediária é executada lentamente e retorna um stream como resultado, portanto, várias operações intermediárias podem ser canalizadas. As operações do terminal marcam o fim do stream e retornam o resultado.

Diferentes operações em streams:

**- operações intermediárias:**

1. **map:** O método map é usado para retornar um fluxo que consiste nos resultados da aplicação da função fornecida aos elementos desse fluxo.
   `List number = Arrays.asList(2,3,4,5);List square = number.stream().map(x->x*x).collect(Collectors.toList());`
2. **filter:** O método filter é usado para selecionar elementos conforme o Predicate passado como argumento.
   `List names = Arrays.asList("Reflection","Collection","Stream");List result = names.stream().filter(s->s.startsWith("S")).collect(Collectors.toList());`
3. **sorted:** O método sorted é usado para classificar o fluxo.
   `List names = Arrays.asList("Reflection","Collection","Stream");List result = names.stream().sorted().collect(Collectors.toList());`

**Operações do Terminal:**

1. **collect:** O método collect é utilizado para retornar o resultado das operações intermediárias realizadas no stream.
   `List number = Arrays.asList(2,3,4,5,3);Set square = number.stream().map(x->x*x).collect(Collectors.toSet());`

2. **forEach:** O método forEach é usado para iterar por todos os elementos do fluxo.
   `List number = Arrays.asList(2,3,4,5);number.stream().map(x->x*x).forEach(y->System.out.println(y));`

3. **reduce:**

    O método reduce é usado para reduzir os elementos de um stream a um único valor.

   O método reduce usa um BinaryOperator como parâmetro.

   

   ```java
   List number = Arrays.asList(2,3,4,5);
   
   int even = number.stream().filter(x->x%2==0).reduce(0,(ans,i)-> ans+i);
   ```

   Aqui, uma variável recebe 0 como valor inicial e i é adicionado a ela.



## Como criar streams

O primeiro passo para se trabalhar com streams é saber como criá-las A forma mais comum é através de uma coleção de dados, tendo em vista que o principal propósito dessa API é tornar mais flexível e eficiente o processamento de coleções. No código abaixo, mostramos como criar uma stream ao invocar o método stream() a partir da interface *java.util.Collection.*

Nesse trecho de código, primeiramente uma lista de strings é definida e três objetos são adicionados a ela. Em seguida, uma stream de strings é obtida ao chamar o método items.stream(). Outra forma de criar *streams* é invocando o método parallelStream(), que possibilitará paralelizar o seu processamento.

Criação de uma stream a partir de um List.

```java
  List items = new ArrayList();
  items.add("um");
  items.add("dois");
  items.add("três");
  Stream stream = items.stream();
```

O método stream() também foi adicionado à interface *java.util.map.* O próximo trecho de código mostra um exemplo de como criar uma stream a partir dessa interface.

Criação de Stream a partir de um Map

```java
 Map  map = new HashMap();
    map.put("key1", "abacate");
  map.put("key2", "melancia");
    	map.put("key3", "manga");
    Stream stream = map.values().stream();
```

Além disso, uma stream pode ser gerada a partir de I/O, arrays e valores. Para obter uma stream a partir de valores ou arrays é muito simples: basta chamar os métodos estáticos Stream.of() ou Arrays.stream(), como mostra o código a seguir:

```java
  Stream numbersFromValues = Stream.of(1, 2, 3, 4, 5); 
  IntStream numbersFromArray = Arrays.stream(new int[] {1, 2, 3, 4, 5});
```

Por sua vez, para criar uma stream de linhas a partir do conteúdo de um arquivo texto (I/O), pode-se chamar o método estático Files.lines(Path path). No código a seguir, por exemplo, é possível descobrir a quantidade de linhas que um arquivo possui:

```java
 Stream  lines= Files.lines(Paths.get(“myFile.txt”),        
         Charset.defaultCharset());
 long numbersLines = lines.count(); 
```

Após conhecer alguns dos diferentes modos para criar e obter streams, o foco agora será em como processá-las. Para isso, será mostrado nos próximos tópicos a transformação e o processamento de *streams* fazendo uso de diferentes operações da interface *Stream*.

Para ilustrar cada uma dessas operações, primeiro criá-se a classe *Pessoa* com quatro atributos básicos: id, nome, nacionalidade e idade. O código abaixo mostra a implementação dessa classe, que traz, também, o método populaPessoas(), criado para preencher uma lista com alguns objetos.

Implementação da classe Pessoa.

```java
public class Pessoa {
    String id;
    String nome;
    String nacionalidade;
    int idade;
     //gets e sets omitidos
 
 public Pessoa(){}
 
 public Pessoa (String id, String nome, String nacionalidade, int idade){
         this.id = id;
         this.nome = nome;
         this.nacionalidade = nacionalidade;
         this.idade = idade;
     }
 
 public List populaPessoas(){
        Pessoa pessoa1 = new Pessoa("p1" , "Matheus Henrique", "Brasil", 18);
         Pessoa pessoa2 = new Pessoa("p2" , "Hernandez Roja", "Mexico", 21);
         Pessoa pessoa3 = new Pessoa("p3" , "Mario Fernandes"¸"Canada", 22);
         Pessoa pessoa4 = new Pessoa("p4" , "Neymar Junior", "Brasil", 22);
         List list = new ArrayList();
         list.add(pessoa1);
         list.add(pessoa2);
         list.add(pessoa3);
         list.add(pessoa4);
         return list;
     } 

       @Override
          public String toString() {
        return this.nome;
      } 
 }
```



**Programa para demonstrar o uso do Stream:**

```java
//um simples exemplo que demonstra o uso do Stream em java
import java.util.*;
import java.util.stream.*;
 
class Demo
{
 public static void main(String args[])
 {
 
  // cria uma lista de inteiros
  List<Integer> number = Arrays.asList(2,3,4,5);
 
  // demonstrando o método map
  List<Integer> square = number.stream().map(x -> x*x).
              collect(Collectors.toList());
  System.out.println(square);
 
  // criando uma lista de String
  List<String> names =
        Arrays.asList("Reflection","Collection","Stream");
 
  // demonstração do método de filtro
  List<String> result = names.stream().filter(s->s.startsWith("S")).
             collect(Collectors.toList());
  System.out.println(result);
 
  // demonstração do método ordenado
  List<String> show =
      names.stream().sorted().collect(Collectors.toList());
  System.out.println(show);
 
  // criação de uma lista de Integer
  List<Integer> numbers = Arrays.asList(2,3,4,5,2);
 
  // método collect retornando um set
  Set<Integer> squareSet =
     numbers.stream().map(x->x*x).collect(Collectors.toSet());
  System.out.println(squareSet);
 }
}
```

Resultado:

```java
[4, 9, 16, 25]
[Fluxo]
[Coleção, Reflexão, Fluxo]
[16, 4, 9, 25]
4
9
16

```

**Pontos/Observações Importantes:**

1. Um stream consiste em source seguido por zero ou mais métodos intermediários combinados (pipelados) e um método terminal para processar os objetos obtidos da fonte conforme os métodos descritos.
2. Stream é usado para computar elementos de acordo com os métodos em pipeline sem alterar o valor original do objeto.

## Expressão lambda em Java

Uma expressão lambda é uma função anônima. Pensando em orientação a objetos em java, uma expressão lambda não pode ser vista como uma função pois não está associada a uma classe onde funções não podem existir fora de um objeto.

Mas na programação funcional, você pode definir funções, fornecer variáveis de referência e passá-las como argumentos de método e muito mais. Geralmente uma **expressão lambda é escrita como parâmetro para uma função.** 

Veja um exemplo simples:

```
Formula : (x) -> 10\*x / 2
```

Recebemos um parâmetro x que será multiplicado por 10 e dividido por 2

Podemos executar desta maneira em Java:

<a href="https://imgur.com/PkK0skr"><img src="https://i.imgur.com/PkK0skr.png" title="source: imgur.com" /></a>

Agora que já vimos como podemos utilizar uma expressão lambda em java, vamos utilizá-la em alguns exemplos com stream.



### Os métodos `skip`, `limit` e `distinct`

Vejamos o exemplo abaixo que filtra alguns resultados antes de apresentá-los.

```java
List<Integer> lista = Arrays.asList(1, 5, 8, 7, 4, 2, 3, 2, 1, 8, 5, 7, 4);

lista.stream()

.skip(2) // ignora os dois primeiros números

.limit(9) // limita a 9 números

.distinct() // ignora números iguais

.forEach(System.out::print);
```

A execução desse código produz a seguinte saída no console:

```java
8742315
```

Nesse exemplo são feitas várias operações **antes** de executar o `forEach:`

- O `skip` serve para ignorar os primeiros X itens. Aqui ignoramos o 1 e o 5.
- O `limit` informa quantos objetos você quer tratar, a partir disso os próximos são ignorados. Aqui pegamos do 8 ao 5.
- O `distinct` é igual ao `DISTINCT` do SQL: ele mantém apenas os resultados que são diferentes entre si. Para isso, ele utiliza o método `equals` dos objetos da lista. Aqui ignoramos a repetição dos números 2 e 8.

### O método `filter`

As 3 funções que mostramos acima “filtram” o nosso stream, ou seja, **ignoram** alguns elementos. Mas e se for necessário um filtro mais **personalizado**? Para isso utiliza-se o método `filter:`

```java
List<Integer> lista = Arrays.asList(1, 5, 8, 7, 4, 2, 3, 2, 1, 8, 5, 7, 4);

lista.stream()

.filter(e -> e % 2 == 0) // mantém apenas números pares

.forEach(System.out::print); // imprime todos no console
```

O trecho de código acima produz a seguinte saída no console:

```java
842284
```

Perceba que o método `filter`, nesse caso, está filtrando nosso stream para manter **apenas** números pares. Se você ainda não está familiarizado com as funções lambdas, a **estrutura** é a seguinte:

<a href="https://imgur.com/bodRh7Z"><img src="https://i.imgur.com/bodRh7Z.png" title="source: imgur.com" /></a>

Estrutura da função lambda passada para o método `filter`

### O método `map`

Caso seja necessário fazer uma **transformação** no dado antes de passá-lo para o próximo método do stream, utiliza-se o método `map`. Apesar do nome, ele não tem relação com a interface `Map`. Veja abaixo.

```java
List<Integer> lista = Arrays.asList(1, 5, 8, 7, 4, 2, 3, 2, 1, 8, 5, 7, 4);

lista.stream()

.map(e -> e * 2) // multiplica cada item por 2

.forEach(e -> System.out.print(e + " ")); // imprime todos no console
```

A saída no console é a seguinte:

```java
2 10 16 14 8 4 6 4 2 16 10 14 8
```

Perceba que todos os números foram multiplicados por 2 antes de serem apresentados no console. Porém, é importante notar que **os números da lista original não foram alterados**. Ou seja, as transformações do método `map` afetam apenas os valores que serão passados para frente **naquele** stream. Isso é excelente, pois sempre que possível o ideal é trabalharmos com valores e instâncias **imutáveis**.

**Exemplo de Stream Java: Possíveis problemas a serem evitados**

No entanto, existem algumas ressalvas ao usar a API de streaming Java e, às vezes, o processamento de stream pode ficar fora de controle. Imagine que temos a seguinte classe Pessoa:

```java
class Person { 
   Genero genero; String name; 
   public Genero getGenero() { return genero; }
   public String getName() { return name; }
}
enum Gender { MASCULINO, FEMININO, OUTROS }
```


Este é um típico Java bean com alguns getters nos campos. Agora, suponha que temos uma lista dessas pessoas e queremos obter a lista de nomes em letras maiúsculas de todas as pessoas “FEMININO” nessa lista. Parece fácil, certo?

```java
List names = new ArrayList(); 
List person = …
people.stream()
  .filter(p -> p.getGenero() == Genero.FEMININO)
  .map(Person::getName)
  .map(String::toUpperCase)
  .forEach(name -> names.add(name)); 
```


Seguimos a especificação do que devemos fazer a cada passo, mas o problema está na mutação do estado compartilhado. Não sabemos nada sobre a natureza do stream e se o stream for paralelo, a adição simultânea dos elementos no fluxo pode levar a erros.

Outra pegadinha a ser evitada: se apenas uma operação intermediária for especificada e a operação do terminal for perdida inadvertidamente, nada será exibido na saída. Isso ocorre porque as operações intermediárias são executadas somente quando uma operação de terminal está presente.

Por exemplo, o snippet a seguir não imprime nenhuma saída:

```java
Stream.of("Cathy","Alba","Beth") 

.filter(s -> { 

System.out.println("filter: " + s); 

return true; 

}); 
```

A ordenação da saída é um tanto surpreendente, pois cada elemento passa por todas as operações (ao contrário do que alguns programadores podem supor - que todos os elementos passam primeiro por filter() e depois por forEach() ). Por exemplo:

```java
Stream.of("Cathy", "Alba", "Beth"). 

filter(s -> { 

System.out.println("filter: " + s); 

return true; 

}) 

.forEach(s -> System.out.println("forEach: " + s)); 

 
```

A saída é:

```java
filter: Cathy 

forEach: Cathy 

filter: Alba 

forEach: Alba 

filter: Beth 

forEach: Beth 
```



**Usando o Java Stream Collect para evitar erros de simultaneidade**

Em vez disso, deveríamos ter *collect* o stream na lista resultante, para que a simultaneidade e a mutabilidade sejam de responsabilidade da estrutura de fluxos. Aqui está o exemplo de como fazer isso:

```java
List people = …
List names = people.stream()
  .filter(p -> p.getGenero() == Genero.FEMININO)
  .map(Person::getName)
  .map(String::toUpperCase)
  .collect(Collectors.toList()); 
```


Em geral, a classe Collectors fornece quase todas as primitivas necessárias para transformar um stream em uma coleção concreta. Um exemplo é o coletor *toMap()* . Você pode estar confuso sobre como um elemento pode ser transformado em um par chave-valor necessário para o mapa.

Para fazer isso, você especifica uma função que transforma o elemento na chave e outra função que cria o valor. Aqui está um exemplo que coleta o mesmo fluxo de pessoas em um mapa:

```java
List people = …
Map<String, Person> names = people.stream()
  .collect(Collectors.toMap(p -> p.getName(), p -> p)); 
```


A primeira função dada ao método *toMap* transforma o elemento na chave e a segunda no valor do mapa.

## Operações de terminal e intermediário do Java Stream

Uma das virtudes dos streams Java é que eles são avaliados demoradamente. Algumas operações nos streams, principalmente as funções que retornam uma instância do stream: filter, map, são chamadas **de intermediárias** . Isso significa que eles não são avaliados quando são especificados. Isso significa que eles não serão avaliados quando forem especificados. Em vez disso, a computação acontecerá quando o resultado dessa operação for necessário. 

Isso significa que, se apenas especificarmos o código como:

```java
Stream names = people.stream()
  .filter(p -> p.getGenero() == Genero.FEMININO)
  .map(Person::getName)
  .map(String::toUpperCase);
```


Nenhum dos nomes será imediatamente coletado e transformado em caixa alta. Então, o cálculo ocorre? Quando uma operação de **terminal** é chamada.

Todas as operações que retornam algo diferente de um stream são terminais. Operações como forEach, collect, reduce são terminais. Isso torna os fluxos particularmente eficientes no manuseio de grandes quantidades de dados.

Do ponto de vista do desempenho, a ordenação das operações intermediárias é crítica.

Por exemplo, se map() for especificado antes de filter(), map() será chamado várias vezes. No entanto, se filter() for especificado antes de map(), map() será chamado apenas uma vez, levando a um alto desempenho.

```java
Stream.of("Cathy", "Alba", "Beth") 

    .map(s -> { 

        System.out.println("map: " + s); 

        return s.toUpperCase(); 

    }) 

    .filter(s -> { 

        System.out.println("filter: " + s); 

        return s.startsWith("A"); 

    }) 

    .forEach(s -> System.out.println("forEach: " + s)); 
 
```

 

Aqui map() é chamado várias vezes, o que é sub-ótimo. No entanto, neste exemplo, map() é chamado apenas uma vez, levando a um desempenho aprimorado.

```java
Stream.of("Cathy", "Alba", "Beth") 

  .filter(s -> { 

    System.out.println("filter: " + s); 

    return s.startsWith("A"); 

  }) 

  .map(s -> { 

    System.out.println("map: " + s); 

    return s.toUpperCase(); 

  }) 

  .forEach(s -> System.out.println("forEach: " + s)); 
```

Além disso, quase sempre pode-se tentar paralelizar o processamento do stream convertendo o stream em um stream paralelo chamando o método *parallel()* . Observe que, embora o stream não precise ser paralelizável, o método para paralelizá-lo está sempre lá. Portanto, dependendo da natureza interna do stream, você pode obter os benefícios de desempenho.

## Considerações finais sobre a API Java Streams

Existem armadilhas em executar cada operação de stream em paralelo; a maioria das implementações de streams usa o ForkJoinPool padrão para realizar as operações em segundo plano. Assim, você pode facilmente tornar o processamento de stream específico um pouco mais rápido, mas, em vez disso, sacrificar o desempenho de toda a JVM sem nem perceber.

Resolver os problemas usando programação funcional requer uma maneira diferente de pensar. Mas com um pouco de experimentação, você pode pegar o jeito.

E, muitas vezes, você pode se esforçar para encontrar uma solução funcional, mas depois de obtê-la, percebe que não é particularmente complicado. E então, da próxima vez, resolver um problema semelhante será muito mais fácil.



------

# **Projeto Java**

## Como implementar?

Agora devemos pensar como podemos implementar dentro do nosso projeto, isso pode se fazer de várias maneiras, uma maneira interessante poderia ser a implementação de alguns produtos bancários dentro do seu projeto. Vamos demonstrar nos códigos abaixo como podemos fazer isso através do stream.

#### Cenário 1

Seu cliente solicita que você some todos os números pares de uma lista e mostre o resultado.
Sem o uso de Stream:

<a href="https://imgur.com/o8fzMV7"><img src="https://i.imgur.com/o8fzMV7.png" title="source: imgur.com" /></a>

Nesta solução percorremos todos os itens da lista usando for , verificamos se o número é par e somamos os números que forem pares na variável resultado e mostramos em tela o resultado.

Agora usando Stream API:

<a href="https://imgur.com/p49zQmG"><img src="https://i.imgur.com/p49zQmG.png" title="source: imgur.com" /></a>

Nesta solução com apenas 2 linhas pegamos a lista, convertemos para Stream, usamos o método filter para filtrar elementos de uma stream com uma condição (predicado), efetuamos a transformação na lista de dados, efetuamos a soma e mostramos em tela.
‍

#### Cenário 2

Seu cliente solicita todos os nomes que começam com a letra “M” de uma lista de clientes do banco que foram convidados.
‍
Sem o uso de Stream:

<a href="https://imgur.com/UHZT2Jy"><img src="https://i.imgur.com/UHZT2Jy.png" title="source: imgur.com" /></a>

Nesta solução percorremos a lista, criamos uma variável para armazenar a primeira letra dos nomes e verificamos se essa primeira letra do nome inicia com M, se iniciar com M mostramos em tela.

Agora usando Stream API:
‍

<a href="https://imgur.com/eFj2eif"><img src="https://i.imgur.com/eFj2eif.png" title="source: imgur.com" /></a>

Nesta solução pegamos a lista lista Convidados do Banco convertemos para Stream, usamos o método filter para filtrar elementos de uma stream com uma condição (predicado), convertemos para um tipo list compatível e mostramos em tela.

Com Stream Api você diminui linhas de código, melhora a legibilidade, facilita a manutenção e ganha produtividade no desenvolvimento. 
