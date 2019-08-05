---
title: 分散式資料管理的挑戰和解決方案
description: 了解微服務產業中分散式資料管理的挑戰和解決方案。
ms.date: 09/20/2018
ms.openlocfilehash: 7733a4523e147591151cd0dda26c43992dbe9a41
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673135"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>分散式資料管理的挑戰和解決方案

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>挑戰 \#1：如何定義每項微服務的界限

定義微服務的界限，可能是所有人遇到的第一項挑戰。 每項微服務必須是您應用程式的一個片段，而且每項微服務應該自發傳達所有的優點和挑戰。 但如何識別這些界限呢？

首先，您需要將焦點放在應用程式的邏輯網域模型及相關資料。 嘗試識別低結合的孤立資料群，以及同一個應用程式內的不同內容。 每個內容可能具有不同的商業語言 (不同的商務詞彙)。 這些內容都應該分開定義與管理。 這些不同內容中使用的字詞和實體可能看似雷同，但您可能會發現特定內容中的某項商務概念，在另一份內容中用於不同的用途，甚至可能使用不同的名稱。 例如，使用者在身分識別或成員資格內容中稱為使用者，在 CRM 內容中稱為客戶，在訂購內容中稱為買方等等。

您識別多種應用程式內容與每種內容不同網域之間界限的方式，與您識別每項商務微服務界限及其相關網域模型和資料的方式如出一轍。 您一定要嘗試將這些微服務之間的結合程度降至最低。 本指南會在稍後的[識別每項微服務的網域模型界限](identify-microservice-domain-model-boundaries.md)一節中，詳細說明此識別和網域模型設計。

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>挑戰 \#2：如何建立從數項微服務擷取資料的查詢

第二項挑戰是如何實作從數項微服務擷取資料的查詢，同時避免與遠端用戶端應用程式的微服務過度對話。 例如，行動應用程式單一畫面需要顯示的使用者資訊，為購物籃、目錄和使用者身分識別微服務所擁有。 另一例則是包含許多資料表的複雜報表，這些資料表位於多項微服務中。 正確的解決方案視查詢的複雜性而定。 但如果您想要改善系統的通訊效率，則無論如何都需要有彙總資訊的方法。 以下是最常用的解決方案。

**API 閘道。** 如是擁有不同資料庫之多項微服務的簡單資料彙總，建議的方法是稱為 API 閘道的彙總微服務。 不過，實作此模式時務須謹慎小心，因為它可能是系統的關鍵點，會違反微服務自主性原則。 為降低這種可能性，您可以有多個精細處理的 API 閘道，它們每一個都將焦點放在系統的垂直「配量」或業務區域。 稍後的 [API 閘道](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#why-consider-api-gateways-instead-of-direct-client-to-microservice-communication)一節會詳細說明 API 閘道模式。

**使用查詢/讀取資料表的 CQRS。** 另一個彙總多項微服務資料的解決方案是[具體化檢視模式](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)。 在這種方法中，您要事先以多項微服務擁有的資料產生唯讀資料表 (在實際查詢開始前準備好反正規化的資料)。 資料表格式要符合用戶端應用程式的需求。

請考慮類似行動應用程式的畫面。 如果您有單一資料庫，您可能會使用執行多個資料表複雜聯結的 SQL 查詢，為該畫面提取資料。 不過，當您有多個資料庫，且每個資料庫為不同的微服務所擁有時，您無法查詢這些資料庫，也無法建立 SQL 聯結。 您的複雜查詢會變成一項挑戰。 您可以使用 CQRS 方法來解決需求：在只用於查詢的不同資料庫中建立反正規化的資料表。 您可以使用應用程式畫面所需欄位和查詢資料表資料行之間的一對一關聯性，專門為複雜查詢所需要的資料設計資料表。 它也可以用作報表。

這種方法不只可解決原始問題 (如何跨微服務查詢及聯結)，相較於複雜聯結，還可以大幅改善效能，因為查詢資料表中已經有應用程式需要的資料。 當然，使用利用查詢/讀取資料表的命令與查詢責任隔離 (CQRS) 表示會有額外的開發工作，而您需要堅持最終的一致性。 然而，您應該對有效能和高延展性需求的[共同作業案例](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (或競爭案例，視觀點而定)，套用使用多個資料庫的 CQRS。

**中央資料庫中「幾乎不存取的資料」。** 對於可能不需要即時資料的複雜報表和查詢，常見方法是將您「經常存取的資料」(來自微服務的交易資料) 匯出至僅供報表使用的大型資料庫成為「幾乎不存取的資料」。 中央資料庫系統可以是巨量資料型系統，例如 Hadoop，類似 Azure SQL 資料倉儲的一種資料倉儲，或甚至僅供報表使用的單一 SQL 資料庫 (如果大小不是問題)。

請牢記，這種集中式的資料庫僅供不需要即時資料的查詢和報表使用。 作為來源的原始更新和交易，必須位於微服務資料中。 同步處理資料的方式，是使用事件導向的通訊 (後續各節予以說明)，或使用其他資料庫基礎結構的匯入/匯出工具。 如果使用事件導向的通訊，則該整合程序會類似先前所述針對 CQRS 查詢資料表的資料傳播方式。

不過，如果您的應用程式設計涉及針對複雜查詢不斷彙總多項微服務的資訊，它可能是不良設計的徵兆，因為微服務應該盡可能與其他微服務隔離。 (這會排除應一律使用幾乎不存取資料中央資料庫的報表/分析。)發生這種問題通常會成為合併微服務的理由。 您必須平衡每一項微服務的演進與部署自主性與強式的相依性、一致性及資料彙總。

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>挑戰 \#3：如何跨多項微服務達到一致性

如前所述，每項微服務所擁有的資料都是該微服務私用的，只能使用其微服務 API 存取。 因此，呈現的挑戰就是如何實作端對端商務程序，同時跨多項微服務保持一致性。

請參閱 [eShopOnContainers 參考應用程式](https://aka.ms/eshoponcontainers)的範例來分析此問題。 目錄微服務會維護包括產品價格在內的所有產品相關資訊。 購物籃微服務會管理使用者新增至購物籃的產品項目暫時資料，包含項目新增至購物籃時的價格。 當目錄中的產品價格更新時，保留相同產品之使用中的購物籃也應該更新該價格，加上系統應該可能會警告使用者，特定項目的價格在新增至購物籃後已變更。

在此應用程式的假設整合型版本中，當 products 資料表的價格變更時，目錄子系統可能只會使用 ACID 交易，更新 Basket 資料表中目前的價格。

不過，在微服務型的應用程式中，Product 和 Basket 資料表分別為其微服務所擁有。 沒有任何一項微服務會在本身交易中包含其他微服務所擁有的資料表/儲存體，直接查詢也不會，如圖 4-9 所示。

![微服務無法直接存取另一項微服務的資料表，必須使用最終一致性同步資料。](./media/image9.png)

**圖 4-9**。 微服務無法直接存取其他微服務的資料表

目錄微服務不應該直接更新 Basket 資料表，因為 Basket 資料表為購物籃微服務所擁有。 為更新購物籃微服務，目錄微服務應該使用可能以非同步通訊為基礎的最終一致性，例如整合事件 (訊息和事件通訊)。 這是 [eShopOnContainers](https://aka.ms/eshoponcontainers) 參考應用程式執行這類跨微服務一致性的方式。

如 [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem) (CAP 定理) 所述，您需要在可用性與 ACID 強式一致性中擇一。 大部分的微服務型案例都會要求可用性和高延展性，而不是強式一致性。 關鍵任務應用程式必須保持啟用及執行，開發人員才能透過處理弱式或最終一致性的技術，處理強式一致性。 這是大部分微服務型架構採用的方法。

此外，ACID 型或兩階段認可交易都不是只針對微服務原則，大部分的 NoSQL 資料庫 (例如 Azure Cosmos DB、MongoDB 等等) 都不支援兩階段認可交易，一般用於分散式資料庫案例。 不過，跨服務和資料庫維護資料的一致性十分重要。 這項挑戰也與當某些資料需要備援時，如何跨多項微服務傳播變更的問題有關，例如目錄微服務和購物籃微服務中需要有產品名稱或描述時。

這個問題的最佳解決方案，是在透過事件導向通訊架構的微服務和發佈訂閱系統之間使用最終一致性。 本指南稍後的[非同步的事件驅動通訊](asynchronous-message-based-communication.md#asynchronous-event-driven-communication)一節會討論這些主題。

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>挑戰 \#4：如何設計跨微服務界限的通訊

跨微服務界限的通訊是項真正的挑戰。 在此內容中，通訊非指您應該使用的通訊協定 (HTTP 和 REST、AMQP、傳訊等等)。 而是處理您應該使用的通訊樣式，特別是您的微服務應有的結合程度。 視結合程度而定，發生失敗時，該失敗對系統造成的影響大不相同。

在類似微服務型應用程式的分散式系統中，會有許多四處移動的成品以及跨許多伺服器或主機的分散式服務，元件最終會失敗。 因為會發生部分失敗甚至更大範圍的中斷問題，所以設計微服務及跨這些微服務的通訊時，您需要將這類分散式系統的常見風險列入考量。

常用的方法是實作以 HTTP (REST) 為基礎的微服務，因為它們簡便易行。 HTTP 型的方法完全可行，問題是您如何使用它。 如果您使用 HTTP 要求和回應只是為了與用戶端應用程式或 API 閘道的微服務進行互動，那就無妨。 但如果您建立跨微服務的同步 HTTP 呼叫長鏈結，將微服務當作整合型應用程式的物件進行跨界限通訊，您的應用程式最後一定會發生問題。

例如，假設用戶端應用程式向個別的微服務發出 HTTP API 呼叫，例如訂購微服務。 如果訂購微服務接著在相同的要求/回應循環中，使用 HTTP 呼叫其他微服務，則要建立 HTTP 呼叫鏈結。 它可能一開始看似合理。 但一路下來總會碰到要考量的重點：

- 封鎖和低效能。 由於 HTTP 的同步本質，在完成所有內部 HTTP 呼叫前，原始要求不會收到回應。 假設這些呼叫的數目大幅增加，與此同時封鎖了微服務的一個中繼 HTTP 呼叫。 結果是會效能受到影響，整體延展性也會隨著額外 HTTP 要求增加而受到等比級數的影響。

- 結合微服務與 HTTP。 商務微服務不應與其他商務微服務結合。 在理想情況下，它們不應該「知道」其他微服務的存在。 如果您的應用程式如範例中所示依賴結合的微服務，希望達到每項微服務都有自主性幾乎是不可能的。

- 任何一項微服務都會失敗。 如已實作經 HTTP 呼叫連結的微服務鏈結，當任一項微服務失敗時 (它們最終都會失敗)，整個微服務鏈結就會失敗。 微服務型系統應該設計成可持續運作，以及在部分失敗期間能夠運作。 即使您實作的用戶端邏輯使用指數輪詢或斷路器機制重試，HTTP 呼叫鏈結愈複雜，所實作的 HTTP 型失敗策略就愈複雜。

事實上，如果您的內部微服務如所述，是透過建立 HTTP 要求的鏈結進行通訊，則您所擁有整合型應用程式是以處理序通訊機制之間的 HTTP 為基礎，而非以內部處理序通訊機制之間的 HTTP 為基礎，就可能引起爭議。

因此，為了強制執行微服務自主性，並實現較佳的復原功能，您應該盡量少用跨微服務的要求/回應通訊鏈結。 微服務通訊間建議只使用非同步互動，使用非同步訊息型及事件型通訊，或使用獨立於原始 HTTP 要求/回應週期外的 (非同步) HTTP 輪詢。

本指南稍後的[非同步微服務整合強制執行微服務自主性](communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy)和[非同步訊息型通訊](asynchronous-message-based-communication.md)等章節會詳細說明非同步通訊的使用。

## <a name="additional-resources"></a>其他資源

- **CAP 定理** \
  <https://en.wikipedia.org/wiki/CAP_theorem>

- **最終一致性** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **資料一致性入門** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Martin Fowler：CQRS (命令與查詢責任隔離)**  \
  <https://martinfowler.com/bliki/CQRS.html>

- **具體化檢視** \
  <https://docs.microsoft.com/azure/architecture/patterns/materialized-view>

- **Charles Row。ACID vs.BASE：資料庫交易處理的轉換 pH** \
  <https://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/>

- **補償交易** \
  <https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction>

- **Udi Dahan.Service Oriented Composition (服務導向組合)**  \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

>[!div class="step-by-step"]
>[上一頁](logical-versus-physical-architecture.md)
>[下一頁](identify-microservice-domain-model-boundaries.md)
