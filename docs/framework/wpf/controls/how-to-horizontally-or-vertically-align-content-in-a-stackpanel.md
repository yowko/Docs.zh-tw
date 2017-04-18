---
title: "如何：水平或垂直對齊 StackPanel 中的內容 | Microsoft Docs"
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
  - "對齊, 內容"
  - "內容對齊"
  - "StackPanel 控制項, 內容對齊"
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：水平或垂直對齊 StackPanel 中的內容
本範例說明如何調整 <xref:System.Windows.Controls.StackPanel> 項目中之內容的 <xref:System.Windows.Controls.StackPanel.Orientation%2A>，以及如何調整子內容的 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 及 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>。  
  
## 範例  
 下列範例會使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 建立三個 <xref:System.Windows.Controls.ListBox> 項目。  每個 <xref:System.Windows.Controls.ListBox> 代表 <xref:System.Windows.Controls.StackPanel> 的 <xref:System.Windows.Controls.StackPanel.Orientation%2A>、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 屬性的可能值。  當使用者選擇 <xref:System.Windows.Controls.ListBox> 項目中的任何值時，<xref:System.Windows.Controls.StackPanel> 的關聯屬性和子 <xref:System.Windows.Controls.Button> 項目都會變更。  
  
 [!code-xml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 下列程式碼後置檔案會定義事件的變更，這些事件都和 <xref:System.Windows.Controls.ListBox> 選取變更相關。  <xref:System.Windows.Controls.StackPanel> 以 <xref:System.Windows.FrameworkElement.Name%2A> `sp1` 識別。  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## 請參閱  
 <xref:System.Windows.Controls.StackPanel>   
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>   
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)