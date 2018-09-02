---
title: 如何：修改線條或線段結尾的端點
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: aef85383a10629eb42f51ea86305636fd90600cb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421824"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>如何：修改線條或線段結尾的端點
此範例示範如何修改的圖形的開頭或結尾開啟<xref:System.Windows.Shapes.Shape>項目。 若要變更的已開啟的開頭上限<xref:System.Windows.Shapes.Shape>，使用其<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>屬性。 若要變更的已開啟的結尾上限<xref:System.Windows.Shapes.Shape>，使用其<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>屬性。 若要檢視可用的線條端點，請參閱<xref:System.Windows.Media.PenLineCap>列舉型別。  
  
> [!NOTE]
>  這個屬性只會影響開放的圖形，例如<xref:System.Windows.Shapes.Line>，則<xref:System.Windows.Shapes.Polyline>，或開啟<xref:System.Windows.Shapes.Path>項目。  
  
 下列範例會繪製四個<xref:System.Windows.Shapes.Polyline>項目，並使用一組不同的圖形的每個端點。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
