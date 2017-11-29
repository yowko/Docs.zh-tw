---
title: "操作說明：使用 GridSplitter 調整資料列的大小"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6621cc0048270b97c42ff4c4e646b0ddd9ca3477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a><span data-ttu-id="ec181-102">操作說明：使用 GridSplitter 調整資料列的大小</span><span class="sxs-lookup"><span data-stu-id="ec181-102">How to: Resize Rows with a GridSplitter</span></span>
<span data-ttu-id="ec181-103">這個範例示範如何使用水平<xref:System.Windows.Controls.GridSplitter>轉散發中的兩個資料列之間的空間<xref:System.Windows.Controls.Grid>而不需要變更維度的<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="ec181-103">This example shows how to use a horizontal <xref:System.Windows.Controls.GridSplitter> to redistribute the space between two rows in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec181-104">範例</span><span class="sxs-lookup"><span data-stu-id="ec181-104">Example</span></span>  
 <span data-ttu-id="ec181-105">**如何建立重疊資料列邊緣的 GridSplitter**</span><span class="sxs-lookup"><span data-stu-id="ec181-105">**How to create a GridSplitter that overlays the edge of a row**</span></span>  
  
 <span data-ttu-id="ec181-106">若要指定<xref:System.Windows.Controls.GridSplitter>的調整大小，相鄰的資料列中<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Row%2A>附加至您要調整大小的資料列的其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="ec181-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="ec181-107">如果您<xref:System.Windows.Controls.Grid>具有一個以上的資料行設定<xref:System.Windows.Controls.Grid.ColumnSpan%2A>附加屬性，以指定的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="ec181-107">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to specify the number of columns.</span></span> <span data-ttu-id="ec181-108">然後設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>至<xref:System.Windows.VerticalAlignment.Top>或<xref:System.Windows.VerticalAlignment.Bottom>（您所設定的對齊方式取決於您要調整大小之兩個資料列）。</span><span class="sxs-lookup"><span data-stu-id="ec181-108">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Top> or <xref:System.Windows.VerticalAlignment.Bottom> (which alignment you set depends on which two rows you want to resize).</span></span> <span data-ttu-id="ec181-109">最後，設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性<xref:System.Windows.HorizontalAlignment.Stretch>。</span><span class="sxs-lookup"><span data-stu-id="ec181-109">Finally, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>.</span></span>  
  
 <span data-ttu-id="ec181-110">下列範例示範如何定義水平<xref:System.Windows.Controls.GridSplitter>的調整大小，相鄰的資料列。</span><span class="sxs-lookup"><span data-stu-id="ec181-110">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 <span data-ttu-id="ec181-111">A<xref:System.Windows.Controls.GridSplitter>不會佔用自己的資料列中的其他控制項可能會遮蔽<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="ec181-111">A <xref:System.Windows.Controls.GridSplitter> that does not occupy its own row may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="ec181-112">如需有關如何防止此問題的詳細資訊，請參閱[確保 GridSplitter 是可見的](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)。</span><span class="sxs-lookup"><span data-stu-id="ec181-112">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="ec181-113">**如何建立佔有資料列的 GridSplitter**</span><span class="sxs-lookup"><span data-stu-id="ec181-113">**How to create a GridSplitter that occupies a row**</span></span>  
  
 <span data-ttu-id="ec181-114">若要指定<xref:System.Windows.Controls.GridSplitter>所佔用的資料列中<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Row%2A>附加至您要調整大小的資料列的其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="ec181-114">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a row in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="ec181-115">如果您<xref:System.Windows.Controls.Grid>具有一個以上的資料行設定<xref:System.Windows.Controls.Grid.ColumnSpan%2A>附加屬性的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="ec181-115">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to the number of columns.</span></span> <span data-ttu-id="ec181-116">然後設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>至<xref:System.Windows.VerticalAlignment.Center>，將<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性<xref:System.Windows.HorizontalAlignment.Stretch>，並設定<xref:System.Windows.Controls.RowDefinition.Height%2A>包含的資料列的<xref:System.Windows.Controls.GridSplitter>至<xref:System.Windows.GridLength.Auto%2A>。</span><span class="sxs-lookup"><span data-stu-id="ec181-116">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>, and set the <xref:System.Windows.Controls.RowDefinition.Height%2A> of the row that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="ec181-117">下列範例示範如何定義水平<xref:System.Windows.Controls.GridSplitter>，會佔用一個資料列而調整大小，在左邊或右邊的資料列。</span><span class="sxs-lookup"><span data-stu-id="ec181-117">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that occupies a row and resizes the rows on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="ec181-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec181-118">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="ec181-119">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="ec181-119">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
