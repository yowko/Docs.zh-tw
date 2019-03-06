---
title: HOW TO：改善 TreeView 的效能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: d04d5997e6f02a4227704b668fdf19324ea20f26
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364732"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a><span data-ttu-id="c8f40-102">HOW TO：改善 TreeView 的效能</span><span class="sxs-lookup"><span data-stu-id="c8f40-102">How to: Improve the Performance of a TreeView</span></span>
<span data-ttu-id="c8f40-103">如果<xref:System.Windows.Controls.TreeView>包含許多項目，載入所花費的時間長度可能在使用者介面項目會造成明顯的延遲。</span><span class="sxs-lookup"><span data-stu-id="c8f40-103">If a <xref:System.Windows.Controls.TreeView> contains many items, the amount of time it takes to load may cause a significant delay in the user interface.</span></span> <span data-ttu-id="c8f40-104">您可以藉由設定改善載入時間`VirtualizingStackPanel.IsVirtualizing`附加屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="c8f40-104">You can improve the load time by setting the `VirtualizingStackPanel.IsVirtualizing` attached property to `true`.</span></span>  <span data-ttu-id="c8f40-105">UI 也可能會變慢，以回應使用者捲動時<xref:System.Windows.Controls.TreeView>藉由使用滑鼠滾輪，或拖曳捲軸捲動方塊。</span><span class="sxs-lookup"><span data-stu-id="c8f40-105">The UI might also be slow to react when a user scrolls the <xref:System.Windows.Controls.TreeView> by using the mouse wheel or dragging the thumb of a scrollbar.</span></span> <span data-ttu-id="c8f40-106">您可以改善效能<xref:System.Windows.Controls.TreeView>當使用者捲動藉由設定`VirtualizingStackPanel.VirtualizationMode`; 附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c8f40-106">You can improve the performance of the <xref:System.Windows.Controls.TreeView> when the user scrolls by setting the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8f40-107">範例</span><span class="sxs-lookup"><span data-stu-id="c8f40-107">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8f40-108">描述</span><span class="sxs-lookup"><span data-stu-id="c8f40-108">Description</span></span>  
<span data-ttu-id="c8f40-109">下列範例會建立<xref:System.Windows.Controls.TreeView>，設定`VirtualizingStackPanel.IsVirtualizing`附加屬性設定為 true 並`VirtualizingStackPanel.VirtualizationMode`; 附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>最佳化其效能。</span><span class="sxs-lookup"><span data-stu-id="c8f40-109">The following example creates a <xref:System.Windows.Controls.TreeView> that sets the `VirtualizingStackPanel.IsVirtualizing` attached property to true and the `VirtualizingStackPanel.VirtualizationMode` attached property to <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> to optimize its performance.</span></span>  
  
## <a name="code"></a><span data-ttu-id="c8f40-110">程式碼</span><span class="sxs-lookup"><span data-stu-id="c8f40-110">Code</span></span>  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 <span data-ttu-id="c8f40-111">下列範例會顯示先前的範例使用的資料。</span><span class="sxs-lookup"><span data-stu-id="c8f40-111">The following example shows the data that the previous example uses.</span></span>  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a><span data-ttu-id="c8f40-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8f40-112">See also</span></span>
- [<span data-ttu-id="c8f40-113">控制項</span><span class="sxs-lookup"><span data-stu-id="c8f40-113">Controls</span></span>](../advanced/optimizing-performance-controls.md)
