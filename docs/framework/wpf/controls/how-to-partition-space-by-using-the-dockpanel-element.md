---
title: "如何：使用 DockPanel 項目分割空間 | Microsoft Docs"
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
  - "控制項 [WPF], DockPanel"
  - "DockPanel 控制項, 分割空間"
  - "分割空間"
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 DockPanel 項目分割空間
下列範例使用 <xref:System.Windows.Controls.DockPanel> 項目建立一個簡單的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 架構。  <xref:System.Windows.Controls.DockPanel> 會分割其子項目可用的空間。  
  
## 範例  
 這個範例使用 <xref:System.Windows.Controls.DockPanel.Dock%2A> 屬性 \(這是一種[附加屬性](GTMT)\)，將兩個相同的 <xref:System.Windows.Controls.Border> 項目停駐在分割空間的 <xref:System.Windows.Controls.Dock>。  第三個 <xref:System.Windows.Controls.Border> 項目停駐在 <xref:System.Windows.Controls.Dock>，且寬度設為 200 像素。  第四個 <xref:System.Windows.Controls.Border> 停駐在螢幕的 <xref:System.Windows.Controls.Dock>。  最後一個 <xref:System.Windows.Controls.Border> 項目會自動填滿剩餘的空間。  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  根據預設，<xref:System.Windows.Controls.DockPanel> 項目的最後一個子系會填滿未配置的剩餘空間。  如果您不想要這個行為，請設定 `LastChildFill="False"`。  
  
 完成編譯的應用程式會產生新的 UI，看起來就像下面這樣。  
  
 ![典型的 DockPanel 案例。](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.png "panel\_intro\_dockpanel")  
  
## 請參閱  
 <xref:System.Windows.Controls.DockPanel>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)