---
title: "如何：在 TreeView 中尋找 TreeViewItem | Microsoft Docs"
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
  - "TreeView 控制項 [WPF], 尋找 TreeViewItem"
  - "TreeViewItem [WPF], 尋找"
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：在 TreeView 中尋找 TreeViewItem
<xref:System.Windows.Controls.TreeView> 控制項是一種方便顯示階層資料的方法。  如果您的<xref:System.Windows.Controls.TreeView> 已繫結至資料來源，<xref:System.Windows.Controls.TreeView.SelectedItem%2A> 屬性可方便您快速擷取所選取的資料物件。  通常最好是處理基礎資料物件，但您有時候可能也需要以程式設計方式操作包含該資料的 <xref:System.Windows.Controls.TreeViewItem>。  例如，您可能會需要以程式設計方式展開 <xref:System.Windows.Controls.TreeViewItem>，或在 <xref:System.Windows.Controls.TreeView> 中選取不同項目。  
  
 若要尋找包含特定資料物件的 <xref:System.Windows.Controls.TreeViewItem>，您必須周遊 <xref:System.Windows.Controls.TreeView> 的每個層級。  此外，您也能將 <xref:System.Windows.Controls.TreeView> 中的項目虛擬化以改善效能。  如果您將項目虛擬化，則還必須實現 <xref:System.Windows.Controls.TreeViewItem> 以檢查它是否包含資料物件。  
  
## 範例  
  
## 描述  
 下列範例會在 <xref:System.Windows.Controls.TreeView> 中搜尋特定物件，並傳回包含該物件的 <xref:System.Windows.Controls.TreeViewItem>。  此範例會確保每個 <xref:System.Windows.Controls.TreeViewItem> 都已具現化，以便搜尋其子項目。  如果 <xref:System.Windows.Controls.TreeView> 不使用虛擬項目，這個範例也能運作。  
  
> [!NOTE]
>  下列範例可用於任何 <xref:System.Windows.Controls.TreeView> \(無論其基礎資料模型為何\)，並且會搜尋每個 <xref:System.Windows.Controls.TreeViewItem> 直到找到物件為止。  另一個效能較好的方式是在資料模型中搜尋指定物件，追蹤它在資料階層架構中的位置，然後在 <xref:System.Windows.Controls.TreeView> 中尋找對應的 <xref:System.Windows.Controls.TreeViewItem>。  不過，這個方式雖然效能較好，但需要對資料模型有所了解，且不能廣泛用於任何 <xref:System.Windows.Controls.TreeView>。  
  
## 程式碼  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 上述程式碼依賴一個公開了 `BringIntoView` 方法的自訂 <xref:System.Windows.Controls.VirtualizingStackPanel>。  下列程式碼就在定義這個自訂 <xref:System.Windows.Controls.VirtualizingStackPanel>。  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 下列 XAML 顯示如何建立一個使用自訂 <xref:System.Windows.Controls.VirtualizingStackPanel> 的 <xref:System.Windows.Controls.TreeView>。  
  
 [!code-xml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## 請參閱  
 [改善 TreeView 的效能](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)