---
title: "使用做為容器執行的資料庫伺服器"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |使用做為容器執行的資料庫伺服器"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7e5f33c4e7edf9d0d4551c5125976fcb8fda392f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-database-server-running-as-a-container"></a>使用做為容器執行的資料庫伺服器

您可以在一般的獨立伺服器，在內部部署叢集，或 PaaS 服務等 Azure SQL DB 雲端上有資料庫 （SQL Server、 PostgreSQL、 MySQL 等）。 不過，對於開發和測試環境，讓您執行做為容器的資料庫是方便，因為您沒有任何外部的相依性，且只需執行 docker 撰寫命令會啟動整個應用程式。 擁有這些資料庫做為容器也是很好的整合測試，因為資料庫啟動容器中，而且一律填入相同的範例資料，好讓測試可以更容易預測。

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server 與微服務相關的資料庫執行的容器

在 eShopOnContainers，沒有名為 sql.data 中定義的容器[docker compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) microservices 所需的所有 SQL Server 資料庫都執行適用於 Linux 的 SQL Server 的檔案。 （您也可以使每個資料庫的一個 SQL Server 容器，但這需要更多的記憶體指派給 Docker）。Microservices 中很重要的一點是，每個微服務擁有其相關的資料，因此其相關的 SQL 資料庫在此情況下。 但是，這些資料庫可以是任何位置。

範例應用程式中的容器設定下列 YAML 程式碼在 docker compose.yml 檔案中，當您執行時執行的 SQL 伺服器 docker-撰寫組成。 請注意 YAML 程式碼已合併來自泛型的 compose.yml docker 和 docker compose.override.yml 檔案的組態資訊。 （通常您會將環境設定，從 SQL Server 映像相關的基底或靜態資訊。）

```yml
sql.data:
  image: microsoft/mssql-server-linux
  environment:
    - SA_PASSWORD=your@password
    - ACCEPT_EULA=Y
  ports:
    - "5434:1433"
```

下列的 docker run 命令可以執行該容器：

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

不過，如果您要部署多個容器應用程式，例如 eShopOnContainers，它會比較方便使用 docker-撰寫設定指令，以便在部署應用程式所需的所有容器。

當您第一次啟動此 SQL Server 容器時，容器會初始化 SQL Server 與您所提供的密碼。 一旦 SQL Server 正在執行做為容器，您可以透過任何規則的 SQL 連接，例如連接從 SQL Server Management Studio、 Visual Studio 中或 C 更新資料庫\#程式碼。

EShopOnContainers 應用程式初始化每個範例資料的微服務資料庫的資料在啟動時，將其植入下一節中所述。

需要為容器執行的 SQL Server 便不只適用於示範，您可能無法再存取 SQL Server 執行個體。 如前所述，也很適合用來開發和測試環境，讓您輕鬆執行整合測試從全新的 SQL Server 映像和已知的植入新範例資料的資料。

#### <a name="additional-resources"></a>其他資源

-   **Linux、 Mac、 或 Windows 上執行 SQL Server Docker 映像**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)

-   **連接及查詢使用 sqlcmd 的 SQL Server on Linux**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>在 Web 應用程式啟動的測試資料植入

應用程式啟動時，請將資料加入至資料庫，您可以設定類別中的方法啟動的 Web API 專案中加入程式碼如下所示：

```csharp
public class Startup
{
    // Other Startup code...
    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure code...
        // Seed data through our custom class
        CatalogContextSeed.SeedAsync(app)
            .Wait();
        // Other Configure code...
    }
}
```

自訂 CatalogContextSeed 類別中的下列程式碼會填入資料。

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

當您執行整合測試時，需要產生整合測試與一致的資料是很有用。 能夠重新，包括容器 （） 上執行的 SQL Server 執行個體中建立的所有項目是最適合用於測試環境。

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF 核心 InMemory 資料庫，以及做為容器執行的 SQL Server

使用 Entity Framework InMemory 資料庫提供者是另一個不錯的選擇時執行測試。 Web API 專案中，您可以在啟動類別的 ConfigureServices 方法中指定該組態：

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }
  
    // Other Startup code ...

}
```

雖然沒有重要的 catch。 記憶體中資料庫不支援專屬於特定資料庫的多個條件約束。 比方說，您可能會將唯一索引的資料行上加入 EF 核心模型中，並針對記憶體中資料庫来檢查，它不會讓您新增重複的值寫入測試。 但當您使用記憶體中資料庫時，您無法處理的資料行上的唯一索引。 因此，記憶體中資料庫行為與實際的 SQL Server 資料庫完全相同，不會模擬特定資料庫的條件約束。

即便如此，記憶體中資料庫仍很有用的測試和原型。 但如果您想要建立精確的整合測試的特定資料庫實作行為納入考量，您必須使用實際的資料庫，例如 SQL Server。 基於這個目的，在容器中執行 SQL Server 是優越 choice 和更精確比 EF 核心 InMemory 資料庫提供者。

### <a name="using-a-redis-cache-service-running-in-a-container"></a>使用 Redis 快取服務容器中執行

您可以執行 Redis 容器，特別是針對開發和測試及概念證明案例上。 此案例中非常方便，因為您可以在容器上執行所有相依性 — 不只針對您的本機開發機器，但針對您在 CI/CD 管線中的測試環境。

不過，當您在生產環境中執行 Redis，最好是尋找 Redis Microsoft Azure 中執行為 PaaS （平台即服務） 的高可用性方案。 在您的程式碼中，您只需要變更連接字串。

Redis 提供使用 Redis 的 Docker 映像。 該映像可從 Docker Hub 這個 url:

<https://hub.docker.com/_/redis/>

您可以在命令提示字元中執行下列 Docker CLI 命令，直接執行 Docker Redis 的容器：

```
  docker run --name some-redis -d redis
```

Redis 映像是由包含公開： 6379 （Redis 所使用的連接埠），因此標準容器連結會將它自動提供給連結的容器。

在 eShopOnContainers，basket.api 微服務會使用執行做為容器的 Redis 快取。 該 basket.data 容器定義一部分的多個容器 docker compose.yml 檔案，如下列範例所示：

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

這個程式碼的 docker compose.yml 定義名為 basket.data redis 映像為基礎，並發佈連接埠 6379 就內部而言，這表示它將會存取只能從執行於 Docker 主機中的其他容器的容器。

最後，在 docker compose.override.yml 檔案中，eShopOnContainers 範例 basket.api 微服務定義要用於該 Redis 容器的連接字串：

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
[上一個](多-container-應用程式-docker-compose.md) [下一步] (整合-事件為基礎的微服務-communications.md)
