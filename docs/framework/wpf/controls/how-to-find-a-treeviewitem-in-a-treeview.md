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
ms.openlocfilehash: ad72c7a7fb11dfe605db4119dde831b47dd7c5a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962086"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="309f3-102">作法：在 TreeView 中尋找 TreeViewItem</span><span class="sxs-lookup"><span data-stu-id="309f3-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="309f3-103"><xref:System.Windows.Controls.TreeView>控制項提供便利的方式來顯示階層式資料。</span><span class="sxs-lookup"><span data-stu-id="309f3-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="309f3-104">如果您<xref:System.Windows.Controls.TreeView>的系結至資料來源<xref:System.Windows.Controls.TreeView.SelectedItem%2A> , 屬性會提供便利的方式, 讓您快速地抓取選取的資料物件。</span><span class="sxs-lookup"><span data-stu-id="309f3-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="309f3-105">通常最好是使用基礎資料物件, 但有時候您可能需要以程式設計方式操作包含<xref:System.Windows.Controls.TreeViewItem>的資料。</span><span class="sxs-lookup"><span data-stu-id="309f3-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="309f3-106">例如, 您可能需要以程式設計方式展開<xref:System.Windows.Controls.TreeViewItem>, 或<xref:System.Windows.Controls.TreeView>在中選取不同的專案。</span><span class="sxs-lookup"><span data-stu-id="309f3-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="309f3-107">若要尋找<xref:System.Windows.Controls.TreeViewItem>包含特定資料物件的, 您必須跨越的<xref:System.Windows.Controls.TreeView>每個層級。</span><span class="sxs-lookup"><span data-stu-id="309f3-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="309f3-108">中的專案也<xref:System.Windows.Controls.TreeView>可以虛擬化以改善效能。</span><span class="sxs-lookup"><span data-stu-id="309f3-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="309f3-109">如果專案可能已虛擬化, 您也必須<xref:System.Windows.Controls.TreeViewItem>瞭解, 以檢查它是否包含資料物件。</span><span class="sxs-lookup"><span data-stu-id="309f3-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="309f3-110">範例</span><span class="sxs-lookup"><span data-stu-id="309f3-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="309f3-111">描述</span><span class="sxs-lookup"><span data-stu-id="309f3-111">Description</span></span>  
 <span data-ttu-id="309f3-112">下列範例會在中<xref:System.Windows.Controls.TreeView>搜尋特定物件, 並傳回包含<xref:System.Windows.Controls.TreeViewItem>的物件。</span><span class="sxs-lookup"><span data-stu-id="309f3-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="309f3-113">此範例會確保每<xref:System.Windows.Controls.TreeViewItem>個都具現化, 以便能夠搜尋其子專案。</span><span class="sxs-lookup"><span data-stu-id="309f3-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="309f3-114">這個範例也適用于未<xref:System.Windows.Controls.TreeView>使用虛擬化專案的情況。</span><span class="sxs-lookup"><span data-stu-id="309f3-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="309f3-115">下列範例適用于任何<xref:System.Windows.Controls.TreeView>, 而不論基礎資料模型為何, 並會在找到物件之前搜尋每個。 <xref:System.Windows.Controls.TreeViewItem></span><span class="sxs-lookup"><span data-stu-id="309f3-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="309f3-116">另一個具有較佳效能的技術是在資料模型中搜尋指定的物件、追蹤其在資料階層中的位置, 然後<xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.TreeView>在中尋找對應的。</span><span class="sxs-lookup"><span data-stu-id="309f3-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="309f3-117">不過, 效能較佳的技術需要資料模型的知識, 而且無法針對任何指定<xref:System.Windows.Controls.TreeView>的進行一般化。</span><span class="sxs-lookup"><span data-stu-id="309f3-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="309f3-118">程式碼</span><span class="sxs-lookup"><span data-stu-id="309f3-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="309f3-119">先前的程式碼依賴會公開<xref:System.Windows.Controls.VirtualizingStackPanel>名為`BringIntoView`之方法的自訂。</span><span class="sxs-lookup"><span data-stu-id="309f3-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="309f3-120">下列程式碼會定義自<xref:System.Windows.Controls.VirtualizingStackPanel>定義。</span><span class="sxs-lookup"><span data-stu-id="309f3-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="309f3-121">下列 XAML 顯示如何建立<xref:System.Windows.Controls.TreeView>使用自訂<xref:System.Windows.Controls.VirtualizingStackPanel>的。</span><span class="sxs-lookup"><span data-stu-id="309f3-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="309f3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="309f3-122">See also</span></span>

- [<span data-ttu-id="309f3-123">改善 TreeView 的效能</span><span class="sxs-lookup"><span data-stu-id="309f3-123">Improve the Performance of a TreeView</span></span>](how-to-improve-the-performance-of-a-treeview.md)
