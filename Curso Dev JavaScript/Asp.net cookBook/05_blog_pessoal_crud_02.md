﻿﻿﻿﻿﻿

<h1>Projeto 02 - Blog Pessoal - CRUD 02</h1>

O que veremos por aqui:

1. Apresentação do Recurso Tema
2. Criar a estrutura de Pacotes
3. Criar a Classe Model Tema

<h2>1. O Recurso Tema</h2>

Nesta etapa vamos começar a construir o Recurso Tema. Veja o Diagrama de Classes abaixo: 

<div align="center"><img src="https://i.imgur.com/1xE9x3f.png" title="source: imgur.com" width="75%"/></div>

Primeiro vamos construir a **Classe Tema**, que servirá de modelo para construir a tabela **tb_tema** (Entidade) dentro do nosso Banco de dados **db_blogpessoal**. Os campos (Atributos) da tabela serão os mesmos que estão definidos no Diagrama de Classes acima. Na próxima etapa vamos construir a **Interface TemaRepository**, que irá nos auxiliar na interação com o Banco de dados. Os métodos descritos no Diagrama de Classes serão implementados na etapa seguinte, na **Classe TemaController**.

Depois de criar a Classe Model Postagem, vamos executar o projeto Blog Pessoal no Visual Studio. Após a execução veremos que será criado no MySQL o Banco de dados **db_blogpessoal** e a tabela **tema****. Veja abaixo como ficará a estrutura da nossa tabela através do **Diagrama de Entidade e Relacionamentos (DER)**:

<div align="center"><img src="https://i.imgur.com/6x7HnDI.png" title="source: imgur.com" width="75%"/></div>

O **Dicionário de dados da nossa tabela tb_tema** será o seguinte:

| Atributo      | Tipo de dado | Descrição           | Chave |
| ------------- | ------------ | ------------------- | ----- |
| **id**        | int          | Identificador único | PK    |
| **descricao** | varchar(100) | Descrição do Tema   |       |



| Camada         | Descrição                                                    |
| -------------- | ------------------------------------------------------------ |
| **Context** | Camada responsável pela comunicação de nossa aplicação ao banco de dados. |
| **Model** | Camada responsável pela abstração dos nossos Objetos em registros das nossas tabelas, que serão geradas no Banco de dados. As Classes criadas nesta camada representam os objetos que serão persistidos no Banco de dados. |
| **Repository** | Camada responsável por implementar as Interfaces, que contém diversos métodos pré-implementados para a  manipulação de dados de uma entidade, como métodos para salvar, deletar,  listar e recuperar dados da classe. |
| **Controller** | Camada responsável por receber todas as Requisições HTTP (HTTP Request), enviadas por um Cliente HTTP (Postman ou o Front-end da API), para a nossa aplicação e responder (HTTP Response) as requisições de acordo com o resultado do processamento da requisição no Back-end. |
| **Startup** | Camada de inicialização do projeto. |



<h2>👣 Passo 01 - Criar a Model Tema</h2>

<div align="center"><img src="https://i.imgur.com/zDnJfwO.png" title="source: imgur.com" /></div>

Se ainda estiver criado, crie uma classe c**#** com o nome Tema na pasta **model**.

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text.Json.Serialization;
using System.Threading.Tasks;

namespace blogPessoal.Model
{
    public class Tema
    {
        public int Id { get; set; }
        
        [StringLength(140)]
        public string Descricao { get; set; }

    }
}
```

Configure a pasta como esta descrito acima

O **Entity Framework** irá mapear o dados a model e seus atributos em C# e transcrever os tipos para uma tabela de banco de dados com suas respectivas colunas e seus tipos.

| Atributo      | Tipo de dado C# | Tipo de dado MySQL |
| ------------- | --------------- | ------------------ |
| **Id**        | int             | int                |
| **Descricao** | string          | varchar(100)       |

# validação de modelo no ASP.NET

| Anotação         | Significado                                           |
| ---------------- | ----------------------------------------------------- |
| [StringLength()] | determina o tamanho maximo do atributo do tipo string |

para saber mais validações de modelos no ASP.NET veja a documentação abaixo:

<div align="left"> <a href="https://docs.microsoft.com/pt-br/aspnet/core/mvc/models/validation?view=aspnetcore-6.0" target="_blank"><b>Documentação site Oficial: Entity FrameworkCore validação de modelo no ASP.NET</b></a>
<br />


| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao criar a Camada Model, não esquecer dos metodos get e setter, anotações e os tipos corretos para os seus  atributos * </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<h2>👣 Passo 02 - Criar a classe AppContext</h2>

<div align="center"><img src="https://i.imgur.com/zDnJfwO.png" title="source: imgur.com" /></div>

Se ainda estiver criado, crie uma classe c# com o nome AppContext.cs na pasta Data.

```c#

using blogPessoal.Model;
using Microsoft.EntityFrameworkCore;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace blogPessoal.Data
{
    public class AppContext : DbContext
    {

        public AppContext(DbContextOptions<AppContext> options) : base(options)
        {

        }

        public DbSet<Tema> Temas { get; set; }

    }
}
```

Configure a pasta como esta descrito acima

A classe appContesxt herda de DbContext 

Uma instância DbContext representa uma combinação da unidade de padrões de trabalho e de repositório, de modo que ele possa ser usado para consultar de um banco de dados e agrupar alterações que serão gravadas novamente no armazenamento como uma unidade. Ou seja é tem como função mapear as models para construir as tabelas no banco de dados.



método DbSet<Tema> Temas mapeia a model tema para ser criado a tabela no banco de dados. 




| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao criar a Camada AppContext, não esquecer dos metodos public DbSet<Tema> Temas { get; set; } * </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |



<h2>👣 Passo 03 - Configurando a classe Startup</h2>



A classe Startup.cs tem como função de executar rotinas em sua aplicação no momento da inicialização, um exemplo é o que faremos nesta aula, inicializar a comunicação o banco de dados no momento que aplicação for executada.



 Para isso configure  o método ConfigureServices como está descrito no código abaixo:



```c#
 public void ConfigureServices(IServiceCollection services)
        {

            services.AddCors();
            services.AddControllers();

            services.AddDbContext<Data.AppContext>(options => options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
            services.AddScoped<ITemaRepository, TemaRepository>();
            services.AddSwaggerGen(c =>
            {
                c.SwaggerDoc("v1", new OpenApiInfo { Title = "blogPessoal", Version = "v1" });
            });
        }
```



nesse método estamos determinando que a aplicação será habilitada o crossOrigin para qualquer origem que for acessa-la.

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> Caso tenha alguma duvida a respeito Cross origin leia a documentação do link abaixo</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<div align="left"> <a href="https://docs.microsoft.com/pt-br/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api" target="_blank"><b>Documentação oficial: CrossOrigin no .NET</b></a>
<br />

Estamos habilitando a comunicação com a camada controller.

Estamos determinando que a aplicação terá comunicação um banco de dados  SqlServer onde será usado como script de comunicação o atributo DefaultConnection do arquivo appsettings.json

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=DESKTOP-8KO7ED6;Initial Catalog=db_blog_pessoal;Integrated Security=True"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}

```

ainda no método ConfigureServices no final do método estamos habilitando o sistema de documentação do swagger definindo o nome do projeto como BlogPessoal.

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> Caso tenha alguma duvida a respeito de documentação automática via swagger leia a documentação abaixo sobre swagger</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<div align="left"> <a href="https://docs.microsoft.com/pt-br/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-6.0n" target="_blank"><b>Documentação oficial: swagger no .NET</b></a>
<br />

Para configurar o swagger no Asp.net utilizamos a técnica de Lambda expression. (expressão lambda).

Você usa uma *expressão lambda* para criar uma função anônima ( ou seja sem declarar nome). Use o [operador de declaração lambda `=>`](https://docs.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/lambda-operator) para separar a lista de parâmetros de lambda do corpo. 

```c#
options => options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")

c  =>  { c.SwaggerDoc("v1", new OpenApiInfo { Title = "blogPessoal", Version = "v1" }
```

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> Caso tenha alguma duvida a respeito de  Lambda expression. (expressão lambda), leia a documentação abaixo sobre Lambda expression. (expressão lambda)</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<div align="left"> <a href="https://docs.microsoft.com/pt-br/dotnet/csharp/language-reference/operators/lambda-expressions" target="_blank"><b>Documentação oficial: Lambda expression. (expressão lambda)</b></a>
<br />

Agora vamos configurar o método Configure:

```c#
public void Configure(IApplicationBuilder app, IWebHostEnvironment env, Data.AppContext context)
        {
            if (env.IsDevelopment())
            {
                context.Database.EnsureCreated();
                app.UseDeveloperExceptionPage();
                app.UseSwagger();
                app.UseSwaggerUI(c => c.SwaggerEndpoint("/swagger/v1/swagger.json", "blogPessoal v1"));
            }

            app.UseRouting();

            app.UseCors(x => x
                .AllowAnyOrigin()
                .AllowAnyMethod()
                .AllowAnyHeader());

            app.UseAuthorization();

            app.UseEndpoints(endpoints =>
            {
                endpoints.MapControllers();
            });
        }
```



no método useCors estamos determinando que a api estará habilitada para qualquer fonte externa pela body header e métodos do protocolo HTTP.



Código completo da class Startup.cs

```c#
using blogPessoal.Repository;
using blogPessoal.Repository.impl;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc;
using Microsoft.EntityFrameworkCore;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;
using Microsoft.OpenApi.Models;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace blogPessoal
{
    public class Startup
    {
        public Startup(IConfiguration configuration)
        {
            Configuration = configuration;
        }

        public IConfiguration Configuration { get; }

        // This method gets called by the runtime. Use this method to add services to the container.
        public void ConfigureServices(IServiceCollection services)
        {

            services.AddCors();
            services.AddControllers();

            services.AddDbContext<Data.AppContext>(options => options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
            services.AddScoped<ITemaRepository, TemaRepository>();
            services.AddSwaggerGen(c =>
            {
                c.SwaggerDoc("v1", new OpenApiInfo { Title = "blogPessoal", Version = "v1" });
            });
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IWebHostEnvironment env, Data.AppContext context)
        {
            if (env.IsDevelopment())
            {
                context.Database.EnsureCreated();
                app.UseDeveloperExceptionPage();
                app.UseSwagger();
                app.UseSwaggerUI(c => c.SwaggerEndpoint("/swagger/v1/swagger.json", "blogPessoal v1"));
            }

            app.UseRouting();

            app.UseCors(x => x
                .AllowAnyOrigin()
                .AllowAnyMethod()
                .AllowAnyHeader());

            app.UseAuthorization();

            app.UseEndpoints(endpoints =>
            {
                endpoints.MapControllers();
            });
        }
    }
}

```



<h2>👣 Passo 04 - Criando repository</h2>

Agora vamos criar a Classe Model que chamaremos de **Postagem**.

1. Clique com o botão direito sobre o projeto e crie uma pasta Repository
2. Dentro da pasta repository crie uma interface chamada ITemaRepository

3. Dentro da pasta repository crie uma pasta chamada impl
4. Dentro da pasta impl crie uma pasta chamada TemaRepository



<div align="center"><img src="https://i.imgur.com/tkqEXaH.png" title="source: imgur.com" /></div>

<h2>👣 Passo 05 - editando os arquivos do repository</h2>

1. Edite o arquivo ITemaRepository como esta descrito abaixo.

   ```c#
   using blogPessoal.Model;
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Threading.Tasks;
   
   namespace blogPessoal.Repository
   {
       public interface ITemaRepository
       {
           List<Tema> GetAll();
   
           Tema Get(int Id);
   
           List<Tema> GetByDescricao(string descricao);
   
           Tema Create(Tema tema);
   
           Tema Update(Tema tema);
   
           void Delete(int Id);
       }
   }
   ```

   2. No arquivo TemaRepository implemente a interface ITemaRepository  como descrito abaixo

      ```C#
      using blogPessoal.Model;
      using System.Collections.Generic;
      
      namespace blogPessoal.Repository.impl
      {
          public class TemaRepository : ITemaRepository
          {
              public Tema Create(Tema tema)
              {
                  throw new System.NotImplementedException();
              }
      
              public void Delete(int Id)
              {
                  throw new System.NotImplementedException();
              }
      
              public Tema Get(int Id)
              {
                  throw new System.NotImplementedException();
              }
      
              public List<Tema> GetAll()
              {
                  throw new System.NotImplementedException();
              }
      
              public List<Tema> GetByDescricao(string descricao)
              {
                  throw new System.NotImplementedException();
              }
      
              public Tema Update(Tema tema)
              {
                  throw new System.NotImplementedException();
              }
          }
      }
      
      ```

      3. injete o AppContext como dependência do TemaRepository que criamos na camada anterior.

         **De forma mais simples injeção de dependencia é uma forma de trazer uma informação de uma camada pro exemplo AppContext para outra Repostory**

      
      
      <div align="center"><img src="https://i.imgur.com/t21gr2B.png" title="source: imgur.com" /></div>
      
      
      
      ```c#
      using blogPessoal.Model;
      using Microsoft.EntityFrameworkCore;
      using System.Collections.Generic;
      
      namespace blogPessoal.Repository.impl
      {
          public class TemaRepository : ITemaRepository
          {
              public readonly Data.AppContext _context;
      
              public TemaRepository(Data.AppContext context)
              {
                  _context = context;
              }
      
              public Tema Create(Tema tema)
              {
                  throw new System.NotImplementedException();
              }
      
              public void Delete(int Id)
              {
                  throw new System.NotImplementedException();
              }
      
              public Tema Get(int id)
              {
                  return _context.Temas.ToListAsync().Result;
              }
      
              public List<Tema> GetAll()
              {
                  return _context.Temas.ToListAsync().Result;
              }
      
              public List<Tema> GetByDescricao(string descricao)
              {
                  throw new System.NotImplementedException();
              }
      
              public Tema Update(Tema tema)
              {
                  throw new System.NotImplementedException();
              }
          }
      }
      
      ```
      
      
      
      
      | <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> *Caso tenha curiosidade para se aprofundar no assunto  injeção de dependência fazer a leitura da documentação sobre.* </div> |
      | ------------------------------------------------------------ | ------------------------------------------------------------ |
      
      <div align="left"> <a href="https://docs.microsoft.com/pt-br/dotnet/core/extensions/dependency-injection" target="_blank"><b>Documentação oficial: Injeção de dependência no .NET</b></a>
      <br />
      
      | <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> *Lembrando que o aprofundamento de injeção de dependência NÃO É UMA COMPETENCIA PARA UMA PESSOAL PROFISSIONAL EM DESENVOLVIMENTO C# JUNIOR, esse conceito precisa de aprofundamento com tempo e experiência, super importante não pular etapas.*</div> |
      | ------------------------------------------------------------ | ------------------------------------------------------------ |

​        

4. Agora vamos construir os métodos getAll e Get do Tema Repository.



```c#
using blogPessoal.Model;
using Microsoft.EntityFrameworkCore;
using System.Collections.Generic;

namespace blogPessoal.Repository.impl
{
    public class TemaRepository : ITemaRepository
    {
        public readonly Data.AppContext _context;

        public TemaRepository(Data.AppContext context)
        {
            _context = context;
        }

        public Tema Create(Tema tema)
        {
            throw new System.NotImplementedException();
        }

        public void Delete(int Id)
        {
            throw new System.NotImplementedException();
        }

        public Tema Get(int id)
        {
            try{
                var TemaReturn = _context.Temas.FirstAsync(i => i.Id == id).Result;
                return TemaReturn;
            }catch 
            {
                return null;
            }           

        }

        public List<Tema> GetAll()
        {
            return _context.Temas.ToListAsync().Result;
        }

        public List<Tema> GetByDescricao(string descricao)
        {
            throw new System.NotImplementedException();
        }

        public Tema Update(Tema tema)
        {
            throw new System.NotImplementedException();
        }
    }
}

```



<h2>👣 Passo 06 - Criando Controller</h2>		

​	Agora vamos criar a classe controller:

<div align="center"><img src="https://i.imgur.com/1FOKUzv.png" title="source: imgur.com" /></div>

1: crie um controlador chamado TemaController.cs

2: implemente ITemaRepository como dependência e coloque as dependências [Route] [ApiController] como descrito no código abaixo:

```c#
using blogPessoal.Model;
using blogPessoal.Repository;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace blogPessoal.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class TemaController : ControllerBase
    {

        private readonly ITemaRepository _temaRepository;

        public TemaController(ITemaRepository temaRepository)
        {
            _temaRepository = temaRepository;
        }
    }

}

```

2. construa o método GetAllTemas como descrito no código abaixo:

```c#
using blogPessoal.Model;
using blogPessoal.Repository;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace blogPessoal.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class TemaController : ControllerBase
    {

        private readonly ITemaRepository _temaRepository;

        public TemaController(ITemaRepository temaRepository)
        {
            _temaRepository = temaRepository;
        }
        
        [HttpGet]
        public ActionResult<List<Tema>> GetAllTemas()
        {
            return Ok(_temaRepository.GetAll());
        }
    }
		
}



```

O método ActionResult<Tema> GetAllTemas()  devolve um ActionResult que retorna um OK 200 com uma lista de todos os temas cadastrados na base de dados.



 Os tipos `ActionResult` representam vários códigos de status HTTP. Qualquer classe não abstrata derivada de é `ActionResult` qualificada como um tipo de retorno válido. Alguns tipos de retorno comuns nessa categoria são [BadRequestResult](https://docs.microsoft.com/pt-br/dotnet/api/microsoft.aspnetcore.mvc.badrequestresult) (400), [NotFoundResult](https://docs.microsoft.com/pt-br/dotnet/api/microsoft.aspnetcore.mvc.notfoundresult) (404) e [OkObjectResult](https://docs.microsoft.com/pt-br/dotnet/api/microsoft.aspnetcore.mvc.okobjectresult) (200). Como alternativa, os métodos de conveniência na [ControllerBase](https://docs.microsoft.com/pt-br/dotnet/api/microsoft.aspnetcore.mvc.controllerbase) classe podem ser usados para retornar `ActionResult` tipos de uma ação. Por exemplo, `return BadRequest();` é uma forma abreviada de `return new BadRequestResult();` .

<div align="left"> <a href="https://docs.microsoft.com/pt-br/aspnet/core/web-api/action-return-types?view=aspnetcore-6.0" target="_blank"><b>Documentação site Oficial: Tipos de retorno de ação do controlador na API Web do ASP.NET Core</b></a>
<br />

​    

<h2>👣 Passo 07 - testando postman/swagger</h2>

1. Execute o método  get/api/tema repare o status 200 e o response body com array vazio

<div align="center"><img src="https://i.imgur.com/y2EbsPq.png" title="source: imgur.com" /></div>

<h2>👣 Passo 08 - Incluindo dados pelo banco de dados e testando postman/swagger</h2>

Entre no sql server management studio e insira um tema na tabela tema;

<div align="center"><img src="https://i.imgur.com/xuCxiya.png" title="source: imgur.com" /></div>

```sql
USE [db_blog_pessoal]
GO
INSERT INTO [dbo].[Temas] ([descricao] ) VALUES
('ASP.NET');
```

<div align="center"><img src="https://i.imgur.com/y2EbsPq.png" title="source: imgur.com" /></div>

​	Teste novamente via swagger ou postman

<div align="center"><img src="https://i.imgur.com/0YwdudP.png" title="source: imgur.com" /></div>

<h2>👣 Passo 09 - Construindo a funcionalidade de busca de tema por Id GetByIdTema</h2>



### Edite o método de GetById do repository.

```c#
using blogPessoal.Model;
using Microsoft.EntityFrameworkCore;
using System.Collections.Generic;

namespace blogPessoal.Repository.impl
{
    public class TemaRepository : ITemaRepository
    {
        public readonly Data.AppContext _context;

        public TemaRepository(Data.AppContext context)
        {
            _context = context;
        }

        public Tema Create(Tema tema)
        {
            throw new System.NotImplementedException();
        }

        public void Delete(int Id)
        {
            throw new System.NotImplementedException();
        }

        public Tema Get(int id)
        {
            try{
                var TemaReturn = _context.Temas.FirstAsync(i => i.Id == id).Result;
                return TemaReturn;
            }catch 
            {
                return null;
            }   

        }

        public List<Tema> GetAll()
        {
            return _context.Temas.ToListAsync().Result;
        }

        public List<Tema> GetByDescricao(string descricao)
        {
            throw new System.NotImplementedException();
        }

        public Tema Update(Tema tema)
        {
            throw new System.NotImplementedException();
        }
    }
}

```

O método Get(int) id  tenta buscar um tema por id através da estrutura try catch caso ele não consiga ele devolve no retorno método um objeto nullo;

para ser validado na camada seguinte



### Construindo o método de GetById do controller.

```c#
using blogPessoal.Model;
using blogPessoal.Repository;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace blogPessoal.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class TemaController : ControllerBase
    {

        private readonly ITemaRepository _temaRepository;

        public TemaController(ITemaRepository temaRepository)
        {
            _temaRepository = temaRepository;
        }

        [HttpGet]
       	public List<Tema> GetAllTemas()
        {
            return Ok(_temaRepository.GetAll());
        }

        [HttpGet("{id}")]
        public ActionResult<Tema> GetByIdTema(int id)
        {
            var tema = _temaRepository.Get(id);
            if (tema == null)
            {
            return NotFound();
            }
            else
            {
                return Ok(tema);
            }
          
        }
    }

}

```



O método ActionResult<Tema> GetByIdTema(int id)  devolve um ActionResult, caso o objeto tema no método get do repository retornar nulo o tipo de ActionResult devolvido é um notFound() 404 objeto não encontrado, caso o objeto esteja presente retorna um OK 200 com objeto tema na body da resposta.



<h2>👣 Passo 10 -Testando a funcionalidade de busca de tema por Id GetByIdTema</h2>

Entre no postman e teste  o método getByIdTema.



acesse o o end point:

http://localhost:5000/api/Tema/3

1. Pesquise por Id 3

2. Selecione o verbo get
3. Clique em Send

<div align="center"><img src="https://i.imgur.com/deQ5y9F.png" title="source: imgur.com" /></div>



repare que ao pesquisar pelo tema de id 3, o back-end entrega uma mensagem com status HTTP 404

notFound isso ocorre porque não temos um tema cadastrado com esse id;



<div align="center"><img src="https://i.imgur.com/EztKH0Y.png" title="source: imgur.com" /></div>

acesse o o end point:

http://localhost:5000/api/Tema/1

1. Pesquise por Id 1

2. Selecione o verbo get
3. Clique em Send



Repare que na area de body do response ele entrega um status 200 com um recurso tema chamado ASP.NET de id 1, isso ocorre porque temos cadastrado no banco de dados um tema.



<h2>👣 Passo 09 - Construindo a funcionalidade de cadastro de tema e atualizar tema</h2>



### Edite o método de cadastro de tema e atualizar tema do repository.



```c#
using blogPessoal.Model;
using Microsoft.EntityFrameworkCore;
using System.Collections.Generic;

namespace blogPessoal.Repository.impl
{
    public class TemaRepository : ITemaRepository
    {
        public readonly Data.AppContext _context;

        public TemaRepository(Data.AppContext context)
        {
            _context = context;
        }

        public Tema Create(Tema tema)
        {
            Tema aux = _context.Temas.FirstOrDefaultAsync(c => 	 c.Id.Equals(tema.Id)).Result;
            if (aux != null)
                return aux;

            _context.Temas.Add(tema);
            _context.SaveChangesAsync();

            return tema;
        }

        public void Delete(int Id)
        {
            throw new System.NotImplementedException();
        }

        public Tema Get(int id)
        {
            try{
                var TemaReturn = _context.Temas.FirstAsync(i => i.Id == id).Result;
                return TemaReturn;
            }catch 
            {
                return null;
            }  

        }

        public List<Tema> GetAll()
        {
            return _context.Temas.ToListAsync().Result;
        }

        public List<Tema> GetByDescricao(string descricao)
        {
            throw new System.NotImplementedException();
        }

        public Tema Update(Tema tema)
        {
            _context.Entry(tema).State = EntityState.Modified;
            _context.SaveChangesAsync();

            return tema;
        }
    }
}

```

O método Create() cadastra um novo tema na tabela tema do banco de dados para isso, ele primeiro verifica se id esta nulo, porque para cadastrar um tema novo não precisamos de id por conta da função de auto increment,  ele adiciona o tema passado por parametro via método add() e salva as alterações.



O método Update() atualiza um tema que ja esteja cadastrado na tabela tema do banco de dados para isso, para isso ele utiiliza do método modified do objeto EntityState, que esta vindo por parametro, as alterações são salvadas através do método SaveChangesAsync()

<div align="left"> <a href="https://docs.microsoft.com/pt-br/aspnet/core/data/ef-mvc/crud?view=aspnetcore-5.0" target="_blank"><b>Documentação site Oficial: Crud em Ef core</b></a>
<br />


​    

<h2>👣 Passo 09 - Construindo a funcionalidade de cadastro de tema e atualizar tema no controller</h2>



Agora vamos construir o método PostTema([FromBody] Tema tema) e PutTema(int id, [FromBody] Tema tema)

```c#
using blogPessoal.Model;
using blogPessoal.Repository;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace blogPessoal.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class TemaController : ControllerBase
    {

        private readonly ITemaRepository _temaRepository;

        public TemaController(ITemaRepository temaRepository)
        {
            _temaRepository = temaRepository;
        }

        [HttpGet]
         public List<Tema> GetAllTemas()
        {
            return Ok(_temaRepository.GetAll());
        }

        [HttpGet("{id}")]
        public ActionResult<Tema> GetByIdTema(int id)
        {
            var tema = _temaRepository.Get(id);
            if (tema == null)
            {
            return NotFound();
            }
            else
            {
                return Ok(tema);
            }
          
        }

        [HttpPost]
        public ActionResult<Tema> PostTema([FromBody] Tema tema)
        {
            var newTema = _temaRepository.Create(tema);
            return CreatedAtAction(nameof(GetAllTemas), new { id = newTema.Id }, newTema);
        }

        [HttpPut]
        public ActionResult PutTema([FromBody] Tema tema)
        {
          
            if (tema.Id == 0)
                return BadRequest();
            else
            {
                var temaUpdate = _temaRepository.Update(tema);

                return Ok(temaUpdate);

            }
          
        }
    }

}
```



O método PostTema([FromBody] Tema tema) utiliza a a anotação  [HttpPost] para determinar que para ser acessado precisa ser utilizado o verbo POST do protocolo HTTP, utiliza tambem a anotação [FromBody] onde determina que a informação de cadastro de tema será passado passado via corpo da requisição.



O método PutTema([FromBody] Tema tema) utiliza a a anotação  [HttpPut] para determinar que para ser acessado precisa ser utilizado o verbo Put do protocolo HTTP, utiliza tambem a anotação [FromBody] onde determina que a informação de cadastro de tema será passado passado via corpo da requisição, dentro do método há uma verificação através de um if else para verificar se o id passado  pelo objeto tema é igual a 0 ,  se for a api entregará um bad request se não a api entrega um status Ok com o objeto tema na body do request.



<div align="left"> <a href="https://docs.microsoft.com/pt-br/aspnet/core/mvc/models/model-binding?view=aspnetcore-6.0" target="_blank"><b>Documentação site Oficial: Atributo [FromBody] na API Web do ASP.NET Core</b></a>
<br />


​    

<h2>👣 Passo 09 -Testando a funcionalidade de cadastro de tema e atualizar tema no postman</h2>



### Criando um tema via postman.



Entre no postman e teste  o método PostTema.

acesse o o end point:

http://localhost:5000/api/Tema

1. clique na opção body

2. clique na opção raw

3. clique na opção json

4. insira um objeto na body da requisição

   ```json
   {
   
       "descricao": "Asp.NET"
   }
   ```

2. Selecione o verbo Post
3. Clique em Send

<div align="center"><img src="https://i.imgur.com/NWZrK3D.png" title="source: imgur.com" /></div>



Repare o satus 201 created 

e o objeto de retorno de id 1.



Objeto foi criado com sucesso.



Atualizando um tema via postman.



Entre no postman e teste  o método PutTema.

acesse o o end point:

http://localhost:5000/api/Tema

1. clique na opção body

2. clique na opção raw

3. clique na opção json

4. insira um objeto na body da requisição modificando o Asp.net para Asp.net core e inserindo o id 1

   ```json
   {
       "id": 1,
       "descricao": "Asp.NET core"
   }
   ```

2. Selecione o verbo Put
3. Clique em Send

<div align="center"><img src="https://i.imgur.com/NWZrK3D.png" title="source: imgur.com" /></div>



Repare o satus 200 created 

e o objeto de retorno de id 1 atualizado.



Objeto foi criado com sucesso





<h2>👣 Passo 09 - Construindo a funcionalidade de deletar tema</h2>



### Edite o método de deletar tema do repository.

```c#
using blogPessoal.Model;
using Microsoft.EntityFrameworkCore;
using System.Collections.Generic;

namespace blogPessoal.Repository.impl
{
    public class TemaRepository : ITemaRepository
    {
        public readonly Data.AppContext _context;

        public TemaRepository(Data.AppContext context)
        {
            _context = context;
        }

        public Tema Create(Tema tema)
        {
            Tema aux = _context.Temas.FirstOrDefaultAsync(c => c.Id.Equals(tema.Id)).Result;
            if (aux != null)
                return aux;

            _context.Temas.Add(tema);
            _context.SaveChangesAsync();

            return tema;
        }

        public void Delete(int id)
        {
            var temaDelete = _context.Temas.FindAsync(id);
            _context.Temas.Remove(temaDelete.Result);
            _context.SaveChangesAsync();
        }

        public Tema Get(int id)
        {
            try{
                var TemaReturn = _context.Temas.FirstAsync(i => i.Id == id).Result;
                return TemaReturn;
            }catch 
            {
                return null;
            }
          
            

        }

        public List<Tema> GetAll()
        {
            return _context.Temas.ToListAsync().Result;
        }

        public List<Tema> GetByDescricao(string descricao)
        {
            throw new System.NotImplementedException();
        }

        public Tema Update(Tema tema)
        {
           

            _context.Entry(tema).State = EntityState.Modified;
            _context.SaveChangesAsync();

            return tema;
        }
    }
}

```

O método Remove() remove um tema na tabela tema do banco de dados para isso, primeiramente é verificado através do método FindAsync(id), se o objeto esta cadastrado no banco em seguida o objeto temaDelete do retorno do método é passado para o método Remove(), onde é removido, ao final é salva as alterações com o método  SaveChangesAsync();





<h2>👣 Passo 09 - Construindo a funcionalidade deletar tema no controller</h2>



```c#
using blogPessoal.Model;
using blogPessoal.Repository;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace blogPessoal.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class TemaController : ControllerBase
    {

        private readonly ITemaRepository _temaRepository;

        public TemaController(ITemaRepository temaRepository)
        {
            _temaRepository = temaRepository;
        }

        [HttpGet]
        public List<Tema> GetAllTemas()
        {
            return Ok(_temaRepository.GetAll());
        }

        [HttpGet("{id}")]
        public ActionResult<Tema> GetByIdTema(int id)
        {
            var tema = _temaRepository.Get(id);
            if (tema == null)
            {
            return NotFound();
            }
            else
            {
                return Ok(tema);
            }
          
        }

        [HttpPost]
        public ActionResult<Tema> PostTema([FromBody] Tema tema)
        {
            var newTema = _temaRepository.Create(tema);
            return CreatedAtAction(nameof(GetAllTemas), new { id = newTema.Id }, newTema);
        }

        [HttpPut]
        public ActionResult PutTema([FromBody] Tema tema)
        {
          
            if (tema.Id == 0)
                return BadRequest();
            else
            {
                var temaUpdate = _temaRepository.Update(tema);

                return Ok(temaUpdate);

            }
          
        }

        [HttpDelete("{id}")]
        public ActionResult Delete(int id)
        {
            var temaToDelete = _temaRepository.Get(id);

            if (temaToDelete == null)
                return NotFound();

            _temaRepository.Delete(temaToDelete.Id);
            return NoContent();


        }
    }

}

```





<h2>👣 Passo 09 -Testando a funcionalidade de deletar tema no postman</h2>



### deletando um tema via postman.

Entre no postman e teste  o método deletar.



acesse o o end point:

http://localhost:5000/api/Tema/3

1. Pesquise por Id 3

2. Selecione o verbo delete
3. Clique em Send

<div align="center"><img src="https://i.imgur.com/RZ9Rlni.png" title="source: imgur.com" /></div>



repare que ao deletar pelo tema de id 3, o back-end entrega uma mensagem com status HTTP 404

notFound isso ocorre porque não temos um tema cadastrado com esse id;



<div align="center"><img src="https://i.imgur.com/GUgD5Cs.png" title="source: imgur.com" /></div>

acesse o o end point:

http://localhost:5000/api/Tema/1

1. Pesquise por Id 1

2. Selecione o verbo delete
3. Clique em Send



Repare que o backend entrega uma mensagem com status 204 No Content, sendo assim o tema foi deletado com sucesso.







<h2>👣 Passo 09 - Construindo a funcionalidade de buscar tema por descrição</h2>



### Edite o método de GetByDescricao do tema  repository.

```c#
using blogPessoal.Model;
using Microsoft.EntityFrameworkCore;
using System.Collections.Generic;
using System.Linq;

namespace blogPessoal.Repository.impl
{
    public class TemaRepository : ITemaRepository
    {
        public readonly Data.AppContext _context;

        public TemaRepository(Data.AppContext context)
        {
            _context = context;
        }

        public Tema Create(Tema tema)
        {
            Tema aux = _context.Temas.FirstOrDefaultAsync(c => c.Id.Equals(tema.Id)).Result;
            if (aux != null)
                return aux;

            _context.Temas.Add(tema);
            _context.SaveChangesAsync();

            return tema;
        }

        public void Delete(int id)
        {
            var temaDelete = _context.Temas.FindAsync(id);
            _context.Temas.Remove(temaDelete.Result);
            _context.SaveChangesAsync();
        }

        public Tema Get(int id)
        {
            try{
                var TemaReturn = _context.Temas.FirstAsync(i => i.Id == id).Result;
                return TemaReturn;
            }catch 
            {
                return null;
            }
          
            

        }

        public List<Tema> GetAll()
        {
            return _context.Temas.ToListAsync().Result;
        }

        public List<Tema> GetByDescricao(string descricao)
        {
            var TemaReturn = _context.Temas.Where(p => p.Descricao.ToLower().Contains(descricao.ToLower())).ToListAsync().Result;
            return TemaReturn;
        }

        public Tema Update(Tema tema)
        {
           

            _context.Entry(tema).State = EntityState.Modified;
            _context.SaveChangesAsync();

            return tema;
        }
    }
}
```

O método GetByDescricao() pesquisa  os temas por descrição, através do método Where() podemos pesquisar por determinadas condições exemplo por descrição.





<h2>👣 Passo 09 - Construindo a funcionalidade GetByDescricao  tema no controller</h2>



```c#
using blogPessoal.Model;
using blogPessoal.Repository;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace blogPessoal.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class TemaController : ControllerBase
    {

        private readonly ITemaRepository _temaRepository;

        public TemaController(ITemaRepository temaRepository)
        {
            _temaRepository = temaRepository;
        }

        [HttpGet]
        public List<Tema> GetAllTemas()
        {
            return Ok(_temaRepository.GetAll());
        }

        [HttpGet("{id}")]
        public ActionResult<Tema> GetByIdTema(int id)
        {
            var tema = _temaRepository.Get(id);
            if (tema == null)
            {
            return NotFound();
            }
            else
            {
                return Ok(tema);
            }
          
        }


        [HttpGet("descricao/{descricao}")]
        public List<Tema> GetByDescricao(string descricao)
        {
            return _temaRepository.GetByDescricao(descricao);
        }

        [HttpPost]
        public ActionResult<Tema> PostTema([FromBody] Tema tema)
        {
            var newTema = _temaRepository.Create(tema);
            return CreatedAtAction(nameof(GetAllTemas), new { id = newTema.Id }, newTema);
        }

        [HttpPut]
        public ActionResult PutTema([FromBody] Tema tema)
        {
          
            if (tema.Id == 0)
                return BadRequest();
            else
            {
                var temaUpdate = _temaRepository.Update(tema);

                return Ok(temaUpdate);

            }
          
        }

        [HttpDelete("{id}")]
        public ActionResult Delete(int id)
        {
            var temaToDelete = _temaRepository.Get(id);

            if (temaToDelete == null)
                return NotFound();

            _temaRepository.Delete(temaToDelete.Id);
            return NoContent();


        }
    }

}
```





<h2>👣 Passo 09 -Testando a funcionalidade de GetByDescricao  tema no postman</h2>



### buscando um tema por desricao via postman.

Entre no postman e teste  o método GetByDescricao .



acesse o o end point:

http://localhost:5000/api/Tema/descricao/Asp

1. Pesquise por Asp

2. Selecione o verbo get
3. Clique em Send

<div align="center"><img src="https://i.imgur.com/dgob5HI.png" title="source: imgur.com" /></div>



repare que ao pesquisar por Asp, o back-end entrega uma mensagem com status HTTP 200

Ok com todos os temas de descrição Asp.

<div align="left"><img src="https://i.imgur.com/bQGvf3h.png" title="source: imgur.com" width="30px"/> <a href="https://github.com/Marcelo7211/blog-pessoal-aspnet-core/tree/CG-87-construcao-cook-book-asp-net-core-crud" target="_blank"><b>Código fonte do projeto</b></a>


