---
title: 無伺服器設計範例-無伺服器應用程式
description: 了解各種不同的無伺服器架構，排程和事件為基礎的處理，檔案觸發程序和資料流處理序所支援的案例。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: d165746ff2f03b0edc59a9284052323a0c1fd05b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784385"
---
# <a name="serverless-design-examples"></a>無伺服器設計範例

有許多的設計模式所存在的無伺服器。 本節會擷取使用無伺服器的一些常見案例。 功能的所有範例有共同的事件觸發程序和商務邏輯的基本組合。

## <a name="scheduling"></a>排程

排程工作是常見的函式。 下圖顯示使用舊版的資料庫沒有適當的完整性檢查。 資料庫必須定期清除。 無伺服器函式會尋找無效的資料，並清除它。 觸發程序是一個計時器，定期執行的程式碼。

![無伺服器的排程](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>命令與查詢職責分離 (CQRS)

命令與查詢責任隔離 (CQRS) 是一種模式，提供不同的介面，用於讀取 （或查詢） 的資料和修改資料的作業。 它解決一些常見的問題。 在傳統的建立讀取更新刪除 (CRUD) 型系統，可能會發生衝突從大量的讀取和寫入相同的資料存放區。 鎖定可能會經常發生，並大幅減慢讀取。 通常，資料會顯示為複合的數個領域物件和讀取的作業必須結合來自不同實體的資料。

使用 CQRS，讀取可能會牽涉到特殊的 「 扁平化 」 實體模型資料的方式加以使用。 在讀取處理方式不同於儲存的方式。 比方說，雖然資料庫可能會儲存為子位址記錄的標頭記錄的連絡人，讀取可以讓具有標頭和位址屬性的實體。 有各種方法來建立讀取的模型。 它可能會從檢視具體化。 更新作業可以封裝為獨立的事件，然後更新觸發至兩個不同的模型中。 用於讀取和寫入，存在不同的模型。

![CQRS 範例](./media/cqrs-example.png)

無伺服器可以提供已隔離的端點，以符合 CQRS 模式。 一個無伺服器函式適用於查詢或讀取，並不同的無伺服器函式或一組功能來處理更新作業。 無伺服器函式可能也會負責確保讀取的模型的最新狀態，並可由資料庫的觸發[變更摘要](https://docs.microsoft.com/azure/cosmos-db/change-feed)。 前端開發會簡化，以連接到必要的端點。 在後端處理事件的處理。 因為不同的團隊可能會解決不同的作業，此模型也會調整適用於大型專案。

## <a name="event-based-processing"></a>事件為基礎的處理

在訊息為基礎的系統中，通常會在佇列或執行時所依據的主題發行者/訂閱者收集事件。 這些事件可以觸發要執行的商務邏輯的無伺服器函式。 事件為基礎的範例是處理的來自事件的系統。 「 事件 」 會將標示為已完成的工作中引發。 事件所觸發的無伺服器函式會更新適當的資料庫文件。 第二個的無伺服器函式可能會使用事件來更新系統的讀取的模型。 [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)可用來為訂閱者的函式與整合事件。

> 事件是告知性訊息。 如需詳細資訊，請參閱 <<c0> [ 事件來源模式](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)。

## <a name="file-triggers-and-transformations"></a>檔案觸發程序和轉換

擷取、 轉換和載入 (ETL) 是常見的商務功能。 無伺服器是很棒的解決方案 etl 因為它可讓程式碼，以觸發管線的一部分。 個別的程式碼元件可以處理各種層面。 一個無伺服器函式可能會下載檔案、 另一個適用於轉換，和另一個載入資料。 程式碼來測試和部署獨立，更容易維護及調整在需要時。

![無伺服器的檔案觸發程序和轉換](./media/serverless-file-triggers.png)

在圖表中，「 非經常性儲存體 」 提供剖析中的資料[Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics)。 資料流中遇到任何問題會觸發 Azure Function 處理異常。

## <a name="asynchronous-background-processing-and-messaging"></a>非同步背景處理和傳訊

非同步傳訊和背景處理可讓應用程式，以開始程序，而不必等候。 非同步處理的範例是 OCR 應用程式。 提交映像，並已排入佇列進行處理。 掃描來擷取文字的映像可能需要時間，和一旦完成通知會傳送。 無伺服器可以處理引動過程，在此案例中的結果。

## <a name="web-apps-and-apis"></a>Web apps 及 Api

常見案例的無伺服器是多層式架構應用程式，最常見的 UI 層所在的 web 應用程式。 具有最近湧現大受歡迎的單一頁面應用程式 (SPA)。 SPA 應用程式呈現單一的頁面，然後依賴動態呈現而不重新載入完整頁面的 新的 UI，API 呼叫而傳回的資料。 用戶端轉譯提供使用者更快、 更靈敏回應應用程式。

HTTP 呼叫所觸發的無伺服器端點可用來處理 API 要求。 例如，ad 服務的公司可能會呼叫要求自訂的廣告的使用者設定檔資訊的無伺服器函式。 無伺服器函式會傳回自訂 ad 和轉譯網頁。

![無伺服器的 web API](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>資料管線

無伺服器函式可用來加速資料管線。 在此範例中，檔案會觸發的函式，將 CSV 檔案將資料表中的資料列中的資料轉譯。 組織的資料表可讓 Power BI 儀表板來呈現給使用者的分析。

![無伺服器的資料管線](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Stream 處理

裝置與感應器通常必須處理的資料流的即時產生。 有數種技術，可以擷取訊息和來自資料流[事件中樞](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)並[IoT 中樞](https://docs.microsoft.com/azure/iot-hub)來[服務匯流排](https://docs.microsoft.com/azure/service-bus)。 不論傳輸，無伺服器是理想的機制，它們會在處理訊息和資料流。 無伺服器可快速調整以滿足需求的大型資料磁碟區。 無伺服器程式碼可以套用商務邏輯來剖析的資料和動作和分析的結構化格式的輸出。

![無伺服器串流處理](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>API 閘道

API 閘道的用戶端提供單一進入點，並以智慧方式將要求路由到後端服務。 您最好管理大量的服務。 它也可以處理版本控制，並輕鬆地將用戶端連接至不同的環境，簡化開發。 無伺服器可以處理後端調整個別的微服務，同時呈現單一的後端，透過 API 閘道。

![無伺服器 API 閘道](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>建議的資源

* [Azure 事件格線](https://docs.microsoft.com/azure/event-grid/overview)
* [Azure IoT 中樞](https://docs.microsoft.com/azure/iot-hub)
* [分散式資料管理的挑戰和解決方案](../microservices-architecture/architect-microservice-container-applications/distributed-data-management.md)
* [設計微服務： 識別微服務界限](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
* [事件中樞](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
* [事件溯源模式](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
* [實作斷路器模式](../microservices-architecture/implement-resilient-applications/implement-circuit-breaker-pattern.md)
* [IoT 中樞](https://docs.microsoft.com/azure/iot-hub)
* [服務匯流排](https://docs.microsoft.com/azure/service-bus)
* [使用中的變更摘要支援 Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[上一頁](serverless-architecture-considerations.md)
>[下一頁](azure-serverless-platform.md)
