---
title: Azure Event Grid-無伺服器應用程式
description: Azure Event Grid 是可靠的事件傳遞和路由事件支付每個模型上大規模的無伺服器解決方案。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b2507da61cbea3b4bdc51c6eecfe4d784737e924
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "49369744"
---
# <a name="event-grid"></a>Event Grid

[Azure Event Grid](/azure-event-grid/overview)事件為基礎的應用程式提供無伺服器的基礎結構。 您可以從任何來源發佈至 Event Grid，並從任何平台取用訊息。 Event Grid 也有內建支援來簡化您的應用程式與整合的 Azure 資源的事件。 例如，您可以訂閱通知您的應用程式，當檔案上傳的 blob 儲存體事件。 然後，您的應用程式可以發佈的自訂事件格線訊息由其他雲端或內部應用程式。 Event Grid 是建置成能夠可靠處理大規模。 您會獲得發佈和訂閱訊息，無需額外設定必要的基礎結構的優點。

![事件格線標誌](./media/event-grid-logo.png)

事件格線的主要功能包括：

* 完全受控的事件路由。
* 近乎即時的事件傳遞分散。
* 涵蓋 Azure 內外的廣泛範圍。

## <a name="scenarios"></a>案例

Event Grid 可解決數個不同的案例。 本章節涵蓋三種最常見的。

### <a name="ops-automation"></a>作業自動化

![作業自動化](./media/ops-automation.png)

Event Grid 可協助速度自動化和簡化原則強制執行通知[Azure 自動化](https://docs.microsoft.com/azure/automation)佈建基礎結構時。

### <a name="application-integration"></a>應用程式整合

![應用程式整合](./media/app-integration.png)

您可以使用 Event Grid，將應用程式連接至其他服務。 使用標準 HTTP 通訊協定，即使是舊版應用程式可以輕鬆地修改以 Event Grid 訊息發佈。 Webhook 可供其他服務和使用事件格線訊息的平台。

### <a name="serverless-apps"></a>無伺服器應用程式

![無伺服器應用程式](./media/serverless-apps.png)

Event Grid 可以觸發 Azure Functions、 Logic Apps 中或您自己的自訂程式碼。 使用 Event Grid 的主要優點是它會使用*推播*事件發生時傳送訊息的機制。 推播架構會耗用較少的資源，以及進行的擴充優於*輪詢*機制。 輪詢必須檢查定期更新。

## <a name="event-grid-vs-other-azure-messaging-services"></a>事件格線與其他 Azure 傳訊服務

Azure 提供數個訊息的服務，包括[事件中樞](https://docs.microsoft.com/azure/event-hubs)並[Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)。 每個旨在解決一組特定的使用案例。 下圖提供服務之間差異的高階概觀。

![Azure 訊息比較](./media/azure-messaging-services.png)

如需更深入的比較，請參閱[比較訊息服務](https://docs.microsoft.com/azure/event-grid/compare-messaging-services)。

## <a name="performance-targets"></a>效能目標

使用事件格線，您可以利用下列效能保證：

* 少於一秒內的第 99 個百分位數的端對端延遲。
* 99.99%可用性。
* 每個區域每秒 10 萬個事件。
* 每個區域 100 萬個訂用帳戶。
* 發行者延遲 50 毫秒。
* 使用指數退避法為保證傳遞，在 1 天 視窗中的 24 小時重試。
* 透明的區域性容錯移轉。

## <a name="event-grid-schema"></a>Event Grid 結構描述

Event Grid 會使用標準的結構描述，來包裝自訂事件。 結構描述就像是信封包裝您的自訂資料元素。 以下是事件格線訊息的範例：

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

有關訊息的所有項目是除了標準`data`屬性。 您可以檢查訊息，並使用`eventType`和`dataVersion`還原序列化的自訂承載一部分。

## <a name="azure-resources"></a>Azure 資源

使用 Event Grid 的主要優點是由 Azure 產生的自動訊息。 在 Azure 中，資源會自動發行至*主題*，可讓您各種事件訂閱。 下表列出的資源類型、 訊息類型和事件，可自動。

| Azure 資源 | 事件類型 | 描述 |
| -------------- | ---------- | ----------- |
| Azure 訂用帳戶 | Microsoft.Resources.ResourceWriteSuccess | 當資源建立或更新作業成功引發。 |
| | Microsoft.Resources.ResourceWriteFailure | 在資源建立或更新作業失敗時引發。 |
| | Microsoft.Resources.ResourceWriteCancel | 當資源建立或更新作業取消引發。 |
|  | Microsoft.Resources.ResourceDeleteSuccess | 在資源刪除作業成功時，就會引發。 |
|  | Microsoft.Resources.ResourceDeleteFailure | 在資源刪除作業失敗時引發。 |
| | Microsoft.Resources.ResourceDeleteCancel | 當資源刪除作業取消時引發。 取消範本部署時，就會發生此事件。 |
| Blob 儲存體 | Microsoft.Storage.BlobCreated | 在建立 blob 時引發。 |
| | Microsoft.Storage.BlobDeleted | 刪除 blob 時引發。 |
| 事件中樞 | Microsoft.EventHub.CaptureFileCreated | 當擷取檔案建立時引發。
| IoT 中樞 | Microsoft.Devices.DeviceCreated | 發行到 IoT 中樞註冊裝置。 |
| | Microsoft.Devices.DeviceDeleted | 從 IoT 中樞刪除裝置時，就會發行。 |
| 資源群組 | Microsoft.Resources.ResourceWriteSuccess | 當資源建立或更新作業成功引發。 |
| | Microsoft.Resources.ResourceWriteFailure | 在資源建立或更新作業失敗時引發。 |
| | Microsoft.Resources.ResourceWriteCancel | 當資源建立或更新作業取消引發。 |
| | Microsoft.Resources.ResourceDeleteSuccess | 在資源刪除作業成功時，就會引發。 |
| | Microsoft.Resources.ResourceDeleteFailure | 在資源刪除作業失敗時引發。 |
| | Microsoft.Resources.ResourceDeleteCancel | 當資源刪除作業取消時引發。 取消範本部署時，就會發生此事件。 |

如需詳細資訊，請參閱 < [Azure Event Grid 事件結構描述](https://docs.microsoft.com/azure/event-grid/event-schema)。

您可以從任何類型的應用程式，甚至是內部部署上執行的一個來存取事件格線。

## <a name="conclusion"></a>結論

在這一章中您已了解 Azure Functions、 Logic Apps 和 Event Grid 組成 Azure 無伺服器平台。 您可以使用這些資源來建置完全無伺服器應用程式架構，或建立混合式解決方案，與其他雲端資源互動，並在內部部署伺服器。 這類結合的無伺服器的資料平台[Azure SQL](https://docs.microsoft.com/azure/sql-database)或是[CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction)，您可以建置完全受控的雲端原生應用程式。

## <a name="recommended-resources"></a>建議的資源

* [App service 方案](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [Application Insights](https://docs.microsoft.com/azure/application-insights)
* [Application Insights 分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [Azure： 將應用程式帶至雲端，無伺服器 Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102)
* [Azure 事件格線](https://docs.microsoft.com/azure/azure-event-grid/overview)
* [Azure Event Grid 事件結構描述](https://docs.microsoft.com/azure/event-grid/event-schema)
* [Azure 事件中樞](https://docs.microsoft.com/azure/event-hubs)
* [Azure Functions 文件](https://docs.microsoft.com/azure/azure-functions)
* [Azure Functions 觸發程序和繫結概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
* [Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging)
* [Azure 資料表儲存體](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [比較 functions 1.x 和 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [連接到 Azure 內部部署資料閘道的內部部署資料來源](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [在 Azure 入口網站中建立您的第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [建立您使用 Azure CLI 的第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [建立您使用 Visual Studio 的第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [支援語言的函式](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [監視 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [使用 Azure Functions Proxy](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
[上一頁](logic-apps.md)
[下一頁](durable-azure-functions.md)