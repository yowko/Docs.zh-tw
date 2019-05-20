---
title: 設計基礎結構持續性層
description: .NET 微服務：容器化 .NET 應用程式的架構 | 探索基礎結構持續性層設計中的存放庫模式。
ms.date: 10/08/2018
ms.openlocfilehash: 76f545403a1b595ce7a541a96d212b9406d89c10
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644585"
---
# <a name="design-the-infrastructure-persistence-layer"></a>設計基礎結構持續性層

資料持續性元件可讓您存取裝載於微服務界限 (也就是微服務的資料庫) 內的資料。 它們包含存放庫和[工作單位](https://martinfowler.com/eaaCatalog/unitOfWork.html)類別 (例如自訂 Entity Framework (EF) <xref:Microsoft.EntityFrameworkCore.DbContext> 物件) 等元件的實際實作。 EF DbContext 會同時實作存放庫和工作單位模式。

## <a name="the-repository-pattern"></a>儲存機制模式

儲存機制是封裝存取資料來源所需邏輯的類別或元件。 它們會集中管理常見的資料存取功能，以提供更佳的可維護性，並將用來存取資料庫與用來存取領域模型層的基礎結構或技術分離。 如果您使用類似 Entity Framework 的物件關聯式對應程式 (ORM)，多虧有 LINQ 和強型別，必須實作的程式碼會經過簡化。 這可讓您專注於資料持續性邏輯，而不是資料存取連接。

儲存機制模式是使用資料來源之妥善記載的方法。 在 [Patterns of Enterprise Application Architecture](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/) 一書中，Martin Fowler 對儲存機制有以下描述：

> 儲存機制會在領域模型層與資料對應之間執行中繼工作，其作用類似於記憶體內部的一組領域物件。 用戶端物件以宣告方式建立查詢，並將它們傳送至儲存機制以尋求解答。 就概念而言，儲存機制會封裝一組儲存在資料庫中的物件，以及可在其上執行的作業，來提供接近持續性層的方式。 儲存機制也支援清楚且一個方向的分離用途，以及工作領域與資料配置或對應之間的一致性。

### <a name="define-one-repository-per-aggregate"></a>每個彙總定義一個儲存機制

您應針對每個彙總或彙總根，建立一個儲存機制類別。 在以領域驅動設計 (DDD) 模式為基礎的微服務中，您唯一可用來更新資料庫的通道應該是存放庫。 這是因為它們具有一對一關聯性和彙總根，可控制彙總的不變式和交易一致性。 您還是可以透過其他通道來查詢資料庫 (例如您可以遵循 CQRS 方法來這樣做)，因為查詢不會變更資料庫的狀態。 不過，交易區域 (也就是更新) 必須一律受到存放庫和彙總根的控制。

基本上，儲存機制可讓您將來自資料庫的資料，以領域實體形式填入記憶體。 一旦實體在記憶體中，就可以變更，然後透過交易保存回到資料庫。

如稍早所述，如果您使用 CQS/CQRS 架構模式，來自領域模型端的查詢 (由使用 Dapper 的簡單 SQL 陳述式來執行) 會執行初始查詢。 此方法比存放庫更有彈性，因為您可以查詢並聯結任何需要的資料表，而且這些查詢不會受到彙總規則的限制。 該資料會移至展示層或用戶端應用程式。

如果使用者進行變更，資料會從用戶端應用程式或展示層更新至應用程式層 (例如 Web API 服務)。 當您在命令處理常式中收到命令時，您可以使用存放庫從資料庫取得您要更新的資料。 您在記憶體中將它更新為使用命令所傳遞的資料，然後透過交易在資料庫中新增或更新資料 (領域實體)。

在這裡要特別再次強調的是，您應該只會針對每個彙總根定義一個存放庫，如圖 7-17 所示。 若要達到在彙總內所有物件之間維持交易一致性的彙總根目標，請絕對不要針對資料庫中的每個資料表建立儲存機制。

![網域層和基礎結構層之間的關聯性：購買者彙總相依於 IBuyerRepository，而訂單彙總相依於 IOrderRepository 介面，這些介面會在基礎結構層中由對應的存放庫實作，這些存放庫不僅相依於 UnitOfWork，也在該處實作，用來存取資料層中的資料表。](./media/image18.png)

**圖 7-17**。 儲存機制、彙總和資料庫資料表之間的關聯性

### <a name="enforce-one-aggregate-root-per-repository"></a>每個存放庫強制執行一個彙總根

以此方式來實作您的儲存機制設計可能很重要，因為它會強制執行規則，只允許彙總根有儲存機制。 您可以建立泛型或基底存放庫類型來限制可搭配使用的實體類型，確保這些實體具有 `IAggregateRoot` 標記介面。

因此，在基礎結構層實作的每個儲存機制類別會實作自己的合約或介面，如下列程式碼所示：

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

每個特定儲存機制介面會實作泛型 IRepository 介面：

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

不過，若要讓程式碼強制執行每個存放庫與單一彙總關聯的慣例，建議實作泛型存放庫類型。 如此可明確指出您使用的存放庫是以特定彙總為目標。 這可透過實作泛型 `IRepository` 基底介面來輕鬆完成，如下列程式碼所示：

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>儲存機制模式可讓您更輕鬆地測試應用程式邏輯

儲存機制模式可讓您使用單元測試輕鬆地測試應用程式。 請記住，單元測試只會測試您的程式碼，不會測試基礎結構，因此儲存機制抽象概念可讓您更輕鬆地達成該目標。

如稍早一節所述，建議您定義存放庫介面並將它放在領域模型層中，讓應用程式層 (例如您的 Web API 微服務) 不會直接相依於您實作實際存放庫類別的基礎結構層。 藉由這樣做，以及在您的 Web API 的控制器中使用相依性插入，您就可以實作模擬儲存機制來傳回假的資料，而不是資料庫中的資料。 此低結合方法可讓您建立並執行單元測試，只著重於您應用程式的邏輯，而不需要連接到資料庫。

資料庫連接可能會失敗，而且更重要的是，對資料庫執行數百個測試不適當的原因有兩個。 首先，因為測試數目很大，所以可能需要很長的時間。 其次，資料庫記錄可能會變更並影響您的測試結果，因此結果可能會不一致。 對資料庫進行的測試不是單元測試，而是整合測試。 您應該會有許多執行速度很快的單元測試，但對資料庫的整合測試則較少。

從單元測試的關注點分離觀點來看，您的邏輯會在記憶體內部的領域實體上運作。 它假設儲存機制類別已達到這些目的。 一旦您的邏輯修改領域實體，它會假設儲存機制類別將會正確地儲存這些實體。 此處的重點是對領域模型及其領域邏輯建立單元測試。 彙總根是 DDD 中的主要一致性界限。

在 eShopOnContainers 中實作的存放庫依賴 EF Core 的 DbContext 使用其變更追蹤程式實作存放庫和工作單位模式，因此它們不會複製這項功能。

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>儲存機制模式與舊版資料存取類別 (DAL 類別) 模式之間的差異

資料存取物件會直接對儲存體執行資料存取和持續性作業。 存放庫會以您要在工作單位物件的記憶體中執行的作業來標示資料 (如同使用 <xref:Microsoft.EntityFrameworkCore.DbContext> 類別時的 EF)，但不會立即對資料庫執行這些更新。

工作單位是指涉及多項插入、更新或刪除作業的單一交易。 簡單來說，這表示針對特定使用者動作 (例如網站註冊)，所有插入、更新和刪除作業都會在單一交易中處理。 比起更耗時地處理多個資料庫交易，這樣做會更有效率。

稍後在單一動作中，當來自應用程式層的程式碼命令時，就會執行多個持續性作業。 將記憶體內部變更套用至實際資料庫儲存體的決策通常會採用[工作單位模式](https://martinfowler.com/eaaCatalog/unitOfWork.html)。 在 EF 中，工作單位模式會實作為 <xref:Microsoft.EntityFrameworkCore.DbContext>。

在許多情況下，此模式或對儲存體套用作業的方式可提高應用程式效能，並降低不一致的可能性。 它也會降低資料庫資料表中的交易封鎖，因為所有預期的作業都會認可為單一交易的一部分。 相較於對資料庫執行許多隔離作業，這樣做會更有效率。 因此，選取的 ORM 能夠藉由群組相同交易內的數個更新動作來最佳化對資料庫的執行，這與許多小型且個別的交易執行正好相反。

### <a name="repositories-shouldnt-be-mandatory"></a>存放庫不應該是強制的

自訂儲存機制很有用 (原因如稍早所述)，而且是 eShopOnContainers 中訂購微服務的方法。 不過，它不是在 DDD 設計或甚至是一般 .NET 程式開發中實作的基本模式。

例如，當 Jimmy Bogard 對本指南提供直接意見反應時表示：

> 這可能是我最強烈的意見反應。 我其實不是儲存機制的愛好者，主要是因為儲存機制會隱藏基礎持續性機制的重要詳細資料。 這也是為什麼我使用 MediatR 命令的原因。 我可以利用持續性層的完整強大功能，並將所有領域行為推送至我的彙總根。 我通常不需要模擬儲存機制 (我仍需要使用真實內容進行整合測試)。 移至 CQRS 表示我們實際上不再需要儲存機制。

存放庫可能很有用，但它們對您的 DDD 設計並不如彙總模式和豐富領域模型同樣重要。 因此，是否使用儲存機制模式完全取決於您。 無論如何，每當您使用 EF Core 時，都會使用存放庫模式，但在此情況下，存放庫會涵蓋整個微服務或限定內容。

## <a name="additional-resources"></a>其他資源

### <a name="repository-pattern"></a>存放庫模式

- **The Repository pattern** \ (存放庫模式)
  <https://deviq.com/repository-pattern/>

- **Edward Hieatt 和 Rob Mee：Repository pattern.** (存放庫模式)。 \
  <https://martinfowler.com/eaaCatalog/repository.html>

- **The Repository pattern** \ (存放庫模式)
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans：網域驅動設計：解決軟體核心的複雜度。** (書籍，包括存放庫模式的討論) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>工作單位模式

- **Martin Fowler：Unit of Work pattern (工作單位模式)。** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **在 ASP.NET MVC 應用程式中實作存放庫與工作單位模式** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[上一頁](domain-events-design-implementation.md)
>[下一頁](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
