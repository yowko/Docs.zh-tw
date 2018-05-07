---
title: 如何：繪製線條
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: 1093e754912cd3ee3b8474ed7d190913079a9f9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-line"></a>如何：繪製線條
此範例將示範如何使用的繪製線條<xref:System.Windows.Shapes.Line>項目。  
  
 若要繪製一條線，建立<xref:System.Windows.Shapes.Line>項目。 使用其<xref:System.Windows.Shapes.Line.X1%2A>和<xref:System.Windows.Shapes.Line.Y1%2A>屬性來設定它的起點; 並使用其<xref:System.Windows.Shapes.Line.X2%2A>和<xref:System.Windows.Shapes.Line.Y2%2A>屬性可用來設定其結束點。 最後，設定其<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>因為沒有筆觸線條是不可見。  
  
 設定<xref:System.Windows.Shapes.Shape.Fill%2A>一條線的項目無效，因為列不有任何內部。  
  
 下列範例會繪製內三行<xref:System.Windows.Controls.Canvas>項目。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 這個範例是較大範例的一部分如需完整範例，請參閱[圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Shapes.Line>  
 [圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)
