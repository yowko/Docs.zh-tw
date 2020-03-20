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
ms.openlocfilehash: 9d67fbc0d9716c9df3935232c6c7e579b50d55bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148318"
---
# <a name="using-drawingvisual-objects"></a>使用 DrawingVisual 物件
本主題概述了如何在<xref:System.Windows.Media.DrawingVisual>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視覺化圖層中使用物件。  
  
<a name="drawingvisual_object"></a>
## <a name="drawingvisual-object"></a>DrawingVisual 物件  
 是<xref:System.Windows.Media.DrawingVisual>用於渲染形狀、圖像或文本的羽量級繪圖類。 此類別之所以被視為輕量型，是因為它不提供版面配置或事件處理，這使它有更好的效能。 基於此原因，它適合用於背景或美工圖案繪圖。  
  
<a name="drawingvisual_host_container"></a>
## <a name="drawingvisual-host-container"></a>DrawingVisual 主機容器  
 為了使用<xref:System.Windows.Media.DrawingVisual>物件，您需要為物件創建一個宿主容器。 主機容器物件必須派生自<xref:System.Windows.FrameworkElement>類，該類提供類缺少的<xref:System.Windows.Media.DrawingVisual>佈局和事件處理支援。 主機容器物件不會顯示任何可見的屬性，因為其主要目的是要包含子物件。 但是，<xref:System.Windows.UIElement.Visibility%2A>主機容器的屬性必須設置為<xref:System.Windows.Visibility.Visible>;否則，其子項目都不會可見。  
  
 為可視物件創建宿主容器物件時，需要在 中<xref:System.Windows.Media.VisualCollection>存儲可視物件引用。 使用<xref:System.Windows.Media.VisualCollection.Add%2A>方法向宿主容器添加可視物件。 在下面的示例中，將創建一個宿主容器物件，並將三個可視物件添加到其<xref:System.Windows.Media.VisualCollection>。  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> 如需先前程式碼範例出處的完整程式碼範例，請參閱[使用 DrawingVisuals 進行點擊測試範例 (英文)](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)。  
  
<a name="creating_drawingvisual_objects"></a>
## <a name="creating-drawingvisual-objects"></a>建立 DrawingVisual 物件  
 創建物件時<xref:System.Windows.Media.DrawingVisual>，它沒有繪圖內容。 您可以通過檢索物件<xref:System.Windows.Media.DrawingContext>並將其繪製到其中來添加文本、圖形或圖像內容。 通過<xref:System.Windows.Media.DrawingContext>調用<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A><xref:System.Windows.Media.DrawingVisual>物件的方法返回 。  
  
 要將矩形繪製到<xref:System.Windows.Media.DrawingContext>中，請使用<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A><xref:System.Windows.Media.DrawingContext>物件的方法。 繪製其他類型的內容有類似的方法。 將內容繪製完到 中<xref:System.Windows.Media.DrawingContext>，調用<xref:System.Windows.Media.DrawingContext.Close%2A>方法以關閉<xref:System.Windows.Media.DrawingContext>並保留內容。  
  
 在下面的示例中，將創建<xref:System.Windows.Media.DrawingVisual>一個物件，並將一個矩形繪製到其<xref:System.Windows.Media.DrawingContext>中。  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>
## <a name="creating-overrides-for-frameworkelement-members"></a>針對 FrameworkElement 成員建立覆寫  
 主機容器物件負責管理其視覺物件的集合。 這要求主機容器實現成員重寫派生<xref:System.Windows.FrameworkElement>類。  
  
 下列清單說明您必須覆寫的兩個成員︰  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>：從子項目集合中返回指定索引處的子項。  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>：獲取此元素中的可視子項目的數量。  
  
 在下面的示例中，將實現兩<xref:System.Windows.FrameworkElement>個成員的重寫。  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>
## <a name="providing-hit-testing-support"></a>提供點擊測試支援  
 主機容器物件可以提供事件處理，即使它不顯示任何可見屬性 ， 但是，其<xref:System.Windows.UIElement.Visibility%2A>屬性必須設置為<xref:System.Windows.Visibility.Visible>。 這可讓您針對可捕捉滑鼠事件 (例如放開滑鼠左鍵) 的主機容器建立事件處理常式。 然後，事件處理常式可以通過調用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法實現點擊測試。 方法的<xref:System.Windows.Media.HitTestResultCallback>參數是指使用者定義的過程，可用於確定點擊測試的結果操作。  
  
 在下列範例中，會針對主機容器物件和其子系實作點擊測試支援。  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
- [視覺分層中的點擊測試](hit-testing-in-the-visual-layer.md)
