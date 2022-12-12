<h1>Collections (Coleções)</h1>

As informações passadas neste documento norteia os conceitos da Oracle e podemos encontrar através deste link:

<div align="left"><a href="https://docs.oracle.com/javase/8/docs/api/"><img src="https://i.imgur.com/DYnNz6q.png" title="source: imgur.com" width="10%"/>Oracle</a></div>

A linguagem Java suporta arrays para armazenar vários objetos. Uma matriz é inicializada com um tamanho predefinido durante a instanciação. Para suportar estruturas de dados mais flexíveis, o Java fornece a **Classe Collections** (coleção). 

Uma Coleção é uma estrutura de dados que contém e processa um conjunto de dados. Os dados armazenados na coleção são encapsulados e o acesso aos dados só é possível por meio de métodos predefinidos. 

**Exemplo:** A pessoa desenvolvedora pode adicionar elementos a uma coleção por meio de um método. As coleções usam matrizes internas para o armazenamento, mas ocultam do desenvolvedor a complexidade de gerenciar o tamanho dinâmico.

As Coleções oferecem formas diferentes de armazenar os dados com base em fatores como:

- Eficiência no acesso, na busca ou na inserção;
- Forma de organização dos dados;
- Forma de acesso, busca e inserção dos dados

<h2>1. A Classe Collections</h2>

O Java oferece uma biblioteca de classes e interfaces (no pacote java.util.*), que implementa as principais estruturas de dados de forma reutilizável (usando apenas duas interfaces comuns). Além disso, oferece implementações de cursor para iteração (Iterator Pattern) para extrair dados de qualquer estrutura usando uma única interface e implementações de métodos estáticos utilitários para manipulação de coleções e vetores.

As Coleções não suportam primitivos (int, float, double, entre outros), somente se forem empacotados dentro de objetos ou se forem utilizadas as Classes Wrappers para converter os primitivos em Objetos:

**Classes Wrappers**

| **Tipo Primitivo** | **Tamanho**                 | **Wrapper** |
| ------------------ | --------------------------- | ----------- |
| **boolean**        | *true* ou *false*           | Boolean     |
| **char**           | 16  bits                    | Character   |
| **byte**           | 08  bits                    | Byte        |
| **short**          | 16  bits                    | Short       |
| **int**            | 32  bits                    | Integer     |
| **long**           | 64  bits                    | Long        |
| **float**          | 32  bits                    | Float       |
| **double**         | 64  bits                    | Double      |
| **void**           | Não  retorna valor          | Void        |
| **String**         | **Não é um tipo primitivo** |             |

> **Wrapper:** Vem do verbo inglês “wrap” que  significa envolver. São Classes que adicionam funcionalidades a aos  tipos primitivos. A Classe Wrapper transforma um primitivo em Objeto e  adiciona Métodos.
>
> **Exemplo:**
>
> ```
> Integer numeroInteiro = Integer.valueOf(2);
> ```
>
> Neste exemplo está sendo criado um **Objeto da Classe wrapper Integer**, chamado **numeroInteiro**, contendo valor 2.

Nos Organogramas abaixo, temos uma visão geral da Classe Collections:

**Collections - Parte 01**

<div align="center"><img src="https://i.imgur.com/PHjCJzj.png" title="source: imgur.com" /></div>

A interface **List** estende-se da interface Collection. **Os elementos em uma lista são ordenados como uma sequência**. O usuário pode utilizar o  número do índice para acessar um determinado elemento da lista, ou seja, o usuário tem controle total sobre qual elemento está inserido na  lista. A Interface List é como um array de tamanho variável.

A interface **Queue** estende a interface Collection. A Fila é a implementação da interface da estrutura de dados da fila. Como a fila em java é uma  interface, ela não tem uma definição dos métodos, apenas as suas assinaturas. A fila é normalmente uma estrutura primeiro a entrar, primeiro a sair (FIFO - First in, First out), embora esse não seja o caso de PriorityQueue. Você pode visualizá-lo como uma fila de pessoas em um balcão, a pessoa  que entra primeiro recebe os serviços primeiro e sai primeiro.

A interface **Set** estende a interface Collection. O Conjunto é uma estrutura que modela a definição matemática de um conjunto de dados. É uma coleção de objetos, que **não permite objetos duplicados**. O conjunto permite no máximo um  elemento nulo. 

**Collections - Parte 02**

<div align="center"><img src="https://i.imgur.com/zuFuBH4.png" title="source: imgur.com" width="75%"/></div>

A interface **Map** define um array associativo, isto é, ao invés de números, objetos são usados como chaves para se recuperar os elementos. As chaves não podem se repetir (seguindo o mesmo princípio da interface Set), mas os valores podem ser repetidos para chaves diferentes. Um Map também não possui necessariamente uma ordem definida para percorrer a coleção. 

<h2>2. Iterator</h2>

A interface **Iterable** é a raiz de toda a hierarquia de coleção, o que  significa que cada classe e interface a implementa. A função principal  de um iterador é permitir que o usuário percorra todos os objetos da  classe de coleção como se fossem sequências simples de itens de dados.

<h2>3. A Collection ArrayList</h2>

Em nosso curso, vamos estudar a Collection List, Subclasse ArrayList. A Collection ArrayList é a escolha natural quando for necessário usar um vetor redimensionável, que é muito mais eficiente para leitura, por ser implementado internamente com vetores, o que a torna ideal para o acesso aleatório aos dados armazenados.

<h3>3.1. Principais Métodos da Interface List</h3>

| **Método**             | **Descrição**                                                |
| ---------------------- | ------------------------------------------------------------ |
| **add(Objeto)**        | Adiciona  um objeto no final da lista.                       |
| **add(Indice,Objeto)** | Adiciona  um objeto na posição indicada (empurra elementos existentes para a frente) |
| **get(Indice)**        | Recupera  um objeto pelo índice.                             |
| **indexOf(Objeto)**    | Procura  um objeto e retorna índice da primeira ocorrência do objeto. |
| **set(Indice,Objeto)** | Grava  um objeto na posição indicada (apaga qualquer outro que ocupava a posição). |
| **remove(Indice)**     | Apaga  o objeto armazenado na posição indicada pelo índice.  |
| **clear()**            | Limpa  a lista                                               |
| **size()**             | Retorna  o tamanho da lista (numero de elementos armazenados). |
| **isEmpty()**          | Retorna  true se a lista está vazia.                         |
| **contains(Objeto)**   | Retorna  true se  existe uma ocorrência do elemento na lista. |

<h2>4. Exemplo com Array List - Lista de notas</h2>

```java
package com.generation.arraylist;

import java.util.ArrayList;
import java.util.Collections;

public class TestaArray {

	public static void main(String[] args) {

		// Cria um Objeto Wrapper Double
		Double y = Double.valueOf(9);

		// Cria a Collection ArrayList notas
		ArrayList<Double> notas = new ArrayList<Double>();

		// Adiciona as Notas. Observe que a primeira nota é o Objeto Wrapper Double
		notas.add(y);
		notas.add(7.0);
		notas.add(5.0);
		notas.add(4.0);
		notas.add(10.0);

		// Mostra na tela todas as notas inseridas
		System.out.println("\nNotas cadastradas: " + notas.toString());

		// Mostra a posição (indice) de uma determinada nota
		// Caso exista 2 notas iguais será exibida a posição da primeira nota
		// encontrada
		System.out.println("\nA posição da nota 5 é: " + notas.indexOf(5d));

		// Mostra uma determinada nota existe na lista
		System.out.println("\nA nota 5 existe na lista? " + notas.contains(5d));

		// Mostra a nota inserida em uma determinada posição (indice)
		System.out.println("\nNa posição 1 da lista, a nota é: " + notas.get(1));

		// Altera a nota 5.0 para 6.0 e exibe que a alteração foi efetuada
		notas.set(notas.indexOf(5d), 6.0d);
		System.out.println("\nA nota 5 foi alterada para 6: " + notas.toString());

		// Apaga a nota 4.0 e exibe que a exclusão foi efetuada
		notas.remove(notas.indexOf(4.0d));
		System.out.println("\nA nota 4 foi apagada: " + notas.toString());

		// Checa se a lista está vazia
		System.out.println("\nA lista está vaiza? " + notas.isEmpty());

		// Exibe o tamanho da lista (numero de elementos)
		System.out.println("\nO tamanho da lista é: " + notas.size());

		// Exibe o maior valor da lista
		System.out.println("\nA maior nota da lista é: " + Collections.max(notas));

		// Exibe o menor valor da lista
		System.out.println("\nA menor nota da lista é: " + Collections.min(notas));

		// Limpa a lista
		notas.clear();
		System.out.println("\nA lista está vazia: " + notas.toString());
	}

}

```

<br /><br />

------



<h1>Projeto Conta Bancária</h1>

Na etapa anterior, implementamos a Interface ContaRepository, que forneceu os Métodos para manipular os Objetos das Classes ContaCorrente e ContaPoupanca. 

Agora vamos implementar a classe ContaController, que irá ficar dentro da camada controller que irá criar uma lista de contas que irá conter dentro dela objetos do tipo Conta. Além disso ela terá os métodos de fazer a busca de conta pelo seu número (procurarContaPorNumero()), o método de listar todas as contas (listarTodas()), método de cadastrar na conta (cadastrar()), o método de atualizar os dados da conta (atualizar()), o método de apagar a conta (deletar()), os métodos de sacar, depositar, transferir, alpem de alguns métodos auxiliares como o de gerar automaticamente o número da conta (gerarNumero()), o método de buscar a conta na Collection (buscarNaCollection()) e o método para retornar o tipo da conta (retornaTipo()). 

O Diagrama de Classes do nosso Projeto ficará da seguinte forma:

+ ```mermaid
  classDiagram
  class Conta {
  <<Abstract>>
  
    - numero : int
    - agencia : int
    - tipo : int
    - titular : String
    - saldo : float
  
    + int getNumero()
    + int getAgencia()
    + int getTipo()
    + String getTitular()
    + float getSaldo()
    + void setNumero(int numero)
    + void setAgencia(int agencia)
    + void setTipo(int tipo)
    + void setTitular(String titular)
    + void setSaldo(float saldo)
    + boolean sacar(float valor)
    + void depositar(float valor)
    + void visualizar()
      }
      class ContaCorrente {
  
    - limite : float
  
    + float getLimite()
    + void setLimite(float limite)
    + boolean sacar(float valor)
    + void visualizar()
      }
      class ContaPoupanca {
  
    - aniversario : int
  
    + int getAniversario()
    + void setAniversario(int aniversario)
    + void visualizar()
      }
      class ContaRepository{
      << Interface >>
  + void procurarPorNumero(int numero)
  + void listarTodas()
  + void cadastrar(Conta conta)
  + void atualizar(Conta conta)
  + void deletar(int numero)
  + void sacar(int numero, float valor)
  + void depositar(int numero, float valor)
  + void transferir(int numeroOrigem, int numeroDestino, float valor)
    }
    Conta <|-- ContaCorrente
    Conta <|-- ContaPoupanca
  ```

  <h2>👣 Passo 01 - Implementar a Classe ContaController</h2>
  
  1. Crie o Pacote controller;
  2. Crie a Classe ContaController;
  3. Insira o código abaixo na Classe:
  
  
  
  ```java
  package conta.controller;
  
  import java.util.ArrayList;
  
  import conta.model.Conta;
  import conta.repository.ContaRepository;
  
  public class ContaController implements ContaRepository {
  /**
   *  Collection listaContas contendo Objetos do tipo Conta
   * */
  private ArrayList<Conta> listaContas = new ArrayList<Conta>();
  
  /**
   *  Procurar Conta por numero
   * */
  @Override
  public void procurarPorNumero(int numero) {
      var conta = buscarNaCollection(numero);
  	
  	if (conta != null)
  		conta.visualizar();
  	else
  		System.out.println("\nA Conta número: " + numero + " não foi encontrada!");
  }
  
  /**
   *  Método Listar todas as Contas
   * */
  @Override
  public void listarTodas() {
      for (var conta : listaContas) {
  		conta.visualizar();
  	}        
  }
  
  /** 
   * Método Cadastrar no Conta
   * */
  @Override
  public void cadastrar(Conta conta) {
  	listaContas.add(conta);
  	System.out.println("\nA Conta número: " + conta.getNumero() + " foi criada com sucesso!");
  }
  
  /**
   * Atualizar dados da Conta
   * */
  @Override
  public void atualizar(Conta conta) {
      var buscaConta = buscarNaCollection(conta.getNumero());
  	
  	if (buscaConta != null) {
  		listaContas.set(listaContas.indexOf(buscaConta), conta);
  		System.out.println("\nA Conta numero: " + conta.getNumero() + " foi atualizada com sucesso!");
  	}else
  		System.out.println("\nA Conta numero: " + conta.getNumero() + " não foi encontrada!");
  }
  
  /**
   *  Apagar Conta
   * */
  @Override
  public void deletar(int numero) {
      var conta = buscarNaCollection(numero);
  	
  	if (conta != null) {
  		if(listaContas.remove(conta) == true)
  			System.out.println("\nA Conta numero: " + numero + " foi deletada com sucesso!");
  	}else
  		System.out.println("\nA Conta numero: " + numero + " não foi encontrada!");
  }
  
  @Override
  public void sacar(int numero, float valor) {
      var buscaConta = buscarNaCollection(numero);
  	
  	if (buscaConta != null) {
  		
  		if(listaContas.get(listaContas.indexOf(buscaConta)).sacar(valor) == true)
  			System.out.println("\nO Saque na Conta numero: " + numero + " foi efetuado com sucesso!");		
  	
  	}else
  		System.out.println("\nA Conta numero: " + numero + " não foi encontrada!");
      
  }
  
  @Override
  public void depositar(int numero, float valor) {
      var buscaConta = buscarNaCollection(numero);
  	
  	if (buscaConta != null) {
  		var indiceConta = listaContas.indexOf(buscaConta);
  		listaContas.get(indiceConta).depositar(valor);
  		System.out.println("\nO Depósito na Conta numero: " + numero + " foi efetuado com sucesso!");
  	}else
  		System.out.println("\nA Conta numero: " + numero + " não foi encontrada ou a Conta destino não é uma Conta Corrente!");
  }
  
  @Override
  public void transferir(int numeroOrigem, int numeroDestino, float valor) {
      var buscaContaOrigem = buscarNaCollection(numeroOrigem);
  	var buscaContaDestino = buscarNaCollection(numeroDestino);
  
  	if (buscaContaOrigem != null && buscaContaDestino != null) {
  						
  			if (listaContas.get(listaContas.indexOf(buscaContaOrigem)).sacar(valor) == true) {
  				listaContas.get(listaContas.indexOf(buscaContaDestino)).depositar(valor);
  				System.out.println("\nA Transferência foi efetuado com sucesso!");
  			}
  	}else
  		System.out.println("\nA Conta de Origem e/ou Destino não foram encontradas!");
  }
  
  /** 
   * Métodos Auxiliares
   **/
  
  /**
   * Método para gerar automaticamente o Número da Conta
   * */
  public int gerarNumero() {
  	return listaContas.size() + 1;
  }
  
  /**
   * Método para buscar a Conta na Collection
   * */
  public Conta buscarNaCollection(int numero) {
  	for (var conta : listaContas) {
  		if (conta.getNumero() == numero) {
  			return conta;
  		}
  	}
  	
  	return null;
  }
  
  /**
   * Método para retornar o Tipo da Conta
   * */
  public int retornaTipo(int numero) {
  	for (var conta : listaContas) {
  		if (conta.getNumero() == numero) {
  			return conta.getTipo();
  		}
  	}
  	
  	return 0;
  }
  ```
  
  }

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>
