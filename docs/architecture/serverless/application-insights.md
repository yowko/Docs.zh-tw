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
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="618ac-103">使用 Application Insights 進行遙測</span><span class="sxs-lookup"><span data-stu-id="618ac-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="618ac-104">[應用程式見解](https://docs.microsoft.com/azure/application-insights)是一個無伺服器診斷平臺，使開發人員能夠檢測、分診和診斷 Web 應用、移動應用、桌面應用和微服務中的問題。</span><span class="sxs-lookup"><span data-stu-id="618ac-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="618ac-105">只需在門戶中翻轉開關，即可打開函數應用的應用程式見解。</span><span class="sxs-lookup"><span data-stu-id="618ac-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="618ac-106">應用程式見解提供所有這些功能，而無需佈建服務器或設置自己的資料庫。</span><span class="sxs-lookup"><span data-stu-id="618ac-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="618ac-107">所有應用程式見解功能都作為自動與您的應用集成的服務提供。</span><span class="sxs-lookup"><span data-stu-id="618ac-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![應用程式見解徽標](./media/application-insights-logo.png)

<span data-ttu-id="618ac-109">向現有應用添加應用程式見解與向應用程式的設置添加檢測金鑰一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="618ac-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="618ac-110">借助應用程式見解，您可以：</span><span class="sxs-lookup"><span data-stu-id="618ac-110">With Application Insights you can:</span></span>

- <span data-ttu-id="618ac-111">基於指標創建自訂圖表和警報，例如函式呼叫次數、運行函數所需的時間以及異常</span><span class="sxs-lookup"><span data-stu-id="618ac-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="618ac-112">分析故障和伺服器異常</span><span class="sxs-lookup"><span data-stu-id="618ac-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="618ac-113">按操作深入瞭解性能並衡量調用協力廠商依賴關係所需的時間</span><span class="sxs-lookup"><span data-stu-id="618ac-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="618ac-114">監視託管功能應用的所有伺服器的 CPU 使用方式、記憶體和速率</span><span class="sxs-lookup"><span data-stu-id="618ac-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="618ac-115">查看指標的即時流，包括功能應用的請求計數和延遲</span><span class="sxs-lookup"><span data-stu-id="618ac-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="618ac-116">使用[Analytics（分析）](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)搜索、查詢和創建函數資料的自訂圖表</span><span class="sxs-lookup"><span data-stu-id="618ac-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![計量瀏覽器](./media/metrics-explorer.png)

<span data-ttu-id="618ac-118">除了內置遙測之外，還可以生成自訂遙測。</span><span class="sxs-lookup"><span data-stu-id="618ac-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="618ac-119">以下程式碼片段使用函數應用的檢測金鑰集創建自訂遙測用戶端：</span><span class="sxs-lookup"><span data-stu-id="618ac-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="618ac-120">以下代碼測量將新行插入[Azure 表存儲](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)實例所需的時間：</span><span class="sxs-lookup"><span data-stu-id="618ac-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="618ac-121">將顯示生成的性能圖：</span><span class="sxs-lookup"><span data-stu-id="618ac-121">The resulting performance graph is shown:</span></span>

![自訂遙測](./media/custom-telemetry.png)

<span data-ttu-id="618ac-123">自訂遙測顯示插入新行的平均時間是 32.6 毫秒。</span><span class="sxs-lookup"><span data-stu-id="618ac-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="618ac-124">應用程式見解提供了一種功能強大、方便的方式來記錄有關無伺服器應用程式的詳細遙測資料。</span><span class="sxs-lookup"><span data-stu-id="618ac-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="618ac-125">您可以完全控制提供的跟蹤和日誌記錄級別。</span><span class="sxs-lookup"><span data-stu-id="618ac-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="618ac-126">您可以跟蹤自訂統計資訊，如事件、依賴項和網頁檢視。</span><span class="sxs-lookup"><span data-stu-id="618ac-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="618ac-127">最後，強大的分析使您能夠編寫詢問重要問題的查詢，並生成圖表和高級見解。</span><span class="sxs-lookup"><span data-stu-id="618ac-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="618ac-128">如需詳細資訊，請參閱[監視 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)。</span><span class="sxs-lookup"><span data-stu-id="618ac-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="618ac-129">[上一個](azure-functions.md)
>[下一個](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="618ac-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
