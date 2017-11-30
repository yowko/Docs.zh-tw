---
title: "設計的微服務網域模型"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |設計的微服務網域模型"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 455a2c5a39fb9b765b557610ab108f8c75882dbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="designing-a-microservice-domain-model"></a>設計的微服務網域模型

*定義一個豐富的網域模型，針對每個商務微服務 」 或 「 繫結的內容*

您的目標是建立單一的一致網域模型，針對每個商務微服務 」 或 「 繫結的內容 (BC)。 記住，不過，BC 或商務微服務有時無法組成數個共用單一網域模型的實體服務。 網域模型必須擷取規則、 行為、 商務語言和單一繫結的內容或它所代表的商務微服務的條件約束。

## <a name="the-domain-entity-pattern"></a>網域實體模式

實體代表網域物件，並由其身分識別、 提供續航力和經過一段時間，持續性並不只是由包含這些屬性主要是定義。 因為 Eric Evans 說，「 主要定義其識別的物件被呼叫實體 」。 實體是在網域模型中，非常重要，因為它是以模型的基底。 因此，您應該識別和它們仔細的設計。

*實體的識別身分都不得跨越多個 microservices 或繫結的內容。*

在相同識別 （但不相同的實體） 可以跨多個繫結的內容或 microservices 建立模型。 不過，並不意味著，在多個繫結的內容中實作相同的實體，具有相同的屬性和邏輯。 相反地，每個繫結的內容中的實體限制其屬性和行為，以必要的繫結內容的網域中。

比方說，買方實體可能會有大部分的設定檔或識別微服務，包括身分識別的使用者實體中定義的個人的屬性。 但是，買方中的實體順序的微服務可能具有較少的屬性，只有特定買方資料與訂單程序。 每個微服務的內容或繫結的內容會影響其網域模型。

*網域實體必須實作除了實作資料屬性的行為*

網域中的實體 DDD 必須實作網域邏輯或實體資料 （在記憶體中存取的物件） 的相關行為。 例如，order 實體類別的一部分必須商務邏輯和實作為工作，例如新增訂單項目、 資料驗證及總計算的方法的作業。 實體的方法負責的非變異值和規則的實體，而不需要這些分散應用程式層的規則。

圖 9-8 顯示實作不僅資料屬性，但作業或方法相關的網域邏輯使用網域實體。

![](./media/image9.png)

**圖 9-8**。 實作資料加上行為網域實體設計的範例

當然，有時您可以有不會為實體類別的一部分實作的任何邏輯實體。 這種情況中彙總內的子實體子實體沒有任何特殊邏輯，因為大部分的邏輯定義彙總的根目錄中。 如果您有複雜的微服務具有大量網域實體中而不是服務類別中實作的邏輯，您無法落入 anemic 網域模型下, 一節所述。

### <a name="rich-domain-model-versus-anemic-domain-model"></a>與 anemic 網域模型的豐富網域模型

他的文章中[AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html)，Martin Fowler 描述 anemic 網域模型這種方式：

Anemic 網域模型的基本徵兆是乍看之下它看起來像真正的動作。 沒有物件、 許多為名網域空間中的名詞和這些物件來連接具有豐富的關聯性，則為 true 的網域模型具有的結構。 捕捉來自您查看行為，和您了解這些物件上沒有任何難以行為使其稍微超過的 getter 和 setter 包時。

當然，當您使用 anemic 網域模型，這些資料模型中要使用的一組服務物件 (傳統上具名*： 商務圖層*) 這會擷取所有的網域或商務邏輯。 商業層位於資料模型之上，並使用只做為資料的資料模型。

Anemic 網域模型是只程序樣式設計。 Anemic 實體物件不是真正的物件，因為它們缺少行為 （方法）。 它們只會保存資料的屬性，因此它不是物件導向設計。 透過將所有的行為出服務物件 （商務層） 放入您基本上得到[之程式碼](https://en.wikipedia.org/wiki/Spaghetti_code)或[交易指令碼](https://martinfowler.com/eaaCatalog/transactionScript.html)，因此您遺失優點，並網域模型提供。

不論，如果您的微服務或繫結的內容是非常簡單 （服務 CRUD） anemic 網域中的模型只是資料屬性與實體物件的形式可能夠好，而且可能無法值得實作更複雜的 DDD 模式。 在此情況下，這是簡單的持續性模式，因為您只使用資料基於 CRUD 刻意建立實體。

這是為什麼 microservices 架構是完美的多重架構的方法，根據每個繫結的內容。 比方說，在 eShopOnContainers，排序的微服務實作 DDD 模式，但目錄微服務，這是一個簡單的 CRUD 服務，並不會。

有些人說出 anemic 網域模型是反向的模式。 它其實取決於您要實作。 如果您要建立微服務是簡單足夠 （例如，CRUD 服務），下列 anemic 網域模型不是反向的模式。 不過，如果您需要處理具有大量不斷改變的商務規則的微服務網域的複雜性，anemic 網域模型可能反面模式或繫結內容的微服務。 在此情況下，將它設計為 rich 與實體，其中包含資料，以及行為，以及實作其他 DDD 模式 （彙總、 值的物件等） 的模型可能會有很大的優點，長期成功的微服務。

#### <a name="additional-resources"></a>其他資源

-   **DevIQ。網域實體**
    [*http://deviq.com/entity/*](http://deviq.com/entity/)

-   **Martin Fowler：網域模型**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)

-   **Martin Fowler：Anemic 網域模型**

    <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>值物件模式

Eric Evans 已經提過，「 許多物件沒有概念的身分識別。 這些物件描述特定特性的事。 」

實體需要身分識別，但系統不會有許多物件類似的值物件的模式。 值物件是具有任何描述網域外觀的概念身分識別的物件。 這些是您具現化來表示只有您有關暫時的設計元素的物件。 您很重視*什麼*它們，不是*人員*它們。 範例包含數字和字串，但也可能是較高層級的概念，像是群組的屬性。

項目中的微服務的實體不可能是另一個的微服務中的實體，因為在第二個案例中，繫結的內容可能會有不同的意義。 例如，電子商務應用程式中的位址可能沒有身分識別，因為它可能只代表客戶的個人或公司的設定檔的屬性群組。 在此情況下，地址應該會歸類為值物件。 不過，接上電源公用程式的公司應用程式中，可能是很重要的商務網域的客戶地址。 因此，位址必須含有身分識別，因此帳務系統可以直接連接到位址。 在此情況下，地址應該會分類為網域實體。

具有名稱和姓氏的人員通常是一個實體，因為個人身分識別，即使另一組值與一致的名稱和姓氏，例如，如果這些名稱也是指不同的人。

值物件難以管理關聯式資料庫和 Orm 像 EF，而在文件導向容易實作，並使用的資料庫。

#### <a name="additional-resources"></a>其他資源

-   **Martin Fowler：值物件模式**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **值物件**
    [*http://deviq.com/value-object/*](http://deviq.com/value-object/)

-   **值物件中有如開發**
    [*https://leanpub.com/tdd-ebook/read\#leanpub 自動值的物件*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

-   **Eric Evans：網域導向設計： 解決核心軟體的複雜度。** （書籍; 包含的值物件的討論）[ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="the-aggregate-pattern"></a>彙總模式

網域模型包含不同的資料實體與可控制重要區域的功能，例如順序完成或清查處理程序的叢集。 更精細的 DDD 單位是彙總，其中描述叢集或群組的實體和行為可視為凝聚的單元。

您通常會定義您所需要的交易為基礎的彙總。 典型的範例是也包含一份訂單項目順序。 訂單項目通常會為實體。 但是會有子實體內的順序彙總，也會包含 「 訂單 」 實體為其根目錄的實體，通常稱為彙總的根。

識別彙總很困難。 彙總在一起，必須維持一致的物件群組但不能只需要挑選一整組物件，並加上標籤它們彙總。 您必須與網域概念開頭，並考慮與該概念相關的最常見交易中使用的實體。 處於交易一致狀態需要這些實體是什麼 form 彙總。 思考交易操作可能是最佳的方式來識別彙總。

### <a name="the-aggregate-root-or-root-entity-pattern"></a>彙總根或根實體模式

彙總由至少一個實體所組成： 彙總根，也稱為根實體或主要 ientity。 此外，它可以有多個子實體和值的物件，包含的所有實體及物件一起工作來實作所需的行為與交易。

彙總根的目的是確保彙總; 一致性它應該是唯一的進入點的更新彙總透過方法或作業的彙總根類別。 您應該變更彙總根僅透過彙總內的實體。 它是在彙總一致性守護者，所有的非變異項目和您可能需要遵守您彙總中的一致性規則列入考量。 如果您是獨立變更子實體或值物件，無法確保彙總根，，彙總就是處於有效狀態。 將與鬆散的階段與資料表類似。 維護的一致性是彙總根的主要用途。

在圖 9-9，您可以查看範例彙總，例如買方彙總，其中包含單一實體 （彙總根買方）。 順序彙總包含多個實體和值的物件。

![](./media/image10.png)

**圖 9 9**。 使用多個彙總的範例或單一實體

請注意買方彙總可能有其他子實體，根據您的網域中順序的微服務 eShopOnContainers 參考應用程式中一樣。 圖 9 9 只將說明其中買方的單一實體，例如彙總，其中包含只有彙總根的情況。

為了維持分離的彙總，並讓它們之間有清楚的界限，最佳作法是在 DDD 網域模型中不允許直接瀏覽不同的彙總，以及只取得外部索引鍵 (FK) 欄位中，以實作[排序微服務網域模型](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)eShopOnContainers 中。 「 訂單 」 實體只有 FK 欄位買方，但不 EF 核心導覽屬性，如下列程式碼所示：

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
}
```

識別及使用彙總需要的研究和經驗。 如需詳細資訊，請參閱下表的其他資源。

#### <a name="additional-resources"></a>其他資源

-   **Vaughn Vernon：有效的彙總設計的第一部份： 模型的單一彙總**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_社群\_短文\_彙總\_一部分\_1.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)

-   **Vaughn Vernon：有效彙總設計-第 2 部分： 進行彙總可共同運作**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf>*

-   **Vaughn Vernon：有效彙總設計-第 3 篇： 取得深入了解透過探索**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf>*

-   **Sergey Grybniak。DDD 戰術設計模式**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)

-   **Chris Richardson。開發使用彙總的交易式 Microservices**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)

-   **DevIQ。彙總模式**
    [*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)


>[!div class="step-by-step"]
[上一個](ddd-導向-microservice.md) [下一步] (net-核心-微服務-網域-model.md)
