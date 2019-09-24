---
title: Azure 監視器
description: 使用 Azure 監視器來取得系統的可見度。
ms.date: 09/23/2019
ms.openlocfilehash: 20048792e95ef1f6e75551cdd0d3571f972f6c14
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214100"
---
# <a name="azure-monitor"></a>Azure 監視器 

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

沒有其他雲端提供者的雲端應用程式監視解決方案成熟，如同在 Azure 中找到的一樣。 Azure 監視器是一組工具集合的資訊，其設計目的是要提供系統狀態的可見度，並深入瞭解您的應用程式的任何問題與優化。 

![Azure 監視器，這是工具的集合，可讓您深入瞭解雲端原生應用程式的運作方式。**圖 7-9**。 ](./media/azure-monitor.png)
 Azure 監視器，這是工具的集合，可讓您深入瞭解雲端原生應用程式的運作方式。

## <a name="gathering-logs-and-metrics"></a>收集記錄和計量

任何監視解決方案中的第一個步驟，是盡可能收集最多的資料。 可以收集的資料愈多，可取得的深入解析就愈深入。 在傳統上，檢測系統並不容易。 簡易網路管理通訊協定（SNMP）是用來收集機器層級資訊的黃金標準通訊協定，但它需要大量的知識和設定。 幸好，大部分的這項困難的工作都已消除，因為最常見的計量會由 Azure 監視器自動收集。

應用層級計量和事件無法自動檢測，因為它們是在要部署之應用程式的本機。 為了收集這些計量，有可用來直接報告這類資訊的[sdk 和 api](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) ，例如當客戶註冊或完成訂單時。 例外狀況也可以透過 Application Insights 加以捕捉並回報給 Azure 監視器。 Sdk 支援最多在雲端原生應用程式（包括 Go、Python、JavaScript 和 .NET 語言）中找到的所有語言。

收集應用程式狀態相關資訊的最終目標，是要確保您的終端使用者擁有良好的體驗。 判斷使用者是否遇到問題的更好方法，比[在外部 web 測試中](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)執行？ 這些測試可以像是從世界各地 ping 網站，或讓代理程式登入網站並執行動作一樣簡單。

## <a name="reporting-data"></a>報告資料

收集資料之後，就可以操作、摘要，並將其繪製成圖表，讓使用者可以在發生問題時立即查看。 這些圖表可以收集到儀表板或活頁簿中，這是一種多頁報表，設計用來告訴有關系統某些層面的故事。

不需要某些人工智慧或機器學習，即可完成現代化應用程式。 為此，您[可以將資料傳遞](https://www.youtube.com/watch?v=Cuza-I1g9tw)至 Azure 中的各種機器學習工具，讓您可以將其他隱藏的趨勢和資訊解壓縮。

Application Insights 提供一種強大的查詢語言，稱為 Kusto，可用來尋找記錄、匯總它們，甚至繪製圖表。 例如，此查詢會找出2007年11月的所有記錄、依州/省分組，然後將前10個圖繪製為圓形圖。

```
StormEvents 
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart 
```

![Application Insights 查詢](./media/azure-monitor.png)
的結果**圖 7-10**。 Application Insights 查詢的結果。

有一個[遊樂場可用於實驗 Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples)查詢，這是一個很棒的地方來花上一小時或兩個。 閱讀[範例查詢](https://docs.microsoft.com/azure/kusto/query/samples)也會有意義。

## <a name="dashboards"></a>儀表板

有數種不同的儀表板技術可用來呈現 Azure 監視器的資訊。 最簡單的方式，就是只在 Application Insights 中執行查詢，並將[資料繪製到圖表](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards)中。 

![內嵌在主要 Azure 儀表板](./media/azure-monitor.png)
**圖 7-11**中 Application Insights 圖表的範例。 內嵌在主要 Azure 儀表板中 Application Insights 圖表的範例。

然後您可以使用儀表板功能，將這些圖表內嵌在 Azure 入口網站中。 對於具有更嚴格需求的使用者，例如能夠向下切入到數個資料層 Azure 監視器資料可供[Power BI](https://powerbi.microsoft.com/)。 Power BI 是業界領先的企業級商業智慧工具，可以從許多不同的資料來源匯總資料。

![Power BI 儀表板](./media/azure-monitor.png)
**圖 7-12**的範例。 Power BI 儀表板範例。

## <a name="alerts"></a>警示

有時候，擁有資料儀表板的空間不足。 如果沒有人進行喚醒來監看儀表板，則在問題解決或甚至偵測到之前，仍然可能需要數小時的時間。 為此，Azure 監視器也會提供最高的槽口[警示解決方案](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview)。 警示可由各種不同的條件觸發，包括：

* 度量值
* 記錄搜尋查詢
* 活動記錄事件
* 基礎 Azure 平臺的健全狀況
* 網站可用性的測試

觸發時，警示可以執行各種不同的工作。 在簡單的情況下，警示可能只會傳送電子郵件通知給郵寄清單或文字訊息給個人。 更多相關警示可能會在 PagerDuty 之類的工具中觸發工作流程，這知道誰正在呼叫特定應用程式。 警示可以在[Microsoft Flow](https://flow.microsoft.com/)解除鎖定工作流程幾乎無限制的可能性中觸發動作。

當識別出常見的警示原因時，可以利用警示的常見原因和解決這些警示的步驟，來增強警示。 成熟的雲端原生應用程式部署可能會選擇啟動自我修復工作，這些工作會執行一些動作，例如從擴展集移除失敗的節點或觸發自動調整活動。 最後，您可能不再需要在12AM-2AM 喚醒待命人員以解決即時網站問題，因為系統能夠自行調整以補償或至少 limp，直到有人在下一個早上抵達工作為止。 

Azure 監視器會自動利用機器學習服務來瞭解已部署應用程式的一般指令引數。 這可讓它偵測在其一般參數之外運作的服務。 例如，網站上的一般工作日流量可能是每分鐘10000個要求。 然後，在指定的一周，突然要求數達到每分鐘非常不尋常的20000要求。 [智慧型偵測](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics)會注意到此偏差與標準，並觸發警示。 同時，趨勢分析的智慧足以避免在預期流量負載時引發誤報。  

>[!div class="step-by-step"]
>[上一頁](monitoring-azure-kubernetes.md)
>[下一頁](identity.md)
