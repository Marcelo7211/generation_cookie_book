# Criação do Layout do TODO e implementação do RecyclerView

Agora vamos desenvolver o **aplicativo base** do bootcamp para aprendermos todos os **fundamentos** necessários de Android. Para isso, construiremos um **TODO List**, que abordará os principais conceitos que veremos durante o curso.

Para iniciar nosso aplicativo, primeiro vamos criar o projeto do zero, implementar todas as **dependências** das tecnologias que utilizaremos e, logo após, implementar o **Componente de Navegação**, para gerar os layouts principais do aplicativo. Além disso, faremos a implementação do **RecyclerView** no App. um componente que gerará uma **listagem de itens**, para visualizar como as tarefas do TODO serão exibidas.

## 1. Criando o Projeto Inicial e Implementando o Gráfico de Navegação

1. Primeiramente, crie um projeto no modelo **Empty Activity** e mantenham o **Minimum SDK** na versão **8.0**

![](https://i.imgur.com/4sQGLu3.png)

2. Com o projeto aberto, na aba Project, clique com o botão direito no diretório `app`.
3. Na sequência, clique em **New → Android Resource File**

![](https://i.imgur.com/lTvpxRA.png)

4. Defina o nome do arquivo como **nav_graph** e o **Resource type** como **Navigation**. Isso criará o nosso **Gráfico de Navegação**.

![](https://i.imgur.com/61KJnsF.png)

5. Na sequência, é provável que uma janela abra para confirmar a adição das dependências no projeto, clique em **Ok**.

![](https://i.imgur.com/jJ88ddW.png)

Com isso, o Gradle começará a sincronizar e, finalizado esse processo, teremos o gráfico de navegação adicionado no projeto. 

![](https://i.imgur.com/UtVoyAg.png)

Agora, começaremos o processo de criação dos Fragments, para definir os layouts mais básicos do nosso aplicativo.



## 2. Criando Fragments de Listagem e Formulário de Tarefas

Com o Gráfico de Navegação bem implementado, vamos implementar dois novos Fragments no projeto.

1. Clique sobre o ícone de adição no gráfico de navegação e selecione **Create New Destination**

![](https://i.imgur.com/1kihqx0.png)

2. Selecione a opção **Fragment (Blank)** e clique em **Next**

![](https://i.imgur.com/iEASSrP.png)

3. Defina o nome do Fragment como `ListFragment` e clique em Finish.

![](https://i.imgur.com/CxfsggP.png)

4. Feito isso, nosso primeiro Fragment está criado.

![](https://i.imgur.com/zyl4iD3.png)

A partir desse momento, faremos o mesmo processo para criar o Fragment que cuidará do Formulário para o cadastro de novas Tarefas, para isso:

1. Clique sobre o ícone de adição no gráfico de navegação e selecione **Create New Destination**

2. Selecione a opção Fragment (Blank) e clique em Next

3. Defina o nome do Fragment como `FormFragment` e clique em Finish.

4. No final, teremos algo parecido com isso:

![](https://i.imgur.com/VYrSWNF.png)

Antes mesmo de criarmos o layout de cada um deles, vamos criar as conexões para fazer a navegação, desse modo:

![](https://i.imgur.com/OVFAvfm.png)

Para evitar que o osso aplicativo fique gerando uma **pilha infinita** de Fragments, vamos adicionar ainda um **Pop Behavior** na ação para navegar de volta para o **listFragment**, adicionando o **PopUpTo** e **PopUpToInclusive**

![](https://i.imgur.com/80W4kGj.png)

[Documentação sobre Navegação](https://developer.android.com/guide/navigation/navigation-navigate)

Finalizado essa etapa, agora podemos cuidar dos layouts de cada Fragment



## 3. Criando o Layout dos Fragments

Vamos agora criar o layout onde ficará a lista e o formulário de Tarefas. 

1. Acesse a aba Project e vá em **res → layout** e acesse o xml do Fragment de Lista (no nosso exemplo, `fragment_list.xml`)

![](https://i.imgur.com/CAZiIOC.png)

2. Aberto o Layout, clique com o botão direito sobre o FrameLayout, dentro da Component Tree, e selecione a opção ConvertView

![](https://i.imgur.com/r0kFJKe.png)

3. Feito isso, selecione a opção **ConstraintLayout** e clique em **Apply**

![](https://i.imgur.com/38wlsBE.png)

4. Com o layout convertido, construa um layout parecido com esse:

![](https://i.imgur.com/bHQNwSL.png)

Perceba, analisando a Component Tree, que adicionamos um RecyclerView no projeto e um FloatingActionButton (FAB), que está com um ícone de +

Não se esqueça de criar esse ícone antes mesmo de adicionar o FAB.

Só precisamos agora construir o layout de formulário e para isso:

1. Acesse a aba Project e vá em **res → layout** e acesse o xml do Fragment de Formulário (no nosso exemplo, `fragment_form.xml`)

2. Aberto o Layout, clique com o botão direito sobre o FrameLayout, dentro da **Component Tree**, e selecione a opção **ConvertView**

3. Feito isso, selecione a opção **ConstraintLayout** e clique em **Apply**

4. Com o layout convertido, construa um layout parecido com esse:

![](https://i.imgur.com/TRdnFpl.png)

A Component Tree deverá estar parecida com essa:

![](https://i.imgur.com/6K7xa5i.png)

Perceba que adicionamos vários objetos do tipo `EditText` para criar as caixas de texto onde o usuário adicionará algumas informações da Tarefa que será cadastrada

Adicionamos um `Switch` para definir se a Tarefa estará em andamento ou não, além de de um `Spinner` que futuramente listará as categorias disponíveis no aplicativo e um `Button` que salvará a tarefa e fará a navegação de volta para o Fragment de Listagem.



### 3.2. Adicionando o NavHostFragment

Para vincular o nosso **Gráfico de Navegação** em um container que exibirá os nossos fragments, precisaremos do **NavHostFragment** para cuidar disso.

1. Abra o arquivo `activity_main.xml`
2. Exclua o objeto **TextView** que é criado por padrão
3. Dentro da Pallete, acesse o componente NavHostFragment

![](https://i.imgur.com/yBCiQ7O.png)

4. Em seguida, adicione ele no Layout e selecione o `nav_graph.xml` criado anteriormente como o **Gráfico de Navegação** desse componente.

![](https://i.imgur.com/KJ1Pv8y.png)

5. Clique em Ok, aplique as Constraints no componente e, no final, teremos um resultado parecido com esse:

![](https://i.imgur.com/wqZYadS.png)





## 4. Adicionando o ViewBinding no projeto

Antes de começar a fazer a parte lógica do nosso aplicativo, vamos habilitar o recurso de `ViewBinding` no projeto, para não depender apenas do `findViewById()` para referênciar os componentes do layout.

[Documentação ViewBinding](https://developer.android.com/topic/libraries/view-binding?hl=pt-br)

1. Abra o pacote Gradle Scripts e, em seguida, o arquivo `Build.Gradle (Module: Projeto.app)`

![](https://i.imgur.com/lfUsSrE.png)

2. Dentro do bloco `android{}`, adicione o seguinte código:

![](https://i.imgur.com/NE5UO0F.png)

3. Clique na opção de Sync Now e aguarde a sincronização ser finalizada.



### 4.2. Configurando o ViewBinding nos Fragments do Projeto

Com o ViewBinding implementado, só falta fazer com que o Fragment de Listagem receba esse recurso, para isso:

1. Abra o arquivo `ListFragment`. 

![](https://i.imgur.com/6m1PIAX.png)

2. Por padrão, ele virá com muito código que não precisaremos utilizar, pois só o que importa para esse momento, por enquanto, é o método `onCreateView()`. Para isso substitua esse código todo:

![](https://i.imgur.com/jnLALba.png)

Por esse:

![](https://i.imgur.com/8RTv9Ih.png)



4. Agora só basta configurar o ViewBinding, dessa forma:

![](https://i.imgur.com/OfsK2b5.png)

Na **linha 12**, criamos um atributo `binding`, do tipo `FragmentListBinding`, que referenciará todos os componentes do `fragment_list.xml`.  Além disso, adicionamos a palavra reservada lateinit, para podermos inicializar esse atributo dentro do método `onCreateView()` 

Na **linha 19**, utilizamos o método `inflate()` da classe `FragmentListBinding`, para **inflar**  o layout `fragment_list.xml`.

Na **linha 21**, retornamos a raiz do atributo `binding`, que contém o layout que inflamos.

Com isso feito, poderemos agora acessar qualquer componente do `fragment_list.xml` utilizando o binding.



## 5. Adicionando o RecyclerView no Projeto

Agora chegou a hora de simularmos como ficará a listagem de itens no aplicativo e, para fazer a inserção dela no projeto, utilizaremos o componente RecyclerView.

Para uma implementação completa do RecyclerView precisaremos de:

- Uma Classe de Modelo (ou Model), que conterá os dados de cada item
- Um layouts, que será arepresentação como cada item aparecerá visualmente para o usuário
- Um Adapter, que fará o processamento dos dados dos itens
- Uma ViewHolder, que será responsável por exibir cada item em seu respectivo layout
- Um LayoutManager, que organizará os elementos da lista

[Documentação Oficial da RecyclerView](https://developer.android.com/guide/topics/ui/layout/recyclerview?hl=pt-br)



### 5.2. Criando Classe de Modelo

Uma tarefa, no modelo do nosso aplicativo, deverá conter algumas informações, sendo elas:

- Nome
- Descrição
- Responsável
- Data
- Status
- Categoria

Então começaremos criando uma classe de modelo que possa gerar objetos contendo essas informações:

1. Clique com o botão direito sobre o pacote principal do aplicativo (em nosso exemplo: **com.example.todomobile**)
2. Na sequência clique em **New  → Package**

![](https://i.imgur.com/d0nAiqB.png)

3. Defina o nome do pacote como `model`

![](https://i.imgur.com/7lpdObF.png)

4. Clique com o botão direito sobre o pacote `model`e vá em **New → Kotlin Class/File**

![](https://i.imgur.com/oA4T9YH.png)

5. Na janela de criação, mantenha o arquivo como `class`, com o nome `Tarefa`

![](https://i.imgur.com/Ky9O5ga.png)

6. Dentro da classe `Tarefa`, adicione o código abaixo para criar o modelo:

![](https://i.imgur.com/Au25PZP.png)

> Perceba que aqui nós mantemos a classe como uma **data class** (ou **Classe de Dados**), para não precisarmos nos preocupar com getters, setters, toString() e assim por diante.



### 5.3. Criando Layout para os Itens

Criado nossa classe de modelo, vamos agora definir o layout que exibirá cada dado dos objetos `Tarefa` que adicionarmos no projeto. Mais para frente, esse será o layout base da nossa **ViewHolder**.

1. Clique com o botão direito no pacote `layout`, localizado no pacote `res`.
2. Na sequência, vá em **New  → Layout Resource File**

![](https://i.imgur.com/b4qNPVP.png)

3. Feito isso, configure o layout dessa forma:

![](https://i.imgur.com/pDrHYwm.png)

Perceba que definimos o Root element como `androidx.cardview.widget.CardView`, pois faremos cada tarefa aparecer em um card diferente, com um efeito interessante de sombreamento

4. Para fazer a exibição de cada dado da nossa classe de modelo `Tarefa`, criaremos um layout parecido com este:

![](https://i.imgur.com/o21I6kd.png)

>  Lembre que criamos o atributo `status`, no modelo `Tarefa`, como `Boolean`. Para fazermos a exibição desse atributo utilizaremos um `Switch`, que ficará ligado se o `status` for `true` e desligado se for `false`.

5. Para aumentar o efeito de sombreamento, selecione o componente de `CardView`, por meio da **Component Tree**, e mude o atributo de **cardElevation** para **7dp**

![](https://i.imgur.com/WFKAi8S.png)



### 5.4. Inserindo o Adapter e a ViewHolder

Agora que já temos uma classe para o modelo das tarefas e um layout para exibir cada uma, criaremos o **Adapter** e a **ViewHolder** no projeto para processar os dados desses itens.

1. Clique com o botão direito sobre o pacote principal do aplicativo (em nosso exemplo: **com.example.todomobile**)
2. Na sequência clique em **New  → Package**

![](https://i.imgur.com/eznvyDk.png)

3. Defina o nome do pacote como `adapter`

![](https://i.imgur.com/JWle7L5.png)

4. Clique com o botão direito sobre o pacote `adapter`e vá em **New → Kotlin Class/File**

![](https://i.imgur.com/vJEuLTm.png)

5. Na janela de criação, mantenha o arquivo como `class`, com o nome `TarefaAdapter`

![](https://i.imgur.com/bAO6NBu.png)

No fim, teremos algo parecido com isso:

![](https://i.imgur.com/juvRQDr.png)

Para fazer a nossa classe `TarefaAdapter` ser, de fato, um **Adapter**, herdaremos os atributos e métodos da classe `RecyclerView.Adapter`, desse modo:

![](https://i.imgur.com/Met9hdp.png)

O problema é que  agora temos dois erros. Como a classe `Adapter` tem alguns métodos abstratos, teremos que implementá-los na nossa classe, porém, antes disso, ainda teremos que passar um `ViewHolder` para ela, dentro da tag `<>`, que também está indicando um erro.

Essa **ViewHolder** nós criaremos do zero e será por meio dela que vamos referenciar **cada componente** do `card_layout.xml`.

1. Dentro da classe TarefaAdapter, crie uma nova classe chamada `TarefaViewHolder`, dessa forma:

![](https://i.imgur.com/temLFui.png)

Perceba que, para a classe `TarefaViewHolder` se comportar como uma `ViewHolder`, precisamos extender a classe `RecyclerView.ViewHolder`, que recebe um objeto do tipo `View`. Esse objeto será o layout de cada um dos itens da lista no futuro.

2. Para referenciarmos cada componente do `card_layout.xml`, utilizaremos o objeto `view`, que, por sua vez, tem acesso ao método `findViewById()`, dessa forma:

![](https://i.imgur.com/sgz6BN4.png)

Nas **linhas 13-19**, criamos objetos para referenciar os componentes do `card_layout.xml`. Com eles, no futuro, conseguiremos exibir cada dado dos objetos do tipo `Tarefa`.

3. Em seguida, adicionaremos a `TarefaViewHolder` dentro da Tag do `Adapter`.

![](https://i.imgur.com/yh9fhNg.png)

4. Ainda temos um erro na classe e, para corrigir, mantenha o mouse em cima de onde o erro está sendo acusado e clique sobre "implement members"

   ![](https://i.imgur.com/DZ0agNz.png)

5. Selecione os métodos que estão faltando e clique em "Ok"

![](https://i.imgur.com/p3XHuIj.png)

6. Feito isso, três novos métodos serão adicionados na classe

![](https://i.imgur.com/txMiOjs.png)

Na **linha 23**, temos o método `onCreateViewHolder()`, que exibirá os itens da RecyclerView em um layout específico.

Na **linha 27**, temos o método `onBindViewHolder()`, que processará os dados de um item e os exibirá nos componentes do layout configurado no `onCreateViewHolder()`.

Na **linha 31**, temos o método `getItemCount()`, que vai dizer quantos itens serão gerados pelo RecyclerView.

Todos os três métodos vão configurar os itens da RecyclerView com base em uma listagem de itens. Desse modo, vamos criar um atributo que armazenará uma lista vazia, do tipo `Tarefa`

![](https://i.imgur.com/u8IceTT.png)

> Perceba que para criar uma lista vazia, utilizamos o método `emptyList()`, indicando `Tarefa` como o tipo de lista a ser criada.

Feito isso, vamos configurar o método onCreateViewHolder para receber o `card_layout.xml`, desse modo:

![](https://i.imgur.com/TJxJ514.png)

Na **linha 28**, criamos um objeto `layoutAdapter`. Em seguida, usamos a classe `LayoutInflater` para termos acesso ao método `from()`, que indicará onde o item da RecyclerView será criado.

Na **linha 29**, utilizamos o método `inflate()`, para inflarmos o `card_layout.xml` cada vez que um item for criado.

Na **linha 31**, retornamos um objeto do tipo TarefaViewHolder, passando o `layoutAdapter` em seu construtor, indicando que criaremos, então, cada **ViewHolder** com base no `card_layout.xml`.

Agora que já temos configurado o layout onde cada item será gerado, precisamos processar os dados dos objetos da lista. Para isso, vamos configurar o método `onBindViewHolder()`, como no código abaixo:

![](https://i.imgur.com/9Zv8Uvi.png)

Na **linha 35**, criamos um objeto `tarefa`, recuperando um item da `listTerfas` na posição em que está sendo criado, utilizando o parâmetro `postition`. 

Nas **linhas 37-42**, utilizamos o `holder` para recuperar os componentes que configuramos anteriormente e alterar seus atributos com os atributos correspondentes do objeto `tarefa`.

A partir desse momento já sabemos exatamente como cada atributo dos objetos do tipo `Tarefa` serão processados nos componentes do `card_layout.xml`.

Feito isso, só precisamos agora configurar o `getItemCount()`, como no código abaixo:

 ![](https://i.imgur.com/5LEvV8m.png)

Com isso, conseguiremos retornar com exatidão a quantidade de itens que deverão ser criadas dentro do RecyclerView.

Perceba que, por enquanto, por mais que estajamos processando os dados da lista, ela ainda é uma **lista vazia**. Para mudar esse cenário, criaremos um **método** para alterar o atributo `listTarefas` com base em uma listagem de tarefas externa, como no código abaixo:

![](https://i.imgur.com/ijWuhSK.png)

Na **linha 49**, criamos o método `setLista()`, adicionando um parâmetro `tarefas` do tipo `List<Tarefa>`.

Na **linha 50**, acessamos o atributo `listTarefas` e alteramos o seu valor com base no parâmetro `tarefas`.

Na **linha 51**, utilizamos o método `notifyDataSetChanged()`, para imediatamente alterar todos os itens do RecyclerView com base na nova lista.



### 5.5. Inserindo Adapter e Layout Manager na RecyclerView

Com o Adapter finalizado, precisamos agora configurar o componente do **RecyclerView** na unidade lógica do Fragment de Listagem, para exibir os itens da maneira correta.

Acesse a classe `ListFragment` e adicione as seguintes linhas de código:

![](https://i.imgur.com/bq0csBw.png)

Na **linha 45**, criamos um objeto do tipo `TarefaAdapter`.

Na **linha 47**, definimos o atributo `layoutManager` da `recyclerTarefa` para receber um `LinearLayoutManager()`, que indicará que os itens serão criados de forma linear, ou seja, um em baixo do outro.

Na **linha 48**, definimos o atributo `adapter` do `recyclerTarefa` para receber o objeto `tarefaAdapter`. Desse modo, o `recyclerTarefa` processará os itens com base no `TarefaAdapter` que criamos anteriormente.

Na **linha 49**, utilizamos o método `setHasFixedSize(true)`, indicando que o componente `recyclerTarefa` manterá sempre um tamanho fixo.

 

## 6. Criando Teste com a RecyclerView

Agora a **RecyclerView** já está totalmente adicionada no nosso projeto e configurada da maneira correta, porém se executarmos o aplicativo agora não veremos nenhuma diferença, isso porque não temos dados para adicionar na lista.

Para darmos uma olhada em como a nossa lista exibe as tarefas, vamos criar uma lista estática de objetos do tipo `Tarefa` e adicioná-la no `TarefaAdapter`.

### 6.1. Criando Lista Estática de Tarefas

Para termos uma noção de como os itens aparecerão na nossa lista, criaremos alguns objetos do tipo `Tarefa`, que popularão o RecyclerView no futuro.

1. Abra a classe `ListFragment`
2. Crie uma listagem de itens do tipo `List`, adicionando dois objetos do tipo `Tarefa` na lista, desse modo:

![](https://i.imgur.com/F3KxmKp.png)

Na **linha 22**, criamos um atributo `listTarefa` que recebe o método `listOf()`, que criará um objeto `List`

Nas **linhas 23-38**, populamos o objeto `List` com dois objetos do tipo `Tarefa`, que simularão duas tarefas que serão exibidas na lista.

> Lembrando que esses itens **nunca mudarão**, pois são apenas **objetos estáticos**. Mais para frente, todos os itens que popularão o RecyclerView serão recuperados de um **banco de dados externo**.

Agora só falta adicionarmos esses itens na lista do RecyclerView e faremos isso através do objeto `tarefaAdapter`, chamando  o método `setLista()`, desse modo:

![](https://i.imgur.com/Aqj7Sq3.png)



### 6.2. Testando o Aplicativo

Feito tudo isso, vamos verificar se o RecyclerView funciona com a lista de objetos estáticos que criamos.

Ao executar o aplicativo, teremos um resultado parecido com esse:

![](https://i.imgur.com/2adbwlF.png)

Percebam que realmente os itens aparecem com base no card que construímos e, além disso, todos os dados, das duas tarefas que configuramos, são apresentados corretamente!

Lembrem-se que o que fizemos na penúltima etapa foi **apenas um teste**, porque essas tarefas serão recuperadas através de um **Banco de Dados externo** no futuro.

Então, para seguir com as próximas etapas, é viável apagarmos esse teste que fizemos e manter apenas o essencial para o RecyclerView funcionar, desse modo:

![](https://i.imgur.com/c5eIoM4.png)

Com isso, finalizamos a implementação do RecyclerView no projeto. As próximas etapas serão a implementação da **Navegação e do Retrofit** no projeto!