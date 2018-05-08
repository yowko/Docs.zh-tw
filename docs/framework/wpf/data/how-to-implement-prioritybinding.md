---
title: 如何：實作 PriorityBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: cf0ed5c2b55358d3a583ac89e307b23b3ab08a9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-prioritybinding"></a>如何：實作 PriorityBinding
<xref:System.Windows.Data.PriorityBinding> 在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的運作方式是指定繫結的清單。 繫結清單被依優先順序從高到最低優先順序。 如果最高優先權繫結的傳回值已成功處理時就永遠不需要處理清單中的其他繫結。 這可能是最高的優先權繫結需要很長的時間進行評估的案例，優先順序較高的繫結成功傳回值之前，都會使用下一個最高優先順序成功傳回值。  
  
## <a name="example"></a>範例  
 若要示範如何<xref:System.Windows.Data.PriorityBinding>運作方式、`AsyncDataSource`物件已建立具有下列三個屬性： `FastDP`， `SlowerDP`，和`SlowestDP`。  
  
 Get 存取子的`FastDP`傳回的值`_fastDP`資料成員。  
  
 Get 存取子的`SlowerDP`3 秒後再傳回的值會等到`_slowerDP`資料成員。  
  
 Get 存取子的`SlowestDP`等待 5 秒鐘，再傳回`_slowestDP`資料成員。  
  
> [!NOTE]
>  此範例僅供示範之用。 [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]指導方針，建議您不要定義速度較慢比欄位集的屬性。 如需詳細資訊，請參閱[NIB： 選擇之間指定屬性和方法](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af)。  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A>屬性繫結至上述`AsyncDS`使用<xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 當繫結引擎處理<xref:System.Windows.Data.Binding>物件，與第一個啟動<xref:System.Windows.Data.Binding>，它繫結至`SlowestDP`屬性。 當這<xref:System.Windows.Data.Binding>是處理，但是不會傳回值已成功因為它正在睡眠中 5 秒，因此下一步<xref:System.Windows.Data.Binding>處理項目。 下一步<xref:System.Windows.Data.Binding>沒有傳回值已成功因為睡眠 3 秒。 繫結引擎，然後移到下一個<xref:System.Windows.Data.Binding>元素，其繫結至`FastDP`屬性。 這<xref:System.Windows.Data.Binding>傳回"Fast Value"的值。 <xref:System.Windows.Controls.TextBlock>現在會顯示 「 快速值 」 的值。  
  
 在 3 秒超過之後`SlowerDP`屬性會傳回值 「 速度較慢的值 」。 <xref:System.Windows.Controls.TextBlock>然後顯示值"慢 Value"。  
  
 在 5 秒超過之後`SlowestDP`屬性會傳回值 「 最慢的值 」。 因為它會先列出，該繫結具有最高優先權。 <xref:System.Windows.Controls.TextBlock>現在會顯示 「 最慢的值 」 的值。  
  
 請參閱<xref:System.Windows.Data.PriorityBinding>如需有關什麼被視為成功的傳回值，從繫結資訊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
