---
title: HOW TO：對立體物件的前後套用材質
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 1d3f6a0622b5e0ccccf14af99782bb78dfe87ccb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698952"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a><span data-ttu-id="2ddb1-102">HOW TO：對立體物件的前後套用材質</span><span class="sxs-lookup"><span data-stu-id="2ddb1-102">How to: Apply Material to the Front and Back of a 3-D Object</span></span>
<span data-ttu-id="2ddb1-103">下列範例示範如何套用<xref:System.Windows.Media.Media3D.Material>前面和背面的 3d 物件，並建立要顯示物件的兩邊的物件的動畫。</span><span class="sxs-lookup"><span data-stu-id="2ddb1-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3-D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="2ddb1-104"><xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>可用來套用紅色<xref:System.Windows.Media.Brush>至物件的正面和<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>可用來套用藍色<xref:System.Windows.Media.Brush>到後端的物件。</span><span class="sxs-lookup"><span data-stu-id="2ddb1-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="2ddb1-105">下列程式碼顯示將材質套用至物件：</span><span class="sxs-lookup"><span data-stu-id="2ddb1-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="2ddb1-106">範例</span><span class="sxs-lookup"><span data-stu-id="2ddb1-106">Example</span></span>  
 <span data-ttu-id="2ddb1-107">下列程式碼顯示整個範例。</span><span class="sxs-lookup"><span data-stu-id="2ddb1-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2ddb1-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ddb1-108">See also</span></span>

- [<span data-ttu-id="2ddb1-109">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="2ddb1-109">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="2ddb1-110">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="2ddb1-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="2ddb1-111">在立體場景中建立材質屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="2ddb1-111">Animate Material Properties in a 3-D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="2ddb1-112">將射出材質套用至立體物件</span><span class="sxs-lookup"><span data-stu-id="2ddb1-112">Apply Emissive Material to a 3-D Object</span></span>](how-to-apply-emissive-material-to-a-3-d-object.md)
