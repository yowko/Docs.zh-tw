---
title: "資料 sovereignty 每微服務"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |資料 sovereignty 每微服務"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c51daae04215cfa6f5b5b8d2158a8ed1a8949652
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="data-sovereignty-per-microservice"></a>資料 sovereignty 每微服務

Microservices 架構的重要規則是每個微服務必須擁有網域資料和邏輯。 就像完整的應用程式擁有其邏輯和資料，因此必須每個微服務擁有其邏輯和自發的生命週期，與獨立部署每個微服務底下的資料。

這表示，概念模型的網域將子系統或 microservices 之間，而有所不同。 請考慮企業應用程式，其中客戶關係管理 (CRM) 應用程式，交易式購買子系統和客戶支援子系統上唯一客戶實體屬性和資料，每次呼叫而且每個使用不同的已繫結的內容 (BC)。

這個原則非常類似[網域導向設計 (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design)，其中每個[繫結內容](https://martinfowler.com/bliki/BoundedContext.html)或自發子系統或服務必須擁有其網域模型 （資料加上的邏輯和行為）。 每個 DDD 繫結內容相互關聯到一個商務微服務 （一或多個服務）。 （我們展開上繫結內容中的模式下一節中有關此點）。

相反地，許多應用程式中使用的傳統 （龐大資料） 方法是有單一的集中式的資料庫或幾個資料庫。 這通常是標準化的 SQL database 用於整個應用程式和所有其內部子系統，如圖 4-7 所示。

![](./media/image7.png)

**圖 4-7**。 資料 sovereignty 比較： 龐大的資料庫，以及 microservices

集中式的資料庫方法一開始會看起來更簡單，而且似乎以便重複使用的不同子系統進行一致的所有項目中的實體。 但事實上您得到很大的資料表，做許多不同子系統，且包含屬性和資料行不需要在大部分情況下。 就像嘗試登山簡短的軌跡、 進行全天汽車旅行，和學習地理區使用相同的實體對應。

通常是單一關聯式資料庫含有的整合應用程式有兩個重要好處： [ACID 交易](https://en.wikipedia.org/wiki/ACID)和 SQL 語言，這兩個工作的所有資料表和應用程式相關的資料。 這種方法可用來輕鬆地撰寫會結合來自多個資料表資料的查詢。

不過，資料存取限制變得更複雜移到 microservices 架構時。 但即使 ACID 交易可以或應該使用 「 微服務 」 或 「 繫結內容中，每個微服務所擁有的資料是私用的微服務，並只能透過其微服務應用程式開發介面來存取。 封裝資料，可確保 microservices 鬆散偶合，而且彼此就能持續改進。 如果多個服務存取相同的資料，結構描述更新需要協調的更新的所有服務。 這會破壞微服務生命週期自主。 但分散式的資料結構，表示您無法跨 microservices 進行單一 ACID 交易。 這會表示商務程序跨越多個 microservices 時，您必須使用最終一致性。 這是難以實作比簡單的 SQL 聯結。同樣地，許多其他關聯式資料庫功能無法使用。 跨多個 microservices

從現在更進一步，不同 microservices 通常使用不同*種類*的資料庫。 現代應用程式存放區和程序的不同種類的資料，以及關聯式資料庫不一定是最佳選擇。 某些使用案例，例如 Azure DocumentDB 或 MongoDB 的 NoSQL 資料庫可能會更方便的資料模型並提供較佳的效能和延展性比 SQL 資料庫，例如 SQL Server 或 Azure SQL Database。 在其他情況下，關聯式資料庫仍是最好的方法。 因此，microservices 為基礎的應用程式通常會使用它有時稱為 「 SQL 和 NoSQL 資料庫的混合[polyglot 持續性](http://martinfowler.com/bliki/PolyglotPersistence.html)方法。

儲存資料的資料分割、 polyglot 持續架構有許多好處。 這些包括鬆散偶合的服務和更佳效能、 延展性、 成本與管理能力。 不過，它可能導致某些分散式的資料管理的挑戰，因為我們將說明中 「[識別網域模型界限](#identifying-domain-model-boundaries-for-each-microservice)"本章稍後。

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Microservices 和繫結內容模式之間的關聯性

微服務概念衍生自[繫結的內容 (BC) 模式](http://martinfowler.com/bliki/BoundedContext.html)中[網域導向設計 (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design)。 透過將其分為多個 BCs 以及明確了解其界限 DDD 是搭配大型模型中處理。 每個 BC 必須有它自己的模型和資料庫。同樣地，每個微服務擁有及其相關的資料。 此外，每個 BC 通常都有它自己[通用語言](http://martinfowler.com/bliki/UbiquitousLanguage.html)協助軟體開發人員 」 和 「 網域專家之間的通訊。

通用語言中的這些詞彙 （主要網域實體） 可以有不同的名稱在不同的繫結內容中，即使不同的網域實體都共用相同的識別 （也就是唯一識別碼是用來從儲存體讀取實體）。 比方說，在使用者設定檔繫結內容中，使用者網域實體可能會共用身分識別與買方網域實體順序的繫結內容中。

微服務因此就像是繫結的內容，但它也會指定它是一種分散式的服務。 建置為個別的處理序針對每個繫結的內容，且必須使用前文所述，如 HTTP/HTTPS，WebSockets，分散式通訊協定或[AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)。 繫結內容模式中，不過，未指定繫結內容是否分散式的服務或其是否只要邏輯界限 （例如泛型的子系統） 整合型部署應用程式中。

請務必反白顯示，定義服務，以針對每個繫結的內容是較好的位置開始。 但您沒有限制，您的設計。 有時您必須設計繫結的內容，或商務微服務是由數個實體的服務所組成。 最後，這兩種模式，但是 — 繫結內容和微服務 — 密切相關。

從藉由取得真正的分散式 microservices 形式界限 microservices DDD 優點。 但不是共用之間 microservices 模型概念都是您也想要在繫結的內容中。

### <a name="additional-resources"></a>其他資源

-   **Chris Richardson。模式： 資料庫每個服務**
    [*http://microservices.io/patterns/data/database-per-service.html*](http://microservices.io/patterns/data/database-per-service.html)

-   **Martin Fowler：BoundedContext**
    [*http://martinfowler.com/bliki/BoundedContext.html*](http://martinfowler.com/bliki/BoundedContext.html)

-   **Martin Fowler：PolyglotPersistence**
    [*http://martinfowler.com/bliki/PolyglotPersistence.html*](http://martinfowler.com/bliki/PolyglotPersistence.html)

-   **Alberto Brandolini。策略性網域導向設計，含有內容對應**
    [*https://www.infoq.com/articles/ddd-contextmapping*](https://www.infoq.com/articles/ddd-contextmapping)


>[!div class="step-by-step"]
[上一個](microservices-architecture.md) [下一步] (邏輯-或-實體-architecture.md)
