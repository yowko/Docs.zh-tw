---
title: Azure 監視器
description: 使用 Azure 監視器來查看系統正在運行。
ms.date: 02/05/2020
ms.openlocfilehash: 4e5ddba6c1c13dc65662a7748d4ae3a58a6a6f68
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805626"
---
# <a name="azure-monitor"></a><span data-ttu-id="40998-103">Azure 監視器</span><span class="sxs-lookup"><span data-stu-id="40998-103">Azure Monitor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="40998-104">沒有其他雲端供應商像 Azure 中那樣成熟雲端應用程式監視解決方案。</span><span class="sxs-lookup"><span data-stu-id="40998-104">No other cloud provider has as mature of a cloud application monitoring solution as that found in Azure.</span></span> <span data-ttu-id="40998-105">Azure 監視器是一系列工具的一個總括名稱,旨在提供對系統狀態的可見性、對任何問題的見解以及應用程式的優化。</span><span class="sxs-lookup"><span data-stu-id="40998-105">Azure Monitor is an umbrella name for a collection of tools designed to provide visibility into the state of your system, insights into any problems, and optimization of your application.</span></span>

<span data-ttu-id="40998-106">![Azure 監視器,一個工具的集合,用於深入瞭解雲原生應用程式的工作原理。](./media/azure-monitor.png)
**圖7-12**。</span><span class="sxs-lookup"><span data-stu-id="40998-106">![Azure Monitor, a collection to tools to provide insight into how a cloud-native application is functioning.](./media/azure-monitor.png)
**Figure 7-12**.</span></span> <span data-ttu-id="40998-107">Azure 監視器,一個工具的集合,用於深入瞭解雲原生應用程式的工作原理。</span><span class="sxs-lookup"><span data-stu-id="40998-107">Azure Monitor, a collection to tools to provide insight into how a cloud-native application is functioning.</span></span>

## <a name="gathering-logs-and-metrics"></a><span data-ttu-id="40998-108">收集記錄和指標</span><span class="sxs-lookup"><span data-stu-id="40998-108">Gathering logs and metrics</span></span>

<span data-ttu-id="40998-109">任何監視解決方案的第一步是收集盡可能多的數據。</span><span class="sxs-lookup"><span data-stu-id="40998-109">The first step in any monitoring solution is to gather as much data as possible.</span></span> <span data-ttu-id="40998-110">可以收集的數據越多,獲得的見解就越深。</span><span class="sxs-lookup"><span data-stu-id="40998-110">The more data that can be gathered, the deeper the insights that can be obtained.</span></span> <span data-ttu-id="40998-111">傳統上,檢測系統很困難。</span><span class="sxs-lookup"><span data-stu-id="40998-111">Instrumenting systems has traditionally been difficult.</span></span> <span data-ttu-id="40998-112">簡單網路管理協定(SNMP)是收集機器級資訊的黃金標準協定,但它需要大量的知識和配置。</span><span class="sxs-lookup"><span data-stu-id="40998-112">Simple Network Management Protocol (SNMP) was the gold standard protocol for collecting machine level information but it required a great deal of knowledge and configuring.</span></span> <span data-ttu-id="40998-113">幸運的是,由於 Azure 監視器會自動收集最常見的指標,因此許多辛勤工作已消除。</span><span class="sxs-lookup"><span data-stu-id="40998-113">Fortunately, much of this hard work has been eliminated as the most common metrics are gathered automatically by Azure Monitor.</span></span>

<span data-ttu-id="40998-114">應用程式等級指標和事件無法自動檢測,因為它們特定於要部署的應用程式。</span><span class="sxs-lookup"><span data-stu-id="40998-114">Application level metrics and events aren't possible to instrument automatically because they're specific to the application being deployed.</span></span> <span data-ttu-id="40998-115">為了收集這些指標,可以使用[SDK 和 API](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics)直接報告此類資訊,例如客戶註冊或完成訂單時。</span><span class="sxs-lookup"><span data-stu-id="40998-115">In order to gather these metrics, there are [SDKs and APIs available](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) to directly report such information, such as when a customer signs up or completes an order.</span></span> <span data-ttu-id="40998-116">還可以捕獲異常,並通過應用程式見解報告回 Azure 監視器。</span><span class="sxs-lookup"><span data-stu-id="40998-116">Exceptions can also be captured and reported back into Azure Monitor via Application Insights.</span></span> <span data-ttu-id="40998-117">SDK 支援雲本機應用程式中找到的大多數語言,包括 Go、Python、JAvaScript 和 .NET 語言。</span><span class="sxs-lookup"><span data-stu-id="40998-117">The SDKs support most every language found in Cloud Native Applications including Go, Python, JavaScript, and the .NET languages.</span></span>

<span data-ttu-id="40998-118">收集有關應用程式狀態資訊的最終目標是確保您的最終用戶獲得良好的體驗。</span><span class="sxs-lookup"><span data-stu-id="40998-118">The ultimate goal of gathering information about the state of your application is to ensure that your end users have a good experience.</span></span> <span data-ttu-id="40998-119">還有什麼比進行[外部 Web 測試](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)更好的方法來判斷使用者是否遇到問題?</span><span class="sxs-lookup"><span data-stu-id="40998-119">What better way to tell if users are experiencing issues than doing [outside-in web tests](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)?</span></span> <span data-ttu-id="40998-120">這些測試可以像從世界各地的位置 ping 網站一樣簡單,也可以像讓代理登錄到網站並類比使用者操作一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="40998-120">These tests can be as simple as pinging your website from locations around the world or as involved as having agents log into the site and simulate user actions.</span></span>

## <a name="reporting-data"></a><span data-ttu-id="40998-121">報告資料</span><span class="sxs-lookup"><span data-stu-id="40998-121">Reporting data</span></span>

<span data-ttu-id="40998-122">收集數據后,可以對其進行操作、匯總和繪製成圖表,從而允許使用者在出現問題時立即查看。</span><span class="sxs-lookup"><span data-stu-id="40998-122">Once the data is gathered, it can be manipulated, summarized, and plotted into charts, which allow users to instantly see when there are problems.</span></span> <span data-ttu-id="40998-123">這些圖表可以收集到儀錶板或工作簿中,這是一個多頁報告,旨在講述有關系統某些方面的故事。</span><span class="sxs-lookup"><span data-stu-id="40998-123">These charts can be gathered into dashboards or into Workbooks, a multi-page report designed to tell a story about some aspect of the system.</span></span>

<span data-ttu-id="40998-124">沒有人工智慧或機器學習,任何現代應用都不完整。</span><span class="sxs-lookup"><span data-stu-id="40998-124">No modern application would be complete without some artificial intelligence or machine learning.</span></span> <span data-ttu-id="40998-125">為此,[可以將資料傳遞到](https://www.youtube.com/watch?v=Cuza-I1g9tw)Azure 中的各種機器學習工具,以允許您提取其他將隱藏的趨勢和資訊。</span><span class="sxs-lookup"><span data-stu-id="40998-125">To this end, data [can be passed](https://www.youtube.com/watch?v=Cuza-I1g9tw) to the various machine learning tools in Azure to allow you to extract trends and information that would otherwise be hidden.</span></span>

<span data-ttu-id="40998-126">應用程式見解提供了一種稱為 Kusto 的強大查詢語言,可用於查找記錄、匯總記錄甚至繪圖圖表。</span><span class="sxs-lookup"><span data-stu-id="40998-126">Application Insights provides a powerful query language called Kusto that can be used to find records, summarize them, and even plot charts.</span></span> <span data-ttu-id="40998-127">例如,此查詢將查找 2007 年 11 月的所有記錄,按狀態對其進行分組,並將前 10 條列印為餅圖。</span><span class="sxs-lookup"><span data-stu-id="40998-127">For instance, this query will locate all the records for the month of November 2007, group them by state, and plot the top 10 as a pie chart.</span></span>

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

<span data-ttu-id="40998-128">![應用程式見解查詢](./media/azure-monitor.png)
**圖圖 7-13**的結果。</span><span class="sxs-lookup"><span data-stu-id="40998-128">![The result of the Application Insights Query](./media/azure-monitor.png)
**Figure 7-13**.</span></span> <span data-ttu-id="40998-129">應用程式見解查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="40998-129">The result of the Application Insights Query.</span></span>

<span data-ttu-id="40998-130">有一個[操場,嘗試Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples)查詢,這是一個夢幻般的地方,花一兩個小時。</span><span class="sxs-lookup"><span data-stu-id="40998-130">There is a [playground for experimenting with Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples) queries, which is a fantastic place to spend an hour or two.</span></span> <span data-ttu-id="40998-131">閱讀[示例查詢](https://docs.microsoft.com/azure/kusto/query/samples)也可以具有指導意義。</span><span class="sxs-lookup"><span data-stu-id="40998-131">Reading [sample queries](https://docs.microsoft.com/azure/kusto/query/samples) can also be instructive.</span></span>

## <a name="dashboards"></a><span data-ttu-id="40998-132">儀表板</span><span class="sxs-lookup"><span data-stu-id="40998-132">Dashboards</span></span>

<span data-ttu-id="40998-133">有幾種不同的儀錶板技術可用於顯示 Azure 監視器中的資訊。</span><span class="sxs-lookup"><span data-stu-id="40998-133">There are several different dashboard technologies that may be used to surface the information from Azure Monitor.</span></span> <span data-ttu-id="40998-134">也許最簡單的方法是在應用程式見解中執行查詢[,並將資料繪製到圖表中](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards)。</span><span class="sxs-lookup"><span data-stu-id="40998-134">Perhaps the simplest is to just run queries in Application Insights and [plot the data into a chart](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards).</span></span>

<span data-ttu-id="40998-135">![嵌入在主 Azure 儀](./media/azure-monitor.png)
表板**圖 7-14**中的應用程式見解圖表的範例。</span><span class="sxs-lookup"><span data-stu-id="40998-135">![An example of Application Insights charts embedded in the main Azure Dashboard](./media/azure-monitor.png)
**Figure 7-14**.</span></span> <span data-ttu-id="40998-136">嵌入在主 Azure 儀表板中的應用程式見解圖表的範例。</span><span class="sxs-lookup"><span data-stu-id="40998-136">An example of Application Insights charts embedded in the main Azure Dashboard.</span></span>

<span data-ttu-id="40998-137">然後,這些圖表可以通過使用儀錶板功能適當地嵌入 Azure 門戶中。</span><span class="sxs-lookup"><span data-stu-id="40998-137">These charts can then be embedded in the Azure portal proper through use of the dashboard feature.</span></span> <span data-ttu-id="40998-138">對於具有更嚴格要求(如能夠向下鑽取到多個資料層)的使用者[,Azure](https://powerbi.microsoft.com/)監視器資料可用於 Power BI 。</span><span class="sxs-lookup"><span data-stu-id="40998-138">For users with more exacting requirements, such as being able to drill down into several tiers of data, Azure Monitor data is available to [Power BI](https://powerbi.microsoft.com/).</span></span> <span data-ttu-id="40998-139">Power BI 是一種行業領先的企業級商業智慧工具,可以聚合來自許多不同的數據源的數據。</span><span class="sxs-lookup"><span data-stu-id="40998-139">Power BI is an industry-leading, enterprise class, business intelligence tool that can aggregate data from many different data sources.</span></span>

<span data-ttu-id="40998-140">![例如 Power](./media/azure-monitor.png)
BI 儀表板**圖 7-15**。</span><span class="sxs-lookup"><span data-stu-id="40998-140">![An example Power BI dashboard](./media/azure-monitor.png)
**Figure 7-15**.</span></span> <span data-ttu-id="40998-141">例如 Power BI 儀錶板。</span><span class="sxs-lookup"><span data-stu-id="40998-141">An example Power BI dashboard.</span></span>

## <a name="alerts"></a><span data-ttu-id="40998-142">警示</span><span class="sxs-lookup"><span data-stu-id="40998-142">Alerts</span></span>

<span data-ttu-id="40998-143">有時,數據儀錶板不足。</span><span class="sxs-lookup"><span data-stu-id="40998-143">Sometimes, having data dashboards is insufficient.</span></span> <span data-ttu-id="40998-144">如果沒有人醒著觀看儀錶板,則問題處理甚至檢測到仍可能需要數小時。</span><span class="sxs-lookup"><span data-stu-id="40998-144">If nobody is awake to watch the dashboards, then it can still be many hours before a problem is addressed, or even detected.</span></span> <span data-ttu-id="40998-145">此選項,Azure 監視器還提供一流的[警示解決方案](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview)。</span><span class="sxs-lookup"><span data-stu-id="40998-145">To this end, Azure Monitor also provides a top notch [alerting solution](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview).</span></span> <span data-ttu-id="40998-146">警示可以由多種條件觸發,包括:</span><span class="sxs-lookup"><span data-stu-id="40998-146">Alerts can be triggered by a wide range of conditions including:</span></span>

- <span data-ttu-id="40998-147">計量值</span><span class="sxs-lookup"><span data-stu-id="40998-147">Metric values</span></span>
- <span data-ttu-id="40998-148">記錄搜尋查詢</span><span class="sxs-lookup"><span data-stu-id="40998-148">Log search queries</span></span>
- <span data-ttu-id="40998-149">活動記錄事件</span><span class="sxs-lookup"><span data-stu-id="40998-149">Activity Log events</span></span>
- <span data-ttu-id="40998-150">基礎 Azure 平台健康情況</span><span class="sxs-lookup"><span data-stu-id="40998-150">Health of the underlying Azure platform</span></span>
- <span data-ttu-id="40998-151">網站可用性測試</span><span class="sxs-lookup"><span data-stu-id="40998-151">Tests for web site availability</span></span>

<span data-ttu-id="40998-152">觸發時,警報可以執行各種任務。</span><span class="sxs-lookup"><span data-stu-id="40998-152">When triggered, the alerts can perform a wide variety of tasks.</span></span> <span data-ttu-id="40998-153">簡單一方面,警報可能只是向郵件清單發送電子郵件通知或向個人發送簡訊。</span><span class="sxs-lookup"><span data-stu-id="40998-153">On the simple side, the alerts may just send an e-mail notification to a mailing list or a text message to an individual.</span></span> <span data-ttu-id="40998-154">涉及的警報越多,可能會觸發 PagerDuty 等工具中的工作流,因為 PagerDuty 知道誰正在呼叫特定應用程式。</span><span class="sxs-lookup"><span data-stu-id="40998-154">More involved alerts might trigger a workflow in a tool such as PagerDuty, which is aware of who is on call for a particular application.</span></span> <span data-ttu-id="40998-155">警報可以在[Microsoft Flow](https://flow.microsoft.com/)中觸發操作,從而在工作流中釋放幾乎無限的可能性。</span><span class="sxs-lookup"><span data-stu-id="40998-155">Alerts can trigger actions in [Microsoft Flow](https://flow.microsoft.com/) unlocking near limitless possibilities for workflows.</span></span>

<span data-ttu-id="40998-156">當識別警報的常見原因時,可以通過有關警報的常見原因以及解決這些問題的步驟的詳細資訊來增強警報。</span><span class="sxs-lookup"><span data-stu-id="40998-156">As common causes of alerts are identified, the alerts can be enhanced with details about the common causes of the alerts and the steps to take to resolve them.</span></span> <span data-ttu-id="40998-157">高度成熟的雲原生應用程式部署可能會選擇啟動自我修復任務,這些任務執行操作,例如從縮放集中刪除故障節點或觸發自動縮放活動。</span><span class="sxs-lookup"><span data-stu-id="40998-157">Highly mature cloud-native application deployments may opt to kick off self-healing tasks, which perform actions such as removing failing nodes from a scale set or triggering an autoscaling activity.</span></span> <span data-ttu-id="40998-158">最終,可能不再需要在淩晨 2 點叫醒待命人員來解決現場問題,因為系統將能夠調整自身以補償或至少跛行,直到第二天早上有人到達工作崗位。</span><span class="sxs-lookup"><span data-stu-id="40998-158">Eventually it may no longer be necessary to wake up on-call personnel at 2AM to resolve a live-site issue as the system will be able to adjust itself to compensate or at least limp along until somebody arrives at work the next morning.</span></span>

<span data-ttu-id="40998-159">Azure 監視器自動利用機器學習來瞭解已部署應用程式的正常操作參數。</span><span class="sxs-lookup"><span data-stu-id="40998-159">Azure Monitor automatically leverages machine learning to understand the normal operating parameters of deployed applications.</span></span> <span data-ttu-id="40998-160">這使它能夠檢測在其正常參數之外運行的服務。</span><span class="sxs-lookup"><span data-stu-id="40998-160">This enables it to detect services that are operating outside of their normal parameters.</span></span> <span data-ttu-id="40998-161">例如,網站上典型的工作日流量可能是每分鐘 10,000 個請求。</span><span class="sxs-lookup"><span data-stu-id="40998-161">For instance, the typical weekday traffic on the site might be 10,000 requests per minute.</span></span> <span data-ttu-id="40998-162">然後,在給定的一周內,請求數量突然達到每分鐘非常不尋常的 20,000 個請求。</span><span class="sxs-lookup"><span data-stu-id="40998-162">And then, on a given week, suddenly the number of requests hits a highly unusual 20,000 requests per minute.</span></span> <span data-ttu-id="40998-163">[智慧檢測](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics)將注意到這種偏離規範並觸發警報。</span><span class="sxs-lookup"><span data-stu-id="40998-163">[Smart Detection](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics) will notice this deviation from the norm and trigger an alert.</span></span> <span data-ttu-id="40998-164">同時,趨勢分析足夠聰明,以避免在流量負載預期時觸發誤報。</span><span class="sxs-lookup"><span data-stu-id="40998-164">At the same time, the trend analysis is smart enough to avoid firing false positives when the traffic load is expected.</span></span>

## <a name="references"></a><span data-ttu-id="40998-165">參考</span><span class="sxs-lookup"><span data-stu-id="40998-165">References</span></span>

- [<span data-ttu-id="40998-166">Azure 監視器</span><span class="sxs-lookup"><span data-stu-id="40998-166">Azure Monitor</span></span>](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
><span data-ttu-id="40998-167">[前一個](monitoring-azure-kubernetes.md)
>[下一個](identity.md)</span><span class="sxs-lookup"><span data-stu-id="40998-167">[Previous](monitoring-azure-kubernetes.md)
[Next](identity.md)</span></span>
