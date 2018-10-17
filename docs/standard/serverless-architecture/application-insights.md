---
title: Application Insights-無伺服器應用程式
description: Application Insights 是一個無伺服器的診斷平台，可讓開發人員偵測、 分級和診斷 web 應用程式、 行動裝置應用程式、 傳統型應用程式和微服務中的問題。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 57b1f70825251c48f720dcd78d094f5e8fb1edb8
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "49369738"
---
# <a name="telemetry-with-application-insights"></a>使用 Application Insights 的遙測

[Application Insights](https://docs.microsoft.com/azure/application-insights)是無伺服器的診斷平台，可讓開發人員可以偵測、 分級和診斷 web 應用程式、 行動裝置應用程式、 傳統型應用程式和微服務中的問題。 您可以開啟 Application Insights 的函式應用程式只要在入口網站中開關。 Application Insights 會提供所有這些功能，您不必設定伺服器，或將您自己的資料庫設定。 服務會自動與您的應用程式整合，提供所有 Application Insights 的功能。

![Application Insights 標誌](./media/application-insights-logo.png)

將 Application Insights 加入現有的應用程式是簡單，只要將檢測金鑰新增至您的應用程式設定。 使用 Application Insights 中，您可以：

* 建立自訂圖表和計量，例如函式引動過程數目為基礎的警示，請執行函式和例外狀況所花費的時間
* 分析失敗和伺服器例外狀況
* 向下鑽研到效能的作業和測量呼叫協力廠商相依性所花費的時間
* 在裝載您的函式應用程式的所有伺服器監視 CPU 使用量、 記憶體和費率
* 檢視即時資料流的度量，包括要求計數和延遲函式應用程式
* 使用[Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)搜尋，查詢和建立您的函式資料的自訂圖表

![計量瀏覽器](./media/metrics-explorer.png)

除了內建遙測，它也可產生自訂的遙測資料。 下列程式碼片段會建立自訂的遙測用戶端使用的設定函式應用程式的檢測金鑰：

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

下列程式碼可讓您測量插入新資料列需要多久[Azure 表格儲存體](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)執行個體：

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

產生的效能圖表所示：

![自訂遙測](./media/custom-telemetry.png)

自訂的遙測會顯示插入新的資料列的平均時間為 32.6 毫秒。

Application Insights 提供強大、 便利的方式來記錄詳細的遙測，有關無伺服器應用程式。 您可以完整控制的追蹤層級，並記錄，提供。 您可以追蹤自訂統計資料，例如事件、 相依性及頁面檢視。 最後，功能強大的分析可讓您撰寫查詢，以提出重要問題，並產生圖表和進階的深入解析。

如需詳細資訊，請參閱 <<c0> [ 監視 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)。

>[!div class="step-by-step"]
[上一頁](azure-functions.md)
[下一頁](logic-apps.md)