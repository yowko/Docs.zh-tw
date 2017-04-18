---
title: "如何：使用 BetweenShowDelay 屬性 | Microsoft Docs"
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
  - "BetweenShowDelay 時間屬性"
  - "ToolTip 控制項, BetweenShowDelay 時間屬性"
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用 BetweenShowDelay 屬性
此範例說明如何使用 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> 時間屬性，在使用者將滑鼠指標從一個工具提示直接移至另一個工具提示時，讓工具提示能快速顯示 \(只有一點點或完全沒有延遲\)。  
  
## 範例  
 在下列範例中，兩個 <xref:System.Windows.Shapes.Ellipse> 控制項之工具提示的 <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> 屬性設定為一秒 \(1000 毫秒\)，<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> 則設定為兩秒 \(2000 毫秒\)。  如果您顯示其中一個橢圓形的工具提示，然後在兩秒之內將滑鼠指標移至另一個橢圓形並停在這裡，就會立即顯示第二個橢圓形的工具提示。  
  
 下列任一情形都會套用 <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>，也就是第二個橢圓形的工具提示會等待一秒再顯示：  
  
-   移至第二個按鈕所花的時間超過兩秒。  
  
-   第一個橢圓形時間間隔一開始時看不到工具提示。  
  
 [!code-xml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## 請參閱  
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipService>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)   
 [工具提示概觀](../../../../docs/framework/wpf/controls/tooltip-overview.md)