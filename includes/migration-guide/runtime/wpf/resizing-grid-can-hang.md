---
ms.openlocfilehash: 8dc1b4d94d01813a8124d1340b50fa78a9b157f8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496302"
---
### <a name="resizing-a-grid-can-hang"></a>調整方格大小可能會當機

#### <a name="details"></a>詳細資料

在下列情況下，<code>T:System.Windows.Controls.Grid</code> 配置期間可能會發生無限迴圈：<ul><li>資料列定義包含兩個數據 \* 列，同時宣告 MinHeight 和 MaxHeight。</li><li>-資料列的內容 \* 不會超過對應的 MaxHeight</li><li>第一個 MinHeight (加上任何其他固定或自動的資料列) 超過方格的可用高度</li><li>應用程式將目標設為 .NET Framework 4.7，或藉由設定 <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code> 選擇新增 4.7 配置演算法</li></ul>迴圈也會發生在兩個以上的資料列，或在類似的資料行案例中。 此問題已在 .NET Framework 4.7.1 中修正。

#### <a name="suggestion"></a>建議

升級至 .NET Framework 4.7.1。  或者，如果您不需要 4.7 配置演算法，可以使用下列組態設定：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.7|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
