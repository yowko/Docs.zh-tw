---
title: 使用作為容器運行的資料庫伺服器
description: 瞭解使用僅作為容器運行的資料庫伺服器進行開發的重要性。 從不用於生產。
ms.date: 01/30/2020
ms.openlocfilehash: 0cbc933003aac10970814378c27e88b5cb0ddbe5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628523"
---
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="e046c-104">使用作為容器運行的資料庫伺服器</span><span class="sxs-lookup"><span data-stu-id="e046c-104">Use a database server running as a container</span></span>

<span data-ttu-id="e046c-105">您可將資料庫 (SQL Server、PostgreSQL、MySQL 等等) 放在一般的獨立伺服器、內部部署叢集，或如 Azure SQL DB 等雲端 PaaS 服務上。</span><span class="sxs-lookup"><span data-stu-id="e046c-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="e046c-106">但是，對於開發和測試環境，將資料庫作為容器運行很方便，因為您沒有任何外部依賴關係，只需運行`docker-compose up`該命令即可啟動整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e046c-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="e046c-107">將這些資料庫當作容器也非常適合整合測試，因為資料庫是在容器中啟動，而且一律填入相同的範例資料，所以測試會更容易預測。</span><span class="sxs-lookup"><span data-stu-id="e046c-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="e046c-108">SQL Server 執行為附微服務相關資料庫的容器</span><span class="sxs-lookup"><span data-stu-id="e046c-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="e046c-109">在 eShopOn 容器中，有一個名為`sqldata`的容器，如[docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml)檔中定義的，該容器運行 Linux 實例的 SQL Server，該容器具有需要的所有微服務的 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e046c-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="e046c-110">微服務的一個關鍵點是每個微服務都擁有其相關資料，因此它應該有自己的資料庫。</span><span class="sxs-lookup"><span data-stu-id="e046c-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="e046c-111">但是，資料庫可以在任何地方。</span><span class="sxs-lookup"><span data-stu-id="e046c-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="e046c-112">在這種情況下，它們都位於同一容器中，以保持 Docker 記憶體要求盡可能低。</span><span class="sxs-lookup"><span data-stu-id="e046c-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="e046c-113">請記住，這是一個足夠好的開發解決方案，也許，測試，但不是生產。</span><span class="sxs-lookup"><span data-stu-id="e046c-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="e046c-114">範例應用程式中的 SQL Server 容器，是在 docker-compose.yml 檔案中使用下列 YAML 程式碼設定，它會在您執行 `docker-compose up` 時執行。</span><span class="sxs-lookup"><span data-stu-id="e046c-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="e046c-115">請注意 YAML 程式碼已合併來自泛型 docker-compose.yml 檔案和 docker-compose.override.yml 檔案的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="e046c-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="e046c-116">(通常您會將環境設定從 SQL Server 映像相關的基底或靜態資訊中分離出來。)</span><span class="sxs-lookup"><span data-stu-id="e046c-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="e046c-117">以類似的方式，而不是使用 `docker-compose`，下列 `docker run` 命令可以執行該容器：</span><span class="sxs-lookup"><span data-stu-id="e046c-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="e046c-118">不過，如果您要部署多容器應用程式，例如 eShopOnContainers，使用 `docker-compose up` 命令會更方便，其會部署應用程式需要的所有容器。</span><span class="sxs-lookup"><span data-stu-id="e046c-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="e046c-119">當您第一次啟動此 SQL Server 容器時，容器會使用您提供的密碼初始化 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="e046c-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="e046c-120">一旦 SQL Server 執行為容器，您就可以透過任何一般 SQL 連線來連線至資料庫來加以更新，例如從 SQL Server Management Studio、Visual Studio 或 C\# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e046c-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="e046c-121">eShopOnContainers 應用程式會在啟動時，將範例資料與資料一起植入，再用它初始化每個微服務資料庫，如下節所述。</span><span class="sxs-lookup"><span data-stu-id="e046c-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="e046c-122">將 SQL Server 執行為容器，不僅適合您可能無法存取 SQL Server 執行個體的示範；</span><span class="sxs-lookup"><span data-stu-id="e046c-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="e046c-123">如前所述，也非常適合開發和測試環境，讓您植入新的範例資料，從全新的 SQL Server 映像和已知資料，輕鬆執行整合測試。</span><span class="sxs-lookup"><span data-stu-id="e046c-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e046c-124">其他資源</span><span class="sxs-lookup"><span data-stu-id="e046c-124">Additional resources</span></span>

- <span data-ttu-id="e046c-125">**在 Linux、Mac 或 Windows 上運行 SQL 伺服器 Docker 映射** </span><span class="sxs-lookup"><span data-stu-id="e046c-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="e046c-126">**使用 sqlcmd 在 Linux 上連接和查詢 SQL Server** </span><span class="sxs-lookup"><span data-stu-id="e046c-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="e046c-127">在 Web 應用程式啟動時植入測試資料</span><span class="sxs-lookup"><span data-stu-id="e046c-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="e046c-128">要在應用程式啟動時將資料添加到資料庫，可以將如下所示的代碼添加到 Web API 專案`Main``Program`類中的方法：</span><span class="sxs-lookup"><span data-stu-id="e046c-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

```csharp
public static int Main(string[] args)
{
    var configuration = GetConfiguration();

    Log.Logger = CreateSerilogLogger(configuration);

    try
    {
        Log.Information("Configuring web host ({ApplicationContext})...", AppName);
        var host = CreateHostBuilder(configuration, args);

        Log.Information("Applying migrations ({ApplicationContext})...", AppName);
        host.MigrateDbContext<CatalogContext>((context, services) =>
        {
            var env = services.GetService<IWebHostEnvironment>();
            var settings = services.GetService<IOptions<CatalogSettings>>();
            var logger = services.GetService<ILogger<CatalogContextSeed>>();

            new CatalogContextSeed()
                .SeedAsync(context, env, settings, logger)
                .Wait();
        })
        .MigrateDbContext<IntegrationEventLogContext>((_, __) => { });

        Log.Information("Starting web host ({ApplicationContext})...", AppName);
        host.Run();

        return 0;
    }
    catch (Exception ex)
    {
        Log.Fatal(ex, "Program terminated unexpectedly ({ApplicationContext})!", AppName);
        return 1;
    }
    finally
    {
        Log.CloseAndFlush();
    }
}
```

<span data-ttu-id="e046c-129">在容器啟動期間應用遷移和種子資料庫時，有一個重要的注意事項。</span><span class="sxs-lookup"><span data-stu-id="e046c-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="e046c-130">由於資料庫伺服器可能由於任何原因不可用，因此在等待伺服器可用時必須處理重試。</span><span class="sxs-lookup"><span data-stu-id="e046c-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="e046c-131">此重試邏輯由`MigrateDbContext()`擴充方法處理，如以下代碼所示：</span><span class="sxs-lookup"><span data-stu-id="e046c-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

```cs
public static IWebHost MigrateDbContext<TContext>(
    this IWebHost host,
    Action<TContext,
    IServiceProvider> seeder)
      where TContext : DbContext
{
    var underK8s = host.IsInKubernetes();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        var logger = services.GetRequiredService<ILogger<TContext>>();

        var context = services.GetService<TContext>();

        try
        {
            logger.LogInformation("Migrating database associated with context {DbContextName}", typeof(TContext).Name);

            if (underK8s)
            {
                InvokeSeeder(seeder, context, services);
            }
            else
            {
                var retry = Policy.Handle<SqlException>()
                    .WaitAndRetry(new TimeSpan[]
                    {
                    TimeSpan.FromSeconds(3),
                    TimeSpan.FromSeconds(5),
                    TimeSpan.FromSeconds(8),
                    });

                //if the sql server container is not created on run docker compose this
                //migration can't fail for network related exception. The retry options for DbContext only
                //apply to transient exceptions
                // Note that this is NOT applied when running some orchestrators (let the orchestrator to recreate the failing service)
                retry.Execute(() => InvokeSeeder(seeder, context, services));
            }

            logger.LogInformation("Migrated database associated with context {DbContextName}", typeof(TContext).Name);
        }
        catch (Exception ex)
        {
            logger.LogError(ex, "An error occurred while migrating the database used on context {DbContextName}", typeof(TContext).Name);
            if (underK8s)
            {
                throw;          // Rethrow under k8s because we rely on k8s to re-run the pod
            }
        }
    }

    return host;
}
```

<span data-ttu-id="e046c-132">下列自訂 CatalogContextSeed 類別中的程式碼會填入資料。</span><span class="sxs-lookup"><span data-stu-id="e046c-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="e046c-133">當您執行整合測試時，能夠產生與整合測試一致的資料會很有用。</span><span class="sxs-lookup"><span data-stu-id="e046c-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="e046c-134">能夠重新建立所有項目，包括在容器上執行的 SQL Server 執行個體，非常適合測試環境。</span><span class="sxs-lookup"><span data-stu-id="e046c-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="e046c-135">EF Core InMemory 資料庫與當作容器執行的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="e046c-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="e046c-136">執行測試時另一個不錯的選擇，是使用 Entity Framework InMemory 資料庫提供者。</span><span class="sxs-lookup"><span data-stu-id="e046c-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="e046c-137">您可以在自己的 Web API 專案之啟動類別的 ConfigureServices 方法中指定該組態：</span><span class="sxs-lookup"><span data-stu-id="e046c-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="e046c-138">雖然有重要的 Catch。</span><span class="sxs-lookup"><span data-stu-id="e046c-138">There is an important catch, though.</span></span> <span data-ttu-id="e046c-139">記憶體內部資料庫不支援專門針對特定資料庫的多個限制式。</span><span class="sxs-lookup"><span data-stu-id="e046c-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="e046c-140">例如，您可能會在您 EF Core 模型的資料行中新增唯一索引，並針對記憶體內部資料庫撰寫測試，確認它不會讓您新增重複的值。</span><span class="sxs-lookup"><span data-stu-id="e046c-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="e046c-141">但當您在使用記憶體內部資料庫時，您無法處理資料行的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="e046c-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="e046c-142">因此，記憶體內部資料庫的行為和實際 SQL Server 資料庫的行為不會一模一樣，它不會模擬資料庫特定的限制式。</span><span class="sxs-lookup"><span data-stu-id="e046c-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="e046c-143">即便如此，記憶體內部資料庫對測試與建立原型仍很有用。</span><span class="sxs-lookup"><span data-stu-id="e046c-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="e046c-144">但如果您想要建立精確的整合測試，將特定資料庫的實作行為納入考量，您必須使用實際的資料庫，例如 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="e046c-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="e046c-145">基於這個目的，在容器中執行 SQL Server 是非常好的選擇，而且會比 EF Core InMemory 資料庫提供者更精確。</span><span class="sxs-lookup"><span data-stu-id="e046c-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="e046c-146">使用在容器中執行的 Redis 快取服務</span><span class="sxs-lookup"><span data-stu-id="e046c-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="e046c-147">您可以在容器上執行 Redis，特別是針對開發和測試以及概念證明案例。</span><span class="sxs-lookup"><span data-stu-id="e046c-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="e046c-148">本案例很方便，因為您可以在容器上執行所有的相依性，不只適用於您的本機開發機器，還適用於您在 CI/CD 管線中的測試環境。</span><span class="sxs-lookup"><span data-stu-id="e046c-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="e046c-149">不過，當您在生產環境中執行 Redis 時，最好是尋找執行為 PaaS (平台即服務) 的高可用性方案，例如 Redis Microsoft Azure。</span><span class="sxs-lookup"><span data-stu-id="e046c-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="e046c-150">在您的程式碼中，您只需要變更連接字串即可。</span><span class="sxs-lookup"><span data-stu-id="e046c-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="e046c-151">Redis 提供使用 Redis 的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="e046c-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="e046c-152">該映像可從位於此 URL 的 Docker Hub 取得：</span><span class="sxs-lookup"><span data-stu-id="e046c-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="e046c-153">您可以在命令提示字元中執行下列 Docker CLI 命令，直接執行 Docker Redis 容器：</span><span class="sxs-lookup"><span data-stu-id="e046c-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="e046c-154">Redis 映像包括 expose:6379 (Redis 使用的連接埠)，因此標準容器連結會自動將它提供給已連結的容器。</span><span class="sxs-lookup"><span data-stu-id="e046c-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="e046c-155">在 eShopOn 容器`basket-api`中，微服務使用作為容器運行的 Redis 緩存。</span><span class="sxs-lookup"><span data-stu-id="e046c-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="e046c-156">該`basketdata`容器被定義為多容器*docker-compose.yml*檔的一部分，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="e046c-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="e046c-157">docker-compose.yml 中的此代碼定義基於 redis`basketdata`映射命名的容器，並在內部發佈埠 6379。</span><span class="sxs-lookup"><span data-stu-id="e046c-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="e046c-158">這意味著它只能從 Docker 主機內運行的其他容器訪問。</span><span class="sxs-lookup"><span data-stu-id="e046c-158">This means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="e046c-159">最後，在*docker-compose.override.yml*檔中，eShopOnContainers 示例的`basket-api`微服務定義了用於該 Redis 容器的連接字串：</span><span class="sxs-lookup"><span data-stu-id="e046c-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="e046c-160">如前所述，微服務`basketdata`的名稱由 Docker 的內部網路 DNS 解析。</span><span class="sxs-lookup"><span data-stu-id="e046c-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e046c-161">[上一個](multi-container-applications-docker-compose.md)
>[下一個](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="e046c-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
