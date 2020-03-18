---
title: Azure 事件網格 - 無伺服器應用
description: Azure 事件網格是一種無伺服器解決方案，用於在按事件付費模型上大規模進行可靠的事件傳遞和路由。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3c577139c12567e762aabd58c9dc29457fa37aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522711"
---
# <a name="event-grid"></a>Event Grid

[Azure 事件網格](/azure/event-grid/overview)為基於事件的應用程式提供無伺服器基礎結構。 可以從任何源發佈到事件網格，並使用來自任何平臺的消息。 事件網格還內置了對 Azure 資源事件的支援，以簡化與應用程式的集成。 例如，您可以訂閱 Blob 存儲事件，以便在上載檔時通知應用。 然後，應用程式可以發佈由其他雲或本地應用程式使用的自訂事件網格消息。 事件網格的構建是為了可靠地處理大規模。 無需設置必要的基礎結構的開銷，即可獲得發佈和訂閱郵件的好處。

![事件網格徽標](./media/event-grid-logo.png)

事件網格的主要功能包括：

- 完全託管的事件路由。
- 規模近乎即時的事件交付。
- Azure 內部和外部的廣泛覆蓋範圍。

## <a name="scenarios"></a>案例

事件網格可處理幾個不同的方案。 本節介紹三個最常見的。

### <a name="ops-automation"></a>作業自動化

![作業自動化](./media/ops-automation.png)

事件網格通過在預配基礎結構時通知[Azure 自動化](https://docs.microsoft.com/azure/automation)來説明加快自動化並簡化策略實施。

### <a name="application-integration"></a>應用程式整合

![應用程式整合](./media/app-integration.png)

您可以使用事件網格將應用連接到其他服務。 使用標準 HTTP 協定，即使是舊版應用也可以輕鬆修改以發佈事件網格消息。 Web 掛鉤可用於其他服務和平臺，用於使用事件網格消息。

### <a name="serverless-apps"></a>無伺服器應用程式

![無伺服器應用程式](./media/serverless-apps.png)

事件網格可以觸發 Azure 函數、邏輯應用或您自己的自訂代碼。 使用事件網格的一個主要好處是，它使用*推送*機制在事件發生時發送消息。 推送體系結構消耗的資源更少，比*輪詢*機制更擴展。 輪詢必須檢查常規間隔的更新。

## <a name="event-grid-vs-other-azure-messaging-services"></a>事件網格與其他 Azure 消息傳遞服務

Azure 提供多個消息傳遞服務，包括[事件中心](https://docs.microsoft.com/azure/event-hubs)[和服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging)。 每個都旨在解決一組特定的用例。 下圖提供了服務之間的差異的高級概述。

![Azure 消息傳遞比較](./media/azure-messaging-services.png)

有關更深入的比較，請參閱[比較消息服務](https://docs.microsoft.com/azure/event-grid/compare-messaging-services)。

## <a name="performance-targets"></a>效能目標

使用事件網格，您可以利用以下性能保證：

- 第 99 個百分位數中的秒端到端延遲。
- 99.99% 可用性。
- 每個區域每秒 1000 萬個事件。
- 每個區域有 1 億個訂閱。
- 50 毫秒發佈延遲。
- 24 小時重試，在 1 天時段內保證交貨，實現指數回退。
- 透明區域容錯移轉。

## <a name="event-grid-schema"></a>事件格線結構描述

事件網格使用標準架構包裝自訂事件。 架構類似于包裝自訂資料元素的信封。 下面是事件網格消息的示例：

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

消息的所有內容都是標準的，`data`但屬性除外。 您可以檢查消息並使用`eventType`和`dataVersion`來取消序列化有效負載的自訂部分。

## <a name="azure-resources"></a>Azure 資源

使用事件網格的主要好處是 Azure 生成的自動消息。 在 Azure 中，資源會自動發佈到允許您訂閱各種事件*的主題*。 下表列出了自動可用的資源類型、訊息類型和事件。

| Azure 資源 | 事件類型 | 描述 |
| -------------- | ---------- | ----------- |
| Azure 訂用帳戶 | Microsoft.Resources.ResourceWriteSuccess | 在資源建立或是更新作業成功時引發。 |
| | Microsoft.Resources.ResourceWriteFailure | 在資源建立或是更新作業失敗時引發。 |
| | Microsoft.Resources.ResourceWriteCancel | 在資源建立或是更新作業取消時引發。 |
|  | Microsoft.Resources.ResourceDeleteSuccess | 在資源刪除作業成功時引發。 |
|  | Microsoft.Resources.ResourceDeleteFailure | 在資源刪除作業失敗時引發。 |
| | Microsoft.Resources.ResourceDeleteCancel | 在資源刪除作業取消時引發。 此事件會於範本部署取消時發生。 |
| Blob 儲存體 | Microsoft.Storage.BlobCreated | 建立 blob 時引發。 |
| | Microsoft.Storage.BlobDeleted | 刪除 blob 時引發。 |
| 事件中樞 | 微軟.eventHub.捕獲檔已創建 | 創建捕獲檔時引發。
| IoT 中樞 | Microsoft.Devices.DeviceCreated | 向 IoT 中樞註冊裝置時發佈。 |
| | Microsoft.Devices.DeviceDeleted | 從 IoT 中樞刪除裝置時發佈。 |
| 資源群組 | Microsoft.Resources.ResourceWriteSuccess | 在資源建立或是更新作業成功時引發。 |
| | Microsoft.Resources.ResourceWriteFailure | 在資源建立或是更新作業失敗時引發。 |
| | Microsoft.Resources.ResourceWriteCancel | 在資源建立或是更新作業取消時引發。 |
| | Microsoft.Resources.ResourceDeleteSuccess | 在資源刪除作業成功時引發。 |
| | Microsoft.Resources.ResourceDeleteFailure | 在資源刪除作業失敗時引發。 |
| | Microsoft.Resources.ResourceDeleteCancel | 在資源刪除作業取消時引發。 此事件會於範本部署取消時發生。 |

有關詳細資訊，請參閱[Azure 事件網格事件架構](https://docs.microsoft.com/azure/event-grid/event-schema)。

可以從任何類型的應用程式（甚至是在本地運行的應用程式）訪問事件網格。

## <a name="conclusion"></a>結論

在本章中，您瞭解了由 Azure 函數、邏輯應用和事件網格組成的 Azure 無伺服器平臺。 您可以使用這些資源構建完全無伺服器的應用體系結構，或創建與其他雲資源和本機伺服器交互的混合解決方案。 結合無伺服器資料平臺（如[Azure SQL](https://docs.microsoft.com/azure/sql-database)或[CosmosDB），](https://docs.microsoft.com/azure/cosmos-db/introduction)可以構建完全託管的雲本機應用程式。

## <a name="recommended-resources"></a>建議的資源

- [應用服務方案](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Application Insights](https://docs.microsoft.com/azure/application-insights)
- [Application Insights 分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [Azure：使用無伺服器 Azure 功能將應用帶到雲中](https://channel9.msdn.com/events/Connect/2017/E102)
- [Azure 事件網格](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure Event Grid 事件結構描述](https://docs.microsoft.com/azure/event-grid/event-schema)
- [Azure 事件中心](https://docs.microsoft.com/azure/event-hubs)
- [Azure 函數文檔](https://docs.microsoft.com/azure/azure-functions)
- [Azure Functions 觸發程序和繫結概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [Azure 邏輯應用](https://docs.microsoft.com/azure/logic-apps)
- [Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging)
- [Azure 表存儲](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [比較函數 1.x 和 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
- [透過 Azure 內部部署資料閘道連線至內部部署資料來源](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [在 Azure 入口網站中建立您的第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [在 Azure CLI 建立您的第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [使用 Visual Studio 建立第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [功能支援的語言](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [監視 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
- [使用 Azure Functions Proxy](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[上一個](logic-apps.md)
>[下一個](durable-azure-functions.md)
