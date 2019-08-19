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
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="939b8-103">具有 Application Insights 的遙測</span><span class="sxs-lookup"><span data-stu-id="939b8-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="939b8-104">[Application Insights](https://docs.microsoft.com/azure/application-insights)是無伺服器診斷平臺, 可讓開發人員偵測、分級和診斷 web 應用程式、行動應用程式、桌面應用程式和微服務中的問題。</span><span class="sxs-lookup"><span data-stu-id="939b8-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="939b8-105">您只要在入口網站中翻轉交換器, 就可以開啟函式應用程式的 Application Insights。</span><span class="sxs-lookup"><span data-stu-id="939b8-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="939b8-106">Application Insights 提供所有這些功能, 而不需要設定伺服器或設定您自己的資料庫。</span><span class="sxs-lookup"><span data-stu-id="939b8-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="939b8-107">所有 Application Insights 的功能都是以服務的形式提供, 可自動與您的應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="939b8-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Application Insights 標誌](./media/application-insights-logo.png)

<span data-ttu-id="939b8-109">將 Application Insights 新增至現有的應用程式, 就像將檢測金鑰新增至應用程式的設定一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="939b8-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="939b8-110">有了 Application Insights, 您可以:</span><span class="sxs-lookup"><span data-stu-id="939b8-110">With Application Insights you can:</span></span>

* <span data-ttu-id="939b8-111">根據度量建立自訂圖表和警示, 例如函式呼叫數目、執行函式所花的時間, 以及例外狀況</span><span class="sxs-lookup"><span data-stu-id="939b8-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
* <span data-ttu-id="939b8-112">分析失敗和伺服器例外狀況</span><span class="sxs-lookup"><span data-stu-id="939b8-112">Analyze failures and server exceptions</span></span>
* <span data-ttu-id="939b8-113">依作業向下切入效能, 並測量呼叫協力廠商相依性所花費的時間</span><span class="sxs-lookup"><span data-stu-id="939b8-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
* <span data-ttu-id="939b8-114">監視裝載函式應用程式的所有伺服器上的 CPU 使用量、記憶體和速率</span><span class="sxs-lookup"><span data-stu-id="939b8-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
* <span data-ttu-id="939b8-115">觀看計量的即時串流, 包括函數應用程式的要求計數和延遲</span><span class="sxs-lookup"><span data-stu-id="939b8-115">View a live stream of metrics including request count and latency for your function apps</span></span>
* <span data-ttu-id="939b8-116">使用[分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)來搜尋、查詢及建立函數資料的自訂圖表</span><span class="sxs-lookup"><span data-stu-id="939b8-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![計量瀏覽器](./media/metrics-explorer.png)

<span data-ttu-id="939b8-118">除了內建的遙測之外, 也可以產生自訂遙測。</span><span class="sxs-lookup"><span data-stu-id="939b8-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="939b8-119">下列程式碼片段會使用函數應用程式的檢測金鑰集來建立自訂遙測用戶端:</span><span class="sxs-lookup"><span data-stu-id="939b8-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="939b8-120">下列程式碼會測量在[Azure 表格儲存體](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)實例中插入新資料列所需的時間:</span><span class="sxs-lookup"><span data-stu-id="939b8-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="939b8-121">產生的效能圖表如下所示:</span><span class="sxs-lookup"><span data-stu-id="939b8-121">The resulting performance graph is shown:</span></span>

![自訂遙測](./media/custom-telemetry.png)

<span data-ttu-id="939b8-123">自訂遙測會顯示插入新資料列的平均時間為32.6 毫秒。</span><span class="sxs-lookup"><span data-stu-id="939b8-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="939b8-124">Application Insights 提供強大且方便的方式, 以記錄有關無伺服器應用程式的詳細遙測。</span><span class="sxs-lookup"><span data-stu-id="939b8-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="939b8-125">您可以完全控制所提供的追蹤和記錄層級。</span><span class="sxs-lookup"><span data-stu-id="939b8-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="939b8-126">您可以追蹤自訂統計資料, 例如事件、相依性和網頁檢視。</span><span class="sxs-lookup"><span data-stu-id="939b8-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="939b8-127">最後, 強大的分析可讓您撰寫詢問重要問題的查詢, 並產生圖表和先進的深入解析。</span><span class="sxs-lookup"><span data-stu-id="939b8-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="939b8-128">如需詳細資訊, 請參閱[Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)。</span><span class="sxs-lookup"><span data-stu-id="939b8-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="939b8-129">[上一頁](azure-functions.md)
>[下一頁](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="939b8-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
