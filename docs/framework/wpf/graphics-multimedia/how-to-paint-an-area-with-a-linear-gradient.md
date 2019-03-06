---
title: HOW TO：使用線形漸層繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: c48ff13811d784ecc7042b73b964a9e6f2d42a34
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367241"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="99ac3-102">HOW TO：使用線形漸層繪製區域</span><span class="sxs-lookup"><span data-stu-id="99ac3-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="99ac3-103">此範例示範如何使用<xref:System.Windows.Media.LinearGradientBrush>類別，以使用線形漸層繪製區域。</span><span class="sxs-lookup"><span data-stu-id="99ac3-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="99ac3-104">在下列範例中，<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>使用轉換從黃色到紅色變成藍色變成淡黃綠色對角線性漸層繪製。</span><span class="sxs-lookup"><span data-stu-id="99ac3-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99ac3-105">範例</span><span class="sxs-lookup"><span data-stu-id="99ac3-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="99ac3-106">下圖顯示先前範例所建立的漸層。</span><span class="sxs-lookup"><span data-stu-id="99ac3-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="99ac3-107">![對角線性漸層](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="99ac3-107">![Diagonal linear gradient](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="99ac3-108">若要建立的水平的線性漸層，請變更<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>和<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>的<xref:System.Windows.Media.LinearGradientBrush>到 (0,0.5) 和 (1,0.5)。</span><span class="sxs-lookup"><span data-stu-id="99ac3-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="99ac3-109">在下列範例中，<xref:System.Windows.Shapes.Rectangle>用於水平的線性漸層繪製。</span><span class="sxs-lookup"><span data-stu-id="99ac3-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="99ac3-110">下圖顯示先前範例所建立的漸層。</span><span class="sxs-lookup"><span data-stu-id="99ac3-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="99ac3-111">![水平的線性漸層](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="99ac3-111">![A horizontal linear gradient](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="99ac3-112">若要建立垂直線性漸層，請變更<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>和<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>的<xref:System.Windows.Media.LinearGradientBrush>到 (0.5,0) 和 (0.5,1)。</span><span class="sxs-lookup"><span data-stu-id="99ac3-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="99ac3-113">在下列範例中，<xref:System.Windows.Shapes.Rectangle>用於垂直線性漸層繪製。</span><span class="sxs-lookup"><span data-stu-id="99ac3-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="99ac3-114">下圖顯示先前範例所建立的漸層。</span><span class="sxs-lookup"><span data-stu-id="99ac3-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="99ac3-115">![垂直線性漸層](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="99ac3-115">![Vertical linear gradient](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99ac3-116">本主題中的範例會使用預設座標系統來設定起始點和結束點。</span><span class="sxs-lookup"><span data-stu-id="99ac3-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="99ac3-117">預設座標系統是相對於週框方塊：0 表示 0%的週框方塊中，而 1 表示週框方塊的 100%。</span><span class="sxs-lookup"><span data-stu-id="99ac3-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="99ac3-118">您可以設定來變更這個座標系統<xref:System.Windows.Media.GradientBrush.MappingMode%2A>屬性設為值<xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="99ac3-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="99ac3-119">絕對座標系統不會相對於週框方塊。</span><span class="sxs-lookup"><span data-stu-id="99ac3-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="99ac3-120">值會直接在本機空間中解譯。</span><span class="sxs-lookup"><span data-stu-id="99ac3-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="99ac3-121">如需其他範例，請參閱 <<c0> [ 筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="99ac3-121">For additional examples, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="99ac3-122">如需有關漸層和其他類型的筆刷的詳細資訊，請參閱[使用純色和漸層概觀繪製](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="99ac3-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
