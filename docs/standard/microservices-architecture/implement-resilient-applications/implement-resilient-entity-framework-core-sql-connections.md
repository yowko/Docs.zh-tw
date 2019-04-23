---
title: 實作具復原功能的 Entity Framework Core SQL 連接
description: 了解如何實作具復原功能的 Entity Framework Core SQL 連線。 在雲端中使用 Azure SQL Database 時，此技術特別重要。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: b056df033a584bc51fed5ccd52a58a6331298aa6
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612247"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>實作具復原功能的 Entity Framework Core SQL 連接

針對 Azure SQL DB，Entity Framework (EF) Core 已提供內部資料庫連線恢復功能和重試邏輯。 如果您想要使用[具復原功能的 EF Core 連線](/ef/core/miscellaneous/connection-resiliency)，則必須為每個 <xref:Microsoft.EntityFrameworkCore.DbContext> 連線啟用 Entity Framework 執行策略。

例如，EF Core 連接層級的下列程式碼可在連接失敗時重試具有恢復功能的 SQL 連接。

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>使用 BeginTransaction 和多個 DbContext 的執行策略和明確異動

在 EF Core 連接中啟用重試時，您使用 EF Core 執行的每項作業都會變成其本身可重試的作業。 如果發生暫時性失敗，`SaveChanges` 的每個查詢和每個呼叫都會當做一個單位來重試。

不過，如果您的程式碼使用 `BeginTransaction` 起始異動，您將定義需視為一個單位的專屬作業群組。 如果發生失敗，必須復原異動內的所有項目。

如果您在使用 EF 執行策略 (重試原則) 時嘗試執行該交易，並呼叫來自多個 DbContext 的 `SaveChanges`，則會看到如下所示的例外狀況：

> System.InvalidOperationException：已設定的執行策略 'SqlServerRetryingExecutionStrategy' 不支援使用者起始的異動。 使用 'DbContext.Database.CreateExecutionStrategy()' 所傳回的執行策略，將異動中的所有作業當做一個可重試的單位來執行。

解決方法是使用代表必須執行之所有項目的委派，來手動叫用 EF 執行策略。 如果發生暫時性失敗，執行策略會再叫用委派一次。 例如，下列程式碼示範在更新產品並接著儲存 ProductPriceChangedIntegrationEvent 物件時 (此時必須使用不同的 DbContext)，如何在具有兩組多個 DbContext (\_catalogContext 和 IntegrationEventLogContext) 的 eShopOnContainers 中實作。

```csharp
public async Task<IActionResult> UpdateProduct(
    [FromBody]CatalogItem productToUpdate)
{
    // Other code ...

    var oldPrice = catalogItem.Price;
    var raiseProductPriceChangedEvent = oldPrice != productToUpdate.Price;

    // Update current product
    catalogItem = productToUpdate;

    // Save product's data and publish integration event through the Event Bus
    // if price has changed
    if (raiseProductPriceChangedEvent)
    {
        //Create Integration Event to be published through the Event Bus
        var priceChangedEvent = new ProductPriceChangedIntegrationEvent(
          catalogItem.Id, productToUpdate.Price, oldPrice);

       // Achieving atomicity between original Catalog database operation and the
       // IntegrationEventLog thanks to a local transaction
       await _catalogIntegrationEventService.SaveEventAndCatalogContextChangesAsync(
           priceChangedEvent);

       // Publish through the Event Bus and mark the saved event as published
       await _catalogIntegrationEventService.PublishThroughEventBusAsync(
           priceChangedEvent);
    }
    // Just save the updated product because the Product's Price hasn't changed.
    else
    {
        await _catalogContext.SaveChangesAsync();
    }
}
```

第一個 <xref:Microsoft.EntityFrameworkCore.DbContext> 為 `_catalogContext`，第二個 `DbContext` 則是在 `_integrationEventLogService` 物件內。 系統會使用 EF 執行策略跨所有 `DbContext` 物件執行認可動作。

為達成此多個 `DbContext` 認可，`SaveEventAndCatalogContextChangesAsync` 會使用 `ResilientTransaction` 類別，如以下程式碼所示：

```csharp
public class CatalogIntegrationEventService : ICatalogIntegrationEventService
{
    //…
    public async Task SaveEventAndCatalogContextChangesAsync(
        IntegrationEvent evt)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        await ResilientTransaction.New(_catalogContext).ExecuteAsync(async () =>
        {
            // Achieving atomicity between original catalog database 
            // operation and the IntegrationEventLog thanks to a local transaction
            await _catalogContext.SaveChangesAsync();
            await _eventLogService.SaveEventAsync(evt,
                _catalogContext.Database.CurrentTransaction.GetDbTransaction());
        });
    }
}
```

`ResilientTransaction.ExecuteAsync` 方法基本上會從傳遞的 `DbContext` (`_catalogContext`) 開始交易，然後使 `EventLogService` 使用該交易以儲存 `IntegrationEventLogContext` 的變更，然後認可整個交易。

```csharp
public class ResilientTransaction
{
    private DbContext _context;
    private ResilientTransaction(DbContext context) =>
        _context = context ?? throw new ArgumentNullException(nameof(context));

    public static ResilientTransaction New (DbContext context) =>
        new ResilientTransaction(context);

    public async Task ExecuteAsync(Func<Task> action)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts 
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        var strategy = _context.Database.CreateExecutionStrategy();
        await strategy.ExecuteAsync(async () =>
        {
            using (var transaction = _context.Database.BeginTransaction())
            {
                await action();
                transaction.Commit();
            }
        });
    }
}
```

## <a name="additional-resources"></a>其他資源

- **在 ASP.NET MVC 應用程式中使用 EF 來恢復連線和攔截命令** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de la Torre：使用具有恢復功能的 Entity Framework Core SQL 連線和異動** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[上一頁](implement-retries-exponential-backoff.md)
>[下一頁](explore-custom-http-call-retries-exponential-backoff.md)
