<h1>Interfaces</h1>

As informações passadas neste documento norteia os conceitos da Oracle e podemos encontrar através deste link:

<div align="left"><a href="https://docs.oracle.com/javase/8/docs/api/"><img src="https://i.imgur.com/DYnNz6q.png" title="source: imgur.com" width="10%"/>Oracle</a></div>

Como vimos no conteúdo sobre  Herança, Java permite a criação de uma Classe herdando as características de outra Classe, chamada Superclasse, com objetivo de simplificar o processo de desenvolvimento através da reutilização de código.

Entretanto, a linguagem Java não permite que uma classe seja derivada de duas ou mais classes (Polimorfismo), como no exemplo demonstrado na figura abaixo, ou seja, Java não permite a utilização do conceito de **Herança Múltipla**.

```mermaid
classDiagram
class Automovel {
+ anda() 
}
class Barco {
+ navega() 
}
class Anfibio {
 
}

Automovel <|-- Anfibio
Barco <|-- Anfibio
```

> •**Herança Simples** é o princípio, implementado em todas as linguagens de programação orientadas a objetos, que possibilita o compartilhamento de atributos e operações de apenas uma classe em uma subclasse. 
>
> •**Herança Múltipla** é o princípio, implementado em algumas linguagens de programação orientadas a objetos, como a liguagem C++ por exemplo, que possibilita o compartilhamento de atributos e operações de duas ou mais classes em uma subclasse, ou seja, uma classe pode ter mais de um superclasse.

Para contornar este fato, a Linguagem Java oferece uma solução elegante para este fim: o conceito de **Interfaces**, onde um Objeto "implementa" as características de outro Objeto.

```mermaid
classDiagram
class Automovel {
+ anda() 
}
class VeiculoAquatico {
<< Interface >>
+ navega() 
}
class Anfibio {
 
}

Automovel <|-- Anfibio
VeiculoAquatico <-- Anfibio : Implementa
```

**Interface** é uma estrutura que representa uma **Classe abstrata "pura"** em Java, que **não têm atributos de dados** (só pode ter constantes estáticas - tipo final), **não tem construtor**, **todos os métodos são abstratos** e **não é declarada como Classe, e sim como Interface**.

Uma Classe pode implementar várias Interfaces, entretanto não é recomendável implementar mais do que 3 Interfaces, porquê pode criar uma complexidade desnecessária ao projeto.

A Interface estabelece **um conjunto de Métodos apenas assinados, ou seja, sem o corpo, que obrigatoriamente devem ser implementados nas Subclasses que a utiliza**. Abaixo vemos a sintaxe de como criar uma Interface:

<div align="center"><img src="https://i.imgur.com/iCNxCVS.png" title="source: imgur.com" /></div>

Na imagem abaixo, vemos a sintaxe de como implementar uma Interface em uma Classe. Observe que as classes utilizam a palavra reservada **implements** na sua assinatura para implementar uma interface.

<div align="center"><img src="https://i.imgur.com/8gdtS8V.png" title="source: imgur.com" /></div>

Vamos ao nosso exemplo:

<div align="center"><img src="https://i.imgur.com/kC6TY2u.png" title="source: imgur.com" /></div>

Observe que **Corredor, Nadador e Ciclista** estendem (herdam) a Classe Atleta. Vamos acrescentar a **Classe Triatleta**.

<div align="center"><img src="https://i.imgur.com/qXuhfKj.png" title="source: imgur.com" /></div>

Na imagem acima, vemos que a Classe **Triatleta** estenderia (herdaria) as 3 Classes: **Corredor, Nadador e Ciclista**.

Teoricamente isto funcionaria, mas na prática não, pois Java **NÃO ACEITA HERANÇA MÚLTIPLA**. Para resolvermos o problema, teríamos que implementar o conceito de **Interfaces**, onde **Atleta, Nadador, Corredor e Ciclista**, seriam as nossas **Interfaces**, enquanto **Pessoa e Triatleta** seriam as únicas classes.

<div align="center"><img src="https://i.imgur.com/a0gsk7E.png" title="source: imgur.com" /></div>

<br />

Abaixo, vemos o Diagrama de Classes do exemplo acima:

<img src="https://i.imgur.com/vGDOChv.png" title="source: imgur.com" width="3%"/>**Exemplo 01 - Diagrama de Classes** 

```mermaid
classDiagram
class Pessoa {
- nome: String
+ String getNome()
+ void setNome(String nome)
}
class Triatleta {
+ void correr()
+ void pedalar()
+ void nadar()
}
class Atleta {
<< Interface >>
+ void aquecer()
}
class Ciclista {
<< Interface >>
+ void pedalar()
}
class Corredor {
<< Interface >>
+ void correr()
}
class Nadador {
<< Interface >>
+ void nadar()
}
Pessoa <|-- Triatleta: << extends >>
Atleta <|-- Ciclista: << extends >>
Atleta <|-- Corredor: << extends >>
Atleta <|-- Nadador: << extends >>
Ciclista <-- Triatleta: << implements >>
Corredor <-- Triatleta: << implements >>
Nadador <-- Triatleta: << implements >>
```

<br />

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 01 - Implementação em Java:** 

**Classe Pessoa**

```java
package triatleta;

public class Pessoa {

	private String nome;

	public Pessoa(String nome) {
		this.nome = nome;
	}

	public String getNome() {
		return nome;
	}

	public void setNome(String nome) {
		this.nome = nome;
	}
	
	public void cansou() {
		System.out.println("\nCansou...");
	}
}
```

A Classe Pessoa (Superclasse), foi criada com apenas um Atributo (nome), conforme o Diagrama de Classes acima. Também foi criado o Método Construtor, os Métodos Get e Set do Atributo e o Método cansou().

**Interface Atleta**


```java
package triatleta;

public interface Atleta {

	public void aquecer();
	
}

```

A Interface Atleta foi criada com apenas um Método (aquecer()), conforme o Diagrama de Classes acima. 

**Interface Ciclista**


```java
package triatleta;

public interface Ciclista extends Atleta {

	public void pedalar();
}
```

A Interface Ciclista foi criada como uma Herança da Classe Atleta, com apenas um Método (pedalar()), conforme o Diagrama de Classes acima. 

**Interface Corredor**


```java
package triatleta;

public interface Corredor extends Atleta {

	public void correr();
}

```

A Interface Corredor foi criada como uma Herança da Classe Atleta, com apenas um Método (correr()), conforme o Diagrama de Classes acima. 

**Interface Nadador**


```java
package triatleta;

public interface Nadador extends Atleta{

	public void nadar();
}

```

A Interface Nadador foi criada como uma Herança da Classe Atleta, com apenas um Método (nadar()), conforme o Diagrama de Classes acima. 

**Classe Triatleta**


```java
package triatleta;

public class Triatleta extends Pessoa implements Nadador, Corredor, Ciclista{

	public Triatleta(String nome) {
		super(nome);
		
	}

	@Override
	public void aquecer() {
		System.out.println("\nAquecendo...");
		
	}

	@Override
	public void pedalar() {
		System.out.println("\nPedalando...");
		
	}

	@Override
	public void correr() {
		System.out.println("\nCorrendo...");
		
	}

	@Override
	public void nadar() {
		System.out.println("\nNadando...");
		
	}

}
```

A Classe Triatleta foi criada como Herança da Classe Pessoa e Implementa as Interfaces: Nadador, Corredor e Ciclista, conforme o Diagrama de Classes acima. Além disso, também foi criado o Método Construtor. 

Observe que todos os Métodos das 3 Interfaces foram implementados. Quando uma Classe Implementa uma Interface, ela "assina um contrato" com a Interface, que a obriga a implementar ou minimamente inserir as assinaturas de todos os Métodos da Interface no Corpo da Classe.

**Classe TestaTriatleta**

```java
package meios_transporte;

public class TestaTriatleta {

	public static void main(String[] args) {

		Triatleta triatleta = new Triatleta("Kelvyn");
		
		triatleta.aquecer();
		triatleta.nadar();
		triatleta.pedalar();
		triatleta.correr();
		triatleta.cansou();

	}

}
```

Na Classe TestaTriatleta, foi instanciado um Objeto da Classe Triatleta. Observe que graças a Herança e as Interfaces implementadas, o Objeto da Classe Triatleta consegue executar os Métodos das 4 Interfaces e da Classe Pessoa. Abaixo, você confere o resultado do código no Console:

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```
Aquecendo...

Nadando...

Pedalando...

Correndo...

Cansou...
```

<br />

<h2>2. Interfaces x Classes Abstratas</h2>

| Classes Abstratas                                           | Interfaces                                                   |
| ----------------------------------------------------------- | ------------------------------------------------------------ |
| Agrupa objetos com implementações compartilhadas            | Agrupa objetos com implementações diferentes                 |
| Define novas classes através de herança (simples) de código | Define novas interfaces através de herança (múltipla) de **assinaturas** |
| Só uma Classe pode ter apenas uma Superclasse               | Uma Classe pode ter várias Interfaces como supertipo         |

<br />

<h2>3. Regras para usar Interface</h2>

Aqui estão alguns pontos-chave para definir uma interface em Java que devem ser mantidos em mente. As regras são as seguintes:

1. Uma interface não pode ser instanciada diretamente. Mas podemos criar uma referência a uma interface que pode apontar para um objeto de qualquer um de seus tipos derivados implementando-o.

2. Uma interface não pode ser declarada com a palavra-chave final.

3. Não pode ter variáveis de instância. Se declararmos uma variável em uma interface, ela deve ser inicializada no momento da declaração.

4. Uma classe que implementa uma interface deve fornecer suas próprias implementações de todos os métodos definidos na interface.

5. Não podemos reduzir a visibilidade de um método de interface durante a substituição. Ou seja, quando implementamos um método de interface, ele deve ser declarado como público.

6. Também pode ser declarado com corpo vazio (ou seja, sem membros). 

7. Uma interface de nível superior pode ser pública ou padrão com o modificador abstract em sua definição. Portanto, uma interface declarada com private, protected ou final gerará um erro em tempo de compilação.

8. Todos os métodos não padrão definidos em uma interface são abstratos e públicos por padrão. Portanto, um método definido com private, protected ou final em uma interface irá gerar um erro em tempo de compilação.

9. Se você adicionar qualquer novo método na interface, todas as classes concretas que implementam essa interface devem fornecer implementações para o método recém-adicionado porque todos os métodos na interface são abstratos por padrão.

<br />

## 🔑**Pontos chave:**

1.  **Interface** é uma estrutura que representa uma **Classe abstrata "pura"** em Java, que **não têm atributos de dados** (só pode ter constantes estáticas - tipo final), **não tem construtor**, **todos os métodos são abstratos** e **não é declarada como Classe, e sim como Interface**.
2. Uma Classe pode implementar várias Interfaces, entretanto não é recomendável implementar mais do que 3 Interfaces, porquê pode criar uma complexidade desnecessária ao projeto.
3. A Interface estabelece **um conjunto de Métodos apenas assinados, ou seja, sem o corpo, que obrigatoriamente devem ser implementados nas Subclasses que a utiliza**.

<br />

------

<h1>Projeto Conta Bancária</h1>

Na etapa anterior, implementamos a Classe Conta em uma Classe Abstrata. 

Nesta etapa, vamos criar a Interface ContaRepository, que fornecerá os Métodos para manipular os Objetos das Classes ContaCorrente e ContaPoupanca. Estes Métodos, posteriormente, serão implementados em uma Classe, de modo a manter os detalhes de implementação (Métodos Construtores, Get e Set, por exemplo), encapsulados na Classe e fornecer apenas as assinaturas dos Métodos necessários para criar, consultar, atualizar, apagar e efetuar as Operações Bancárias com os Objetos das Classes ContaCorrente e ContaPoupanca. O Diagrama de Classes do nosso Projeto ficará da seguinte forma:

```mermaid
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

<br />

<h2>👣 Passo 01 - Implementar a Interface ContaRepository</h2>

1. Crie o Pacote repository;
2. Crie a Interface ContaRepository;
3. Insira o código abaixo na Interface:

```java
package conta.repository;

import conta.model.Conta;

public interface ContaRepository {

	// CRUD da Conta
	public void procurarPorNumero(int numero);
	public void listarTodas();
	public void cadastrar(Conta conta);
	public void atualizar(Conta conta);
	public void deletar(int numero);
	
	// Métodos Bancários
	public void sacar(int numero, float valor);
	public void depositar(int numero, float valor);
	public void transferir(int numeroOrigem, int numeroDestino, float valor);
	
}
```

Observe que todos os Métodos da Interface foram apenas assinados, ou seja, nenhum foi implementado.

<br /><br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>