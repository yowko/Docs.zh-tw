---
title: "如何：設定項目的高度屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ae66e60375cfbc45a4f1e8834b6420bc5c0b70a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>如何：設定項目的高度屬性
## <a name="example"></a>範例  
 此範例以視覺化方式顯示在轉譯中的四個高度相關屬性之間的行為差異[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  
  
 <xref:System.Windows.FrameworkElement>類別會公開的四個屬性描述項目的高度特性。 這四個屬性可能會發生衝突，並會優先使用的值時，請決定，如下所示：<xref:System.Windows.FrameworkElement.MinHeight%2A>值優先順序高於<xref:System.Windows.FrameworkElement.MaxHeight%2A>值接著會優先於<xref:System.Windows.FrameworkElement.Height%2A>值。 第四個屬性， <xref:System.Windows.FrameworkElement.ActualHeight%2A>、 處於唯讀狀態，和報表版面配置處理序之間的互動所決定實際的高度。  
  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例繪製<xref:System.Windows.Shapes.Rectangle>元素 (`rect1`) 做為子系<xref:System.Windows.Controls.Canvas>。 您可以變更的高度屬性<xref:System.Windows.Shapes.Rectangle>使用一系列的<xref:System.Windows.Controls.ListBox>代表的屬性值的項目<xref:System.Windows.FrameworkElement.MinHeight%2A>， <xref:System.Windows.FrameworkElement.MaxHeight%2A>，和<xref:System.Windows.FrameworkElement.Height%2A>。 這種方式，以視覺化方式顯示每個屬性的優先順序。  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 下列程式碼後置範例處理事件的<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>事件引發。 每個處理常式會從輸入<xref:System.Windows.Controls.ListBox>，將做為值剖析<xref:System.Double>，並套用至指定的高度相關屬性的值。 高度值也會轉換成字串，並寫入至各種<xref:System.Windows.Controls.TextBlock>（定義這些項目未顯示在選取的 XAML） 的項目。  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 如需完整範例，請參閱[高度屬性範例](http://go.microsoft.com/fwlink/?LinkID=159993)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [設定元素的寬度屬性](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [高度屬性範例](http://go.microsoft.com/fwlink/?LinkID=159993)
