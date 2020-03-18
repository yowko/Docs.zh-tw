---
title: 無伺服器設計示例 - 無伺服器應用
description: 瞭解無伺服器體系結構支援的各種方案，從基於計畫和事件的處理到檔觸發器和流進程。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4e8fda0c1423c881c0807602e11f7c49ff7cfe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093561"
---
# <a name="serverless-design-examples"></a>無伺服器設計範例

對於無伺服器，存在許多設計模式。 本節捕獲一些使用無伺服器的常見方案。 所有示例的共同點是事件觸發器和業務邏輯的基本組合。

## <a name="scheduling"></a>排程

計畫任務是一個常見的函數。 下圖顯示了沒有適當完整性檢查的舊資料庫。 必須定期清除資料庫。 無伺服器函數查找無效資料並清除資料。 觸發器是按計劃運行代碼的計時器。

![無伺服器調度](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>命令與查詢責任隔離 (CQRS)

命令和查詢責任分離 （CQRS） 是一種模式，它為讀取（或查詢）資料以及修改資料的操作提供不同的介面。 它解決了幾個常見問題。 在傳統的基於創建讀取更新刪除 （CRUD） 的系統中，大量讀取和寫入同一資料存儲可能會產生衝突。 鎖定可能經常發生，並顯著減慢讀取速度。 通常，資料作為多個域物件的複合顯示，讀取操作必須合併來自不同實體的資料。

使用 CQRS，讀取可能涉及一個特殊的"扁平化"實體，該實體以使用方式對資料進行建模。 讀取的處理方式與存儲方式不同。 例如，儘管資料庫可能將連絡人存儲為具有子地址記錄的標頭記錄，但讀取可能涉及具有標頭和位址屬性的實體。 創建讀取模型的方法有很多種。 它可能從視圖中具體化。 更新操作可以封裝為隔離事件，然後觸發兩個不同模型的更新。 有用於閱讀和寫作的單獨模型。

![CQRS 示例](./media/cqrs-example.png)

無伺服器可以通過提供隔離的終結點來適應 CQRS 模式。 一個無伺服器函數可容納查詢或讀取，另一個無伺服器函數或函數集處理更新操作。 無伺服器函數也可以負責使讀取模型保持最新，並且可以通過資料庫的[更改源](https://docs.microsoft.com/azure/cosmos-db/change-feed)觸發。 前端開發簡化為連接到必要的終結點。 事件處理在後端處理。 此模型還適用于大型專案，因為不同的團隊可能處理不同的操作。

## <a name="event-based-processing"></a>基於事件的處理

在基於消息的系統中，事件通常收集在佇列或發行者/訂閱者主題中，以便執行操作。 這些事件可以觸發無伺服器函數來執行業務邏輯。 基於事件的處理的一個示例是事件源系統。 引發"事件"以將任務標記為已完成。 事件觸發的無伺服器函數將更新相應的資料庫文檔。 第二個無伺服器函數可以使用事件更新系統的讀取模型。 [Azure 事件網格](https://docs.microsoft.com/azure/event-grid/overview)提供了一種將事件與函數作為訂閱者集成的方法。

> 事件是資訊性消息。 有關詳細資訊，請參閱[事件採購模式](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)。

## <a name="file-triggers-and-transformations"></a>檔觸發器和轉換

擷取、轉換和下載 （ETL） 是一種常見的業務功能。 無伺服器是 ETL 的一個很好的解決方案，因為它允許將代碼作為管道的一部分觸發。 各個代碼元件可以處理各個方面。 一個無伺服器函數可以下載檔案，另一個函數應用轉換，另一個載入資料。 代碼可以獨立測試和部署，從而更輕鬆地根據需要維護和擴展。

![無伺服器檔觸發器和轉換](./media/serverless-file-triggers.png)

在關係圖中，"冷存儲"提供在[Azure 流分析](https://docs.microsoft.com/azure/stream-analytics)中解析的資料。 資料流程中遇到的任何問題都觸發 Azure 函數來解決異常問題。

## <a name="asynchronous-background-processing-and-messaging"></a>非同步幕後處理和消息傳送

非同步消息傳遞和幕後處理允許應用程式啟動進程，而無需等待。 非同步處理的一個示例是 OCR 應用。 提交映射並排隊進行處理。 掃描圖像以提取文本可能需要時間，一旦完成，就會發送通知。 在這種情況下，無伺服器可以同時處理調用和結果。

## <a name="web-apps-and-apis"></a>Web Apps 和 API

無伺服器應用程式的一個常見方案是 N 層應用程式，最常見的是 UI 層是 Web 應用的應用程式。 單頁應用程式 （SPA） 的受歡迎程度最近大幅上升。 SPA 應用呈現單個頁面，然後依靠 API 呼叫和返回的資料動態呈現新 UI，而無需重新載入整個頁面。 用戶端轉譯為最終使用者提供了更快、回應更快的應用程式。

HTTP 調用觸發的無伺服器終結點可用於處理 API 請求。 例如，廣告服務公司可能會調用包含使用者設定檔資訊的無伺服器功能來請求自訂廣告。 無伺服器功能返回自訂廣告，網頁呈現它。

![無伺服器 Web API](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Data Pipeline

無伺服器函數可用於促進資料管道。 在此示例中，檔將觸發將 CSV 檔中的資料轉換為表中的資料行的函數。 有組織的表允許 Power BI 儀表板向最終使用者顯示分析。

![無伺服器資料管道](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>串流處理

設備和感應器通常生成必須即時處理的資料流程。 有許多技術可以捕獲消息和流從[事件中心和](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) [IoT 中心](https://docs.microsoft.com/azure/iot-hub)到[服務匯流排](https://docs.microsoft.com/azure/service-bus)。 無論傳輸如何，無伺服器都是處理消息和資料流程的理想機制。 無伺服器可以快速擴展以滿足大量資料的需求。 無伺服器代碼可以應用業務邏輯來分析資料和輸出，以結構化格式進行操作和分析。

![無伺服器流處理](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>API 閘道

API 閘道為用戶端提供單一進入點，然後智慧地將請求路由到後端服務。 管理大型服務集很有用。 它還可以通過輕鬆將用戶端連接到不同的環境來處理版本控制並簡化開發。 無伺服器可以處理單個微服務的後端擴展，同時通過 API 閘道呈現單個前端。

![無伺服器 API 閘道](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>建議的資源

- [Azure 事件網格](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure IoT 中心](https://docs.microsoft.com/azure/iot-hub)
- [分散式資料管理的挑戰和解決方案](../microservices/architect-microservice-container-applications/distributed-data-management.md)
- [設計微服務：識別微服務邊界](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
- [事件中樞](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
- [事件採購模式](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
- [實作斷路器模式](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
- [IoT 中樞](https://docs.microsoft.com/azure/iot-hub)
- [服務匯流排](https://docs.microsoft.com/azure/service-bus)
- [使用 Azure Cosmos DB 中的變更摘要支援](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[上一個](serverless-architecture-considerations.md)
>[下一個](azure-serverless-platform.md)
