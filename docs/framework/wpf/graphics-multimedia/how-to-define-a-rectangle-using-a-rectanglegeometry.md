---
title: HOW TO：使用 RectangleGeometry 定義矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: bd42aca2541d67469173f63655ada18a12eb692c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352499"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>HOW TO：使用 RectangleGeometry 定義矩形
此範例說明如何使用<xref:System.Windows.Media.RectangleGeometry>來描述矩形的類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立和轉譯<xref:System.Windows.Media.RectangleGeometry>。  所定義的相對位置和維度的矩形<xref:System.Windows.Rect>結構。 相對的位置`50,50`以及高度和寬度都`25`建立正方形。 用於繪製的矩形內部<xref:System.Windows.Media.Brushes.LemonChiffon%2A>筆刷和其外框使用繪製<xref:System.Windows.Media.Brushes.Black%2A>筆觸粗細是`1`。  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 雖然此範例中使用<xref:System.Windows.Shapes.Path>項目來呈現<xref:System.Windows.Media.RectangleGeometry>，有許多其他使用方式<xref:System.Windows.Media.RectangleGeometry>物件。 例如，<xref:System.Windows.Media.RectangleGeometry>可用來指定<xref:System.Windows.UIElement.Clip%2A>的<xref:System.Windows.UIElement>或<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>的<xref:System.Windows.Media.GeometryDrawing>。  
  
 其他簡單幾何類別包括<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.EllipseGeometry>。 這些幾何，以及更複雜的也可以建立使用<xref:System.Windows.Media.PathGeometry>或<xref:System.Windows.Media.StreamGeometry>。  
  
## <a name="see-also"></a>另請參閱
- [幾何概觀](geometry-overview.md)
- [建立複合圖案](how-to-create-a-composite-shape.md)
- [使用 PathGeometry 建立圖案](how-to-create-a-shape-by-using-a-pathgeometry.md)
