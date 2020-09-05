---
ms.openlocfilehash: d23d7821e19b9d7f2db13a6bfdf868a8414cf721
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497739"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>在具有不同像素高度之項目的簡單列表中進行項目捲動

#### <a name="details"></a>詳細資料

<xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> 使用虛擬化 (<code>IsVirtualizing=true</code>) 及項目捲動 (<code>ScrollUnit=Item</code>) 顯示集合時，以及捲動控制項以顯示高度 (以像素為單位) 與其相鄰項目不同的項目時，<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> 會逐一查看集合中的所有項目。 UI 在此反覆運算期間沒有回應;如果集合很大，這可視為停止回應。 即使在先前的 .NET Framework 版本中，也會在其他情況下進行反復專案。 例如，在下列情況會發生這種情況：如果在發現像素高度不同的項目時進行像素捲動 (<code>ScrollUnit=Pixel</code>)，以及如果在發現子系項目數與其相鄰項目不同的項目時進行階層式資料項目捲動 (例如，在已啟用群組的 <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 或 <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> 中)。針對項目捲動和不同像素高度的情況，.NET Framework 4.6.1 中引進了逐一查看，以修正階層式資料配置中的 Bug。  如果是單層式資料 (沒有階層)，則不需要逐一查看，而且 .NET Framework 4.6.2 在此情況下不會這麼做。

#### <a name="suggestion"></a>建議

如果在 .NET Framework 4.6.1 中出現逐一查看行為，但舊版本中並未出現 (亦即，如果 <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> 是在具有不同像素高度之項目的簡單列表中進行項目捲動)，則有兩種解決方式：<ol><li>安裝 .NET Framework 4.6.2。</li><li>安裝 .NET Framework 4.6.1 的 Hotfix HR 1605。</li></ol>

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.6.1|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.VirtualizingStackPanel`

-->
