---
title: HOW TO：對立體物件套用放射材質
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3-D objects
- 3-D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: b898148fa07950e3ad1eddcaf9206f7d6a837241
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698962"
---
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a><span data-ttu-id="76e3a-102">HOW TO：對立體物件套用放射材質</span><span class="sxs-lookup"><span data-stu-id="76e3a-102">How to: Apply Emissive Material to a 3-D Object</span></span>
<span data-ttu-id="76e3a-103">下列範例示範如何使用<xref:System.Windows.Media.Media3D.EmissiveMaterial>將色彩加入至現有的材料等於 EmissiveMaterial 的筆刷的色彩。</span><span class="sxs-lookup"><span data-stu-id="76e3a-103">The following example shows how to use <xref:System.Windows.Media.Media3D.EmissiveMaterial> to add color to an existing Material equal to the color of the EmissiveMaterial's brush.</span></span> <span data-ttu-id="76e3a-104">以下顯示的程式碼<xref:System.Windows.Media.Media3D.DiffuseMaterial>和<xref:System.Windows.Media.Media3D.EmissiveMaterial>套用結合藍色加入 diffusematerial 之後的外觀。</span><span class="sxs-lookup"><span data-stu-id="76e3a-104">The code below shows <xref:System.Windows.Media.Media3D.DiffuseMaterial> and <xref:System.Windows.Media.Media3D.EmissiveMaterial> applied in combination to add blue to the DiffuseMaterial's appearance.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 <span data-ttu-id="76e3a-105">程序的程式碼：</span><span class="sxs-lookup"><span data-stu-id="76e3a-105">In procedural code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="76e3a-106">範例</span><span class="sxs-lookup"><span data-stu-id="76e3a-106">Example</span></span>  
 <span data-ttu-id="76e3a-107">下列程式碼會顯示在 XAML 中的完整範例。</span><span class="sxs-lookup"><span data-stu-id="76e3a-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="76e3a-108">範例</span><span class="sxs-lookup"><span data-stu-id="76e3a-108">Example</span></span>  
 <span data-ttu-id="76e3a-109">以下是完整的範例程序程式碼。</span><span class="sxs-lookup"><span data-stu-id="76e3a-109">Below is the entire sample in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="76e3a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76e3a-110">See also</span></span>

- [<span data-ttu-id="76e3a-111">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="76e3a-111">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="76e3a-112">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="76e3a-112">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="76e3a-113">在立體場景中建立材質屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="76e3a-113">Animate Material Properties in a 3-D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="76e3a-114">對立體物件的前後套用材質</span><span class="sxs-lookup"><span data-stu-id="76e3a-114">Apply Material to the Front and Back of a 3-D Object</span></span>](how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
