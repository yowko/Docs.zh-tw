---
title: 如何：使用放射狀漸層繪製區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 8a53d5d7247f82905816265f7c92b22f287591c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452749"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="6a53c-102">如何：使用放射狀漸層繪製區域</span><span class="sxs-lookup"><span data-stu-id="6a53c-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="6a53c-103">這個範例會示範如何使用 <xref:System.Windows.Media.RadialGradientBrush> 類別，以放射狀漸層繪製區域。</span><span class="sxs-lookup"><span data-stu-id="6a53c-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a53c-104">範例</span><span class="sxs-lookup"><span data-stu-id="6a53c-104">Example</span></span>  
 <span data-ttu-id="6a53c-105">下列範例會使用 <xref:System.Windows.Media.RadialGradientBrush> 來繪製具有放射漸層的矩形，而星形漸層會從黃色轉換成紅色到藍色，以綠色顯示。</span><span class="sxs-lookup"><span data-stu-id="6a53c-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="6a53c-106">下圖顯示上述範例中的漸層。</span><span class="sxs-lookup"><span data-stu-id="6a53c-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="6a53c-107">漸層的停駐點已反白顯示。</span><span class="sxs-lookup"><span data-stu-id="6a53c-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="6a53c-108">![放射狀漸層中的漸層停駐點](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="6a53c-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a53c-109">本主題中的範例會使用預設的座標系統來設定控制點。</span><span class="sxs-lookup"><span data-stu-id="6a53c-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="6a53c-110">預設座標系統是相對於周框方塊：0表示周框方塊的0%，而1表示周框方塊的100%。</span><span class="sxs-lookup"><span data-stu-id="6a53c-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="6a53c-111">您可以藉由將 <xref:System.Windows.Media.GradientBrush.MappingMode%2A> 屬性設為 <xref:System.Windows.Media.BrushMappingMode.Absolute>的值，來變更此座標系統。</span><span class="sxs-lookup"><span data-stu-id="6a53c-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="6a53c-112">絕對座標系統不會相對於週框方塊。</span><span class="sxs-lookup"><span data-stu-id="6a53c-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="6a53c-113">值會直接在本機空間中解譯。</span><span class="sxs-lookup"><span data-stu-id="6a53c-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="6a53c-114">如需其他 <xref:System.Windows.Media.RadialGradientBrush> 範例，請參閱[筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。</span><span class="sxs-lookup"><span data-stu-id="6a53c-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="6a53c-115">如需漸層和其他類型之筆刷的詳細資訊，請參閱[使用純色和漸層繪製的色彩](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6a53c-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
