---
title: HOW TO：改善 TreeView 的效能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: 3c7bd151e1c8a5f318660cc45702b5b9c98534a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500690"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="8ae68-102">HOW TO：改善 TreeView 的效能</span><span class="sxs-lookup"><span data-stu-id="8ae68-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="8ae68-103">如果<xref:System.Windows.Controls.TreeView>包含許多項目，載入所花費的時間長度可能在使用者介面項目會造成明顯的延遲。</span><span class="sxs-lookup"><span data-stu-id="8ae68-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="8ae68-104">您可以藉由設定改善載入時間`VirtualizingStackPanel.IsVirtualizing`附加屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="8ae68-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="8ae68-105">UI 也可能會變慢，以回應使用者捲動時<xref:System.Windows.Controls.TreeView>藉由使用滑鼠滾輪，或拖曳捲軸捲動方塊。</span><span class="sxs-lookup"><span data-stu-id="8ae68-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="8ae68-106">您可以改善效能<xref:System.Windows.Controls.TreeView>當使用者捲動藉由設定`VirtualizingStackPanel.VirtualizationMode`; 附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8ae68-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ae68-107">範例</span><span class="sxs-lookup"><span data-stu-id="8ae68-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="8ae68-108">描述</span><span class="sxs-lookup"><span data-stu-id="8ae68-108">Description</span></span>  
<span data-ttu-id="8ae68-109">下列範例會建立<xref:System.Windows.Controls.TreeView>，設定`VirtualizingStackPanel.IsVirtualizing`附加屬性設定為 true 並`VirtualizingStackPanel.VirtualizationMode`; 附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>最佳化其效能。</span><span class="sxs-lookup"><span data-stu-id="8ae68-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="8ae68-110">程式碼</span><span class="sxs-lookup"><span data-stu-id="8ae68-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="8ae68-111">下列範例會顯示先前的範例使用的資料。</span><span class="sxs-lookup"><span data-stu-id="8ae68-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="8ae68-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ae68-112">See also</span></span>
- [<span data-ttu-id="8ae68-113">控制項</span><span class="sxs-lookup"><span data-stu-id="8ae68-113">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
