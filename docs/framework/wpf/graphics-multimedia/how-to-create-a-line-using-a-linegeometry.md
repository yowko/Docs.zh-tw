---
title: "如何：使用 LineGeometry 建立線條"
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
helpviewer_keywords: graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: acb2c3db2027f8a4e9594212d1f5af9ea1c8a43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="ac7a8-102">如何：使用 LineGeometry 建立線條</span><span class="sxs-lookup"><span data-stu-id="ac7a8-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="ac7a8-103">這個範例示範如何使用<xref:System.Windows.Media.LineGeometry>類別來說明一條線。</span><span class="sxs-lookup"><span data-stu-id="ac7a8-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="ac7a8-104">A<xref:System.Windows.Media.LineGeometry>由其開始和結束點定義。</span><span class="sxs-lookup"><span data-stu-id="ac7a8-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac7a8-105">範例</span><span class="sxs-lookup"><span data-stu-id="ac7a8-105">Example</span></span>  
 <span data-ttu-id="ac7a8-106">下列範例示範如何建立及呈現<xref:System.Windows.Media.LineGeometry>。</span><span class="sxs-lookup"><span data-stu-id="ac7a8-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="ac7a8-107">A<xref:System.Windows.Shapes.Path>元素用來呈現線條。</span><span class="sxs-lookup"><span data-stu-id="ac7a8-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="ac7a8-108">線條會不有任何區域中，因為<xref:System.Windows.Shapes.Path>物件的<xref:System.Windows.Shapes.Shape.Fill%2A>未指定，改為<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性可用。</span><span class="sxs-lookup"><span data-stu-id="ac7a8-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="ac7a8-109">![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="ac7a8-109">![A LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="ac7a8-110">從 (10,20) 繪製到 (100,130) 的 LineGeometry</span><span class="sxs-lookup"><span data-stu-id="ac7a8-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="ac7a8-111">其他簡單的幾何類別包含<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.EllipseGeometry>。</span><span class="sxs-lookup"><span data-stu-id="ac7a8-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="ac7a8-112">這些幾何，以及更複雜的也可以建立使用<xref:System.Windows.Media.PathGeometry>或<xref:System.Windows.Media.StreamGeometry>。</span><span class="sxs-lookup"><span data-stu-id="ac7a8-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="ac7a8-113">如需詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ac7a8-113">For more information, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac7a8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac7a8-114">See Also</span></span>  
 [<span data-ttu-id="ac7a8-115">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="ac7a8-115">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="ac7a8-116">建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="ac7a8-116">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="ac7a8-117">使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="ac7a8-117">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
