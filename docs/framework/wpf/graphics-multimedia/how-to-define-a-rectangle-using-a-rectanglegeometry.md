---
title: 如何：使用 RectangleGeometry 定義矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 5d2ec6aec1eea8528ea6b43f72f4820b8bc19a37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>如何：使用 RectangleGeometry 定義矩形
這個範例說明如何使用<xref:System.Windows.Media.RectangleGeometry>來描述矩形的類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立及呈現<xref:System.Windows.Media.RectangleGeometry>。  所定義的相對位置和矩形的維度<xref:System.Windows.Rect>結構。 相對的位置是`50,50`和高度和寬度都`25`建立正方形。 矩形的內部繪製與<xref:System.Windows.Media.Brushes.LemonChiffon%2A>筆刷和控制項外框繪製與<xref:System.Windows.Media.Brushes.Black%2A>筆觸的粗細`1`。  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 雖然這個範例使用<xref:System.Windows.Shapes.Path>項目來呈現<xref:System.Windows.Media.RectangleGeometry>，有許多其他的方式使用<xref:System.Windows.Media.RectangleGeometry>物件。 例如，<xref:System.Windows.Media.RectangleGeometry>可以用來指定<xref:System.Windows.UIElement.Clip%2A>的<xref:System.Windows.UIElement>或<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>的<xref:System.Windows.Media.GeometryDrawing>。  
  
 其他簡單的幾何類別包含<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.EllipseGeometry>。 這些幾何，以及更複雜的也可以建立使用<xref:System.Windows.Media.PathGeometry>或<xref:System.Windows.Media.StreamGeometry>。  
  
## <a name="see-also"></a>另請參閱  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [建立複合圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [使用 PathGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
