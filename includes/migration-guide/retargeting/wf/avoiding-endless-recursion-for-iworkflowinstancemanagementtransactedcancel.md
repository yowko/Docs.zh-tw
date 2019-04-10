---
ms.openlocfilehash: 5850e3359dab6503d5745a2266c7bf77780e5cc0
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760787"
---
### <a name="avoiding-endless-recursion-for-iworkflowinstancemanagementtransactedcancel-and-iworkflowinstancemanagementtransactedterminate"></a>避免 IWorkflowInstanceManagement.TransactedCancel 與 IWorkflowInstanceManagement.TransactedTerminate 的無止盡遞迴

|   |   |
|---|---|
|詳細資料|在某些情況下，若使用 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedCancel%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedTerminate%2A?displayProperty=nameWithType> API 取消或終止工作流程服務執行個體，當 <code>Workflow</code> 執行階段因為處理要求的過程，而嘗試保有該服務執行個體時，工作流程執行個體可能會出現因為無止盡遞迴而發生堆疊溢位。 若工作流程執行個體的狀態是正在等待某些其他未完成的 WCF 要求進入至另一個服務才能完成，就會發生此問題。作業 <code>TransactedCancel</code> 和 <code>TransactedTerminate</code> 會為該工作流程服務執行個體，建立已排入佇列的工作項目。 處理 <code>TransactedCancel/TransactedTerminate</code> 要求的過程中，不會執行這些工作項目。 因為工作流程服務執行個體正忙於等候其他未完成的 WCF 要求完成，所以建立的工作項目會維持在佇列中。 <code>TransactedCancel/TransactedTerminate</code> 作業已完成，且控制權已回到用戶端。 當交易與嘗試認可的 <code>TransactedCancel/TransactedTerminate</code> 作業相關聯時，它需要保有該工作流程服務執行個體的狀態。 但因為執行個體仍有未完成的 <code>WCF</code>要求，所以工作流程執行階段無法保有該工作流程服務執行個體，因而發生無止盡的遞迴迴圈而導致堆疊溢位。因為 <code>TransactedCancel</code> 與 <code>TransactedTerminate</code> 只會在記憶體中建立工作項目，所以交易存在的事實並沒有任何影響。 復原交易並不會捨棄該工作項目。為解決此問題，從 .NET Framework 4.7.2 起已引進了 <code>AppSetting</code>，其可新增至工作流程服務的 <code>web.config/app.config</code>，告知它可忽略 <code>TransactedCancel</code> 與 <code>TransactedTerminate</code> 的交易。 如此即可讓交易在無須等待要保有工作流程執行個體的情況下進行認可。此功能的 AppSetting 名稱為 <code>microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate</code>。 值 <code>true</code> 表示應忽略該交易，以避免堆疊溢位。 此 AppSetting 的預設值為 <code>false</code>，因此不會影響現有的工作流程服務執行個體。|
|建議|若目前使用 AppFabric 或另一個 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> 用戶端，且在嘗試取消或終止工作流程執行個體時，在工作流程服務執行個體中發生了堆疊溢位，您可以將下列內容加入工作流程服務的 web.config/app.config 檔案之 <code>&lt;appSettings&gt;</code> 區段中：<pre><code class="lang-xml">&lt;add key=&quot;microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate&quot; value=&quot;true&quot;/&gt;&#13;&#10;</code></pre>若未遇到問題，則不需要執行這項動作。|
|範圍|Edge|
|版本|4.7.2|
|類型|正在重定目標|

