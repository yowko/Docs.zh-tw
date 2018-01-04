---
title: "如何：建立複合圖案"
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
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ecb4ecdc5c83cbb6f2b4faee9cb3654939bd346
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="fe5f9-102">如何：建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="fe5f9-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="fe5f9-103">這個範例示範如何建立使用複合圖形<xref:System.Windows.Media.Geometry>物件，並顯示它們使用<xref:System.Windows.Shapes.Path>項目。</span><span class="sxs-lookup"><span data-stu-id="fe5f9-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="fe5f9-104">在下列範例中， <xref:System.Windows.Media.LineGeometry>， <xref:System.Windows.Media.EllipseGeometry>，和<xref:System.Windows.Media.RectangleGeometry>搭配<xref:System.Windows.Media.GeometryGroup>建立複合的圖形。</span><span class="sxs-lookup"><span data-stu-id="fe5f9-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="fe5f9-105">使用再繪製幾何<xref:System.Windows.Shapes.Path>項目。</span><span class="sxs-lookup"><span data-stu-id="fe5f9-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe5f9-106">範例</span><span class="sxs-lookup"><span data-stu-id="fe5f9-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="fe5f9-107">下圖顯示上一個範例中所建立的圖案。</span><span class="sxs-lookup"><span data-stu-id="fe5f9-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="fe5f9-108">![使用 GeometryGroup 建立的複合幾何](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="fe5f9-108">![A composite geometry created using a GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="fe5f9-109">複合幾何</span><span class="sxs-lookup"><span data-stu-id="fe5f9-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="fe5f9-110">更複雜的圖形，例如多邊形和圖形的曲線線段，可能會建立使用<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="fe5f9-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="fe5f9-111">如需範例示範如何建立使用圖形<xref:System.Windows.Media.PathGeometry>，請參閱[建立圖形使用 PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)。</span><span class="sxs-lookup"><span data-stu-id="fe5f9-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="fe5f9-112">雖然這個範例會呈現圖形以螢幕使用<xref:System.Windows.Shapes.Path>項目，<xref:System.Windows.Media.Geometry>物件可能也可用來說明的內容<xref:System.Windows.Media.GeometryDrawing>或<xref:System.Windows.Media.DrawingContext>。</span><span class="sxs-lookup"><span data-stu-id="fe5f9-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="fe5f9-113">它們也可用來裁剪及點擊測試。</span><span class="sxs-lookup"><span data-stu-id="fe5f9-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="fe5f9-114">這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989)。</span><span class="sxs-lookup"><span data-stu-id="fe5f9-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>
