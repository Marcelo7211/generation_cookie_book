<h1>Deploy do Back-end no Heroku</h1>

<h2>O que é Deploy?</h2>

O verbo **deploy**, em inglês, significa **implantar**.

Em programação, seu sentido está intimamente relacionado à sua tradução literal: fazer um deploy, em termos práticos, significa colocar no ar alguma aplicação que teve seu desenvolvimento concluído.
Quando um site é finalizado por um desenvolvedor e, após seus testes, é finalmente hospedado na nuvem e colocado no ar, ele passa pelo processo de deploy.
De mesmo modo, quando um sistema sofre alguma melhoria ou alteração em seu código-fonte, implementar essa alteração ao sistema que está no ar também é um tipo de deploy.

<h2>O que veremos por aqui?</h2>

Esse documento é um passo a passo para você enviar a sua aplicação Asp.NET, gratuitamente para a nuvem (Deploy). Este processo irá gerar um link de acesso a sua aplicação, que poderá ser acessado de qualquer lugar, a partir de qualquer dispositivo com acesso a Internet. 
Para efetuar o Deploy vamos precisar fazer algumas modificações em nosso projeto, que serão detalhadas nas próximas páginas.

<h2>👣 Passo 01 - Criando uma conta grátis no Heroku</h2>



1) Acesse o endereço: **https://www.heroku.com**

<div align="center"><img  src="https://i.imgur.com/9lFOzru.png" title="source: imgur.com" width="90%"/></div>

2. Crie a sua conta grátis no Heroku clicando no botão **SIGN UP FOR FREE**.

3. Preencha os dados do formulário e clique no botão **CREATE FREE ACCOUNT**.

   <div align="center"><img src="https://i.imgur.com/yp46vWx.png" title="source: imgur.com" width="80%"/></div>

4. Será exibida a mensagem abaixo informando que você receberá uma mensagem no seu e-mail para ativar a sua conta no Heroku. Acesse o seu e-mail e ative a sua conta.

   <div align="center"><img src="https://i.imgur.com/d1YV3RK.png" title="source: imgur.com" width="80%"/></div>

5. O e-mail que você receberá será semelhante a imagem abaixo. Clique no link indicado em vermelho para ativar a sua nova conta

   <div align="center"><img src="https://i.imgur.com/cgeQPVF.png" title="source: imgur.com" width="85%"/></div>

6. Será aberta a janela abaixo para criar a senha da sua conta. Crie uma senha e clique no botão **SET PASSWORD AND LOGIN**.

   <div align="center"><img src="https://i.imgur.com/j3hWcWD.png" title="source: imgur.com" width="80%"/></div>

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="70px"/> | <p align="justify"> **ATENÇÃO:**  *A senha deve ter no mínimo 8 caracteres e pelo menos 1 letra maiúscula, 1 caracter especial e 1 numero*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

7. Será exibida a tela de Boas Vindas. Clique no botão **CLICK HERE TO PROCEED**.

   <div align="center"><img src="https://i.imgur.com/0RtgWeI.png?1" title="source: imgur.com" /></div>

8. Na próxima tela, concorde com os termos de uso da plataforma clicando no botão **Accept**.

   <div align="center"><img src="https://i.imgur.com/0pRIHhl.png" title="source: imgur.com" /></div>

9. Você será redirecionado para o **Dashboard do Heroku**. Agora você está pronto para criar as suas aplicações na Nuvem do Heroku.

   <div align="center"><img src="https://i.imgur.com/MtxGolw.png" title="source: imgur.com" /></div>

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="70px"/> | <p align="justify"> **ATENÇÃO:**  *Conclua todas etapas do processo de criação da conta no Heroku antes de avançar para o próximo passo do Deploy*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br /><br /><br />

10. Caso o Heroku exiba a mensagem abaixo, solicitando a ativação do **MFA (Multi-Factor Authentication)**, não habilite esta opção. Clique no link **Later**, como mostra a figura abaixo, no item marcado em vermelho.

    <div align="center">
    <img src="https://i.imgur.com/OejMn66.png" title="source: imgur.com" /></div>



| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="200px"/> | <p align="justify"> **ATENÇÃO:**  *Não habilite em sua conta no Heroku a opção MFA (Multi-Factor Authentication), ou seja, o login em 2 etapas. Em alguns servidores não é possível efetuar login via Heroku Client com o MFA habilitado*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br /><br />

<h2>👣 Passo 02 - Instalação do Node.js</h2>



1) Acesse o endereço: **https://nodejs.org/en/**

<div align="center"><img src="https://i.imgur.com/t6mCAGb.png" title="source: imgur.com" /></div>

2. Faça o download da última versão LTS disponível do Node.js e instale no seu computador. 

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="120px"/> | <p align="justify"> **ATENÇÃO:** No momento em que este e-book foi escrito, a versão LTS mais atual do Node.js era a versão 16.13.0. Hoje pode ser que a versão mais atual seja outra* </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |



| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="72px"/> | <p align="justify"> **DICA:** *Caso você tenha alguma dúvida quanto a instalação do Node.js, consulte o Guia de Instalação do Node. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br /><br /><br /><br /><br /><br /><br />

<h2>👣 Passo 03 - Instalação do Heroku Client</h2>



Para instalar e executar os comandos do Heroku Client usaremos o **Prompt de comando do Windows (cmd)**. 

1) Para instalar, execute o atalho <img width="50" src="https://i.imgur.com/JpqKaVh.png" title="source: imgur.com" /> para abrir a janela **Executar**.

<div align="center"><img src="https://i.imgur.com/uDHCB0H.png" title="source: imgur.com" width=55%"/></div>

2) Digite o comando **cmd** para abrir o **Prompt de comando do Windows**

3) Antes de instalar o **Heroku Client**, verifique se o Node já está instalado através do comando: 

```bash
npm -version
```

<div align="justify"><img src="https://i.imgur.com/sfHThTC.png" title="source: imgur.com" /></div>

** A versão pode ser diferente da imagem*

4) Caso não esteja instalado, volte ao passo **Instalação do Node.js**. 
5) Para instalar o **Heroku Client** digite o comando: 

```bash
npm i -g heroku
```

<div align="center"><img  src="https://i.imgur.com/rcsDAZ0.png" title="source: imgur.com" /></div>

6) Confirme a instalação do Heroku Client através do comando: 

```bash
heroku version
```

<div align="center"><img src="https://i.imgur.com/MO23QyV.png" title="source: imgur.com" /></div>

**A versão pode ser diferente da imagem*

<br />
   
<h2>👣 Passo 04 - Atualizando o projeto para uso de Task e métodos assincronos</h2>
   
   Como vamos trabalhar com um banco de dados remoto precisamos garantir que nossso projeto trabalhe com métodos assincronos,
   
   onde atraves da palavra reservada await e do uso de objetos do tipo task podemos garantir que as proximas instruções só serão realizadas quando a requisição para o banco for realizada, atualize as camadas abaixo do seu projeto
 
 <h4>AppContext.cs</h4>   
   
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

        protected override void OnModelCreating(ModelBuilder modelBuilder)
        {
            modelBuilder.Entity<Postagem>()
            .HasOne(p => p.Tema)
            .WithMany(b => b.Postagem);
        }

        public DbSet<Tema> Temas { get; set; }
        public DbSet<Postagem> Postagens { get; set; }

        public DbSet<User> Users { get; set; }
    }
}  
   
```
    
 <h4>IUserRepository.cs</h4> 
   
```c#
   
using blogPessoal.Model;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace blogPessoal.Repository
{
    public interface IUserRepository
    {
        User GetUserName(string usuario, string senha);


        Task<User> CreateUser(User user);


    }
}   
   
```
   
<h4>ITemaRepository.cs</h4>    
   
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

        Task<Tema> GetById(int Id);

        List<Tema> GetByDescricao(string descricao);

        Task<Tema> Create(Tema tema);

        Task<Tema> Update(Tema tema);

        Task<Tema> Delete(int Id);
    }
}
   
```
   

<h4>IPostagemRepository.cs</h4> 
   
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

        Task<Postagem> GetById(int Id);

        List<Postagem> GetTitulo(string Titulo);

        Task<Postagem> Create(Postagem postagem);

        Task<Postagem> Update(Postagem postagem);

        Task<Postagem> Delete(int Id);
    }
}
   
```
 

<h4>UserRepository.cs</h4> 
   
```c#
using blogPessoal.Data;
using blogPessoal.Model;
using Microsoft.EntityFrameworkCore;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace blogPessoal.Repository
{
    public class UserRepository : IUserRepository
    {
        public readonly Data.AppContext _context;

        public UserRepository(Data.AppContext context)
        {
            _context = context;
        }

        public async Task<User> CreateUser(User user)
        {
            var aux = await _context.Users.FirstOrDefaultAsync(c => c.Id.Equals(user.Id));
            if (aux != null)
            {
                return null;
            }
            else
            {

                var valueBytes = Encoding.UTF8.GetBytes(user.Senha);
                user.Senha = System.Convert.ToBase64String(valueBytes);
                _context.Users.AddAsync(user);
                await _context.SaveChangesAsync();

                return user;
            }

        }

        public User GetUserName(string usuario, string senha)
        {

            Task<User> UserReturn = _context.Users.Where(u => u.Usuario == usuario).FirstOrDefaultAsync();
            var valueBytes = System.Convert.FromBase64String(UserReturn.Result.Senha);
            string passwordDecode = Encoding.UTF8.GetString(valueBytes);
            if (passwordDecode == senha)
            {
                return UserReturn.Result;
            }
            else
            {
                return null;
            }



        }
    }
}   
   
```
   

<h4>TemaRepository.cs</h4> 
   
```c#

using blogPessoal.Model;
using Microsoft.EntityFrameworkCore;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace blogPessoal.Repository.impl
{
    public class TemaRepository : ITemaRepository
    {
        public readonly Data.AppContext _context;

        public TemaRepository(Data.AppContext context)
        {
            _context = context;
        }

        public async Task<Tema> Create(Tema tema)
        {
            var aux = await _context.Temas.FirstOrDefaultAsync(c => c.Id.Equals(tema.Id));
            if (aux != null)
                return aux;
            _context.Temas.AddAsync(tema);
            await _context.SaveChangesAsync();

            return tema;
        }

        public async Task<Tema> Delete(int id)
        {
            var temaDelete = await _context.Temas.FindAsync(id);
            _context.Temas.Remove(temaDelete);
            await _context.SaveChangesAsync();

            return null;
        }

        public async Task<Tema> GetById(int Id)
        {
            try
            {
                var TemaReturn = await _context.Temas.FirstAsync(i => i.Id == Id);
                return TemaReturn;
            }
            catch
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

        public async Task<Tema> Update(Tema tema)
        {
            _context.Entry(tema).State = EntityState.Modified;
            await _context.SaveChangesAsync();

            return tema;
        }
    }
}
   
```
   
<h4>PostagemRepository.cs</h4> 
   
```c#
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

        public async Task<Postagem> Create(Postagem postagem)
        {


            var aux = await _context.Postagens.FirstOrDefaultAsync(c => c.Id.Equals(postagem.Id));
            if (aux != null)
                return aux;

            if (postagem.Tema != null)
                postagem.Tema = await this.temaRepository.Create(postagem.Tema);

            _context.Postagens.AddAsync(postagem);
            await _context.SaveChangesAsync();

            return postagem;
        }


        public async Task<Postagem> Delete(int id)
        {
            var postagemDelete = await _context.Postagens.FindAsync(id);
            _context.Postagens.Remove(postagemDelete);
            await _context.SaveChangesAsync();

            return null;
        }

        public List<Postagem> GetAll()
        {
            return _context.Postagens.Include(p => p.Tema).ToListAsync().Result;
        }

        public async Task<Postagem> GetById(int id)
        {
            try
            {
                var PostagemReturn = await _context.Postagens.Include(p => p.Tema).FirstAsync(i => i.Id == id);
                return PostagemReturn;
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

        public async Task<Postagem> Update(Postagem postagem)
        {
            if (postagem.Tema != null)
                postagem.Tema = await this.temaRepository.Create(postagem.Tema);

            _context.Entry(postagem).State = EntityState.Modified;
            await _context.SaveChangesAsync();

            return postagem;

        }
    }
}   
   
```

<h4>UserController.cs</h4> 
 
   
```c#

using blogPessoal.Model;
using blogPessoal.Repository;
using blogPessoal.Service;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using System.Threading.Tasks;

namespace blogPessoal.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class UserController : ControllerBase
    {

        private readonly IUserRepository _userRepository;


        public UserController(IUserRepository userRepository)
        {
            _userRepository = userRepository;

        }

        [HttpPost]
        [Route("login")]
        [AllowAnonymous]
        public ActionResult<dynamic> Login([FromBody] User model)
        {

            var user = _userRepository.GetUserName(model.Usuario, model.Senha);
            if (user == null)
                return Unauthorized(new { message = "Usuário ou senha inválidos" });
            else
            {
                var userResult = new User { Id = user.Id, Nome = user.Nome, Usuario = user.Usuario, Senha = "" };

                var token = TokenService.GenerateToken(userResult);
                return new
                {
                    user = userResult,
                    token = "Bearer " + token
                };
            }
        }


        [HttpPost]
        [Route("cadastrar")]
        [AllowAnonymous]
        public async Task<ActionResult<User>> Cadastrar([FromBody] User user)
        {

            var newBook = await _userRepository.CreateUser(user);
            return newBook;

        }

    }

}
   
```
   
<h4>TemaController.cs</h4> 
   
```c#
 
using blogPessoal.Model;
using blogPessoal.Repository;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;
using System.Threading.Tasks;

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
        [Authorize]
        public List<Tema> GetAllTemas()
        {
            return _temaRepository.GetAll();
        }

        [HttpGet("{id}")]
        [Authorize]
        public async Task<ActionResult<Tema>> GetByIdTema(int id)
        {
            var tema = await _temaRepository.GetById(id);
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
        [Authorize]
        public List<Tema> GetByDescricao(string descricao)
        {
            return _temaRepository.GetByDescricao(descricao);
        }

        [HttpPost]
        [Authorize]
        public async Task<ActionResult<Tema>> PostTema([FromBody] Tema tema)
        {
            var temaReturn = await _temaRepository.Create(tema);
            return CreatedAtAction(nameof(GetAllTemas), new { id = temaReturn.Id }, temaReturn);
        }

        [HttpPut]
        [Authorize]
        public async Task<ActionResult> PutTema([FromBody] Tema tema)
        {

            if (tema.Id == 0)
                return BadRequest();
            else
            {
                var temaUpdate = await _temaRepository.Update(tema);

                return Ok(temaUpdate);

            }

        }

        [HttpDelete("{id}")]
        [Authorize]
        public async Task<ActionResult> DeleteTema(int id)
        {
            var temaToDelete = await _temaRepository.GetById(id);

            if (temaToDelete == null)
                return NotFound();

            await _temaRepository.Delete(temaToDelete.Id);
            return NoContent();


        }
    }

}
   
```
   
<h4>PostagemController.cs</h4> 
   
```c#

using blogPessoal.Model;
using blogPessoal.Repository;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;
using System.Threading.Tasks;

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
        [Authorize]
        public List<Postagem> GetAllPostagens()
        {
            return _postagemRepository.GetAll();
        }

        [HttpGet("{id}")]
        [Authorize]
        public async Task<ActionResult<Postagem>> GetByIdPostagem(int id)
        {
            var postagem = await _postagemRepository.GetById(id);
            if (postagem == null)
            {
                return NotFound();
            }
            else
            {
                return Ok(postagem);
            }
        }

        [HttpGet("titulo/{titulo}")]
        [Authorize]
        public List<Postagem> GetByTituloPostagem(string titulo)
        {
            return _postagemRepository.GetTitulo(titulo);
        }

        [HttpPost]
        public async Task<ActionResult<Tema>> PostPostagem([FromBody] Postagem postagem)
        {
            var newPostagem = await _postagemRepository.Create(postagem);
            return Ok(newPostagem);
        }


        [HttpDelete("{id}")]
        [Authorize]
        public async Task<ActionResult> DeletePostagem(int id)
        {
            var postagemToDelete = await _postagemRepository.GetById(id);

            if (postagemToDelete == null)
                return NotFound();

            await _postagemRepository.Delete(postagemToDelete.Id);
            return NoContent();


        }

        [HttpPut]
        [Authorize]
        public async Task<ActionResult<Postagem>> PutPostagem([FromBody] Postagem postagem)
        {
            if (postagem.Id <= 0)
                return BadRequest();

            var postagemResult = await _postagemRepository.Update(postagem);

            return Ok(postagemResult);
        }
    }
}
   
```
 

<h2>👣 Passo 05 - Adicionar a Dependência do PostgreSQL no projeto</h2>


O Heroku, na sua versão gratuita, utiliza o **PostgreSQL** como **SGBD**.  Estamos utilizando o **SQL-Server** para desenvolver o Blog Pessoal. Ambos são Banco de dados Relacionais e graças ao **Entity Framework Core **, não será necessário realizar nenhuma alteração no código do nosso aplicativo. A única mudança necessária, além de adicionar a **Dependência no nuget**,  e configurar a aplicação para utilizar o PostgreSQL. 

<div align="left"><img src="https://i.imgur.com/b3khcJI.png" title="source: imgur.com" width="25px"/> <a href="https://www.postgresql.org/" target="_blank"><b>Site Oficial: PostgreSQL</b></a></div>

1. clique com botão direito sobre dependência 
2. clique em gerenciar pacotes do Nuget

<div align="center"><img src="https://i.imgur.com/biUST6C.png" title="source: imgur.com" /></div>    

<br />

3. procure por Npgsql.EntityFrameworkCore.PostgreSQL e instale a versão 5.0.1

<div align="center"><img src="https://i.imgur.com/gcAd13C.png" title="source: imgur.com" /></div>    

<h2>👣 Passo 06 - Configurar o Banco de Dados</h2>
   
   

A Configuração do Banco de dados Local é diferente da configuração que será utilizada no Heroku. 

No passo anterior, adicionamos a Dependência do PostgreSQL no projeto, neste passo vamos configurar a aplicação para acessar o Banco de dados remoto no Heroku.

### Editando StartUp.cs

1.  Edite o arquivo **StartUp.cs** como o codigo abaixo.

```c#
using blogPessoal.Data;
using blogPessoal.Repository;
using blogPessoal.Repository.impl;
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.EntityFrameworkCore;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.IdentityModel.Tokens;
using Microsoft.OpenApi.Models;

using System.Text;


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

            var key = Encoding.ASCII.GetBytes(Settings.Secret);
            services.AddAuthentication(x =>
            {
                x.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
                x.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
            })
            .AddJwtBearer(x =>
            {
                x.RequireHttpsMetadata = false;
                x.SaveToken = true;
                x.TokenValidationParameters = new TokenValidationParameters
                {
                    ValidateIssuerSigningKey = true,
                    IssuerSigningKey = new SymmetricSecurityKey(key),
                    ValidateIssuer = false,
                    ValidateAudience = false
                };
            });

            services.AddEntityFrameworkNpgsql()
            .AddDbContext<AppContext>(options => options.UseNpgsql(Configuration.GetConnectionString("DefaultConnection")));
            services.AddScoped<IPostagemRepository, PostagemRepository>();
            services.AddScoped<ITemaRepository, TemaRepository>();
            services.AddScoped<IUserRepository, UserRepository>();
            services.AddControllers();
            services.AddSwaggerGen(c =>
            {
                c.SwaggerDoc("v1", new OpenApiInfo { Title = "blogPessoal", Version = "v1" });
            });
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IWebHostEnvironment env, Data.AppContext context)
        {
            context.Database.EnsureCreated();
            app.UseDeveloperExceptionPage();
            app.UseSwagger();
            app.UseSwaggerUI(c => c.SwaggerEndpoint("/swagger/v1/swagger.json", "blogPessoal v1"));

            if (env.IsDevelopment())
            {
                context.Database.EnsureCreated();
                app.UseDeveloperExceptionPage();
                app.UseSwagger();
                app.UseSwaggerUI(c => c.SwaggerEndpoint("/swagger/v1/swagger.json", "blogPessoal v1"));
            }
         
            app.UseHttpsRedirection();

            app.UseRouting();

            app.UseCors(x => x
                 .AllowAnyOrigin()
                 .AllowAnyMethod()
                 .AllowAnyHeader());

            app.UseAuthentication();
            app.UseAuthorization();

            app.UseEndpoints(endpoints =>
            {
                endpoints.MapControllers();
            });
        }
    }
}
```

### Explicando o código

2.  Você devera trocar o conector do banco de dados SQL-Server para o UseNpgsql

```c#
 services.AddEntityFrameworkNpgsql()
            .AddDbContext<AppContext>(options => options.UseNpgsql(Configuration.GetConnectionString("DefaultConnection")));
```

3. Você deverá colocar o código de criação do banco/criação do swagger fora do if de verificação de ambiente de desenvolvimento.

```c#
 context.Database.EnsureCreated();
            app.UseDeveloperExceptionPage();
            app.UseSwagger();
            app.UseSwaggerUI(c => c.SwaggerEndpoint("/swagger/v1/swagger.json", "blogPessoal v1"));
```

### Editando appsettings.json

1. Edite o arquivo **appsettings.json** como o codigo abaixo.

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Host=ec2-3-209-61-239.compute-1.amazonaws.com;Port=5432;Pooling=true;Database=df7doa9h5c6c56;User Id=cjsxoutsklffoo;Password=40d9fa09eeb19c297dc87529c39a376446b35dc2b06ec136d1df755730b64a8f;SSL Mode=Require;TrustServerCertificate=True;"
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



<h2>👣 Passo 07 - Deploy com o Git</h2>

Vamos preparar o nosso repositório local para subir a aplicação para o Heroku utilizando o Git.

1. Abra pasta do seu projeto BlogPessoal
2.  Para saber que esta na pasta certa identifique o arquivo **appsettings.json**.

<div align="left"><img src="https://i.imgur.com/DCHSRSf.png" title="source: imgur.com" /></div>

4. Abra a pasta **deploy_blogpessoal** e verifique se existe uma pasta chamada **.git**. Caso ela exista, apague esta pasta. **Esta pasta estará presente <u>APENAS</u> se você inicializou o git dentro da pasta do projeto.**

<div align="left"><img src="https://i.imgur.com/DCHSRSf.png" title="source: imgur.com" /></div>

7. Caso esta pasta não esteja sendo exibida, na janela do Windows Explorer, clique na **Guia Exibir** e na sequência no botão **Opções**. Na janela **Opções de Pasta**, na **Guia Modo de Exibição**, no item **Configurações avançadas**, localize a opção: **Pastas e arquivos ocultos** e marque a opção **Mostrar arquivos, pastas e unidades ocultas** (como mostra a figura abaixo). Em seguida clique em **OK** para concluir.

<div align="center"><img width="340px" src="https://i.imgur.com/n8hQu12.png" title="source: imgur.com" /></div>

8. Execute o atalho <img width="80" src="https://i.imgur.com/JpqKaVh.png" title="source: imgur.com" /> para abrir a janela Executar

<div align="center"><img src="https://i.imgur.com/ISBwaaK.png" title="source: imgur.com" /></div>

9. Digite o comando abaixo para abrir o **Prompt de Comando do Windows**:

```
cmd
```

10. Na pasta **deploy_blogpessoal**, no **Windows Explorer**, copie o caminho da pasta conforme a figura abaixo:

<div align="center"><img src="https://i.imgur.com/pUs2wYc.png" title="source: imgur.com" /></div>

11. No Prompt de comando do Windows digite o comando cd e cole na frente do comando o caminho copiado: 

```
cd C:\Users\DELL\Desktop\asp.net curso\deploy\blog-pessoal-aspnet-core\blogPessoal\blogPessoal
```

**o nome da pasta pode ser diferente*

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao iniciar o Deploy pelo Git. A partir deste ponto, todos os comandos do Git e do Heroku Client devem ser executados via Prompt de Comando do Windows (CMD), dentro da pasta deploy-blogpessoal.* |
| ------------------------------------------------------------ | :----------------------------------------------------------- |

12. Digite a sequência de comandos abaixo para inicializar o seu repositório local para efetuar o Deploy no Heroku:

```
git init
```

<br />

<h2>👣 Passo 8 - Login no Heroku</h2>

1. Digite o comando: 

```
heroku login
```

<div><img src="https://i.imgur.com/pvygxsZ.png" title="source: imgur.com" /></div>

<br /><br /><br /><br /><br /><br />

2. Será aberta a janela abaixo. Clique no botão **Log in**

<div align="center"><img src="https://i.imgur.com/PXR6hFW.png" title="source: imgur.com" /></div>

3. Após efetuar o login na sua conta, será exibida a janela abaixo. 

<div align="center"><img src="https://i.imgur.com/i6VMoMp.png" title="source: imgur.com" /></div>

4. Volte para o Prompt de comando para continuar o Deploy.

<div align="center"><img src="https://i.imgur.com/IjyMzrH.png" title="source: imgur.com" /></div>

<br /><br />

<h2>👣 Passo 9 - Criar um novo projeto no Heroku</h2>



Para criar um novo projeto na sua conta do Heroku, digite o comando abaixo, onde o **nomedoprojeto** deve ser substituído por um nome (escolhido por você), que esteja disponível no Heroku.

```
heroku create nomedoprojeto --buildpack https://github.com/UCSFCDHI/heroku-dotnet-5.0.git
```

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="200px"/> | <p align="justify"> **ATENÇÃO:** *O NOME DO PROJETO NÃO PODE CONTER LETRAS MAIUSCULAS, NUMEROS OU CARACTERES ESPECIAIS. ALÉM DISSO ELE PRECISA SER ÚNICO DENTRO DA PLATAFORMA HEROKU. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

Se o nome escolhido já existir, será exibida a mensagem abaixo:

<div><img src="https://i.imgur.com/L7ayFaz.png" title="source: imgur.com" /></div>

Se o nome escolhido for aceito, será exibida a mensagem abaixo:

<div><img src="https://i.imgur.com/P0KazWd.png" title="source: imgur.com" /></div>



<h2>👣Passo 10 - Efetuar o Deploy</h2>

1. Para concluir o Deploy, digite o comando: 

```
git add .
git commit -m “Deploy inicial - Blog Pessoal”
git push heroku master
```

2. Ao finalizar o Deploy, será exibida a mensagem **BUILD SUCESS** (destacado em verde na imagem) e será exibido o endereço (**https://nomedoprojeto.herokuapp.com**) para acessar a API na Internet (destacado em amarelo na imagem)

<div align="center"><img src="https://i.imgur.com/VGoSZth.png" title="source: imgur.com" /></div>



<h2>👣 Passo 11 - Adicionar o Banco de dados no Heroku</h2>



Acesse o link https://elements.heroku.com/addons/heroku-postgresql

ou procure no google por /heroku-postgresql

<div align="center"><img src="https://i.imgur.com/q9rc2Xj.png" title="source: imgur.com" /></div>



1. Escolha a versão de desenvolvimento e clique no botão install heroku postgress

<div align="center"><img src="https://i.imgur.com/VA2otiu.png" title="source: imgur.com" /></div>

2. Escolha o repositório que foi criado anteriormente, buscando pelo nome do repositório.

<div align="center"><img src="https://i.imgur.com/kb6Z92G.png" title="source: imgur.com" /></div>

4. Abra o Data e escolha o banco de dados que está linkado a sua aplicação.

<div align="center"><img src="https://i.imgur.com/mv3C9Bi.png" title="source: imgur.com" /></div>

5. Clique em Settings e clique em view credentials.

<div align="center"><img src="https://i.imgur.com/vliUVlE.png" title="source: imgur.com" /></div>

6. Passe cada um dos dados para o arquivo **appsettings.json**.

```json
{
  "ConnectionStrings": {
    "DefaultConnection": 
    "Host="Insira o Host";
    Port= "Insira o Port";
    Pooling=true;
    Database="Insira o Database";
    User Id="Insira o User";
    Password="Insira o Password";
    SSL Mode=Require;TrustServerCertificate=True;"
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

7. Salve os arquivos alterados: 

8. Para concluir o Deploy, digite o comando no terminal na pasta de origem: 

```
git add .
git commit -m “Deploy inicial - Blog Pessoal”
git push heroku master
```

9. Ao finalizar o Deploy, será exibida a mensagem **BUILD SUCESS** (destacado em verde na imagem) e será exibido o endereço (**https://nomedoprojeto.herokuapp.com**) para acessar a API na Internet (destacado em amarelo na imagem)

<div align="center"><img src="https://i.imgur.com/VGoSZth.png" title="source: imgur.com" /></div>



<h2>👣 Passo 12 - Testar o link e a aplicação</h2>



1) Abra o navegador e digite o endereço a sua aplicação (**https://nomedoprojeto.herokuapp.com/swagger**).
2) Será solicitado o **Usuário e a Senha**. Digite **root** para ambos.
3) Sua aplicação abrirá o **Swagger**. 

<div align="center"><img src="https://i.imgur.com/wl90Me9.png" title="source: imgur.com" /></div>



<div align="left"><img src="https://i.imgur.com/bQGvf3h.png" title="source: imgur.com" width="25px"/> <a href="https://github.com/Marcelo7211/blog-pessoal-aspnet-core/tree/CG-81-construcao-cook-book-asp-net-core-deploy" target="_blank"><b>Código fonte: Projeto Finalizado</b></a> 
</div>

