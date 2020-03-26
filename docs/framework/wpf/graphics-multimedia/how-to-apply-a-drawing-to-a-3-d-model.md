---
title: 如何：將繪圖應用於 3D 模型
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112176"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a><span data-ttu-id="6e21a-102">如何：將繪圖應用於 3D 模型</span><span class="sxs-lookup"><span data-stu-id="6e21a-102">How to: Apply a Drawing to a 3D Model</span></span>

<span data-ttu-id="6e21a-103">此示例演示如何將<xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.Material></span><span class="sxs-lookup"><span data-stu-id="6e21a-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3D model.</span></span>

<span data-ttu-id="6e21a-104">以下代碼將 定義為<xref:System.Windows.Media.DrawingGroup>的內容。 <xref:System.Windows.Media.DrawingBrush></span><span class="sxs-lookup"><span data-stu-id="6e21a-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="6e21a-105"><xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>設置為<xref:System.Windows.Media.Media3D.DiffuseMaterial>應用於 3D 平面的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e21a-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="6e21a-106">通常，最好將複雜的物件和值（如下圖）定義為可以重用和簡化代碼的資源。</span><span class="sxs-lookup"><span data-stu-id="6e21a-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="6e21a-107">有關詳細資訊，請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="6e21a-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="6e21a-108">範例</span><span class="sxs-lookup"><span data-stu-id="6e21a-108">Example</span></span>

<span data-ttu-id="6e21a-109">以下代碼顯示整個示例。</span><span class="sxs-lookup"><span data-stu-id="6e21a-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="6e21a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e21a-110">See also</span></span>

- [<span data-ttu-id="6e21a-111">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="6e21a-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="6e21a-112">創建 3D 場景</span><span class="sxs-lookup"><span data-stu-id="6e21a-112">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="6e21a-113">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="6e21a-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="6e21a-114">3D 圖形概述</span><span class="sxs-lookup"><span data-stu-id="6e21a-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
