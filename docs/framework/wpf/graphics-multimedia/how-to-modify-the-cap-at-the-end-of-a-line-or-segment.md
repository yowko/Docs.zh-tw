---
title: 如何：修改線條或線段結尾的端點
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: e69f461d426fc6a587263cea7a18478da53b5b09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>如何：修改線條或線段結尾的端點
這個範例示範如何修改開頭或結尾開啟圖形<xref:System.Windows.Shapes.Shape>項目。 若要變更的開啟開頭 cap <xref:System.Windows.Shapes.Shape>，使用其<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>屬性。 若要變更已開啟的結尾處的 cap <xref:System.Windows.Shapes.Shape>，使用其<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>屬性。 若要檢視可用的線條端點，請參閱<xref:System.Windows.Media.PenLineCap>列舉型別。  
  
> [!NOTE]
>  這個屬性只會影響在圖案，例如<xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Polyline>，或開啟<xref:System.Windows.Shapes.Path>項目。  
  
 下列範例會繪製四個<xref:System.Windows.Shapes.Polyline>項目，並使用每個端點上的一組不同的圖形。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 這個範例是較大範例的一部分如需完整範例，請參閱[圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
