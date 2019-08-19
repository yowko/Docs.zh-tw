---
title: Application Insights-無伺服器應用程式
description: Application Insights 是無伺服器診斷平臺, 可讓開發人員偵測、分級和診斷 web 應用程式、行動應用程式、桌面應用程式和微服務中的問題。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 1f5b99fba448c2c1c12139524ffdcd3708b3c956
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577721"
---
# <a name="telemetry-with-application-insights"></a>具有 Application Insights 的遙測

[Application Insights](https://docs.microsoft.com/azure/application-insights)是無伺服器診斷平臺, 可讓開發人員偵測、分級和診斷 web 應用程式、行動應用程式、桌面應用程式和微服務中的問題。 您只要在入口網站中翻轉交換器, 就可以開啟函式應用程式的 Application Insights。 Application Insights 提供所有這些功能, 而不需要設定伺服器或設定您自己的資料庫。 所有 Application Insights 的功能都是以服務的形式提供, 可自動與您的應用程式整合。

![Application Insights 標誌](./media/application-insights-logo.png)

將 Application Insights 新增至現有的應用程式, 就像將檢測金鑰新增至應用程式的設定一樣簡單。 有了 Application Insights, 您可以:

* 根據度量建立自訂圖表和警示, 例如函式呼叫數目、執行函式所花的時間, 以及例外狀況
* 分析失敗和伺服器例外狀況
* 依作業向下切入效能, 並測量呼叫協力廠商相依性所花費的時間
* 監視裝載函式應用程式的所有伺服器上的 CPU 使用量、記憶體和速率
* 觀看計量的即時串流, 包括函數應用程式的要求計數和延遲
* 使用[分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)來搜尋、查詢及建立函數資料的自訂圖表

![計量瀏覽器](./media/metrics-explorer.png)

除了內建的遙測之外, 也可以產生自訂遙測。 下列程式碼片段會使用函數應用程式的檢測金鑰集來建立自訂遙測用戶端:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

下列程式碼會測量在[Azure 表格儲存體](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)實例中插入新資料列所需的時間:

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

產生的效能圖表如下所示:

![自訂遙測](./media/custom-telemetry.png)

自訂遙測會顯示插入新資料列的平均時間為32.6 毫秒。

Application Insights 提供強大且方便的方式, 以記錄有關無伺服器應用程式的詳細遙測。 您可以完全控制所提供的追蹤和記錄層級。 您可以追蹤自訂統計資料, 例如事件、相依性和網頁檢視。 最後, 強大的分析可讓您撰寫詢問重要問題的查詢, 並產生圖表和先進的深入解析。

如需詳細資訊, 請參閱[Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)。

>[!div class="step-by-step"]
>[上一頁](azure-functions.md)
>[下一頁](logic-apps.md)
