---
title: 如何：設定項目的寬度屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 682929625612114d042e4619d8388617988b3c48
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124269"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>如何：設定項目的寬度屬性
## <a name="example"></a>範例  
 這個範例會以視覺化方式顯示 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]中四個與寬度相關的屬性之間的轉譯行為差異。  
  
 <xref:System.Windows.FrameworkElement> 類別會公開四個屬性，以描述元素的寬度特性。 這四個屬性可能會互相衝突，而當它們發生時，優先順序的值會決定如下： <xref:System.Windows.FrameworkElement.MinWidth%2A> 值優先于 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 值，而後者的優先順序高於 <xref:System.Windows.FrameworkElement.Width%2A> 值。 第四個屬性（<xref:System.Windows.FrameworkElement.ActualWidth%2A>）是唯讀的，並會回報與配置處理常式互動所決定的實際寬度。  
  
 下列 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例會將 <xref:System.Windows.Shapes.Rectangle> 元素（`rect1`）繪製為 <xref:System.Windows.Controls.Canvas>的子系。 您可以使用一系列的 <xref:System.Windows.Controls.ListBox> 元素（代表 <xref:System.Windows.FrameworkElement.MinWidth%2A>、<xref:System.Windows.FrameworkElement.MaxWidth%2A>和 <xref:System.Windows.FrameworkElement.Width%2A>的屬性值），來變更 <xref:System.Windows.Shapes.Rectangle> 的寬度屬性。 如此一來，就會以視覺化方式顯示每個屬性的優先順序。  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 下列程式碼後置範例會處理 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件引發的事件。 每個自訂方法都會從 <xref:System.Windows.Controls.ListBox>取得輸入、將值剖析為 <xref:System.Double>，並將值套用至指定的寬度相關屬性。 寬度值也會轉換為字串，並寫入至各種 <xref:System.Windows.Controls.TextBlock> 專案（這些元素的定義不會顯示在選取的 XAML 中）。  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 如需完整範例，請參閱[寬度屬性比較範例](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [面板概觀](panels-overview.md)
- [設定元素的高度屬性](how-to-set-the-height-properties-of-an-element.md)
- [寬度屬性比較範例](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)
