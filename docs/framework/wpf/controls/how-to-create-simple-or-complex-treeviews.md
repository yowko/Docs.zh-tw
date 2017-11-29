---
title: "如何：建立簡單或複雜的 TreeView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e09f0f39d0c9a40a0e91299d308921917067166
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-simple-or-complex-treeviews"></a>如何：建立簡單或複雜的 TreeView
這個範例示範如何建立簡單或複雜<xref:System.Windows.Controls.TreeView>控制項。  
  
 A<xref:System.Windows.Controls.TreeView>組成的階層<xref:System.Windows.Controls.TreeViewItem>控制項，可包含簡單的文字字串，也更複雜的內容，例如<xref:System.Windows.Controls.Button>控制項或<xref:System.Windows.Controls.StackPanel>與內嵌的內容。 您可以明確定義<xref:System.Windows.Controls.TreeView>內容或資料來源可以提供內容。 本主題提供這些概念的範例。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>屬性<xref:System.Windows.Controls.TreeViewItem>包含內容的<xref:System.Windows.Controls.TreeView>顯示該項目。 A<xref:System.Windows.Controls.TreeViewItem>也可以有<xref:System.Windows.Controls.TreeViewItem>控制項為其子項目，而您可以使用定義這些子項目<xref:System.Windows.Controls.ItemsControl.Items%2A>屬性。  
  
 下列範例示範如何明確地定義<xref:System.Windows.Controls.TreeViewItem>藉由設定內容<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>屬性設為文字字串。  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 下列範例顯示如何定義子項目的<xref:System.Windows.Controls.TreeViewItem>藉由定義<xref:System.Windows.Controls.ItemsControl.Items%2A>所<xref:System.Windows.Controls.Button>控制項。  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 下列範例示範如何建立<xref:System.Windows.Controls.TreeView>其中<xref:System.Windows.Data.XmlDataProvider>提供<xref:System.Windows.Controls.TreeViewItem>內容和<xref:System.Windows.HierarchicalDataTemplate>定義內容的外觀。  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 下列範例示範如何建立<xref:System.Windows.Controls.TreeView>其中<xref:System.Windows.Controls.TreeViewItem>內容包含<xref:System.Windows.Controls.DockPanel>內嵌內容控制項。  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [TreeView 概觀](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
