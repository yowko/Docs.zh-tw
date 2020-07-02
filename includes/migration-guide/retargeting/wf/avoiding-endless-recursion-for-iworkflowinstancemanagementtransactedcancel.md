---
ms.openlocfilehash: daf09748e69e70ad982bcee14461b66579f3bb87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614393"
---
### <a name="avoiding-endless-recursion-for-iworkflowinstancemanagementtransactedcancel-and-iworkflowinstancemanagementtransactedterminate"></a>避免 IWorkflowInstanceManagement.TransactedCancel 與 IWorkflowInstanceManagement.TransactedTerminate 的無止盡遞迴

#### <a name="details"></a>詳細資料

在某些情況下，若使用 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedCancel%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedTerminate%2A?displayProperty=nameWithType> API 取消或終止工作流程服務執行個體，當 `Workflow` 執行階段因為處理要求的過程，而嘗試保有該服務執行個體時，工作流程執行個體可能會出現因為無止盡遞迴而發生堆疊溢位。 如果工作流程實例處於等待其他服務的其他未完成 WCF 要求的狀態，就會發生此問題。 `TransactedCancel`和 `TransactedTerminate` 作業會建立針對工作流程服務實例排入佇列的工作專案。 處理 `TransactedCancel/TransactedTerminate` 要求的過程中，不會執行這些工作項目。 因為工作流程服務執行個體正忙於等候其他未完成的 WCF 要求完成，所以建立的工作項目會維持在佇列中。 `TransactedCancel/TransactedTerminate` 作業已完成，且控制權已回到用戶端。 當交易與嘗試認可的 `TransactedCancel/TransactedTerminate` 作業相關聯時，它需要保有該工作流程服務執行個體的狀態。 但因為執行個體仍有未完成的 `WCF`要求，所以工作流程執行階段無法保有該工作流程服務執行個體，因而發生無止盡的遞迴迴圈而導致堆疊溢位。因為 `TransactedCancel` 與 `TransactedTerminate` 只會在記憶體中建立工作項目，所以交易存在的事實並沒有任何影響。 復原交易並不會捨棄該工作項目。為解決此問題，從 .NET Framework 4.7.2 起已引進了 `AppSetting`，其可新增至工作流程服務的 `web.config/app.config`，告知它可忽略 `TransactedCancel` 與 `TransactedTerminate` 的交易。 這可讓交易認可，而不需要等候工作流程實例保存。 這項功能的 AppSetting 名為 `microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate` 。 值 `true` 表示應忽略該交易，以避免堆疊溢位。 此 AppSetting 的預設值為 `false`，因此不會影響現有的工作流程服務執行個體。

#### <a name="suggestion"></a>建議

若目前使用 AppFabric 或另一個 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> 用戶端，且在嘗試取消或終止工作流程執行個體時，在工作流程服務執行個體中發生了堆疊溢位，您可以將下列內容加入工作流程服務的 web.config/app.config 檔案之 `<appSettings>` 區段中：

<pre><code class="lang-xml">&lt;add key=&quot;microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate&quot; value=&quot;true&quot;/&gt;&#13;&#10;</code></pre>

若未遇到問題，則不需要執行這項動作。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |
