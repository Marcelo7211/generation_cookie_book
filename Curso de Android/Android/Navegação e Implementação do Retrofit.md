# Navegação e Implementação do Retrofit

Depois de configurar a nossa lista e o aplicativo estar rodando, já temos tudo o que precisa para fazer a navegação mais básica do aplicativo. O objetivo é irmos do `ListFragment` para o `FormFragment` e, para isso, navegaremos utilizando o `navController`, do componente de navegação.

Vamos ainda implementar o Retrofit no projeto, para poder conversar com a nossa API e listar as categorias, possibilitando o usuário escolher qualquer uma disponível no Banco de Dados. Depois, vamos adicionar funções para cadastrar, listar, atualizar e deletar tarefas, realizando um CRUD completo. Além disso, implementaremos funções para recuperar a data atual da tarefa e dar a possibilidade do usuário escolher outras.

## 1. Implementando a navegação do App

1. Abra a classe `ListFragment` e através do binding, dentro do método `onCreateView()`, adicione o método `onSetClickListener{}` no FAB (Floating Action Button). No nosso exemplo, o id dele é `floatingAdd`

   ![Evento de Clique](https://i.imgur.com/BmT2LGZ.png)

   

2. Use o método `findNavController` e, em seguida, o `navigate`, passando o id da navegação nos parâmetros, que definimos anteriormente no `nav_graph`

   ![](https://i.imgur.com/GANXkfb.png)

   

3.  Abra o arquivo `FormFragment`,  onde também faremos a implementação da navegação dele. Por padrão, ele virá com todo aquele código como vimos anteriormente. Exclua todo o código que não usaremos, deixando apenas o método `onCreateView`

   ![](https://i.imgur.com/Ayr9NlU.png)

   

4. Configure o `binding` para o `FormFragment` e deixe o retorno da função `onCreateView()` como `binding.root`, como na imagem abaixo:

   ![](https://i.imgur.com/cxxSHvS.png)

   

5. Adicione um evento de clique para o botão de salvar (no nosso exemplo, buttonSalvar) e recupere o id da navegação, utilizando o `navController` mais uma vez:

   ![](https://i.imgur.com/4Xp61Wi.png)

   

   Desse modo, o aplicativo já vai estar fazendo a navegação de um Fragment para o outro.

   

## 2. Implementação do Retrofit no Projeto

O próximo passo será configurar o Spinner para permitir que o usuário escolha uma categoria disponível, antes de cadastrar uma tarefa. Por conta disso, vamos então implementar o Retrofit no projeto, para recuperar as categorias já existentes na API e preparar o ambiente para o CRUD das tarefas.

Para uma implementação completa do Retrofit, precisaremos de:

- Uma classe de Modelo (ou Model)
- Uma classe de Serviço (ou Service), que conterá todos os métodos https (e os **Verbos** de cada requisição)
- Um objeto da instância do Retrofit (que definirá a URL base da API)
- Um repositório (ou Repository), que recuperará cada método da classe de Serviço
- Uma ViewModel, para processar o que acontecerá quando cada requisição for chamada e preparar os dados para exibição

[Documentação Oficial do Retrofit!](https://square.github.io/retrofit/)



### 2.2. Criando Classes de Modelo

Para fazer o `RecyclerView`, criamos uma classe de modelo para as tarefas. Agora vamos atualizar isso com base no que nossa API precisa para trazer os dados.

Para criarmos uma classe de modelo que o Retrofit possa utilizar para recuperar os dados da API, precisamos que ela tenha todas as propriedades do objeto que ela retorna. Desse modo, acessaremos esse [link](https://todohenriqueliza.herokuapp.com/swagger-ui/index.html?configUrl=/api-docs/swagger-config), que contém todos os dados sobre como nossa API funciona.

![](https://i.imgur.com/2q5KPCV.png)

Começaremos criando a classe de Modelo da Categoria no nosso projeto:

1. Clique com o botáo direito sobre o pacote `model`.

2. Na sequência. clique em **New → Kotlin Class/File**

   ![](https://i.imgur.com/KhM1Yi5.png)

   

3. Na janela de criação, mantenha o arquivo como `Class` e o renomeie para `Categoria`

![](https://i.imgur.com/gNqwMzl.png)

4. Utilizando o Postman, utilize o método **GET** (/categoria) na API, para analisar o objeto que ele retorna, como na imagem abaixo

![](https://i.imgur.com/4Zt04LY.png)

5. Com base nisso, dentro da classe `Categoria`, digite o código abaixo para criar o modelo

![](https://i.imgur.com/2EITwwp.png)





> Percebam que nossa classe é uma data class, para não nos preocuparmos com a criação de getters, setters e tudo mais.
>
> Na API, tarefas é um atributo que tem vários objetos dentro dele, por esse motivo criamos uma `List<Tarefas>` na nossa classe de modelo
>
> Quando formos cadastrar uma nova tarefa, poderemos passar apenas o Id da categoria, sem a necessidade de especificar os outros atributos. Por isso, manteremos `descricao` e `tarefas` como `nullables`, ou seja, que podem receber valores nulos.



Com isso finalizamos a criação do Modelo da Categoria, agora faremos o mesmo para a classe `Tarefa`:

1. Verifique o objeto que conseguimos retornar em `/tarefa`, na página inicial da API

   ![](https://i.imgur.com/6yxwrqn.png)

   

2. Abra o arquivo `Tarefa`, localizado dentro do pacote `model`, e substitua este código

   ![](https://i.imgur.com/DO9P9zM.png)

   Por esse

   ![](https://i.imgur.com/te1zBe9.png)

   Aqui nós só precisamos adicionar mais um atributo `id` e substituir o tipo da variável `categoria` de `String` para `Categoria`, já que, na API, ele vai retornar um objeto.

   

Como mudamos a nossa classe de modelo, precisamos adaptar o `TarefaAdapter` para ele. Abra essa classe e perceberá que ele tem um erro.

![](https://i.imgur.com/JZMR7tf.png)

Como categoria não é mais uma string, precisamos retornar, na verdade, o atributo `descricao` desse objeto, portanto substituiremos essa linha por

![](https://i.imgur.com/TuaEVDD.png)



Depois dos ajustes feitos, as classes de modelo do nosso projeto estão finalizadas e agora começaremos a implementar o primeiro método http dentro do projeto, para conseguirmos listar as categorias.



### 2.3. Criando o Service da API e o método GET

Vamos criar uma nova interface no nosso projeto, para o Serviço.

1. Clique com o botão direito sobre o pacote principal do aplicativo (em nosso exemplo: **com.example.todomobile**)

2. Na sequência clique em **New  → Package**

   ![](https://i.imgur.com/BFOpLag.png)

   

3. Defina o nome do pacote como api

   ![](https://i.imgur.com/GoA5qSc.png)

   

4. Clique com o botão direito sobre o pacote `api`e vá em **New → Kotlin Class/File**

   ![](https://i.imgur.com/vYTeFmV.png)

5. Na janela de criação, mantenha o arquivo como `interface`, com o nome `ApiService`

   ![](https://i.imgur.com/t9P9IlW.png)

   

Agora vamos criar o código da nossa **Classe de Serviço**, igual a figura abaixo:

![](https://i.imgur.com/6s3X6oZ.png)

Na **linha 11**, a anotação **@GET** mapeia solicitações HTTP GET para tratamentos específicos, ou seja, indica que o método `listCategoria()`responderá à requisições **HTTP GET**, enviadas ao endereço https://todogenerationmobile.herokuapp.com/categoria.

Na **linha 12**, marcamos a função como `suspend` indicando que ela só poderá rodar dentro de uma **Corrotina**. Essa função, ainda retorna um **Response** (que será o objeto responsável por guardar a resposta da API) do tipo **List<Categoria>** (que armazenará os objetos da resposta em sí)



### 2.4. Criando instância do Retrofit

1. Clique com o botão direito sobre o pacote `api`

2. Na sequência clique em **New  → Kotlin Class/File**

   ![](https://i.imgur.com/CgdwJI5.png)

   

3. Na janela de criação, mantenha o arquivo como `Object` e defina o nome como `RetrofitInstance`

   ![](https://i.imgur.com/6kBX8q0.png)

   

Agora criaremos de fato a instância do Retrofit no nosso projeto, igual a figura abaixo:

![](https://i.imgur.com/FoSY74A.png)



Na **linha 8**, criamos a variável que vai armazenar a instância do Retrofit, que será criada mais tarde. Além disso, para definir o valor da variável utilizamos o `by lazy{}`, que inicializará os dados na primeira vez que o objeto for utilizado e tornará seus valores disponíveis imediatamente quando for usado de novo.

Na **linha 9**, usamos o `Retrofit.Builder()`, que terá acesso a todos os métodos para a criação do Retrofit.

Na **linha 10** definimos qual vai ser a URL base da nossa API que, por enquanto, deixaremos vazia

Por padrão, o Kotlin não consegue ler uma resposta de um **JSON**. Portanto, Na **linha 11**, utilizamos o `GsonConverterFactory` para converter o **JSON** em algo que o Kotlin consegue utilizar.

Na **linha 12** executamos o método `build()` para construir a instância do Retrofit com base nas informações que passamos anteriormente.

Na **linha 15** criamos mais um atributo chamado `api` que criará a instância do Retrofit com base na interface de Serviço que criamos anteriormente.

Por fim, na **linha 16**, utilizamos o método `create()` diretamente da variável `retrofit`, convertendo a interface `ApiService` em uma classe Java, para o Retrofit saber em que lugar ele buscará as requisições.



### 2.5. Criando arquivo de Constantes para a URL Base da API

Para adicionar mais segurança ao nosso aplicativo, faremos a implementação de um arquivo separado para armazenar a URL da nossa API.

Vamos fazer a criação desse arquivo:

1. Clique com o botão direito sobre o pacote principal do aplicativo

2. Na sequência clique em **New  → Package**

   ![](https://i.imgur.com/06hWWFI.png)

   

3. Defina o nome do pacote como util

   ![](https://i.imgur.com/jFEnaMF.png)

   

4. Clique com o botão direito sobre o pacote `util`e vá em **New → Kotlin Class/File**

   ![](https://i.imgur.com/9Qqbv4q.png)

5. Na janela de criação, mantenha o arquivo como `object`, com o nome `Cosntants`

   ![](https://i.imgur.com/dN9Wxal.png)

   

Agora vamos criar o código do nosso **Objeto de Constantes**, igual a figura abaixo:

![](https://i.imgur.com/vQzNOBl.png)

Perceba que o valor da constante é uma String, contendo a URL base da nossa API, ou seja, este endereço: https://todohenriqueliza.herokuapp.com/



Acesse o objeto `RetrofitInstance` e substitua `""`, que definimos no método `baseUrl()`, para a constante que acabamos de criar, dessa forma:

![](https://i.imgur.com/yejMQhh.png)

Agora sim o Retrofit sabe exatamente em que lugar ele buscará os nossos dados.



### 2.5. Criando o Repository

Primeiro vamos criar o pacote `repository` e, em seguida, criaremos a classe `Repository`

1. Clique com o botão direito sobre o pacote principal do aplicativo (em nosso exemplo: **com.example.todomobile**)

2. Na sequência clique em **New  → Package**

   ![](https://i.imgur.com/G318Q6t.png)

   

3. Defina o nome do pacote como `repository`

   ![](https://i.imgur.com/5stj25n.png)

4. Clique com o botão direito sobre o pacote `repository`e vá em **New → Kotlin Class/File**

   ![](https://i.imgur.com/ENlSbJW.png)

   

5. Em seguida, mantenha o arquivo como `Class` e chame de `Repository`

   ![](https://i.imgur.com/WOJdYpN.png)

   

Agora faremos essa classe acessar o objeto de instância do Retrofit e já retornar o método **GET** da interface de Serviço, como no código abaixo:

![](https://i.imgur.com/dY2iVqU.png)

Nas ***linhas 10-11** criamos uma função que tem o mesmo tipo de retorno do método **GET** que criamos na interface de Serviço. Além disso nós retornamos exatamente o objeto `RetrofitInstance`, com a variável `api` que fará a criação da instância do Retrofit e acessamos o método `listCategoria()` da nossa classe de serviço.

Note que como `RetrofitInstance` é um objeto anônimo e por isso ele será instanciado apenas uma vez, então, a partir do momento que chamamos esse objeto em qualquer função e acessamos o atributo `api`, a instância do Retrofit será criada no projeto e já poderemos fazer as requisições através dela.



### 2.6 Adicionando a ViewModel no Projeto

A implementação do Retrofit no projeto está quase pronta, só falta adicionarmos agora a ViewModel para conseguirmos preparar os dados para exibição, além do comportamento de cada um para inserirmos no banco de dados remoto.

Então primeiro vamos criar a classe onde teremos todo o código dela:

1. Clique com o botão direito sobre o pacote principal do aplicativo e vá em **New → Kotlin Class/File**

2. Depois disso, crie uma nova classe chamada de `MainViewModel`

   ![](https://i.imgur.com/mhC90BS.png)

​		Essa classe não precisa necessariamente estar dentro de um pacote, mas isso fica a critério de vocês.



Agora vamos extender essa classe com a `ViewModel()`, para transformá-la em uma ViewModel de fato

![](https://i.imgur.com/BRFFeau.png)



Sabemos que precisaremos acessar os métodos do repositório para criar a instância do Retrofit e usar tudo que ele proporciona. Para isso, criaremos um construtor para essa classe, que recebe a classe `Repository`

![](https://i.imgur.com/xjylEdE.png)

Nosso objetivo agora é poder recuperar as categorias já existentes na nossa API, para popular o Spinner antes de criar uma Tarefa. Então criaremos variáveis para armazenar esses valores e poder recuperá-los mais para frente no nosso código, como no exemplo abaixo:

![](https://i.imgur.com/SNKtgeO.png)

Nas **linhas 11-12**, criamos uma variável privada com o tipo `MutableLiveData<>`. Diferente do `LiveData`, o `MutableLiveData` permite que possamos trocar o valor dessa variável no futuro, ou seja, será ela que utilizaremos para trazer os dados do banco, sempre que fizermos a requisição. Inclusive, esse `MutableLiveData` recebe uma `Response<List<Categoria>>`, o mesmo tipo que nossa requisição **GET** retorna.

[Documentação LiveData](https://developer.android.com/topic/libraries/architecture/livedata?hl=pt-br).

Nas **linhas 14-15**, fizemos a criação de mais uma variável do tipo `LiveData`, que sempre receberá os valores da variável que criamos anteriormente. Isso porque será com essa variável que conseguiremos acessar os valores da `MainViewModel` em outras classes, só que sem a possibilidade de altera-los, o que dá uma segurança maior para o código. 

Vamos agora criar o método que fará a requisição das categorias no projeto, como no código abaixo:

![](https://i.imgur.com/fDiDnTI.png)

Na **linha 25**, criamos uma nova **corrotina** com base no ciclo de vida da ViewModel, para rodar a requisição da API. Isso porque todos os métodos da interface de Serviço são funções marcadas como `suspend`. Isso faz com que sejamos obrigados a seguir esses passos e evitar que o programa possa rodar as requisições de forma síncrona, ou seja, fora de uma corrotina e na **Thread** principal.

[Documentação Corrotinas ](https://kotlinlang.org/docs/coroutines-overview.html) (Link em Inglês).

Na **linha 26** iniciamos um bloco try...catch para evitar que o programa quebre caso algum erro aconteça.

Nas **linhas 27-28** guardamos a requisição `listCategoria()`, que fizemos através do `repository` dentro de uma variável e passamos esse valor para o `MutableLiveData` (no exemplo, o `_myCategoriaResponse`).

Na **linha 30**, criamos um **log** com a mensagem de erro genérica que o programa retornar, caso não consiga realizar a requisição.

Agora vamos criar o código para que o programa possa fazer essa requisição e já armazenar as categorias dentro das variáveis que criamos, assim que a `MainViewModel` for instanciada, desse modo:

![](https://i.imgur.com/S61UYnU.png)

**Nas linhas 24-25-26**, chamamos o método `listCategoria()` dentro do bloco `init`.

Com isso finalizamos a implementação do Retrofit no projeto, agora falta recuperarmos esses dados que já configuramos e iniciar a construção de todas as funções do nosso aplicativo.



## 3. Recuperando dados da ViewModel e Injetando Dependências com Hilt

Agora que temos tudo para recuperarmos os dados da requisição GET, os próximos passos será recuperar as categorias dentro do Spinner. 

### 3.1. Criando Teste com a ViewModel

Vamos acessar a classe `FormFragment` e, primeiramente, criar o código para instanciar a `MainViewModel`, como no modelo abaixo:

![](https://i.imgur.com/1dB6kxm.png)

Agora realizaremos um código de teste para verificar se conseguimos trazer os dados da ViewModel, como o código abaixo:

![](https://i.imgur.com/sTTJIAn.png)

Na **linha 31**, adicionamos o método `observe()` para o atributo `myCategoriaResponse` que recuperamos da `mainViewModel`.  Esse `observe()` permite que possamos **executar um bloco de código** cada vez que a variável **mudar de valor**. Como primeiro parâmetro desse método, passamos o `viewLifecycleOwner`, para dizer que a variável será observada com base no **ciclo de vida do Fragment** e, logo após, abrimos as **chaves** onde digitaremos o código que será executado quando a variável **mudar seu valor**.

Na **linha 32**, criamos uma variável `response`, que terá os valores do atributo `myCategoriaResponse`.  Depois disso, utilizamos o `Log.d()` para exibir o corpo da `response`, com o método `body()`. Com isso, retornaremos uma `List<Categoria>`, que poderá ser convertida em uma `String`, utilizando o método `toString()`.

Porém, isso vai acarretar em um erro no momento em que executarmos o aplicativo e formos para o Fragment de Formulário. Isso porque, quando ele tentar instanciar a `MainViewModel`, não haverá nenhuma instância de `Repository` no projeto para acessar as requisições. O erro será parecido com esse:

![](https://i.imgur.com/ATgnU7l.png)

Perceba então que ele tenta criar a instância, mas não consegue. Então vamos corrigir esse erro.



### 3.2. Implementando o Hilt no Projeto para Injeção de Dependências

Queremos que sempre que instanciarmos a **ViewModel** no projeto possamos trazer junto dela uma instância do nosso **Repositório**, que tem acesso as requisições. Desse modo, usaremos o **Hilt** para criar a instância de `Repository` assim que o programa for iniciado e injetá-la no construtor da `MainViewModel`. 

[Documentação oficial do Hilt](https://dagger.dev/hilt/) (Link em inglês)

[Documentação - Injeção de Dependência com Hilt no Android Studio](https://developer.android.com/training/dependency-injection/hilt-android?hl=pt-br)

Começaremos criando a classe que extenderá de `Application`, para definirmos que o nosso projeto utilizará o **Hilt**

1. Clique com o botão direito sobre o pacote principal do aplicativo e vá em **New → Kotlin Class/File**
2. Depois disso, crie uma nova classe chamada de `TodoApplication`

Agora vamos criar o código dela

![](https://i.imgur.com/apOcqxw.png)

Na **linha 6** usamos a anotação **@HiltAndroidApp**, define que a classe será a base de dependências para o nosso aplicativo.

Na **linha 7**, extendemos a classe `Application`, o que quer dizer que agora o Hilt poderá injetar as dependências em qualquer lugar do aplicativo.

Feito isso, precisaremos dizer ao nosso app que a classe `TodoApplication` é quem agora cuida do aplicativo como um todo. Abra o arquivo `manifest.xml` e adicione essa linha:

![](https://i.imgur.com/fMKG1u6.png)

Agora criaremos um objeto anônimo que criará a instância da classe `Repository`, que injetaremos na `MainViewModel`:

1. Clique com o botão direito sobre o pacote principal do aplicativo
2. Na sequência clique em **New  → Package**

3. Defina o nome do pacote como `di` (que vem de Dependency Injection)

4. Clique com o botão direito sobre o pacote `di`e vá em **New → Kotlin Class/File**

5. Em seguida, mantenha o arquivo como `Class` e chame de `ServiceModule`

   ![](https://i.imgur.com/ZBFZmHi.png)

Agora faremos a criação de todo o código para criar a instância do `Repository` assim que o projeto for iniciado, como no código abaixo:

![](https://i.imgur.com/RisF3AU.png)

Na **linha 10** temos a anotação **@Module**, que adiciona a possibilidade de criarmos tipos que não podem ser injetados manualmente.

Na **linha 11** é utilizado o **@InstallIn**, passando um `SingletonComponent` como uma `Kclass`. Isso apenas indica em quais containers as dependências geradas pelo módulo estarão disponíveis e, como o `SingletonComponent` sobrevive ao ciclo de vida da `Application`, as dependências só serão destruídas quando o app for finalizado.

Na **linha 14** utilizamos o **@Provides**, que literalmente terá uma função que possa retornar a dependência que queremos injetar futuramente.

Na **linha 15** utilizamos o **@Singleton**, para dizer que a dependência terá o mesmo ciclo de vida do `SingletonComponent`.

Por fim, nas **linhas 16-18**, criamos uma função que retorna uma instância de `Repository`

Desse modo, uma instância de `Repository` será criada dentro do projeto.

 

Agora vamos dizer ao Hilt em que lugar do código está o Container dos nossos Fragments, já que cada um deles utilizará a ViewModel e as dependência que ele injeta.

Abra a classe `MainActivity` e adicione esta linha:

![](https://i.imgur.com/wuc16Gb.png)

Perceba que logo acima da declaração da classe, usamos a anotação **@AndroidEntryPoint**, que serve para definir que a `MainActivity` receberá um container contendo todas as dependências que injetamos, para poder ser utilizada nos fragments futuramente.



Com tudo isso feito, só precisamos agora **injetar essa dependência** dentro da **ViewModel**.

Abra a classe `MainViewModel` e faça a injeção de dependências como no código abaixo:

![](https://i.imgur.com/KXwx8Ut.png)

Perceba que, na **linha 16**, adicionamos a anotação **@HiltViewModel**, que prepara a **ViewModel** para receber dependência e, logo em seguida, utilizamos o **@Inject** na **linha 17**, que finalmente injeta qualquer dependência que criamos dentro de `ServiceModule` que, no nosso caso, será uma instância de `Repository`.

Se executarmos o aplicativo agora com o teste que fizemos anteriormente, vamos conseguir criar a instância da `MainViewModel` e nosso código conseguirá trazer as informações do Banco. Desse modo:
![](https://i.imgur.com/8i3ZuzB.png)

Se quiser entender melhor cada uma das anotações que utilizamos no processo, acesse a [tabela de anotações do Hilt](https://developer.android.com/training/dependency-injection/hilt-cheatsheet) (Link em Inglês)





## 4. Populando o Spinner com as Categorias do Banco

Criaremos um método agora para exibir as categorias no Spinner que criamos anteriormente no App. Desse modo, criaremos um método sem retorno que possa receber uma lista de categorias:

![](https://i.imgur.com/VZNi5w4.png)

Perceba que vamos receber um `List<Categoria>?` como parâmetro dessa função e esse valor poderá ser **nulo**, justamente porque quando fazemos uma requisição no banco **pode demorar um pouco** até ela se completar e, enquanto **não há dados**, temos valores nulos.

Agora vamos criar a lógica para popular o Spinner, como o código abaixo:

![](https://i.imgur.com/0Ld3RhM.png)

Criamos então um bloco `if` que verifica se a categoria é diferente de nula, para evitar erros futuros. Logo em seguida recuperamos o `spinnerCategoria` e configuramos seu `Adapter` com base em um `ArrayAdapter`.  Assim, passamos o **contexto do Fragment**, o **layout que o Spinner se baseará** e a **lista de categorias**, que recuperaremos nos **parâmetros**. 



Só falta agora chamar esse método em algum lugar para o Spinner ser criado e faremos isso no mesmo bloco onde adicionamos o Log das categorias, como no código abaixo:

![](https://i.imgur.com/83WSYdX.png)

Perceba que chamamos a função e já atribuímos o corpo da `response` como parâmetros dela, retornando exatamente uma lista de categoria.



Assim, vamos executar o app para ver se tudo deu certo. O Spinner deverá estar parecido com isso:

![](https://i.imgur.com/D9Gy5sa.png)

Precisamos ajustar essa forma com que as categorias estão sendo exibidas. Para isso, abra a classe `Categoria` e adicione estas linhas no código:

![](https://i.imgur.com/tLJ4qX6.png)

Aqui nós sobrescrevemos, então, o método `toString()` e retornamos apenas o atributo de `descricao` da Categoria, como uma `String` não nula (por isso adicionamos o `!!`). 

Com isso, não teremos mais o problema do aplicativo exibir o padrão de uma `data class` no método `toString()`. Quando executarmos o código, teremos algo parecido com isso:

![](https://i.imgur.com/JAaAHzB.png)

## 5. Criando Data Personalizada

Agora o que teremos que fazer é dar a possibildade do usuário escolher uma data para sua tarefa de forma automática. Faremos isso com um conjunto de passos:

- Primeiro temos que ter uma forma de retornar a data atual, a partir do momento que o usuário entrar na tela de Formulário

- Depois disso, o usuário terá que ter a possibilidade de escolher uma data, e faremos isso configurando um `DatePickerFragment`, para ter um calendário.

- A data escolhida no calendário terá que ser retornado no campo de Data

  

### 5.1. Recuperando Data atual

Para recuperarmos a data atual, criaremos uma lógica para ter esse valor no momento que a ViewModel for instanciada.

1. Abra a classe `MainViewModel` e adicione o código a seguir:

   ![](https://i.imgur.com/Sr9aoMp.png)

   Criamos a variável `dataSelecionada` como um `MutableLiveData`, para podermos observá-la futuramente.  Perceba que a variável recebe um `LocalDate`, pois é com esse tipo que conseguiremos gerar a data no padrão yyyy-mm-dd.

   [Documenação LocalDate](https://docs.oracle.com/javase/8/docs/api/java/time/LocalDate.html)

2. Agora faremos o código para recuperar a data atual e armazená-la no atributo que criamos:

   ![](https://i.imgur.com/Vr8IIfh.png)

   

   

Feito isso, já temos a data atual, agora falta recuperar esse dado no Fragment de Formulário e passar o valor para o campo de Data:

1. Abra a classe `FormFragment`.

2. Dentro dela, vamos criar um observador para o atributo `dataSelecionada`

3. Depois, basta recuperar o valor da `dataSelecionada` e transmitir seu valor para o `EditText` que criamos para exibir a data, desse modo:

   ![](https://i.imgur.com/DL0wCLB.png)

   É interessante lembrar que como um `EditText` só recebe `CharSequence`, precisamos converter o valor em uma `String`

   

A partir do momento que executarmos o App, teremos algo parecido com isso:

![](https://i.imgur.com/Hea0FNP.png)



### 5.2. Criando o DatePickerFragment

Vamos agora criar o calendário que o usuário acessará ao clicar na data.

O primeiro passo será criar a classe `DatePickerFragment`, para criarmos o `DatePickerDialog`.

[Documentação oficial - DatePickerDialog](https://developer.android.com/reference/android/app/DatePickerDialog)

1. Clique com o botão direito sobre o pacote principal do aplicativo
2. Na sequência clique em **New  → Package**

3. Defina o nome do pacote como `fragment` (nesse pacote não adicionaremos todas as unidades lógicas dos Fragments, mas apenas do `DatePickerFragment`)

4. Clique com o botão direito sobre o pacote `fragment`e vá em **New → Kotlin Class/File**

5. Em seguida, mantenha o arquivo como `Class` e chame de `DatePickerFragment`

   ![](https://i.imgur.com/nPTJiQJ.png)

   É nessa classe onde criaremos toda a lógica para abrir o `DatePickerDialog` e recuperar a data que o usuário selecionar

Feito isso, vamos inserir uma interface dentro do código que nos auxiliará na recuperação da data como um `LocalDate`, como no exemplo abaixo:

![](https://i.imgur.com/UhkOaU8.png)

Perceba que, na linha 10, criamos uma função abstrata para a interface que recebe um `LocalDate`. Usaremos essa interface futuramente, quando quisermos recuperar o que o usuário selecionou.

Depois disso, vamos transformar essa classe em algo que possa utilizar a interface que criamos e ter os métodos necessários para construir o nosso calendário, como no código abaixo:

![](https://i.imgur.com/wvnLunF.png)

Na linha 9, criamos um construtor para a classe `DatePickerFragment` do tipo `TimePickerListener`, para termos o método que recupera a data selecionada.

Na linha 11, extendemos a classe `DialogFragment()` e implementamos as regras de negócio da interface `OnDateSetListener`, que pegamos da classe `DatePickerDialog`. Com isso, temos o ambiente preparado para criar o DatePickerFragment.



Note que a classe `DatePickerFragment` tem um erro, isso porque deveremos implementar os métodos abstratos que estão faltando, para isso:

1. Mantenha o mouse em cima de onde o erro está sendo acusado e clique sobre "implement members"

   ![](https://i.imgur.com/5RA5naJ.png)

2. Selecione o método faltante e clique em "Ok"

   ![](https://i.imgur.com/NJS1sTP.png)

3. Feito isso, um novo método será adicionado na classe

   ![](https://i.imgur.com/w646qhv.png)



Nós já decidiremos como utilizar essa função, mas antes sobrescreveremos o método `onCreateDialog()`, da classe `DialogFragment`, e implementaremos o código que abrirá o nosso Dialog com a data atual selecionada, dessa forma:

![](https://i.imgur.com/BypsVTX.png)

Na **linha 17**, nós sobrescrevemos o método `onCreateDialog()`

Nas **linhas 19-22**, criamos variáveis que recuperam uma **instância do calendário, ano, mês e dia**.

Na **linha 25**, retornamos uma instância do `DatePickerDialog` com base na data atual.



Certo, agora utilizaremos o método `onDateSet()` para recuperar a data que o usuário selecionar no calendário:

![](https://i.imgur.com/cy1L81D.png)

Na **linha 30**, criamos uma variável para guardar a **instância do calendário**.

Nas **linhas 31-33**, recuperamos o valor de **ano, mês e dia** com base na **data que o usuário escolher**.

Nas **linhas 34-35**, usamos o atributo do construtor `timerPickerListener` para termos acesso ao método `onTimeSelected()`. Assim, recuperamos  a **data atual do calendário** (que o usuário escolheu) e convertemos em `LocalDate`, mantendo o padrão yyyy-mm-dd.

Com isso, a classe `DatePickerFragment` está finalizada.



### 5.3. Exibindo o Calendário

Agora que temos toda a classe do DatePickerFragment finalizada, construiremos a lógica para exibir o calendário e recuperar a data que o usuário selecionar, transmitindo para o campo de data do Fragment de Formulário.

Abra a classe `FragmentForm` e vamos implementar a interface `TimerPickerListener`

![](https://i.imgur.com/hCSKK3P.png)

Feito isso, adicionaremos o método abstrato que criamos para recuperar a data selecionada

1. Mantenha o mouse em cima do erro que está sendo acusado pela classe e clique em "Implement members"

2. Selecione o método que está faltando e clique em "Ok"

   ![](https://i.imgur.com/KbJmRGB.png)

   

Agora vamos fazer o código para armazenar a data que o usuário escolher:

![](https://i.imgur.com/dsch5bJ.png)

Perceba que, toda vez que o usuário selecionar uma data, armazenaremos esse valore no atributo `dataSelecionada`, dentro da  `MainViewModel`.

Queremos que toda a vez que clicarmos no campo de data, o calendário seja exibido para escolhermos a data. Vamos implementar essa lógica, como no código abaixo:

![](https://i.imgur.com/qxMNqCl.png)

Adicionamos um evento de clique para o `EditText `(no exemplo, `editData`) , na **linha 50**.

Na **linha 51**, instanciamos o `DatePickerFragment`, passando o `timePickerListener` como parâmetro.

Na **linha 52**, utilizamos o método `show()`, passando o `parentFragmentManager` como parâmetro e definindo uma tag, tudo para exibir o calendário sem problemas no **Fragment atual**.

Com isso feito, ao selecionar o campo de data o calendário será exibido e a data escolhida também, como no exemplo abaixo:

![](https://i.imgur.com/Y0gDJTv.png)

Se selecionarmos uma data (no caso, selecionaremos 31 de janeiro no exemplo), ela será salva:

![](https://i.imgur.com/dQqMxJZ.png)



## 6. Inserindo Tarefas no Banco

Temos tudo o que é necessário no formulário para salvar uma tarefa no Banco de Dados remoto. Para fazer essa inserção agora, precisaremos seguir alguns passos:

- Primeiro deveremos recuperar qual categoria está selecionada no Spinner e armazenar seu id.
- Criar uma requisição POST para a API
- Implementar a lógica para validar os dados que o usuário colocou
- Inserir, enfim, a tarefa no Banco



### 6.1. Recuperando categoria selecionada

Abra o arquivo `FormFragment` para conseguirmos gerar o código para verificar a categoria selecionada

1. Primeiro, criaremos uma variável para armazenar o id da categoria

   ![](https://i.imgur.com/0hJsuqa.png)

   

2. Dentro do método `spinnerCategoria()`, vamos verificar o item selecionado como no código abaixo:

   ![](https://i.imgur.com/3l3Gayj.png)

   Na **linha 68**, utilizamos o atributo `onItemSelectedListener`, para indicar o que acontecerá no momento em que um item for selecionado

   Na **linha 69**, configuramos um objeto que implementar a interface `OnItemSelectedListener`, da classe `AdapterView`, para conseguirmos ter acesso aos métodos necessários para verificar o **item selecionado pelo usuário**.

3. Na sequência, coloque o mouse sobre o código onde o erro está sendo acusado e clique em "implement members"

4. Selecione os métodos que estão faltando e clique em "Ok"

   ![](https://i.imgur.com/xbolXkF.png)

   

Agora modificaremos o método `onItemSelected()` para recuperarmos o item selecionado e armazenar seu id, como no código abaixo:

![](https://i.imgur.com/rkkeYgX.png)

Nas **linhas 73-74**, criamos uma variável que armazena o item selecionado no Spinner, como um objeto `Categoria`

Na **linha 76**, armazenamos o id desse item no atributo `categoriaSelecionada`, que criamos anteriormente. 

Recuperando o id da categoria, todo o ambiente está preparado para salvarmos um item no banco.



### 6.2. Implementando Método POST no Retrofit, para as Tarefas

Abra a interface `ApiService` para criarmos o método POST, como no código abaixo:

![](https://i.imgur.com/17g9glp.png)

Na **linha 18**, a anotação **@POST** mapeia solicitações HTTP POST para tratamentos específicos, ou seja, indica que o método `addTarefa()`responderá à requisições **HTTP POST**, enviadas ao endereço https://todohenriqueliza.herokuapp.com/tarefa.

Na **linha 19**, marcamos a função como `suspend` indicando que ela só poderá rodar dentro de uma **Corrotina**.

Na **linha 20**, adicionamos um parâmetro para o método. A anotação **@Body** indica que passaremos um corpo à requisição, que será um objeto `Tarefa` 

Na **linha 21**, indicamos que o retorno da função é um `Response<Tarefa>`, para podermos verificar, no futuro, se a Tarefa foi cadastrada.

Feito isso, abra a classe `Repository` para acessarmos o método criado, como no exemplo abaixo:

![](https://i.imgur.com/Ckj1sm8.png)

Nas ***linhas 14-15** criamos uma função que tem o mesmo tipo de retorno do método **POST** que criamos na interface de Serviço, além de ter um objeto `Tarefa` como parâmetro

Agora só precisamos criar o código para processar os dados da requisição na `MainViewModel`, dessa forma:

![](https://i.imgur.com/QPCHgZf.png)

Na **linha 49**, criamos uma nova **corrotina** com base no ciclo de vida da ViewModel, para rodar a requisição da API. Como precisamos de um objeto `Tarefa`, passamos ele como parâmetro.

Na **linha 50** iniciamos um bloco try...catch para evitar que o programa quebre caso algum erro aconteça.

Nas **linhas 51** chamamos o método `addTarefa()` do repositório, passando o objeto `Tarefa` do método.

Na **linha 53**, criamos um **log** com a mensagem de erro genérica que o programa retornar, caso não consiga realizar a requisição.

Com isso, o método **POST** está pronto para ser utilizado.



### 6.4. Validando dados do Usuário

Antes de salvar os dados, precisamos nos certificar que o usuário não deixou **nenhum campo vazio**, além de respeitar as regras da requisição **POST** para salvar uma tarefa na API.

Para isso, abra o `FragmentForm` e, em seguida, implementaremos um método para validar os dados:

![](https://i.imgur.com/bKVu93Z.png)

Nas **linhas 87-90**, criamos um método com retorno do tipo `Boolean`. Como sabemos que tudo que o usuário digitar vai vir de vários `EditText`, passamos como parâmetros nome, descrição, responsável e data como `String`, para realizarmos essa validação.

> A data não precisaria necessariamente estar aí, mas, caso aconteça algum tipo de erro e a data **venha a ficar vazia**, temos mais essa verificação.

Nas **linhas 92-96**, adicionamos um retorno implementando **todas as regras** para verificar se o texto de cada parâmetro está **preenchido e no tamanho correto**. Caso algo esteja fora das regras, a função retornará `false`, mas se todos os textos estiverem corretos, a função retorna `true`.



### 6.5 Inserindo dados no Banco

Enfim, vamos recuperar tudo que o usuário selecionou no formulário para inserir esses dados no Banco. Primeiro, implementaremos um método para iniciar o processo de inserção de dados:

![](https://i.imgur.com/eBXy9fW.png)

Criamos, então, o método `inserirNoBanco()`.

Nas **linhas 104-109**, recuperamos todas as informações que precisamos do formulário e **armazenamos dentro de variáveis**, para **nome, descrição, responsável, data, status e categoria**. 

Percebam que, como a nossa classe `Tarefa` tem um atributo do tipo `Categoria`, criamos um objeto desse tipo, passando apenas o **id**, onde descrição e tarefas deixamos como `null`. Isso porque, **para cadastrar uma tarefa na API**, só precisamos do **id da categoria**.

Agora vamos criar o código para fazer a validação desses campos e inserir a tarefa no banco:

![](https://i.imgur.com/dx2XQOI.png)

Na **linha 111**, criamos um bloco `if` e  utilizando o método `validarCampos()` para verificarmos se todos os dados foram inseridos corretamente.

Nas **linhas 112-114**, criamos um objeto `Tarefa` com todas as informações que trouxemos do formulário.

> O **id** deixamos como **0**, justamente porque a **API cuidará da criação dele**

Na **linha 115**, chamamos o método `addTarefa()` da `MainViewModel`, passando o objeto `Tarefa` que instanciamos.

Nas **linhas 116-119**, criamos uma mensagem `Toast` para exibir que o salvamento foi um sucesso.

Na **linha 120**, usamos o `findNavController()` para navegar de volta ao Fragment de Lista.

Nas **linhas 122-125**, dentro do bloco `else`, exibimos uma mensagem `Toast` caso a validação dos campos retorne `false`.



Com o método para inserir as tarefas no banco finalizado, vamos agora criar o código para chamá-lo assim que o usuário clicar no botão de salvar

![](https://i.imgur.com/ksyebq7.png)



Feito isso, os dados já estarão sendo salvos na API. Se formos testar esse recurso, teremos um resultado parecido com esse:

![](https://i.imgur.com/VCNWzt2.png)

Uma tarefa bem simples, clicando para salvar:

![](https://i.imgur.com/L2kAL4n.png)

A tarefa é salva com sucesso! Mas ainda não temos certeza se isso foi, de fato, adicionado no banco. Por isso, faremos a requisição dessa tarefa pelo navegador

![](https://i.imgur.com/2Dgcb1C.png)

Com isso, temos a certeza de que nosso aplicativo já salva as tarefas na API. Podemos também verificar se a validação funciona conforme programamos, como no exemplo abaixo:

![](https://i.imgur.com/HDwvX6n.png)

Perceba que na descrição colocamos apenas uma letra, o que quebra umas das regras da validação, portanto a tarefa não é salva.



## 7. Listando Tarefas

Com as tarefas sendo cadastradas, vamos agora listar todas elas no Fragment de Lista. Desse modo, teremos que:

- Criar uma requisição GET na API, no caminho `/tarefa`
- Recuperar os dados da API
- Adicionar os dados na lista do `RecyclerView`



### 7.1. Implementando Método GET no Retrofit, para as Tarefas

Abra a interface `ApiService` para criarmos o método GET, como no código abaixo:

![](https://i.imgur.com/4N6uYAE.png)

Na **linha 24**, a anotação **@GET** indica que o método `addTarefa()`responderá à requisições **HTTP GET**, enviadas ao endereço https://todohenriqueliza.herokuapp.com/tarefa.

Na **linha 25**, marcamos a função como `suspend` indicando que ela só poderá rodar dentro de uma **Corrotina**. Além disso, declaramos que ela terá um retorno do tipo `Response<List<Tarefa>>`, para trazer uma listagem de tarefas da API.

Feito isso, abra a classe `Repository` para acessarmos o método criado, como no exemplo abaixo:

![](https://i.imgur.com/c1fstCO.png)

Nas ***linhas 18-19** criamos uma função que tem o mesmo tipo de retorno do método **GET** que criamos na interface de Serviço.

Nosso objetivo agora é poder recuperar as tarefas já existentes na nossa API. Então criaremos variáveis para armazenar esses valores.

![](https://i.imgur.com/K4aTMPK.png)

Nas **linhas 29-30**, criamos uma variável privada com o tipo `MutableLiveData<>`, que recebe um `Response<List<Categoria>>`, o mesmo tipo que nossa requisição **GET** retorna.

Nas **linhas 32-33**, fizemos a criação de mais uma variável do tipo `LiveData`, para receber os valores da variável criada anteriormente e ser recuperada mais para frente no código.

Agora só precisamos criar o código para processar os dados da requisição na `MainViewModel`, dessa forma:

![](https://i.imgur.com/EZbRcp8.png)

Na **linha 65**, criamos uma nova **corrotina** com base no ciclo de vida da ViewModel, para rodar a requisição da API.

Na **linha 66** iniciamos um bloco try...catch para evitar que o programa quebre caso algum erro aconteça.

Nas **linhas 67-68** criamos uma variável `response` para armazenar o retorno do método `listTarefas()` do repositório. Logo após, salvamos esses dado no atributo `_myTarefaResponse`, para termos acesso a eles futuramente.

Na **linha 70**, criamos um **log** com a mensagem de erro genérica que o programa retornar, caso não consiga realizar a requisição.

Com isso, o método **GET** está pronto para ser utilizado.



### 7.2. Criando Lista de Tarefas

Como nosso `RecyclerView` já foi criado anteriormente, só falta atualizarmos os dados da lista.

Vamos acessar a classe `ListFragment` e, primeiramente, criar o código para instanciar a `MainViewModel`, como no modelo abaixo:

![](https://i.imgur.com/JQPDnzL.png)



Em seguida vamos fazer a requisição quando o Fragment for criado, isso para já recuperarmos tarefas que existem no banco.

![](https://i.imgur.com/ByIhlYZ.png)



Agora vamos criar o código para popular a Lista de Tarefas:

![](https://i.imgur.com/cSAgAEu.png)

Na **linha 47**, adicionamos o método `observe()` para o atributo `myTarefaResponse` que recuperamos da `mainViewModel`. Como primeiro parâmetro desse método, passamos o `viewLifecycleOwner`, para dizer que a variável será observada com base no **ciclo de vida do Fragment** e, logo após, abrimos as **chaves** onde digitaremos o código que será executado quando a variável **mudar seu valor**.

Nas **linhas 48**, criamos uma variável `response`, que terá os valores do atributo `myCategoriaResponse`.  Depois disso, criamos uma verificação para analisar se o valor de `response` é diferente de nulo.

Na **linha 49**, utilizamos o método `setLista()` do objeto `tarefaAdapter`, passando o corpo da requisição, retornando o valor como **não nulo**.

Com isso, nós finalizamos a criação da lista com os dados da API. Se formos testar o aplicativo, teremos um resultado parecido com esse:

![](https://i.imgur.com/tUTGJBn.png)

### 7.3. Atualizando Lista ao Adicionar Tarefa

A lista funciona e já busca os dados da API, porém se fizermos um teste agora e adicionar uma nova tarefa, a lista não será atualizada, ou seja, só exibirá as tarefas que requisitou no começo do aplicativo.

Para corrigir isso, atualizaremos o código do método `addTarefa()`, chamando o método `listTarefas()` após a requisição, como no código abaixo:

![](https://i.imgur.com/5SsFYSF.png)

Se formos fazer um teste, depois de adicionarmos uma nova tarefa, o resultado será parecido com esse:

![](https://i.imgur.com/yY797mi.png)



## 8. Atualizando Tarefas

Precisamos agora conseguir selecionar uma tarefa da Lista e poder modificá-la. Para isso, nós vamos precisar seguir alguns passos:

- Adicionaremos a requisição PUT de tarefas no projeto
- Criaremos a lógica para selecionar uma tarefa da lista e recuperar suas informações no formulário.
- Alteraremos o método de inserir dados no banco, para verificar se estamos criando uma tarefa ou atualizando.



### 8.1. Implementando Método PUT no Retrofit, para as Tarefas

Abra a interface `ApiService` para criarmos o método PUT, como no código abaixo:

![](https://i.imgur.com/UXr4U5X.png)

Na **linha 29**, a anotação **@PUT** mapeia solicitações HTTP PUT para tratamentos específicos, ou seja, indica que o método `updateTarefa()`responderá à requisições **HTTP PUT**, enviadas ao endereço https://todohenriqueliza.herokuapp.com/tarefa.

Na **linha 30**, marcamos a função como `suspend` indicando que ela só poderá rodar dentro de uma **Corrotina**.

Na **linha 31**, adicionamos um parâmetro para o método. A anotação **@Body** indica que passaremos um corpo à requisição, que será um objeto `Tarefa` 

Na **linha 32**, indicamos que o retorno da função é um `Response<Tarefa>`, para podermos verificar, no futuro, se a Tarefa foi cadastrada.

Feito isso, abra a classe `Repository` para criarmos o método de atualização, como no exemplo abaixo:

![](https://i.imgur.com/xi2TJoO.png)

Nas ***linhas 22-23** criamos uma função que tem o mesmo tipo de retorno do método **GET** que criamos na interface de Serviço, além de ter um objeto `Tarefa` como parâmetro

Agora só precisamos criar o código para processar os dados da requisição na `MainViewModel`, dessa forma:

![](https://i.imgur.com/27NZLe8.png)

Na **linha 78**, criamos uma nova **corrotina** com base no ciclo de vida da ViewModel, para rodar a requisição da API. Como precisamos de um objeto `Tarefa`, passamos ele como parâmetro da função.

Na **linha 79** iniciamos um bloco try...catch para evitar que o programa quebre caso algum erro aconteça.

Na **linha 80** chamamos o método `updateTarefa()` do repositório, passando o objeto `tarefa` do método.

Na **linha 81**, chamamos o método `listTarefas()`, para atualizar a lista com os novos dados.

Na **linha 83**, criamos um **log** com a mensagem de erro genérica que o programa retornar, caso não consiga realizar a requisição.

Com isso, o método **PUT** está pronto para ser utilizado.



### 8.2. Selecionando uma Tarefa da Lista

Precisamos agora de um atributo dentro da `MainViewModel` que possa armazenar a tarefa que for selecionada, como no código abaixo:

![](https://i.imgur.com/loe8aU4.png)

É esse atributo que vai controlar se o usuário está criando ou atualizando uma tarefa.

Criaremos agora uma **interface**, contendo um método para **recuperar a tarefa selecionada** quando for chamado.

1. Clique com o botão direito sobre o pacote `Adapter` e vá em **New → Kotlin Class/File**

2. Mantenha o arquivo como `Interface` e defina o nome como `TaskItemClickListener`

   ![](https://i.imgur.com/5rorhJp.png)

Desse modo, vamos criar o método para recuperar uma tarefa:

![](https://i.imgur.com/sJzr0tQ.png)





Feito isso, dentro da classe `ListFragment`,  faremos o código que servirá de base para recuperarmos a tarefa

1. Implemente a interface `TaskItemClickListener`

   ![](https://i.imgur.com/aQkricN.png)

2. Mantenha o mouse sobre o erro que o programa está acusando e clique em "implement members"

3. Selecione o método que está faltando e clique em "Ok"

   ![](https://i.imgur.com/hkmm9I4.png)

   

Agora faremos o código para recuperar a tarefa dentro do método sobrescrito:

![](https://i.imgur.com/Yaz6PWv.png)

Na **linha 59**, armazenamos o objeto `tarefas` no atributo `tarefaSelecionada` da `MainViewModel`.

Na **linha 60**, utilizamos o `findNavController` para navegar para o Fragment de Formulário, após recuperar a tarefa que o usuário selecionou.



Vamos acessar a classe `TarefaAdapter` e criar um construtor, contendo um atributo do tipo `TaskItemClickListener` e outro do tipo `MainViewModel`:

![](https://i.imgur.com/zOv59vC.png)

> Não utilizaremos o atributo `mainViewModel` por agora, mas ele servirá de base para atualizar a tarefa no futuro.

Com isso, podemos acessar o que precisamos para recuperar a tarefa e faremos isso dentro do método `onBindViewHolder()`:

![](https://i.imgur.com/DrME9Sp.png)

Na **linha 47**, criamos um evento de clique para o `itemView`, ou seja, o item que está sendo selecionado a partir da lista de tarefas.

Na **linha 48**, chamamos o método `onTaskClicked()`, recuperando a **tarefa selecionada**.

Como adicionamos um construtor na classe `TarefaAdapter`, precisamos acessar a classe `ListFragment` e atualizar a instância que criamos anteriormente:

![](https://i.imgur.com/qyN1iMF.png)

Dessa forma, conseguimos recuperar a tarefa que o usuário selecionou da lista e, a partir disso, navegar para o Fragment de Formulário.



### 8.3. Recuperando Informações da Tarefa Selecionada

Por mais que conseguimos selecionar a tarefa e salvar na **ViewModel**, precisamos agora recuperar as informações dela no **Formulário** .

Acessaremos agora a classe `FormFragment` e criaremos um atributo para receber, no futuro, a tarefa atual

![](https://i.imgur.com/v0O39cT.png)

Desse modo, vamos implementar um método para recuperar as informações da tarefa selecionada:

![](https://i.imgur.com/kMEzXoC.png)

Na **linha 142**, definimos o valor de `tarefaSelecionada` com os valores do atributo`tarefaSelecionada` da `MainViewModel`.

Na **linha 143**, verificamos se o valor que recuperamos é **diferente de nulo**, ou seja, se há alguma **tarefa selecionada**.

Nas **linhas 144-148**, definimos **todos os componentes do formulário** para recuperar as informações da **tarefa selecionada**.

Nas **linhas 150-153**, dentro do bloco `else`, definimos o texto dos `EditText` para **nulos**, ou seja, se nenhuma tarefa estiver selecionada, **não teremos informações preenchidas**.

Agora só precisamos chamar essa função no momento em que o Fragment for criado, desse modo:

![](https://i.imgur.com/EiFk4Py.png)

Se fizermos um teste a partir desse momento, teremos um resultado parecido com esse:

![](https://i.imgur.com/L3FDSVP.png)

Porém, a partir desse momento, o atributo `tarefaSelecionada` da `MainViewModel` nunca deixará de ter o valor que recuperamos. Mesmo se clicarmos no botão para adicionar, ainda teremos os dados da tarefa anterior sendo exibidos.

Para corrigir, dentro da classe `ListFragment` adicionaremos mais uma linha no evento de clique do `floatingAdd`, alterando o valor de `tarefaSelecionada` para `null`

![](https://i.imgur.com/cJezAo9.png)

Desse modo, ao clicar em adicionar, o programa entenderá que não queremos popular o formulário, já que nenhuma tarefa foi selecionada.



### 8.4. Atualizando uma Tarefa

Por enquanto, o método para inserir no banco, que temos dentro do `FormFragment`, apenas adiciona uma nova tarefa. Agora vamos readaptar esse método, para adicionar e atualizar.

Vamos acessar a classe `FormFragment` e acessar o método `inserirNoBanco()`. Assim, substituiremos esse código:

![](https://i.imgur.com/eO9feYG.png)

Por esse:

![](https://i.imgur.com/o3hJVrm.png)

Na **linha 120**, adicionamos agora uma verificação para analisar se a variável `tarefaSelecionada` é nula.

Nas **linhas 121-124**, temos o código para adicionar uma nova tarefa.

Nas **linhas 126-130**, dentro do bloco `else`, criamos um objeto `tarefa` recuperando o id da variável `tarefaSelecionada`, ou seja, passamos um objeto com as alterações do usuário, mas o id permanece o mesmo.

Se fizermos um teste e atualizarmos aquela tarefa de exemplo (que tinha o título "Jogar o Lixo"), teremos um resultado parecido com esse:

![](https://i.imgur.com/FbnoO0e.png)

Perceba que mudei a descrição e a tarefa foi atualizada!



### 8.5. Atualizando o  Andamento da Tarefa através da Lista

Um recurso interessante para colocarmos é a possibilidade do usuário atualizar o andamento da tarefa tocando no `Switch` e já atualizar o estado da tarefa tanto na lista, como na API.

Para isso, vamos abrir a classe `TarefaAdapter` e, usando o atributo que criamos para a `MainViewModel`, faremos o código para atualizar a tarefa assim que o usuário alterar o estado do Switch:

![](https://i.imgur.com/V0k6w7G.png)

Na **linha 62**, dentro do método `onBindViewHolder()`, recuperamos o `Switch`

Na **linha 63**, acessamos o método `setOnCheckedChangeListener()`, que indica o que acontecerá a partir do momento que o **estado do Switch** for alterado e, assim, definimos uma variável `compoundButtton` (que não chegaremos a utilizar) e outra chamada `ativo`, que **armazenará** o estado atual do Switch.

Na **linha 64**, atualizamos o status da tarefa atual para receber a variável `ativo`, ou seja, o status do objeto `tarefa` atual será trocado de acordo com o **estado do Switch**.

Na **linha 65**, utilizamos o método `updateTarefa()` do atributo `mainViewModel` que criamos anteriormente, passando a tarefa atual já atualizada. Com isso, conseguiremos alterar o estado da tarefa tanto no **aplicativo**, quanto na **API**.



## 9. Deletando Tarefas

Por fim, precisamos agora ter a possibilidade de deletar uma tarefa da API e atualizar diretamente na lista. Para isso, seguiremos os seguintes passos

- Adicionaremos a requisição DELETE de tarefas no projeto
- Criaremos a lógica para clicar no botão de Deletar, a partir da lista, e deletar a tarefa de fato.



### 9.1. Implementando Método DELETE no Retrofit, para as Tarefas

Abra a interface `ApiService` para criarmos o método DELETE, como no código abaixo:

![](https://i.imgur.com/AEYvmeQ.png)

Na **linha 32**, a anotação **@DELETE** mapeia solicitações HTTP DELETE para tratamentos específicos, ou seja, indica que o método `deleteTarefa()`responderá à requisições **HTTP DELETE**, enviadas ao endereço https://todohenriqueliza.herokuapp.com/tarefa/. Além disso, indicamos um id, que recuperaremos a partir dos parâmetros da função.

Na **linha 33**, marcamos a função como `suspend` indicando que ela só poderá rodar dentro de uma **Corrotina**.

Na **linha 34**, a anotação **@Path** indica que o parâmetro que passamos para a função será adicionado ao caminho `tarefa/{id}`, onde receberemos, então, o id da tarefa que será deletada.

Na **linha 32**, indicamos que o retorno da função é um `Response<Tarefa>`, para podermos verificar, no futuro, se a Tarefa foi cadastrada.

Feito isso, abra a classe `Repository` para acessarmos o método criado, como no exemplo abaixo:

![](https://i.imgur.com/ah7lfPw.png)

Nas ***linhas 26-27** criamos uma função que tem o mesmo tipo de retorno do método **DELETE** que criamos na interface de Serviço, além de ter um objeto `Tarefa` como parâmetro

Agora só precisamos criar o código para processar os dados da requisição na `MainViewModel`, dessa forma:

![](https://i.imgur.com/xOSUjCH.png)

Na **linha 92**, criamos uma nova **corrotina** com base no ciclo de vida da ViewModel, para rodar a requisição da API

Na **linha 93** iniciamos um bloco try...catch para evitar que o programa quebre caso algum erro aconteça.

Na **linha 94** chamamos o método `deleteTarefa()` do repositório, passando o  `id` dos parâmetros no método.

Na **linha 95**, chamamos o método `listTarefas()`, para atualizar a lista com os novos dados.

Na **linha 97**, criamos um **log** com a mensagem de erro genérica que o programa retornar, caso não consiga realizar a requisição.

Com isso, o método **DELETE** está pronto para ser utilizado.



### 9.2. Deletando uma Tarefa

Vamos acessar a classe `TarefaAdapter` e fazer o código para chamar a requisição DELETE, como no exemplo abaixo:

![](https://i.imgur.com/4HHgHrG.png)

Na linha 55, chamamos o método `deleteTarefa()` da `MainViewModel`, passando o id da tarefa atual. Isso foi feito dentro do método `onBindViewHolder`, onde temos acesso a um item único da lista.

Se formos testar o aplicativo, teremos um resultado parecido com esse:

![](https://i.imgur.com/9ErCAyA.png)

Clicando, então, para deletar uma tarefa, no nosso exemplo, excluiu uma das que tínhamos na lista.

**Com isso, finalizamos o nosso aplicativo!**
