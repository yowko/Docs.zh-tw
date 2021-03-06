---
ms.openlocfilehash: 31ada197db36be192317e32a37a353d375d9cc65
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497042"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>在 VirtualizingStackPanel 中捲動 WPF TreeView 或群組 ListBox 可能會造成停止回應

#### <a name="details"></a>詳細資料

在 .NET Framework v4.5 中，如果檢視區有邊界 (例如在 <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 中的項目之間或在 ItemsPresenter 項目上)，在虛擬化堆疊面板中捲動 WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 可能會造成停止回應。 此外，在某些情況下，即使沒有邊界，檢視中不同大小的項目也可能會造成不穩定的情況。

#### <a name="suggestion"></a>建議

您可以升級至 .NET Framework 4.5.1 來避免此錯誤 (bug)。 或者，如果所有包含的項目大小都相同，您也可以從虛擬化堆疊面板內的檢視集合 (例如 <xref:System.Windows.Controls.TreeView?displayProperty=fullName>) 移除邊界。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |主要|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)`

-->
