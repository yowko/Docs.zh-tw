---
title: 服務到服務通訊
description: 瞭解後端雲端雲端微服務如何與其他後端微服務進行通信。
author: robvet
ms.date: 09/09/2019
ms.openlocfilehash: 926be3c2eb4513c89ebcd1f31dceb7d58639dc6f
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523554"
---
# <a name="service-to-service-communication"></a>服務到服務通訊

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

從前端用戶端,我們現在處理後端微服務相互通信。

構建雲本機應用程式時,您需要對後端服務如何相互通信敏感。 理想情況下,服務間通信越少越好。 但是,由於後端服務通常相互依賴來完成操作,因此並非始終能夠避免。

實施跨服務通信的方法被廣泛接受。 *通信交互的類型*通常將決定最佳方法。

請考慮以下互動型態:

- *查詢*– 當呼叫微服務需要來自被呼叫的微服務的回應時,例如「嘿,給我給定客戶 ID 的買方資訊。

- *命令*– 當呼叫微服務需要另一個微服務來執行操作,但不需要回應時,例如「嘿,只需發出此訂單」。

- *事件*— 當稱為發佈伺服器的微服務引發狀態已更改或已發生操作的事件時。 其他微服務(稱為訂閱者)有興趣,可以對事件做出適當的反應。 發行者和訂閱者彼此不知道。

在執行需要跨服務交互的操作時,微服務系統通常使用這些交互類型的組合。 讓我們仔細看看每個以及如何實現它們。

## <a name="queries"></a>查詢

很多時候,一個微服務可能需要*查詢*另一個微服務,需要立即回應才能完成操作。 購物籃微服務可能需要產品資訊和價格才能將商品添加到其購物籃中。 實現查詢操作的方法有很多種。

### <a name="requestresponse-messaging"></a>要求/回應傳訊

實現此方案的一個選項是調用後端微服務,以便直接向需要查詢的微服務發出 HTTP 請求,如圖 4-8 所示。

![直接 HTTP 通訊](./media/direct-http-communication.png)

**圖4-8**。 直接 HTTP 通訊

雖然微服務之間的直接 HTTP 調用執行起來相對簡單,但應注意將這種做法降至最低。 要啟動,這些調用始終是*同步*的,並將阻止操作,直到返回結果或請求超時。 曾經自成一體的獨立服務能夠獨立發展並頻繁部署,現在卻相互耦合。 隨著微服務之間的耦合增加,其體系結構優勢逐漸降低。

執行對另一個微服務進行單個直接 HTTP 調用的不常見請求對於某些系統可能是可以接受的。 但是,不建議調用對多個微服務直接 HTTP 調用的高容量調用。 它們會增加延遲,並產生負面影響系統的性能、可擴充性和可用性。 更糟糕的是,一系列直接 HTTP 通信可能導致同步微服務調用的深層和複雜鏈,如圖 4-9 所示:

![連結 HTTP 查詢](./media/chaining-http-queries.png)

**圖4-9**。 連結 HTTP 查詢

您當然可以想像前一張圖片中顯示的設計中的風險。 如果步驟\#3 失敗,會發生什麼情況? 還是步驟\#8 失敗? 你如何恢復? 如果步驟\#6 由於基礎服務繁忙而速度較慢,該怎麼辦? 你如何繼續? 即使所有操作都正常工作,也想想此調用產生的延遲,即每個步驟的延遲總和。

上圖中大量耦合表明,服務沒有進行最佳建模。 團隊應該重新審視他們的設計。

### <a name="materialized-view-pattern"></a>具體化檢視模式

刪除微服務耦合的一個常用選項是[一個影像](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)的檢視模式 。 使用此模式,微服務存儲其自己的本地、非規範化數據副本,這些副本由其他服務擁有。 它維護自己的本地數據副本,而不是查詢產品目錄和定價微服務的購物籃微服務。 此模式消除了不必要的耦合,提高了可靠性和響應時間。 整個操作在單個進程內執行。 我們在第 5 章中探討此模式和其他數據問題。

### <a name="service-aggregator-pattern"></a>服務集合模式模式

消除微服務到微服務耦合的另一個選項是[聚合器微服務](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/),如圖 4-10 中紫色所示。

![彙總器服務](./media/aggregator-service.png)

**圖 4-10**： 聚合器微服務

該模式隔離了對多個後端微服務進行調用的操作,將其邏輯集中到專用微服務中。  上圖中的紫色簽出聚合器微服務協調簽出操作的工作流。 它包括按順序順序對多個後端微服務的調用。 來自工作流的數據將聚合併返回到調用方。 雖然它仍然實現直接 HTTP 調用,但聚合器微服務減少了後端微服務之間的直接依賴關係。

### <a name="requestreply-pattern"></a>請求/回覆模式

分離同步 HTTP 訊息的另一種方法是[請求回覆模式](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html),它使用佇列通信。 使用佇列的通信始終是單向通道,生產者發送消息並接收消費者。 使用此模式,將實現請求佇列和響應佇列,如圖 4-11 所示。

![要求-回覆模式](./media/request-reply-pattern.png)

**圖 4-11**： 要求-回覆模式

在這裡,消息生成器創建一個基於查詢的消息,其中包含唯一的相關性 ID 並將其放入請求佇列中。 使用服務取消消息排隊,處理消息,並將回應放在具有相同關聯 ID 的回應佇列中。 生產者服務取消消息的排隊,將其與相關 ID 匹配並繼續處理。 我們將在下一節中詳細介紹佇列。

## <a name="commands"></a>命令

另一種類型的通訊互動是*指令*。 微服務可能需要另一個微服務來執行操作。 訂購微服務可能需要運輸微服務為已批准的訂單創建貨件。 在圖 4-12 中,一個稱為"生產者"的微服務向另一個微服務"消費者"發送消息,命令它執行某些操作。

![命令與佇列的互動](./media/command-interaction-with-queue.png)

**圖 4-12**. 命令與佇列的互動

通常,生產者不需要回應,可能會*觸發和忘記*消息。 如果需要回復,使用者將發送單獨的消息回另一個通道上的生產者。 命令消息最好使用消息佇列非同步發送。 由輕量級消息代理支援。 在上圖中,請注意佇列如何分離和分離兩個服務。

消息佇列是一種中間構造,生產者和使用者通過它傳遞消息。 佇列實現非同步點對點訊息傳遞模式。 生產者知道需要發送命令的位置並相應地路由。 佇列保證消息由從通道讀取的消費者實例之一處理。 在這種情況下,生產者或消費者服務可以橫向擴展,而不會影響其他服務。 同樣,技術在兩側可能各不相同,這意味著我們可能有一個 JAVA 微服務,稱為[Golang](https://golang.org)微服務。

在第 1 章中,我們討論了*支援服務*。 支援服務是雲原生系統所依賴的輔助資源。 消息佇列是支援服務。 Azure 雲支援兩種類型的消息佇列,雲原生系統可用於實現命令消息傳遞:Azure 儲存佇列和 Azure 服務總線佇列。

### <a name="azure-storage-queues"></a>Azure 儲存體佇列

Azure 儲存佇列提供快速、經濟實惠並由 Azure 存儲帳戶提供支援的簡單佇列基礎結構。

[Azure 儲存佇列](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)具有基於 REST 的排隊機制,具有可靠且持久的消息傳遞。 它們提供最少的功能集,但價格低廉,並存儲數百萬條消息。 其容量範圍可達 500 TB。 一條消息的大小可達 64 KB。

您可以使用 HTTP 或 HTTPS 透過經過身份驗證的通話從世界任何地方存取訊息。 存儲佇列可以擴展到大量併發用戶端,以處理流量峰值。

也就是說,服務存在限制:

- 消息順序不保證。

- 消息只能保留七天,然後才能自動刪除。

- 不支持狀態管理、重複檢測或事務不可用。

圖 4-13 顯示了 Azure 儲存佇列的層次結構。

![儲存佇列層次結構](./media/storage-queue-hierarchy.png)

**圖 4-13**. 儲存佇列層次結構

在上圖中,請注意儲存佇列如何將其消息存儲在基礎 Azure 存儲帳戶中。

對於開發人員,Microsoft 提供了多個用戶端和伺服器端庫,用於存儲佇列處理。 大多數主要平臺都受支援,包括 .NET、JAVA、JAVAScript、Ruby、Python 和 Go。 開發人員絕不應直接與這些庫通信。 這樣做會將微服務代碼與 Azure 儲存佇列服務緊密耦合。 最好隔離 API 的實現詳細資訊。 引入中介層或中間 API,該層公開泛型操作並封裝具體庫。 這種鬆散的耦合使您能夠將一個佇列服務交換到另一個佇列服務,而無需更改主線服務代碼。

Azure 儲存佇列是在雲本機應用程式中實現命令消息傳遞的經濟選擇。 特別是當佇列大小超過 80 GB 時,或者一個簡單的功能集是可以接受的。 您只為郵件的存儲付費;沒有固定的小時費用。

### <a name="azure-service-bus-queues"></a>Azure 服務匯流排佇列

對於更複雜的消息傳遞要求,請考慮 Azure 服務總線佇列。

[Azure 服務匯流線](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)位於強大的訊息基礎結構之上,支援*中轉訊息傳遞模型*。 消息可靠地存儲在代理(佇列)中,直到消費者收到消息。 佇列保證先到/先出 (FIFO) 消息傳遞,遵守消息添加到佇列的順序。

消息的大小可以大得多,高達 256 KB。 消息在佇列中保留無限時間。 服務總線不僅支援基於 HTTP 的調用,而且還提供對[AMPQ 協定的](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-amqp-overview)完全支援。 AMPQ 是跨供應商的開放標準,支援二進位協定和更高可靠性度。

服務匯流排提供豐富的功能,包括[事務支援](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions)與[重覆偵測功能](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection)。 佇列保證每條消息"最多傳遞一次」。 它會自動丟棄已發送的消息。 如果生產者有疑問,它可以重新發送相同的消息,並且服務總線保證只處理一個副本。 重複檢測使您不必構建其他基礎結構管道。

另外兩個企業功能是分區和會話。 傳統的服務總線佇列由單一消息代理處理並存儲在單一消息儲存中。 但是,[服務總線分區](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning)將佇列分散到多個消息代理和消息存儲中。 總體輸送量不再受單個消息代理或消息存儲的性能的限制。 消息存儲的臨時中斷不會使分區佇列不可用。

[服務總線會話](https://codingcanvas.com/azure-service-bus-sessions/)提供了一種組相關消息的方法。 想像一下工作流方案,其中消息必須一起處理,操作在結束時完成。 要利用此優勢,必須為佇列顯式啟用會話,並且每個相關消息必須包含相同的會話 ID。

但是,有一些重要的警告:服務總線佇列大小限制為 80 GB,這比商店佇列中可用的小得多。 此外,服務總線佇列會產生基本成本和每次操作的費用。

圖 4-14 概述了服務總線佇列的高級體系結構。

![服務匯流排佇列](./media/service-bus-queue.png)

**圖 4-14**. 服務匯流排佇列

在上圖中,請注意點對點關係。 同一提供程式的兩個實例正在將消息排入單個服務總線佇列中。 每條消息僅由右側三個使用者實例中的一個使用。 接下來,我們將討論如何在不同消費者都對同一消息感興趣的地方實現消息傳遞。

## <a name="events"></a>事件

消息佇列是實現通信的有效方法,其中生產者可以異步向消費者發送消息。 但是,當*許多不同的消費者對*同一消息感興趣時,會發生什麼情況? 每個消費者的專用消息佇列不會很好地擴展,並且將變得難以管理。

為了解決這個問題,我們轉到第三種類型的消息交互,*事件*。 一個微服務宣佈已發生操作。 其他微服務(如果有興趣)對操作或事件做出反應。

事件是一個兩步過程。 對於給定的狀態更改,微服務將事件發佈到消息代理,使其可用於任何其他感興趣的微服務。 通過訂閱消息代理中的事件來通知感興趣的微服務。 您可以使用[「 發布/訂閱](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber)模式」 來實現[此事件的通訊](https://docs.microsoft.com/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications)。

圖 4-15 顯示了購物籃微服務發佈事件,其中另外兩個微服務訂閱了它。

![事件驅動訊息](./media/event-driven-messaging.png)

**圖 4-15**： 事件驅動訊息

請注意位於通信通道中間*的事件總線*元件。 它是一個自定義類,它封裝消息代理並將其與基礎應用程式分離。 訂購和庫存微服務在彼此不知情的情況下獨立操作事件,也無需購物籃微服務。 當註冊事件發佈到事件總線時,它們會對它執行操作。

通過事件,我們從排隊技術轉向*主題*。 [主題](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)類似於佇列,但支援一對多消息傳遞模式。 一個微服務發佈消息。 多個訂閱微服務可以選擇接收該消息並採取行動。 圖 4-16 顯示了主題體系結構。

![主題架構結構](./media/topic-architecture.png)

**圖 4-16**： 主題架構結構

在上圖中,發佈者向主題發送消息。 最後,訂閱者會從訂閱接收消息。 在中間,主題根據一組*規則*將消息轉發到訂閱,這些規則顯示在深藍色框中。 規則充當將特定消息轉發到訂閱的篩選器。 此處,將"創建訂單"事件發送到訂閱\#1\#和訂閱 3,但不會\#發送到訂閱 2。 群組訂單完成"事件將發送到訂閱\#2\#和訂閱 3。

Azure 雲支援兩種不同的主題服務:Azure 服務總線主題和 Azure 事件網格。

### <a name="azure-service-bus-topics"></a>Azure 服務匯流排主題

坐在 Azure 服務總線佇列的相同強大代理訊息模型的頂部是 Azure[服務總線主題](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions)。 主題可以接收來自多個獨立發佈者的消息,並向多達 2,000 個訂閱者發送消息。 訂閱可以在運行時動態添加或刪除,而無需停止系統或重新建立主題。

Azure 服務匯流排排列中的許多進階功能也可用於主題,包括[重複偵測](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection)與[事務支援](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions)。 默認情況下,服務總線主題由單個消息代理處理並存儲在單個消息存儲中。 但是,[服務總線分區](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning)通過將主題傳播到許多消息代理和消息存儲中來擴展主題。

[計劃郵件傳遞](https://docs.microsoft.com/azure/service-bus-messaging/message-sequencing)標記具有特定時間處理的郵件。 在此之前,該消息不會顯示在主題中。 [消息延遲](https://docs.microsoft.com/azure/service-bus-messaging/message-deferral)使您能夠將郵件的檢索推遲到以後。 這兩種情況通常用於工作流處理方案,其中操作按特定順序處理。 您可以推遲處理已接收的消息,直到完成之前的工作。

服務總線主題是一種強大且經過驗證的技術,可在雲本機系統中啟用發佈/訂閱通信。

### <a name="azure-event-grid"></a>Azure Event Grid

雖然 Azure 服務總線是經過戰鬥測試的消息代理,具有一整套企業功能,但[Azure 事件網格](https://docs.microsoft.com/azure/event-grid/overview)是塊上的新孩子。

乍一看,事件網格可能只是另一個基於主題的郵件系統。 然而,它在許多方面是不同的。 它專注於事件驅動的工作負載,支援即時事件處理、深度 Azure 整合和開放平臺 - 所有這些都位於無伺服器基礎架構上。 它專為現代雲原生和無伺服器應用程式而設計

作為集中*式事件背板*或管道,事件網格對 Azure 資源內的事件和您自己的服務做出反應。

事件通知發佈到事件網格主題,而事件網格主題又將每個事件路由到訂閱。 訂閱伺服器對應到訂閱並使用事件。 與服務總線一樣,事件網格支援*篩選的訂閱者模型*,其中訂閱集其希望接收的事件的規則。 事件網格提供快速輸送量,保證每秒 1000 萬個事件,實現近乎即時的傳遞 -遠遠超過 Azure 服務總線所能生成的。

事件網格的一個最佳亮點是它深入集成到 Azure 基礎結構的結構中。 Azure 資源(如Cosmos DB)可以直接將內建事件發佈到其他感興趣的Azure資源,而無需自定義代碼。 事件網格可以從 Azure 訂閱、資源組或服務發佈事件,使開發人員能夠細粒度地控制雲資源的生命週期。 但是,事件網格並不僅限於 Azure。 它是一個開放的平臺,可以使用從應用程式或第三方服務發佈的自定義 HTTP 事件,並將事件路由到外部訂閱者。

從 Azure 資源發佈和訂閱本機事件時,不需要編碼。 通過簡單的配置,您可以利用主題和訂閱的內建管道將事件從一個 Azure 資源整合到另一個 Azure 資源。 圖 4-17 顯示了事件網格的剖析。

![事件網格解剖](./media/event-grid-anatomy.png)

**圖 4-17**： 事件網格解剖

事件格線與服務匯流線之間的主要區別是基礎*訊息交換模式*。

服務總線實現了較舊的樣式*拉取模型*,其中下游訂閱者主動輪詢主題訂閱的新消息。 有利的一面是,此方法使訂閱者能夠完全控制其處理消息的速度。 它控制在任意給定時間處理的時間和消息數。 未讀郵件將保留在訂閱中,直到處理。 一個重大缺點是生成事件的時間與將該消息拉至訂閱者進行處理的輪詢操作之間的延遲。 此外,下一個事件的恆定輪詢開銷會消耗資源和資金。

但是,事件網格是不同的。 它實現了一個*推送模型*,其中事件在接收時發送到事件處理程式,提供近乎即時的事件傳遞。 它還降低了成本,因為服務僅在需要使用事件時觸發 –而不是與輪詢那樣持續。 也就是說,事件處理程序必須處理傳入負載並提供限制機制,以防止自身不堪重負。 許多使用這些事件的 Azure 服務(如 Azure 函數和邏輯應用)提供自動自動縮放功能來處理增加的負載。  

事件網格是一個完全託管的無伺服器雲服務。 它根據您的流量動態擴展,僅針對實際使用方式收費,而不是預購買容量。 每月的前 100,000 個操作是免費的 - 操作定義為事件入口(傳入事件通知)、訂閱傳遞嘗試、管理調用和按主題篩選。 憑藉 99.99% 的可用性,EventGrid 保證在 24 小時內交付事件,並內置重試功能,以不成功交付。 未傳遞的消息可以移動到"死信"佇列以進行解析。  與 Azure 服務總線不同,事件網格經過最佳化以獲得快速性能,不支援有序訊息傳遞、事務和會話等功能。

### <a name="streaming-messages-in-the-azure-cloud"></a>在 Azure 雲中流式傳輸訊息

Azure 服務總線和事件網格為公開單個離散事件(如新文檔)的應用程式提供了極大的支援,這些事件已插入到Cosmos DB中。 但是,如果您的雲原生系統需要處理*一系列相關事件*,該怎麼辦? [事件流](https://docs.microsoft.com/archive/msdn-magazine/2015/february/microsoft-azure-the-rise-of-event-stream-oriented-systems)更為複雜。 它們通常是按時間順序排列的,是相互關聯的,必須作為一個組進行處理。

[Azure 事件中心](https://azure.microsoft.com/services/event-hubs/)是一個數據流平臺和事件引入服務,用於收集、轉換和存儲事件。 它經過微調以捕獲流數據,例如從遙測上下文中發出的連續事件通知。 該服務具有高度可擴充性,每秒可以儲存[和處理數百萬個事件](https://docs.microsoft.com/azure/event-hubs/event-hubs-about)。 如圖 4-18 所示,它通常是事件管道的前門,將引入流與事件消耗分離。

![Azure 事件中樞](./media/azure-event-hub.png)

**圖 4-18**. Azure 事件中樞

事件中心支援低延遲和可配置的時間保留。 與佇列和主題不同,事件中心在使用者讀取事件數據後保留事件數據。 此功能使內部和外部的其他數據分析服務能夠重播數據以進行進一步分析。 存儲在事件中心的事件僅在保留期到期時刪除,默認情況下為一天,但可配置。

事件中心支援常見的事件發佈協定,包括 HTTPS 和 AMQP。 它還支援卡夫卡1.0。 [現有的 Kafka 應用程式可以使用](https://docs.microsoft.com/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview)Kafka 協定與事件中心通信,為管理大型 Kafka 群集提供了替代方案。 許多開源雲原生系統都擁抱卡夫卡。

事件中心通過[分區消費者模型](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)實現消息流,其中每個消費者唯讀取消息流的特定子集或分區。 此模式支援大幅的水平擴充來處理事件，並提供佇列和主題所沒有的其他串流功能。 資料分割是經過排序且保存在事件中樞內的事件序列。 當較新的事件到達時,它們將添加到此序列的末尾。圖 4-19 顯示了事件中心中的分區。

![事件中心分割區](./media/event-hub-partitioning.png)

**圖 4-19**. 事件中心分割區

每個使用者組讀取消息流的子集或分區不是從同一資源讀取。

對於必須流式傳輸大量事件的雲原生應用程式,Azure 事件中心可以是一個強大且經濟實惠的解決方案。

>[!div class="step-by-step"]
>[前一個](front-end-communication.md)
>[下一個](grpc.md)
