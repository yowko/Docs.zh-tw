---
title: HOW TO：使用放射狀漸層繪製區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: c3bcc11dea4b1f223f629415591ab03588881dde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921822"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="817bc-102">HOW TO：使用放射狀漸層繪製區域</span><span class="sxs-lookup"><span data-stu-id="817bc-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="817bc-103">此範例示範如何使用<xref:System.Windows.Media.RadialGradientBrush>類別，以使用放射狀漸層繪製區域。</span><span class="sxs-lookup"><span data-stu-id="817bc-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="817bc-104">範例</span><span class="sxs-lookup"><span data-stu-id="817bc-104">Example</span></span>  
 <span data-ttu-id="817bc-105">下列範例會使用<xref:System.Windows.Media.RadialGradientBrush>來繪製從黃色會轉換成紅色變成藍色變成淡黃綠色放射狀漸層的矩形。</span><span class="sxs-lookup"><span data-stu-id="817bc-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="817bc-106">下圖顯示前述範例中的漸層。</span><span class="sxs-lookup"><span data-stu-id="817bc-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="817bc-107">漸層停駐點已反白顯示。</span><span class="sxs-lookup"><span data-stu-id="817bc-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="817bc-108">![放射狀漸層中的漸層停駐點](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="817bc-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="817bc-109">本主題中的範例會使用預設座標系統設定的控制點。</span><span class="sxs-lookup"><span data-stu-id="817bc-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="817bc-110">預設座標系統是相對於週框方塊：0 表示 0%的週框方塊中，而 1 表示週框方塊的 100%。</span><span class="sxs-lookup"><span data-stu-id="817bc-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="817bc-111">您可以設定來變更這個座標系統<xref:System.Windows.Media.GradientBrush.MappingMode%2A>屬性設為值<xref:System.Windows.Media.BrushMappingMode.Absolute>。</span><span class="sxs-lookup"><span data-stu-id="817bc-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="817bc-112">絕對座標系統不會相對於週框方塊。</span><span class="sxs-lookup"><span data-stu-id="817bc-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="817bc-113">值會直接在本機空間中解譯。</span><span class="sxs-lookup"><span data-stu-id="817bc-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="817bc-114">針對其他<xref:System.Windows.Media.RadialGradientBrush>範例，請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="817bc-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="817bc-115">如需有關漸層和其他類型的筆刷的詳細資訊，請參閱[使用純色和漸層概觀繪製](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="817bc-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
