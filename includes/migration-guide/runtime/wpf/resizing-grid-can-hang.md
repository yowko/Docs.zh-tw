---
ms.openlocfilehash: 86169b5c9a20678647153c951550e590a5bce588
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622231"
---
### <a name="resizing-a-grid-can-hang"></a>調整方格大小可能會當機

#### <a name="details"></a>詳細資料

在下列情況下，<code>T:System.Windows.Controls.Grid</code> 配置期間可能會發生無限迴圈：<ul><li>資料列定義包含兩個數據 \* 列，同時宣告 MinHeight 和 MaxHeight。</li><li>\*-Rows 的內容不會超過對應的 MaxHeight</li><li>第一個 MinHeight (加上任何其他固定或自動的資料列) 超過方格的可用高度</li><li>應用程式將目標設為 .NET Framework 4.7，或藉由設定 <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code> 選擇新增 4.7 配置演算法</li></ul>迴圈也會發生在兩個以上的資料列，或資料行的類似案例中。 此問題已在 .NET Framework 4.7.1 中修正。

#### <a name="suggestion"></a>建議

升級至 .NET Framework 4.7.1。  或者，如果您不需要 4.7 配置演算法，可以使用下列組態設定：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.7|
|類型|執行階段|
