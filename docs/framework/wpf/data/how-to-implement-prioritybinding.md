---
title: 如何：實作 PriorityBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: a7729ec3d06ec701cf2194bed5d90b5bed76573a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077378"
---
# <a name="how-to-implement-prioritybinding"></a>如何：實作 PriorityBinding
<xref:System.Windows.Data.PriorityBinding> 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的運作方式是指定繫結的清單。 繫結清單的順序是從最高優先順序到最低優先順序。 如果最高的優先權繫結傳回值已成功處理時就永遠不需要處理清單中的其他繫結。 它可能是最高的優先權繫結需要很長的時間，要評估的情況下，優先順序較高的繫結成功地傳回值之前，都會使用下一個最高優先順序成功地傳回值。  
  
## <a name="example"></a>範例  
 示範如何<xref:System.Windows.Data.PriorityBinding>運作`AsyncDataSource`物件已建立具有下列三個屬性： `FastDP`， `SlowerDP`，和`SlowestDP`。  
  
 Get 存取子`FastDP`傳回的值`_fastDP`資料成員。  
  
 Get 存取子`SlowerDP`等候 3 秒後，再傳回`_slowerDP`資料成員。  
  
 Get 存取子`SlowestDP`等候傳回的值之前的 5 秒`_slowestDP`資料成員。  
  
> [!NOTE]
>  此範例僅供示範之用。 [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]指導方針，建議您不要定義速度較慢的欄位集合會比的屬性。 如需詳細資訊，請參閱 < [NIB： 選擇之間的屬性和方法](https://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af)。  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A>屬性繫結至上述`AsyncDS`使用<xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 當繫結引擎會處理<xref:System.Windows.Data.Binding>物件，它的第一個開頭<xref:System.Windows.Data.Binding>，它繫結至`SlowestDP`屬性。 當這<xref:System.Windows.Data.Binding>是處理，它不會傳回值已成功因為它正在睡眠中 5 秒，因此下一步<xref:System.Windows.Data.Binding>處理項目。 下一步<xref:System.Windows.Data.Binding>不會傳回值已成功因為睡眠 3 秒。 然後，繫結引擎會移到下一步<xref:System.Windows.Data.Binding>項目，繫結至`FastDP`屬性。 這<xref:System.Windows.Data.Binding>傳回值 「 快速值 」。 <xref:System.Windows.Controls.TextBlock>現在會顯示 「 快速值 」 的值。  
  
 在 3 秒過後之後,`SlowerDP`屬性會傳回 「 較慢的值 」 的值。 <xref:System.Windows.Controls.TextBlock>接著會顯示 「 速度較慢的值 」 的值。  
  
 在 5 秒過後之後,`SlowestDP`屬性會傳回值 「 最慢值 」。 該繫結具有最高優先權，因為它會先列出。 <xref:System.Windows.Controls.TextBlock>現在會顯示 「 最慢值 」 的值。  
  
 請參閱<xref:System.Windows.Data.PriorityBinding>如需有關什麼會被視為成功的傳回值，從繫結資訊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
