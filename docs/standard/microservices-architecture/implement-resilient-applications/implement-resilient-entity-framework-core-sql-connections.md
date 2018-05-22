---
title: 實作具有恢復功能的 Entity Framework Core SQL 連接
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 實作具有恢復功能的 Entity Framework Core SQL 連接
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 54d0df517514c359c155de35d34e1e0f56eed4eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="909d6-103">實作具有恢復功能的 Entity Framework Core SQL 連接</span><span class="sxs-lookup"><span data-stu-id="909d6-103">Implementing resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="909d6-104">在 Azure SQL DB 中，Entity Framework Core 已提供內部資料庫恢復連接功能和重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="909d6-104">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="909d6-105">如果您想要使用[具有恢復功能的 EF Core 連接](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)，您必須針對每個 DbContext 連接啟用 Entity Framework 執行策略。</span><span class="sxs-lookup"><span data-stu-id="909d6-105">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="909d6-106">例如，EF Core 連接層級的下列程式碼可在連接失敗時重試具有恢復功能的 SQL 連接。</span><span class="sxs-lookup"><span data-stu-id="909d6-106">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="909d6-107">使用 BeginTransaction 和多個 DbContext 的執行策略和明確異動</span><span class="sxs-lookup"><span data-stu-id="909d6-107">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="909d6-108">在 EF Core 連接中啟用重試時，您使用 EF Core 執行的每項作業都會變成其本身可重試的作業。</span><span class="sxs-lookup"><span data-stu-id="909d6-108">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="909d6-109">如果發生暫時性失敗，SaveChanges 的每個查詢和每個呼叫會當做一個單位來重試。</span><span class="sxs-lookup"><span data-stu-id="909d6-109">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="909d6-110">不過，如果您的程式碼使用 BeginTransaction 起始異動，您將定義需視為一個單位的專屬作業群組，如果發生失敗，必須復原異動內的所有項目。</span><span class="sxs-lookup"><span data-stu-id="909d6-110">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="909d6-111">如果您在使用 EF 執行策略 (重試原則) 時嘗試執行該異動，並在異動中包含來自多個 DbContext 的數個 SaveChanges 呼叫，您會看到類似如下的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="909d6-111">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="909d6-112">System.InvalidOperationException：已設定的執行策略 'SqlServerRetryingExecutionStrategy' 不支援使用者起始的異動。</span><span class="sxs-lookup"><span data-stu-id="909d6-112">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="909d6-113">使用 'DbContext.Database.CreateExecutionStrategy()' 所傳回的執行策略，將異動中的所有作業當做一個可重試的單位來執行。</span><span class="sxs-lookup"><span data-stu-id="909d6-113">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="909d6-114">解決方法是使用代表必須執行之所有項目的委派，來手動叫用 EF 執行策略。</span><span class="sxs-lookup"><span data-stu-id="909d6-114">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="909d6-115">如果發生暫時性失敗，執行策略會再叫用委派一次。</span><span class="sxs-lookup"><span data-stu-id="909d6-115">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="909d6-116">例如，下列程式碼示範在更新產品並接著儲存 ProductPriceChangedIntegrationEvent 物件時 (此時必須使用不同的 DbContext)，如何在具有兩組多個 DbContext (\_catalogContext 和 IntegrationEventLogContext) 的 eShopOnContainers 中實作。</span><span class="sxs-lookup"><span data-stu-id="909d6-116">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="909d6-117">第一個 DbContext 是 \_catalogContext，第二個 DbContext 則位於 \_integrationEventLogService 物件中。</span><span class="sxs-lookup"><span data-stu-id="909d6-117">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="909d6-118">系統會使用 EF 執行策略跨多個 DbContext 執行認可動作。</span><span class="sxs-lookup"><span data-stu-id="909d6-118">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="909d6-119">其他資源</span><span class="sxs-lookup"><span data-stu-id="909d6-119">Additional resources</span></span>

-   <span data-ttu-id="909d6-120">**Connection Resiliency and Command Interception with the Entity Framework (使用 Entity Framework 來恢復連接和攔截命令)**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="909d6-120">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="909d6-121">**Cesar de la Torre：Using Resilient Entity Framework Core Sql Connections and Transactions (使用具有恢復功能的 Entity Framework Core SQL 連接和異動)**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="909d6-121">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="909d6-122">[上一個] (implement-retries-exponential-backoff.md) [下一個] (implement-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="909d6-122">[Previous] (implement-retries-exponential-backoff.md) [Next] (implement-custom-http-call-retries-exponential-backoff.md)</span></span>
