---
title: HOW TO：修改線條或線段結尾的端點
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916124"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="82fd9-102">HOW TO：修改線條或線段結尾的端點</span><span class="sxs-lookup"><span data-stu-id="82fd9-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="82fd9-103">這個範例會示範如何在開啟<xref:System.Windows.Shapes.Shape>專案的開頭或結尾修改圖形。</span><span class="sxs-lookup"><span data-stu-id="82fd9-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="82fd9-104">若要在開啟<xref:System.Windows.Shapes.Shape>的開頭變更端點, 請使用其<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="82fd9-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="82fd9-105">若要變更已開啟<xref:System.Windows.Shapes.Shape>結尾的端點, 請使用其<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="82fd9-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="82fd9-106">若要查看可用的行首, 請<xref:System.Windows.Media.PenLineCap>參閱列舉。</span><span class="sxs-lookup"><span data-stu-id="82fd9-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82fd9-107">這個屬性只會影響開啟的<xref:System.Windows.Shapes.Line>圖形, 例如<xref:System.Windows.Shapes.Polyline>、或 open <xref:System.Windows.Shapes.Path>元素。</span><span class="sxs-lookup"><span data-stu-id="82fd9-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="82fd9-108">下列範例會繪製四<xref:System.Windows.Shapes.Polyline>個元素, 並在每個專案的兩端使用一組不同的圖形。</span><span class="sxs-lookup"><span data-stu-id="82fd9-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82fd9-109">範例</span><span class="sxs-lookup"><span data-stu-id="82fd9-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="82fd9-110">這個範例是較大範例的一部分;如需完整範例, 請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="82fd9-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82fd9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82fd9-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
