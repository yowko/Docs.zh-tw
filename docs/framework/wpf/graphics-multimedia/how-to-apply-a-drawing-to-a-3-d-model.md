---
title: HOW TO：套用繪圖至立體模型
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 07811f8c0326827ed90484ce12632589b2f6fc82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611237"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="00ac6-102">HOW TO：套用繪圖至立體模型</span><span class="sxs-lookup"><span data-stu-id="00ac6-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="00ac6-103">此範例示範如何使用<xref:System.Windows.Media.DrawingBrush>作為<xref:System.Windows.Media.Media3D.Material>套用至[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型。</span><span class="sxs-lookup"><span data-stu-id="00ac6-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="00ac6-104">下列程式碼定義<xref:System.Windows.Media.DrawingGroup>的內容<xref:System.Windows.Media.DrawingBrush>。</span><span class="sxs-lookup"><span data-stu-id="00ac6-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="00ac6-105"><xref:System.Windows.Media.DrawingBrush>設定為<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>屬性<xref:System.Windows.Media.Media3D.DiffuseMaterial>套用至[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]平面。</span><span class="sxs-lookup"><span data-stu-id="00ac6-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="00ac6-106">**注意：** 它通常會定義複雜的物件和值，例如下面繪製為資源，可以重複使用，並簡化您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="00ac6-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="00ac6-107">請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="00ac6-107">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="00ac6-108">範例</span><span class="sxs-lookup"><span data-stu-id="00ac6-108">Example</span></span>  
 <span data-ttu-id="00ac6-109">下列程式碼顯示整個範例。</span><span class="sxs-lookup"><span data-stu-id="00ac6-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="00ac6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00ac6-110">See also</span></span>
- [<span data-ttu-id="00ac6-111">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="00ac6-111">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [<span data-ttu-id="00ac6-112">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="00ac6-112">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="00ac6-113">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="00ac6-113">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="00ac6-114">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="00ac6-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
