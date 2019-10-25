---
ms.openlocfilehash: 4254cceab0048341b32fe5babf53b5ea3e5a52d6
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "72846996"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>工作流程 XOML 定義和 SqlTrackingService 快取索引鍵已從 MD5 變更為 SHA256

|   |   |
|---|---|
|詳細資料|工作流程執行階段會保留 XOML 中定義之工作流程定義的快取。 SqlTrackingService 也會保留以字串作為索引鍵的快取。 這些快取會依包含總和檢查碼雜湊值的值作為索引鍵。 在 .NET Framework 4.7.2 及更早版本中，這個總和檢查碼雜湊會使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。 從 .NET Framework 4.8 開始，使用的演算法是 SHA256。這項變更應該不會有相容性問題，因為每次工作流程執行時間和 SqlTrackingService 啟動時，都會重新計算這些值。 不過，如有需要，我們也提供可讓客戶還原回使用舊版雜湊演算法的方式。|
|建議|如果這項變更在執行工作流程時會造成問題，請嘗試設定其中一個 <code>AppContext</code> 參數 (或兩者)：<ul><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; 設為 True。</li><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; 設為 True.</li></ul>程式碼：<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>或在組態檔中 (必須位於建立 <xref:System.Workflow.Runtime.WorkflowRuntime> 物件之應用程式的組態檔中)：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.8|
|輸入|正在重定目標|
