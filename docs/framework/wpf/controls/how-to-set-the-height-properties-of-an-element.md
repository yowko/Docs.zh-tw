---
title: 如何：設定項目的高度屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124282"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>如何：設定項目的高度屬性
## <a name="example"></a>範例  
 這個範例會以視覺化方式顯示 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]中四個高度相關屬性之間的呈現行為差異。  
  
 <xref:System.Windows.FrameworkElement> 類別會公開四個屬性，以描述元素的高度特性。 這四個屬性可能會互相衝突，而當它們發生時，優先順序的值會決定如下： <xref:System.Windows.FrameworkElement.MinHeight%2A> 值優先于 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 值，而後者的優先順序高於 <xref:System.Windows.FrameworkElement.Height%2A> 值。 第四個屬性（<xref:System.Windows.FrameworkElement.ActualHeight%2A>）是唯讀的，而且會回報與配置處理常式互動所決定的實際高度。  
  
 下列 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例會將 <xref:System.Windows.Shapes.Rectangle> 元素（`rect1`）繪製為 <xref:System.Windows.Controls.Canvas>的子系。 您可以使用一系列的 <xref:System.Windows.Controls.ListBox> 元素來變更 <xref:System.Windows.Shapes.Rectangle> 的 height 屬性，這些專案代表 <xref:System.Windows.FrameworkElement.MinHeight%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>和 <xref:System.Windows.FrameworkElement.Height%2A>的屬性值。 如此一來，就會以視覺化方式顯示每個屬性的優先順序。  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 下列程式碼後置範例會處理 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件引發的事件。 每個處理常式都會接受來自 <xref:System.Windows.Controls.ListBox>的輸入、將值剖析為 <xref:System.Double>，並將值套用至指定的高度相關屬性。 高度值也會轉換為字串，並寫入至各種 <xref:System.Windows.Controls.TextBlock> 專案（這些元素的定義不會顯示在選取的 XAML 中）。  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 如需完整範例，請參閱[Height Properties sample](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [設定元素的寬度屬性](how-to-set-the-width-properties-of-an-element.md)
- [面板概觀](panels-overview.md)
- [Height 屬性範例](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
