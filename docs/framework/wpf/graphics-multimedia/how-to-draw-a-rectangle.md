---
title: 如何：繪製矩形
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452931"
---
# <a name="how-to-draw-a-rectangle"></a>如何：繪製矩形
這個範例會示範如何使用 <xref:System.Windows.Shapes.Rectangle> 元素繪製矩形。  
  
 若要繪製矩形，請建立 <xref:System.Windows.Shapes.Rectangle> 元素，並指定其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A>。 若要在矩形內繪製，請設定其 <xref:System.Windows.Shapes.Shape.Fill%2A>。 若要為矩形提供外框，請使用其 <xref:System.Windows.Shapes.Shape.Stroke%2A> 並 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性。  
  
 若要提供矩形圓角，請指定選擇性的 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>，並 <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 屬性。 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> 和 <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 屬性會設定橢圓形的 X 軸和 y 軸半徑，用來舍入矩形的圓角。  
  
 在下列範例中，會在 <xref:System.Windows.Controls.Canvas>中繪製兩個 <xref:System.Windows.Shapes.Rectangle> 元素。 第一個矩形具有 <xref:System.Windows.Media.Brushes.Blue%2A> 內部。 第二個矩形具有 <xref:System.Windows.Media.Brushes.Blue%2A> 內部、<xref:System.Windows.Media.Brushes.Black%2A> 外框和圓角。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 雖然此範例使用包含矩形的 <xref:System.Windows.Controls.Canvas>，但您可以使用矩形元素（以及所有其他圖形元素）搭配任何支援非文字內容的 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.Control>。 事實上，矩形特別適合用來提供部分 <xref:System.Windows.Controls.Grid> 面板的背景。 如需範例，請參閱[資料表總覽](../advanced/table-overview.md)。  
  
 這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Shapes.Rectangle>
- [圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [資料表概觀](../advanced/table-overview.md)
