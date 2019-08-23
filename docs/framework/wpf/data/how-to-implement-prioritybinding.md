---
title: 作法：實作 PriorityBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: ad19db9d686469e3ade1ff188553fceb8d525674
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937438"
---
# <a name="how-to-implement-prioritybinding"></a>作法：實作 PriorityBinding
<xref:System.Windows.Data.PriorityBinding>在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] [運作方式] 中, 指定系結的清單。 系結清單的排序次序是從最高優先順序到最低優先順序。 如果在處理時, 最高優先順序的系結成功傳回值, 則不需要處理清單中的其他系結。 可能是最高優先順序的系結需要較長的時間才能進行評估, 則會使用成功傳回值的下一個最高優先順序, 直到較高優先權的系結成功傳回值為止。  
  
## <a name="example"></a>範例  
 為了示範如何<xref:System.Windows.Data.PriorityBinding>運作`AsyncDataSource` , 已使用下列三個屬性建立物件: `FastDP`、 `SlowerDP`和`SlowestDP`。  
  
 的 get 存取`FastDP`子會傳回`_fastDP`資料成員的值。  
  
 Get 存取`SlowerDP`子會等候3秒, 然後才傳回`_slowerDP`資料成員的值。  
  
 Get 存取`SlowestDP`子會等待5秒, 然後才傳回`_slowestDP`資料成員的值。  
  
> [!NOTE]
> 此範例僅供示範之用。 本[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]指導方針建議您不要定義的屬性, 其速度比欄位集還慢。 如需詳細資訊, 請參閱[在屬性和方法之間選擇](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100))。  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 屬性會`AsyncDS` 使用<xref:System.Windows.Data.PriorityBinding>系結至上述的: <xref:System.Windows.Controls.TextBlock.Text%2A>  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 當系結引擎處理<xref:System.Windows.Data.Binding>物件時, 它會以第一個<xref:System.Windows.Data.Binding>系結至`SlowestDP`屬性的開始。 當處理<xref:System.Windows.Data.Binding>這個時, 它不會成功傳回值, 因為它會進入5秒的睡眠狀態, 因此<xref:System.Windows.Data.Binding>會處理下一個元素。 下一個<xref:System.Windows.Data.Binding>未成功傳回值, 因為它正在睡眠3秒。 然後, 系結引擎會移至<xref:System.Windows.Data.Binding>下一個系結`FastDP`至屬性的元素。 這<xref:System.Windows.Data.Binding>會傳回值「快速值」。 <xref:System.Windows.Controls.TextBlock>現在會顯示值「快速值」。  
  
 經過3秒後, `SlowerDP`屬性會傳回值「較慢的值」。 <xref:System.Windows.Controls.TextBlock>然後會顯示值「較慢的值」。  
  
 經過5秒之後, `SlowestDP`屬性會傳回值「最慢的值」。 該系結具有最高的優先順序, 因為它會先列出。 <xref:System.Windows.Controls.TextBlock>現在會顯示值「最慢的值」。  
  
 如<xref:System.Windows.Data.PriorityBinding>需從系結中被視為成功傳回值的相關資訊, 請參閱。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
