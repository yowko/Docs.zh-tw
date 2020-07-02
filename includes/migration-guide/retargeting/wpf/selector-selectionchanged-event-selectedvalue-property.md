---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614599"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Selector 的 SelectionChanged 事件和 SelectedValue 屬性

#### <a name="details"></a>詳細資料

從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.Primitives.Selector> 在其選取項目變更時，一律會先更新其 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性的值，再引發 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件。 這會讓 SelectedValue 屬性與其他的選取項目屬性一致 (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> 和 <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>)，它們會在引發事件前予以更新。<p/>在 .NET Framework 4.7 和舊版中，在大部分情況下，更新 SelectedValue 會發生在事件之前，但如果選取項目變更是由於變更 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性所造成，則會發生在事件之後。

#### <a name="suggestion"></a>建議

以 .NET Framework 4.7.1 或更新版本為目標的應用程式可透過在應用程式組態檔的 `<runtime>` 區段中新增下列內容來選擇退出此變更，並使用舊版行為：

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

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
