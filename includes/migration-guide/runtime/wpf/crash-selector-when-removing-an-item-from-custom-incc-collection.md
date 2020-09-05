---
ms.openlocfilehash: f50022d9a7bacd7be40fe3050ced26e7c25cf7aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497824"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>從自訂 INCC 集合中移除項目時，選取器發生損毀

#### <a name="details"></a>詳細資料

在下列狀況中可能發生 <code>T:System.InvalidOperationException</code>：<ul><li><code>T:System.Windows.Controls.Primitives.Selector</code> 的 ItemsSource 是具有 <code>T:System.Collections.Specialized.INotifyCollectionChanged</code> 自訂實作的集合。</li><li>已從集合中移除選取的項目。</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> 具有 <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (表示未知的位置)。</li></ul>例外狀況的呼叫堆疊開頭為：at System.Windows.Threading.Dispatcher.VerifyAccess() at System.Windows.DependencyObject.GetValue(DependencyProperty dp) at System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element)。在 .NET Framework 4.5 中，如果應用程式有超過一個以上的發送器執行緒，可能會發生此例外狀況。 在 .NET Framework 4.7 中，具有單一發送器執行緒的應用程式也可能會發生此例外狀況。 此問題已在 .NET Framework 4.7.1 中修正。

#### <a name="suggestion"></a>建議

升級至 .NET Framework 4.7.1。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.7|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
