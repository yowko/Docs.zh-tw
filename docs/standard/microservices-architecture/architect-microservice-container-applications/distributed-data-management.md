---
title: "挑戰和解決方案的分散式的資料管理"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |挑戰和解決方案的分散式的資料管理"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f961475b40c74bf448cff1aeae04ae4866360e52
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>挑戰和解決方案的分散式的資料管理

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>挑戰\#1： 如何定義的每個微服務界限

定義微服務界限可能是任何人在遇到第一個驗證題目。 必須是您的應用程式的每個微服務，而且每個微服務應該是自發所有的優點和它所傳達的挑戰。 但如何識別這些界限嗎？

首先，您需要將焦點放在應用程式的邏輯網域模型及相關的資料。 您必須嘗試識別資料及同一個應用程式內的不同內容的解除解合的島。 每個內容可能會有不同的商業語言 （不同的商務詞彙表示）。 表示內容應定義，並分開管理。 條款和在這些不同的內容中使用的實體可能會看似相似，但您可能會發現，在特定內容中，其中包含一個商務概念用於不同的用途，在另一個內容中，甚至可能需要不同的名稱。 例如，使用者可以稱為身分識別或成員資格的內容中的使用者身分在順序的內容中，買方之客戶在 CRM 內容中，為等等。

每個內容只是如何識別每個商務微服務和其相關的界限，識別與不同網域的多個應用程式內容之間的界限的方式領域模型和資料。 您一定會嘗試最小化這些 microservices 之間的連接。 本指南會進入此識別和網域模型設計的一節更詳細地[識別每個微服務的網域模型界限](#identifying-domain-model-boundaries-for-each-microservice)更新版本。

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>挑戰\#2： 如何建立從數個 microservices 擷取資料的查詢

第二個挑戰是如何實作從數個 microservices，擷取資料，同時避免多對話通訊以 microservices，從遠端用戶端應用程式的查詢。 範例可能需要顯示使用者資訊的購物籃、 類別目錄和使用者身分識別 microservices 所擁有的行動裝置應用程式在單一螢幕。 另一個範例就是包含許多資料表位於多個 microservices 複雜報表。 絕佳的解決方案視查詢的複雜性而定。 但是，在任何情況下，您將需要彙總資訊的方法如果您想要改善您的系統通訊的效率。 以下是最常用的解決方案。

**API 閘道**。 對於多個 microservices 擁有不同的資料庫從簡單的資料彙總，建議的方法是指 API 閘道彙總微服務。 不過，您需要謹慎實作此模式中，因為它可以在系統中，淺壓深點，它可能會違反微服務自主性的原則。 若要減輕這種可能性，您可以有多個處以精細 API 閘道每一個將焦點放在垂直 「 部分 」 或業務區域的系統。 使用中的一節將詳細說明 API 閘道模式稍後 API 閘道。

**查詢/reads 資料表 CQRS**。 從多個 microservices 彙總資料的另一個解決方案是[具體化的檢視模式](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)。 在這種方式，您會產生，事先 （非正規化的資料之前準備實際的查詢，就可能發生），唯讀資料的資料表與多個 microservices 所擁有。 資料表的格式，適合用戶端應用程式的需求。

請考慮類似行動應用程式的畫面。 如果您有單一資料庫時，您可能會提取一起使用的 SQL 查詢，執行複雜的聯結涉及多個資料表，該螢幕上的資料。 不過，當您有多個資料庫，且每個資料庫由不同的微服務所擁有，您無法查詢這些資料庫，並建立 SQL 聯結。 複雜的查詢會變成一項挑戰。 您可以解決使用 CQRS 方法的需求，您在不同的資料庫只用於查詢建立反正規化的資料表。 設計資料表時，可能特別針對複雜的查詢，所需的應用程式的螢幕和查詢資料表中的資料行的欄位之間有一對一關聯性所需的資料。 它也可做為報表用途。

這種方法不只會解決了原始問題 （如何查詢及聯結跨 microservices）;也可以改善效能大幅相較於複雜的聯結，因為您已經有應用程式必須在查詢資料表中的資料。 當然，使用查詢/讀取資料表中的命令和查詢責任隔離 (CQRS) 表示額外的開發工作，您必須不怕最終一致性。 然而，對於效能和高延展性需求[共同作業案例](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/)（或競爭的情況下，根據觀點來看） 是您應該將 CQRS 套用具有多個資料庫。

**在中央資料庫中的 「 冷資料 」**。 對於複雜的報表和可能不需要即時資料的查詢，常見的方法不會匯出您 「 熱資料 」 （從 microservices 異動資料） 為成只用於報表的大型資料庫的 「 冷資料 」。 中央資料庫系統都可以是巨量資料為基礎系統，例如 Hadoop，根據 Azure SQL 資料倉儲或甚至單一 SQL 資料庫 （如果大小不會發生問題），僅供報表使用類似的資料倉儲。

請注意，這個集中式的資料庫會僅適用於查詢和需要即時資料的報表。 原始的更新和交易，做為來源的真實性，一定要 microservices 資料中。 使用事件導向的通訊 （涵蓋在下一節），或使用其他資料庫基礎結構匯入/匯出工具，將會同步處理資料的方式。 如果您使用事件導向的通訊，該整合程序會如先前所述的 CQRS 查詢資料表，會傳播資料的方式類似。

不過，如果您的應用程式的設計牽涉到不斷地彙總來自多個 microservices 複雜查詢的資訊，它可能不正確的設計的徵兆，應該儘可能從其他 microservices 為隔離微服務。 （這不包括報表/analytics，應一律使用冷資料的中央資料庫。）通常發生此問題可能是合併 microservices 的理由。 您必須平衡的演進自主性和部署的每個強式的相依性、 一致性，與資料彙總的微服務。

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>挑戰\#3： 如何跨多個 microservices 達到一致性

如先前所述，每個微服務所擁有的資料是私用的微服務，並只使用可以存取其應用程式開發介面的微服務。 因此，呈現一項挑戰是如何同時保持一致性，跨多個 microservices 實作端對端商務程序。

若要分析此問題，讓我們看看從範例[eShopOnContainers 參考應用程式](http://aka.ms/eshoponcontainers)。 類別目錄的微服務會維護所有產品，包括其股票的層級的相關資訊。 訂購微服務管理訂單，並必須確認新的訂單不能超過可用的類別目錄產品存貨。 （或此案例可能涉及邏輯會處理交貨產品）。在此應用程式假設整合型版本，排序子系統無法只使用 ACID 交易來檢查可用的內建、 在 「 訂單 」 資料表中建立順序並更新 Products 資料表中可用的存貨。

不過，在 microservices 為基礎應用程式中，Order 和產品資料表所擁有其各自的 microservices。 沒有微服務曾應該包含在自己的交易或查詢，另一個的微服務所擁有的資料庫，如圖 4 至 9 所示。

![](./media/image9.PNG)

**圖 4 至 9**。 微服務無法直接存取另一個的微服務中的資料表

訂購微服務應該更新 Products 資料表直接管理，因為 Products 資料表由目錄微服務所擁有。 若要更新目錄微服務，訂購微服務應該永遠只會使用非同步通訊，例如整合事件 （訊息和事件為基礎的通訊）。 這是如何[eShopOnContainers](http://aka.ms/eshoponcontainers)參考應用程式會執行這種類型的更新。

如下所述[CAP 理論](https://en.wikipedia.org/wiki/CAP_theorem)，您必須選擇可用性之間 ACID 強式一致性。 大部分的微服務為基礎的情況下要求可用性和高的延展性，而不是強式一致性。 關鍵任務應用程式必須保持註冊，並且執行，以及開發人員可以處理強式一致性使用弱式或最終一致性的使用技巧。 這是大部分的微服務基礎架構所採用的方法。

此外，ACID 樣式或兩階段認可的交易不是只針對 microservices 原則;大部分的 NoSQL 資料庫 （例如 Azure Cosmos DB、 MongoDB、 等等） 不支援兩階段認可的交易。 不過，維護資料服務和資料庫的一致性十分重要。 如何跨多個 microservices 傳播變更，某些資料需要備援時的問題也與這項挑戰 — 例如，當您需要有產品的名稱或類別目錄的微服務 」 和 「 購物籃中的描述微服務。

這個問題的最佳解決方案是使用最終 microservices 以透過事件導向的通訊和發佈和訂閱的系統之間的一致性。 這些主題的章節將討論[事件驅動的非同步通訊](#async_event_driven_communication)本指南稍後的。

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>挑戰\#4： 如何設計跨微服務界限的通訊

通訊跨微服務界限是真正的挑戰。 在此內容中的通訊並不是指您哪些通訊協定 （HTTP 和 AMQP 訊息，依此類推，REST） 應該使用。 相反地，其定址該使用何種通訊樣式，以及特別是如何結合您 microservices 應該。 結合層級，依據發生失敗時，您的系統上發生失敗的影響將會大大地改變。

就像 microservices 型應用程式，與許多移動的成品和跨許多伺服器或主機，分散式服務的分散式系統中的元件最終將會失敗。 部分失敗，而且甚至更大的潛在性中斷問題會發生，因此您需要對它們列入考量的風險一般在這種類型的分散式系統設計您 microservices 和通訊。

常用的方法是實作 HTTP (REST) 為基礎 microservices，由於其簡易性。 以 HTTP 為基礎的方法是完全可接受的。與使用方式相關的問題。 如果您只是為了與您從用戶端應用程式或應用程式開發介面閘道的 microservices 互動使用 HTTP 要求和回應，沒關係。 但如果您建立的同步 HTTP 呼叫的長鏈結跨 microservices，如同 microservices 是整合的應用程式中的物件，其界限透過通訊應用程式將最終遇到問題。

比方說，假設用戶端應用程式可讓個別的微服務，例如訂購微服務的 HTTP API 呼叫。 如果訂購微服務接著會呼叫其他使用相同的要求/回應 HTTP microservices 循環，您所建立的 HTTP 呼叫鏈結。 它可能會看似合理一開始。 不過，有向此路徑時要考量的重點：

-   封鎖和低效能。 由於 HTTP 同步的本質，原始要求不會收到回應之前完成所有的內部 HTTP 呼叫。 假設是否這些呼叫的數目會大幅提升，而其中一個中繼 HTTP 呼叫的微服務，同時被封鎖。 結果是會影響效能，，和其他 HTTP 要求增加為以等比級數受影響的整體延展性。

-   結合 microservices 使用 HTTP。 商務 microservices 不應搭配其他商務 microservices。 在理想情況下，它們應該不 「 知道 」 有關的其他 microservices 存在。 如果您的應用程式依賴耦合 microservices 範例所示，達成自主性每微服務會幾乎不可能。

-   失敗的任何一個的微服務。 如果您實作 microservices 任何 microservices 失敗時 （將會失敗的最終） microservices 的整個鏈結，透過 HTTP 呼叫連結的鏈結將會失敗。 微服務為基礎的系統應該設計成可繼續運作且盡可能期間部分失敗。 即使您實作重試使用指數型輪詢或斷路器機制與用戶端邏輯時，多個複雜 HTTP 呼叫鏈結是，它會實作 HTTP 為基礎的失敗策略越複雜。

事實上，若您的內部 microservices 正在通訊所述，建立的 HTTP 要求的鏈結，它可以被 argued 您有一個根據 HTTP，而不是 intraprocess 通訊機制的處理序之間的整合應用程式。

因此，為了強制執行微服務自主性，並讓較佳的恢復功能，您應該盡量少用鏈結的要求/回應通訊的跨 microservices。 建議您間微服務通訊，使用唯一的非同步互動，使用非同步訊息和事件為基礎的通訊，或使用 HTTP 輪詢獨立原始的 HTTP 要求/回應週期。

具有其他詳細資料，稍後在本指南中的各節說明的非同步通訊使用[非同步的微服務整合會強制微服務的自主性](#asynchronous-microservice-integration-enforce-microservices-autonomy)和[非同步訊息架構通訊](#asynchronous-message-based-communication)。

## <a name="additional-resources"></a>其他資源

-   **CAP 理論**
    [*https://en.wikipedia.org/wiki/CAP\_理論*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **最終一致性**
    [*https://en.wikipedia.org/wiki/Eventual\_一致性*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **資料一致性入門**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Martin Fowler：CQRS （命令和查詢責任隔離）**
    [*http://martinfowler.com/bliki/CQRS.html*](http://martinfowler.com/bliki/CQRS.html)

-   **具體化檢視**
    [*https://docs.microsoft.com/azure/architecture/patterns/materialized-view*](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

-   **Charles 資料列。ACID vs。基底： Shifting pH 資料庫交易處理**
    [*http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/*](http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/)

-   **補償交易**
    [*https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction*](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

-   **Udi Dahan。服務導向組合**
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)


>[!div class="step-by-step"]
[上一個](邏輯-或-實體-architecture.md) [下一步] (識別的微服務-網域-模型-boundaries.md)
