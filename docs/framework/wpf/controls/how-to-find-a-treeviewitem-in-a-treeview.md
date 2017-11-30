---
title: "如何：在 TreeView 中尋找 TreeViewItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a231f5eae92bff8e3d525579dae865aaa0d7e496
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>如何：在 TreeView 中尋找 TreeViewItem
<xref:System.Windows.Controls.TreeView>控制項提供便利的方式顯示階層式資料。 如果您<xref:System.Windows.Controls.TreeView>繫結至資料來源，<xref:System.Windows.Controls.TreeView.SelectedItem%2A>屬性提供便利的方式，讓您快速擷取選取的資料物件。 它通常是最佳選擇使用基礎資料物件，但有時候您可能需要以程式設計方式操作的資料包含<xref:System.Windows.Controls.TreeViewItem>。 例如，您可能需要以程式設計方式展開<xref:System.Windows.Controls.TreeViewItem>，或選取不同的項目中<xref:System.Windows.Controls.TreeView>。  
  
 若要尋找<xref:System.Windows.Controls.TreeViewItem>包含特定資料物件，則必須周遊的每個層級<xref:System.Windows.Controls.TreeView>。 中的項目<xref:System.Windows.Controls.TreeView>也都可以虛擬化來改善效能。 在案例中可能會虛擬化項目，您也必須了解<xref:System.Windows.Controls.TreeViewItem>檢查它是否包含資料的物件。  
  
## <a name="example"></a>範例  
  
## <a name="description"></a>說明  
 下列範例會搜尋<xref:System.Windows.Controls.TreeView>的特定物件，並傳回所含之物件的<xref:System.Windows.Controls.TreeViewItem>。 範例會確保每個<xref:System.Windows.Controls.TreeViewItem>具現化，而可以搜尋其子項目。 這個範例也適用於如果<xref:System.Windows.Controls.TreeView>不使用虛擬化的項目。  
  
> [!NOTE]
>  下列範例適用於任何<xref:System.Windows.Controls.TreeView>，不論基礎資料模型和搜尋每個<xref:System.Windows.Controls.TreeViewItem>直到找到的物件。 另一個有較佳的效能的技術是搜尋指定的物件的資料模型、 追蹤資料階層架構中的位置，並找出對應<xref:System.Windows.Controls.TreeViewItem>中<xref:System.Windows.Controls.TreeView>。 不過，有更佳的效能的技術需要資料模型的知識，而且無法一般化任何給定的<xref:System.Windows.Controls.TreeView>。  
  
## <a name="code"></a>程式碼  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 先前的程式碼依賴自訂<xref:System.Windows.Controls.VirtualizingStackPanel>可公開方法，名為`BringIntoView`。 下列程式碼會定義自訂<xref:System.Windows.Controls.VirtualizingStackPanel>。  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 下列 XAML 顯示如何建立<xref:System.Windows.Controls.TreeView>使用自訂<xref:System.Windows.Controls.VirtualizingStackPanel>。  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>另請參閱  
 [改善 TreeView 的效能](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
