---
title: HOW TO：繪製線條
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: 54152b6b68dd453c565afa2ffb23edfe8132a441
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629016"
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="d613f-102">HOW TO：繪製線條</span><span class="sxs-lookup"><span data-stu-id="d613f-102">How to: Draw a Line</span></span>
<span data-ttu-id="d613f-103">此範例將示範如何藉由繪製線條<xref:System.Windows.Shapes.Line>項目。</span><span class="sxs-lookup"><span data-stu-id="d613f-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="d613f-104">若要繪製一條線，請建立<xref:System.Windows.Shapes.Line>項目。</span><span class="sxs-lookup"><span data-stu-id="d613f-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="d613f-105">使用其<xref:System.Windows.Shapes.Line.X1%2A>並<xref:System.Windows.Shapes.Line.Y1%2A>屬性來設定它的起點，並使用其<xref:System.Windows.Shapes.Line.X2%2A>和<xref:System.Windows.Shapes.Line.Y2%2A>屬性來設定其端點。</span><span class="sxs-lookup"><span data-stu-id="d613f-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="d613f-106">最後，設定其<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>因為沒有筆觸線條是不可見。</span><span class="sxs-lookup"><span data-stu-id="d613f-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="d613f-107">設定<xref:System.Windows.Shapes.Shape.Fill%2A>一行的項目會有任何作用，由於線條沒有任何內部。</span><span class="sxs-lookup"><span data-stu-id="d613f-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="d613f-108">下列範例會繪製內的三行<xref:System.Windows.Controls.Canvas>項目。</span><span class="sxs-lookup"><span data-stu-id="d613f-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d613f-109">範例</span><span class="sxs-lookup"><span data-stu-id="d613f-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="d613f-110">這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="d613f-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d613f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d613f-111">See also</span></span>
- <xref:System.Windows.Shapes.Line>
- [<span data-ttu-id="d613f-112">圖形元素範例</span><span class="sxs-lookup"><span data-stu-id="d613f-112">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
