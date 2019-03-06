---
title: HOW TO：繪製矩形
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 2734d5e808e8bc1f78c281e3fd6ab3c6ff12c58f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363744"
---
# <a name="how-to-draw-a-rectangle"></a>HOW TO：繪製矩形
此範例示範如何藉由繪製矩形<xref:System.Windows.Shapes.Rectangle>項目。  
  
 若要繪製矩形，建立<xref:System.Windows.Shapes.Rectangle>項目，並指定其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>。 若要繪製的矩形內部，請將其<xref:System.Windows.Shapes.Shape.Fill%2A>。 若要讓矩形外框，使用其<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性。  
  
 提供給矩形的圓角中，指定選擇性<xref:System.Windows.Shapes.Rectangle.RadiusX%2A>和<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>屬性。 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>和<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>設定 x 軸和 y 軸半徑，用來將矩形的圓角的省略符號的屬性。  
  
 在下列範例中，兩個<xref:System.Windows.Shapes.Rectangle>項目會繪製<xref:System.Windows.Controls.Canvas>。 第一個矩形具有<xref:System.Windows.Media.Brushes.Blue%2A>內部。 第二個矩形<xref:System.Windows.Media.Brushes.Blue%2A>內部，<xref:System.Windows.Media.Brushes.Black%2A>大綱和圓的角。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 雖然此範例會使用<xref:System.Windows.Controls.Canvas>要包含的矩形，您可以使用矩形元素 （和其他圖形元素） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。 事實上，矩形會特別有用的部分位置提供背景<xref:System.Windows.Controls.Grid>面板。 如需範例，請參閱[資料表概觀](../advanced/table-overview.md)。  
  
 這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Shapes.Rectangle>
- [圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [資料表概觀](../advanced/table-overview.md)
