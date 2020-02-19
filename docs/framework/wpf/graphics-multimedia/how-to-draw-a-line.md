---
title: 如何：繪製線條
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a803c1be01086ca8911ef4cc33bd67697239e2c0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452944"
---
# <a name="how-to-draw-a-line"></a>如何：繪製線條
這個範例會示範如何使用 <xref:System.Windows.Shapes.Line> 元素繪製線條。  
  
 若要繪製線條，請建立 <xref:System.Windows.Shapes.Line> 元素。 使用其 <xref:System.Windows.Shapes.Line.X1%2A> 和 <xref:System.Windows.Shapes.Line.Y1%2A> 屬性來設定其起始點;和會使用其 <xref:System.Windows.Shapes.Line.X2%2A> 和 <xref:System.Windows.Shapes.Line.Y2%2A> 屬性來設定其結束點。 最後，設定它的 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>，因為不會隱藏沒有筆觸的線條。  
  
 設定線條的 <xref:System.Windows.Shapes.Shape.Fill%2A> 專案不會有任何作用，因為線條沒有內部。  
  
 下列範例會在 <xref:System.Windows.Controls.Canvas> 元素內繪製三行。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Shapes.Line>
- [圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
