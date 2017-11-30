---
title: "設計 DDD 導向的微服務"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |設計 DDD 導向的微服務"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: df45441089fd59d5e0e52b4bcec409adcc11fb71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="designing-a-ddd-oriented-microservice"></a>設計 DDD 導向的微服務

網域導向設計 (DDD) 倡導人士等商務的使用案例相關的事實為基礎的模型。 在建立應用程式的內容中，DDD 交談的問題為網域中。 它會描述繫結內容當做獨立的問題區域 （每個繫結的內容會將微服務相互關聯），並強調常用的語言，討論這些問題。 另提出許多技術概念和模式，如同網域實體具有豐富的模型 (沒有[anemic 網域模型](https://martinfowler.com/bliki/AnemicDomainModel.html))，值的物件、 彙總及彙總根 （或根實體） 以支援內部實作的規則。 本節將介紹的設計和實作這些內部的模式。

有時候這些 DDD 技術規則和模式會認為有實作 DDD 方法並不容易學習的學習曲線的障礙。 但重要的部分是不模式本身，但其對齊的商業問題，讓組織程式碼和使用相同的商務詞彙表示 （通用語言）。 此外，只有當您實作複雜 microservices 重要的商務規則應該套用 DDD 方法。 更簡單的責任，類似 CRUD 服務，可以使用簡單的方法來管理。

要繪製的界限是索引鍵的工作設計和定義微服務時。 DDD 模式可協助您了解網域中的複雜度。 網域模型，針對每個繫結的內容，您可以找出並定義實體、 值的物件，與您的網域建立模型的彙總。 您建立並精簡包含定義您的內容界限內的網域模型。 而這是非常明確的微服務形式。 這些界限內的元件最終要您 microservices，不過在某些情況下，a BC 或商務 microservices 可以包括數個實體的服務。 DDD 即將界限及 microservices。

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>保留的微服務內容界限相對較小

決定繫結內容之間的界限的放置位置平衡兩個競爭目標。 首先，您想要一開始建立最小的可能 microservices，雖然，不應該是主要的驅動程式。您應該建立需要一致性的項目周圍的界限。 第二，您會想要避免多對話 microservices 之間的通訊。 這些目標可以有所出入另一個。 您應該將系統分解成許多小 microservices 像直到您看到成長快速隨著每個額外的嘗試將新的繫結內容的通訊界限來平衡它們。 一致性是單一的繫結內容中的索引鍵。

類似於[不適當的熟悉度程式碼的氣味](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy)時實作類別。 如果兩個 microservices 需要許多協同合作，它們可能應該相同的微服務。

若要查看的另一個方法是自主。 如果微服務必須依賴其他服務，以直接要求，並不真的自發。

## <a name="layers-in-ddd-microservices"></a>DDD microservices 中的圖層

大部分的企業應用程式具有重要的商務和技術的複雜性是由多個圖層定義。 圖層是邏輯的成品，並不相關的服務部署。 它們存在於協助開發人員管理在程式碼的複雜度。 不同層級 （例如網域的模型層與展示層等） 可能有不同的類型，這會強制這些型別之間的翻譯。

例如，無法從資料庫載入實體。 然後該資訊之後，或彙總的資訊包括額外的資料，從其他實體，可以傳送至用戶端透過 REST Web API 的 UI。 網域實體包含在網域模型層，而不會傳播至它不屬於，例如展示層的其他區域的點。

此外，您需要有實體永遠有效 (請參閱[設計網域模型層中的驗證](#designing-validations-in-the-domain-model-layer)> 一節) 彙總的根目錄 （根實體） 所控制。 因此，實體不應是繫結至用戶端檢視，因為 UI 層級某些資料可能仍然不會驗證。 這是 ViewModel 是的。 ViewModel 是專門用於簡報層所需的資料模型。 直接到 ViewModel 不屬於網域實體。 相反地，您需要翻譯 ViewModels 和網域實體之間，反之亦然。

透過單一項目時處理的複雜性，一定要有網域模型，由彙總根 （我們這更詳細地稍後討論），可確保所有的非變異值和規則相關以執行該群組的實體 （彙總）點或閘道，彙總的根。

圖 9 5 顯示 eShopOnContainers 應用程式中實作多層式的設計的方式。

![](./media/image6.png)

**圖 9 5**。 DDD eShopOnContainers 中順序的微服務中的圖層

您想要設計系統，讓每個圖層會只與特定的其他圖層進行通訊。 可能您更輕鬆地強制執行如果圖層會實作為不同的類別庫，因為您可以清楚地識別哪些相依性會設定程式庫之間。 比方說，網域模型層應該不依賴其他任何層級 (網域模型類別應該是一般舊 CLR 物件，或[POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)，類別)。 顯示在圖 9-6， **Ordering.Domain**層媒體櫃具有相依性，只有在.NET Core 文件庫上但不是能在任何其他自訂的程式庫 （資料程式庫、 持續性文件庫等）。

![](./media/image7.PNG)

**圖 9-6**。 實作為程式庫允許更佳控制圖層之間的相依性的圖層

### <a name="the-domain-model-layer"></a>網域模型層

Eric Evans 絕佳書籍[網域導向設計](http://domainlanguage.com/ddd/)隻字下列網域模型層和應用程式層級。

**網域模型層**： 負責代表商務、 商務規則與商務情況的相關資訊的概念。 會反映商務狀況的狀態是控制，而且在這裡使用，即使將其儲存的技術詳細資料會委派給基礎結構。 此圖層是商務軟體的核心。

網域模型層是表示商務的位置。 當您在.NET 中實作微服務網域模型層時，該圖層會編碼為擷取資料加上行為 （方法的邏輯） 之網域實體的類別程式庫。

遵循[永續性無知之](http://deviq.com/persistence-ignorance/)和[基礎結構忽略](https://ayende.com/blog/3137/infrastructure-ignorance)原則，此圖層必須完全忽略資料持續性的詳細資料。 基礎結構層級才能執行這些持續性工作。 因此，此圖層不應該直接相依性的基礎，這表示很重要的規則是您在網域模型實體類別應該是[POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s。

網域實體不應該有直接的相依性 （例如衍生自基底類別），Entity Framework 或 NHibernate 等任何資料存取基礎結構架構上。 在理想情況下，您網域的實體不應衍生自或實作任何基礎結構架構中定義的任何類型。

Entity Framework Core 像大多數最新型的 ORM 架構允許這種方式，以便您在網域模型類別不會連結至基礎結構。 不過，具有 POCO 實體不一定可以使用特定的 NoSQL 資料庫和架構，像執行者與 Azure Service Fabric 中的可靠集合時。

請務必遵循永續性無知之原則的網域模型，即使您不應該忽略持續性考量。 它仍然是您一定要了解實體資料模型，以及它如何對應至您的實體物件模型。 否則，您可以建立不可能的設計。

此外，這不表示您可以使用關聯式資料庫設計模型，並直接將它移至 NoSQL 或文件導向的資料庫。 在某些實體模型，模型可能適合，但通常沒有。 仍有實體模型必須遵守，基礎儲存體技術和 ORM 技術的條件約束。

### <a name="the-application-layer"></a>應用程式層

繼續移至應用程式層中，我們可以再次引用 Eric Evans 書籍[網域導向設計](http://domainlanguage.com/ddd/):

**應用程式層：**定義軟體應執行的工作，並指示算出問題的易懂的網域物件的工作。 此圖層會負責的工作是商務有意義，或所需的應用程式層級中的其他系統的互動。 此圖層是保持精簡。 它不包含商務規則或知識，但是只有座標工作和委派工作向下的下一層的網域物件的共同作業。 它並沒有狀態反映出商務狀況中，但它可能會反映使用者或程式的工作進度的狀態。

在.NET 中的微服務應用程式層通常自動程式碼做為 ASP.NET Core Web API 專案。 專案實作微服務的互動、 遠端網路存取，以及從 UI 或用戶端應用程式所使用之外部 Web Api。 如果使用 CQRS 處理命令接受微服務，以及甚至事件導向間的通訊 microservices （整合事件），它就會包含查詢。 代表應用程式層 ASP.NET Core Web API 不能包含商務規則或定義域知識 （尤其是網域的規則的交易或更新）;這些網域模型類別庫所擁有。 應用程式層必須只有座標工作和不保留或定義任何網域的狀態 （網域模型）。 它會委派商務規則的網域模型類別本身 （彙總根和網域實體），最後將會更新這些網域實體內的資料來的執行。

基本上，應用程式邏輯是您用來實作所有相依於指定的前端的使用案例。 例如，相關的 Web API 服務的實作。

目標是在網域模型層，其非變異項目、 資料模型與相關的商務規則的網域邏輯必須是完全獨立於展示和應用程式層。 大部分，網域模型層必須直接依存於任何基礎結構架構。

### <a name="the-infrastructure-layer"></a>基礎結構層級

基礎結構層級是一開始會保留網域實體 （在記憶體中） 中的資料保存在資料庫或其他持續性存放區中的方式。 例如，使用 Entity Framework 核心程式碼來實作使用建立的 DBContext 來保存關聯式資料庫中的資料儲存機制模式類別。

根據先前所述[永續性無知之](http://deviq.com/persistence-ignorance/)和[基礎結構忽略](https://ayende.com/blog/3137/infrastructure-ignorance)基礎結構層級的原則必須不"contaminate 」 網域模型層。 您必須防止網域模型實體類別無從驗證您用來保存資料 （EF 或任何其他架構） 的基礎結構不在架構上採取硬式相依性。 網域模型層類別庫應該只有您網域程式碼，只要[POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)實體類別實作您的軟體中心以及完全分開基礎結構技術。

因此，您的圖層或類別庫和專案應該最終取決於網域模型層級 （程式庫） 不是反之亦然，如圖 9-7 所示。

![](./media/image8.png)

**圖 9 7**。 DDD 各層之間的相依性

此圖層設計應該是獨立的每個微服務。 如前文所述，您可以實作最複雜 microservices 遵循 DDD 模式時實作簡單資料導向 microservices (單一層中的簡單 CRUD) 更簡單的方式。

#### <a name="additional-resources"></a>其他資源

-   **DevIQ。持續性忽略原則**
    [*http://deviq.com/persistence-ignorance/*](http://deviq.com/persistence-ignorance/)

-   **Oren Eini。基礎結構忽略**
    [*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)

-   **天使培茲。分層架構中網域導向設計**
    [*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)


>[!div class="step-by-step"]
[上一個](cqrs-微服務-reads.md) [下一步] (微服務-網域-model.md)
