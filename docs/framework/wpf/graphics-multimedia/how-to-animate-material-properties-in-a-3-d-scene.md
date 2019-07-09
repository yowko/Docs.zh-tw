---
title: 作法：在立體場景中建立材質屬性的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3-D scenes
- animation [WPF], Material properties in 3-D scenes
- 3-D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: 8dfd7f01b87e2becfbcf57544ec4f8340cf8d5cc
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662544"
---
# <a name="how-to-animate-material-properties-in-a-3-d-scene"></a><span data-ttu-id="dc780-102">作法：在立體場景中建立材質屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="dc780-102">How to: Animate Material Properties in a 3-D Scene</span></span>
<span data-ttu-id="dc780-103">此範例示範如何建立動畫<xref:System.Windows.Media.Brush.Opacity%2A>屬性<xref:System.Windows.Media.Media3D.Material>套用至 3d 模型。</span><span class="sxs-lookup"><span data-stu-id="dc780-103">This example shows how to animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>  
  
 <span data-ttu-id="dc780-104">下列程式碼範例會定義<xref:System.Windows.Media.LinearGradientBrush>做為<xref:System.Windows.Media.Media3D.Material>套用至 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="dc780-104">The following code example defines the <xref:System.Windows.Media.LinearGradientBrush> used as the <xref:System.Windows.Media.Media3D.Material> applied to the 3D object.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <span data-ttu-id="dc780-105"><xref:System.Windows.Media.Brush.Opacity%2A>屬性的<xref:System.Windows.Media.LinearGradientBrush>以動畫顯示使用下列程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="dc780-105">The <xref:System.Windows.Media.Brush.Opacity%2A> property of this <xref:System.Windows.Media.LinearGradientBrush> is animated using the code example below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="dc780-106">範例</span><span class="sxs-lookup"><span data-stu-id="dc780-106">Example</span></span>  
 <span data-ttu-id="dc780-107">下列程式碼顯示整個範例。</span><span class="sxs-lookup"><span data-stu-id="dc780-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="dc780-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc780-108">See also</span></span>

- [<span data-ttu-id="dc780-109">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="dc780-109">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="dc780-110">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="dc780-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
