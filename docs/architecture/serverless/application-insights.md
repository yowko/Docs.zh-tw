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
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="9d4bc-103">使用 Application Insights 進行遙測</span><span class="sxs-lookup"><span data-stu-id="9d4bc-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="9d4bc-104">[Application Insights](/azure/application-insights) 是無伺服器的診斷平臺，可讓開發人員偵測、分級和診斷 web 應用程式、行動應用程式、桌面應用程式和微服務中的問題。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-104">[Application Insights](/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="9d4bc-105">只要在入口網站中翻轉切換開關，您就可以開啟函式應用程式的 Application Insights。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="9d4bc-106">Application Insights 可提供這些功能，您不需要設定伺服器或設定自己的資料庫。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="9d4bc-107">所有 Application Insights 的功能都會以服務的形式提供，並自動與您的應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Application Insights 標誌](./media/application-insights-logo.png)

<span data-ttu-id="9d4bc-109">將 Application Insights 新增至現有的應用程式，就像在您的應用程式設定中新增檢測金鑰一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="9d4bc-110">使用 Application Insights 您可以：</span><span class="sxs-lookup"><span data-stu-id="9d4bc-110">With Application Insights you can:</span></span>

- <span data-ttu-id="9d4bc-111">根據計量數目、函式調用數目、執行函式所花的時間，以及例外狀況，建立自訂圖表和警示</span><span class="sxs-lookup"><span data-stu-id="9d4bc-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="9d4bc-112">分析失敗和伺服器例外狀況</span><span class="sxs-lookup"><span data-stu-id="9d4bc-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="9d4bc-113">依作業深入探索效能，並測量呼叫協力廠商相依性所花費的時間</span><span class="sxs-lookup"><span data-stu-id="9d4bc-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="9d4bc-114">監視裝載函式應用程式之所有伺服器的 CPU 使用量、記憶體和速率</span><span class="sxs-lookup"><span data-stu-id="9d4bc-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="9d4bc-115">觀看計量的即時資料流，包括函數應用程式的要求計數和延遲</span><span class="sxs-lookup"><span data-stu-id="9d4bc-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="9d4bc-116">使用 [分析](/azure/application-insights/app-insights-analytics) 來搜尋、查詢及建立函數資料的自訂圖表</span><span class="sxs-lookup"><span data-stu-id="9d4bc-116">Use [Analytics](/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![計量瀏覽器](./media/metrics-explorer.png)

<span data-ttu-id="9d4bc-118">除了內建遙測之外，也可以產生自訂遙測。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="9d4bc-119">下列程式碼片段會使用函式應用程式的檢測金鑰集來建立自訂遙測用戶端：</span><span class="sxs-lookup"><span data-stu-id="9d4bc-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="9d4bc-120">下列程式碼會測量將新的資料列插入至 [Azure 資料表儲存體](/azure/cosmos-db/table-storage-overview) 實例所需的時間長度：</span><span class="sxs-lookup"><span data-stu-id="9d4bc-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="9d4bc-121">產生的效能圖表如下所示：</span><span class="sxs-lookup"><span data-stu-id="9d4bc-121">The resulting performance graph is shown:</span></span>

![自訂遙測](./media/custom-telemetry.png)

<span data-ttu-id="9d4bc-123">自訂遙測會顯示插入新資料列的平均時間是32.6 毫秒。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="9d4bc-124">Application Insights 提供了一種功能強大且方便的方式，可記錄有關無伺服器應用程式的詳細遙測資料。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="9d4bc-125">您可以完整控制所提供的追蹤和記錄層級。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="9d4bc-126">您可以追蹤自訂統計資料，例如事件、相依性和頁面流覽。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="9d4bc-127">最後，強大的分析可讓您撰寫查詢，以提出重要的問題並產生圖表和先進的見解。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="9d4bc-128">如需詳細資訊，請參閱[監視 Azure Functions](/azure/azure-functions/functions-monitoring)。</span><span class="sxs-lookup"><span data-stu-id="9d4bc-128">For more information, see [Monitor Azure Functions](/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9d4bc-129">[上一個](azure-functions.md) 
>[下一步](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="9d4bc-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
