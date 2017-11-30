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
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="f904e-102">如何：在 TreeView 中尋找 TreeViewItem</span><span class="sxs-lookup"><span data-stu-id="f904e-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="f904e-103"><xref:System.Windows.Controls.TreeView>控制項提供便利的方式顯示階層式資料。</span><span class="sxs-lookup"><span data-stu-id="f904e-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="f904e-104">如果您<xref:System.Windows.Controls.TreeView>繫結至資料來源，<xref:System.Windows.Controls.TreeView.SelectedItem%2A>屬性提供便利的方式，讓您快速擷取選取的資料物件。</span><span class="sxs-lookup"><span data-stu-id="f904e-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="f904e-105">它通常是最佳選擇使用基礎資料物件，但有時候您可能需要以程式設計方式操作的資料包含<xref:System.Windows.Controls.TreeViewItem>。</span><span class="sxs-lookup"><span data-stu-id="f904e-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="f904e-106">例如，您可能需要以程式設計方式展開<xref:System.Windows.Controls.TreeViewItem>，或選取不同的項目中<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="f904e-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="f904e-107">若要尋找<xref:System.Windows.Controls.TreeViewItem>包含特定資料物件，則必須周遊的每個層級<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="f904e-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="f904e-108">中的項目<xref:System.Windows.Controls.TreeView>也都可以虛擬化來改善效能。</span><span class="sxs-lookup"><span data-stu-id="f904e-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="f904e-109">在案例中可能會虛擬化項目，您也必須了解<xref:System.Windows.Controls.TreeViewItem>檢查它是否包含資料的物件。</span><span class="sxs-lookup"><span data-stu-id="f904e-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f904e-110">範例</span><span class="sxs-lookup"><span data-stu-id="f904e-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="f904e-111">說明</span><span class="sxs-lookup"><span data-stu-id="f904e-111">Description</span></span>  
 <span data-ttu-id="f904e-112">下列範例會搜尋<xref:System.Windows.Controls.TreeView>的特定物件，並傳回所含之物件的<xref:System.Windows.Controls.TreeViewItem>。</span><span class="sxs-lookup"><span data-stu-id="f904e-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="f904e-113">範例會確保每個<xref:System.Windows.Controls.TreeViewItem>具現化，而可以搜尋其子項目。</span><span class="sxs-lookup"><span data-stu-id="f904e-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="f904e-114">這個範例也適用於如果<xref:System.Windows.Controls.TreeView>不使用虛擬化的項目。</span><span class="sxs-lookup"><span data-stu-id="f904e-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f904e-115">下列範例適用於任何<xref:System.Windows.Controls.TreeView>，不論基礎資料模型和搜尋每個<xref:System.Windows.Controls.TreeViewItem>直到找到的物件。</span><span class="sxs-lookup"><span data-stu-id="f904e-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="f904e-116">另一個有較佳的效能的技術是搜尋指定的物件的資料模型、 追蹤資料階層架構中的位置，並找出對應<xref:System.Windows.Controls.TreeViewItem>中<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="f904e-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="f904e-117">不過，有更佳的效能的技術需要資料模型的知識，而且無法一般化任何給定的<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="f904e-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="f904e-118">程式碼</span><span class="sxs-lookup"><span data-stu-id="f904e-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="f904e-119">先前的程式碼依賴自訂<xref:System.Windows.Controls.VirtualizingStackPanel>可公開方法，名為`BringIntoView`。</span><span class="sxs-lookup"><span data-stu-id="f904e-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="f904e-120">下列程式碼會定義自訂<xref:System.Windows.Controls.VirtualizingStackPanel>。</span><span class="sxs-lookup"><span data-stu-id="f904e-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="f904e-121">下列 XAML 顯示如何建立<xref:System.Windows.Controls.TreeView>使用自訂<xref:System.Windows.Controls.VirtualizingStackPanel>。</span><span class="sxs-lookup"><span data-stu-id="f904e-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f904e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f904e-122">See Also</span></span>  
 [<span data-ttu-id="f904e-123">改善 TreeView 的效能</span><span class="sxs-lookup"><span data-stu-id="f904e-123">Improve the Performance of a TreeView</span></span>](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
