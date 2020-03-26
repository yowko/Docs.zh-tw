---
title: 如何：將透射材料應用於 3D 物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3D objects
- 3D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: bf32b41ec2410c01ad137ec0ca9311f7c2b70061
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112150"
---
# <a name="how-to-apply-emissive-material-to-a-3d-object"></a><span data-ttu-id="866e9-102">如何：將透射材料應用於 3D 物件</span><span class="sxs-lookup"><span data-stu-id="866e9-102">How to: Apply Emissive Material to a 3D Object</span></span>
<span data-ttu-id="866e9-103">下面的示例演示如何使用<xref:System.Windows.Media.Media3D.EmissiveMaterial>向等於 E 使材料畫筆顏色的現有材質添加顏色。</span><span class="sxs-lookup"><span data-stu-id="866e9-103">The following example shows how to use <xref:System.Windows.Media.Media3D.EmissiveMaterial> to add color to an existing Material equal to the color of the EmissiveMaterial's brush.</span></span> <span data-ttu-id="866e9-104">下面的代碼顯示<xref:System.Windows.Media.Media3D.DiffuseMaterial>並<xref:System.Windows.Media.Media3D.EmissiveMaterial>結合應用，以向 Diffuse 材料的外觀添加藍色。</span><span class="sxs-lookup"><span data-stu-id="866e9-104">The code below shows <xref:System.Windows.Media.Media3D.DiffuseMaterial> and <xref:System.Windows.Media.Media3D.EmissiveMaterial> applied in combination to add blue to the DiffuseMaterial's appearance.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 <span data-ttu-id="866e9-105">在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="866e9-105">In procedural code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="866e9-106">範例</span><span class="sxs-lookup"><span data-stu-id="866e9-106">Example</span></span>  
 <span data-ttu-id="866e9-107">以下代碼在 XAML 中顯示整個示例。</span><span class="sxs-lookup"><span data-stu-id="866e9-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="866e9-108">範例</span><span class="sxs-lookup"><span data-stu-id="866e9-108">Example</span></span>  
 <span data-ttu-id="866e9-109">下面是過程代碼中的全部示例。</span><span class="sxs-lookup"><span data-stu-id="866e9-109">Below is the entire sample in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="866e9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="866e9-110">See also</span></span>

- [<span data-ttu-id="866e9-111">創建 3D 場景</span><span class="sxs-lookup"><span data-stu-id="866e9-111">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="866e9-112">3D 圖形概述</span><span class="sxs-lookup"><span data-stu-id="866e9-112">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="866e9-113">在 3D 場景中設置材質屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="866e9-113">Animate Material Properties in a 3D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="866e9-114">將材質應用於 3D 物件的正面和背面</span><span class="sxs-lookup"><span data-stu-id="866e9-114">Apply Material to the Front and Back of a 3D Object</span></span>](how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
