---
title: 如何：修改線條或線段結尾的端點
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: aef85383a10629eb42f51ea86305636fd90600cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504072"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="db9f3-102">如何：修改線條或線段結尾的端點</span><span class="sxs-lookup"><span data-stu-id="db9f3-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="db9f3-103">此範例示範如何修改的圖形的開頭或結尾開啟<xref:System.Windows.Shapes.Shape>項目。</span><span class="sxs-lookup"><span data-stu-id="db9f3-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="db9f3-104">若要變更的已開啟的開頭上限<xref:System.Windows.Shapes.Shape>，使用其<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="db9f3-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="db9f3-105">若要變更的已開啟的結尾上限<xref:System.Windows.Shapes.Shape>，使用其<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="db9f3-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="db9f3-106">若要檢視可用的線條端點，請參閱<xref:System.Windows.Media.PenLineCap>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="db9f3-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db9f3-107">這個屬性只會影響開放的圖形，例如<xref:System.Windows.Shapes.Line>，則<xref:System.Windows.Shapes.Polyline>，或開啟<xref:System.Windows.Shapes.Path>項目。</span><span class="sxs-lookup"><span data-stu-id="db9f3-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="db9f3-108">下列範例會繪製四個<xref:System.Windows.Shapes.Polyline>項目，並使用一組不同的圖形的每個端點。</span><span class="sxs-lookup"><span data-stu-id="db9f3-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db9f3-109">範例</span><span class="sxs-lookup"><span data-stu-id="db9f3-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="db9f3-110">這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="db9f3-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db9f3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db9f3-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
