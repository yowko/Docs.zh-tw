---
title: "如何：修改線條或線段結尾的端點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d2cd55de403b766344749259068ccd313558f89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="9946d-102">如何：修改線條或線段結尾的端點</span><span class="sxs-lookup"><span data-stu-id="9946d-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="9946d-103">這個範例示範如何修改開頭或結尾開啟圖形<xref:System.Windows.Shapes.Shape>項目。</span><span class="sxs-lookup"><span data-stu-id="9946d-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="9946d-104">若要變更的開啟開頭 cap <xref:System.Windows.Shapes.Shape>，使用其<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9946d-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="9946d-105">若要變更已開啟的結尾處的 cap <xref:System.Windows.Shapes.Shape>，使用其<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9946d-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="9946d-106">若要檢視可用的線條端點，請參閱<xref:System.Windows.Media.PenLineCap>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="9946d-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9946d-107">這個屬性只會影響在圖案，例如<xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Polyline>，或開啟<xref:System.Windows.Shapes.Path>項目。</span><span class="sxs-lookup"><span data-stu-id="9946d-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="9946d-108">下列範例會繪製四個<xref:System.Windows.Shapes.Polyline>項目，並使用每個端點上的一組不同的圖形。</span><span class="sxs-lookup"><span data-stu-id="9946d-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9946d-109">範例</span><span class="sxs-lookup"><span data-stu-id="9946d-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="9946d-110">這個範例是較大範例的一部分如需完整範例，請參閱[圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="9946d-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9946d-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="9946d-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
