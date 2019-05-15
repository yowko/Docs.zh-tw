---
title: Application Insights-無伺服器應用程式
description: Application Insights 是一個無伺服器的診斷平台，可讓開發人員偵測、 分級和診斷 web 應用程式、 行動裝置應用程式、 傳統型應用程式和微服務中的問題。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 1f5b99fba448c2c1c12139524ffdcd3708b3c956
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643369"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="68c6f-103">使用 Application Insights 的遙測</span><span class="sxs-lookup"><span data-stu-id="68c6f-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="68c6f-104">[Application Insights](https://docs.microsoft.com/azure/application-insights)是無伺服器的診斷平台，可讓開發人員可以偵測、 分級和診斷 web 應用程式、 行動裝置應用程式、 傳統型應用程式和微服務中的問題。</span><span class="sxs-lookup"><span data-stu-id="68c6f-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="68c6f-105">您可以開啟 Application Insights 的函式應用程式只要在入口網站中開關。</span><span class="sxs-lookup"><span data-stu-id="68c6f-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="68c6f-106">Application Insights 會提供所有這些功能，您不必設定伺服器，或將您自己的資料庫設定。</span><span class="sxs-lookup"><span data-stu-id="68c6f-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="68c6f-107">服務會自動與您的應用程式整合，提供所有 Application Insights 的功能。</span><span class="sxs-lookup"><span data-stu-id="68c6f-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Application Insights 標誌](./media/application-insights-logo.png)

<span data-ttu-id="68c6f-109">將 Application Insights 加入現有的應用程式是簡單，只要將檢測金鑰新增至您的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="68c6f-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="68c6f-110">使用 Application Insights 中，您可以：</span><span class="sxs-lookup"><span data-stu-id="68c6f-110">With Application Insights you can:</span></span>

* <span data-ttu-id="68c6f-111">建立自訂圖表和計量，例如函式引動過程數目為基礎的警示，請執行函式和例外狀況所花費的時間</span><span class="sxs-lookup"><span data-stu-id="68c6f-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
* <span data-ttu-id="68c6f-112">分析失敗和伺服器例外狀況</span><span class="sxs-lookup"><span data-stu-id="68c6f-112">Analyze failures and server exceptions</span></span>
* <span data-ttu-id="68c6f-113">向下鑽研到效能的作業和測量呼叫協力廠商相依性所花費的時間</span><span class="sxs-lookup"><span data-stu-id="68c6f-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
* <span data-ttu-id="68c6f-114">在裝載您的函式應用程式的所有伺服器監視 CPU 使用量、 記憶體和費率</span><span class="sxs-lookup"><span data-stu-id="68c6f-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
* <span data-ttu-id="68c6f-115">檢視即時資料流的度量，包括要求計數和延遲函式應用程式</span><span class="sxs-lookup"><span data-stu-id="68c6f-115">View a live stream of metrics including request count and latency for your function apps</span></span>
* <span data-ttu-id="68c6f-116">使用[Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)搜尋，查詢和建立您的函式資料的自訂圖表</span><span class="sxs-lookup"><span data-stu-id="68c6f-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![計量瀏覽器](./media/metrics-explorer.png)

<span data-ttu-id="68c6f-118">除了內建遙測，它也可產生自訂的遙測資料。</span><span class="sxs-lookup"><span data-stu-id="68c6f-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="68c6f-119">下列程式碼片段會建立自訂的遙測用戶端使用的設定函式應用程式的檢測金鑰：</span><span class="sxs-lookup"><span data-stu-id="68c6f-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="68c6f-120">下列程式碼可讓您測量插入新資料列需要多久[Azure 表格儲存體](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)執行個體：</span><span class="sxs-lookup"><span data-stu-id="68c6f-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="68c6f-121">產生的效能圖表所示：</span><span class="sxs-lookup"><span data-stu-id="68c6f-121">The resulting performance graph is shown:</span></span>

![自訂遙測](./media/custom-telemetry.png)

<span data-ttu-id="68c6f-123">自訂的遙測會顯示插入新的資料列的平均時間為 32.6 毫秒。</span><span class="sxs-lookup"><span data-stu-id="68c6f-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="68c6f-124">Application Insights 提供強大、 便利的方式來記錄詳細的遙測，有關無伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="68c6f-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="68c6f-125">您可以完整控制的追蹤層級，並記錄，提供。</span><span class="sxs-lookup"><span data-stu-id="68c6f-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="68c6f-126">您可以追蹤自訂統計資料，例如事件、 相依性及頁面檢視。</span><span class="sxs-lookup"><span data-stu-id="68c6f-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="68c6f-127">最後，功能強大的分析可讓您撰寫查詢，以提出重要問題，並產生圖表和進階的深入解析。</span><span class="sxs-lookup"><span data-stu-id="68c6f-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="68c6f-128">如需詳細資訊，請參閱 <<c0> [ 監視 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)。</span><span class="sxs-lookup"><span data-stu-id="68c6f-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="68c6f-129">[上一頁](azure-functions.md)
>[下一頁](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="68c6f-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
