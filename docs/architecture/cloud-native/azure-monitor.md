---
title: Azure 監視器
description: 使用 Azure 監視器來查看您的系統是否正在執行。
ms.date: 07/05/2020
ms.openlocfilehash: 65e17740dba49c3ac3f6e13462897b5342da6710
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160966"
---
# <a name="azure-monitor"></a><span data-ttu-id="6eb2d-103">Azure 監視器</span><span class="sxs-lookup"><span data-stu-id="6eb2d-103">Azure Monitor</span></span>

<span data-ttu-id="6eb2d-104">除了在 Azure 中找到的雲端應用程式監視解決方案之外，其他任何雲端提供者都沒有成熟。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-104">No other cloud provider has as mature of a cloud application monitoring solution than that found in Azure.</span></span> <span data-ttu-id="6eb2d-105">Azure 監視器是設計用來提供系統狀態可見度的工具集合的一組傘名稱。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-105">Azure Monitor is an umbrella name for a collection of tools designed to provide visibility into the state of your system.</span></span> <span data-ttu-id="6eb2d-106">它可協助您瞭解雲端原生服務的執行狀況，並主動識別影響它們的問題。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-106">It helps you understand how your cloud-native services are performing and proactively identifies issues affecting them.</span></span> <span data-ttu-id="6eb2d-107">圖7-12 顯示 Azure 監視器的高階觀點。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-107">Figure 7-12 presents a high level of view of Azure Monitor.</span></span>

<span data-ttu-id="6eb2d-108">![Azure 監視器的高階觀點。 ](./media/azure-monitor.png)
**圖 7-12**。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-108">![High-level view of Azure Monitor.](./media/azure-monitor.png)
**Figure 7-12**.</span></span> <span data-ttu-id="6eb2d-109">Azure 監視器的高階觀點。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-109">High-level view of Azure Monitor.</span></span>

## <a name="gathering-logs-and-metrics"></a><span data-ttu-id="6eb2d-110">正在搜集記錄和計量</span><span class="sxs-lookup"><span data-stu-id="6eb2d-110">Gathering logs and metrics</span></span>

<span data-ttu-id="6eb2d-111">任何監視解決方案中的第一個步驟，就是盡可能收集最多的資料。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-111">The first step in any monitoring solution is to gather as much data as possible.</span></span> <span data-ttu-id="6eb2d-112">收集的資料越多，深入解析就越深入。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-112">The more data gathered, the deeper the insights.</span></span> <span data-ttu-id="6eb2d-113">傳統上的檢測系統很難。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-113">Instrumenting systems has traditionally been difficult.</span></span> <span data-ttu-id="6eb2d-114">簡易網路管理通訊協定 (SNMP) 是用來收集電腦層級資訊的黃金標準通訊協定，但需要大量的知識和設定。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-114">Simple Network Management Protocol (SNMP) was the gold standard protocol for collecting machine level information, but it required a great deal of knowledge and configuration.</span></span> <span data-ttu-id="6eb2d-115">幸運的是，這大部分的困難工作都已經消除，因為最常見的計量會由 Azure 監視器自動收集。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-115">Fortunately, much of this hard work has been eliminated as the most common metrics are gathered automatically by Azure Monitor.</span></span>

<span data-ttu-id="6eb2d-116">應用層級度量和事件無法自動檢測，因為它們是專屬於正在部署的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-116">Application level metrics and events aren't possible to instrument automatically because they're specific to the application being deployed.</span></span> <span data-ttu-id="6eb2d-117">為了收集這些計量，有可用來直接報告這類資訊的 [sdk 和 api](/azure/azure-monitor/app/api-custom-events-metrics) ，例如當客戶註冊或完成訂單時。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-117">In order to gather these metrics, there are [SDKs and APIs available](/azure/azure-monitor/app/api-custom-events-metrics) to directly report such information, such as when a customer signs up or completes an order.</span></span> <span data-ttu-id="6eb2d-118">例外狀況也可以透過 Application Insights 來捕捉並回報給 Azure 監視器。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-118">Exceptions can also be captured and reported back into Azure Monitor via Application Insights.</span></span> <span data-ttu-id="6eb2d-119">Sdk 支援在雲端原生應用程式（包括 Go、Python、JavaScript 和 .NET 語言）中找到的大部分語言。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-119">The SDKs support most every language found in Cloud Native Applications including Go, Python, JavaScript, and the .NET languages.</span></span>

<span data-ttu-id="6eb2d-120">收集應用程式狀態相關資訊的最終目標是確保您的終端使用者有良好的體驗。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-120">The ultimate goal of gathering information about the state of your application is to ensure that your end users have a good experience.</span></span> <span data-ttu-id="6eb2d-121">要告訴使用者是否遇到與 [在外部 web 測試之外](/azure/azure-monitor/app/monitor-web-app-availability)的問題，有何更好的方法？</span><span class="sxs-lookup"><span data-stu-id="6eb2d-121">What better way to tell if users are experiencing issues than doing [outside-in web tests](/azure/azure-monitor/app/monitor-web-app-availability)?</span></span> <span data-ttu-id="6eb2d-122">這些測試可以像是從全球各地的地點 ping 您的網站，或是讓代理程式登入網站並模擬使用者動作一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-122">These tests can be as simple as pinging your website from locations around the world or as involved as having agents log into the site and simulate user actions.</span></span>

## <a name="reporting-data"></a><span data-ttu-id="6eb2d-123">報告資料</span><span class="sxs-lookup"><span data-stu-id="6eb2d-123">Reporting data</span></span>

<span data-ttu-id="6eb2d-124">一旦收集資料之後，就可以將其操作、摘要並繪製成圖表，讓使用者能夠立即查看發生問題的時間。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-124">Once the data is gathered, it can be manipulated, summarized, and plotted into charts, which allow users to instantly see when there are problems.</span></span> <span data-ttu-id="6eb2d-125">您可以將這些圖表收集到儀表板或活頁簿中，這是一種多頁報表，其設計目的是要告訴有關系統某些方面的故事。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-125">These charts can be gathered into dashboards or into Workbooks, a multi-page report designed to tell a story about some aspect of the system.</span></span>

<span data-ttu-id="6eb2d-126">不需要一些人工智慧或機器學習，即可完成現代化的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-126">No modern application would be complete without some artificial intelligence or machine learning.</span></span> <span data-ttu-id="6eb2d-127">至此，您 [可以將資料傳遞](https://www.youtube.com/watch?v=Cuza-I1g9tw) 至 Azure 中的各種機器學習工具，讓您可以解壓縮其他隱藏的趨勢和資訊。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-127">To this end, data [can be passed](https://www.youtube.com/watch?v=Cuza-I1g9tw) to the various machine learning tools in Azure to allow you to extract trends and information that would otherwise be hidden.</span></span>

<span data-ttu-id="6eb2d-128">Application Insights 提供一種功能強大的 (類似 SQL 的) 查詢語言，稱為 *Kusto* ，可查詢記錄、摘要記錄，甚至繪製圖表。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-128">Application Insights provides a powerful (SQL-like) query language called *Kusto* that can query records, summarize them, and even plot charts.</span></span> <span data-ttu-id="6eb2d-129">例如，下列查詢會尋找2007年11月的所有記錄、依州/省將其分組，然後將前10個繪製為圓形圖。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-129">For example, the following query will locate all records for the month of November 2007, group them by state, and plot the top 10 as a pie chart.</span></span>

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

<span data-ttu-id="6eb2d-130">圖7-13 顯示此 Application Insights 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-130">Figure 7-13 shows the results of this Application Insights Query.</span></span>

<span data-ttu-id="6eb2d-131">![Application Insights 查詢結果 ](./media/application_insights_example.png)
 **圖 7-13**。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-131">![Application Insights query results](./media/application_insights_example.png)
**Figure 7-13**.</span></span> <span data-ttu-id="6eb2d-132">Application Insights 查詢結果。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-132">Application Insights query results.</span></span>

<span data-ttu-id="6eb2d-133">您可以 [使用遊樂場來試驗 Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples) 查詢。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-133">There is a [playground for experimenting with Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples) queries.</span></span> <span data-ttu-id="6eb2d-134">讀取 [範例查詢](/azure/kusto/query/samples) 也可以有意義。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-134">Reading [sample queries](/azure/kusto/query/samples) can also be instructive.</span></span>

## <a name="dashboards"></a><span data-ttu-id="6eb2d-135">儀表板</span><span class="sxs-lookup"><span data-stu-id="6eb2d-135">Dashboards</span></span>

<span data-ttu-id="6eb2d-136">有幾種不同的儀表板技術可用來呈現 Azure 監視器的資訊。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-136">There are several different dashboard technologies that may be used to surface the information from Azure Monitor.</span></span> <span data-ttu-id="6eb2d-137">或許最簡單的方式是直接在 Application Insights 中執行查詢，並將 [資料繪製到圖表](/azure/azure-monitor/learn/tutorial-app-dashboards)中。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-137">Perhaps the simplest is to just run queries in Application Insights and [plot the data into a chart](/azure/azure-monitor/learn/tutorial-app-dashboards).</span></span>

<span data-ttu-id="6eb2d-138">![內嵌于主要 Azure 儀表板 ](./media/azure_dashboard.png)
 **圖 7-14**中 Application Insights 圖表的範例。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-138">![An example of Application Insights charts embedded in the main Azure Dashboard](./media/azure_dashboard.png)
**Figure 7-14**.</span></span> <span data-ttu-id="6eb2d-139">在主要 Azure 儀表板中內嵌 Application Insights 圖表的範例。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-139">An example of Application Insights charts embedded in the main Azure Dashboard.</span></span>

<span data-ttu-id="6eb2d-140">然後，您可以透過使用儀表板功能，將這些圖表適當地內嵌在 Azure 入口網站中。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-140">These charts can then be embedded in the Azure portal proper through use of the dashboard feature.</span></span> <span data-ttu-id="6eb2d-141">對於具有更嚴格需求的使用者，例如能夠向下切入到數個階層的資料，Azure 監視器資料可以 [Power BI](https://powerbi.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-141">For users with more exacting requirements, such as being able to drill down into several tiers of data, Azure Monitor data is available to [Power BI](https://powerbi.microsoft.com/).</span></span> <span data-ttu-id="6eb2d-142">Power BI 是領先業界的企業級商業智慧工具，可以從許多不同的資料來源匯總資料。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-142">Power BI is an industry-leading, enterprise class, business intelligence tool that can aggregate data from many different data sources.</span></span>

![儀表板 Power BI 範例](./media/powerbidashboard.png)

<span data-ttu-id="6eb2d-144">**圖 7-15**。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-144">**Figure 7-15**.</span></span> <span data-ttu-id="6eb2d-145">儀表板 Power BI 範例。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-145">An example Power BI dashboard.</span></span>

## <a name="alerts"></a><span data-ttu-id="6eb2d-146">警示</span><span class="sxs-lookup"><span data-stu-id="6eb2d-146">Alerts</span></span>

<span data-ttu-id="6eb2d-147">有時候，擁有資料儀表板的許可權不足。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-147">Sometimes, having data dashboards is insufficient.</span></span> <span data-ttu-id="6eb2d-148">如果沒有人處於喚醒狀態以監看儀表板，則在問題解決或甚至偵測到問題之前，可能仍會有很多的時間。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-148">If nobody is awake to watch the dashboards, then it can still be many hours before a problem is addressed, or even detected.</span></span> <span data-ttu-id="6eb2d-149">至此，Azure 監視器也提供最高槽口的 [警示解決方案](/azure/azure-monitor/platform/alerts-overview)。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-149">To this end, Azure Monitor also provides a top notch [alerting solution](/azure/azure-monitor/platform/alerts-overview).</span></span> <span data-ttu-id="6eb2d-150">警示可以透過各式各樣的條件觸發，包括：</span><span class="sxs-lookup"><span data-stu-id="6eb2d-150">Alerts can be triggered by a wide range of conditions including:</span></span>

- <span data-ttu-id="6eb2d-151">計量值</span><span class="sxs-lookup"><span data-stu-id="6eb2d-151">Metric values</span></span>
- <span data-ttu-id="6eb2d-152">記錄搜尋查詢</span><span class="sxs-lookup"><span data-stu-id="6eb2d-152">Log search queries</span></span>
- <span data-ttu-id="6eb2d-153">活動記錄事件</span><span class="sxs-lookup"><span data-stu-id="6eb2d-153">Activity Log events</span></span>
- <span data-ttu-id="6eb2d-154">底層 Azure 平台健康情況</span><span class="sxs-lookup"><span data-stu-id="6eb2d-154">Health of the underlying Azure platform</span></span>
- <span data-ttu-id="6eb2d-155">網站可用性測試</span><span class="sxs-lookup"><span data-stu-id="6eb2d-155">Tests for web site availability</span></span>

<span data-ttu-id="6eb2d-156">觸發時，警示可以執行各種不同的工作。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-156">When triggered, the alerts can perform a wide variety of tasks.</span></span> <span data-ttu-id="6eb2d-157">簡單的說，警示可能只會傳送電子郵件通知給個別的郵寄清單或文字訊息。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-157">On the simple side, the alerts may just send an e-mail notification to a mailing list or a text message to an individual.</span></span> <span data-ttu-id="6eb2d-158">更多相關警示可能會在 PagerDuty 之類的工具中觸發工作流程，這會知道誰正在呼叫特定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-158">More involved alerts might trigger a workflow in a tool such as PagerDuty, which is aware of who is on call for a particular application.</span></span> <span data-ttu-id="6eb2d-159">警示可以在 [Microsoft Flow](https://flow.microsoft.com/) 中觸發動作，讓工作流程幾乎無限制的可能性。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-159">Alerts can trigger actions in [Microsoft Flow](https://flow.microsoft.com/) unlocking near limitless possibilities for workflows.</span></span>

<span data-ttu-id="6eb2d-160">由於系統會識別出警示的常見原因，因此可以使用警示的常見原因詳細資料，以及解決這些警示所需採取的步驟來增強警示。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-160">As common causes of alerts are identified, the alerts can be enhanced with details about the common causes of the alerts and the steps to take to resolve them.</span></span> <span data-ttu-id="6eb2d-161">高度成熟的雲端原生應用程式部署可能會選擇開始自我修復工作，這類工作會執行一些動作，例如從擴展集移除失敗的節點或觸發自動調整活動。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-161">Highly mature cloud-native application deployments may opt to kick off self-healing tasks, which perform actions such as removing failing nodes from a scale set or triggering an autoscaling activity.</span></span> <span data-ttu-id="6eb2d-162">最後，可能不再需要喚醒 >12AM-2AM 的待命人員來解決即時網站問題，因為系統將能夠自行調整以彌補或至少 limp，直到有人在下早上抵達工作為止。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-162">Eventually it may no longer be necessary to wake up on-call personnel at 2AM to resolve a live-site issue as the system will be able to adjust itself to compensate or at least limp along until somebody arrives at work the next morning.</span></span>

<span data-ttu-id="6eb2d-163">Azure 監視器會自動利用機器學習服務來瞭解已部署應用程式的正常指令引數。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-163">Azure Monitor automatically leverages machine learning to understand the normal operating parameters of deployed applications.</span></span> <span data-ttu-id="6eb2d-164">這可讓它偵測在其正常參數之外運作的服務。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-164">This enables it to detect services that are operating outside of their normal parameters.</span></span> <span data-ttu-id="6eb2d-165">例如，網站上的一般工作日流量可能是每分鐘10000個要求。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-165">For instance, the typical weekday traffic on the site might be 10,000 requests per minute.</span></span> <span data-ttu-id="6eb2d-166">然後，在指定的一周，每分鐘的要求數突然達到高度不尋常的20000要求。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-166">And then, on a given week, suddenly the number of requests hits a highly unusual 20,000 requests per minute.</span></span> <span data-ttu-id="6eb2d-167">[智慧型偵測](/azure/azure-monitor/app/proactive-diagnostics) 會注意到此差異與標準，並觸發警示。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-167">[Smart Detection](/azure/azure-monitor/app/proactive-diagnostics) will notice this deviation from the norm and trigger an alert.</span></span> <span data-ttu-id="6eb2d-168">同時，趨勢分析的智慧足以避免在預期流量負載時引發誤報。</span><span class="sxs-lookup"><span data-stu-id="6eb2d-168">At the same time, the trend analysis is smart enough to avoid firing false positives when the traffic load is expected.</span></span>

## <a name="references"></a><span data-ttu-id="6eb2d-169">參考資料</span><span class="sxs-lookup"><span data-stu-id="6eb2d-169">References</span></span>

- [<span data-ttu-id="6eb2d-170">Azure 監視器</span><span class="sxs-lookup"><span data-stu-id="6eb2d-170">Azure Monitor</span></span>](/azure/azure-monitor/overview)

>[!div class="step-by-step"]
><span data-ttu-id="6eb2d-171">[上一個](monitoring-azure-kubernetes.md) 
>[下一步](identity.md)</span><span class="sxs-lookup"><span data-stu-id="6eb2d-171">[Previous](monitoring-azure-kubernetes.md)
[Next](identity.md)</span></span>
