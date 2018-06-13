---
title: 如何：建立立體場景
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: e3c2ea803961ca57606f8ea8bec21d50a38dbe1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559522"
---
# <a name="how-to-create-a-3-d-scene"></a><span data-ttu-id="e6314-102">如何：建立立體場景</span><span class="sxs-lookup"><span data-stu-id="e6314-102">How to: Create a 3-D Scene</span></span>
<span data-ttu-id="e6314-103">這個範例示範如何建立 3d 物件會像一般的工作表的已旋轉的紙張。</span><span class="sxs-lookup"><span data-stu-id="e6314-103">This example shows how to create a 3-D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="e6314-104">A<xref:System.Windows.Controls.Viewport3D>以及下列元件用來建立這個簡單的 3d 場景：</span><span class="sxs-lookup"><span data-stu-id="e6314-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3-D scene:</span></span>  
  
-   <span data-ttu-id="e6314-105">使用建立相機<xref:System.Windows.Media.Media3D.PerspectiveCamera>。</span><span class="sxs-lookup"><span data-stu-id="e6314-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="e6314-106">相機指定可檢視的 3d 場景哪個部分。</span><span class="sxs-lookup"><span data-stu-id="e6314-106">The camera specifies what part of the 3-D scene is viewable.</span></span>  
  
-   <span data-ttu-id="e6314-107">網狀結構是用來指定 3d 物件 （單張紙） 使用的圖形<xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>。</span><span class="sxs-lookup"><span data-stu-id="e6314-107">A mesh is created to specify the shape of 3-D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="e6314-108">材質指定物件 （在此範例中的線性漸層） 使用的介面上顯示<xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>屬性<xref:System.Windows.Media.Media3D.GeometryModel3D>。</span><span class="sxs-lookup"><span data-stu-id="e6314-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
-   <span data-ttu-id="e6314-109">物件使用平台建立光線<xref:System.Windows.Media.Media3D.DirectionalLight>。</span><span class="sxs-lookup"><span data-stu-id="e6314-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6314-110">範例</span><span class="sxs-lookup"><span data-stu-id="e6314-110">Example</span></span>  
 <span data-ttu-id="e6314-111">下列程式碼會示範如何在 XAML 中建立的 3d 場景。</span><span class="sxs-lookup"><span data-stu-id="e6314-111">The code below shows how to create a 3-D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="e6314-112">範例</span><span class="sxs-lookup"><span data-stu-id="e6314-112">Example</span></span>  
 <span data-ttu-id="e6314-113">下列程式碼會示範如何在程序程式碼中建立相同的 3d 場景。</span><span class="sxs-lookup"><span data-stu-id="e6314-113">The code below shows how to create the same 3-D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e6314-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6314-114">See Also</span></span>  
 [<span data-ttu-id="e6314-115">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="e6314-115">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
