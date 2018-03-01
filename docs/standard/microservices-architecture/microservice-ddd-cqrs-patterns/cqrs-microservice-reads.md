---
title: "在 CQRS 微服務中實作讀取/查詢"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 在 CQRS 微服務中實作讀取/查詢"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/02/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ca9bcefb317d2b3c7c225b773918ca4a2484cb8f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="297dd-104">在 CQRS 微服務中實作讀取/查詢</span><span class="sxs-lookup"><span data-stu-id="297dd-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="297dd-105">如需讀取/查詢，eShopOnContainers 參考應用程式的訂購微服務，會在 DDD 模型和交易區域之外實作查詢。</span><span class="sxs-lookup"><span data-stu-id="297dd-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="297dd-106">這項作業能夠完成，主要是因為查詢和交易的需求大不相同。</span><span class="sxs-lookup"><span data-stu-id="297dd-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="297dd-107">寫入的執行交易必須與網域邏輯相容。</span><span class="sxs-lookup"><span data-stu-id="297dd-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="297dd-108">另一方面，查詢具有等冪性，可從網域規則中隔離。</span><span class="sxs-lookup"><span data-stu-id="297dd-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="297dd-109">方法很簡單，如圖 9-3 所示。</span><span class="sxs-lookup"><span data-stu-id="297dd-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="297dd-110">API 介面是由 Web API 控制器實作，這些控制器會使用任何基礎結構，例如 Dapper 等微物件關聯式對應 (ORM)，並根據 UI 應用程式的需求傳回動態 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="297dd-110">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="297dd-111">**圖 9-3**。</span><span class="sxs-lookup"><span data-stu-id="297dd-111">**Figure 9-3**.</span></span> <span data-ttu-id="297dd-112">CQRS 微服務中最簡單的查詢方法</span><span class="sxs-lookup"><span data-stu-id="297dd-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="297dd-113">這是最簡單可行的查詢方法。</span><span class="sxs-lookup"><span data-stu-id="297dd-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="297dd-114">查詢定義會查詢資料庫，並傳回每個查詢立即建立的動態 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="297dd-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="297dd-115">因為查詢都具有等冪性，所以無論您執行查詢多少次，它們都不會變更資料。</span><span class="sxs-lookup"><span data-stu-id="297dd-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="297dd-116">因此，您不必受限於交易端使用的任何 DDD 模式，例如彙總及其他模式，這就是查詢與交易區域分開的原因。</span><span class="sxs-lookup"><span data-stu-id="297dd-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="297dd-117">您只要向資料庫查詢 UI 需要的資料，並傳回不需要在任何位置以靜態方式定義的動態 ViewModel (ViewModel 沒有類別)，SQL 陳述式本身除外。</span><span class="sxs-lookup"><span data-stu-id="297dd-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="297dd-118">因為這是簡單的方法，所以查詢端需要的程式碼 (例如使用 [Dapper](https://github.com/StackExchange/Dapper) 等微 ORM 的程式碼) 可在[相同的 Web API 專案](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)中實作。</span><span class="sxs-lookup"><span data-stu-id="297dd-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="297dd-119">如圖 9-4 所示。</span><span class="sxs-lookup"><span data-stu-id="297dd-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="297dd-120">查詢是在 eShopOnContainers 解決方案內的 **Ordering.API** 微服務專案中所定義。</span><span class="sxs-lookup"><span data-stu-id="297dd-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="297dd-121">**圖 9-4**。</span><span class="sxs-lookup"><span data-stu-id="297dd-121">**Figure 9-4**.</span></span> <span data-ttu-id="297dd-122">eShopOnContainers 訂購微服務中的查詢</span><span class="sxs-lookup"><span data-stu-id="297dd-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="297dd-123">使用專為用戶端應用程式建立的 ViewModel，獨立於網域模型限制式之外</span><span class="sxs-lookup"><span data-stu-id="297dd-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="297dd-124">因為執行查詢是為取得用戶端應用程式所需要的資料，所以可以根據查詢傳回的資料，專為用戶端建立傳回型別。</span><span class="sxs-lookup"><span data-stu-id="297dd-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="297dd-125">這些模型或資料傳輸物件 (DTO)，稱為 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="297dd-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="297dd-126">傳回的資料 (ViewModel) 可以是多個實體或資料庫多資料表的聯結資料結果，甚至可以是跨多個在交易區域網域模型中定義的彙總結果。</span><span class="sxs-lookup"><span data-stu-id="297dd-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="297dd-127">在此情況下，因為您要建立獨立於網域模型外的查詢，所以完全略過彙總界限和限制式，而且您可以隨意查詢可能需要的任何資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="297dd-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="297dd-128">此方法為開發人員建立或更新查詢提供了極大的彈性和生產力。</span><span class="sxs-lookup"><span data-stu-id="297dd-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="297dd-129">ViewModel 可以是在類別中定義的靜態類型。</span><span class="sxs-lookup"><span data-stu-id="297dd-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="297dd-130">或者，您可以根據執行的查詢以動態方式建立它們 (如同在訂購微服務中實作的一樣)，這對開發人員而言非常方便好用。</span><span class="sxs-lookup"><span data-stu-id="297dd-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="297dd-131">將 Dapper 用作微 ORM 以執行查詢</span><span class="sxs-lookup"><span data-stu-id="297dd-131">Using Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="297dd-132">您可以使用任何微 ORM、Entity Framework Core 或甚至純 ADO.NET 進行查詢。</span><span class="sxs-lookup"><span data-stu-id="297dd-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="297dd-133">在範例應用程式中，eShopOnContainers 的訂購微服務選取 Dapper 為熱門的微 ORM 範例。</span><span class="sxs-lookup"><span data-stu-id="297dd-133">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="297dd-134">它在執行一般 SQL 查詢時有絕佳的效能，因為它是非常輕簡的架構。</span><span class="sxs-lookup"><span data-stu-id="297dd-134">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="297dd-135">您可以使用 Dapper 撰寫能存取並聯結多份資料表的 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="297dd-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="297dd-136">Dapper 是開放原始碼專案 (原創者為 Sam Saffron)，屬於 [Stack Overflow](https://stackoverflow.com/) (堆疊溢位) 的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="297dd-136">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="297dd-137">若要使用 Dapper，您只需要透過 [Dapper NuGet 套件](https://www.nuget.org/packages/Dapper)安裝它即可，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="297dd-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![](./media/image4.1.png)

<span data-ttu-id="297dd-138">您也需要新增 using 陳述式，以便您的程式碼存取 Dapper 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="297dd-138">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="297dd-139">當您在程式碼中使用 Dapper 時，您可直接使用 <xref:System.Data.SqlClient> 命名空間提供的 <xref:System.Data.SqlClient.SqlConnection> 類別。</span><span class="sxs-lookup"><span data-stu-id="297dd-139">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="297dd-140">透過 QueryAsync 方法和其他擴充 <xref:System.Data.SqlClient.SqlConnection> 類別的擴充方法，您可以直接且有效率的只執行查詢。</span><span class="sxs-lookup"><span data-stu-id="297dd-140">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="297dd-141">動態 ViewModel 與靜態 ViewModel</span><span class="sxs-lookup"><span data-stu-id="297dd-141">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="297dd-142">從伺服器端將 ViewModel 傳回用戶端應用程式時，您可以將這些 ViewModel 視為不同於您實體模型內部網域實體的 DTO，因為 ViewModel 是依用戶端應用程式需要的方式保留資料。</span><span class="sxs-lookup"><span data-stu-id="297dd-142">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="297dd-143">因此，在許多情況下，您可以彙總來自多個網域實體的資料，並根據用戶端應用程式需要該資料的方式精確撰寫 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="297dd-143">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="297dd-144">您可以明確定義這些 ViewModel 或 DTO (為資料持有者類別)，如稍後之程式碼片段中示範的 [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) 類別；或者可以只根據您查詢傳回的屬性，僅傳回動態 ViewModel 或動態 DTO 作為 `dynamic` 類型。</span><span class="sxs-lookup"><span data-stu-id="297dd-144">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a `dynamic` type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="297dd-145">ViewModel 作為動態類型</span><span class="sxs-lookup"><span data-stu-id="297dd-145">ViewModel as dynamic type</span></span>

<span data-ttu-id="297dd-146">如下列程式碼所示，透過傳回在內部以查詢所傳回屬性為基礎的動態類型，查詢可以直接傳回 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="297dd-146">As shown in the following code, a ViewModel can be directly returned by the queries by returning a dynamic type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="297dd-147">這表示要傳回的屬性子集是以查詢本身為基礎。</span><span class="sxs-lookup"><span data-stu-id="297dd-147">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="297dd-148">因此，如果您在查詢或聯結中新增新的資料行，該資料會以動態方式新增至傳回的 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="297dd-148">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span>

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

<span data-ttu-id="297dd-149">重點是，透過使用動態類型，傳回的資料集合會以動態方式組合成 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="297dd-149">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="297dd-150">優點：這種方法可在您每次更新查詢的 SQL 句子時，減少修改靜態 ViewModel 類別的需求，讓這種設計方法在撰寫程式碼更為靈活，簡單快速地因應未來的變更。</span><span class="sxs-lookup"><span data-stu-id="297dd-150">*Pros:* This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="297dd-151">缺點：長期來看，動態類型對清晰度可能造成負面影響，並影響服務與用戶端應用程式的相容性。</span><span class="sxs-lookup"><span data-stu-id="297dd-151">*Cons:* In the long term, dynamic types can impact negatively the clarity and impact the compatibility of a service with client apps.</span></span> <span data-ttu-id="297dd-152">此外，如果使用動態類型，像 Swagger 這類的中介軟體無法提供傳回型別的同級文件。</span><span class="sxs-lookup"><span data-stu-id="297dd-152">In addition, middleware software like Swagger cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="297dd-153">ViewModel 作為預先定義的 DTO 類別</span><span class="sxs-lookup"><span data-stu-id="297dd-153">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="297dd-154">優點：擁有靜態預先定義的 ViewModel 類別，像以明確 DTO 類別為基礎的「合約」，絕對適合公用 API，但也適用於長期的微服務，即使只有相同的應用程式使用它們。</span><span class="sxs-lookup"><span data-stu-id="297dd-154">*Pros:* Having static predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="297dd-155">如要指定 Swagger 的回應類型，您需要使用明確的 DTO 類別作為傳回型別。</span><span class="sxs-lookup"><span data-stu-id="297dd-155">If you want to specify response types for swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="297dd-156">因此，預先定義的 DTO 類別可讓您提供更豐富的 Swagger 資訊。</span><span class="sxs-lookup"><span data-stu-id="297dd-156">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="297dd-157">這會在使用 API 時改善 API 文件和相容性。</span><span class="sxs-lookup"><span data-stu-id="297dd-157">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="297dd-158">缺點：如前所述，更新程式碼時，它會採用更多步驟來更新 DTO 類別。</span><span class="sxs-lookup"><span data-stu-id="297dd-158">*Cons:* As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="297dd-159">經驗提示：在 eShopOnContainers 訂購微服務實作的查詢中，我們就開始使用動態 ViewModel 進行開發，因為它在早期開發階段非常簡單靈活。</span><span class="sxs-lookup"><span data-stu-id="297dd-159">*Tip based on our experience:* In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="297dd-160">但是，一旦開發趨於穩定，我們會選擇重構 API 並使用靜態或預先定義的 DTO 取代 ViewModel，因為這樣可讓微服務取用者更清楚知道用作「合約」的明確 DTO 類型。</span><span class="sxs-lookup"><span data-stu-id="297dd-160">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="297dd-161">在下例中，您會看到查詢如何使用明確的 ViewModel DTO 類別：OrderSummary 類別，傳回資料。</span><span class="sxs-lookup"><span data-stu-id="297dd-161">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            var result = await connection.QueryAsync<dynamic>(
                  @"SELECT o.[Id] as ordernumber, 
                  o.[OrderDate] as [date],os.[Name] as [status], 
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid 
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    } 
}
```

#### <a name="describing-response-types-of-web-apis"></a><span data-ttu-id="297dd-162">描述 Web API 的回應類型</span><span class="sxs-lookup"><span data-stu-id="297dd-162">Describing response types of Web APIs</span></span>

<span data-ttu-id="297dd-163">取用 Web API 和微服務的開發人員最關心的是傳回的內容，尤其是回應類型和錯誤碼 (如果不是標準的話)。</span><span class="sxs-lookup"><span data-stu-id="297dd-163">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="297dd-164">這些是以 XML 註解和資料註釋進行處理。</span><span class="sxs-lookup"><span data-stu-id="297dd-164">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="297dd-165">Swagger UI 中沒有正確的文件，取用者就不清楚應該傳回哪些類型或可以傳回哪些 HTTP 代碼。</span><span class="sxs-lookup"><span data-stu-id="297dd-165">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="297dd-166">藉由新增 <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType> 已修正該問題，因此 Swagger 可以產生更豐富的 API 傳回模型和值的相關資訊，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="297dd-166">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swagger can generate richer information about the API return model and values, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
       //Additional code...
       [Route("")]
       [HttpGet]
       [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
                             (int)HttpStatusCode.OK)]
       public async Task<IActionResult> GetOrders()
       {
           var orderTask = _orderQueries.GetOrdersAsync();
           var orders = await orderTask;
           return Ok(orders);
        }
    }
}
```

<span data-ttu-id="297dd-167">不過，`ProducesResponseType` 屬性不能用作動態類型，卻需要使用像 `OrderSummary` ViewModel DTO 的明確類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="297dd-167">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="297dd-168">這是就長期而言，明確的傳回型別優於動態類型的另一個原因。</span><span class="sxs-lookup"><span data-stu-id="297dd-168">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span>
<span data-ttu-id="297dd-169">使用 `ProducesResponseType` 屬性時，您也可以就可能的 HTTP 錯誤/程式碼指定預期結果的內容，例如 200、400 等等。</span><span class="sxs-lookup"><span data-stu-id="297dd-169">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200,400, etc.</span></span>

<span data-ttu-id="297dd-170">在下圖中，您會看到 Swagger UI 如何顯示 ResponseType 資訊。</span><span class="sxs-lookup"><span data-stu-id="297dd-170">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![](./media/image5.png)

<span data-ttu-id="297dd-171">**圖 9-5**。</span><span class="sxs-lookup"><span data-stu-id="297dd-171">**Figure 9-5**.</span></span> <span data-ttu-id="297dd-172">顯示 Web API 回應類型和可能 HTTP 狀態碼的 Swagger UI</span><span class="sxs-lookup"><span data-stu-id="297dd-172">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="297dd-173">您在上圖中可以看到一些範例值，它們是以 ViewModel 類型為基礎，加上可以傳回的可能 HTTP 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="297dd-173">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="297dd-174">其他資源</span><span class="sxs-lookup"><span data-stu-id="297dd-174">Additional resources</span></span>

-   <span data-ttu-id="297dd-175">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="297dd-175">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="297dd-176">**Julie Lerman。資料點 - Dapper、Entity Framework 與 Hybrid Apps (MSDN Mag. 文章)**</span><span class="sxs-lookup"><span data-stu-id="297dd-176">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="297dd-177">*https://msdn.microsoft.com/magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="297dd-177">*https://msdn.microsoft.com/magazine/mt703432.aspx*</span></span>

-   <span data-ttu-id="297dd-178">**使用 Swagger 的 ASP.NET Core Web API 說明頁面**</span><span class="sxs-lookup"><span data-stu-id="297dd-178">**ASP.NET Core Web API Help Pages using Swagger**</span></span>

    <span data-ttu-id="297dd-179">*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*</span><span class="sxs-lookup"><span data-stu-id="297dd-179">*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="297dd-180">[上一頁] (eshoponcontainers-cqrs-ddd-microservice.md) [下一頁] (ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="297dd-180">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
