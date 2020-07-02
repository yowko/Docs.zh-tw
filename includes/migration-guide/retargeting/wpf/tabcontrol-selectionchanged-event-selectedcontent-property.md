---
ms.openlocfilehash: dfdb62e8dd6db67d4fd12aba93928f4615e3f284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614607"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>TabControl SelectionChanged 事件和 SelectedContent 屬性

#### <a name="details"></a>詳細資料

從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.TabControl> 會在其選取項目變更時先更新其 <xref:System.Windows.Controls.TabControl.SelectedContent> 屬性的值，再引發 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件。在 .NET Framework 4.7 和舊版中，更新 SelectedContent 發生在事件之後。

#### <a name="suggestion"></a>建議

以 .NET Framework 4.7.1 或更新版本為目標的應用程式可透過在應用程式組態檔的 `<runtime>` 區段中新增下列內容來選擇退出此變更，並使用舊版行為：

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

以 .NET Framework 4.7 或舊版為目標但在 .NET Framework 4.7.1 或更新版本上執行的應用程式，只要在應用程式組態檔的 `<runtime>` 區段新增下列程式行，就能啟用新行為：

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7.1       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
