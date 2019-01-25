---
title: HOW TO：取得 Visual 的位移
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: ad45dee5b72594f30b141e3affbb26706af645aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645388"
---
# <a name="how-to-get-the-offset-of-a-visual"></a><span data-ttu-id="d3024-102">HOW TO：取得 Visual 的位移</span><span class="sxs-lookup"><span data-stu-id="d3024-102">How to: Get the Offset of a Visual</span></span>
<span data-ttu-id="d3024-103">這些範例示範如何擷取相對於其父代，或任何上階或下階的視覺物件的位移的值。</span><span class="sxs-lookup"><span data-stu-id="d3024-103">These examples show how to retrieve the offset value of a visual object that is relative to its parent, or any ancestor or descendant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3024-104">範例</span><span class="sxs-lookup"><span data-stu-id="d3024-104">Example</span></span>  
 <span data-ttu-id="d3024-105">下列標記範例示範<xref:System.Windows.Controls.TextBlock>定義與<xref:System.Windows.FrameworkElement.Margin%2A>值為 4。</span><span class="sxs-lookup"><span data-stu-id="d3024-105">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is defined with <xref:System.Windows.FrameworkElement.Margin%2A> value of 4.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 <span data-ttu-id="d3024-106">下列程式碼範例示範如何使用<xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A>方法來擷取的位移<xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="d3024-106">The following code example shows how to use the <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="d3024-107">位移的值都包含在傳回<xref:System.Windows.Vector>值。</span><span class="sxs-lookup"><span data-stu-id="d3024-107">The offset values are contained within the returned <xref:System.Windows.Vector> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 <span data-ttu-id="d3024-108">位移會考量<xref:System.Windows.FrameworkElement.Margin%2A>值。</span><span class="sxs-lookup"><span data-stu-id="d3024-108">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> value.</span></span> <span data-ttu-id="d3024-109">在此情況下，<xref:System.Windows.Vector.X%2A>為 4，和<xref:System.Windows.Vector.Y%2A>為 4。</span><span class="sxs-lookup"><span data-stu-id="d3024-109">In this case, <xref:System.Windows.Vector.X%2A> is 4, and <xref:System.Windows.Vector.Y%2A> is 4.</span></span>  
  
 <span data-ttu-id="d3024-110">傳回的位移的值是相對於父代<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="d3024-110">The returned offset value is relative to the parent of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="d3024-111">如果您想要傳回的位移的值不是相對於父代<xref:System.Windows.Media.Visual>，使用<xref:System.Windows.Media.Visual.TransformToAncestor%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="d3024-111">If you want to return an offset value that is not relative to the parent of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a><span data-ttu-id="d3024-112">取得相對於上階的位移</span><span class="sxs-lookup"><span data-stu-id="d3024-112">Getting the Offset Relative to an Ancestor</span></span>  
 <span data-ttu-id="d3024-113">下列標記範例示範<xref:System.Windows.Controls.TextBlock>巢狀內兩個<xref:System.Windows.Controls.StackPanel>物件。</span><span class="sxs-lookup"><span data-stu-id="d3024-113">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is nested within two <xref:System.Windows.Controls.StackPanel> objects.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 <span data-ttu-id="d3024-114">下圖顯示標記的結果。</span><span class="sxs-lookup"><span data-stu-id="d3024-114">The following illustration shows the results of the markup.</span></span>  
  
 <span data-ttu-id="d3024-115">![物件的位移值](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")</span><span class="sxs-lookup"><span data-stu-id="d3024-115">![Offset values of objects](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")</span></span>  
<span data-ttu-id="d3024-116">巢狀內兩個 StackPanels 的 TextBlock</span><span class="sxs-lookup"><span data-stu-id="d3024-116">TextBlock nested within two StackPanels</span></span>  
  
 <span data-ttu-id="d3024-117">下列程式碼範例示範如何使用<xref:System.Windows.Media.Visual.TransformToAncestor%2A>方法來擷取的位移<xref:System.Windows.Controls.TextBlock>相對於包含<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="d3024-117">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock> relative to the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="d3024-118">位移的值都包含在傳回<xref:System.Windows.Media.GeneralTransform>值。</span><span class="sxs-lookup"><span data-stu-id="d3024-118">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 <span data-ttu-id="d3024-119">位移會考量<xref:System.Windows.FrameworkElement.Margin%2A>內包含的所有物件的值<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="d3024-119">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects within the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="d3024-120">在此情況下，<xref:System.Windows.Vector.X%2A>為 28 (16 + 8 + 4)，和<xref:System.Windows.Vector.Y%2A>為 28。</span><span class="sxs-lookup"><span data-stu-id="d3024-120">In this case, <xref:System.Windows.Vector.X%2A> is 28 (16 + 8 + 4), and <xref:System.Windows.Vector.Y%2A> is 28.</span></span>  
  
 <span data-ttu-id="d3024-121">傳回的位移的值是相對於上階<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="d3024-121">The returned offset value is relative to the ancestor of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="d3024-122">如果您想要傳回的位移的值的子系相對於所<xref:System.Windows.Media.Visual>，使用<xref:System.Windows.Media.Visual.TransformToDescendant%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="d3024-122">If you want to return an offset value that is relative to the descendant of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a><span data-ttu-id="d3024-123">取得相對於其下階的位移</span><span class="sxs-lookup"><span data-stu-id="d3024-123">Getting the Offset Relative to a Descendant</span></span>  
 <span data-ttu-id="d3024-124">下列標記範例示範<xref:System.Windows.Controls.TextBlock>中所含<xref:System.Windows.Controls.StackPanel>物件。</span><span class="sxs-lookup"><span data-stu-id="d3024-124">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is contained within a <xref:System.Windows.Controls.StackPanel> object.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 <span data-ttu-id="d3024-125">下列程式碼範例示範如何使用<xref:System.Windows.Media.Visual.TransformToDescendant%2A>方法來擷取的位移<xref:System.Windows.Controls.StackPanel>相對於它的子系<xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="d3024-125">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method to retrieve the offset of the <xref:System.Windows.Controls.StackPanel> relative to its child <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="d3024-126">位移的值都包含在傳回<xref:System.Windows.Media.GeneralTransform>值。</span><span class="sxs-lookup"><span data-stu-id="d3024-126">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 <span data-ttu-id="d3024-127">位移會考量<xref:System.Windows.FrameworkElement.Margin%2A>的所有物件的值。</span><span class="sxs-lookup"><span data-stu-id="d3024-127">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects.</span></span> <span data-ttu-id="d3024-128">在此情況下，<xref:System.Windows.Vector.X%2A>為-4，和<xref:System.Windows.Vector.Y%2A>為-4。</span><span class="sxs-lookup"><span data-stu-id="d3024-128">In this case, <xref:System.Windows.Vector.X%2A> is -4, and <xref:System.Windows.Vector.Y%2A> is -4.</span></span> <span data-ttu-id="d3024-129">位移的值會是負值，因為父物件的位移負相對於其子物件。</span><span class="sxs-lookup"><span data-stu-id="d3024-129">The offset values are negative values, since the parent object is negatively offset relative to its child object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3024-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3024-130">See also</span></span>
- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="d3024-131">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="d3024-131">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
