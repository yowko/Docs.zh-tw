---
title: 使用 DrawingVisual 物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
ms.openlocfilehash: 4e6fc89b64f7b0acc1a0077708d567eb97e2868e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962835"
---
# <a name="using-drawingvisual-objects"></a>使用 DrawingVisual 物件
本主題提供如何<xref:System.Windows.Media.DrawingVisual> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在視覺圖層中使用物件的總覽。  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>DrawingVisual 物件  
 <xref:System.Windows.Media.DrawingVisual>是輕量繪圖類別, 可用來呈現圖形、影像或文字。 此類別之所以被視為輕量型，是因為它不提供版面配置或事件處理，這使它有更好的效能。 基於此原因，繪圖適合背景或美工圖案。  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual 主機容器  
 若要使用<xref:System.Windows.Media.DrawingVisual>物件, 您必須建立物件的主機容器。 主機容器物件必須衍生自<xref:System.Windows.FrameworkElement>類別, 以提供<xref:System.Windows.Media.DrawingVisual>類別缺少的版面配置和事件處理支援。 主機容器物件不會顯示任何可見的屬性，因為其主要目的是要包含子物件。 不過, 主機<xref:System.Windows.UIElement.Visibility%2A>容器的屬性必須設定為<xref:System.Windows.Visibility.Visible>, 否則, 將不會顯示其任何子項目。  
  
 當您建立視覺物件的主機容器物件時, 必須將視覺物件參考儲存在中<xref:System.Windows.Media.VisualCollection>。 <xref:System.Windows.Media.VisualCollection.Add%2A>使用方法, 將視覺物件新增至主機容器。 在下列範例中, 會建立主機容器物件, 並將三個視覺物件加入其<xref:System.Windows.Media.VisualCollection>中。  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> 如需先前程式碼範例出處的完整程式碼範例，請參閱[使用 DrawingVisuals 進行點擊測試範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159994)。  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>建立 DrawingVisual 物件  
 當您建立<xref:System.Windows.Media.DrawingVisual>物件時, 它不會有任何繪圖內容。 您可以藉由抓取物件的<xref:System.Windows.Media.DrawingContext>並在其中繪製, 來加入文字、圖形或影像內容。 會藉由<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>呼叫<xref:System.Windows.Media.DrawingVisual>物件的方法來傳回。 <xref:System.Windows.Media.DrawingContext>  
  
 若要在中繪製矩形<xref:System.Windows.Media.DrawingContext>, 請使用<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> <xref:System.Windows.Media.DrawingContext>物件的方法。 繪製其他類型的內容有類似的方法。 當您完成將內容繪製到<xref:System.Windows.Media.DrawingContext>時, 請<xref:System.Windows.Media.DrawingContext.Close%2A>呼叫方法來關閉<xref:System.Windows.Media.DrawingContext>並保存內容。  
  
 在下列範例中, <xref:System.Windows.Media.DrawingVisual>會建立物件, 並在其<xref:System.Windows.Media.DrawingContext>中繪製一個矩形。  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>針對 FrameworkElement 成員建立覆寫  
 主機容器物件負責管理其視覺物件的集合。 這需要主機容器執行衍生<xref:System.Windows.FrameworkElement>類別的成員覆寫。  
  
 下列清單說明您必須覆寫的兩個成員︰  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>：傳回子專案集合中指定索引處的子系。  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>：取得這個項目內的視覺化子項目數。  
  
 在下列範例中, 會執行兩個<xref:System.Windows.FrameworkElement>成員的覆寫。  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>提供點擊測試支援  
 主機容器物件可以提供事件處理, 即使它並未顯示任何可見的屬性, 但它<xref:System.Windows.UIElement.Visibility%2A>的屬性必須設定為。 <xref:System.Windows.Visibility.Visible> 這可讓您針對可捕捉滑鼠事件 (例如放開滑鼠左鍵) 的主機容器建立事件處理常式。 接著, 事件處理常式就可以叫用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法來執行點擊測試。 方法的<xref:System.Windows.Media.HitTestResultCallback>參數會參考使用者定義的程式, 您可以使用這個程式來判中斷點擊測試的結果動作。  
  
 在下列範例中，會針對主機容器物件和其子系實作點擊測試支援。  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
