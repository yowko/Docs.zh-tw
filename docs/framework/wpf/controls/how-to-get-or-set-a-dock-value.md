---
title: "如何：取得或設定 Dock 值 | Microsoft Docs"
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
  - "Dock 值, 取得"
  - "Dock 值, 設定"
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：取得或設定 Dock 值
下列範例說明如何指派 <xref:System.Windows.Controls.Dock> 值給物件。  本範例使用 <xref:System.Windows.Controls.DockPanel> 的 <xref:System.Windows.Controls.DockPanel.GetDock%2A> 和 <xref:System.Windows.Controls.DockPanel.SetDock%2A> 方法。  
  
## 範例  
 本範例會建立一個 <xref:System.Windows.Controls.TextBlock> 項目的執行個體 \(`txt1`\)，並使用 <xref:System.Windows.Controls.DockPanel> 的 <xref:System.Windows.Controls.DockPanel.SetDock%2A> 方法，將 <xref:System.Windows.Controls.Dock> 值指派為 `Top`。  然後使用 <xref:System.Windows.Controls.DockPanel.GetDock%2A> 方法，將 <xref:System.Windows.Controls.Dock> 屬性的值附加至 <xref:System.Windows.Controls.TextBlock> 項目的 <xref:System.Windows.Controls.TextBlock.Text%2A>。  最後，範例會將 <xref:System.Windows.Controls.TextBlock> 項目新增至父代 <xref:System.Windows.Controls.DockPanel> \(`dp1`\)。  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Controls.DockPanel>   
 <xref:System.Windows.Controls.DockPanel.GetDock%2A>   
 <xref:System.Windows.Controls.DockPanel.SetDock%2A>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)