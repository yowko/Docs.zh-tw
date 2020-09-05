---
ms.openlocfilehash: e9f769af6d85403c2a6f085cbc3462cf549adae9
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497457"
---
### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>WPF TreeViewItem 必須在 TreeView 內使用

#### <a name="details"></a>詳細資料

4.5 中引進一項變更，限制在 <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 外使用 <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> 項目。 在下列狀況下可能會發生這種情形：<ul><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> 的視覺化父代不是面板。 (針對 <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 產生的 <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> 會有一個面板作為其父代)</li><li><xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> 是 <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> 的子系，可作為清單控制項 (ListBox、DataGrid、ListView 等) 的「項目主控件」。 不需要啟用虛擬化。</li><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> 是項目捲動 (<code>ScrollUnit=&quot;Item&quot;</code>)。</li><li>使用者可呼叫 <code>VirtualizingStackPanel.MakeVisible(v)</code> 將項目 <code>v</code> 捲動至檢視中。 這可以透過數種方式明確或隱含完成；最常見的方式可能是直接按一下 <code>v</code> 以提供鍵盤焦點。</li><li>從 <code>v</code> 到 <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> 的視覺化父代鏈結會通過 <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName>。</li></ul>換句話說，在 <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 外使用 <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName>，然後使用者點選 <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> 的子系將其帶入檢視時，就會看到此問題。 如果 <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> 沒有可設定焦點的子系，則絕不會看到此問題。 例如，當 <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> 是 DataTemplate 的根項目時，就會遇到此問題。 遇到此問題時，WPF 架構內會出現 InvalidCastException。

#### <a name="suggestion"></a>建議

未來將針對此問題提供 Hotfix。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
