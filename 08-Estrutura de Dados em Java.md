# **Estrutura de Dados em Java**

Uma **estrutura de dados** é usada para organizar informações que um computador pode acessar e processar de maneira fácil e eficiente. Você já está familiarizado com um tipo de estrutura de dados — arrays, que discutimos no Java7. Se você se lembra, um array é um exemplo de estrutura de dados em que todos os dados são do mesmo tipo ou classe e em que os elementos são acessados por sua posição (índice ou subscrito). Um array é um exemplo de estrutura estática, pois seu tamanho é fixo durante a execução do programa. (Este é um significado diferente de static do que a palavra-chave Java static.)

A classe Vector é outro exemplo de estrutura de dados. Como uma matriz, os elementos vetoriais individuais são acessados por sua posição. No entanto, diferentemente dos arrays, um vetor é um exemplo de **estrutura dinâmica** — ou seja, uma estrutura que pode crescer e diminuir durante a execução de um programa.

Essas são apenas duas das muitas estruturas de dados desenvolvidas por cientistas da computação. Para problemas mais avançados, muitas vezes é necessário desenvolver estruturas especializadas para armazenar e manipular informações. Algumas dessas estruturas — listas encadeadas, pilhas, filas, árvores binárias, tabelas de hash — tornaram-se objetos clássicos de estudo em ciência da computação.

Vamos descrever neste documento como implementar uma lista encadeada e como usar a herança para estender a lista para implementar as estruturas de pilha e fila. `java.util`Em seguida , será descrita a implementação do Java Collections Framework de várias estruturas de dados no pacote.



## **Vantagens das estruturas de dados Java**

- **Eficiência:** Estruturas de dados são usadas para aumentar a eficiência e o desempenho de um aplicativo, organizando os dados de forma que exija menos espaço com maior velocidade de processamento.
- **Reutilização:** As estruturas de dados fornecem reutilização de dados, ou seja, após implementar uma determinada estrutura de dados uma vez, podemos usá-la muitas vezes em qualquer outro lugar. Podemos compilar a implementação dessas estruturas de dados em bibliotecas e os clientes podem usar essas bibliotecas de várias maneiras.
- **Abstração:** Em Java, o ADT (Abstract Data Types) é usado para especificar uma estrutura de dados. O ADT fornece um nível de abstração. O programa cliente usa a estrutura de dados apenas com a ajuda da interface, sem ter conhecimento dos detalhes de implementação.



## **Classificação da Estrutura de Dados em Java**

<a href="https://imgur.com/mj6O7jC"><img src="https://i.imgur.com/mj6O7jC.png" title="source: imgur.com" /></a>

- **Estruturas de dados lineares:** Em uma estrutura de dados linear, todos os elementos são organizados na ordem linear ou sequencial. A estrutura de dados linear é uma estrutura de dados de nível único.
- **Estruturas de dados não lineares:** A estrutura de dados não linear não organiza os dados de maneira sequencial como nas estruturas de dados lineares. As estruturas de dados não lineares são a estrutura de dados multinível.

## Tipos de estrutura de dados em Java

Existem alguns tipos comuns de estrutura de dados em Java, eles são os seguintes:

1. **Arrays**
2. **Linked Lists**
3. **Stack**
4. **Queue**
5. **Graph**
6. **Set**



**1- Arrays**

Esta estrutura de dados já vimos no documento anterior então não vamos mostrar a sua prática e seus conceitos neste documento.

**2- Linked Lists**

Uma lista vinculada (ou encadeada) dinamicamente é uma estrutura de dados linear e dinâmica. Ela é composta por um conjunto de nós, cada nó possuindo dois elementos: o primeiro armazena informações e o segundo armazena o ponteiro, o qual guarda informação do endereço (referências a endereços de memória) para o próximo nó na lista. Em uma implementação de lista ligada, cada nó (item) da lista é ligado com o seguinte através do ponteiro (uma variável com o valor do endereçamento para o próximo nó). Isso significa dizer que cada nó da lista contém o registro de dados (informações) e uma variável que aponta para o próximo nó. Este tipo de implementação permite utilizar posições não contíguas de memória, sendo possível inserir e retirar elementos sem haver a necessidade de deslocar os nós seguintes da lista.

<a href="https://imgur.com/l1x98MQ"><img src="https://i.imgur.com/l1x98MQ.png" title="source: imgur.com" /></a>

A cabeça em uma lista ligada dinamicamente representa o primeiro elemento da lista e deve ser guardada em uma variável (primeiro) e a cauda representa o último elemento a qual também deve ser guardada em uma variável (ultimo). Assim, conhecemos, inicialmente, dois elementos da lista: o primeiro e o último. Se desejarmos manipular a lista, devemos inicialmente nos referenciar a estas variáveis e, a partir delas, percorrer a lista para identificar o restante. 

O limite para a alocação dinâmica é diretamente proporcional à quantidade de memória física que está disponível na máquina, valendo, também, o tamanho do espaço físico disponível dentro do sistema de memória virtual . 

Se a memória disponível for insuficiente, a expressão lança um OutOfMemoryError. 

Vamos ver as vantagens e desvantagens da utilização desse tipo de lista: 

**Vantagens** 

• A inserção ou remoção de um elemento na lista não implica a mudança de lugar de outros elementos. 

• Não é necessário definir, no momento da criação da lista, o número máximo de elementos que esta poderá ter. em outras palavras, é possível alocar memória "dinamicamente", apenas para o número de nós necessários. 

**Desvantagens** 

• A manipulação torna-se mais "perigosa" uma vez que, se o encadeamento (ligação) entre elementos da lista for mal feito, toda a lista pode ser perdida. 

• Para aceder ao elemento na posição n da lista, deve-se percorrer os n - 1 anteriores. Conhecedores dos prós e contras, vamos aprender como implementar uma lista ligada dinâmica.



A implementação a seguir utilizará os conceitos de Orientação a Objeto para criar a lista. 

Teremos duas classes: No e Lista. Inicialmente, criamos uma Classe No e ela será a nossa base para a alocação dinâmica e representará cada elemento da lista. Contém 2 (dois) atributos fundamentais: o campo dado para receber a informação e prox para referenciar o próximo objeto da nossa lista.

```java
public class No 
{ 
private String dado; private No prox; 
//Propriedades da classe 
public No getProx() { 
	return this.prox; 
} 
public void setProx(No prox) 
{ 
    this.prox = prox; 
} 
public String getDado() 
{ 
    return this.dado; 
} 
//Construtor da classe No 
public No(String dadonovo) { 
	dado = dadonovo; prox = null; 
} 
public No(String dadonovo, No ligacao) 
{ 
    dado = dadonovo; prox = ligacao; 
} 
}
```

Alguns conceitos importantes relacionados à atribuição de valores a objetos: 

No 

```java
n1 = new No(); 
```

//declara n1 como No, aponta para o nó criado 

```java
n1.Dado = “aa”; 
```

<a href="https://imgur.com/XOi2rF6"><img src="https://i.imgur.com/XOi2rF6.png" title="source: imgur.com" /></a>



```java
n2 = n1; //declara n2 como No e atribui o endereço de n1 a n2, tanto n1 quanto n2 apontam para o nó criado.
```

 <a href="https://imgur.com/cAbi0Cu"><img src="https://i.imgur.com/cAbi0Cu.png" title="source: imgur.com" /></a>



```java
n3 = new No(); //declara n3 como No, aponta para o nó criado 
```

```java
n3.Dado = “bb”; 
```

<a href="https://imgur.com/sq0zisE"><img src="https://i.imgur.com/sq0zisE.png" title="source: imgur.com" /></a>



```java
n1.Prox = n3; //atribui o endereco de n3 ao atributo Prox do nó n1. 
```

Assim o “prox” de n1 apontará para n3. O mesmo vale para n2, pois ele “aponta” para o mesmo endereço de n1. 

<a href="https://imgur.com/OHqQPal"><img src="https://i.imgur.com/OHqQPal.png" title="source: imgur.com" /></a>



A classe Lista possuirá três atributos principais: primeiro (indica o início da lista, declarado com o tipo No), último (indica o fim da lista, declarado com o tipo No) e nomeDaLista. 

Perceba que a lista é “composta” apenas de dois nós. Na verdade, é o que basta para manipularmos a lista e não precisamos conhecer o restante, pois a partir do primeiro podemos percorrer toda a lista, seguindo o conceito de que cada nó conhece o seu sucessor. Assim, o primeiro sabe qual é o próximo, sucessivamente até chegarmos ao último. 



**3/4-Stack(pilha) e Queue(fila)**

Stacks são estruturas de dados lineares que seguem o princípio LIFO, ou seja, *last in first out* . Isso significa simplesmente que a inserção de um novo nó e a remoção de um nó ocorrem a partir do final. Isso é conhecido como o topo na terminologia da pilha. As operações são chamadas de push e pop para inserção e exclusão, respectivamente.

As pilhas são estruturas de dados extremamente úteis usadas amplamente em ciência da computação para chamadas de funções recursivas. Eles também são usados quando o controle passa de um ponto de um programa para outro para armazenar os endereços de retorno.

As filas, por outro lado, seguem o princípio FIFO, que é o primeiro a entrar, primeiro a sair. Eles representam uma fila real na vida real, onde as pessoas que entram primeiro são atendidas primeiro e assim por diante. A operação de inserção é conhecida como *enfileiramento* e a exclusão é conhecida como *desenfileiramento* . As filas também são extremamente populares na rede, bem como no design do sistema. Eles são amplamente utilizados para controlar o acesso aos recursos. Um bom exemplo é uma impressora de escritório. Você pode ter usado uma impressora de rede para imprimir documentos e isso usa uma fila internamente para que várias pessoas possam solicitar ao mesmo tempo, mas serão processadas sequencialmente.

**Operações de pilha - Push e pop**

<a href="https://imgur.com/TpM1o4i"><img src="https://i.imgur.com/TpM1o4i.png" title="source: imgur.com" /></a>

Primeiro, temos pilhas. Implementá-los em Java é bastante simples, então você vai gostar de tentar isso. Em primeiro lugar, crie uma classe e nomeie-a como Pilha. Temos três variáveis que determinam o tamanho da pilha, os próprios elementos e o elemento superior.

Temos um construtor que é usado para inicializar a pilha com o valor de tamanho máximo. Depois disso, um array desse tamanho é criado e top é inicializado com -1. Você pode estar pensando por que top é inicializado com -1. Lembre-se que Java usa indexação baseada em zero, o que significa que o primeiro elemento estaria no índice 0, o segundo estaria no índice 1 e assim por diante.

Agora, vamos dar uma olhada nas operações de inserção e exclusão, mais popularmente conhecidas como push e popping.

<a href="https://imgur.com/aqCXFO8"><img src="https://i.imgur.com/aqCXFO8.png" title="source: imgur.com" /></a>

Vamos começar olhando para o push. A função aceita um valor inteiro que deve ser colocado na pilha. Neste ponto, verifique se o topo está apontando para maxSize – 1, o que significa que a pilha estaria cheia e não podemos inserir. Se não estiver cheio, incrementamos o valor superior e inserimos o item nesse índice no array.

Popping é uma operação muito mais fácil. Primeiro verificamos se top é igual a -1, que é a condição inicial da pilha estar vazia. Se for esse o caso, não podemos tirar nada disso. Caso contrário, imprimimos o elemento que está atualmente no topo e o decrementamos. A função peek é simplesmente uma função utilitária que nos permite ver qual elemento está no topo atualmente.

<a href="https://imgur.com/82g2klT"><img src="https://i.imgur.com/82g2klT.png" title="source: imgur.com" /></a>

O seu deve ficar um pouco assim.

Confira o código do driver acima para criar uma pilha de tamanho 3. Inserimos 3 elementos nela, após os quais nenhuma inserção é possível. Na última linha, destacamos o elemento superior. O diagrama abaixo é uma visualização útil de todo o processo. Uma vez que top é igual a 2 (que é maxSize – 1), não podemos inserir mais elementos. Quando chamamos a função pop, o elemento mais alto é excluído e o valor de top é decrementado em 1.

<a href="https://imgur.com/iPOwvyl"><img src="https://i.imgur.com/iPOwvyl.png" title="source: imgur.com" /></a>



## **Operações de fila – Enfileirar e desenfileirar**

<a href="https://imgur.com/1u0LOyG"><img src="https://i.imgur.com/1u0LOyG.png" title="source: imgur.com" /></a>

A fila é muito semelhante à classe de pilha que vimos anteriormente. Em vez de top, temos frente e traseira. Isso porque, em uma fila, a inserção acontece por trás e a exclusão acontece pela frente. Então temos um array para a própria fila, o tamanho máximo, e também uma contagem do número de itens. Temos quatro funções de utilidade, conforme mostrado abaixo:

<a href="https://imgur.com/X3sVL6T"><img src="https://i.imgur.com/X3sVL6T.png" title="source: imgur.com" /></a>

Eles são bem autoexplicativos. Espreitar é usado para visualizar o item atual na parte traseira e frontal. CheckEmpty e checkFull é usado para verificar se a fila tem algum item ou não. Agora vamos entrar na implementação real das operações de enfileiramento e desenfileiramento.

<a href="https://imgur.com/cTyQmXA"><img src="https://i.imgur.com/cTyQmXA.png" title="source: imgur.com" /></a>

A função enqueue pega o elemento a ser inserido e verifica se a fila está cheia, antes de inseri-lo na retaguarda. Isso é feito incrementando o ponteiro traseiro e anexando-o a esse índice. Também incrementamos o número de itens em 1.

A função dequeue, que verifica se a fila está vazia usando a função utilitária que vimos anteriormente e, caso contrário, exibe o elemento atualmente na frente e o diminui em um. Como antes, também diminuímos o número de itens na fila em 1.

<a href="https://imgur.com/g6iCldm"><img src="https://i.imgur.com/g6iCldm.png" title="source: imgur.com" /></a>

Assim como fizemos anteriormente, confira o código do driver acima para criar uma fila de tamanho 3. Vamos inserir 3 elementos nela, após o que a fila fica cheia. Em seguida, removeremos um elemento também. A visualização abaixo ajudará você a entender melhor o processo.

<a href="https://imgur.com/SjnecXt"><img src="https://i.imgur.com/SjnecXt.png" title="source: imgur.com" /></a>

<a href="https://imgur.com/wSUskPs"><img src="https://i.imgur.com/wSUskPs.png" title="source: imgur.com" /></a>



**5- Graph**

Um graph é uma estrutura de dados que armazena dados conectados. Em outras palavras, um grafo G (ou g) é definido como um conjunto de vértices (V) e arestas (E) que conectam vértices. Os exemplos de gráfico são uma rede de mídia social, rede de computadores, Google Maps, etc.

Cada grafo consiste em arestas e vértices (também chamados de nós). Cada vértice e aresta têm uma relação. Onde vértice representa os dados e aresta representa a relação entre eles. Vértice é denotado por um círculo com um rótulo sobre eles. As arestas são indicadas por uma linha que conecta os nós (vértices).

**Terminologia do graph**
Vértice: Os vértices são o ponto que une as arestas. Ele representa os dados. Também é conhecido como nó. É indicado por um círculo e deve ser rotulado. Para construir um grafo deve haver pelo menos um nó. Por exemplo, casa, ponto de ônibus, etc.

Aresta: Uma aresta é uma linha que liga dois vértices. Representa a relação entre os vértices. As arestas são indicadas por uma linha. Por exemplo, um caminho para o ponto de ônibus de sua casa.

Peso: Está rotulado até a borda. Por exemplo, a distância entre duas cidades é de 100 km, então a distância é chamada de peso para a borda.

Caminho: O caminho é uma maneira de chegar a um destino a partir do ponto inicial em uma sequência.

## Implementação do Java Graph

A implementação Java de um Graph tem um método de instância .addVertex() que recebe dados e cria um novo vértice, que ele adiciona aos vértices. O método retorna o novo Vertex.

```java
public Vertex addVertex(String data) {
  Vertex newVertex = new Vertex(data);
  this.vertices.add(newVertex);
  return newVertex;
}
```

**Adicionando uma borda**
A implementação Java de um Graph tem um método de instância .addEdge() que recebe vertexOne, vertexTwo e weight e não retorna nada. Ele adiciona uma aresta de vertexOne a vertexTwo e, se o grafo for direcionado, adiciona uma aresta de vertexTwo a vertexOne. Se o gráfico for ponderado, ele adiciona peso a cada aresta.

```java
public void addEdge(Vertex vertex1, Vertex vertex2, Integer weight) {
  if (!this.isWeighted) {
    weight = null;
  }
  vertex1.addEdge(vertex2, weight);
  if (!this.isDirected) {
    vertex2.addEdge(vertex1, weight);
  }
}
```

**Visão geral do gráfico**
Uma classe Graph implementada em Java possui os seguintes atributos:

3 variáveis de instância privada:

- ArrayList vertices
- booleano isWeighted
- boolean isDirected

Um construtor com parâmetros vertices, isWeighted e isDirected que atualiza as variáveis de instância correspondentes apropriadamente:

- um método .addVertex() que adiciona um vértice ao gráfico
- um método .removeVertex() que remove um vértice do gráfico
- um método .addEdge() que adiciona uma aresta ao gráfico
- um método .removeEdge() que remove uma aresta do gráfico

```java
import java.util.ArrayList;
public class Graph {  
    private ArrayList<Vertex> vertices;  
    private boolean isWeighted;  
    private boolean isDirected;
public Graph(boolean inputIsWeighted, boolean inputIsDirected) {    
    this.vertices = new ArrayList<Vertex>();    
    this.isWeighted = inputIsWeighted;    
    this.isDirected = inputIsDirected;  
}
public Vertex addVertex(String data) {    
    Vertex newVertex = new Vertex(data);    
    this.vertices.add(newVertex);    
    return newVertex;  
}
public void addEdge(Vertex vertex1, Vertex vertex2, Integer weight) {    
    if (!this.isWeighted) {      
        weight = null;    
    }    
    vertex1.addEdge(vertex2, weight);    
    if (!this.isDirected) {      
        vertex2.addEdge(vertex1, weight);    
    }  
}
public void removeEdge(Vertex vertex1, Vertex vertex2) {    
    vertex1.removeEdge(vertex2);
    if (!this.isDirected) {      
        vertex2.removeEdge(vertex1);    
    }  
}
public void removeVertex(Vertex vertex) {    
    this.vertices.remove(vertex);  
}
public ArrayList<Vertex> getVertices() {    
    return this.vertices;  
}
public boolean isWeighted() {    
    return this.isWeighted;  
}
public boolean isDirected() {    
    return this.isDirected;  
}
public Vertex getVertexByValue(String value) {    
    for(Vertex v: this.vertices) {       
        if (v.getData() == value) {        
            return v;      
        }    
    }
    return null;  
}	  
public void print() {    
    for(Vertex v: this.vertices) {      
        v.print(isWeighted);    
    }  
}	
}
```

## **6- Set**

Existem dois tipos principais de conjuntos:

- **HashSet:** Elementos podem ser basicamente qualquer coisa.
- **TreeSet:** Os elementos devem ser comparáveis e a iteração é feita sobre os elementos em ordem de classificação.

Se você usar Set.of ou Set.copyOf para criar um conjunto, você não saberá que tipo de conjunto obteve, e não há garantia de que os elementos sejam iterados em nenhuma ordem específica.

```java
// Crie conjuntos de tamanho fixo e somente leitura (imutáveis)
Set.of(1, 13, 8)        // {1, 13, 8}
Set.of()                // {}

// Crie conjuntos imutáveis que podem crescer ou diminuir
var s = new HashSet<Integer>();
var t = new TreeSet<Integer>();

// Adicionando
s.add(3)                // s is {3}
s.add(5)                // s is {3, 5}
t.add(5)                // t is {5}
t.add(8)                // t is {5, 8}
t.add(13)               // t is {5, 8, 13}
s.addAll(t)             // s is {3, 5, 8, 13} (set "union")
s.size()                // 4

// Removendo
s.remove(5)             // s é {3, 8, 13}
s.remove(55)            // s ainda é {3, 8, 13} nenhum dano
s.removeAll(t)          // s is {3} (set "difference")
s.size()                // 1
s.isEmpty()             // false
s.clear()               // s is {}
s.isEmpty()             // true

// Testa de associação
t                       // {5, 8, 13}
t.contains(8)           // true
t.contains(21)          // false

// Iteração
for (var e: t) {
  // Faça algo com e
}

// Imprimindo
System.out.println(t)   // prints [5, 8, 13]
```



------

# **Projeto Java**

Olá pessoal, agora que já entendemos o que são estruturas de dados, podemos começar a implementar essas estruturas dentro do nosso projeto.

Por exemplo, podemos ter a necessidade de buscar as contas dos clientes, para isso precisaríamos utilizar uma estrutura de dados que pode ser o ArrayList():

Collection listaContas contendo Objetos do tipo Conta

```java
  private ArrayList<Conta> listaContas = new ArrayList<Conta>();
```

E a sua utilização ficaria dessa forma:

Método para buscar a Conta na Collection:

```java
public Conta buscarNaCollection(int numero) {

for (var conta : listaContas) {

	if (conta.getNumero() == numero) {

	return conta;
}
}
return null;
}
```

Assim podemos verificar as Contas que forma criadas fazendo uso de uma estrutura de dados.