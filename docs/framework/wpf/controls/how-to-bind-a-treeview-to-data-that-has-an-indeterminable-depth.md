---
title: "如何：將樹狀檢視繫結至未知深度的資料 | Microsoft Docs"
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
  - "TreeView 控制項 [WPF], 繫結至未知深度的資料"
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：將樹狀檢視繫結至未知深度的資料
有時您會想要將 <xref:System.Windows.Controls.TreeView> 繫結至資料深度未知的資料來源。  當資料具有遞迴的性質時，就可能發生這種情況。這類資料的範例包括檔案系統 \(資料夾能包含資料夾\)、公司組織結構 \(任何員工都有可能是其他員工的直屬上級\) 等等。  
  
 資料來源必須有階層式物件模型 \(Object Model\)。  舉例來說，`Employee` 類別可能包含本身為直屬報告者員工之 Employee 物件的集合。  如果資料的表示方式不是階層式，您就必須建置資料的階層式表示。  
  
 當您設定 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=fullName> 屬性時，如果 <xref:System.Windows.Controls.ItemsControl> 為每個子項目產生 <xref:System.Windows.Controls.ItemsControl>，則子系 <xref:System.Windows.Controls.ItemsControl> 會使用和父代一樣的 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。  舉例來說，如果您在資料繫結 <xref:System.Windows.Controls.TreeView> 上設定 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 屬性，則每一個產生的 <xref:System.Windows.Controls.TreeViewItem> 都會使用已指派給 <xref:System.Windows.Controls.TreeView> 之 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 屬性的 <xref:System.Windows.DataTemplate>。  
  
 <xref:System.Windows.HierarchicalDataTemplate> 可以讓您在資料樣板 \(Template\) 上指定 <xref:System.Windows.Controls.TreeViewItem> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>，或是任何 <xref:System.Windows.Controls.HeaderedItemsControl>。  如果您設定 <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=fullName> 屬性，則在套用 <xref:System.Windows.HierarchicalDataTemplate> 的時候才會使用這個屬性值。  藉由使用 <xref:System.Windows.HierarchicalDataTemplate>，您就可以在 <xref:System.Windows.Controls.TreeView> 中為每個 <xref:System.Windows.Controls.TreeViewItem> 遞迴設定 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。  
  
## 範例  
 在下列範例中，會示範如何將 <xref:System.Windows.Controls.TreeView> 繫結至階層式資料，並使用 <xref:System.Windows.HierarchicalDataTemplate> 來為每個 <xref:System.Windows.Controls.TreeViewItem> 指定 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>。  <xref:System.Windows.Controls.TreeView> 會繫結至表示公司員工的 XML 資料。  每個 `Employee` 項目都能包含其他 `Employee` 項目來表示直屬報告者。  因為是遞迴性資料，所以每一層都能套用 <xref:System.Windows.HierarchicalDataTemplate>。  
  
 [!code-xml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## 請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)