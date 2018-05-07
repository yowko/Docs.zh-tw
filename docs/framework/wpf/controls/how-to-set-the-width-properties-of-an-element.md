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
ms.openlocfilehash: 72617744a8b2565857d19a1c6ef41bf4211c89ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>如何：設定項目的寬度屬性
## <a name="example"></a>範例  
 此範例以視覺化方式顯示在轉譯中的四個寬度相關屬性之間的行為差異[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  
  
 <xref:System.Windows.FrameworkElement>類別會公開的四個屬性描述項目的寬度特性。 這四個屬性可能會發生衝突，並會優先使用的值時，請決定，如下所示：<xref:System.Windows.FrameworkElement.MinWidth%2A>值優先順序高於<xref:System.Windows.FrameworkElement.MaxWidth%2A>值接著會優先於<xref:System.Windows.FrameworkElement.Width%2A>值。 第四個屬性， <xref:System.Windows.FrameworkElement.ActualWidth%2A>、 處於唯讀狀態，和報表的版面配置處理序之間的互動所決定的實際寬度。  
  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例繪製<xref:System.Windows.Shapes.Rectangle>元素 (`rect1`) 做為子系<xref:System.Windows.Controls.Canvas>。 您可以變更的寬度屬性<xref:System.Windows.Shapes.Rectangle>使用一系列的<xref:System.Windows.Controls.ListBox>代表的屬性值的項目<xref:System.Windows.FrameworkElement.MinWidth%2A>， <xref:System.Windows.FrameworkElement.MaxWidth%2A>，和<xref:System.Windows.FrameworkElement.Width%2A>。 這種方式，以視覺化方式顯示每個屬性的優先順序。  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 下列程式碼後置範例處理事件的<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>事件引發。 每個自訂的方法會從輸入<xref:System.Windows.Controls.ListBox>，將做為值剖析<xref:System.Double>，並套用至指定的寬度與相關屬性的值。 寬度值也會轉換成字串，並寫入至各種<xref:System.Windows.Controls.TextBlock>（定義這些項目未顯示在選取的 XAML） 的項目。  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 如需完整範例，請參閱[寬度屬性比較範例](http://go.microsoft.com/fwlink/?LinkID=160050)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>  
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [設定元素的高度屬性](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)  
 [寬度屬性比較的範例](http://go.microsoft.com/fwlink/?LinkID=160050)
