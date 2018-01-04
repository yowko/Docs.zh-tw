---
title: "如何：套用繪圖至立體模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7437f4c8279d80d7287565a28337a3cd647e239
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="c1d13-102">如何：套用繪圖至立體模型</span><span class="sxs-lookup"><span data-stu-id="c1d13-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="c1d13-103">這個範例示範如何使用<xref:System.Windows.Media.DrawingBrush>為<xref:System.Windows.Media.Media3D.Material>套用至[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型。</span><span class="sxs-lookup"><span data-stu-id="c1d13-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="c1d13-104">下列程式碼定義<xref:System.Windows.Media.DrawingGroup>做內容<xref:System.Windows.Media.DrawingBrush>。</span><span class="sxs-lookup"><span data-stu-id="c1d13-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="c1d13-105"><xref:System.Windows.Media.DrawingBrush>設為<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>屬性<xref:System.Windows.Media.Media3D.DiffuseMaterial>套用至[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]平面。</span><span class="sxs-lookup"><span data-stu-id="c1d13-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="c1d13-106">**注意：**它通常會定義為資源，可以重複使用，並簡化您的程式碼的複雜物件及類似下方繪製的值。</span><span class="sxs-lookup"><span data-stu-id="c1d13-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="c1d13-107">請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c1d13-107">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="c1d13-108">範例</span><span class="sxs-lookup"><span data-stu-id="c1d13-108">Example</span></span>  
 <span data-ttu-id="c1d13-109">下列程式碼顯示完整的範例。</span><span class="sxs-lookup"><span data-stu-id="c1d13-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c1d13-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="c1d13-110">See Also</span></span>  
 [<span data-ttu-id="c1d13-111">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="c1d13-111">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="c1d13-112">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="c1d13-112">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="c1d13-113">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="c1d13-113">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="c1d13-114">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="c1d13-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
