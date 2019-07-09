---
title: 作法：對立體模型套用繪圖
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 8ac24fdf8d7e407e10764c17fcc12121aa5f51d7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662804"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="9c6f0-102">作法：對立體模型套用繪圖</span><span class="sxs-lookup"><span data-stu-id="9c6f0-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="9c6f0-103">此範例示範如何使用<xref:System.Windows.Media.DrawingBrush>做為<xref:System.Windows.Media.Media3D.Material>套用至 3d 模型。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>  
  
 <span data-ttu-id="9c6f0-104">下列程式碼定義<xref:System.Windows.Media.DrawingGroup>的內容<xref:System.Windows.Media.DrawingBrush>。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="9c6f0-105"><xref:System.Windows.Media.DrawingBrush>設定為<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>屬性<xref:System.Windows.Media.Media3D.DiffuseMaterial>套用至 3d 的平面。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>  
  
 <span data-ttu-id="9c6f0-106">**注意：** 它通常會定義複雜的物件和值，例如下面繪製為資源，可以重複使用，並簡化您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="9c6f0-107">請參閱[XAML 資源](../advanced/xaml-resources.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="9c6f0-108">範例</span><span class="sxs-lookup"><span data-stu-id="9c6f0-108">Example</span></span>  
 <span data-ttu-id="9c6f0-109">下列程式碼顯示整個範例。</span><span class="sxs-lookup"><span data-stu-id="9c6f0-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9c6f0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c6f0-110">See also</span></span>

- [<span data-ttu-id="9c6f0-111">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="9c6f0-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="9c6f0-112">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="9c6f0-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="9c6f0-113">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="9c6f0-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="9c6f0-114">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="9c6f0-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
