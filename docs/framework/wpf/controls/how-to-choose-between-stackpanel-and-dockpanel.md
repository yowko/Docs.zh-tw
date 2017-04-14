---
title: "如何：在 StackPanel 和 DockPanel 之間選擇 | Microsoft Docs"
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
  - "控制項 [WPF], StackPanel"
  - "DockPanel 控制項, 與 StackPanel 控制項比較"
  - "StackPanel 控制項, 與 DockPanel 控制項比較"
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在 StackPanel 和 DockPanel 之間選擇
本範例說明在 <xref:System.Windows.Controls.Panel> 中堆疊內容時，如何選擇使用 <xref:System.Windows.Controls.StackPanel> 或 <xref:System.Windows.Controls.DockPanel>。  
  
## 範例  
 雖然您可以使用 <xref:System.Windows.Controls.DockPanel> 或 <xref:System.Windows.Controls.StackPanel> 來堆疊子項目，但這兩個控制項並不會一直產生相同的結果。  例如，放置子項目的順序在 <xref:System.Windows.Controls.DockPanel> 中會影響子項目的大小，但在 <xref:System.Windows.Controls.StackPanel> 中卻沒有影響。  會發生不同的行為，是因為 <xref:System.Windows.Controls.StackPanel> 會測量 <xref:System.Double>.<xref:System.Double.PositiveInfinity> 中堆疊的方向，但是 <xref:System.Windows.Controls.DockPanel> 只會測量可用的大小。  
  
 下列範例說明 <xref:System.Windows.Controls.DockPanel> 和 <xref:System.Windows.Controls.StackPanel> 之間的主要差異。  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## 請參閱  
 <xref:System.Windows.Controls.StackPanel>   
 <xref:System.Windows.Controls.DockPanel>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)