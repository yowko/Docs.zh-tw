---
title: 如何：使用 PathGeometry 建立圖案
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: 4c9cd7a1af921a0a547c7dec3afc5f69b29e6aed
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748576"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>如何：使用 PathGeometry 建立圖案
此範例示範如何使用建立圖形<xref:System.Windows.Media.PathGeometry>類別。 <xref:System.Windows.Media.PathGeometry> 物件會組成一或多個<xref:System.Windows.Media.PathFigure>物件; 每個<xref:System.Windows.Media.PathFigure>代表不同的 「 圖形 」 或圖案。 每個<xref:System.Windows.Media.PathFigure>本身由一或多個<xref:System.Windows.Media.PathSegment>物件，每個均代表圖形或圖案的已連接的部分。 線段類型包括<xref:System.Windows.Media.LineSegment>， <xref:System.Windows.Media.ArcSegment>，和<xref:System.Windows.Media.BezierSegment>。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.PathGeometry>，以建立三角形。 <xref:System.Windows.Media.PathGeometry>會顯示使用<xref:System.Windows.Shapes.Path>項目。  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 下圖顯示上一個範例中所建立的圖案。  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
使用 PathGeometry 建立三角形  
  
 前一個範例，示範如何建立簡單的圖形，三角形。 A<xref:System.Windows.Media.PathGeometry>也可用來建立更複雜的圖形，包括弧線和曲線。 如需範例，請參閱[建立橢圓形弧線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)，[建立三次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)，並[建立二次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)。  
  
 這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)
