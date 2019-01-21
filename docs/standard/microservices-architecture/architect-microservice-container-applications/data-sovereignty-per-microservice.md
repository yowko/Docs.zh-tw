---
title: 每個微服務的資料自主性
description: 每個微服務之資料自主性是微服務的其中一個重點。 每個微服務必須是其資料庫的唯一擁有者，不與任何其他人共用。 當然，微服務所有執行個體會連接到相同的高可用性資料庫。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 4900c294f94f4b4d604ba841595fc5c6d7952c10
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144898"
---
# <a name="data-sovereignty-per-microservice"></a>每個微服務的資料自主性

微服務架構的重要規則是，每個微服務必須擁有自己的網域資料和邏輯。 就像完整的應用程式擁有其邏輯和資料，每個微服務也必須在自發的生命週期裡擁有其邏輯和資料，並且每個微服務有獨立的部署。

這表示，網域的概念模型將在各個子系統或微服務之間有所不同。 請考慮企業應用程式，其中客戶關係管理 (CRM) 應用程式、交易式購買子系統和客戶支援子系統每個都呼叫不同的客戶實體屬性和資料，而每一者都使用不同的繫結內容 (BC)。

這個原則非常類似[網域導向設計 (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design)，其中每個[繫結內容](https://martinfowler.com/bliki/BoundedContext.html)或自發子系統或服務必須擁有其網域模型 (資料加上邏輯和行為)。 每個 DDD 繫結內容相互關聯到一個商務微服務 (一或多個服務)。 我們會在下一節從這點繼續展開繫結內容模式。

在另一方面，許多應用程式中使用的傳統 (單一資料) 方法，是單一的集中式資料庫或幾個資料庫。 這通常是標準化的 SQL 資料庫，用於整個應用程式及其所有內部子系統，如圖 4-7 所示。

![在傳統的方法中，所有服務之間會共用單一資料庫，通常使用分層架構。 在微服務方法中，每個微服務擁有其模型/資料](./media/image7.png)

**圖 4-7**. 資料自主性比較：單一資料庫與微服務

集中式資料庫方法一開始看起來較簡單，而且似乎能重複使用不同子系統中的實體，讓一切一致。 但事實上，您會得到很大的資料表，它們會服務許多不同子系統，且包含在大部分情況下不需要的屬性和資料行。 就像是嘗試使用相同的實體地圖來進行短距離的健走、一整天的汽車旅行，以及學習地理。

一般具有單一關聯式資料庫的單一應用程式有兩個重要優點：[ACID 交易](https://en.wikipedia.org/wiki/ACID)和 SQL 語言，兩者都可在與您應用程式相關的所有資料表和資料之間使用。 這種方法可用來輕鬆地撰寫查詢，以結合來自多個資料表的資料。

不過，當您移到微服務架構時，資料存取變得複雜許多。 但即使 ACID 交易可以或應該用於微服務或繫結內容中，每個微服務所擁有的資料仍是該微服務私用，並且只能透過其微服務 API 來存取。 封裝資料可確保微服務鬆散偶合，而且彼此獨立地持續改進。 如果多個服務存取相同的資料，結構描述更新便需要所有服的協調性更新。 這會破壞微服務生命週期自主。 但分散式資料結構表示您無法讓單一 ACID 交易跨越微服務。 這又表示當商務程序跨越多個微服務時，您必須使用最終一致性。 這要實作時比簡單的 SQL 聯結難上許多，因為您無法建立完整性條件約束，或在不同的資料庫之間使用分散式交易，我們將在稍後說明。 同樣地，許多其他關聯式資料庫功能無法跨多個微服務使用。

更進一步地說，不同的微服務通常使用不同「種類」的資料庫。 現代應用程式會存放和處理多種種類的資料，且關聯式資料庫不一定是最佳選擇。 對於某些使用案例，例如 Azure CosmosDB 或 MongoDB 的 NoSQL 資料庫，可能會有更方便的資料模型，並提供較 SQL Server 或 Azure SQL Database 等 SQL 資料庫更佳的效能和延展性。 在其他情況下，關聯式資料庫仍是最好的方法。 因此，以微服務為基礎的應用程式通常會使用 SQL 和 NoSQL 資料庫的混合，這有時稱為[混合持續性 (Polyglot Persistence)](https://martinfowler.com/bliki/PolyglotPersistence.html) 方法。

資料儲存體的資料分割、混合持續架構有許多優點。 這些包括鬆散偶合的服務和更佳的效能、延展性、成本與管理能力。 不過，它可能導致某些分散式資料管理的挑戰，如本章稍後的[識別領域模型界限](identify-microservice-domain-model-boundaries.md)中所說明。

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>微服務和繫結內容模式之間的關聯性

微服務概念衍生自[網域導向設計 (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design) 中的[繫結內容 (BC) 模式](https://martinfowler.com/bliki/BoundedContext.html)。 DDD 透過將大型模型分成多個 BC 並且明確指定其界限來處理大型模型。 每個 BC 必須有自己的模型和資料庫。同樣地，每個微服務也擁有其相關資料。 此外，每個 BC 通常都有它自己的[通用語言](https://martinfowler.com/bliki/UbiquitousLanguage.html)，協助軟體開發人員和網域專家之間的溝通。

通用語言中的詞彙 (主要為領域實體) 在不同繫結內容中可以有不同名稱，即使是不同領域實體都共用相同的識別 (亦即，用來從儲存體讀取實體的唯一識別碼)。 比方說，在使用者設定檔繫結內容中，使用者網域實體可能會與排序之繫結內容中的買方網域實體共用身分識別。

因此，微服務就像是繫結內容，但它也會指定其為一種分散式服務。 它針對每個繫結內容建置為個別的處理序，且必須使用前文所述的分散式通訊協定，例如 HTTP/HTTPS、WebSockets 或 [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)。 不過，繫結內容模式並未指定繫結內容是否為分散式服務，還是它只是單一部署應用程式中的邏輯界限 (例如泛型子系統)。

值得強調的一點是，為每個繫結內容定義服務是個不錯的起點。 但您不必將設計限制於此。 有時您必須設計由數個實體服務組成的繫結內容或商務微服務。 但最後，這兩種模式 - 繫結內容和微服務 - 密切相關。

DDD 藉由以分散式微服務的形式得到真實界限而從微服務獲益。 但如同不要在微服務之間共用模型，您可能也不想在繫結內容中共用模型。

### <a name="additional-resources"></a>其他資源

- **Chris Richardson：模式：每個服務的資料庫** \
  [*https://microservices.io/patterns/data/database-per-service.html*](https://microservices.io/patterns/data/database-per-service.html)

- **Martin Fowler：BoundedContext** \
  [*https://martinfowler.com/bliki/BoundedContext.html*](https://martinfowler.com/bliki/BoundedContext.html)

- **Martin Fowler：PolyglotPersistence** \
  [*https://martinfowler.com/bliki/PolyglotPersistence.html*](https://martinfowler.com/bliki/PolyglotPersistence.html)

- **Alberto Brandolini.含內容對應的策略性領域導向設計** \
  [*https://www.infoq.com/articles/ddd-contextmapping*](https://www.infoq.com/articles/ddd-contextmapping)

>[!div class="step-by-step"]
>[上一頁](microservices-architecture.md)
>[下一頁](logical-versus-physical-architecture.md)
