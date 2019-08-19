---
title: Azure 事件方格-無伺服器應用程式
description: Azure 事件格線是一種無伺服器解決方案, 可在每個事件的隨用隨付模型上大規模地進行可靠的事件傳遞和路由。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4970130ede0c96c645129ee6c8c7d54cb1114042
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577571"
---
# <a name="event-grid"></a>事件方格

[Azure 事件方格](/azure/event-grid/overview)提供事件型應用程式的無伺服器基礎結構。 您可以從任何來源發佈至事件方格, 並取用來自任何平臺的訊息。 事件方格也提供來自 Azure 資源的事件內建支援, 以簡化與您應用程式的整合。 例如, 您可以訂閱 blob 儲存體事件, 以在上傳檔案時通知您的應用程式。 您的應用程式接著可以發佈其他雲端或內部部署應用程式所使用的自訂事件方格訊息。 事件方格是為了可靠地處理大規模而建立的。 您可以獲得發佈和訂閱訊息的優點, 而不需要額外設定所需的基礎結構。

![事件方格標誌](./media/event-grid-logo.png)

事件方格的主要功能包括:

* 完全受控的事件路由。
* 近乎即時的大規模事件傳遞。
* Azure 內部和外部的廣泛涵蓋範圍。

## <a name="scenarios"></a>案例

事件方格會解決幾個不同的案例。 本節涵蓋三個最常見的部分。

### <a name="ops-automation"></a>Ops 自動化

![Ops 自動化](./media/ops-automation.png)

事件方格可以在布建基礎結構時通知[Azure 自動化](https://docs.microsoft.com/azure/automation), 以協助加快自動化速度並簡化原則強制執行。

### <a name="application-integration"></a>應用程式整合

![應用程式整合](./media/app-integration.png)

您可以使用事件方格, 將您的應用程式連線到其他服務。 使用標準 HTTP 通訊協定, 甚至可以輕鬆地修改繼承應用程式來發佈事件方格訊息。 Web 勾點可供其他服務和平臺使用事件方格訊息。

### <a name="serverless-apps"></a>無伺服器應用程式

![無伺服器應用程式](./media/serverless-apps.png)

事件方格可以觸發 Azure Functions、Logic Apps 或您自己的自訂程式碼。 使用「事件方格」的主要優點是, 它會在發生事件時使用*推*播機制來傳送訊息。 推播架構會耗用較少的資源, 而且比*輪詢*機制更適合進行調整。 輪詢必須定期檢查是否有更新。

## <a name="event-grid-vs-other-azure-messaging-services"></a>事件方格與其他 Azure 訊息服務的比較

Azure 提供數個訊息服務, 包括[事件中樞](https://docs.microsoft.com/azure/event-hubs)和[服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging)。 每個都是設計來處理一組特定的使用案例。 下圖提供服務之間差異的高層級總覽。

![Azure 訊息比較](./media/azure-messaging-services.png)

如需更深入的比較, 請參閱[比較訊息服務](https://docs.microsoft.com/azure/event-grid/compare-messaging-services)。

## <a name="performance-targets"></a>效能目標

使用「事件方格」, 您可以利用下列效能保證:

* 次秒第99個百分位數的端對端延遲。
* 99.99% 的可用性。
* 每個區域每秒10000000個事件。
* 每個區域100000000個訂閱。
* 50-ms 發行者延遲。
* 以指數輪詢的24小時重試, 在1天的時間範圍內提供保證。
* 透明的區域性容錯移轉。

## <a name="event-grid-schema"></a>事件方格架構

事件方格會使用標準架構來包裝自訂事件。 架構就像是包裝自訂資料元素的信封。 以下是事件方格的範例訊息:

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

除了`data`屬性外, 訊息的所有內容都是標準的。 您可以檢查訊息, 並使用`eventType`和`dataVersion`來還原序列化裝載的自訂部分。

## <a name="azure-resources"></a>Azure 資源

使用「事件方格」的主要優點是 Azure 所產生的自動訊息。 在 Azure 中, 資源會自動發行至可讓您訂閱各種事件的*主題*。 下表列出可自動使用的資源類型、訊息類型和事件。

| Azure 資源 | 事件類型 | 描述 |
| -------------- | ---------- | ----------- |
| Azure 訂用帳戶 | Microsoft.Resources.ResourceWriteSuccess | 在資源建立或更新作業成功時引發。 |
| | Microsoft.Resources.ResourceWriteFailure | 當資源建立或更新作業失敗時引發。 |
| | Microsoft.Resources.ResourceWriteCancel | 在資源建立或更新作業取消時引發。 |
|  | Microsoft.Resources.ResourceDeleteSuccess | 在資源刪除作業成功時引發。 |
|  | Microsoft.Resources.ResourceDeleteFailure | 在資源刪除作業失敗時引發。 |
| | Microsoft.Resources.ResourceDeleteCancel | 在資源刪除作業取消時引發。 取消範本部署時, 就會發生此事件。 |
| Blob 儲存體 | Microsoft.Storage.BlobCreated | 建立 blob 時引發。 |
| | Microsoft.Storage.BlobDeleted | 刪除 blob 時引發。 |
| 事件中樞 | Microsoft.EventHub.CaptureFileCreated | 建立 capture 檔案時引發。
| IoT 中樞 | Microsoft.Devices.DeviceCreated | 已在裝置註冊至 IoT 中樞時發佈。 |
| | Microsoft.Devices.DeviceDeleted | 從 IoT 中樞刪除裝置時發佈。 |
| 資源群組 | Microsoft.Resources.ResourceWriteSuccess | 在資源建立或更新作業成功時引發。 |
| | Microsoft.Resources.ResourceWriteFailure | 當資源建立或更新作業失敗時引發。 |
| | Microsoft.Resources.ResourceWriteCancel | 在資源建立或更新作業取消時引發。 |
| | Microsoft.Resources.ResourceDeleteSuccess | 在資源刪除作業成功時引發。 |
| | Microsoft.Resources.ResourceDeleteFailure | 在資源刪除作業失敗時引發。 |
| | Microsoft.Resources.ResourceDeleteCancel | 在資源刪除作業取消時引發。 取消範本部署時, 就會發生此事件。 |

如需詳細資訊, 請參閱[Azure Event Grid 事件架構](https://docs.microsoft.com/azure/event-grid/event-schema)。

您可以從任何類型的應用程式存取事件方格, 即使是在內部部署環境中執行。

## <a name="conclusion"></a>結論

在本章中, 您已瞭解由 Azure Functions、Logic Apps 和事件方格組成的 Azure 無伺服器平臺。 您可以使用這些資源來建立完全無伺服器的應用程式架構, 或建立與其他雲端資源和內部部署伺服器互動的混合式解決方案。 結合了無伺服器資料平臺 (例如[AZURE SQL](https://docs.microsoft.com/azure/sql-database)或[CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction)), 您可以建立完全受控的雲端原生應用程式。

## <a name="recommended-resources"></a>建議的資源

* [App service 方案](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [Application Insights](https://docs.microsoft.com/azure/application-insights)
* [Application Insights 分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [Azure透過無伺服器 Azure Functions 將您的應用程式帶入雲端](https://channel9.msdn.com/events/Connect/2017/E102)
* [Azure 事件格線](https://docs.microsoft.com/azure/event-grid/overview)
* [Azure 事件方格事件架構](https://docs.microsoft.com/azure/event-grid/event-schema)
* [Azure 事件中樞](https://docs.microsoft.com/azure/event-hubs)
* [Azure Functions 檔](https://docs.microsoft.com/azure/azure-functions)
* [Azure Functions 觸發程式和系結概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps)
* [Azure 服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging)
* [Azure 表格儲存體](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [比較函數1.x 和2。x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [使用 Azure 內部部署資料閘道連接到內部部署資料來源](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [在 Azure 入口網站中建立您的第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [使用 Azure CLI 建立您的第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [使用 Visual Studio 建立您的第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [功能支援的語言](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [監視 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [使用 Azure Functions Proxy](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[上一頁](logic-apps.md)
>[下一頁](durable-azure-functions.md)
