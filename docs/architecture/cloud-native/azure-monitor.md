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
# <a name="azure-monitor"></a>Azure 監視器

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

沒有其他雲端供應商像 Azure 中那樣成熟雲端應用程式監視解決方案。 Azure 監視器是一系列工具的一個總括名稱,旨在提供對系統狀態的可見性、對任何問題的見解以及應用程式的優化。

![Azure 監視器,一個工具的集合,用於深入瞭解雲原生應用程式的工作原理。](./media/azure-monitor.png)
**圖7-12**。 Azure 監視器,一個工具的集合,用於深入瞭解雲原生應用程式的工作原理。

## <a name="gathering-logs-and-metrics"></a>收集記錄和指標

任何監視解決方案的第一步是收集盡可能多的數據。 可以收集的數據越多,獲得的見解就越深。 傳統上,檢測系統很困難。 簡單網路管理協定(SNMP)是收集機器級資訊的黃金標準協定,但它需要大量的知識和配置。 幸運的是,由於 Azure 監視器會自動收集最常見的指標,因此許多辛勤工作已消除。

應用程式等級指標和事件無法自動檢測,因為它們特定於要部署的應用程式。 為了收集這些指標,可以使用[SDK 和 API](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics)直接報告此類資訊,例如客戶註冊或完成訂單時。 還可以捕獲異常,並通過應用程式見解報告回 Azure 監視器。 SDK 支援雲本機應用程式中找到的大多數語言,包括 Go、Python、JAvaScript 和 .NET 語言。

收集有關應用程式狀態資訊的最終目標是確保您的最終用戶獲得良好的體驗。 還有什麼比進行[外部 Web 測試](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)更好的方法來判斷使用者是否遇到問題? 這些測試可以像從世界各地的位置 ping 網站一樣簡單,也可以像讓代理登錄到網站並類比使用者操作一樣簡單。

## <a name="reporting-data"></a>報告資料

收集數據后,可以對其進行操作、匯總和繪製成圖表,從而允許使用者在出現問題時立即查看。 這些圖表可以收集到儀錶板或工作簿中,這是一個多頁報告,旨在講述有關系統某些方面的故事。

沒有人工智慧或機器學習,任何現代應用都不完整。 為此,[可以將資料傳遞到](https://www.youtube.com/watch?v=Cuza-I1g9tw)Azure 中的各種機器學習工具,以允許您提取其他將隱藏的趨勢和資訊。

應用程式見解提供了一種稱為 Kusto 的強大查詢語言,可用於查找記錄、匯總記錄甚至繪圖圖表。 例如,此查詢將查找 2007 年 11 月的所有記錄,按狀態對其進行分組,並將前 10 條列印為餅圖。

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

![應用程式見解查詢](./media/azure-monitor.png)
**圖圖 7-13**的結果。 應用程式見解查詢的結果。

有一個[操場,嘗試Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples)查詢,這是一個夢幻般的地方,花一兩個小時。 閱讀[示例查詢](https://docs.microsoft.com/azure/kusto/query/samples)也可以具有指導意義。

## <a name="dashboards"></a>儀表板

有幾種不同的儀錶板技術可用於顯示 Azure 監視器中的資訊。 也許最簡單的方法是在應用程式見解中執行查詢[,並將資料繪製到圖表中](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards)。

![嵌入在主 Azure 儀](./media/azure-monitor.png)
表板**圖 7-14**中的應用程式見解圖表的範例。 嵌入在主 Azure 儀表板中的應用程式見解圖表的範例。

然後,這些圖表可以通過使用儀錶板功能適當地嵌入 Azure 門戶中。 對於具有更嚴格要求(如能夠向下鑽取到多個資料層)的使用者[,Azure](https://powerbi.microsoft.com/)監視器資料可用於 Power BI 。 Power BI 是一種行業領先的企業級商業智慧工具,可以聚合來自許多不同的數據源的數據。

![例如 Power](./media/azure-monitor.png)
BI 儀表板**圖 7-15**。 例如 Power BI 儀錶板。

## <a name="alerts"></a>警示

有時,數據儀錶板不足。 如果沒有人醒著觀看儀錶板,則問題處理甚至檢測到仍可能需要數小時。 此選項,Azure 監視器還提供一流的[警示解決方案](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview)。 警示可以由多種條件觸發,包括:

- 計量值
- 記錄搜尋查詢
- 活動記錄事件
- 基礎 Azure 平台健康情況
- 網站可用性測試

觸發時,警報可以執行各種任務。 簡單一方面,警報可能只是向郵件清單發送電子郵件通知或向個人發送簡訊。 涉及的警報越多,可能會觸發 PagerDuty 等工具中的工作流,因為 PagerDuty 知道誰正在呼叫特定應用程式。 警報可以在[Microsoft Flow](https://flow.microsoft.com/)中觸發操作,從而在工作流中釋放幾乎無限的可能性。

當識別警報的常見原因時,可以通過有關警報的常見原因以及解決這些問題的步驟的詳細資訊來增強警報。 高度成熟的雲原生應用程式部署可能會選擇啟動自我修復任務,這些任務執行操作,例如從縮放集中刪除故障節點或觸發自動縮放活動。 最終,可能不再需要在淩晨 2 點叫醒待命人員來解決現場問題,因為系統將能夠調整自身以補償或至少跛行,直到第二天早上有人到達工作崗位。

Azure 監視器自動利用機器學習來瞭解已部署應用程式的正常操作參數。 這使它能夠檢測在其正常參數之外運行的服務。 例如,網站上典型的工作日流量可能是每分鐘 10,000 個請求。 然後,在給定的一周內,請求數量突然達到每分鐘非常不尋常的 20,000 個請求。 [智慧檢測](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics)將注意到這種偏離規範並觸發警報。 同時,趨勢分析足夠聰明,以避免在流量負載預期時觸發誤報。

## <a name="references"></a>參考

- [Azure 監視器](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[前一個](monitoring-azure-kubernetes.md)
>[下一個](identity.md)
