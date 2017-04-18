---
title: "如何：確保 GridSplitter 是可見的 | Microsoft Docs"
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
  - "GridSplitter 控制項, 確保可視性"
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：確保 GridSplitter 是可見的
本範例說明如何確定 <xref:System.Windows.Controls.GridSplitter> 控制項不會被 <xref:System.Windows.Controls.Grid> 中的其他控制項隱藏。  
  
## 範例  
 <xref:System.Windows.Controls.Grid> 控制項的 <xref:System.Windows.Controls.Panel.Children%2A> 是依照它們在標記或程式碼中的定義順序而呈現。  如果您沒有將 <xref:System.Windows.Controls.GridSplitter> 控制項定義為 <xref:System.Windows.Controls.Panel.Children%2A> 集合中的最後項目，或者您為其他控制項指定更高的 <xref:System.Windows.Controls.Panel.ZIndexProperty>，它們就會被其他控制項隱藏。  
  
 若要避免隱藏 <xref:System.Windows.Controls.GridSplitter> 控制項，請執行下列其中一項動作。  
  
-   確定 <xref:System.Windows.Controls.GridSplitter> 控制項是最後加入至 <xref:System.Windows.Controls.Grid> 的 <xref:System.Windows.Controls.Panel.Children%2A>。  下列範例顯示 <xref:System.Windows.Controls.GridSplitter> 是 <xref:System.Windows.Controls.Grid> 的 <xref:System.Windows.Controls.Panel.Children%2A> 集合中的最後一個項目。  
  
 [!code-xml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   將 <xref:System.Windows.Controls.GridSplitter> 上的 <xref:System.Windows.Controls.Panel.ZIndexProperty> 設定為高於原本會隱藏它的其他控制項。  下列範例會為 <xref:System.Windows.Controls.GridSplitter> 控制項提供比 <xref:System.Windows.Controls.Button> 控制項更高的 <xref:System.Windows.Controls.Panel.ZIndexProperty>。  
  
 [!code-xml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   在原本會隱藏 <xref:System.Windows.Controls.GridSplitter> 的控制項上設定邊界，以便公開 <xref:System.Windows.Controls.GridSplitter>。  下列範例會在原本會覆疊及隱藏 <xref:System.Windows.Controls.GridSplitter> 的控制項上設定邊界。  
  
 [!code-xml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## 請參閱  
 <xref:System.Windows.Controls.GridSplitter>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)