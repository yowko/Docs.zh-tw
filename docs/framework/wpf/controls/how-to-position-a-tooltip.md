---
title: HOW TO：置放工具提示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 811818fe6e7c0d8ce9e2aa058b42bf592ada4b92
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212345"
---
# <a name="how-to-position-a-tooltip"></a>HOW TO：置放工具提示
此範例示範如何在螢幕上指定工具提示的位置。  
  
## <a name="example"></a>範例  
 您可以使用一組五個屬性定義在置放工具提示<xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ToolTipService>類別。 下表顯示這兩個集合的五個屬性，並提供其根據類別的參考文件的連結。  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>對應的工具提示屬性，它是根據類別  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> 類別屬性|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> 類別屬性|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 如果您使用定義的工具提示內容<xref:System.Windows.Controls.ToolTip>物件，您可以使用任一類別的屬性; 不過，<xref:System.Windows.Controls.ToolTipService>屬性更高的優先順序。 使用<xref:System.Windows.Controls.ToolTipService>屬性未定義為的工具提示<xref:System.Windows.Controls.ToolTip>物件。  
  
 下列圖例顯示如何使用這些屬性來置放工具提示。 雖然，則[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]在這些實例中的範例示範如何設定所定義的屬性<xref:System.Windows.Controls.ToolTip>類別的對應屬性<xref:System.Windows.Controls.ToolTipService>類別遵循相同的配置規則。 如需有關放置屬性的可能值的詳細資訊，請參閱[快顯放置行為](popup-placement-behavior.md)。  
 
 下圖顯示工具提示放置使用位置屬性：  
  
 ![此圖表顯示工具提示放置使用位置屬性。](./media/how-to-position-a-tooltip/tooltip-placement-property.png)
 
 下圖顯示工具提示放置藉由使用放置與 PlacementRectangle 屬性：   

 ![此圖表顯示工具提示放置使用 PlacementRectangle 屬性。](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  
 
 下圖顯示工具提示放置藉由使用放置、 PlacementRectangle 和位移屬性：   
  
 ![使用 Offset 屬性顯示 ToolTip 位置圖表。](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 下列範例示範如何使用<xref:System.Windows.Controls.ToolTip>屬性，以指定其內容是為工具提示的位置<xref:System.Windows.Controls.ToolTip>物件。  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 下列範例示範如何使用<xref:System.Windows.Controls.ToolTipService>屬性，以指定其內容不是為工具提示的位置<xref:System.Windows.Controls.ToolTip>物件。  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [HOW TO 主題](tooltip-how-to-topics.md)
- [ToolTip 概觀](tooltip-overview.md)
