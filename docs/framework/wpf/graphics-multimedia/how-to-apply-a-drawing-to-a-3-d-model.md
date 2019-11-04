---
title: 如何：套用繪圖至立體模型
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 311a3ac1d9fa219a3a365d506d9d0c3e8b6bc229
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459363"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="4640b-102">如何：套用繪圖至立體模型</span><span class="sxs-lookup"><span data-stu-id="4640b-102">How to: Apply a Drawing to a 3-D Model</span></span>

<span data-ttu-id="4640b-103">這個範例示範如何使用 <xref:System.Windows.Media.DrawingBrush> 做為 <xref:System.Windows.Media.Media3D.Material> 套用至3D 模型的方式。</span><span class="sxs-lookup"><span data-stu-id="4640b-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>

<span data-ttu-id="4640b-104">下列程式碼會將 <xref:System.Windows.Media.DrawingGroup> 定義為 <xref:System.Windows.Media.DrawingBrush>的內容。</span><span class="sxs-lookup"><span data-stu-id="4640b-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="4640b-105"><xref:System.Windows.Media.DrawingBrush> 會設定為套用至立體平面之 <xref:System.Windows.Media.Media3D.DiffuseMaterial> 的 <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4640b-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="4640b-106">您通常會想要定義複雜的物件和值，如下圖所示，做為可重複使用並簡化程式碼的資源。</span><span class="sxs-lookup"><span data-stu-id="4640b-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="4640b-107">如需詳細資訊，請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="4640b-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="4640b-108">範例</span><span class="sxs-lookup"><span data-stu-id="4640b-108">Example</span></span>

<span data-ttu-id="4640b-109">下列程式碼顯示整個範例。</span><span class="sxs-lookup"><span data-stu-id="4640b-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="4640b-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="4640b-110">See also</span></span>

- [<span data-ttu-id="4640b-111">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="4640b-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="4640b-112">建立立體場景</span><span class="sxs-lookup"><span data-stu-id="4640b-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="4640b-113">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="4640b-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="4640b-114">立體圖形概觀</span><span class="sxs-lookup"><span data-stu-id="4640b-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
