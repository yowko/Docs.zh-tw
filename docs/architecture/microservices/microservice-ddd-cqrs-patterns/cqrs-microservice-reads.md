---
title: 在 CQRS 微服務中實作讀取/查詢
description: .NET 微服務：容器化 .NET 應用程式的架構 | 了解 CQRS 查詢端使用 Dapper 在 eShopOnContainers 訂購微服務上的實作。
ms.date: 10/08/2018
ms.openlocfilehash: f791546e2fc00e276ab55302802a5534465ace58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674335"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>在 CQRS 微服務中實作讀取/查詢

如需讀取/查詢，eShopOnContainers 參考應用程式的訂購微服務，會在 DDD 模型和交易區域之外實作查詢。 這項作業能夠完成，主要是因為查詢和交易的需求大不相同。 寫入的執行交易必須與網域邏輯相容。 另一方面，查詢具有等冪性，可從網域規則中隔離。

方法很簡單，如圖 7-3 所示。 API 介面是由 Web API 控制器實作，這些控制器會使用任何基礎結構，例如 Dapper 等微物件關聯式對應 (ORM)，並根據 UI 應用程式的需求傳回動態 ViewModel。

![對於簡化 CQRS 方法中的查詢端，最簡單的方法可以藉由使用例如 Dapper 等微型 ORM，傳回動態 ViewModel 查詢資料庫來實作。](./media/image3.png)

**圖 7-3**. CQRS 微服務中最簡單的查詢方法

這是最簡單可行的查詢方法。 查詢定義會查詢資料庫，並傳回每個查詢立即建立的動態 ViewModel。 因為查詢都具有等冪性，所以無論您執行查詢多少次，它們都不會變更資料。 因此，您不必受限於交易端使用的任何 DDD 模式，例如彙總及其他模式，這就是查詢與交易區域分開的原因。 您只要向資料庫查詢 UI 需要的資料，並傳回不需要在任何位置以靜態方式定義的動態 ViewModel (ViewModel 沒有類別)，SQL 陳述式本身除外。

因為這是簡單的方法，所以查詢端需要的程式碼 (例如使用 [Dapper](https://github.com/StackExchange/Dapper) 等微 ORM 的程式碼) 可在[相同的 Web API 專案](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)中實作。 如圖 7-4 所示。 查詢是在 eShopOnContainers 解決方案內的 **Ordering.API** 微服務專案中所定義。

![Ordering.API 專案的 [方案總管] 檢視，顯示應用程式 > 查詢資料夾。](./media/image4.png)

**圖 7-4**. eShopOnContainers 訂購微服務中的查詢

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>使用專為用戶端應用程式建立的 ViewModel，獨立於網域模型限制式之外

因為執行查詢是為取得用戶端應用程式所需要的資料，所以可以根據查詢傳回的資料，專為用戶端建立傳回型別。 這些模型或資料傳輸物件 (DTO)，稱為 ViewModel。

傳回的資料 (ViewModel) 可以是多個實體或資料庫多資料表的聯結資料結果，甚至可以是跨多個在交易區域網域模型中定義的彙總結果。 在此情況下，因為您要建立獨立於網域模型外的查詢，所以完全略過彙總界限和限制式，而且您可以隨意查詢可能需要的任何資料表和資料行。 此方法為開發人員建立或更新查詢提供了極大的彈性和生產力。

ViewModel 可以是在類別中定義的靜態類型。 或者，您可以根據執行的查詢以動態方式建立它們 (如同在訂購微服務中實作的一樣)，這對開發人員而言非常方便好用。

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>將 Dapper 用作微 ORM 以執行查詢 

您可以使用任何微 ORM、Entity Framework Core 或甚至純 ADO.NET 進行查詢。 在範例應用程式中，eShopOnContainers 的訂購微服務選取 Dapper 為熱門的微 ORM 範例。 它在執行一般 SQL 查詢時有絕佳的效能，因為它是非常輕簡的架構。 您可以使用 Dapper 撰寫能存取並聯結多份資料表的 SQL 查詢。

Dapper 是開放原始碼專案 (原創者為 Sam Saffron)，屬於 [Stack Overflow](https://stackoverflow.com/) (堆疊溢位) 的建置組塊。 若要使用 Dapper，您只需要透過 [Dapper NuGet 套件](https://www.nuget.org/packages/Dapper)安裝它即可，如下圖所示：

![在 VS [管理 NuGet 套件] 檢視中所檢視的 Dapper 套件。](./media/image4.1.png)

您也需要新增 using 陳述式，以便您的程式碼存取 Dapper 擴充方法。

當您在程式碼中使用 Dapper 時，您可直接使用 <xref:System.Data.SqlClient> 命名空間提供的 <xref:System.Data.SqlClient.SqlConnection> 類別。 透過 QueryAsync 方法和其他擴充 <xref:System.Data.SqlClient.SqlConnection> 類別的擴充方法，您可以直接且有效率的只執行查詢。

## <a name="dynamic-versus-static-viewmodels"></a>動態 ViewModel 與靜態 ViewModel

從伺服器端將 ViewModel 傳回用戶端應用程式時，您可以將這些 ViewModel 視為不同於您實體模型內部網域實體的 DTO (資料傳輸物件)，因為 ViewModel 是依用戶端應用程式需要的方式保留資料。 因此，在許多情況下，您可以彙總來自多個網域實體的資料，並根據用戶端應用程式需要該資料的方式精確撰寫 ViewModel。

您可以明確定義這些 ViewModel 或 DTO (為資料持有者類別)，如稍後之程式碼片段中示範的 `OrderSummary` 類別；或者可以只根據您查詢傳回的屬性，僅傳回動態 ViewModel 或動態 DTO 作為動態類型。

### <a name="viewmodel-as-dynamic-type"></a>ViewModel 作為動態類型

如下列程式碼所示，透過傳回在內部以查詢所傳回屬性為基礎的「動態」  類型，查詢可以直接傳回 `ViewModel`。 這表示要傳回的屬性子集是以查詢本身為基礎。 因此，如果您在查詢或聯結中新增新的資料行，該資料會以動態方式新增至傳回的 `ViewModel`。

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

重點是，透過使用動態類型，傳回的資料集合會以動態方式組合成 ViewModel。

**優點：** 這種方法可在您每次更新查詢的 SQL 句子時，減少修改靜態 ViewModel 類別的需求，讓這種設計方法在撰寫程式碼更為靈活，簡單快速地因應未來的變更。

**缺點：** 長期來看，動態類型對清晰度和服務與用戶端應用程式的相容性可能造成負面影響。 此外，如果使用動態類型，像 Swashbuckle 這類的中介軟體無法提供傳回型別的同級文件。

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel 作為預先定義的 DTO 類別

**優點：** 擁有靜態預先定義的 ViewModel 類別，例如以明確 DTO 類別為基礎的「合約」，絕對適合公用 API，但也適用於長期的微服務，即使只有相同的應用程式使用它們。

如要指定 Swagger 的回應類型，您需要使用明確的 DTO 類別作為傳回型別。 因此，預先定義的 DTO 類別可讓您提供更豐富的 Swagger 資訊。 這會在使用 API 時改善 API 文件和相容性。

**缺點：** 如前所述，更新程式碼時，它會採用更多步驟來更新 DTO 類別。

經驗提示  ：在 eShopOnContainers 訂購微服務實作的查詢中，我們就開始使用動態 ViewModel 進行開發，因為它在早期開發階段非常簡單靈活。 但是，一旦開發趨於穩定，我們會選擇重構 API 並使用靜態或預先定義的 DTO 取代 ViewModel，因為這樣可讓微服務取用者更清楚知道用作「合約」的明確 DTO 類型。

在下例中，您會看到查詢如何使用明確的 ViewModel DTO 類別：OrderSummary 類別，傳回資料。

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
            var result = await connection.QueryAsync<OrderSummary>(
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

#### <a name="describe-response-types-of-web-apis"></a>描述 Web API 的回應類型

取用 Web API 和微服務的開發人員最關心的是傳回的內容，尤其是回應類型和錯誤碼 (如果不是標準的話)。 這些是以 XML 註解和資料註釋進行處理。

Swagger UI 中沒有正確的文件，取用者就不清楚應該傳回哪些類型或可以傳回哪些 HTTP 代碼。 已藉由新增 <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType> 來修正該問題，因此 Swashbuckle 可以產生 API 傳回模型和值的更多相關資訊，如下列程式碼所示：

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
            var userid = _identityService.GetUserIdentity();
            var orders = await _orderQueries
                .GetOrdersFromUserAsync(Guid.Parse(userid));
            return Ok(orders);
        }
    }
}
```

不過，`ProducesResponseType` 屬性不能用作動態類型，卻需要使用像 `OrderSummary` ViewModel DTO 的明確類型，如下列範例所示：

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

這是就長期而言，明確的傳回型別優於動態類型的另一個原因。 使用 `ProducesResponseType` 屬性時，您也可以可能的 HTTP 錯誤/程式碼來指定預期結果的內容，例如 200、400 等等。

在下圖中，您會看到 Swagger UI 如何顯示 ResponseType 資訊。

![訂購 API 的 Swagger UI 頁面瀏覽器檢視。](./media/image5.png)

**圖 7-5**. 顯示 Web API 回應類型和可能 HTTP 狀態碼的 Swagger UI

您在上圖中可以看到一些範例值，它們是以 ViewModel 類型為基礎，加上可以傳回的可能 HTTP 狀態碼。

## <a name="additional-resources"></a>其他資源

- **Dapper** \
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman。資料點 - Dapper、Entity Framework 與 Hybrid Apps (MSDN Mag. 文章)**  \
  <https://msdn.microsoft.com/magazine/mt703432.aspx>

- **使用 Swagger 的 ASP.NET Core Web API 說明頁面** \
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[上一頁](eshoponcontainers-cqrs-ddd-microservice.md)
>[下一頁](ddd-oriented-microservice.md)
