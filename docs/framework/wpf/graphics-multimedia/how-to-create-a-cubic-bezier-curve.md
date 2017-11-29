---
title: "如何：建立三次方貝茲曲線"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35d4fad0634586d5d0c6ea85f276d6e76edb3f63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>如何：建立三次方貝茲曲線
這個範例示範如何建立三次方貝茲曲線。 若要建立的三次方貝茲曲線，使用<xref:System.Windows.Media.PathGeometry>， <xref:System.Windows.Media.PathFigure>，和<xref:System.Windows.Media.BezierSegment>類別。  若要顯示產生的幾何，請使用<xref:System.Windows.Shapes.Path>項目，或使用它與<xref:System.Windows.Media.GeometryDrawing>或<xref:System.Windows.Media.DrawingContext>。 在下列範例中，三次方貝茲曲線取自 （10，100） 到 （300，100）。 曲線有的控點 （100，0） 和 （200，200）。  
  
## <a name="example"></a>範例  
 [xaml]  
  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您可以使用縮寫的標記語法來描述路徑。  
  
 [!code-xaml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 [xaml]  
  
 在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您也可以繪製三次方貝茲曲線，使用物件標記。 下列範例相當於先前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例。  
  
 [!code-xaml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989)。  
  
## <a name="see-also"></a>另請參閱  
 [建立橢圓形弧線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [在 PathGeometry 中建立 LineSegment](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)  
 [建立三次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)  
 [建立二次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
