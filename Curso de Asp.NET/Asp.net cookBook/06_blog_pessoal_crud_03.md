﻿﻿﻿﻿

<h1>Projeto 02 - Blog Pessoal - CRUD 02 relacionamento de entidade</h1>

<h2>1. O Recurso Postagem</h2>

Nesta etapa vamos começar a construir o Recurso Postagem. Veja o Diagrama de Classes abaixo: 

<div align="center"><img src="https://i.imgur.com/pcEblY5.png" title="source: imgur.com" width="75%"/></div>

Primeiro vamos construir a **Classe Postagem**, que servirá de modelo para construir a tabela **tb_postagem** (Entidade) dentro do nosso Banco de dados **db_blogpessoal**. Os campos (Atributos) da tabela serão os mesmos que estão definidos no Diagrama de Classes acima. Na próxima etapa vamos construir a **Interface PostagemRepository**, que irá nos auxiliar na interação com o Banco de dados. Os métodos descritos no Diagrama de Classes serão implementados na etapa seguinte, na **Classe PostagemController**.

Depois de criar a Classe Model Postagem, vamos executar o projeto Blog Pessoal no Visual Studio. Após a execução veremos que será criado no MySQL o Banco de dados **db_blogpessoal** e a tabela **postagem****. 

<h2>👣 Passo 01 - Criar a Model Postagem</h2>

<div align="center"><img src="https://i.imgur.com/zDnJfwO.png" title="source: imgur.com" /></div>

Se ainda estiver criado, crie uma classe c**#** com o nome Postagem na pasta **model**.

```c#
using System;
using System.Collections.Generic;
using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;
using System.Linq;
using System.Text.Json.Serialization;
using System.Threading.Tasks;

namespace blogPessoal.Model
{
    public class Postagem
    {
        public int Id { get; set; }

        [Required]
        [StringLength(100)]
        public string Titulo { get; set; }

        [Required]
        [StringLength(140)]
        public string Descricao { get; set; }
        
        [ForeignKey("TemaId")]
        public Tema Tema { get; set; }

    }
}
```

Configure a pasta como esta descrito acima

O **Entity Framework** irá mapear o dados a model e seus atributos em C# e transcrever os tipos para uma tabela de banco de dados com suas respectivas colunas e seus tipos.

| Atributo      | Tipo de dado C# | Tipo de dado MySQL |
| ------------- | --------------- | ------------------ |
| **Id**        | int             | int                |
| **Titulo**    | string          | varchar(100)       |
| **Descricao** | string          | varchar(140)       |
| **Tema**      | Tema            | Tema               |

# validação de modelo no ASP.NET

| Anotação               | Significado                                                  |
| ---------------------- | ------------------------------------------------------------ |
| [Required]             | determina que o prenchimento desse atributo é obrigatório    |
| [StringLength()]       | determina o tamanho maximo do atributo do tipo string        |
| [ForeignKey("TemaId")] | determina que o nome da chave estrangeira cliada será TemaId |

para saber mais validações de modelos no ASP.NET veja a documentação abaixo:

<div align="left"> <a href="https://docs.microsoft.com/pt-br/aspnet/core/mvc/models/validation?view=aspnetcore-6.0" target="_blank"><b>Documentação site Oficial: Entity FrameworkCore validação de modelo no ASP.NET</b></a>
<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao criar a Camada Model, não esquecer dos metodos get e setter, anotações e os tipos corretos para os seus  atributos * </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |





<h2>👣 Passo 02 - Editar Model de Tema (Criar relacionamento com Postagem)</h2>



Edite a model de postagem com o código abaixo.

<div align="center"><img src="https://i.imgur.com/zDnJfwO.png" title="source: imgur.com" /></div>



```c#
using System;
using System.Collections.Generic;
using System.ComponentModel.DataAnnotations;
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

        [JsonIgnore]
        public List<Postagem> Postagem { get; set; }

    }
}
```



| Atributo      | Tipo de dado C# | Tipo de dado MySQL |
| ------------- | --------------- | ------------------ |
| **Id**        | int             | int                |
| **Titulo**    | string          | varchar(100)       |
| **Descricao** | string          | varchar(140)       |
| **Tema**      | Tema            | Tema               |

# validação de modelo no ASP.NET

| Anotação         | Significado                                                 |
| ---------------- | ----------------------------------------------------------- |
| [Required]       | determina que o prenchimento desse atributo é obrigatório   |
| [StringLength()] | determina o tamanho maximo do atributo do tipo string       |
| [JsonIgnore]     | determina que api elimine a recursividade do banco de dados |

<h2>👣 Passo 02 - Editando a classe AppContext</h2>

Edite a camada AppContext.cs inserindo o codigo  public DbSet<Postagem> Postagens { get; set; }

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
        public DbSet<Postagem> Postagens { get; set; }


    }
}
```



<h2>👣 Passo 04 - Criando repository</h2>

Agora vamos criar a Classe Model que chamaremos de **Postagem**.

1. Dentro da pasta repository crie uma interface chamada IPostagemRepository
2. Dentro da pasta impl crie uma pasta chamada PostagemRepository



<div align="center"><img src="https://i.imgur.com/wO9dc2h.png" title="source: imgur.com" /></div>

<h2>👣 Passo 05 - Criando os arquivos do repository</h2>

1. Crie a interface IPostagemRepository como esta descrito abaixo.

   ```c#
   using blogPessoal.Model;
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Threading.Tasks;
   
   namespace blogPessoal.Repository
   {
       public interface IPostagemRepository
       {
           List<Postagem> GetAll();
   
           Postagem Get(int Id);
   
           List<Postagem> GetTitulo(string Titulo);
   
           Postagem Create(Postagem postagem);
   
           Postagem Update(Postagem postagem);
   
           void Delete(int Id);
       }
   }
   ```

   2. Configure o arquivo TemaRepository  como descrito abaixo

      ```C#
      using blogPessoal.Data;
      using blogPessoal.Model;
      using Microsoft.EntityFrameworkCore;
      using System.Collections.Generic;
      using System.Linq;
      using System.Threading.Tasks;
      
      namespace blogPessoal.Repository
      {
          public class PostagemRepository : IPostagemRepository
          {
              public readonly Data.AppContext _context;
              private readonly ITemaRepository temaRepository;
      
              public PostagemRepository(AppContext context, ITemaRepository temaRepository)
              {
                  _context = context;
                  this.temaRepository = temaRepository;
              
              }
      
              public Postagem Create(Postagem postagem)
              {
                  Postagem aux = _context.Postagens.FirstOrDefaultAsync(c => c.Id.Equals(postagem.Id)).Result;
                  if (aux != null)
                      return aux;
      
                  if (postagem.Tema != null)
                      postagem.Tema = this.temaRepository.Create(postagem.Tema);
      
      
      
                  _context.Postagens.Add(postagem);
                  _context.SaveChangesAsync();
      
                  return postagem;
              }
      
      
              public void Delete(int id)
              {
                  var postagemDelete = _context.Postagens.FindAsync(id);
                  _context.Postagens.Remove(postagemDelete.Result);
                  _context.SaveChangesAsync();
              }
      
              public List<Postagem> GetAll()
              {
                  return _context.Postagens.Include(p => p.Tema).ToListAsync().Result;
              }
      
              public Postagem Get(int id)
              {
                  try
                  {
                      var PostagemReturn = _context.Postagens.Include(p => p.Tema).FirstAsync(i => i.Id == id);
                      return PostagemReturn.Result;
                  }
                  catch
                  {
                      return null;
                  }
      
              }
      
              public List<Postagem> GetTitulo(string Titulo)
              {
                  var PostagemReturn = _context.Postagens.Include(p => p.Tema).Where(p => p.Titulo.ToLower().Contains(Titulo.ToLower())).ToListAsync();
                  return PostagemReturn.Result;
              }
      
              public Postagem Update(Postagem postagem)
              {
                  if (postagem.Tema != null)
                      postagem.Tema = this.temaRepository.Create(postagem.Tema);
      
                  _context.Entry(postagem).State = EntityState.Modified;
                  _context.SaveChangesAsync();
      
                  return postagem;
      
              }
          }
      }
      ```

      

<h2>👣 Passo 03 - Configurando a classe Startup</h2>



Edite a classe Startup.cs inserindo  services.AddScoped<IPostagemRepository, PostagemRepository>();

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
            services.AddScoped<IPostagemRepository, PostagemRepository>();
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



<h2>👣 Passo 06 - Apagando o banco de dados</h2>		

​	Agora vamos apagar o banco de dados blogPessoal, porque se encontra apenas com uma única tabela, precisamos apaga-lo para recria-lo com 2 tabelas relacionadas postagem e tema.

apague o seu banco de dados pelo Microsoft SQL Server Management Studio clicando em excluir, como demonstrado na imagem abaixo.

<div align="center"><img src="https://i.imgur.com/UYckTL6.png" title="source: imgur.com" /></div>



<h2>👣 Passo 06 - Criando Controller</h2>		

​	Agora vamos criar a classe controller:

<div align="center"><img src="https://i.imgur.com/cJILJX6.png" title="source: imgur.com" /></div>

1: crie um controlador chamado PostagemController.cs

2: implemente IPostagemaRepository como dependência e coloque as dependências [Route] [ApiController] como descrito no código abaixo:

3: implemente o codigo abaixo na camada PostagemController.cs

```c#
using blogPessoal.Model;
using blogPessoal.Repository;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace blogPessoal.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class PostagemController : ControllerBase
    {

        private readonly IPostagemRepository _postagemRepository;

        public PostagemController(IPostagemRepository postagemRepository)
        {
            _postagemRepository = postagemRepository;
        }

        [HttpGet]
        public List<Postagem> GetPostagens()
        {
            return _postagemRepository.GetAll();
        }

        [HttpGet("{id}")]
        public ActionResult<Postagem> GetPostagens(int id)
        {
            return _postagemRepository.Get(id);
        }

        [HttpGet("titulo/{titulo}")]
        public List<Postagem> GetTituloPostagens(string titulo)
        {
            return _postagemRepository.GetTitulo(titulo);
        }

        [HttpPost]
        public ActionResult<Postagem> PostPostagens([FromBody] Postagem postagem)
        {
            var newPostagem = _postagemRepository.Create(postagem);
            return CreatedAtAction(nameof(GetPostagens), new { id = newPostagem.Id }, newPostagem);
        }


        [HttpDelete("{id}")]
        public ActionResult Delete(int id)
        {
            var postagemToDelete = _postagemRepository.Get(id);

            if (postagemToDelete == null)
                return NotFound();

            _postagemRepository.Delete(postagemToDelete.Id);
            return NoContent();


        }

        [HttpPut]
        public ActionResult<Postagem> PutPostagens([FromBody] Postagem postagem)
        {
            if (postagem.Id <= 0)
                return BadRequest();

            var postagemResult = _postagemRepository.Update(postagem);

            return postagemResult;
        }
    }
}
```

<h2>👣 Passo 07 - testando postman</h2>

### Testando o método post Postagem



1. Execute o método  Post

2. insira a url http://localhost:5000/api/Postagem

3. insira o objeto abaixo na body da requisição:

   ```json
   {
       "titulo":"Asp.NET",
       "texto":"Asp.NET",
       "tema":{
           "id":1
       }
   }
   ```

4. clique em Send

1.  repare o status 201 e o response body com objeto criado



<div align="center"><img src="https://i.imgur.com/hcZ6i2I.png" title="source: imgur.com" /></div>



### Testando o método get Postagem

1. execute o método Get
2. insira a url http://localhost:5000/api/Postagem
3. clique em Send
4.  repare o status 200 e o response body com array contendo as postagem.

<div align="center"><img src="https://i.imgur.com/hcZ6i2I.png" title="source: imgur.com" /></div>



### Testando o método Put de postagem 

1. execute o método Put
2. insira a url http://localhost:5000/api/Postagem
3. clique em Send
4.  repare o status 200 e o response body com objeto atualizado

<div align="center"><img src="https://i.imgur.com/5NWJpFr.png" title="source: imgur.com" /></div>



### Testando o método GetById de postagem 

1. execute o método Get
2. insira a url http://localhost:5000/api/Postagem/1
3. clique em Send
4.  repare o status 200 e o response body contendo a postagem com id indicado.

<div align="center"><img src="https://i.imgur.com/iTDdTDB.png" title="source: imgur.com" /></div>



### Testando o método delete de postagem 

1. execute o método Delete
2. insira a url http://localhost:5000/api/Postagem/1
3. clique em Send
4.  repare o status 204, objeto apagado com sucesso

<div align="center"><img src="https://i.imgur.com/iTDdTDB.png" title="source: imgur.com" /></div>





### Testando o método GetTitulo de postagem 

1. execute o método Get
2. insira a url http://localhost:5000/api/Postagem/titulo/SQL Server
3. clique em Send
4.  repare o status 200 e o response body com array contendo as postagem.

<div align="center"><img src="https://i.imgur.com/vM0pjKf.png" title="source: imgur.com" /></div>



| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao manipular o postman se atentando a verbo/metodo usado url e objeto na body* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<div align="left"><img src="https://i.imgur.com/bQGvf3h.png" title="source: imgur.com" width="30px"/> <a href="https://github.com/Marcelo7211/blog-pessoal-aspnet-core/tree/CG-87-construcao-cook-book-asp-net-core-crud" target="_blank"><b>Código fonte do projeto</b></a>

