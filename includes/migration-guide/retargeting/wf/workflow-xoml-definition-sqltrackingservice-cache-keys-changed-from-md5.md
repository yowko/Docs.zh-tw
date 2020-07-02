---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617795"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>工作流程 XOML 定義和 SqlTrackingService 快取索引鍵已從 MD5 變更為 SHA256

#### <a name="details"></a>詳細資料

工作流程執行階段會保留 XOML 中定義之工作流程定義的快取。 SqlTrackingService 也會保留以字串作為索引鍵的快取。 這些快取會依包含總和檢查碼雜湊值的值作為索引鍵。 在 .NET Framework 4.7.2 及更早版本中，這個總和檢查碼雜湊會使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。 從 .NET Framework 4.8 開始，使用的演算法是 SHA256。這項變更應該不會有相容性問題，因為每次工作流程執行時間和 SqlTrackingService 啟動時，都會重新計算這些值。 不過，如有需要，我們也提供可讓客戶還原回使用舊版雜湊演算法的方式。

#### <a name="suggestion"></a>建議

如果這項變更在執行工作流程時會造成問題，請嘗試設定其中一個 `AppContext` 參數 (或兩者)：

- &quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; 設為 True。
- &quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; 設為 True.
在程式碼中：

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

或在組態檔中 (必須位於建立 <xref:System.Workflow.Runtime.WorkflowRuntime> 物件之應用程式的組態檔中)：

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.8         |
| 類型    | 正在重定目標 |
