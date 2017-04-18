---
title: "如何：在文字方塊使用自訂內容功能表 | Microsoft Docs"
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
  - "內容功能表, 自訂"
  - "自訂內容功能表"
  - "功能表, 自訂"
  - "TextBox 控制項, 自訂內容功能表"
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在文字方塊使用自訂內容功能表
本範例示範如何定義及實作 <xref:System.Windows.Controls.TextBox> 的簡單自訂內容功能表。  
  
## 範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例定義包含自訂內容功能表的 <xref:System.Windows.Controls.TextBox> 控制項。  
  
 內容功能表是使用 <xref:System.Windows.Controls.ContextMenu> 項目來定義。  內容功能表本身則由一系列的 <xref:System.Windows.Controls.MenuItem> 項目和 <xref:System.Windows.Controls.Separator> 項目所組成。  每個 <xref:System.Windows.Controls.MenuItem> 項目各定義內容功能表中的一個命令，<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 屬性 \(Attribute\) 定義功能表命令的顯示文字，而 <xref:System.Windows.Controls.MenuItem.Click> 屬性則指定每個功能表項目的處理常式方法。  <xref:System.Windows.Controls.Separator> 項目只會在前一個和後續功能表項目之間顯示一條分隔線。  
  
 [!code-xml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## 範例  
 下列範例顯示前述內容功能表定義的實作程式碼，以及啟用及停用內容功能表的程式碼。  <xref:System.Windows.Controls.ContextMenu.Opened> 事件會依據 <xref:System.Windows.Controls.TextBox> 目前的狀態，動態啟用或停用特定命令。  
  
 若要還原預設內容功能表，請使用 <xref:System.Windows.DependencyObject.ClearValue%2A> 方法清除 <xref:System.Windows.FrameworkElement.ContextMenu%2A> 屬性的值。  若要完全停用內容功能表，請將 <xref:System.Windows.FrameworkElement.ContextMenu%2A> 屬性設定為 null 參考 \(在 Visual Basic 中則為 `Nothing`\)。  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## 請參閱  
 [使用內容功能表的拼字檢查](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)   
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)