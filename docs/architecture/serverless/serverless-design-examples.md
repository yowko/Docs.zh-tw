---
title: 無伺服器設計範例-無伺服器應用程式
description: 瞭解無伺服器架構支援的各種案例, 從排程和以事件為基礎的處理到檔案觸發程式和串流處理。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 096dce6ef23bde5ef9c6ca65769f4dcc7e08a904
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577191"
---
# <a name="serverless-design-examples"></a>無伺服器設計範例

無伺服器有許多設計模式存在。 本節將說明一些使用無伺服器的常見案例。 所有的範例都共通, 是事件觸發程式和商務邏輯的基本組合。

## <a name="scheduling"></a>功能

排程工作是常見的函式。 下圖顯示沒有適當完整性檢查的舊版資料庫。 必須定期清除資料庫。 無伺服器函式會尋找不正確資料, 並將其清除。 觸發程式是在排程上執行程式碼的計時器。

![無伺服器排程](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>命令與查詢責任隔離 (CQRS)

命令與查詢責任隔離 (CQRS) 是一種模式, 可提供不同的介面來讀取 (或查詢) 資料和修改資料的作業。 它解決了幾個常見的問題。 在傳統的建立讀取更新刪除 (CRUD) 型系統中, 可能會從讀取和寫入相同資料存放區的大量磁片產生衝突。 鎖定可能經常發生, 而且會大幅降低讀取速度。 通常, 資料會以數個網域物件的複合形式呈現, 而且讀取作業必須結合來自不同實體的資料。

使用 CQRS 時, 讀取可能牽涉到特別的「簡維」實體, 它會以取用的方式建立資料模型。 讀取的處理方式不同于它的儲存方式。 例如, 雖然資料庫可能會將連絡人儲存為具有子地址記錄的標頭記錄, 但讀取可能牽涉到具有標頭和位址屬性的實體。 建立讀取模型的方法有很多種。 它可能會從 views 具體化。 更新作業可以封裝為隔離的事件, 然後觸發兩個不同模型的更新。 有不同的模型可供讀取和寫入。

![CQRS 範例](./media/cqrs-example.png)

無伺服器可以藉由提供隔離的端點來容納 CQRS 模式。 一個無伺服器函式可容納查詢或讀取, 而不同的無伺服器函式或一組函式會處理更新作業。 無伺服器函式可能也會負責讓讀取模型保持在最新狀態, 而且可以由資料庫的[變更](https://docs.microsoft.com/azure/cosmos-db/change-feed)摘要觸發。 前端開發已簡化, 可連接到必要的端點。 事件的處理會在後端處理。 此模型也適用于大型專案, 因為不同的小組可能會在不同的作業上運作。

## <a name="event-based-processing"></a>以事件為基礎的處理

在以訊息為基礎的系統中, 通常會在佇列或發行者/訂閱者主題中收集事件, 以進行動作。 這些事件可以觸發無伺服器函式來執行商務邏輯。 事件型處理的範例是事件來源系統。 會引發「事件」以將工作標示為完成。 由事件觸發的無伺服器函式會更新適當的資料庫檔案。 第二個無伺服器函數可能會使用事件來更新系統的讀取模型。 [Azure 事件方格](https://docs.microsoft.com/azure/event-grid/overview)提供了一種方式, 可將事件與功能整合為訂閱者。

> 事件是參考訊息。 如需詳細資訊, 請參閱[事件來源模式](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)。

## <a name="file-triggers-and-transformations"></a>檔案觸發程式和轉換

「解壓縮」、「轉換」和「載入」 (ETL) 是常見的商務功能。 無伺服器是 ETL 的絕佳解決方案, 因為它可讓程式碼觸發為管線的一部分。 個別的程式碼元件可以處理各種層面。 一個無伺服器函式可能會下載檔案, 另一個則套用轉換, 而另一個則會載入資料。 程式碼可以單獨進行測試和部署, 讓您更容易維護和調整所需的位置。

![無伺服器檔案觸發程式和轉換](./media/serverless-file-triggers.png)

在圖表中, 「非經常性存取儲存體」會提供在[Azure 串流分析](https://docs.microsoft.com/azure/stream-analytics)中剖析的資料。 資料流程中發生的任何問題都會觸發 Azure 函式來處理異常。

## <a name="asynchronous-background-processing-and-messaging"></a>非同步背景處理和訊息

非同步訊息和背景處理可讓應用程式啟動進程, 而不需要等待。 非同步處理的範例是 OCR 應用程式。 提交影像並將其排入佇列進行處理。 掃描影像以解壓縮文字可能需要一些時間, 一旦完成後, 就會傳送通知。 無伺服器可以在此案例中處理調用和結果。

## <a name="web-apps-and-apis"></a>Web 應用程式和 Api

無伺服器的熱門案例是多層式架構應用程式, 最常見的是 UI 層是 web 應用程式。 單一頁面應用程式 (SPA) 最熱門的 surged 最近。 SPA 應用程式會轉譯單一頁面, 然後依賴 API 呼叫和傳回的資料, 以動態方式呈現新的 UI, 而不需要重載整頁。 用戶端轉譯提供更快、更快速的應用程式給終端使用者。

HTTP 呼叫所觸發的無伺服器端點可以用來處理 API 要求。 例如, ad 服務公司可能會呼叫具有使用者設定檔資訊的無伺服器功能, 以要求自訂廣告。 無伺服器函式會傳回自訂廣告, 而網頁會呈現該 ad。

![無伺服器 Web API](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>資料管線

無伺服器函式可以用來加速資料管線。 在此範例中, 檔案會觸發函式, 將 CSV 檔案中的資料轉譯成資料表中的資料列。 [已組織] 資料表可讓 Power BI 儀表板向使用者呈現分析。

![無伺服器資料管線](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>串流處理

裝置和感應器通常會產生必須即時處理的資料流程。 有一些技術可以從[事件中樞](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)中捕獲訊息和串流, 並[IoT 中樞](https://docs.microsoft.com/azure/iot-hub)至[服務匯流排](https://docs.microsoft.com/azure/service-bus)。 無論傳輸為何, 無伺服器是一種理想的機制, 用來處理訊息和資料串流。 無伺服器可以快速調整以符合大量資料的需求。 無伺服器程式碼可以套用商務邏輯來剖析資料, 並以結構化格式輸出以進行動作和分析。

![無伺服器串流處理](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>API 閘道

API 閘道會為用戶端提供單一進入點, 然後以智慧方式將要求路由傳送至後端服務。 管理大量服務是很有用的。 它也可以輕鬆地將用戶端連接到不同的環境, 藉此處理版本設定並簡化開發。 無伺服器可以處理個別微服務的後端調整, 同時透過 API 閘道呈現單一前端。

![無伺服器 API 閘道](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>建議的資源

* [Azure 事件格線](https://docs.microsoft.com/azure/event-grid/overview)
* [Azure IoT 中樞](https://docs.microsoft.com/azure/iot-hub)
* [分散式資料管理的挑戰和解決方案](../microservices/architect-microservice-container-applications/distributed-data-management.md)
* [設計微服務: 識別微服務界限](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
* [事件中樞](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
* [事件來源模式](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
* [實作斷路器模式](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
* [IoT 中樞](https://docs.microsoft.com/azure/iot-hub)
* [服務匯流排](https://docs.microsoft.com/azure/service-bus)
* [使用 Azure Cosmos DB 中的變更摘要支援](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[上一頁](serverless-architecture-considerations.md)
>[下一頁](azure-serverless-platform.md)
