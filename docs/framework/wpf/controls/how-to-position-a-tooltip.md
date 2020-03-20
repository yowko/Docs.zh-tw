---
title: 如何：置放工具提示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 0f52703e4fe127daa40f220280f084b2026580cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186943"
---
# <a name="how-to-position-a-tooltip"></a>如何：置放工具提示
此示例演示如何在螢幕上指定工具提示的位置。  
  
## <a name="example"></a>範例  
 可以使用 在 和<xref:System.Windows.Controls.ToolTip><xref:System.Windows.Controls.ToolTipService>類 中定義的一組五個屬性來定位工具提示。 下表顯示了這兩組五個屬性，並根據類提供指向其參考文檔的連結。  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>根據類對應的工具提示屬性  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>類屬性|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>類屬性|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 如果使用物件定義工具提示的內容，則可以使用任一類的屬性<xref:System.Windows.Controls.ToolTip>;如果使用物件定義工具提示的內容，則可以使用任一類的屬性。但是，<xref:System.Windows.Controls.ToolTipService>屬性優先。 對未<xref:System.Windows.Controls.ToolTipService>定義為<xref:System.Windows.Controls.ToolTip>物件的工具提示使用屬性。  
  
 下圖顯示了如何使用這些屬性定位工具提示。 儘管這些插圖[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中的示例演示如何設置由<xref:System.Windows.Controls.ToolTip>類定義的屬性，但類的<xref:System.Windows.Controls.ToolTipService>相應屬性遵循相同的佈局規則。 有關放置屬性的可能值的詳細資訊，請參閱[彈出放置行為](popup-placement-behavior.md)。  

 下圖顯示了使用"放置"屬性的工具提示放置：  
  
 ![使用放置屬性顯示工具提示放置的圖表。](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 下圖使用"放置"和"放置矩形"屬性顯示工具提示放置：

 ![使用放置矩形屬性顯示工具提示放置位置的圖表。](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 下圖使用"放置"、放置矩形和偏移屬性顯示工具提示放置：
  
 ![使用"偏移"屬性顯示工具提示放置位置的圖表。](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 下面的示例演示如何使用<xref:System.Windows.Controls.ToolTip>屬性來指定其內容為<xref:System.Windows.Controls.ToolTip>物件的工具提示的位置。  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 下面的示例演示如何使用<xref:System.Windows.Controls.ToolTipService>屬性來指定其內容不是<xref:System.Windows.Controls.ToolTip>物件的工具提示的位置。  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [如何使用主題](tooltip-how-to-topics.md)
- [工具提示概觀](tooltip-overview.md)
