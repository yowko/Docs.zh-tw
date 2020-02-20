---
title: 如何：使用 PathGeometry 建立圖案
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: bdf3c937bfff1780a72e8743bc86a3c3dad2558d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452041"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>如何：使用 PathGeometry 建立圖案
這個範例會示範如何使用 <xref:System.Windows.Media.PathGeometry> 類別來建立圖形。 <xref:System.Windows.Media.PathGeometry> 物件是由一或多個 <xref:System.Windows.Media.PathFigure> 物件所組成;每個 <xref:System.Windows.Media.PathFigure> 都代表不同的「圖形」或圖形。 每個 <xref:System.Windows.Media.PathFigure> 本身都是由一或多個 <xref:System.Windows.Media.PathSegment> 物件所組成，每個都代表圖表或圖形的連接部分。 區段類型包括 <xref:System.Windows.Media.LineSegment>、<xref:System.Windows.Media.ArcSegment>和 <xref:System.Windows.Media.BezierSegment>。  
  
## <a name="example"></a>範例  
 下列範例會使用 <xref:System.Windows.Media.PathGeometry> 來建立三角形。 <xref:System.Windows.Media.PathGeometry> 會使用 <xref:System.Windows.Shapes.Path> 元素來顯示。  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 下圖顯示上一個範例中所建立的圖案。  
  
 ![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
以 System.windows.media.pathgeometry> 建立的三角形  
  
 先前的範例示範如何建立一個相對簡單的圖形，也就是一個三角形。 <xref:System.Windows.Media.PathGeometry> 也可以用來建立更複雜的圖形，包括弧形和曲線。 如需範例，請參閱[建立橢圓形弧線](how-to-create-an-elliptical-arc.md)、[建立三次方貝茲曲線](how-to-create-a-cubic-bezier-curve.md)和[建立二次方貝茲曲線](how-to-create-a-quadratic-bezier-curve.md)。  
  
 這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [幾何概觀](geometry-overview.md)
- [幾何範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
