---
title: 如何：使用 Polyline 項目繪製聚合線
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 6698141bcaa3b0fd5f5b9cf66bcab1be1f4ea2f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452957"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>如何：使用 Polyline 項目繪製聚合線
這個範例會示範如何使用 <xref:System.Windows.Shapes.Polyline> 元素繪製一系列連接線條的「折線」。  
  
 若要繪製一個折線，請建立一個 <xref:System.Windows.Shapes.Polyline> 專案，並使用其 <xref:System.Windows.Shapes.Polyline.Points%2A> 屬性來指定圖形頂點。 最後，使用 [<xref:System.Windows.Shapes.Shape.Stroke%2A>] 和 [<xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性] 來描述 [折線外框]，因為不會顯示沒有筆觸的線條。  
  
> [!NOTE]
> 因為 <xref:System.Windows.Shapes.Polyline> 元素不是封閉圖形，所以即使您故意關閉圖形大綱，<xref:System.Windows.Shapes.Shape.Fill%2A> 屬性也沒有任何作用。 若要建立具有 <xref:System.Windows.Shapes.Shape.Fill%2A>的封閉圖形，請使用 <xref:System.Windows.Shapes.Polygon> 元素。  
  
 下列範例會在 <xref:System.Windows.Controls.Canvas>內繪製兩個 <xref:System.Windows.Shapes.Polyline> 元素。  
  
## <a name="example"></a>範例  
 在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，點的有效語法是以空格分隔的逗號分隔 x 和 y 座標配對清單。  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 雖然此範例會使用 <xref:System.Windows.Controls.Canvas> 來包含多線條，但您可以搭配任何支援非文字內容的 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.Control>，使用折線元素（以及所有其他圖形元素）。  
  
 這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
