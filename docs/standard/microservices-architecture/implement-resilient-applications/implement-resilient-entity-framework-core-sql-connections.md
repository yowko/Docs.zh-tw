---
title: 實作具有恢復功能的 Entity Framework Core SQL 連接
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 實作具有恢復功能的 Entity Framework Core SQL 連接
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 79f115a2d897463c213eda6f4d6951ff0cbeb3ca
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105471"
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a>實作具有恢復功能的 Entity Framework Core SQL 連接

在 Azure SQL DB 中，Entity Framework Core 已提供內部資料庫恢復連接功能和重試邏輯。 如果您想要使用[具有恢復功能的 EF Core 連接](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)，您必須針對每個 DbContext 連接啟用 Entity Framework 執行策略。

例如，EF Core 連接層級的下列程式碼可在連接失敗時重試具有恢復功能的 SQL 連接。

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>使用 BeginTransaction 和多個 DbContext 的執行策略和明確異動

在 EF Core 連接中啟用重試時，您使用 EF Core 執行的每項作業都會變成其本身可重試的作業。 如果發生暫時性失敗，SaveChanges 的每個查詢和每個呼叫會當做一個單位來重試。

不過，如果您的程式碼使用 BeginTransaction 起始異動，您將定義需視為一個單位的專屬作業群組，如果發生失敗，必須復原異動內的所有項目。 如果您在使用 EF 執行策略 (重試原則) 時嘗試執行該異動，並在異動中包含來自多個 DbContext 的數個 SaveChanges 呼叫，您會看到類似如下的例外狀況。

> System.InvalidOperationException：已設定的執行策略 'SqlServerRetryingExecutionStrategy' 不支援使用者起始的異動。 使用 'DbContext.Database.CreateExecutionStrategy()' 所傳回的執行策略，將異動中的所有作業當做一個可重試的單位來執行。

解決方法是使用代表必須執行之所有項目的委派，來手動叫用 EF 執行策略。 如果發生暫時性失敗，執行策略會再叫用委派一次。 例如，下列程式碼示範在更新產品並接著儲存 ProductPriceChangedIntegrationEvent 物件時 (此時必須使用不同的 DbContext)，如何在具有兩組多個 DbContext (\_catalogContext 和 IntegrationEventLogContext) 的 eShopOnContainers 中實作。

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

第一個 DbContext 是 \_catalogContext，第二個 DbContext 則位於 \_integrationEventLogService 物件中。 系統會使用 EF 執行策略跨多個 DbContext 執行認可動作。

## <a name="additional-resources"></a>其他資源

-   **Connection Resiliency and Command Interception with the Entity Framework (使用 Entity Framework 來恢復連接和攔截命令)**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Cesar de la Torre：Using Resilient Entity Framework Core Sql Connections and Transactions (使用具有恢復功能的 Entity Framework Core SQL 連接和異動)**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>


>[!div class="step-by-step"]
[上一頁](implement-retries-exponential-backoff.md)
[下一頁](implement-custom-http-call-retries-exponential-backoff.md)
