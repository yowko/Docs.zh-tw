---
title: "如何：置放工具提示 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "放置 ToolTip 控制項"
  - "ToolTip 控制項, 位置"
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：置放工具提示
這個範例在說明如何指定工具提示在螢幕上的位置。  
  
## 範例  
 您可以使用 <xref:System.Windows.Controls.ToolTip> 及 <xref:System.Windows.Controls.ToolTipService> 類別中所定義的一組五個屬性，放置工具提示。  下表顯示這兩組五個屬性，並根據類別提供參考文件的連結。  
  
### 根據類別的對應工具提示屬性  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=fullName> 類別屬性|<xref:System.Windows.Controls.ToolTipService?displayProperty=fullName> 類別屬性|  
|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=fullName>|  
  
 如果您使用 <xref:System.Windows.Controls.ToolTip> 物件定義工具提示的內容，就可以使用任一類別的屬性，但是 <xref:System.Windows.Controls.ToolTipService> 屬性的優先順序最高。  請對未定義為 <xref:System.Windows.Controls.ToolTip> 物件的工具提示，使用 <xref:System.Windows.Controls.ToolTipService> 屬性。  
  
 下圖顯示如何使用這些屬性來放置工具提示。  雖然圖示中的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例有說明如何設定 <xref:System.Windows.Controls.ToolTip> 類別所定義的屬性，但是 <xref:System.Windows.Controls.ToolTipService> 類別對應的屬性會遵循相同的配置規則。  如需 Placement 屬性之可能值的詳細資訊，請參閱[快顯功能表放置行為](../../../../docs/framework/wpf/controls/popup-placement-behavior.md)。  
  
 ![ToolTip 位置](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")  
使用 Placement 屬性放置工具提示  
  
 ![使用定位矩形放置 ToolTip](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")  
使用 Placement 和 PlacementRectangle 屬性放置工具提示  
  
 ![ToolTip 位置圖表](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")  
使用 Placement、PlacementRectangle 和 Offset 屬性放置工具提示  
  
 下列範例說明如何使用 <xref:System.Windows.Controls.ToolTip> 屬性，以指定內容為 <xref:System.Windows.Controls.ToolTip> 物件之工具提示的位置。  
  
 [!code-xml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 下列範例說明如何使用 <xref:System.Windows.Controls.ToolTipService> 屬性，以指定內容不是 <xref:System.Windows.Controls.ToolTip> 物件之工具提示的位置。  
  
 [!code-xml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## 請參閱  
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipService>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)   
 [工具提示概觀](../../../../docs/framework/wpf/controls/tooltip-overview.md)   
 [Use the ContextMenuService and ToolTipService](http://msdn.microsoft.com/zh-tw/809b0e9c-d612-4cda-b8af-1a698c68f4d1)