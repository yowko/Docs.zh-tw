---
title: HOW TO：建立橢圓形弧線
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: aae304b9963f3a8e5833b4d8ba0a54777a750225
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183647"
---
# <a name="how-to-create-an-elliptical-arc"></a>HOW TO：建立橢圓形弧線
此範例示範如何繪製橢圓形弧線。使用來建立橢圓形弧線<xref:System.Windows.Media.PathGeometry>， <xref:System.Windows.Media.PathFigure>，和<xref:System.Windows.Media.ArcSegment>類別。  
  
## <a name="example"></a>範例  
 在下列範例中，會從 (10100) 到 (200,100) 繪製橢圓形弧線。 該弧線<xref:System.Windows.Media.ArcSegment.Size%2A>100 x 50 與裝置無關的像素， <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 度，<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>設定`true`，和<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>的<xref:System.Windows.Media.SweepDirection.Counterclockwise>。  
  
 [xaml]  
  
 在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您可以使用屬性語法來描述路徑。  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 [xaml]  
  
 (請注意，此屬性語法實際上會建立<xref:System.Windows.Media.StreamGeometry>，輕量版<xref:System.Windows.Media.PathGeometry>。 如需詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)頁面。)  
  
 在  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您也可以明確地使用物件標記繪製橢圓形弧線。 以下是相當於上述[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記。  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 這個範例是某完整範例的一部分。 如需完整的範例，請參閱[幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)。  
  
## <a name="see-also"></a>另請參閱

- [建立二次方貝茲曲線](how-to-create-a-quadratic-bezier-curve.md)
- [建立三次方貝茲曲線](how-to-create-a-cubic-bezier-curve.md)
