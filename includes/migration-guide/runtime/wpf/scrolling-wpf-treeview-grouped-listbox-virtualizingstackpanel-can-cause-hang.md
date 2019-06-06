---
ms.openlocfilehash: 53fc2a51a7995e9b6ad43e28429313d2aea9abf1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379250"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-result-in-an-unresponsive-application"></a>在 VirtualizingStackPanel 中捲動 WPF TreeView 或群組 ListBox 可能會導致應用程式停止回應

|   |   |
|---|---|
|詳細資料|使用 .NET Framework v4.5 時，如果檢視區有邊界 (例如在 <xref:System.Windows.Controls.TreeView?displayProperty=name> 中的項目之間或在 ItemsPresenter 項目上)，在虛擬化堆疊面板中捲動 WPF <xref:System.Windows.Controls.TreeView?displayProperty=name> 可能會造成應用程式停止回應。 此外，在某些情況下，即使沒有邊界，檢視中不同大小的項目也可能會造成不穩定的情況。|
|建議|您可以升級至 .NET Framework 4.5.1 來避免此錯誤 (bug)。 或者，如果所有包含的項目大小都相同，您也可以從虛擬化堆疊面板內的檢視集合 (例如 <xref:System.Windows.Controls.TreeView?displayProperty=name>) 移除邊界。|
|範圍|主要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
