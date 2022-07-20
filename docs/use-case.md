Oferecemos velocidade e confiança através de nossa Stack para times de desenvolvimento, no processo de conectar softwares de sua empresa através de um Worker.  

Iniciando seu produto através de nosso template base, trazemos o benefício onde você pode buildar e executar o projeto localmente. Ressaltamos que nossa Stack não é intrusiva, criamos código para ajudar times de desenvolvimento, mas cada desenvolvedor opta pelo o que prefere usar.  

Para começar sua jornada de desenvolvimento utilizando os recursos disponibilizados pelo Estúdio Mind aplique o template base para iniciar o desenvolvimento de um Worker completo utilizando C#, rodando em um cluster de contêiner.  

### Visão Geral
O plugin **`dotnet-worker-template`** adiciona em uma Stack a capacidade de provisionar serviços que executam em background.

### Pré-requisitos
Para utilizar o template **dotnet-api-template** você precisa instalar a tanto a [**`STK CLI`**](https://stackspot.com/) quanto o **.NET 5 e/ou 6**. 

### **Inputs**
Os inputs necessários para utilizar o template são:
| **Campo** | **Valor** | **Descrição** |
| :--- | :--- | :--- |
| Project Name| ex.: MyApp | Nome da aplicação  |
| Target Framework| 5 ou 6 | Framework em que o Worker será criado  |

### Exemplo de execução do projeto criado  

1. Depois de criar o projeto, acesse o diretório onde se encontra a `Solution` e os demais arquivos do projeto. Execute o seguinte comando:

```bash
    dotnet restore <MyApp>.Worker.sln
```

2. Compileo projeto rodando o comando abaixo:

```bash
    dotnet build <MyApp>.Worker.sln
```

3. Execute os testes unitários e de integração, rodando o seguinte comando:

```bash
dotnet test <MyApp>.Worker.sln
```

> Para testar a aplicação, ainda no mesmo diretório da `Solution`, execute o comando abaixo:

```bash
    dotnet run --project ./src/<MyApp>.Worker/<MyApp>.Worker.csproj
```

### Configuração do Docker

Para que o Docker funcione, você precisará adicionar um certificado SSL temporário e montar um volume para manter esse certificado.
Você pode encontrar no [Microsoft Docs](https://docs.microsoft.com/en-us/aspnet/core/security/docker-https?view=aspnetcore-6.0) que descrevem as etapas necessárias para Windows, macOS e Linux.

- **Para Windows**  
O seguinte comando precisará ser executado a partir do seu terminal para criar um certificado:

```bash
dotnet dev-certs https -ep %USERPROFILE%\.aspnet\https\aspnetapp.pfx -p Your_password123
dotnet dev-certs https --trust
```

> NOTA: Ao usar o PowerShell, substitua **%USERPROFILE% por $env:USERPROFILE**.

- **Para **macOS**  
O seguinte comando precisará ser executado a partir do seu terminal para criar um certificado:

```bash
dotnet dev-certs https -ep ${HOME}/.aspnet/https/aspnetapp.pfx -p Your_password123
dotnet dev-certs https --trust
```

- **Para Linux**  
O seguinte comando precisará ser executado a partir do seu terminal para criar um certificado:  

```bash
dotnet dev-certs https -ep ${HOME}/.aspnet/https/aspnetapp.pfx -p Your_password123
dotnet dev-certs https --trust
```

####  **Execução de contêiners Docker**  

1. Para construir e executar os contêiners Docker, execute o comando abaixo na raiz da solução onde você encontra o arquivo **`docker-compose.yml`**:  

 ```bash
 docker-compose -f 'docker-compose.yml' up --build
 ```

2. Em seguida, abra http://localhost:5000/health no seu navegador.

> Você também pode utilizar uma **IDE** (VSCode, Visual Studio) de sua preferência para realizar os passos acima.

Aplicando este projeto base, é possível adicionar ao seu template base as capacidades disponíveis na próxima página. 

