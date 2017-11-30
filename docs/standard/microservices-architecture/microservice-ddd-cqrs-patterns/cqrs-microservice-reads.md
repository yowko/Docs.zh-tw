---
title: "實作讀取/查詢中 CQRS 微服務"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |實作讀取/查詢中 CQRS 微服務"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e017aaaa701d8033110be8d6244d3e1120fc4fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="e32c2-104">實作讀取/查詢中 CQRS 微服務</span><span class="sxs-lookup"><span data-stu-id="e32c2-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="e32c2-105">讀取/查詢，從 eShopOnContainers 參考應用程式排序的微服務會實作 DDD 模型和交易式區域之外另行查詢。</span><span class="sxs-lookup"><span data-stu-id="e32c2-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="e32c2-106">這項作業完成，主要是因為查詢和交易的需求會大幅不同。</span><span class="sxs-lookup"><span data-stu-id="e32c2-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="e32c2-107">寫入執行必須與網域邏輯相容的交易。</span><span class="sxs-lookup"><span data-stu-id="e32c2-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="e32c2-108">查詢，相反地，具有等冪性，而且可以從定義域規則隔離。</span><span class="sxs-lookup"><span data-stu-id="e32c2-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="e32c2-109">如圖 9-3 所示，此方法很簡單。</span><span class="sxs-lookup"><span data-stu-id="e32c2-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="e32c2-110">API 介面是由 Web API 控制器使用任何基礎結構 （例如微 ORM 例如 Dapper），並傳回根據 UI 應用程式的需求動態 ViewModels 實作。</span><span class="sxs-lookup"><span data-stu-id="e32c2-110">The API interface is implemented by the Web API controllers using any infrastructure (such as a micro ORM like Dapper) and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="e32c2-111">**圖 9-3**。</span><span class="sxs-lookup"><span data-stu-id="e32c2-111">**Figure 9-3**.</span></span> <span data-ttu-id="e32c2-112">CQRS 微服務中的查詢最簡單的方法</span><span class="sxs-lookup"><span data-stu-id="e32c2-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="e32c2-113">這是最簡單的查詢可能的方法。</span><span class="sxs-lookup"><span data-stu-id="e32c2-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="e32c2-114">查詢定義查詢資料庫，並傳回每個查詢，立即建立動態 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="e32c2-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="e32c2-115">查詢都具有等冪性，因為它們不會變更執行查詢多少次的資料。</span><span class="sxs-lookup"><span data-stu-id="e32c2-115">Since the queries are idempotent, they will not change the data no matter how many times you run a query.</span></span> <span data-ttu-id="e32c2-116">因此，您不需要使用中交易的側邊，彙總與其他模式，例如任何 DDD 模式，以限制，這就是為什麼查詢會從交易式區域分隔。</span><span class="sxs-lookup"><span data-stu-id="e32c2-116">Therefore, you do not need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="e32c2-117">只要查詢資料庫中的 UI 所需要的資料，並傳回不需要以靜態方式是動態 ViewModel 隨處 （沒有 ViewModels 類別） 除了中定義的 SQL 陳述式本身。</span><span class="sxs-lookup"><span data-stu-id="e32c2-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="e32c2-118">由於這是一個簡單的方法時，程式碼所需的查詢端 (例如程式碼使用 ORM 喜歡微[Dapper](https://github.com/StackExchange/Dapper)) 可以實作[內相同的 Web API 專案](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)。</span><span class="sxs-lookup"><span data-stu-id="e32c2-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="e32c2-119">圖 9-4 顯示這點。</span><span class="sxs-lookup"><span data-stu-id="e32c2-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="e32c2-120">查詢中所定義**Ordering.API** eShopOnContainers 方案內的微服務專案。</span><span class="sxs-lookup"><span data-stu-id="e32c2-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="e32c2-121">**圖 9-4**。</span><span class="sxs-lookup"><span data-stu-id="e32c2-121">**Figure 9-4**.</span></span> <span data-ttu-id="e32c2-122">在 eShopOnContainers 訂購微服務中的查詢</span><span class="sxs-lookup"><span data-stu-id="e32c2-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="e32c2-123">使用 ViewModels 特別設定為用戶端應用程式，獨立於網域模型條件約束</span><span class="sxs-lookup"><span data-stu-id="e32c2-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="e32c2-124">取得用戶端應用程式所需的資料執行查詢，因為傳回的型別可以特別針對進行用戶端，根據查詢所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="e32c2-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="e32c2-125">這些模型或資料傳輸物件 (Dto)，稱為 ViewModels。</span><span class="sxs-lookup"><span data-stu-id="e32c2-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="e32c2-126">傳回的資料 (ViewModel) 可以是聯結來自多個實體或資料表的資料，在資料庫中，或甚至可跨多個交易式區域的網域模型中定義的彙總的結果。</span><span class="sxs-lookup"><span data-stu-id="e32c2-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="e32c2-127">在此情況下，您要建立獨立網域模型的查詢，因為彙總界限和條件約束完全略過，而且可用來查詢任何資料表和您可能需要的資料行。</span><span class="sxs-lookup"><span data-stu-id="e32c2-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you are free to query any table and column you might need.</span></span> <span data-ttu-id="e32c2-128">此方法提供很大的彈性和產能，為開發人員建立或更新的查詢。</span><span class="sxs-lookup"><span data-stu-id="e32c2-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="e32c2-129">ViewModels 可以是靜態類別中定義的型別。</span><span class="sxs-lookup"><span data-stu-id="e32c2-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="e32c2-130">或者，您可以在建立以動態方式根據查詢執行 （因為實作在排序的微服務），這是非常靈活的開發人員。</span><span class="sxs-lookup"><span data-stu-id="e32c2-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="e32c2-131">使用 Dapper 微 ORM 為執行查詢</span><span class="sxs-lookup"><span data-stu-id="e32c2-131">Using Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="e32c2-132">您可以使用任何微 ORM、 Entity Framework 的核心或甚至純 ADO.NET 進行查詢。</span><span class="sxs-lookup"><span data-stu-id="e32c2-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="e32c2-133">在範例應用程式中，我們選取受歡迎的微 ORM 的理想範例為 eShopOnContainers 中順序的微服務 Dapper。</span><span class="sxs-lookup"><span data-stu-id="e32c2-133">In the sample application, we selected Dapper for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="e32c2-134">執行一般的 SQL 查詢時絕佳的效能，因為它是一個非常輕微的架構。</span><span class="sxs-lookup"><span data-stu-id="e32c2-134">It can run plain SQL queries with great performance, because it is a very light framework.</span></span> <span data-ttu-id="e32c2-135">您可以使用 Dapper，來撰寫 SQL 查詢，可以存取並加入多個資料表。</span><span class="sxs-lookup"><span data-stu-id="e32c2-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="e32c2-136">Dapper 是開放原始碼專案 （原始 Sam Saffron 所建立），而且屬於中使用的建置組塊[堆疊溢位](https://stackoverflow.com/)。</span><span class="sxs-lookup"><span data-stu-id="e32c2-136">Dapper is an open source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="e32c2-137">若要使用 Dapper，您只需要安裝它透過[Dapper NuGet 封裝](https://www.nuget.org/packages/Dapper)，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e32c2-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure.</span></span>

![](./media/image5.png)

<span data-ttu-id="e32c2-138">您也必須加入 using 陳述式，使您的程式碼可存取的 Dapper 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="e32c2-138">You will also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="e32c2-139">當您在程式碼中使用 Dapper 時，您會直接使用在 System.Data.SqlClient 命名空間中的 SqlClient 類別。</span><span class="sxs-lookup"><span data-stu-id="e32c2-139">When you use Dapper in your code, you directly use the SqlClient class available in the System.Data.SqlClient namespace.</span></span> <span data-ttu-id="e32c2-140">透過 QueryAsync 方法和其他擴充 SqlClient 類別的擴充方法，您只可以直接且高效能的方式執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e32c2-140">Through the QueryAsync method and other extension methods which extend the SqlClient class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-and-static-viewmodels"></a><span data-ttu-id="e32c2-141">動態和靜態 ViewModels</span><span class="sxs-lookup"><span data-stu-id="e32c2-141">Dynamic and static ViewModels</span></span>

<span data-ttu-id="e32c2-142">排序的微服務的下列程式碼所示，大部分的查詢所傳回的 ViewModels 會實作為*動態*。</span><span class="sxs-lookup"><span data-stu-id="e32c2-142">As shown in the following code from the ordering microservice, most of the ViewModels returned by the queries are implemented as *dynamic*.</span></span> <span data-ttu-id="e32c2-143">這表示要傳回的屬性子集為根據查詢本身。</span><span class="sxs-lookup"><span data-stu-id="e32c2-143">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="e32c2-144">如果您加入新的資料行的查詢或聯結時，該資料是以動態方式加入傳回 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="e32c2-144">If you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span> <span data-ttu-id="e32c2-145">這種方法可減少需要修改查詢，以回應基礎資料模型，讓這種設計方式，更有彈性且容許未來變更的更新。</span><span class="sxs-lookup"><span data-stu-id="e32c2-145">This approach reduces the need to modify queries in response to updates to the underlying data model, making this design approach more flexible and tolerant of future changes.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
@"SELECT o.[Id] as ordernumber,
o.[OrderDate] as [date],os.[Name] as [status],
SUM(oi.units*oi.unitprice) as total
FROM [ordering].[Orders] o
LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
  }
}
```

<span data-ttu-id="e32c2-146">很重要的一點是，使用動態類型，傳回的集合的資料將以動態方式組合成 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="e32c2-146">The important point is that by using a dynamic type, the returned collection of data will be dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="e32c2-147">對於大部分查詢，您不需要預先定義 DTO 或 ViewModel 類別，讓其編碼簡單且更有生產力。</span><span class="sxs-lookup"><span data-stu-id="e32c2-147">For most queries, you do not need to predefine a DTO or ViewModel class, which makes coding them straightforward and productive.</span></span> <span data-ttu-id="e32c2-148">不過，您可以預先定義 ViewModels （例如，預先定義的 Dto) 如果您想要以更具限制性的定義，做為合約有 ViewModels。</span><span class="sxs-lookup"><span data-stu-id="e32c2-148">However, you can predefine ViewModels (like predefined DTOs) if you want to have ViewModels with a more restricted definition as contracts.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e32c2-149">其他資源</span><span class="sxs-lookup"><span data-stu-id="e32c2-149">Additional resources</span></span>

-   <span data-ttu-id="e32c2-150">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="e32c2-150">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="e32c2-151">**Julie Lerman。資料點-Dapper、 Entity Framework 和混合式應用程式 （MSDN Mag.文章）**</span><span class="sxs-lookup"><span data-stu-id="e32c2-151">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="e32c2-152">*https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="e32c2-152">*https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e32c2-153">[上一個](eshoponcontainers-cqrs-ddd-microservice.md) [下一步] (ddd-導向-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="e32c2-153">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
