---
title: "如何：改善 TreeView 的效能"
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
helpviewer_keywords: TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 209f2c5645758aba4d1e10fc36fe773faa975e6b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a>如何：改善 TreeView 的效能
如果<xref:System.Windows.Controls.TreeView>包含許多項目，載入所花費的時間量可能會造成明顯的延遲使用者介面中。 您可以藉由設定改善載入時間`VirtualizingStackPanel.IsVirtualizing`附加屬性`true`。  UI 也可能會變慢，當使用者捲動時反應<xref:System.Windows.Controls.TreeView>藉由使用滑鼠滾輪，或拖曳捲軸的捲動方塊。 您可以改善效能<xref:System.Windows.Controls.TreeView>當使用者捲動藉由設定`VirtualizingStackPanel.VirtualizationMode`附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>。  
  
## <a name="example"></a>範例  
  
## <a name="description"></a>說明  
下列範例會建立<xref:System.Windows.Controls.TreeView>設定`VirtualizingStackPanel.IsVirtualizing`附加屬性為 true 而`VirtualizingStackPanel.VirtualizationMode`附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>最佳化其效能。  
  
## <a name="code"></a>程式碼  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 下列範例會顯示先前的範例使用的資料。  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a>另請參閱  
 [控制項](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
