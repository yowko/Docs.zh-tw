---
title: 如何：繪製橢圓形或圓形
description: 瞭解如何在 Windows Presentation Foundation （WPF）中，使用外框粗細和內部色彩的選項繪製橢圓形或圓形。
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853558"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a>如何：繪製橢圓形或圓形
這個範例示範如何使用元素繪製橢圓形和圓形 <xref:System.Windows.Shapes.Ellipse> 。 若要繪製橢圓形，請建立 <xref:System.Windows.Shapes.Ellipse> 元素，並指定其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 。 使用其 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性來指定 <xref:System.Windows.Media.Brush> 用來繪製橢圓形內部的。 使用其 <xref:System.Windows.Shapes.Shape.Stroke%2A> 屬性來指定 <xref:System.Windows.Media.Brush> 用來繪製橢圓形外框的。 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性會指定橢圓形外框的粗細。  
  
 若要繪製圓形，請讓 <xref:System.Windows.FrameworkElement.Width%2A> 元素的和彼此 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Shapes.Ellipse> 相等。  
  
 下列範例會在中繪製四個 <xref:System.Windows.Shapes.Ellipse> 元素 <xref:System.Windows.Controls.Canvas> 。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 雖然此範例使用 <xref:System.Windows.Controls.Canvas> 來包含省略號，但是您可以使用橢圓形元素（以及所有其他圖形元素）搭配任何 <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Control> 支援非文字內容的或。  
  
 這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
