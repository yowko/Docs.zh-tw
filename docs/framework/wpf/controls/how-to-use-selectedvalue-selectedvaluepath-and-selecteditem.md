---
title: "如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem | Microsoft Docs"
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
  - "Control 類別, SelectedItem 屬性"
  - "Control 類別, SelectedValue 屬性"
  - "Control 類別, SelectedValuePath 屬性"
  - "Control 類別, TreeView 屬性"
  - "SelectedValue, SelectedItem 屬性"
  - "SelectedValue, SelectedValuePath 屬性"
  - "TreeView 控制項, SelectedItem 屬性"
  - "TreeView 控制項, SelectedValue 屬性"
  - "TreeView 控制項, SelectedValuePath 屬性"
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用 SelectedValue、SelectedValuePath 和 SelectedItem
本範例顯示如何使用 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 和 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 屬性，指定 <xref:System.Windows.Controls.TreeView> 的 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 值。  
  
## 範例  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 屬性可提供一種方法，替 <xref:System.Windows.Controls.TreeView> 中的 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 指定 <xref:System.Windows.Controls.TreeView.SelectedValue%2A>。  <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 表示 <xref:System.Windows.Controls.ItemsControl.Items%2A> 集合中的物件，而 <xref:System.Windows.Controls.TreeView> 會顯示選定項目的單一屬性值。  <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 屬性可指定用來判斷 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 屬性值的屬性路徑。  本主題中的範例會說明此概念。  
  
 下列範例顯示含有員工資訊的 <xref:System.Windows.Data.XmlDataProvider>。  
  
 [!code-xml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 下列範例會定義 <xref:System.Windows.HierarchicalDataTemplate>，以顯示 `Employee` 的 `EmployeeName` 和 `EmployeeWorkDay`。  請注意，<xref:System.Windows.HierarchicalDataTemplate> 不會將 `EmployeeNumber` 指定為範本的一部分。  
  
 [!code-xml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 下列範例顯示 <xref:System.Windows.Controls.TreeView>，它會使用先前定義的 <xref:System.Windows.HierarchicalDataTemplate> 並將 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 屬性設定為 `EmployeeNumber`。  當您選取 <xref:System.Windows.Controls.TreeView> 中的 `EmployeeName` 時，<xref:System.Windows.Controls.TreeView.SelectedItem%2A> 屬性會傳回對應至選定 `EmployeeName` 的 `EmployeeInfo` 資料項目。  但是，由於此 <xref:System.Windows.Controls.TreeView> 的 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 已設定為 `EmployeeNumber`，所以 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 會設定為 `EmployeeNumber`。  
  
 [!code-xml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## 請參閱  
 <xref:System.Windows.Controls.TreeView>   
 <xref:System.Windows.Controls.TreeViewItem>   
 [TreeView 概觀](../../../../docs/framework/wpf/controls/treeview-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)