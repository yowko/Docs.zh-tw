---
title: 如何：在 PathGeometry 內建立多個子路徑
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 5b129b1bacb5dc2cba87376e8df70e115a5ebd72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a>如何：在 PathGeometry 內建立多個子路徑
這個範例示範如何建立多個子路徑中的<xref:System.Windows.Media.PathGeometry>。 若要建立多個路徑，您建立<xref:System.Windows.Media.PathFigure>的每一個子路徑。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個路徑，每個三角形。  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 下列範例示範如何藉由建立多個子路徑<xref:System.Windows.Shapes.Path>和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性語法。 每個`M`會建立新的子路徑，讓此範例會建立每個繪製三角形的兩個路徑。  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 (請注意，此屬性的語法確實建立<xref:System.Windows.Media.StreamGeometry>的輕量型版本<xref:System.Windows.Media.PathGeometry>。 如需詳細資訊，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)頁面。)  
  
## <a name="see-also"></a>另請參閱  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
