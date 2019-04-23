---
title: 利用 DDD 和 CQRS 模式解決微服務中的商務複雜度
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 了解如何利用 DDD 與 CQRS 模式解決複雜的商業案例
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: f17acd6765de96bf8cec28c4e212733822fa0b73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019759"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>使用 DDD 與 CQRS 模式解決微服務中的商務複雜度

設計每個微服務的領域模型，或反映對業務領域了解程度的繫結內容。

本節著重於當您需要解決複雜的子系統時所實作的更進階微服務，或是衍生自領域專家對不斷改變之商務規則知識的微服務。 此節中所使用的架構模式是以領域驅動設計 (Domain-Driven Design，DDD) 以及命令和查詢職責分離 (Command and Query Responsibility Segregation，CQRS) 方法為基礎，如圖 7-1 所示。

![外部架構的差異：微服務模式、API 閘道、彈性通訊、pub/sub 等：內部架構：資料 動/CRUD、DDD 模式、相依性插入、多程式庫等。](./media/image1.png)

**圖 7-1**. 外部微服務架構與每個微服務的內部架構模式

不過，資料驅動微服務的大多數技術，像是如何實作 ASP.NET Core Web API 服務，或如何使用 Swashbuckle 或 NSwag 公開 Swagger 中繼資料，也適用於以 DDD 模式在內部實作之更進階的微服務。 本節是前面幾節的延伸，因為稍早所述的大部分實務也適用於這裡或任何類型的微服務。

本節會先提供 eShopOnContainers 參考應用程式中所使用之簡化 CQRS 模式的詳細資料。 稍後會對您概要說明 DDD 技術，這些技術可讓您尋找常見的模式，以便在應用程式中重複使用。

DDD 是一個龐大的主題，內含一組豐富的學習資源。 您可以從 Eric Evans 所著 [Domain-Driven Design](https://domainlanguage.com/ddd/) 之類的書籍，以及 Vaughn Vernon、Jimmy Nilsson、Greg Young、Udi Dahan、Jimmy Bogard 和許多其他 DDD/CQRS 專家所提供的其他教材開始著手。 但最重要的是，您需要試著了解如何在專家協助下，將來自交談、白板與領域模型課程的 DDD 技術，應用在您的實體業務領域中。

#### <a name="additional-resources"></a>其他資源

##### <a name="ddd-domain-driven-design"></a>DDD (領域驅動設計)

- **Eric Evans：領域語言** \
  <https://domainlanguage.com/>

- **Martin Fowler：領域驅動設計** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmy Bogard：加強您的領域：初階** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>DDD 書籍

- **Eric Evans：網域驅動設計：解決軟體核心的複雜度** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans：領域驅動設計參考：定義與模式摘要** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn Vernon：實作領域驅動設計**  \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn Vernon：領域驅動設計精華** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson：套用領域驅動設計與模式** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **Cesar de la Torre：N 層領域導向架構指南 (.NET)** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Abel Avram 和 Floyd Marinescu：快速領域驅動設計** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett、Nick Tune - 領域驅動設計的模式、準則與實務** \
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a>DDD 訓練課程

- **Julie Lerman 和 Steve Smith：網域驅動設計基本概念** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[上一頁](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[下一頁](apply-simplified-microservice-cqrs-ddd-patterns.md)
