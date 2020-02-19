---
title: 如何：繪製橢圓形或圓形
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 5f17615da4907cba6e25b68f2f934602c2f8a390
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452918"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>如何：繪製橢圓形或圓形
這個範例示範如何使用 <xref:System.Windows.Shapes.Ellipse> 元素繪製橢圓形和圓形。 若要繪製橢圓形，請建立 <xref:System.Windows.Shapes.Ellipse> 元素，並指定其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A>。 使用其 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性來指定用來繪製橢圓形內部的 <xref:System.Windows.Media.Brush>。 使用其 <xref:System.Windows.Shapes.Shape.Stroke%2A> 屬性來指定用來繪製橢圓形外框的 <xref:System.Windows.Media.Brush>。 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性會指定橢圓形外框的粗細。  
  
 若要繪製圓形，請將 <xref:System.Windows.Shapes.Ellipse> 元素的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 相等。  
  
 下列範例會在 <xref:System.Windows.Controls.Canvas>中繪製四個 <xref:System.Windows.Shapes.Ellipse> 元素。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 雖然此範例使用 <xref:System.Windows.Controls.Canvas> 來包含省略號，但是您可以使用橢圓形元素（以及所有其他圖形元素）搭配任何支援非文字內容的 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.Control>。  
  
 這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
