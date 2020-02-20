---
title: 如何：建立橢圓弧形
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453061"
---
# <a name="how-to-create-an-elliptical-arc"></a>如何：建立橢圓弧形
這個範例示範如何繪製橢圓形弧線。若要建立橢圓形弧線，請使用 [<xref:System.Windows.Media.PathGeometry>]、[<xref:System.Windows.Media.PathFigure>] 和 [<xref:System.Windows.Media.ArcSegment>] 類別。  
  
## <a name="example"></a>範例  
 在下列範例中，會從（10100）繪製橢圓形弧線到（200100）。 弧線的 <xref:System.Windows.Media.ArcSegment.Size%2A> 為100，50與裝置無關的圖元、45度的 <xref:System.Windows.Media.ArcSegment.RotationAngle%2A>、`true`的 <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> 設定，以及 <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> <xref:System.Windows.Media.SweepDirection.Counterclockwise>。  
  
 [xaml]  
  
 在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，您可以使用屬性語法來描述路徑。  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 [xaml]  
  
 （請注意，此屬性語法實際上會建立 <xref:System.Windows.Media.StreamGeometry>，也就是較輕量的 <xref:System.Windows.Media.PathGeometry>版本。 如需詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)頁面。)  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中，您也可以藉由明確地使用物件標記來繪製橢圓形弧線。 下列相當於上述 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記。  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 這個範例是某完整範例的一部分。 如需完整範例，請參閱[幾何範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)。  
  
## <a name="see-also"></a>另請參閱

- [建立二次方貝茲曲線](how-to-create-a-quadratic-bezier-curve.md)
- [建立三次方貝茲曲線](how-to-create-a-cubic-bezier-curve.md)
