---
ms.openlocfilehash: b761cb699c4677f815835cdab9c6aa3039f5bb38
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235322"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectiontmove"></a>ListBoxItem IsSelected binding issue with ObservableCollection\<T>.Move

|   |   |
|---|---|
|詳細資料|針對繫結至 <xref:System.Windows.Controls.ListBox?displayProperty=name> 且已選取項目的集合呼叫 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> 或 <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)>，可能會在未來選取或取消選取 <xref:System.Windows.Controls.ListBox?displayProperty=name> 項目時導致不穩定的行為。|
|建議|呼叫 <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> 和 <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> 而不是 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> 可解決此問題。 此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。|
|範圍|次要|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
