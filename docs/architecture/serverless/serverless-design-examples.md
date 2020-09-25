---
title: 無伺服器設計範例-無伺服器應用程式
description: 瞭解無伺服器架構支援的各種案例，從排程和以事件為基礎的處理到檔案觸發程式和串流處理。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3aa9b7951fd8f11a65a64c22443de7041aba7d94
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171750"
---
# <a name="serverless-design-examples"></a>無伺服器設計範例

有許多適用于無伺服器的設計模式。 本節將說明一些使用無伺服器的常見案例。 所有範例的共通之處是事件觸發程式和商務邏輯的基本組合。

## <a name="scheduling"></a>排程

排程工作是常見的函式。 下圖顯示沒有適當完整性檢查的舊版資料庫。 資料庫必須定期進行清理。 無伺服器函式會找出不正確資料，並將其清除。 觸發程式是依排程執行程式碼的計時器。

![無伺服器排程](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>命令與查詢責任隔離 (CQRS)

命令與查詢責任隔離 (CQRS) 是一種模式，可提供不同的介面來讀取 (或查詢修改資料的) 資料和作業。 它解決了幾個常見的問題。 在傳統的 Create Read Update Delete (CRUD) 型系統中，從大量的讀取和寫入到相同的資料存放區都可能發生衝突。 鎖定可能會經常發生，並大幅降低讀取的速度。 通常，資料會以數個網域物件的複合呈現，而讀取作業必須結合來自不同實體的資料。

使用 CQRS，讀取可能牽涉到特殊的「壓平合併」實體，以模型化資料的方式來建立資料的模型。 讀取的處理方式不同于其儲存方式。 例如，雖然資料庫可能會將連絡人儲存為具有子地址記錄的標頭記錄，但讀取可能涉及具有標頭和位址屬性的實體。 有多種方法可建立讀取模型。 它可能會從視圖中具體化。 更新作業可以封裝為隔離的事件，然後將更新觸發至兩個不同的模型。 有個別的模型可供讀取和寫入。

![CQRS 範例](./media/cqrs-example.png)

無伺服器可提供隔離的端點來容納 CQRS 模式。 一個無伺服器函式可容納查詢或讀取，而不同的無伺服器函式或一組函式會處理更新作業。 無伺服器函式也可以負責讓讀取模型保持在最新狀態，並可由資料庫的 [變更](/azure/cosmos-db/change-feed)摘要觸發。 前端開發已簡化，以連接到必要的端點。 事件的處理會在後端處理。 這種模型也適用于大型專案，因為不同的小組可能會處理不同的作業。

## <a name="event-based-processing"></a>以事件為基礎的處理

在以訊息為基礎的系統中，事件通常會收集在佇列或發行者/訂閱者主題中，以進行處理。 這些事件可以觸發無伺服器函式，以執行部分商務邏輯。 以事件為基礎的處理是事件來源的系統範例。 引發「事件」以將工作標示為已完成。 由事件觸發的無伺服器函式會更新適當的資料庫檔案。 第二個無伺服器函式可能會使用事件來更新系統的讀取模型。 [Azure 事件方格](/azure/event-grid/overview) 可讓您將事件與功能整合為訂閱者。

> 事件是告知性訊息。 如需詳細資訊，請參閱 [事件來源模式](/azure/architecture/patterns/event-sourcing)。

## <a name="file-triggers-and-transformations"></a>檔案觸發程式和轉換

 (ETL) 的解壓縮、轉換和載入是常見的商務功能。 無伺服器是 ETL 的絕佳解決方案，因為它可讓程式碼觸發為管線的一部分。 個別的程式碼元件可以處理各種層面。 一個無伺服器函式可能會下載檔案，另一個則會套用轉換，另一個則會載入資料。 程式碼可以獨立測試和部署，讓您更容易維護及擴充所需的位置。

![無伺服器檔案觸發程式和轉換](./media/serverless-file-triggers.png)

在此圖中，「非經常性儲存體」提供在 [Azure 串流分析](/azure/stream-analytics)中剖析的資料。 資料流程中遇到的任何問題都會觸發 Azure 函式以處理異常。

## <a name="asynchronous-background-processing-and-messaging"></a>非同步背景處理和訊息

非同步通訊和背景處理可讓應用程式啟動進程，而不需要等待。 非同步處理的範例是 OCR 應用程式。 提交影像並排入佇列以進行處理。 掃描影像以解壓縮文字可能需要一些時間，一旦完成，就會傳送通知。 無伺服器可以處理此案例中的調用和結果。

## <a name="web-apps-and-apis"></a>Web Apps 和 API

無伺服器的常見案例是多層式應用程式，最常見的是 UI 層是 web 應用程式。 最受歡迎的單一頁面應用程式 (SPA) 最近 surged。 SPA 應用程式會轉譯單一頁面，然後依賴 API 呼叫和傳回的資料來動態呈現新的 UI，而不需要重載整頁。 用戶端轉譯提供更快、更快速的應用程式給終端使用者。

HTTP 呼叫所觸發的無伺服器端點可以用來處理 API 要求。 例如，ad 服務公司可能會以使用者設定檔資訊來呼叫無伺服器功能，以要求自訂廣告。 無伺服器函式會傳回自訂廣告，而網頁則會呈現該自訂廣告。

![無伺服器 web API](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Data Pipeline

無伺服器函數可用來加速資料管線。 在此範例中，檔案會觸發函式，將 CSV 檔案中的資料轉譯成資料表中的資料列。 組織的資料表可讓 Power BI 的儀表板向終端使用者呈現分析。

![無伺服器資料管線](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>串流處理

裝置和感應器通常會產生必須即時處理的資料流程。 有許多技術可從 [事件中樞](/azure/event-hubs/event-hubs-what-is-event-hubs) 和 [IoT 中樞](/azure/iot-hub) 將訊息和串流處理至 [服務匯流排](/azure/service-bus)。 不論是何種傳輸，無伺服器是一種理想的機制，可處理訊息和資料串流。 無伺服器可以快速調整以符合大量資料的需求。 無伺服器程式碼可以套用商務邏輯，以使用結構化格式來剖析資料和輸出，以進行動作和分析。

![無伺服器串流處理](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>API 閘道

API 閘道會為用戶端提供單一進入點，然後以智慧方式將要求路由傳送至後端服務。 管理大型的服務集是很有用的。 它也可以輕鬆地將用戶端連接至不同的環境，以處理版本控制並簡化開發。 無伺服器可以處理個別微服務的後端調整，同時透過 API 閘道呈現單一前端。

![無伺服器 API 閘道](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>建議的資源

- [事件格線](/azure/event-grid/overview)
- [Azure IoT 中心](/azure/iot-hub)
- [分散式資料管理的挑戰和解決方案](../microservices/architect-microservice-container-applications/distributed-data-management.md)
- [設計微服務：識別微服務界限](/azure/architecture/microservices/microservice-boundaries)
- [事件中樞](/azure/event-hubs/event-hubs-what-is-event-hubs)
- [事件來源模式](/azure/architecture/patterns/event-sourcing)
- [實作斷路器模式](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
- [IoT 中心](/azure/iot-hub)
- [服務匯流排](/azure/service-bus)
- [使用 Azure Cosmos DB 中的變更摘要支援](/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[上一個](serverless-architecture-considerations.md) 
>[下一步](azure-serverless-platform.md)
