---
title: HOW TO：在 TreeView 中尋找 TreeViewItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: 034ec2e57fb3b6a9b3a81f66f6888a68e2c113d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219040"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="c8e3c-102">HOW TO：在 TreeView 中尋找 TreeViewItem</span><span class="sxs-lookup"><span data-stu-id="c8e3c-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="c8e3c-103"><xref:System.Windows.Controls.TreeView>控制項提供便利的方式，來顯示階層式資料。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="c8e3c-104">如果您<xref:System.Windows.Controls.TreeView>繫結至資料來源，<xref:System.Windows.Controls.TreeView.SelectedItem%2A>屬性提供便利的方式，讓您快速擷取選取的資料物件。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="c8e3c-105">通常最好使用基礎資料物件中，但有時候您可能需要以程式設計方式操作的資料包含<xref:System.Windows.Controls.TreeViewItem>。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="c8e3c-106">例如，您可能需要以程式設計方式展開<xref:System.Windows.Controls.TreeViewItem>，或選取不同的項目中<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="c8e3c-107">若要尋找<xref:System.Windows.Controls.TreeViewItem>，其中包含特定的資料物件，則必須周遊的每個層級<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="c8e3c-108">中的項目<xref:System.Windows.Controls.TreeView>也都可以虛擬化來改善效能。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="c8e3c-109">在案例中可能會虛擬化項目，您也必須了解<xref:System.Windows.Controls.TreeViewItem>來檢查它是否包含資料的物件。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8e3c-110">範例</span><span class="sxs-lookup"><span data-stu-id="c8e3c-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8e3c-111">描述</span><span class="sxs-lookup"><span data-stu-id="c8e3c-111">Description</span></span>  
 <span data-ttu-id="c8e3c-112">下列範例會搜尋<xref:System.Windows.Controls.TreeView>針對特定物件，並傳回包含之物件的<xref:System.Windows.Controls.TreeViewItem>。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="c8e3c-113">此範例可確保每個<xref:System.Windows.Controls.TreeViewItem>會具現化，而可以搜尋其子項目。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="c8e3c-114">此範例也適用於如果<xref:System.Windows.Controls.TreeView>不會使用虛擬化的項目。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8e3c-115">下列範例適用於任何<xref:System.Windows.Controls.TreeView>不論基礎資料模型，並搜尋每個<xref:System.Windows.Controls.TreeViewItem>直到找到的物件。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="c8e3c-116">具有較佳的效能的另一個方法是搜尋指定的物件的資料模型、 追蹤內資料階層中，其位置，並找出對應<xref:System.Windows.Controls.TreeViewItem>在<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="c8e3c-117">不過，有較佳的效能的技巧需要資料模型的知識，而且無法在任何給定的一般化<xref:System.Windows.Controls.TreeView>。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="c8e3c-118">程式碼</span><span class="sxs-lookup"><span data-stu-id="c8e3c-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="c8e3c-119">先前的程式碼依賴自訂<xref:System.Windows.Controls.VirtualizingStackPanel>公開一個名為方法`BringIntoView`。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="c8e3c-120">下列程式碼會定義自訂<xref:System.Windows.Controls.VirtualizingStackPanel>。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="c8e3c-121">下列 XAML 示範如何建立<xref:System.Windows.Controls.TreeView>使用自訂<xref:System.Windows.Controls.VirtualizingStackPanel>。</span><span class="sxs-lookup"><span data-stu-id="c8e3c-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c8e3c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8e3c-122">See also</span></span>

- [<span data-ttu-id="c8e3c-123">改善 TreeView 的效能</span><span class="sxs-lookup"><span data-stu-id="c8e3c-123">Improve the Performance of a TreeView</span></span>](how-to-improve-the-performance-of-a-treeview.md)
