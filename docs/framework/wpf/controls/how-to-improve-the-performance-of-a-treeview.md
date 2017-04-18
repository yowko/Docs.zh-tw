---
title: "如何：改善 TreeView 的效能 | Microsoft Docs"
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
  - "TreeView 控制項 [WPF], 改善效能"
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：改善 TreeView 的效能
如果 <xref:System.Windows.Controls.TreeView> 包含許多項目，則所需要的載入時間量可能會造成使用者介面明顯延後。  藉由將 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> 附加屬性設為 `true`，即可以改善載入時間。  當使用者透過使用滑鼠滾輪或是拖曳捲軸的捲動方塊，捲動 <xref:System.Windows.Controls.TreeView> 時，UI 的反應可能也會很慢。  藉由將 <xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> 附加屬性設為 <xref:System.Windows.Controls.VirtualizationMode>，即可以改善使用者捲動時的 <xref:System.Windows.Controls.TreeView> 效能。  
  
## 範例  
  
## 描述  
 下列範例建立的 <xref:System.Windows.Controls.TreeView> 會將 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> 設為 true，並將 <xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> 設為 <xref:System.Windows.Controls.VirtualizationMode>，以最佳化其效能。  
  
## 程式碼  
 [!code-xml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 下列範例顯示前述範例使用的資料。  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## 請參閱  
 [控制項](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)