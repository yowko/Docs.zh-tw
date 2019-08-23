---
title: 作法：使用線形漸層繪製區域
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 92c9ccd846dbbce043d13e6ba82b9fa8e72fa8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916169"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="93cf8-102">HOW TO：使用線形漸層繪製區域</span><span class="sxs-lookup"><span data-stu-id="93cf8-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="93cf8-103">這個範例顯示如何使用<xref:System.Windows.Media.LinearGradientBrush>類別, 以線性漸層繪製區域。</span><span class="sxs-lookup"><span data-stu-id="93cf8-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="93cf8-104">在下列範例中, <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>的會以對角線線性漸層繪製, 而此漸層會從黃色轉換成紅色到藍色, 到酸綠色。</span><span class="sxs-lookup"><span data-stu-id="93cf8-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93cf8-105">範例</span><span class="sxs-lookup"><span data-stu-id="93cf8-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="93cf8-106">下圖顯示上一個範例所建立的漸層。</span><span class="sxs-lookup"><span data-stu-id="93cf8-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="93cf8-107">![對角線線性]漸層(./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="93cf8-107">![Diagonal linear gradient](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="93cf8-108">若要建立水平線性漸層, 請<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>將<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>的和<xref:System.Windows.Media.LinearGradientBrush>變更為 (0, 0.5) 和 (1, 0.5)。</span><span class="sxs-lookup"><span data-stu-id="93cf8-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="93cf8-109">在下列範例中, <xref:System.Windows.Shapes.Rectangle>會以水平線性漸層繪製。</span><span class="sxs-lookup"><span data-stu-id="93cf8-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="93cf8-110">下圖顯示上一個範例所建立的漸層。</span><span class="sxs-lookup"><span data-stu-id="93cf8-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="93cf8-111">![水平線性]漸層(./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="93cf8-111">![A horizontal linear gradient](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="93cf8-112">若要建立垂直線性漸層, 請<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>將<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>的和<xref:System.Windows.Media.LinearGradientBrush>變更為 (0.5, 0) 和 (0.5, 1)。</span><span class="sxs-lookup"><span data-stu-id="93cf8-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="93cf8-113">在下列範例中, <xref:System.Windows.Shapes.Rectangle>會以垂直線性漸層繪製。</span><span class="sxs-lookup"><span data-stu-id="93cf8-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="93cf8-114">下圖顯示上一個範例所建立的漸層。</span><span class="sxs-lookup"><span data-stu-id="93cf8-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="93cf8-115">![垂直線性]漸層(./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="93cf8-115">![Vertical linear gradient](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93cf8-116">本主題中的範例會使用預設座標系統來設定起始點和結束點。</span><span class="sxs-lookup"><span data-stu-id="93cf8-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="93cf8-117">預設座標系統是相對於周框方塊:0 表示週框方塊的 0%，1 表示週框方塊的 100%。</span><span class="sxs-lookup"><span data-stu-id="93cf8-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="93cf8-118">您可以藉由將<xref:System.Windows.Media.GradientBrush.MappingMode%2A>屬性設定為值<xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>來變更此座標系統。</span><span class="sxs-lookup"><span data-stu-id="93cf8-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="93cf8-119">絕對座標系統不會相對於週框方塊。</span><span class="sxs-lookup"><span data-stu-id="93cf8-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="93cf8-120">值會直接在本機空間中解譯。</span><span class="sxs-lookup"><span data-stu-id="93cf8-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="93cf8-121">如需其他範例, 請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="93cf8-121">For additional examples, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="93cf8-122">如需漸層和其他類型之筆刷的詳細資訊, 請參閱[使用純色和漸層繪製的色彩](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="93cf8-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
