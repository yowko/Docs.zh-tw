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
ms.openlocfilehash: e76ac22d4b8205576c8ed9ab67482c143a52fbd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565310"
---
# <a name="using-drawingvisual-objects"></a>使用 DrawingVisual 物件
本主題概略說明如何使用<xref:System.Windows.Media.DrawingVisual>中的物件[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]visual 的圖層。  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>DrawingVisual 物件  
 <xref:System.Windows.Media.DrawingVisual>是輕量型繪製用來呈現圖形、 影像或文字的類別。 此類別之所以被視為輕量型，是因為它不提供版面配置或事件處理，這使它有更好的效能。 基於此原因，繪圖適合背景或美工圖案。  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual 主機容器  
 若要使用<xref:System.Windows.Media.DrawingVisual>物件，您必須建立主應用程式容器物件。 裝載容器物件必須衍生自<xref:System.Windows.FrameworkElement>類別，可提供配置和事件處理支援的<xref:System.Windows.Media.DrawingVisual>類別缺少。 主機容器物件不會顯示任何可見的屬性，因為其主要目的是要包含子物件。 不過，<xref:System.Windows.UIElement.Visibility%2A>主機容器屬性必須設定為<xref:System.Windows.Visibility.Visible>; 否則它的所有子元素將會顯示。  
  
 當您建立主控件容器物件的視覺物件時，您需要儲存中的視覺物件參考<xref:System.Windows.Media.VisualCollection>。 使用<xref:System.Windows.Media.VisualCollection.Add%2A>方法，將視覺物件加入至主機的容器。 在下列範例中，建立裝載容器物件，並將三個視覺物件會加入其<xref:System.Windows.Media.VisualCollection>。  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  如需先前程式碼範例出處的完整程式碼範例，請參閱[使用 DrawingVisuals 進行點擊測試範例 (英文)](http://go.microsoft.com/fwlink/?LinkID=159994)。  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>建立 DrawingVisual 物件  
 當您建立<xref:System.Windows.Media.DrawingVisual>物件，它沒有任何繪圖內容。 您可以藉由擷取的物件加入文字、 圖形或映像內容<xref:System.Windows.Media.DrawingContext>及繪圖到其中。 A<xref:System.Windows.Media.DrawingContext>傳回透過呼叫<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>方法<xref:System.Windows.Media.DrawingVisual>物件。  
  
 若要繪製成矩形<xref:System.Windows.Media.DrawingContext>，使用<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A>方法<xref:System.Windows.Media.DrawingContext>物件。 繪製其他類型的內容有類似的方法。 當您已完成繪製內容<xref:System.Windows.Media.DrawingContext>，呼叫<xref:System.Windows.Media.DrawingContext.Close%2A>方法，關閉<xref:System.Windows.Media.DrawingContext>和將內容保存。  
  
 在下列範例中，<xref:System.Windows.Media.DrawingVisual>時會建立物件，而且矩形繪製到其<xref:System.Windows.Media.DrawingContext>。  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>針對 FrameworkElement 成員建立覆寫  
 主機容器物件負責管理其視覺物件的集合。 這需要在裝載容器實作的衍生的成員覆寫<xref:System.Windows.FrameworkElement>類別。  
  
 下列清單說明您必須覆寫的兩個成員︰  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A>： 從子項目集合傳回指定索引處的子系。  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>： 取得此項目內的視覺子項目的數目。  
  
 在下列範例中，會覆寫這兩個<xref:System.Windows.FrameworkElement>成員實作。  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>提供點擊測試支援  
 裝載容器物件可提供事件處理，即使它不會顯示任何可見的屬性，不過，其<xref:System.Windows.UIElement.Visibility%2A>屬性必須設定為<xref:System.Windows.Visibility.Visible>。 這可讓您針對可捕捉滑鼠事件 (例如放開滑鼠左鍵) 的主機容器建立事件處理常式。 事件處理常式，然後實作叫用的點擊測試<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法。 方法的<xref:System.Windows.Media.HitTestResultCallback>參數是指使用者定義的程序，您可以使用它來判斷點擊測試產生的動作。  
  
 在下列範例中，會針對主機容器物件和其子系實作點擊測試支援。  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.DrawingVisual>  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
