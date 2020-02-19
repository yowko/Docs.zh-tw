---
title: 如何：修改線條或線段結尾的端點
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 5f755d7b4d1682755ea461121f91c0666d450ad1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452775"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>如何：修改線條或線段結尾的端點
這個範例示範如何在開啟的 <xref:System.Windows.Shapes.Shape> 元素的開頭或結尾修改圖形。 若要變更開啟 <xref:System.Windows.Shapes.Shape>開頭的端點，請使用其 <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> 屬性。 若要變更開啟 <xref:System.Windows.Shapes.Shape>結尾的端點，請使用其 <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> 屬性。 若要查看可用的行首，請參閱 <xref:System.Windows.Media.PenLineCap> 列舉。  
  
> [!NOTE]
> 此屬性只會影響開啟的圖形，例如 <xref:System.Windows.Shapes.Line>、<xref:System.Windows.Shapes.Polyline>或 open <xref:System.Windows.Shapes.Path> 元素。  
  
 下列範例會繪製四個 <xref:System.Windows.Shapes.Polyline> 專案，並在每個元素的兩端使用不同的圖形集。  
  
## <a name="example"></a>範例  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
