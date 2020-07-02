---
ms.openlocfilehash: f4ff938b2d0e9ead481fdf239aed8a6b918a99b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620092"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ObservableCollection&lt;T&gt;.Move 的 ListBoxItem IsSelected 繫結問題

#### <a name="details"></a>詳細資料

針對繫結至 <xref:System.Windows.Controls.ListBox?displayProperty=fullName> 且已選取項目的集合呼叫 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> 或 <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)>，可能會在未來選取或取消選取 <xref:System.Windows.Controls.ListBox?displayProperty=fullName> 項目時導致不穩定的行為。

#### <a name="suggestion"></a>建議

呼叫 <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> 和 <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> 而不是 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> 可解決此問題。 此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
