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
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a>實作讀取/查詢中 CQRS 微服務

讀取/查詢，從 eShopOnContainers 參考應用程式排序的微服務會實作 DDD 模型和交易式區域之外另行查詢。 這項作業完成，主要是因為查詢和交易的需求會大幅不同。 寫入執行必須與網域邏輯相容的交易。 查詢，相反地，具有等冪性，而且可以從定義域規則隔離。

如圖 9-3 所示，此方法很簡單。 API 介面是由 Web API 控制器使用任何基礎結構 （例如微 ORM 例如 Dapper），並傳回根據 UI 應用程式的需求動態 ViewModels 實作。

![](./media/image3.png)

**圖 9-3**。 CQRS 微服務中的查詢最簡單的方法

這是最簡單的查詢可能的方法。 查詢定義查詢資料庫，並傳回每個查詢，立即建立動態 ViewModel。 查詢都具有等冪性，因為它們不會變更執行查詢多少次的資料。 因此，您不需要使用中交易的側邊，彙總與其他模式，例如任何 DDD 模式，以限制，這就是為什麼查詢會從交易式區域分隔。 只要查詢資料庫中的 UI 所需要的資料，並傳回不需要以靜態方式是動態 ViewModel 隨處 （沒有 ViewModels 類別） 除了中定義的 SQL 陳述式本身。

由於這是一個簡單的方法時，程式碼所需的查詢端 (例如程式碼使用 ORM 喜歡微[Dapper](https://github.com/StackExchange/Dapper)) 可以實作[內相同的 Web API 專案](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)。 圖 9-4 顯示這點。 查詢中所定義**Ordering.API** eShopOnContainers 方案內的微服務專案。

![](./media/image4.png)

**圖 9-4**。 在 eShopOnContainers 訂購微服務中的查詢

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>使用 ViewModels 特別設定為用戶端應用程式，獨立於網域模型條件約束

取得用戶端應用程式所需的資料執行查詢，因為傳回的型別可以特別針對進行用戶端，根據查詢所傳回的資料。 這些模型或資料傳輸物件 (Dto)，稱為 ViewModels。

傳回的資料 (ViewModel) 可以是聯結來自多個實體或資料表的資料，在資料庫中，或甚至可跨多個交易式區域的網域模型中定義的彙總的結果。 在此情況下，您要建立獨立網域模型的查詢，因為彙總界限和條件約束完全略過，而且可用來查詢任何資料表和您可能需要的資料行。 此方法提供很大的彈性和產能，為開發人員建立或更新的查詢。

ViewModels 可以是靜態類別中定義的型別。 或者，您可以在建立以動態方式根據查詢執行 （因為實作在排序的微服務），這是非常靈活的開發人員。

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a>使用 Dapper 微 ORM 為執行查詢 

您可以使用任何微 ORM、 Entity Framework 的核心或甚至純 ADO.NET 進行查詢。 在範例應用程式中，我們選取受歡迎的微 ORM 的理想範例為 eShopOnContainers 中順序的微服務 Dapper。 執行一般的 SQL 查詢時絕佳的效能，因為它是一個非常輕微的架構。 您可以使用 Dapper，來撰寫 SQL 查詢，可以存取並加入多個資料表。

Dapper 是開放原始碼專案 （原始 Sam Saffron 所建立），而且屬於中使用的建置組塊[堆疊溢位](https://stackoverflow.com/)。 若要使用 Dapper，您只需要安裝它透過[Dapper NuGet 封裝](https://www.nuget.org/packages/Dapper)，如下圖所示。

![](./media/image5.png)

您也必須加入 using 陳述式，使您的程式碼可存取的 Dapper 擴充方法。

當您在程式碼中使用 Dapper 時，您會直接使用在 System.Data.SqlClient 命名空間中的 SqlClient 類別。 透過 QueryAsync 方法和其他擴充 SqlClient 類別的擴充方法，您只可以直接且高效能的方式執行查詢。

## <a name="dynamic-and-static-viewmodels"></a>動態和靜態 ViewModels

排序的微服務的下列程式碼所示，大部分的查詢所傳回的 ViewModels 會實作為*動態*。 這表示要傳回的屬性子集為根據查詢本身。 如果您加入新的資料行的查詢或聯結時，該資料是以動態方式加入傳回 ViewModel。 這種方法可減少需要修改查詢，以回應基礎資料模型，讓這種設計方式，更有彈性且容許未來變更的更新。

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

很重要的一點是，使用動態類型，傳回的集合的資料將以動態方式組合成 ViewModel。

對於大部分查詢，您不需要預先定義 DTO 或 ViewModel 類別，讓其編碼簡單且更有生產力。 不過，您可以預先定義 ViewModels （例如，預先定義的 Dto) 如果您想要以更具限制性的定義，做為合約有 ViewModels。

#### <a name="additional-resources"></a>其他資源

-   **Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

-   **Julie Lerman。資料點-Dapper、 Entity Framework 和混合式應用程式 （MSDN Mag.文章）**

    *https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*


>[!div class="step-by-step"]
[上一個](eshoponcontainers-cqrs-ddd-microservice.md) [下一步] (ddd-導向-microservice.md)
