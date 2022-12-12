<h1>Programação Orientada a Objetos</h1>

As informações passadas neste documento norteia os conceitos da Oracle e podemos encontrar através deste link:

<div align="left"><a href="https://docs.oracle.com/javase/8/docs/api/"><img src="https://i.imgur.com/DYnNz6q.png" title="source: imgur.com" width="10%"/>Oracle</a></div>

Em geral, quanto maior o software, mais complexo é o seu desenvolvimento, devido às muitas partes que o compõem o todo e o inter-relacionamento entre estas partes. 

Uma razão frequente para as dificuldades de implementação, testes e manutenção é que, em geral, quando se segue uma lógica de projeto de software voltado apenas nas funcionalidades, o sistema é desenvolvido estruturado de acordo com o que ele faz, sem uma preocupação em representar o processo de uma maneira similar ao que acontece no mundo real, ou seja, no dia a dia.

O problema dessa abordagem é que, de tempos em tempos, as empresas mudam seus processos e procedimentos. Isso significa que, o software também terá que mudar e se ele foi todo estruturado de acordo com o que ele precisava fazer antes, pode ser que agora ele precise ser totalmente reestruturado ou ser refeito, a menos que façamos um POG "Programação Orientada a Gambiarras" para manter as coisas funcionando.

Entretanto, alguns desenvolvedores pensaram: "Se as funções de uma empresa e de um software mudam com muita frequência, eu não posso usá-las para basear a organização de meu programa". Essa foi a primeira grande conclusão dos fatos acima. A pergunta que levou à segunda grande conclusão foi: "Mas o que é que, em uma empresa e em seus processos, raramente muda?" Por sorte alguém conseguiu perceber coisas que raramente mudam: **as coisas!**

Como assim, as coisas? **Simples: tudo aquilo que é físico**. Existe uma grande constância no uso de formulários, na produção de um determinado produto, nos funcionários envolvidos em um procedimento, entre outros. As entidades são muito constantes, os objetos envolvidos na realização dos processos são, quase sempre, os mesmos. E disso surgiu a segunda grande conclusão: "Vamos basear a estrutura do software nos objetos envolvidos em seus processos e não nos processos em sí".

**Programação Orientada a Objetos** (POO) **é um paradigma de programação que ajuda a definir a estrutura de programas de computadores, baseado nos conceitos do mundo real, sejam eles reais ou abstratos.** A ideia é simular as coisas que existem e acontecem no mundo real no mundo virtual.

- O mundo real é composto de objetos que interagem entre si.
- Um modelo orientado a objetos é composto de objetos que interagem entre si.

> **Abstrato:** Algo que não é concreto; que resulta da abstração, que opera unicamente com ideias, com associações de ideias, não diretamente com a realidade sensível, que possui um alto grau de generalização 

Da teoria de sistemas, temos que um sistema é um conjunto de entidades que interagem entre si a fim de produzir um resultado comum. Assim, é natural o uso de "objetos programa" a fim de compor um sistema computacional.

<h2>1. Objetos</h2>

No mundo real, objetos podem ser animados ou inanimados, mas **qualquer um deles possui características que podem ser classificadas como atributos ou comportamentos**. Na imagem abaixo, vemos alguns exemplos de objetos:

<div align="center"><img src="https://i.imgur.com/MJIvLag.png" title="source: imgur.com" /></div>

Observe que nos exemplos acima cada Objeto foi definido de forma Genérica: Animal, Pessoa, Produto e Conta. Sabemos que a Conta é de uma Banco, mas não sabemos os detalhes da Conta como:

1) Quem é o titular da Conta?
2) Qual é o tipo da Conta?
3) Qual Banco a Conta pertence?
4) Qual é o numero da  Agência Bancária?

O Objeto Conta foi definido de uma forma Abstrata, com poucos ou nenhum detalhe. Nesta etapa, o foco é identificar os Objetos Genéricos, ou seja, uma generalização da Abstração.

Modelar um Sistema baseado em Objetos traz algumas vantagens:

- **Simplificação da concepção do sistema:** a transição da realidade para o modelo é
  facilitada.

- **Simplificação da compreensão do modelo:** como o modelo é mais próximo da realidade,
  a compreensão do modelo por quem compreende o problema real é quase automática.

- **Simplificação do Gerenciamento do sistema:** assim como na realidade, os objetos são
  estáveis na solução de um problema, ou seja, os objetos mudam muito pouco; quando é
  necessário resolver problemas ligeiramente diferentes, modificamos a forma com que os
  objetos interagem e não os objetos em si.

**O que são objetos em programação?**

Em programação (e, de certa forma também na vida real), um objeto é uma entidade caracterizada por um conjunto de operações e um estado, caracterizados por **funções e campos**, podendo ainda ser **compostos por outros Objetos**.

Note que um objeto é uma estrutura similar à uma "estrutura de dados"; porém, além de "dados", um objeto pode armazenar também "funções". Em um objeto os dados são chamados de **Atributos** e as funções são chamadas de **Métodos**.

<h2>2. Classes</h2>

Classes são como pequenos programas, que podem ser considerados novos tipos de dados. Uma classe pode ser considerada como um "molde" de um objeto, sendo uma descrição de como um objeto pode ser criado. Uma forma interessante de explicar é que uma classe está para um objeto assim como a planta de uma casa está para a casa. 

<div align="center"><img src="https://i.imgur.com/0zF5E7u.png" title="source: imgur.com" /></div>

Repare que a classe em si é um conceito abstrato, como um molde, que se torna concreto e palpável através da criação de um objeto. Chamamos essa criação de **Instanciação da Classe**, como se estivesse usando a Classe como molde para criar vários Objetos.

<div align="center"><img src="https://i.imgur.com/Q40v71w.png" title="source: imgur.com" /></div>

Na imagem acima vemos que uma Planta pode ser utilizada para construir N casas. Da mesma forma, uma Classe pode instanciar (criar) vários Objetos.

Como todo programa, uma classe é composta por algumas variáveis, que chamamos de **Atributos** e algumas funções que chamaremos de **Métodos**, conforme vimos no tópico anterior. 

Os **Atributos são responsáveis por identificar as características do Objeto**. Veja no exemplo abaixo:

<div align="center"><img src="https://i.imgur.com/xVM3Qpq.png" title="source: imgur.com" /></div>

Observe que definindo os Atributos do Objeto nós conseguimos identificar os detalhes da Conta e automaticamente conseguimos responder as perguntas. Cada classe deve representar um conceito (Conta, Pessoa, Animal, Produto) e um conceito pode ser descrito através dos seus Atributos (Conta: titular, tipo, banco, agencia e etc.).

Os **Métodos são responsáveis por definir as ações que irão modificar e/ou interagir com os Atributos**.

<div align="center"><img src="https://i.imgur.com/SKyQ6rN.png" title="source: imgur.com" /></div>

Observe no Diagrama acima, que ele identifica algumas ações que os Objetos Conta possuem (Sacar, Depositar, Transferir, Abrir conta e Fechar conta).

Observe também que os **Atributos são identificados por substantivos** e os **Métodos são identificados por verbos**.

Na Computação um Sistema Orientado a Objetos é visto como um conjunto de Objetos agrupados em Classes de Objetos similares que interagem através da troca de mensagens (Chamada dos Métodos). Cada **classe** é um **modelo** **estático** que permite especificar um conjunto de características do conceito que representa. Cada **objeto** é uma **entidade** **dinâmica** criada a partir de uma classe, que possui os dados sobre os quais são realizadas as operações disponíveis em sua Classe. **Todos os objetos são instâncias de uma classe, ou seja, é a materialização de um conceito formalizado**.

**Exemplo:** 

<div align="center"><img src="https://i.imgur.com/esIWB81.png" title="source: imgur.com" /></div>

**Conta** **é uma classe.**

**A Conta da Maria Joaquina e a Conta do João da Silva são instâncias da Classe Conta, ou seja, Objetos.**

<h3>2.1. Representação Gráfica</h3>

Para representar uma Classe graficamente na Orientação Objetos, utilizamos o **Diagrama de Classes**, que faz parte da **UML - Unified Model Language**, que é uma Linguagem de Modelagem Unificada para Sistemas Orientados a Objetos. Veja o Diagrama de Classes da nossa Classe Conta abaixo:

```mermaid
classDiagram
class Conta {
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
  + boolean saque(float valor)
  + void visualiza()
}
```

O Diagrama de Classes é organizado da seguinte forma:

<div align="center"><img src="https://i.imgur.com/7KSofpB.png" title="source: imgur.com" /></div>

- **Nome:** Nome da Classe.
- **Campos:** São os Atributos da Classe. Os Atributos devem vir acompanhados do seu tipo de dado.
- **Métodos:** São as ações da Classe. Os Métodos devem vir acompanhados do seu tipo de dado de saída e podem vir acompanhados do tipo de dado de entrada.

<h3>2.2. Visibilidade</h3>

A visibilidade merece um tópico a parte. A visibilidade ou Modificadores de acesso determina como Método (visto no capítulo anterior) ou Atributo será manipulado no decorrer do desenvolvimento do programa, ou seja, qual (is) Classes podem chamar o Método. Na tabela abaixo temos os Modificadores de visibilidade:

| **Modificador** | **Descrição**                                                | UML  |
| --------------- | ------------------------------------------------------------ | ---- |
| **padrão**      | Um Método ou Atributo padrão (identificado pela ausência de modificadores) poderá ser acessado por todas as classes que estiverem **no mesmo pacote**, que a classe que possui o Atributo. |      |
| **public**      | Um Método ou Atributo public poderá ser acessado por qualquer classe em qualquer pacote. O  acesso a um método só é permitido se você tiver primeiro acesso à classe (Pública). | +    |
| **protected**   | Um Método ou Atributo protected é protegido e pode ser chamado por todas as classes que compõe o pacote  **package**. A grande diferença para o modificador padrão é que uma classe (mesmo que esteja fora do pacote), que estende a Classe com o Atributo ou o Método protected, ela terá acesso a ele, logo o acesso é por pacote e por herança. | #    |
| **private**     | Um Método ou Atributo private possui o acesso restrito. Somente a Classe que o definiu pode acessá-lo, ou seja, um  método privado só poderá ser acessado dentro da classe que o definiu. | -    |

Observe que na coluna UML da tabela acima, temos o símbolo que identifica a visibilidade do Método. O mais comum na Modelagem de uma Classe é **manter os Atributos Private (-) e os Métodos Public (+)**.

Na imagem abaixo podemos visualizar a hierarquia dos modificadores:

<div align="center"><img src="https://i.imgur.com/NdEp3gV.png" title="source: imgur.com" /></div>

A imagem acima mostra o nível de visibilidade dos Atributos e Métodos, do nível de acesso mais restrito (Private) ao nível de acesso total e irrestrito (Public). Na tabela abaixo temos um resumo:

| Modificador   | Classe | Pacote | Sub Classe | Mundo |
| ------------- | :----: | :----: | :--------: | :---: |
| **public**    |   ✔    |   ✔    |     ✔      |   ✔   |
| **protected** |   ✔    |   ✔    |     ✔      |   ❌   |
| **padrão**    |   ✔    |   ✔    |     ❌      |   ❌   |
| **private**   |   ✔    |   ❌    |     ❌      |   ❌   |

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <div align="left"> **ATENÇÃO:** *Os Modificadores de acesso de um Atributo definem quais Classes poderão acessar o Atributo, da mesma forma que os Modificadores de acesso de um Método definem quais Classes terão acesso ao Método.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

**Exemplo - Classe Conta com os respectivos Atributos e Modificadores de Acesso:**

```java
public class Conta {

	private int numero;
	private int agencia;
	private int tipo;
	private String titular;
	private float saldo;
   
}
```



<h3>2.3. Método Construtor</h3>

Para criar (instanciar) um novo Objeto de uma Classe, precisamos implementar um Método para gerar este novo Objeto. O Método responsável por esta tarefa em uma Classe é o **Método Construtor**. 

**Um Método Construtor é um Método especial, definido para cada classe**. Entre as suas principais características, podemos destacar:

- Determina as ações associadas à **inicialização** de **cada objeto criado**.
- Toda vez que o programa instancia um novo Objeto da Classe, ele é o Método que será **invocado**. 
- A **assinatura de um construtor** diferencia-se das assinaturas dos outros métodos por não ter nenhum tipo de retorno (nem mesmo **void**).
- O **nome do construtor** deve ser o próprio **nome da classe**. 
- O construtor pode receber argumentos, como qualquer Método. Geralmente ele recebe variáveis com o mesmo nome doa Atributos da Classe.
- Toda **Classe tem pelo menos um construtor** sempre definido. 
- Se nenhum construtor for explicitamente definido pelo programador da classe, um construtor *default* (**0** para tipos numéricos primitivos, **false** para **boolean** e **null** para referências), que não recebe argumentos, é criado pelo compilador Java. 
- Se o programador da classe criar pelo menos um método construtor, o construtor *default* **não será** criado automaticamente - se ele o desejar, deverá criar um construtor sem argumentos explicitamente (Construtor de Objetos Nulos). 
- Usando o mecanismo de Sobrecarga (veremos este assunto no próximo tópico), mais de um construtor pode ser definido para oferecer diversas maneiras de inicializar os objetos dessa classe. 

**Exemplo - Método Construtor da Classe Conta:**

```java
	public Conta(int numero, int agencia, int tipo, String titular, float saldo) {
		this.numero = numero;
		this.agencia = agencia;
		this.tipo = tipo;
		this.titular = titular;
		this.saldo = saldo;
	}
```

Observe que o Método Construtor está definido com **public** para que as outras Classes tenham acesso ao Método e possam instanciar novos Objetos da Classe Conta.

Observe que em cada atributo foi adicionada a palavra reservada **this**. O motivo é simples: sempre que
os nomes das variáveis de um método forem iguais aos nomes dos atributos de uma classe, devemos usar a palavra **this** para **identificar o atributo**. Observe que os parâmetros do Método Construtor tem o mesmo nome e tipo dos atributos.

<h3>2.4. Métodos Get e Set</h3>

Os métodos GET e SET são **técnicas padronizadas para gerenciamento sobre o acesso dos atributos**. Nesses métodos determinamos quando será alterado um atributo e o acesso ao mesmo, tornando o controle e as modificações mais práticas e limpas,  sem a necessidade de alterar a assinatura do método usado para acessar o atributo. Estes Métodos são essenciais porquê os Atributos da Classe são privados e portanto só podem ser manipuladas por estes métodos da classe.

<h4>2.4.1. Métodos SET</h4>

Os métodos SET servem para modificar os atributos. Eles são chamados de setters. Se o nome do atributo é nome, o nome do setter será setIdade( int idade). Entre parênteses devemos indicar o novo valor desejado para o atributo (parâmetro). É recomendado que o setter valide os novos valores para variáveis de instância, inclusive retornando um valor ou mensagem para indicar que os dados são inválidos.

**Exemplo - Método set na Classe Conta:**

```java
	public void setNumero(int numero) {
		this.numero = numero;
	}
```

Observe que no atributo numero foi adicionada a palavra reservada **this**, porquê o nome da variável do método Set é igual ao nome do atributo da classe. Você deve criar um Método Set para cada Atributo da Classe.

<h4>2.4.2. Métodos GET</h4>

Agora já sabemos como mudar os valores dos atributos, vamos entender como ler os dados dos atributos. Os métodos GET servem para ler os dados dos atributos. Eles também são chamados de getters. Se o nome do atributo é nome, o nome do getter será getNome(). Observe que diferente do Método Set, ele não recebe parâmetro. Eles também são conhecidos como métodos de acesso ou métodos de consulta, porquê obtêm os valores dos atributos do Objeto.

**Exemplo - Método get na Classe Conta:**

```java
	public int getNumero() {
		return numero;
	}
```

Basicamente um Método get retorna o valor do atributo. 

Embora os métodos get e set possam fornecer acesso a dados private, o acesso é restringido pela implementação dos métodos feita pelo programador.

Qual a vantagem de usar getters e setters?
1. Se você não quiser que um atributo seja modificado por outras classes, remova o setter daquela variável.
2. Se você não quiser que um atributo seja lido por outras classes, remova o getter daquela variável.
3. O setter permite validar os dados antes de armazená-los, evitando que dados incorretos sejam colocados nos atributos.
4. O getter permite esconder o formato (tipo de dado) com que um atributo está armazenado.

<h2>3. Sobrecarga de Métodos</h2>

Sobrecarregar métodos significa ter vários métodos com nomes iguais, mas assinaturas diferentes. Veja o exemplo abaixo:

```java
	public Conta(int numero, int agencia, int tipo, String titular, float saldo) {
		this.numero = numero;
		this.agencia = agencia;
		this.tipo = tipo;
		this.titular = titular;
		this.saldo = saldo;
	}
	
	public Conta() { }
```

Observe que forma criados 2 Métodos Construtores:

- O primeiro com os parâmetros para serem preenchidos
- O segundo sem os parâmetros, com o objetivo de criar um Objeto vazio.

Graças a Sobrecarga de Métodos é possível ter várias versões de um Método recebendo diferentes tipos de parâmetros. Você pode aplicar a Sobrecarga em qualquer Método da sua Classe, **exceto o Método main**.

<h2>4. Encapsulamento</h2>

**Encapsular**, nada mais é do que proteger membros de uma classe de acesso externo, permitindo somente sua manipulação de forma indireta.  

Encapsular os dados de uma aplicação significa evitar que estes sofram acessos indevidos. Para isso, é criada uma estrutura que contém métodos que podem ser utilizados por qualquer outra classe, sem causar inconsistências no desenvolvimento de um código.

Na prática, isso é feito por meio de dois métodos: os getters e os setters, que forma vistos no tópico anterior. Os Métodos getters tem por objetivo retornar o valor que lhe foi pedido, mas de forma a não prejudicar a integridade do dado em si, enquanto os Métodos setters recebem como argumento uma informação, que pode ser qualquer tipo de dado suportados pela linguagem. Dessa forma, não haverá o risco de  ocorrerem acessos indevidos. Veja o exemplo abaixo:

Na Classe Conta, além dos Métodos Construtor, Getters e Setters, nós vamos criar um Método para sacar um valor da conta. Se os atributos puderem ser acessados diretamente em qualquer trecho do código, haverá o risco de o saldo ser alterado sem passar pelo método sacar(). Para evitar isso, podemos usar os métodos get e set para  evitar o acesso direto. Logo, **para proteger os atributos da Classe, principalmente o saldo, utilizamos os métodos get saldo e set saldo**. 

**Quais as vantagens de encapsular?**

Com base no fato de que o encapsulamento evita o acesso indevido a  alguns tipos de dados, diversas vantagens podem ser notadas, entre elas podemos destacar:

- **Manutenção de código:** Com o encapsulamento, **isso passa a ser mais fácil, uma vez que, com a devida proteção de acesso aos dados**, a pessoa desenvolvedora achará mais rápido algum ponto onde o código precisa ser melhorado. Sem o encapsulamento, seria bem difícil encontrar os pontos de inconsistência do código.
- **Reuso de código:** Com o encapsulamento, **o programa terá mais chances de ter o código reaproveitado** em outros projetos, poupando bastante tempo da equipe de desenvolvimento.
- **Desenvolvimento acelerado e simplificado:** O encapsulamento transforma a implementação de alguns códigos em uma espécie de caixa preta. Na prática, isso significa que **as classes externas não precisam acessar alguns dados de forma direta.** Assim, o desenvolvimento dos sistemas passa a ficar simplificado e acelerado.

<h2>5. Instanciando um Objeto</h2>

Para instanciar Objetos da Classe Conta, nós utilizaremos uma outra Classe chamada TestaConta. Nesta Classe nós iremos implementar um velho conhecido de vocês: O Método main()!

Abaixo, temos um exemplo de um Objeto da Classe Conta:

```java
package com.generation.conta;

import com.generation.conta.model.Conta;

public class TestaConta {

	public static void main(String[] args) {
		
	    Conta c1 = new Conta();
        c1.visualiza();
        
       	Conta c2 = new Conta(123456, 123, 1, "João da Silva", 2000.0f);
        c2.visualiza();
        
        c1.setSaldo(100000.0f);
        c1.setTitular("Maria Joaquina");
        c1.visualiza();

	}

}
```

Observe que foram criados 2 Objetos (c1 e c2) do tipo Conta. Para instanciar os Objetos, os Métodos Construtores foram chamados através da palavra reservada **new**. A Classe Conta sabe qual dos dois Construtores usar pela assinatura de cada Construtor.

Para acessar os Métodos da Classe Conta, utiliza-se o padrão **objeto.método()**. Exemplo: c1.visualiza();

Observe que 2 Métodos set foram utilizados para inserir dados no Objeto vazio c1.

Abaixo, você confere a Classe Conta finalizada:

```java
package conta.model;

public class Conta {
    
    private int numero;
	private int agencia;
	private int tipo;
	private String titular;
	private float saldo;

	public Conta(int numero, int agencia, int tipo, String titular, float saldo) {
		this.numero = numero;
		this.agencia = agencia;
		this.tipo = tipo;
		this.titular = titular;
		this.saldo = saldo;
	}

	public int getNumero() {
		return numero;
	}

	public void setNumero(int numero) {
		this.numero = numero;
	}

	public int getAgencia() {
		return agencia;
	}

	public void setAgencia(int agencia) {
		this.agencia = agencia;
	}

	public int getTipo() {
		return tipo;
	}

	public void setTipo(int tipo) {
		this.tipo = tipo;
	}

	public String getTitular() {
		return titular;
	}

	public void setTitular(String titular) {
		this.titular = titular;
	}

	public float getSaldo() {
		return saldo;
	}

	public void setSaldo(float saldo) {
		this.saldo = saldo;
	}

	public boolean sacar(float valor) { 
		
		if(getSaldo() < valor) {
			System.out.println("\n Saldo Insuficiente!");
			return false;
		}
			
		this.setSaldo(getSaldo() - valor);
		return true;
	}
	
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
		
		System.out.println("\n\n*********************************************************************");
		System.out.println("Dados da Conta:");
		System.out.println("*********************************************************************");
		System.out.println("Numero da Conta: " + this.numero);
		System.out.println("Agência: " + this.agencia);
		System.out.println("Tipo da Conta: " + tipo);
		System.out.println("Titular: " + this.titular);
		System.out.println("Saldo: " + this.saldo);

	}
    
}
```

<br /><br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>
