---
title: 使用作為容器執行的資料庫伺服器
description: .NET 微服務：容器化 .NET 應用程式的架構 | 使用作為容器執行的資料庫伺服器？只適用於開發！ 了解原因。
ms.date: 10/02/2018
ms.openlocfilehash: a508ba734525b24e2f3f00408e2c59c8c00f1898
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291302"
---
# <a name="using-a-database-server-running-as-a-container"></a>使用作為容器執行的資料庫伺服器

您可將資料庫 (SQL Server、PostgreSQL、MySQL 等等) 放在一般的獨立伺服器、內部部署叢集，或如 Azure SQL DB 等雲端 PaaS 服務上。 不過，若為開發和測試環境，將資料庫執行為容器會很方便，因為您沒有任何外部相依性，只要執行 `docker-compose up` 命令即可啟動整個應用程式。 將這些資料庫當作容器也非常適合整合測試，因為資料庫是在容器中啟動，而且一律填入相同的範例資料，所以測試會更容易預測。

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server 執行為附微服務相關資料庫的容器

eShopOnContainers 中有個容器名為 sql.data，在 [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) 檔案中定義，此檔案執行 SQL Server for Linux 及微服務需要的所有 SQL Server 資料庫。 (您也可以每個資料庫各一個 SQL Server 容器，但這樣就需要指派更多的記憶體給 Docker。)微服務有一個重點是每項微服務擁有自己的相關資料，在本例中為其相關的 SQL 資料庫。 但是這些資料庫可以位在任何位置。

範例應用程式中的 SQL Server 容器，是在 docker-compose.yml 檔案中使用下列 YAML 程式碼設定，它會在您執行 `docker-compose up` 時執行。 請注意 YAML 程式碼已合併來自泛型 docker-compose.yml 檔案和 docker-compose.override.yml 檔案的組態資訊。 (通常您會將環境設定從 SQL Server 映像相關的基底或靜態資訊中分離出來。)

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

以類似的方式，而不是使用 `docker-compose`，下列 `docker run` 命令可以執行該容器：

```console
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

不過，如果您要部署多容器應用程式，例如 eShopOnContainers，使用 `docker-compose up` 命令會更方便，其會部署應用程式需要的所有容器。

當您第一次啟動此 SQL Server 容器時，容器會使用您提供的密碼初始化 SQL Server。 一旦 SQL Server 執行為容器，您就可以透過任何一般 SQL 連線來連線至資料庫來加以更新，例如從 SQL Server Management Studio、Visual Studio 或 C\# 程式碼。

eShopOnContainers 應用程式會在啟動時，將範例資料與資料一起植入，再用它初始化每個微服務資料庫，如下節所述。

將 SQL Server 執行為容器，不僅適合您可能無法存取 SQL Server 執行個體的示範； 如前所述，也非常適合開發和測試環境，讓您植入新的範例資料，從全新的 SQL Server 映像和已知資料，輕鬆執行整合測試。

#### <a name="additional-resources"></a>其他資源

- **在 Linux、Mac 或 Windows 上執行 SQL Server Docker 映像** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- **使用 sqlcmd 連線及查詢 Linux 上的 SQL Server** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>在 Web 應用程式啟動時植入測試資料

若要在應用程式啟動時將資料新增至資料庫，您可將與下列類似的程式碼新增至 Web API 專案之啟動類別的 Configure 方法：

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

下列自訂 CatalogContextSeed 類別中的程式碼會填入資料。

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

當您執行整合測試時，能夠產生與整合測試一致的資料會很有用。 能夠重新建立所有項目，包括在容器上執行的 SQL Server 執行個體，非常適合測試環境。

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core InMemory 資料庫與當作容器執行的 SQL Server

執行測試時另一個不錯的選擇，是使用 Entity Framework InMemory 資料庫提供者。 您可以在自己的 Web API 專案之啟動類別的 ConfigureServices 方法中指定該組態：

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

雖然有重要的 Catch。 記憶體內部資料庫不支援專門針對特定資料庫的多個限制式。 例如，您可能會在您 EF Core 模型的資料行中新增唯一索引，並針對記憶體內部資料庫撰寫測試，確認它不會讓您新增重複的值。 但當您在使用記憶體內部資料庫時，您無法處理資料行的唯一索引。 因此，記憶體內部資料庫的行為和實際 SQL Server 資料庫的行為不會一模一樣，它不會模擬資料庫特定的限制式。

即便如此，記憶體內部資料庫對測試與建立原型仍很有用。 但如果您想要建立精確的整合測試，將特定資料庫的實作行為納入考量，您必須使用實際的資料庫，例如 SQL Server。 基於這個目的，在容器中執行 SQL Server 是非常好的選擇，而且會比 EF Core InMemory 資料庫提供者更精確。

### <a name="using-a-redis-cache-service-running-in-a-container"></a>使用在容器中執行的 Redis 快取服務

您可以在容器上執行 Redis，特別是針對開發和測試以及概念證明案例。 本案例很方便，因為您可以在容器上執行所有的相依性，不只適用於您的本機開發機器，還適用於您在 CI/CD 管線中的測試環境。

不過，當您在生產環境中執行 Redis 時，最好是尋找執行為 PaaS (平台即服務) 的高可用性方案，例如 Redis Microsoft Azure。 在您的程式碼中，您只需要變更連接字串即可。

Redis 提供使用 Redis 的 Docker 映像。 該映像可從位於此 URL 的 Docker Hub 取得：

<https://hub.docker.com/\_/redis/>

您可以在命令提示字元中執行下列 Docker CLI 命令，直接執行 Docker Redis 容器：

```console
docker run --name some-redis -d redis
```

Redis 映像包括 expose:6379 (Redis 使用的連接埠)，因此標準容器連結會自動將它提供給已連結的容器。

在 eShopOnContainers 中，basket.api 微服務會使用當作容器執行的 Redis 快取。 該 basket.data 容器會定義為多容器 docker-compose.yml 檔案的一部分，如下列範例所示：

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

docker-compose.yml 的這段程式碼會根據 redis 映像，定義名為 basket.data 的容器，並在內部發佈連接埠 6379，表示它只能從在 Docker 主機中執行的其他容器存取。

最後，在 docker-compose.override.yml 檔案中，eShopOnContainers 範例的 basket.api 微服務會定義要用於該 Redis 容器的連接字串：

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

如前所述，docker 的內部網路 DNS 會解析微服務 "basket.data" 的名稱。

>[!div class="step-by-step"]
>[上一頁](multi-container-applications-docker-compose.md)
>[下一頁](integration-event-based-microservice-communications.md)
