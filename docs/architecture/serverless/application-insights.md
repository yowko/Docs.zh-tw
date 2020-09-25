---
title: Application Insights 無伺服器應用程式
description: Application Insights 是無伺服器的診斷平臺，可讓開發人員偵測、分級和診斷 web 應用程式、行動應用程式、桌面應用程式和微服務中的問題。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 42791b052ebb068c9b7109291e66b30b47e5821f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173317"
---
# <a name="telemetry-with-application-insights"></a>使用 Application Insights 進行遙測

[Application Insights](/azure/application-insights) 是無伺服器的診斷平臺，可讓開發人員偵測、分級和診斷 web 應用程式、行動應用程式、桌面應用程式和微服務中的問題。 只要在入口網站中翻轉切換開關，您就可以開啟函式應用程式的 Application Insights。 Application Insights 可提供這些功能，您不需要設定伺服器或設定自己的資料庫。 所有 Application Insights 的功能都會以服務的形式提供，並自動與您的應用程式整合。

![Application Insights 標誌](./media/application-insights-logo.png)

將 Application Insights 新增至現有的應用程式，就像在您的應用程式設定中新增檢測金鑰一樣簡單。 使用 Application Insights 您可以：

- 根據計量數目、函式調用數目、執行函式所花的時間，以及例外狀況，建立自訂圖表和警示
- 分析失敗和伺服器例外狀況
- 依作業深入探索效能，並測量呼叫協力廠商相依性所花費的時間
- 監視裝載函式應用程式之所有伺服器的 CPU 使用量、記憶體和速率
- 觀看計量的即時資料流，包括函數應用程式的要求計數和延遲
- 使用 [分析](/azure/application-insights/app-insights-analytics) 來搜尋、查詢及建立函數資料的自訂圖表

![計量瀏覽器](./media/metrics-explorer.png)

除了內建遙測之外，也可以產生自訂遙測。 下列程式碼片段會使用函式應用程式的檢測金鑰集來建立自訂遙測用戶端：

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

下列程式碼會測量將新的資料列插入至 [Azure 資料表儲存體](/azure/cosmos-db/table-storage-overview) 實例所需的時間長度：

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

產生的效能圖表如下所示：

![自訂遙測](./media/custom-telemetry.png)

自訂遙測會顯示插入新資料列的平均時間是32.6 毫秒。

Application Insights 提供了一種功能強大且方便的方式，可記錄有關無伺服器應用程式的詳細遙測資料。 您可以完整控制所提供的追蹤和記錄層級。 您可以追蹤自訂統計資料，例如事件、相依性和頁面流覽。 最後，強大的分析可讓您撰寫查詢，以提出重要的問題並產生圖表和先進的見解。

如需詳細資訊，請參閱[監視 Azure Functions](/azure/azure-functions/functions-monitoring)。

>[!div class="step-by-step"]
>[上一個](azure-functions.md) 
>[下一步](logic-apps.md)
