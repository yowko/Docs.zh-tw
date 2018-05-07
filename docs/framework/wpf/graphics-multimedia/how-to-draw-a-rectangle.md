---
title: 如何：繪製矩形
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 100f1a8062628e892e9a71b988bb2a8754ea6bad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-rectangle"></a>如何：繪製矩形
這個範例示範如何使用繪製矩形<xref:System.Windows.Shapes.Rectangle>項目。  
  
 若要繪製矩形，建立<xref:System.Windows.Shapes.Rectangle>項目，並指定其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>。 若要繪製的矩形內部，將其<xref:System.Windows.Shapes.Shape.Fill%2A>。 若要讓矩形外框，使用其<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性。  
  
 若要將矩形的圓角中，指定選擇性<xref:System.Windows.Shapes.Rectangle.RadiusX%2A>和<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>屬性。 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>和<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>設定 x 軸和 y 軸半徑，用來決定矩形的圓橢圓形的屬性。  
  
 在下列範例中，兩個<xref:System.Windows.Shapes.Rectangle>項目會繪製<xref:System.Windows.Controls.Canvas>。 第一個矩形<xref:System.Windows.Media.Brushes.Blue%2A>內部。 第二個矩形<xref:System.Windows.Media.Brushes.Blue%2A>內部，<xref:System.Windows.Media.Brushes.Black%2A>大綱，以及圓的角。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 雖然這個範例會使用<xref:System.Windows.Controls.Canvas>包含矩形，您可以使用矩形項目 （以及所有其他圖形項目） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。 事實上，矩形會特別有用的部分提供背景<xref:System.Windows.Controls.Grid>面板。 如需範例，請參閱[資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)。  
  
 這個範例是較大範例的一部分如需完整範例，請參閱[圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Shapes.Rectangle>  
 [圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)
