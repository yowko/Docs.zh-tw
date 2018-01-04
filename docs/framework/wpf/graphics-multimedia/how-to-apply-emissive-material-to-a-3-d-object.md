---
title: "如何：將射出材質套用至立體物件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3-D objects
- 3-D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c62436adc974df4b74cf1548abc09ac1f396fc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a><span data-ttu-id="ce5e1-102">如何：將射出材質套用至立體物件</span><span class="sxs-lookup"><span data-stu-id="ce5e1-102">How to: Apply Emissive Material to a 3-D Object</span></span>
<span data-ttu-id="ce5e1-103">下列範例示範如何使用<xref:System.Windows.Media.Media3D.EmissiveMaterial>將色彩加入至現有的材料等於 EmissiveMaterial 的筆刷的色彩。</span><span class="sxs-lookup"><span data-stu-id="ce5e1-103">The following example shows how to use <xref:System.Windows.Media.Media3D.EmissiveMaterial> to add color to an existing Material equal to the color of the EmissiveMaterial's brush.</span></span> <span data-ttu-id="ce5e1-104">程式碼所示<xref:System.Windows.Media.Media3D.DiffuseMaterial>和<xref:System.Windows.Media.Media3D.EmissiveMaterial>藍色加入 DiffuseMaterial 外觀的組合中套用。</span><span class="sxs-lookup"><span data-stu-id="ce5e1-104">The code below shows <xref:System.Windows.Media.Media3D.DiffuseMaterial> and <xref:System.Windows.Media.Media3D.EmissiveMaterial> applied in combination to add blue to the DiffuseMaterial's appearance.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 <span data-ttu-id="ce5e1-105">在程序的程式碼：</span><span class="sxs-lookup"><span data-stu-id="ce5e1-105">In procedural code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="ce5e1-106">範例</span><span class="sxs-lookup"><span data-stu-id="ce5e1-106">Example</span></span>  
 <span data-ttu-id="ce5e1-107">下列程式碼會顯示 XAML 中的完整範例。</span><span class="sxs-lookup"><span data-stu-id="ce5e1-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="ce5e1-108">範例</span><span class="sxs-lookup"><span data-stu-id="ce5e1-108">Example</span></span>  
 <span data-ttu-id="ce5e1-109">以下是完整的範例程序性程式碼中。</span><span class="sxs-lookup"><span data-stu-id="ce5e1-109">Below is the entire sample in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ce5e1-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce5e1-110">See Also</span></span>  
 [<span data-ttu-id="ce5e1-111">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="ce5e1-111">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="ce5e1-112">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="ce5e1-112">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="ce5e1-113">在立體場景中建立材質屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="ce5e1-113">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [<span data-ttu-id="ce5e1-114">對立體物件的前後套用材質</span><span class="sxs-lookup"><span data-stu-id="ce5e1-114">Apply Material to the Front and Back of a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
