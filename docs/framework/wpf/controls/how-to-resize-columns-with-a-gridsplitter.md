---
title: "操作說明：使用 GridSplitter 調整資料行的大小"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d68d829e5543b1c299668493c11b62ccb11d81af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a><span data-ttu-id="402e0-102">操作說明：使用 GridSplitter 調整資料行的大小</span><span class="sxs-lookup"><span data-stu-id="402e0-102">How to: Resize Columns with a GridSplitter</span></span>
<span data-ttu-id="402e0-103">這個範例示範如何建立垂直<xref:System.Windows.Controls.GridSplitter>才能重新發佈中的兩個資料行之間的間距<xref:System.Windows.Controls.Grid>而不需要變更維度的<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="402e0-103">This example shows how to create a vertical <xref:System.Windows.Controls.GridSplitter> in order to redistribute the space between two columns in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="402e0-104">範例</span><span class="sxs-lookup"><span data-stu-id="402e0-104">Example</span></span>  
 <span data-ttu-id="402e0-105">**如何建立重疊資料行邊緣的 GridSplitter**</span><span class="sxs-lookup"><span data-stu-id="402e0-105">**How to create a GridSplitter that overlays the edge of a column**</span></span>  
  
 <span data-ttu-id="402e0-106">若要指定<xref:System.Windows.Controls.GridSplitter>的調整大小，相鄰的資料行中<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Column%2A>附加至其中一個您要調整大小的資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="402e0-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent columns in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="402e0-107">如果您<xref:System.Windows.Controls.Grid>有一個以上的資料列集<xref:System.Windows.Controls.Grid.RowSpan%2A>附加屬性的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="402e0-107">If your <xref:System.Windows.Controls.Grid> has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="402e0-108">然後設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性<xref:System.Windows.HorizontalAlignment.Left>或<xref:System.Windows.HorizontalAlignment.Right>（您所設定的對齊方式取決於您要調整大小的兩個資料行上）。</span><span class="sxs-lookup"><span data-stu-id="402e0-108">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Left> or <xref:System.Windows.HorizontalAlignment.Right> (which alignment you set depends on which two columns you want to resize).</span></span> <span data-ttu-id="402e0-109">最後，設定<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性<xref:System.Windows.VerticalAlignment.Stretch>。</span><span class="sxs-lookup"><span data-stu-id="402e0-109">Finally, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 <span data-ttu-id="402e0-110">A<xref:System.Windows.Controls.GridSplitter>沒有自己的資料行中的其他控制項可能會遮蔽<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="402e0-110">A <xref:System.Windows.Controls.GridSplitter> that does not have its own column may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="402e0-111">如需有關如何防止此問題的詳細資訊，請參閱[確保 GridSplitter 是可見的](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)。</span><span class="sxs-lookup"><span data-stu-id="402e0-111">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="402e0-112">**如何建立佔有資料行的 GridSplitter**</span><span class="sxs-lookup"><span data-stu-id="402e0-112">**How to create a GridSplitter that occupies a column**</span></span>  
  
 <span data-ttu-id="402e0-113">若要指定<xref:System.Windows.Controls.GridSplitter>，佔用中的資料行<xref:System.Windows.Controls.Grid>，將<xref:System.Windows.Controls.Grid.Column%2A>附加至其中一個您要調整大小的資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="402e0-113">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a column in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="402e0-114">如果方格具有多個資料列，設定<xref:System.Windows.Controls.Grid.RowSpan%2A>附加屬性的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="402e0-114">If your Grid has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="402e0-115">然後設定<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>至<xref:System.Windows.HorizontalAlignment.Center>，將<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>屬性<xref:System.Windows.VerticalAlignment.Stretch>，並設定<xref:System.Windows.Controls.ColumnDefinition.Width%2A>包含的資料行的<xref:System.Windows.Controls.GridSplitter>至<xref:System.Windows.GridLength.Auto%2A>。</span><span class="sxs-lookup"><span data-stu-id="402e0-115">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> to <xref:System.Windows.HorizontalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>, and set the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the column that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="402e0-116">下列範例示範如何定義垂直<xref:System.Windows.Controls.GridSplitter>佔用資料行，而且會在左邊或右邊的資料行的調整大小。</span><span class="sxs-lookup"><span data-stu-id="402e0-116">The following example shows how to define a vertical <xref:System.Windows.Controls.GridSplitter> that occupies a column and resizes the columns on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="402e0-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="402e0-117">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="402e0-118">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="402e0-118">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
