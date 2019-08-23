---
title: 作法：使用聚合線條元素繪製聚合線條
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934966"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>作法：使用聚合線條元素繪製聚合線條
這個範例示範如何使用<xref:System.Windows.Shapes.Polyline>專案, 繪製一系列連接線條的折線。  
  
 若要繪製一條折線, <xref:System.Windows.Shapes.Polyline>請建立一個專案<xref:System.Windows.Shapes.Polyline.Points%2A> , 並使用其屬性來指定圖形頂點。 最後, 使用<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性來描述聚合線條外框, 因為不會顯示沒有筆觸的線條。  
  
> [!NOTE]
> 因為專案不是封閉圖形<xref:System.Windows.Shapes.Shape.Fill%2A> , 所以即使您故意關閉圖形大綱, 屬性也不會有任何作用。 <xref:System.Windows.Shapes.Polyline> 若要使用來建立已關閉<xref:System.Windows.Shapes.Shape.Fill%2A>的圖形, <xref:System.Windows.Shapes.Polygon>請使用元素。  
  
 下列範例會在<xref:System.Windows.Shapes.Polyline> <xref:System.Windows.Controls.Canvas>內繪製兩個元素。  
  
## <a name="example"></a>範例  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中, 點的有效語法是以空格分隔的逗號分隔 x 和 y 座標配對清單。  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 雖然此範例使用<xref:System.Windows.Controls.Canvas>來包含多線條, 但您可以使用折線元素 (以及所有其他圖形元素) 搭配任何<xref:System.Windows.Controls.Panel>支援非<xref:System.Windows.Controls.Control>文字內容的或。  
  
 這個範例是較大範例的一部分;如需完整範例, 請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
