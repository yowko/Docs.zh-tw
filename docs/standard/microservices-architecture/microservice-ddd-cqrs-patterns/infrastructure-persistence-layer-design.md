---
title: "設計基礎結構的持續性層級"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |設計基礎結構的持續性層級"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ce0f1d608eed909a7707f3c580afc5253f3eef06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-infrastructure-persistence-layer"></a>設計基礎結構的持續性層級

資料持續性元件提供裝載界限內的微服務 （也就是微服務 」 資料庫） 資料的存取權。 它們包含的元件，例如儲存機制的實際實作和[工作單位](http://martinfowler.com/eaaCatalog/unitOfWork.html)類別，如自訂 EF DBContexts。

## <a name="the-repository-pattern"></a>儲存機制模式

儲存機制是類別或元件的封裝來存取資料來源所需的邏輯。 它們集中化通用資料存取功能，提供更佳的可維護性，並減少基礎結構或技術，用來存取資料庫，從網域模型層。 如果您使用 Entity Framework 像 ORM 時，必須實作的程式碼已經過簡化，這點受惠 LINQ 和強型別。 這可讓您將焦點放在資料持續性邏輯上，而不是資料存取配管。

儲存機制模式會完善記載使用這種使用資料來源。 活頁簿中[企業應用程式架構模式](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/)，Martin Fowler 描述儲存機制，如下所示：

儲存機制會執行之間的媒介，網域模型圖層與資料對應到記憶體中的網域物件的一組類似的方式做的工作。 用戶端物件以宣告方式建立查詢，並將它們傳送至儲存機制的答案。 就概念而言，儲存機制封裝一組儲存在資料庫和作業可執行的頁面，提供一種方式較接近保存層中的物件。 儲存機制中，此外，支援分隔，清楚地與一個方向工作網域 」 和 「 資料配置之間的相依性或對應的目的。

### <a name="define-one-repository-per-aggregate"></a>定義彙總每一個儲存機制

您應針對每個彙總或彙總根，建立一個儲存機制類別。 在微服務，根據網域導向設計模式，您應該使用以更新資料庫的通道唯一應該儲存機制。 這是因為它們具有一對一的關聯性的彙總根，控制彙總的非變異值與交易一致性。 還是可以查詢資料庫，透過其他通道 （因為您可以執行下列 CQRS 方法），因為查詢不會變更資料庫的狀態。 不過，交易式區域 — 更新 — 永遠必須控制儲存機制和彙總的根目錄。

基本上，儲存機制可讓您填入來自網域實體的表單中的資料庫的記憶體中的資料。 實體都在記憶體中之後，它們可以變更，然後回到交易透過資料庫保存。

如前文所述，如果您使用 CQS/CQRS 架構模式，從網域模型，使用 Dapper 簡單的 SQL 陳述式所執行的側邊查詢來執行初始查詢。 這個方法是較具彈性的儲存機制，因此您可以查詢聯結任何資料表需要而且這些查詢不受限於的規則從彙總更多。 該資料將會移至展示層或用戶端應用程式。

如果使用者對進行變更，更新的資料將來自用戶端應用程式或展示層到應用程式層 （例如 Web API 服務）。 當您收到的命令 （資料） 是命令處理常式中時，您可以使用儲存機制取得您想要從資料庫更新的資料。 您在記憶體中已使用更新的命令，傳遞的資訊，然後加入或更新交易透過資料庫中的資料 （網域實體）。

我們必須強調一次，應該對於每個彙總根，定義只能有一個儲存機制，為顯示圖 9-17。 若要達到以維護交易一致性彙總中的所有物件之間的彙總根目標，您應該永遠不會在資料庫中建立每個資料表的儲存機制。

![](./media/image18.png)

**圖 9-17**。 儲存機制、 彙總，以及資料庫資料表之間的關聯性

### <a name="enforcing-one-aggregate-root-per-repository"></a>強制執行一個彙總根，每個儲存機制

它可以是實作您儲存機制的設計方式，它會強制執行彙總根只應該有儲存機制的規則有價值。 您可以建立會限制它以確定它們有 IAggregateRoot 標記介面使用的實體類型的泛型或基底的儲存機制類型。

因此，在基礎結構層級實作每個儲存機制類別會實作自己的合約或介面，如下列程式碼所示：

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

每個特定的儲存機制介面會實作泛型 IRepository 介面：

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

不過，強制執行慣例使程式碼更好的方法，每個儲存機制應該與相關的單一彙總就是實作泛型的儲存機制類型，所以明確使用儲存機制為目標的特定彙總。 可以輕鬆地完成藉由實作該泛型 IRepository 基底介面中，如下列程式碼所示：

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>儲存機制模式可讓您更輕鬆地測試您的應用程式邏輯

儲存機制模式可讓您輕鬆地測試您的應用程式與單元測試。 請記住，單元測試只測試您的程式碼，不是基礎結構，因此儲存機制的抽象概念更輕鬆地達成這個目標。

如前一節中所述，建議您定義，並放置儲存機制介面網域模型層中讓應用程式層 （比方說，您 Web 應用程式開發介面微服務） 不會依賴直接基礎結構層級具有實作實際的儲存機制類別。 如此一來，並使用您的 Web API 控制器中的相依性插入，您可以實作模擬儲存機制從資料庫傳回假的資料，而非資料。 解除解合的方式可讓您建立，並執行的單元測試，可以測試應用程式的邏輯，而不需要連線到資料庫。

資料庫的連線可能會失敗，並更重要的是，對資料庫執行數百項測試錯誤原因有兩個。 首先，因為大量的測試可能需要大量時間。 第二，可能會變更資料庫記錄，並影響您的測試結果，因此，它們可能不一致。 對資料庫的測試並不是單元測試整合測試。 您應該有許多的單元測試執行快速，但較少的整合測試針對資料庫。

單元測試的重要性分離，根據您的邏輯作業網域中的實體記憶體。 它會假設此儲存機制類別提供的。 一旦您的邏輯修改網域實體時，它會假設此儲存機制類別將能正確地儲存。 此處的重點是要建立單元測試對您的網域模型和其網域邏輯。 彙總的根目錄是 DDD 中的主要的一致性。

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>儲存機制模式與舊版的資料存取類別 （DAL 類別） 模式之間的差異

資料存取物件直接執行資料存取與持續性作業，對儲存體。 儲存機制標記，與您想要執行的工作物件 （如同在 EF 使用 DbContext 時)，但這些更新的一個單位的記憶體中作業的資料不會立即執行。

工作的單位被指視為單一交易，包括多項插入、 更新或刪除作業。 簡單來說，這表示，特定的使用者動作 （例如，在網站上註冊），所有插入、 更新和刪除交易都處理在單一交易中。 這是更有效率的 chattier 方式處理多個資料庫交易。

您的程式碼應用程式層命令它時，將會在單一動作中稍後執行這些多個持續性作業。 將記憶體中的變更套用至實際的資料庫儲存體的決策通常根據[工作單位模式](http://martinfowler.com/eaaCatalog/unitOfWork.html)。 在 EF，工作單元模式會實作為 DBContext。

在許多情況下，此模式或套用對儲存體作業的方式可以提高應用程式效能，並降低不一致的可能性。 此外，它會降低交易封鎖資料庫的資料表，因為所有預期的作業都會認可為單一交易的一部分。 這是相較於執行許多對資料庫的隔離的作業更有效率。 因此，所選的 ORM 可以最佳化對資料庫執行分組為相同的交易，而不是許多小型和個別的交易執行中的數個更新動作。

### <a name="repositories-should-not-be-mandatory"></a>儲存機制不是強制性

由於稍早所提的原因很有用的自訂儲存機制，而這是在 eShopOnContainers 順序的微服務的方法。 不過，它不是實作 DDD 設計中，或甚至一般的.NET 中的程式開發基本模式。

比方說，Jimmy Bogard，本指南中，為提供直接的意見反應時說下列：

這可能會是大我的意見反應。 我實際上風扇的儲存機制中，主要是因為它們隱藏基礎持續性機制的重要詳細資料。 它的原因在哪裡尋求 MediatR 的命令，太。 我可以使用完整的持續性的圖層，並將所有網域行為都推送至我的彙總根。 通常不希望我的儲存機制的模擬 – 仍然需要的整合測試與實際的動作。 將 CQRS，目的在於我們真的沒有任何多具有儲存機制的需求。

我們有幫助，儲存機制，但我們了解它們並不重要的您 DDD，彙總模式和豐富的網域模型的方式。 因此，要使用儲存機制模式，如 調整。

#### <a name="additional-resources"></a>其他資源

##### <a name="the-repository-pattern"></a>儲存機制模式

-   **愛德華 Hieatt 和 Rob 我。儲存機制模式。** 
     [ *http://martinfowler.com/eaaCatalog/repository.html*](http://martinfowler.com/eaaCatalog/repository.html)

-   **儲存機制模式**
    [*https://msdn.microsoft.com/en-us/library/ff649690.aspx*](https://msdn.microsoft.com/en-us/library/ff649690.aspx)

-   **儲存機制模式： 資料持續性抽象**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)

-   **Eric Evans：網域導向設計： 解決核心軟體的複雜度。** （書籍; 儲存機制模式的討論包括）[ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

##### <a name="unit-of-work-pattern"></a>工作模式的單位

-   **Martin Fowler：工作模式的單位。** 
     [ *http://martinfowler.com/eaaCatalog/unitOfWork.html*](http://martinfowler.com/eaaCatalog/unitOfWork.html)

<!-- -->

-   **ASP.NET MVC 應用程式中實作的儲存機制和工作模式單位**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)


>[!div class="step-by-step"]
[上一個](網域-事件-設計-implementation.md) [下一步] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)
