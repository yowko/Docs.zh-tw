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
ms.openlocfilehash: d065d3cead1ed9746a9615ce2bb6d3ec4cbd614d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855426"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>如何：使用 Polyline 項目繪製聚合線
此範例示範如何繪製聚合線，也就是一系列連接的直線，使用<xref:System.Windows.Shapes.Polyline>項目。  
  
 若要繪製聚合線，請建立<xref:System.Windows.Shapes.Polyline>項目，並使用其<xref:System.Windows.Shapes.Polyline.Points%2A>屬性來指定圖形的頂點。 最後，使用<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>來描述聚合線條的屬性說明，因為沒有筆觸線條是不可見。  
  
> [!NOTE]
>  因為<xref:System.Windows.Shapes.Polyline>項目不是封閉的形狀，<xref:System.Windows.Shapes.Shape.Fill%2A>屬性有任何作用，即使您刻意關閉圖形外框。 若要建立一個封閉的形狀，與<xref:System.Windows.Shapes.Shape.Fill%2A>，使用<xref:System.Windows.Shapes.Polygon>項目。  
  
 下列範例會繪製兩個<xref:System.Windows.Shapes.Polyline>內的項目<xref:System.Windows.Controls.Canvas>。  
  
## <a name="example"></a>範例  
 在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，有效的語法，點是以逗號分隔的 x 和 y 座標組的逗號分隔清單。  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 雖然此範例會使用<xref:System.Windows.Controls.Canvas>包含多線條，您可以使用 polyline 項目 （和其他圖形元素） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。  
  
 這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Shapes.Polygon>  
 <xref:System.Windows.Shapes.Shape>  
 [圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)  
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
