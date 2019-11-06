---
title: 如何：實作 PriorityBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 343b0aca4736905f3a0cbff5a0f76b170da0c920
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459791"
---
# <a name="how-to-implement-prioritybinding"></a>如何：實作 PriorityBinding
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 <xref:System.Windows.Data.PriorityBinding> 會藉由指定系結的清單來運作。 系結清單的排序次序是從最高優先順序到最低優先順序。 如果在處理時，最高優先順序的系結成功傳回值，則不需要處理清單中的其他系結。 可能是最高優先順序的系結需要較長的時間才能進行評估，則會使用成功傳回值的下一個最高優先順序，直到較高優先權的系結成功傳回值為止。  
  
## <a name="example"></a>範例  
 為了示範 <xref:System.Windows.Data.PriorityBinding> 的運作方式，已建立具有下列三個屬性的 `AsyncDataSource` 物件： `FastDP`、`SlowerDP`和 `SlowestDP`。  
  
 `FastDP` 的 get 存取子會傳回 `_fastDP` 資料成員的值。  
  
 `SlowerDP` 的 get 存取子會等待3秒，再傳回 `_slowerDP` 資料成員的值。  
  
 `SlowestDP` 的 get 存取子會等待5秒，再傳回 `_slowestDP` 資料成員的值。  
  
> [!NOTE]
> 此範例僅供示範之用。 .NET 指導方針建議定義的屬性，其速度比欄位集還慢。 如需詳細資訊，請參閱[在屬性和方法之間選擇](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100))。  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性會使用 <xref:System.Windows.Data.PriorityBinding>系結至上述 `AsyncDS`：  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 當系結引擎處理 <xref:System.Windows.Data.Binding> 物件時，它會從系結至 `SlowestDP` 屬性的第一個 <xref:System.Windows.Data.Binding>開始。 處理此 <xref:System.Windows.Data.Binding> 時，它不會成功傳回值，因為它正在睡眠5秒，因此會處理下一個 <xref:System.Windows.Data.Binding> 元素。 下一個 <xref:System.Windows.Data.Binding> 未成功傳回值，因為它正在睡眠3秒。 然後，系結引擎會移至下一個系結至 `FastDP` 屬性的 <xref:System.Windows.Data.Binding> 元素。 此 <xref:System.Windows.Data.Binding> 會傳回值「快速值」。 <xref:System.Windows.Controls.TextBlock> 現在會顯示值「快速值」。  
  
 經過3秒之後，`SlowerDP` 屬性會傳回值「較慢的值」。 然後，<xref:System.Windows.Controls.TextBlock> 會顯示「較慢的值」值。  
  
 經過5秒之後，`SlowestDP` 屬性會傳回值「最慢的值」。 該系結具有最高的優先順序，因為它會先列出。 <xref:System.Windows.Controls.TextBlock> 現在會顯示值「最慢的值」。  
  
 如需從系結中被視為成功傳回值的相關資訊，請參閱 <xref:System.Windows.Data.PriorityBinding>。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
