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
# <a name="azure-monitor"></a>Azure 監視器

除了在 Azure 中找到的雲端應用程式監視解決方案之外，其他任何雲端提供者都沒有成熟。 Azure 監視器是設計用來提供系統狀態可見度的工具集合的一組傘名稱。 它可協助您瞭解雲端原生服務的執行狀況，並主動識別影響它們的問題。 圖7-12 顯示 Azure 監視器的高階觀點。

![Azure 監視器的高階觀點。 ](./media/azure-monitor.png)
**圖 7-12**。 Azure 監視器的高階觀點。

## <a name="gathering-logs-and-metrics"></a>正在搜集記錄和計量

任何監視解決方案中的第一個步驟，就是盡可能收集最多的資料。 收集的資料越多，深入解析就越深入。 傳統上的檢測系統很難。 簡易網路管理通訊協定 (SNMP) 是用來收集電腦層級資訊的黃金標準通訊協定，但需要大量的知識和設定。 幸運的是，這大部分的困難工作都已經消除，因為最常見的計量會由 Azure 監視器自動收集。

應用層級度量和事件無法自動檢測，因為它們是專屬於正在部署的應用程式。 為了收集這些計量，有可用來直接報告這類資訊的 [sdk 和 api](/azure/azure-monitor/app/api-custom-events-metrics) ，例如當客戶註冊或完成訂單時。 例外狀況也可以透過 Application Insights 來捕捉並回報給 Azure 監視器。 Sdk 支援在雲端原生應用程式（包括 Go、Python、JavaScript 和 .NET 語言）中找到的大部分語言。

收集應用程式狀態相關資訊的最終目標是確保您的終端使用者有良好的體驗。 要告訴使用者是否遇到與 [在外部 web 測試之外](/azure/azure-monitor/app/monitor-web-app-availability)的問題，有何更好的方法？ 這些測試可以像是從全球各地的地點 ping 您的網站，或是讓代理程式登入網站並模擬使用者動作一樣簡單。

## <a name="reporting-data"></a>報告資料

一旦收集資料之後，就可以將其操作、摘要並繪製成圖表，讓使用者能夠立即查看發生問題的時間。 您可以將這些圖表收集到儀表板或活頁簿中，這是一種多頁報表，其設計目的是要告訴有關系統某些方面的故事。

不需要一些人工智慧或機器學習，即可完成現代化的應用程式。 至此，您 [可以將資料傳遞](https://www.youtube.com/watch?v=Cuza-I1g9tw) 至 Azure 中的各種機器學習工具，讓您可以解壓縮其他隱藏的趨勢和資訊。

Application Insights 提供一種功能強大的 (類似 SQL 的) 查詢語言，稱為 *Kusto* ，可查詢記錄、摘要記錄，甚至繪製圖表。 例如，下列查詢會尋找2007年11月的所有記錄、依州/省將其分組，然後將前10個繪製為圓形圖。

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

圖7-13 顯示此 Application Insights 查詢的結果。

![Application Insights 查詢結果 ](./media/application_insights_example.png)
 **圖 7-13**。 Application Insights 查詢結果。

您可以 [使用遊樂場來試驗 Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples) 查詢。 讀取 [範例查詢](/azure/kusto/query/samples) 也可以有意義。

## <a name="dashboards"></a>儀表板

有幾種不同的儀表板技術可用來呈現 Azure 監視器的資訊。 或許最簡單的方式是直接在 Application Insights 中執行查詢，並將 [資料繪製到圖表](/azure/azure-monitor/learn/tutorial-app-dashboards)中。

![內嵌于主要 Azure 儀表板 ](./media/azure_dashboard.png)
 **圖 7-14**中 Application Insights 圖表的範例。 在主要 Azure 儀表板中內嵌 Application Insights 圖表的範例。

然後，您可以透過使用儀表板功能，將這些圖表適當地內嵌在 Azure 入口網站中。 對於具有更嚴格需求的使用者，例如能夠向下切入到數個階層的資料，Azure 監視器資料可以 [Power BI](https://powerbi.microsoft.com/)。 Power BI 是領先業界的企業級商業智慧工具，可以從許多不同的資料來源匯總資料。

![儀表板 Power BI 範例](./media/powerbidashboard.png)

**圖 7-15**。 儀表板 Power BI 範例。

## <a name="alerts"></a>警示

有時候，擁有資料儀表板的許可權不足。 如果沒有人處於喚醒狀態以監看儀表板，則在問題解決或甚至偵測到問題之前，可能仍會有很多的時間。 至此，Azure 監視器也提供最高槽口的 [警示解決方案](/azure/azure-monitor/platform/alerts-overview)。 警示可以透過各式各樣的條件觸發，包括：

- 計量值
- 記錄搜尋查詢
- 活動記錄事件
- 底層 Azure 平台健康情況
- 網站可用性測試

觸發時，警示可以執行各種不同的工作。 簡單的說，警示可能只會傳送電子郵件通知給個別的郵寄清單或文字訊息。 更多相關警示可能會在 PagerDuty 之類的工具中觸發工作流程，這會知道誰正在呼叫特定的應用程式。 警示可以在 [Microsoft Flow](https://flow.microsoft.com/) 中觸發動作，讓工作流程幾乎無限制的可能性。

由於系統會識別出警示的常見原因，因此可以使用警示的常見原因詳細資料，以及解決這些警示所需採取的步驟來增強警示。 高度成熟的雲端原生應用程式部署可能會選擇開始自我修復工作，這類工作會執行一些動作，例如從擴展集移除失敗的節點或觸發自動調整活動。 最後，可能不再需要喚醒 >12AM-2AM 的待命人員來解決即時網站問題，因為系統將能夠自行調整以彌補或至少 limp，直到有人在下早上抵達工作為止。

Azure 監視器會自動利用機器學習服務來瞭解已部署應用程式的正常指令引數。 這可讓它偵測在其正常參數之外運作的服務。 例如，網站上的一般工作日流量可能是每分鐘10000個要求。 然後，在指定的一周，每分鐘的要求數突然達到高度不尋常的20000要求。 [智慧型偵測](/azure/azure-monitor/app/proactive-diagnostics) 會注意到此差異與標準，並觸發警示。 同時，趨勢分析的智慧足以避免在預期流量負載時引發誤報。

## <a name="references"></a>參考資料

- [Azure 監視器](/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[上一個](monitoring-azure-kubernetes.md) 
>[下一步](identity.md)
