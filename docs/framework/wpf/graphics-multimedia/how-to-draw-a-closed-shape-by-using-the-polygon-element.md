---
title: HOW TO：使用 Polygon 項目繪製封閉的形狀
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 533c341e2fae528ec896bf38bafa13974af1d127
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360031"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a><span data-ttu-id="b5bc1-102">HOW TO：使用 Polygon 項目繪製封閉的形狀</span><span class="sxs-lookup"><span data-stu-id="b5bc1-102">How to: Draw a Closed Shape by Using the Polygon Element</span></span>
<span data-ttu-id="b5bc1-103">此範例示範如何使用來繪製封閉的形狀<xref:System.Windows.Shapes.Polygon>項目。</span><span class="sxs-lookup"><span data-stu-id="b5bc1-103">This example shows how to draw a closed shape by using the <xref:System.Windows.Shapes.Polygon> element.</span></span> <span data-ttu-id="b5bc1-104">若要繪製封閉的形狀，建立<xref:System.Windows.Shapes.Polygon>項目，並使用其<xref:System.Windows.Shapes.Polygon.Points%2A>屬性來指定圖形的頂點。</span><span class="sxs-lookup"><span data-stu-id="b5bc1-104">To draw a closed shape, create a <xref:System.Windows.Shapes.Polygon> element and use its <xref:System.Windows.Shapes.Polygon.Points%2A> property to specify the vertices of a shape.</span></span> <span data-ttu-id="b5bc1-105">自動繪製線條連接的第一個和最後一個點。</span><span class="sxs-lookup"><span data-stu-id="b5bc1-105">A line is automatically drawn that connects the first and last points.</span></span> <span data-ttu-id="b5bc1-106">最後，指定<xref:System.Windows.Shapes.Shape.Fill%2A>、 <xref:System.Windows.Shapes.Shape.Stroke%2A>，或兩者。</span><span class="sxs-lookup"><span data-stu-id="b5bc1-106">Finally, specify a <xref:System.Windows.Shapes.Shape.Fill%2A>, a <xref:System.Windows.Shapes.Shape.Stroke%2A>, or both.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5bc1-107">範例</span><span class="sxs-lookup"><span data-stu-id="b5bc1-107">Example</span></span>  
 <span data-ttu-id="b5bc1-108">在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，有效的語法，點是以逗號分隔的 x 和 y 座標組的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="b5bc1-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 <span data-ttu-id="b5bc1-109">雖然此範例會使用<xref:System.Windows.Controls.Canvas>包含多邊形，您可以使用 polygon 項目 （和其他圖形元素） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。</span><span class="sxs-lookup"><span data-stu-id="b5bc1-109">Although the example uses a <xref:System.Windows.Controls.Canvas> to contain the polygons, you can use polygon elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="b5bc1-110">這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="b5bc1-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>
