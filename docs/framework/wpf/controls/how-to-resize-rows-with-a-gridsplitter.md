---
title: HOW TO：使用 GridSplitter 調整資料列的大小
ms.date: 03/30/2017
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
ms.openlocfilehash: 6760a7a691af4f666294556cae3bc95a4299730a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074270"
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a><span data-ttu-id="21b91-102">HOW TO：使用 GridSplitter 調整資料列的大小</span><span class="sxs-lookup"><span data-stu-id="21b91-102">How to: Resize Rows with a GridSplitter</span></span>
<span data-ttu-id="21b91-103">此範例示範如何使用水平<xref:System.Windows.Controls.GridSplitter>來重新分配的空間中的兩個資料列之間<xref:System.Windows.Controls.Grid>而不需要變更的維度<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="21b91-103">This example shows how to use a horizontal <xref:System.Windows.Controls.GridSplitter> to redistribute the space between two rows in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21b91-104">範例</span><span class="sxs-lookup"><span data-stu-id="21b91-104">Example</span></span>  
 <span data-ttu-id="21b91-105">**如何建立重疊資料列邊緣的 GridSplitter**</span><span class="sxs-lookup"><span data-stu-id="21b91-105">**How to create a GridSplitter that overlays the edge of a row**</span></span>  
  
 <span data-ttu-id="21b91-106">若要指定<xref:System.Windows.Controls.GridSplitter>，調整大小中的相鄰資料列<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Row%2A>附加屬性設定為其中一個您想要調整大小的資料列。</span><span class="sxs-lookup"><span data-stu-id="21b91-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="21b91-107">如果您<xref:System.Windows.Controls.Grid>有一個以上的資料行，設定<xref:System.Windows.Controls.Grid.ColumnSpan%2A>附加屬性指定的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="21b91-107">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to specify the number of columns.</span></span> <span data-ttu-id="21b91-108">然後設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>要<xref:System.Windows.VerticalAlignment.Top>或<xref:System.Windows.VerticalAlignment.Bottom>（您所設定的對齊方式取決於您想要調整大小之兩個資料列）。</span><span class="sxs-lookup"><span data-stu-id="21b91-108">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Top> or <xref:System.Windows.VerticalAlignment.Bottom> (which alignment you set depends on which two rows you want to resize).</span></span> <span data-ttu-id="21b91-109">最後，設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性設<xref:System.Windows.HorizontalAlignment.Stretch>。</span><span class="sxs-lookup"><span data-stu-id="21b91-109">Finally, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>.</span></span>  
  
 <span data-ttu-id="21b91-110">下列範例示範如何定義水平<xref:System.Windows.Controls.GridSplitter>，調整大小，相鄰的資料列。</span><span class="sxs-lookup"><span data-stu-id="21b91-110">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 <span data-ttu-id="21b91-111">A<xref:System.Windows.Controls.GridSplitter>未佔有自己資料列中的其他控制項可能會被遮蔽<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="21b91-111">A <xref:System.Windows.Controls.GridSplitter> that does not occupy its own row may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="21b91-112">如需有關如何防止此問題的詳細資訊，請參閱[確保 GridSplitter 是可見的](how-to-make-sure-that-a-gridsplitter-is-visible.md)。</span><span class="sxs-lookup"><span data-stu-id="21b91-112">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="21b91-113">**如何建立佔有資料列的 GridSplitter**</span><span class="sxs-lookup"><span data-stu-id="21b91-113">**How to create a GridSplitter that occupies a row**</span></span>  
  
 <span data-ttu-id="21b91-114">若要指定<xref:System.Windows.Controls.GridSplitter>所佔用的資料列<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Row%2A>附加屬性設定為其中一個您想要調整大小的資料列。</span><span class="sxs-lookup"><span data-stu-id="21b91-114">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a row in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="21b91-115">如果您<xref:System.Windows.Controls.Grid>有一個以上的資料行，設定<xref:System.Windows.Controls.Grid.ColumnSpan%2A>附加屬性設定為資料行數目。</span><span class="sxs-lookup"><span data-stu-id="21b91-115">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to the number of columns.</span></span> <span data-ttu-id="21b91-116">然後設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>要<xref:System.Windows.VerticalAlignment.Center>，將<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性設<xref:System.Windows.HorizontalAlignment.Stretch>，並設定<xref:System.Windows.Controls.RowDefinition.Height%2A>包含的資料列的<xref:System.Windows.Controls.GridSplitter>至<xref:System.Windows.GridLength.Auto%2A>。</span><span class="sxs-lookup"><span data-stu-id="21b91-116">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>, and set the <xref:System.Windows.Controls.RowDefinition.Height%2A> of the row that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="21b91-117">下列範例示範如何定義水平<xref:System.Windows.Controls.GridSplitter>，佔有一個資料列，並調整大小在左邊或右邊的資料列。</span><span class="sxs-lookup"><span data-stu-id="21b91-117">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that occupies a row and resizes the rows on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="21b91-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21b91-118">See also</span></span>

- <xref:System.Windows.Controls.GridSplitter>
- [<span data-ttu-id="21b91-119">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="21b91-119">How-to Topics</span></span>](gridsplitter-how-to-topics.md)
