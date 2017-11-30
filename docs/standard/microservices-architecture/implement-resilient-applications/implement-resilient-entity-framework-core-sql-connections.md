---
title: "實作有彈性的 Entity Framework Core SQL 連線"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |實作有彈性的 Entity Framework Core SQL 連線"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 8600625c2022d69ebaa2645c2a8159a848b12ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a>實作有彈性的 Entity Framework Core SQL 連線

Azure SQL DB、 針對 Entity Framework Core 已經提供內部資料庫連接恢復功能和重試邏輯。 但您必須啟用每個 DbContext 連接的 Entity Framework 執行策略，如果您想要有[彈性 EF 核心連線](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)。

比方說，下列程式碼在 EF 核心連接層級可讓具有恢復功能的 SQL 連線的連線失敗時重試。

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 5,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>執行策略和使用 BeginTransaction 和多個 DbContexts 的明確交易

在 EF 核心連線啟用重試時，您使用 EF 核心執行每項作業會變成可重試作業。 每個查詢和 SaveChanges 每次呼叫將會重試做為一個單位發生暫時性失敗時。

不過，如果您的程式碼啟動使用 BeginTransaction 的交易，您要定義您自己的作業需要被視為一個單位的群組，如果失敗，就會發生已復原在交易內的所有項目。 如果您嘗試使用的 EF 執行策略 （重試原則） 時執行該交易，並將在交易中包含來自多個 DbContexts 的數個 SaveChanges 呼叫，您會看到像下列的例外狀況。

> System.InvalidOperationException： 設定的執行策略 'SqlServerRetryingExecutionStrategy' 不支援使用者起始的交易。 在做為可重試單位的交易中執行所有作業中使用 'DbContext.Database.CreateExecutionStrategy()' 所傳回的執行策略。

解決方法是手動叫用的委派代表的所有項目需要執行的 EF 執行策略。 如果發生暫時性中斷，執行策略會叫用委派一次。 例如，下列程式碼顯示如何實作中具有兩個 eShopOnContainers 多個 DbContexts (\_catalogContext 和 IntegrationEventLogContext) 產品，然後儲存在更新時ProductPriceChangedIntegrationEvent 物件，需要使用不同的 DbContext。

```csharp
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem
    productToUpdate)
{
    // Other code ...
    // Update current product
    catalogItem = productToUpdate;

    // Use of an EF Core resiliency strategy when using multiple DbContexts
    // within an explicit transaction
    // See:
    // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
    var strategy = _catalogContext.Database.CreateExecutionStrategy();
    await strategy.ExecuteAsync(async () =>
    {
        // Achieving atomicity between original Catalog database operation and the
        // IntegrationEventLog thanks to a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
            _catalogContext.CatalogItems.Update(catalogItem);
            await _catalogContext.SaveChangesAsync();
            // Save to EventLog only if product price changed
            if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
            transaction.Commit();
        }
    });
}
```

First DbContext 是\_內，第二個 catalogContext 是 DbContext \_integrationEventLogService 物件。 認可動作會執行跨多個 DbContexts 使用 EF 執行策略。

## <a name="additional-resources"></a>其他資源

-   **連接恢復功能和命令攔截與 Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Cesar de la Torre：使用具有恢復功能的實體架構核心 Sql 連接與交易**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>


>[!div class="step-by-step"]
[上一個](實作-重試-指數-backoff.md) [下一步] (implement-custom-http-call-retries-exponential-backoff.md)
