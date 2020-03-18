---
title: 應用程式洞察 - 無伺服器應用
description: 應用程式見解是一個無伺服器診斷平臺，使開發人員能夠檢測、分診和診斷 Web 應用、移動應用、桌面應用和微服務中的問題。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522742"
---
# <a name="telemetry-with-application-insights"></a>使用 Application Insights 進行遙測

[應用程式見解](https://docs.microsoft.com/azure/application-insights)是一個無伺服器診斷平臺，使開發人員能夠檢測、分診和診斷 Web 應用、移動應用、桌面應用和微服務中的問題。 只需在門戶中翻轉開關，即可打開函數應用的應用程式見解。 應用程式見解提供所有這些功能，而無需佈建服務器或設置自己的資料庫。 所有應用程式見解功能都作為自動與您的應用集成的服務提供。

![應用程式見解徽標](./media/application-insights-logo.png)

向現有應用添加應用程式見解與向應用程式的設置添加檢測金鑰一樣簡單。 借助應用程式見解，您可以：

- 基於指標創建自訂圖表和警報，例如函式呼叫次數、運行函數所需的時間以及異常
- 分析故障和伺服器異常
- 按操作深入瞭解性能並衡量調用協力廠商依賴關係所需的時間
- 監視託管功能應用的所有伺服器的 CPU 使用方式、記憶體和速率
- 查看指標的即時流，包括功能應用的請求計數和延遲
- 使用[Analytics（分析）](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)搜索、查詢和創建函數資料的自訂圖表

![計量瀏覽器](./media/metrics-explorer.png)

除了內置遙測之外，還可以生成自訂遙測。 以下程式碼片段使用函數應用的檢測金鑰集創建自訂遙測用戶端：

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

以下代碼測量將新行插入[Azure 表存儲](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)實例所需的時間：

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

將顯示生成的性能圖：

![自訂遙測](./media/custom-telemetry.png)

自訂遙測顯示插入新行的平均時間是 32.6 毫秒。

應用程式見解提供了一種功能強大、方便的方式來記錄有關無伺服器應用程式的詳細遙測資料。 您可以完全控制提供的跟蹤和日誌記錄級別。 您可以跟蹤自訂統計資訊，如事件、依賴項和網頁檢視。 最後，強大的分析使您能夠編寫詢問重要問題的查詢，並生成圖表和高級見解。

如需詳細資訊，請參閱[監視 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)。

>[!div class="step-by-step"]
>[上一個](azure-functions.md)
>[下一個](logic-apps.md)
