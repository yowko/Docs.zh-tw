---
title: "如何：置放工具提示"
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
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc81fa247f21448a4ccbd62baccb72c0ec14bb31
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-position-a-tooltip"></a>如何：置放工具提示
這個範例示範如何在螢幕上指定工具提示的位置。  
  
## <a name="example"></a>範例  
 您可以使用放置在工具提示的五個屬性定義中的一組<xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ToolTipService>類別。 下表顯示這兩個集合的五個屬性，並提供根據類別參考文件的連結。  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>對應的工具提示屬性，根據類別  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>類別屬性|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>類別屬性|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 如果您定義工具提示的內容使用<xref:System.Windows.Controls.ToolTip>物件，您可以使用其中一個類別的屬性; 不過，<xref:System.Windows.Controls.ToolTipService>屬性的優先順序。 使用<xref:System.Windows.Controls.ToolTipService>內容為未定義的工具提示<xref:System.Windows.Controls.ToolTip>物件。  
  
 下圖顯示如何使用放置在工具提示的這些屬性。 雖然、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]這些圖中的範例示範如何設定所定義的屬性<xref:System.Windows.Controls.ToolTip>類別的對應屬性<xref:System.Windows.Controls.ToolTipService>類別遵循相同的配置規則。 如需可能的值為位置屬性的詳細資訊，請參閱[快顯視窗放置行為](../../../../docs/framework/wpf/controls/popup-placement-behavior.md)。  
  
 ![ToolTip 位置](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")  
ToolTip 位置使用放置屬性  
  
 ![使用定位矩形放置 ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")  
ToolTip 位置使用 Placement 與 PlacementRectangle 屬性  
  
 ![ToolTip 位置圖表](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")  
ToolTip 位置使用的位置、 PlacementRectangle 和位移屬性  
  
 下列範例示範如何使用<xref:System.Windows.Controls.ToolTip>屬性，以指定的內容會以工具提示的位置<xref:System.Windows.Controls.ToolTip>物件。  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 下列範例示範如何使用<xref:System.Windows.Controls.ToolTipService>屬性，以指定其內容不是為工具提示的位置<xref:System.Windows.Controls.ToolTip>物件。  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [工具提示概觀](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [使用 ContextMenuService 和 ToolTipService](http://msdn.microsoft.com/library/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
