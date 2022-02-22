﻿﻿﻿﻿<h1>Projeto 02 - Blog Pessoal - Spring Security</h1>



O que veremos por aqui:

1. O Ecossistema do Usuário
2. Apresentação do Recurso Usuário
3. Criar a Classe Model Usuario relacionada com a Classe Postagem
4. Criar a Classe UsuarioLogin
5. Criar a Interface UsuarioRepository

<h2>2. O Recurso Usuario</h2>

Nesta etapa vamos começar a construir o Recurso Usuario, que será composto por 2 Classes: **Usuario** e **Usuario Login**. 

<div align="center"><img src="https://i.imgur.com/E1jgjV6.png" title="source: imgur.com" width="70%"/></div>

A **Classe Usuario** servirá de modelo para construir a tabela **tb_usuario** (Entidade) dentro do nosso Banco de dados **db_blogpessoal**. Os campos (Atributos) da tabela serão os mesmos que estão definidos no Diagrama de Classes acima. Além de construirmos a Classe Usuario, também faremos o Relacionamento com as Classe Postagem, construída anteriormente. Veja como ficará o Relacionamento entre as 3 Classes, após a implementação, no Diagrama de Classes abaixo:

<div align="center"><img src="https://i.imgur.com/5p6IKku.png" title="source: imgur.com" /></div>

Na sequência vamos construir a **Interface UsuarioRepository**, que irá nos auxiliar na interação com o Banco de dados e com as Classes **UsuarioController**, onde serão implementados os 5 métodos descritos no Diagrama de Classes acima e com a Classe de Serviço (Service), **UsuarioService**, onde serão implementadas as **Regras de Negócio** exigidas pela **Asp.Net Authentication**.

<br />


<h2>👣 Passo 02 - Criar a Classe Usuario na Camada Model</h2>

Agora vamos criar a terceira Classe Model que chamaremos de **Usuario**.

1. Crie a Model Usuario como descrito no codigo abaixo.

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text.Json.Serialization;
using System.Threading.Tasks;

namespace blogPessoal.Model
{
    public class User
    {
        public int Id { get; set; }

        public string Nome { get; set; }
        public string Usuario { get; set; }
        public string Senha { get; set; }


        [JsonIgnore]
        public List<Postagem> Postagem { get; set; }
    }
}
```



<h2>👣 Passo 03 - Editando a classe Postagem </h2>



A Classe Postagem será o lado N:1, ou seja, **Muitas Postagens podem ter apenas Um Usuario**. Para criar a Relação vamos inserir depois do último atributo da Classe Postagem (tema), as 3 linhas abaixo:

```c#
	[ForeignKey("UserId")]
    public User User { get; set; }
```

Não esqueça de acrescentar acrescentar os **Métodos Get e Set** para o novo atributo (usuario), que foi adicionado na Classe Postagem. Veja o código completo abaixo:


| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="170px"/> | <div align="left"> **DICA:** *Toda vez que você adicionar um novo Atributo na sua Classe, não esqueça de criar os Métodos GET e SET do Atributo. Caso contrário, você não conseguirá visualizar ou atualizar os dados do Atributo.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

```java
using System;
using System.Collections.Generic;
using System.ComponentModel.DataAnnotations.Schema;
using System.Linq;
using System.Text.Json.Serialization;
using System.Threading.Tasks;

namespace blogPessoal.Model
{
    public class Postagem
    {
        public int Id { get; set; }

        public string Titulo { get; set; }

        public string Descricao { get; set; }
        [ForeignKey("TemaId")]
        public Tema Tema { get; set; }

        [ForeignKey("UserId")]
        public User User { get; set; }
    }
}
```



| Anotação               | Significado                                              |
| ---------------------- | -------------------------------------------------------- |
| [ForeignKey("UserId")] | determina que a chave estrangeira vai se chamar "UserId" |

<h2>👣 Passo 04 - Criar a camada UsuarioRepository </h2>



Agora vamos criar a Interface Repository que chamaremos de **IUserRepository**.

<br />

A seguir veja sua implementação:

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

        User CreateUser(User user);

        User Create(User user);
    }
}
```

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="300px"/> | <div align="left">ALERTA DE BSM: Mantenha a Atenção aos Detalhes, tome muito cuidado pois se a escrita dos métodos CreateUser, CreateUser e Create  .</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

Agora vamos criar a Classe Repository que chamaremos de **UserRepository**.

<br />

A seguir veja sua implementação:

```c#
using blogPessoal.Model;

namespace blogPessoal.Repository.impl
{
    public class UserRepository : IUserRepository
    {
        public User Create(User user)
        {
            throw new System.NotImplementedException();
        }

        public User CreateUser(User user)
        {
            throw new System.NotImplementedException();
        }

        public User GetUserName(string usuario, string senha)
        {
            throw new System.NotImplementedException();
        }
    }
}

```

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="300px"/> | <div align="left">ALERTA DE BSM: Mantenha a Atenção aos Detalhes, tome muito cuidado pois se a escrita dos métodos CreateUser, CreateUser e Create  .</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |




<h2>👣 Passo 05 - Editar a camada AppContext.cs </h2>

Edite a classe AppContext.cs como descrito no código abaixo:

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

        public DbSet<User> Users { get; set; }
    }
}
```



<h2>👣 Passo 06 - Criar a camada Settings.cs </h2>

Crie a classe Settings.cs como descrito no código abaixo:

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace blogPessoal
{
    public static class Settings
    {
        public static string Secret = "fedaf7d8863b48e197b9287d492b708e";
    }
}
```



O Secret cria uma senha padrão que determina a comunicação pelo JWT.

<h2>👣 Passo 08 - Editar a camada Startup.cs </h2>

Edite a classe Startup.cs como descrito no código abaixo:

```c#
using blogPessoal.Repository;
using blogPessoal.Repository.impl;
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.HttpsPolicy;
using Microsoft.AspNetCore.Mvc;
using Microsoft.EntityFrameworkCore;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;
using Microsoft.IdentityModel.Tokens;
using Microsoft.OpenApi.Models;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
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


            services.AddDbContext<Data.AppContext>(options => options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
            services.AddScoped<ITemaRepository, TemaRepository>();
            services.AddScoped<IPostagemRepository, PostagemRepository>();
            services.AddScoped<IUserRepository, UserRepository>();
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



​	O código abaixo determina que  a aplicação utilizará addJwtBearer sobre API. No método AddJwtBearer será implementado apenas o básico, portanto apenas o saveToken será implentado como verdadeiro, para a aplicação consiga guardar o tokem enquanto estiver em execução.

​	A variavel key é determinada com a informação que vem do  secret.

```c#
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
```



<h2>👣 Passo 08 - Criando a camada TokenService.cs </h2>

Crie uma pasta chamada Service na raiz do seu projeto.

<div align="center"><img src="https://i.imgur.com/3Ns3CIU.png" title="source: imgur.com" /></div>

Dentro da pasta Service, crie a classe TokenService.cs como descrito no código abaixo:

```c#
using System;
using System.IdentityModel.Tokens.Jwt;
using System.Security.Claims;
using System.Text;
using blogPessoal.Model;
using Microsoft.IdentityModel.Tokens;

namespace blogPessoal.Service
{
    public static class TokenService
    {
        public static string GenerateToken(User user)
        {
            var tokenHandler = new JwtSecurityTokenHandler();
            var key = Encoding.ASCII.GetBytes(Settings.Secret);
            var tokenDescriptor = new SecurityTokenDescriptor
            {
                Subject = new ClaimsIdentity(new Claim[]
                {
                    new Claim(ClaimTypes.Name, user.Usuario.ToString()),
                   
                }),
                Expires = DateTime.UtcNow.AddHours(2),
                SigningCredentials = new SigningCredentials(new SymmetricSecurityKey(key), SecurityAlgorithms.HmacSha256Signature)
            };
            var token = tokenHandler.CreateToken(tokenDescriptor);
            return tokenHandler.WriteToken(token);
        }
    }
}
```

 	A Camada TokenService.cs tem como responsabilidade gerar o token para a nossa aplicação, dentro dela o método GenerateToken faz esse papel.

​	Através das informações do usuario é criado um token usando como principio o nome o email( atributo usuário) , o token possui validade de 2 horas como descrito na variável Expires, ao final é utilizado o nome e o email do usuário para gerar o token através do algoritmo de criptografia HmacSha256Signature, ao final do método é retornado o token criptografado. HmacSha256Signature é um tipo de criptografia utilizada para criptografar informações sensiveis.



<div align="left"> <a href="https://docs.microsoft.com/pt-br/dotnet/api/system.identitymodel.tokens.securityalgorithms?view=netframework-4.8" target="_blank"><b>Documentação: Algoritimos de criptografia</b></a></div>



<h2>👣 Passo 04 - Editando a camada UsuarioRepository </h2>



Agora vamos editar a classe **UsuarioRepository.cs**.

<br />

A seguir veja sua implementação:

```c#
using blogPessoal.Data;
using blogPessoal.Model;
using Microsoft.EntityFrameworkCore;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace blogPessoal.Repository
{
    public class UserRepository : IUserRepository
    {
        public readonly Data.AppContext _context;

        public UserRepository(AppContext context)
        {
            _context = context;
        }

        public User Create(User user)
        {
            User aux = _context.Users.FirstOrDefaultAsync(c => c.Id.Equals(user.Id)).Result;
            if (aux != null)
                return aux;

            _context.Users.Add(user);
            _context.SaveChangesAsync();

            return user;
        }

        public User CreateUser(User user)
        {
            var userResult = _context.Users.Where(u => u.Usuario == user.Usuario).FirstOrDefaultAsync();
            if (userResult.Result != null)
            {
                return null;
            }
            else
            {
                var valueBytes = Encoding.UTF8.GetBytes(user.Senha);
                user.Senha = System.Convert.ToBase64String(valueBytes);
                _context.Users.Add(user);
                _context.SaveChangesAsync();

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



Na camada UserRepository criaremos 3 métodos Create(User user), CreateUser(User user), GetUserName(string usuario, string senha)



O método Create(User user) tem como função criar um usuário na tabela user do banco de dados.



O método CreateUser(User user) tem como função criar um usuário na tabela user do banco de dados e criptografar a senha do usuario, ao chamar esse método antes de criptografar a senha é feito uma validação se o usuário já se encontra cadastrado no banco de dados, caso não esteja a senha será criptografada através do método FromBase64String() e Encoding.UTF8.GetString(), ao termino a informação é salva no banco de dados com a senha criptografada para proteger está informação sensível. 



​	O método GetUserName(string usuario, string senha) tem como função verificar se a informação do que está sendo passada via login de email e senha confere com o registro cadastrado no banco de dados, para isso é feito uma requisição na tabela user por email através do método _context.Users.Where(u => u.Usuario == user.Usuario).FirstOrDefaultAsync(), logo em seguida a senha é descriptografada através do método  string passwordDecode = Encoding.UTF8.GetString(valueBytes), se o login e a senha for igual a informação cadastrada no banco de dados é retornado o usuário no final do método.



<div align="left"> <a href="https://docs.microsoft.com/pt-br/dotnet/api/system.convert.tobase64string?view=net-6.0" target="_blank"><b>Documentação: Método Convert.ToBase64String</b></a></div>



<h2>👣 Passo 04 - Criando a camada  UserController </h2>



Agora vamos criar a classe **UserController.cs**.

<br />

A seguir veja sua implementação:

```c#
using blogPessoal.Model;
using blogPessoal.Repository;
using blogPessoal.Service;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;


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
        public ActionResult<User> Cadastrar([FromBody] User user)
        {

            _userRepository.CreateUser(user);
            return Created("/api/User/cadastrar", user);

        }

    }

}
```



​	O controller **UserController.cs**. possui 2 métodos Login e Cadastrar.

​	O método Cadastrar pega as informações de usuário pela body da requisição e envia para o o método CreateUser(user) para o cadastro do usuario no banco de dados.

​	O método Login pega as informações de usuário pela body da requisição e envia para o o método userRepository.GetUserName(model.Usuario, model.Senha); para verificação de senha e login do usuário, caso o método entregar  objeto null, o método entregará a resposta 401 Unauthorized("não autorizado"),	caso existir um usuário e senha igual a do banco de dados, é criado um objeto userResult com as informações Id, nome, usuário(email), em seguida é gerado o token através do método TokenService.GenerateToken(userResult), ao final do método é retornado o objeto userResult, com a informação do token com um prefixo Bearer, o prefixo Bearer é uma palavra chave que vem antes do token, crucial para autenticação do método.

​	Os dois método Login e Cadastrar são anotados com a anotação:  [AllowAnonymous], determina que esse métodos não precisam ser autenticado via token para ser acessados.



<div align="left"> <a href="https://docs.microsoft.com/pt-br/aspnet/core/security/authorization/simple?view=aspnetcore-6.0" target="_blank"><b>Documentação: Anotação [AllowAnonymous]</b></a></div>

<h2>👣 Passo 04 - Inserindo a anotação [Authorize] nos métodos do Controller </h2>



Agora vamos inserir a anotação **[Authorize]**  na classe **TemaController.cs**.

<br />

A seguir veja sua implementação:

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
    public class TemaController : ControllerBase
    {

        private readonly ITemaRepository _temaRepository;

        public TemaController(ITemaRepository temaRepository)
        {
            _temaRepository = temaRepository;
        }

        [HttpGet]
        [Authorize]
        public ActionResult<List<Tema>> GetAllTemas()
        {
            return Ok(_temaRepository.GetAll());
        }

        [HttpGet("{id}")]
        [Authorize]
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
        [Authorize]
        public List<Tema> GetByDescricao(string descricao)
        {
            return _temaRepository.GetByDescricao(descricao);
        }

        [HttpPost]
        [Authorize]
        public ActionResult<Tema> PostTema([FromBody] Tema tema)
        {
            var newTema = _temaRepository.Create(tema);
            return CreatedAtAction(nameof(GetAllTemas), new { id = newTema.Id }, newTema);
        }

        [HttpPut]
        [Authorize]
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
        [Authorize]
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





Agora vamos inserir a anotação **[Authorize]**  na classe **PostagemController.cs**.

<br />

A seguir veja sua implementação:

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
        [Authorize]
        public List<Postagem> GetPostagens()
        {
            return _postagemRepository.GetAll();
        }

        [HttpGet("{id}")]
        [Authorize]
        public ActionResult<Postagem> GetPostagens(int id)
        {
            return _postagemRepository.Get(id);
        }

        [HttpGet("titulo/{titulo}")]
        [Authorize]
        public List<Postagem> GetTituloPostagens(string titulo)
        {
            return _postagemRepository.GetTitulo(titulo);
        }

        [HttpPost]
        [Authorize]
        public ActionResult<Postagem> PostPostagens([FromBody] Postagem postagem)
        {
            var newPostagem = _postagemRepository.Create(postagem);
            return CreatedAtAction(nameof(GetPostagens), new { id = newPostagem.Id }, newPostagem);
        }


        [HttpDelete("{id}")]
        [Authorize]
        public ActionResult Delete(int id)
        {
            var postagemToDelete = _postagemRepository.Get(id);

            if (postagemToDelete == null)
                return NotFound();

            _postagemRepository.Delete(postagemToDelete.Id);
            return NoContent();


        }

        [HttpPut]
        [Authorize]
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



A anotação [Authorize] determina que esses métodos sejam broqueados, onde a requisição só é permitida caso o usuário ofereça um token na requisição.

<div align="left"> <a href="https://docs.microsoft.com/pt-br/aspnet/core/security/authorization/simple?view=aspnetcore-6.0" target="_blank"><b>Documentação: Anotação [Authorize]</b></a></div>



<h2>👣 Passo 07 - testando via  postman</h2>



### Testando o método cadastrar Usuario

1. execute o método post

2. insira a url http://localhost:5000/api/User/cadastrar

3. insira o objeto abaixo na body da requisição:

   ```json
   {
       "nome": "participante A",
       "usuario":"participante@generation.com",
       "senha":"123456"
   }
   ```

4. clique em Send

5. repare o status 201 e o response body com objeto criado.



<div align="center"><img src="https://i.imgur.com/rt1P6Xm.png" title="source: imgur.com" /></div>





### Testando o método login Usuario

1. execute o método post

2. insira a url http://localhost:5000/api/User/login

3. insira o objeto abaixo na body da requisição:

   ```json
   {
       "usuario":"participante@generation.com",
       "senha":"123456"
   }
   ```

4. clique em Send

5. repare o status 200 e o response body com objeto usuario e token.



<div align="center"><img src="https://i.imgur.com/uF0cHG4.png" title="source: imgur.com" /></div>







### Testando o método get Tema (sem token)



1. execute o método get
2. insira a url http://localhost:5000/api/Tema
3. clique em header
4. clique em send
5. repare o status 401 requisição não autorizada

<div align="center"><img src="https://i.imgur.com/T9rzd5x.png" title="source: imgur.com" /></div>



### Testando o método get Tema (enviando token)



1. copie o token = " **Bearer  ##################**"

2. execute o método get

3. insira a url http://localhost:5000/api/Tema

4. clique em header

   <div align="center"><img src="https://i.imgur.com/oKgwzqV.png" title="source: imgur.com" /></div>

5. insira o atributo Authorization

6. cole o valor do token no atributo Authorization

7. clique em send

8. repare o status 200 autorizado com a informação de um array vazio.



<div align="center"><img src="https://i.imgur.com/fru1FEL.png" title="source: imgur.com" /></div>



<div align="left"><img src="https://i.imgur.com/bQGvf3h.png" title="source: imgur.com" width="30px"/> <a href="https://github.com/Marcelo7211/blog-pessoal-aspnet-core/tree/CG-88-construcao-cook-book-asp-net-core-seguranca" target="_blank"><b>Código fonte: blogPessoal Security</b></a>

