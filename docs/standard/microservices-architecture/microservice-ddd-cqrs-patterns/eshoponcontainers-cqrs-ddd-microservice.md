---
title: "套用 CQRS 和 CQS 中 eShopOnContainers DDD 微服務方法"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |套用 CQRS 和 CQS 中 eShopOnContainers DDD 微服務方法"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: a2c4429a75ca47d4fbcde868b95e76bc65ea2bef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>套用 CQRS 和 CQS 中 eShopOnContainers DDD 微服務方法

排序的微服務 eShopOnContainers 參考的應用程式的設計根據 CQRS 原則。 不過，它會使用簡單的方法，其只分隔之命令的查詢，並使用相同的資料庫，這兩個動作的。

這些模式，並在這裡，很重要的一點的本質是查詢是等冪： 無論查詢系統時，該系統的狀態的多少次不會變更您甚至還可以使用不同的 「 讀取 」 資料模型比交易的邏輯 「 寫入 」網域模型，雖然排序 microservices 使用相同的資料庫。 因此，這是簡單的 CQRS 方法。

相反地，觸發程序的交易和資料更新的命令會將狀態變更系統中。 使用命令，您需要時請小心處理複雜和多變的商務規則。 這正是您要套用至具有更好的模型化的系統 DDD 技術。

本指南中的 DDD 模式不應該套用通用。 它們會導致您的設計上的條件約束。 這些條件約束提供一段時間，特別是在命令和其他程式碼會修改系統狀態的優點，例如，較高的品質。 不過，這些條件約束加入較少的優點，進行讀取和查詢資料的複雜性。

其中一個這類模式是彙總的模式中，我們更檢查稍後的章節。 簡言之，在彙總模式中，您將許多網域物件視為單一單位，因為其網域中的關聯性。 您可能不一定能取得從查詢; 在此模式的優點它可以增加查詢邏輯的複雜度。 唯讀查詢，未取得多個物件視為單一的彙總的優點。 您只能取得複雜性。

如下圖 9-2，本指南建議使用 DDD 模式只能在您的微服務的交易式/更新區域中 （也就觸發命令）。 查詢可以依照更簡單的方法，而且應該分開之後 CQRS 方法的命令。

實作 「 查詢端 」，您可以選擇許多方式，從您完全成熟 ORM EF 核心、 AutoMapper 投影、 預存程序、 檢視、 具體化的檢視或微 ORM 等。

本指南中，及我們選擇實作直接查詢使用微 eShopOnContainers （特別是順序微服務） 中，例如 ORM [Dapper](https://github.com/StackExchange/dapper-dot-net)。 這可讓您實作任何 SQL 陳述式，以取得最佳效能，這點受惠非常少的額外負荷的淺架構為基礎的查詢。

請注意，當您使用這個方法時，實體保存至 SQL 資料庫的方式會影響的任何更新您的模型也需要個別更新 Dapper 或任何其他個別 (非 EF) 方法來查詢所使用的 SQL 查詢。

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>CQRS 和 DDD 模式不是最上層的架構

它一定要了解該 CQRS 和大部分 DDD 模式 （例如 DDD 層級或領域模型搭配彙總） 不是架構的樣式，而只是架構模式。 Microservices、 SOA 和事件驅動的架構 (EDA) 是的範例架構的樣式。 這些主題說明許多元件，例如許多 microservices 系統。 CQRS 和 DDD 模式描述的項目在單一系統或元件。在此情況下，項目內的微服務。

不同的繫結內容 (BCs) 會採用不同的模式。 它們有不同的責任，並會導致不同的解決方案。 值得強調的強制執行相同的模式，每個地方會導致失敗。 請勿 everywhere 使用 CQRS 和 DDD 模式。 許多子系統、 BCs 或 microservices 更簡單，可以更輕鬆地使用簡單的 CRUD 服務，或使用另一種方法實作。

沒有一個應用程式架構： 您要設計的系統或端對端應用程式架構 （例如 microservices 架構）。 不過，每個繫結內容 」 或 「 微服務該應用程式中的設計會反映其本身的權衡取捨完全和架構模式層級的內部的設計決策。 請勿嘗試套用相同的架構模式 CQRS 或 DDD 等位置。

####  <a name="additional-resources"></a>其他資源

-   **Martin Fowler：CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

-   **Greg Young。CQS vs。CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)

-   **Greg Young。CQRS 文件**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)

-   **Greg Young。CQRS，工作基礎的 Ui 和事件來源**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)

-   **Udi Dahan。已釐清 CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **事件來源 (ES)**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)


>[!div class="step-by-step"]
[上一個](apply-simplified-microservice-cqrs-ddd-patterns.md) [下一步] (cqrs-微服務-reads.md)
