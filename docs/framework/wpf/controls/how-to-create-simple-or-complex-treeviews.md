---
title: "如何：建立簡單或複雜的 TreeView | Microsoft Docs"
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
  - "Control 類別, TreeView, 建立"
  - "TreeView 控制項, 建立"
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：建立簡單或複雜的 TreeView
這個範例說明如何建立簡單或複雜的 <xref:System.Windows.Controls.TreeView> 控制項。  
  
 <xref:System.Windows.Controls.TreeView> 包含 <xref:System.Windows.Controls.TreeViewItem> 控制項的階層架構，可以包含簡單的文字字串和更複雜的內容，例如 <xref:System.Windows.Controls.Button> 控制項或含內嵌內容的 <xref:System.Windows.Controls.StackPanel>。  您可以明確定義 <xref:System.Windows.Controls.TreeView> 內容，或由資料來源提供此內容。  本主題提供了這些概念的範例。  
  
## 範例  
 <xref:System.Windows.Controls.TreeViewItem> 的 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 屬性含有 <xref:System.Windows.Controls.TreeView> 為該項目顯示的內容。  <xref:System.Windows.Controls.TreeViewItem> 也可以有 <xref:System.Windows.Controls.TreeViewItem> 控制項做為其子項目，而且您可以使用 <xref:System.Windows.Controls.ItemsControl.Items%2A> 屬性來定義這些子項目。  
  
 下列範例示範如何藉由將 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 屬性設定為文字字串，以明確定義 <xref:System.Windows.Controls.TreeViewItem> 內容。  
  
 [!code-xml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 下列範例示範如何藉由定義屬於 <xref:System.Windows.Controls.Button> 控制項的 <xref:System.Windows.Controls.ItemsControl.Items%2A>，以定義 <xref:System.Windows.Controls.TreeViewItem> 的子項目。  
  
 [!code-xml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 下列範例示範如何建立 <xref:System.Windows.Controls.TreeView>，其中的 <xref:System.Windows.Data.XmlDataProvider> 會提供 <xref:System.Windows.Controls.TreeViewItem> 內容，而且 <xref:System.Windows.HierarchicalDataTemplate> 會定義內容外觀。  
  
 [!code-xml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 下列範例示範如何建立 <xref:System.Windows.Controls.TreeView>，其中的 <xref:System.Windows.Controls.TreeViewItem> 內容包含有內嵌內容的 <xref:System.Windows.Controls.DockPanel> 控制項。  
  
 [!code-xml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## 請參閱  
 <xref:System.Windows.Controls.TreeView>   
 <xref:System.Windows.Controls.TreeViewItem>   
 [TreeView 概觀](../../../../docs/framework/wpf/controls/treeview-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)