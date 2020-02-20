---
title: 如何：建立三次方貝茲曲線
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452106"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>如何：建立三次方貝茲曲線
這個範例顯示如何建立三次方貝茲曲線。 若要建立三次方貝茲曲線，請使用 [<xref:System.Windows.Media.PathGeometry>]、[<xref:System.Windows.Media.PathFigure>] 和 [<xref:System.Windows.Media.BezierSegment>] 類別。  若要顯示產生的幾何，請使用 <xref:System.Windows.Shapes.Path> 元素，或搭配 <xref:System.Windows.Media.GeometryDrawing> 或 <xref:System.Windows.Media.DrawingContext>使用。 在下列範例中，會從（10，100）到（300，100）繪製三次方貝茲曲線。 曲線的控制點為（100，0）和（200，200）。  
  
## <a name="example"></a>範例  
 [xaml]  
  
 在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，您可以使用縮寫的標記語法來描述路徑。  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 [xaml]  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中，您也可以使用物件標記繪製三次方貝茲曲線。 下列範例相當於先前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例。  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)。  
  
## <a name="see-also"></a>另請參閱

- [建立橢圓形弧線](how-to-create-an-elliptical-arc.md)
- [在 PathGeometry 中建立 LineSegment](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [建立三次方貝茲曲線](how-to-create-a-cubic-bezier-curve.md)
- [建立二次方貝茲曲線](how-to-create-a-quadratic-bezier-curve.md)
