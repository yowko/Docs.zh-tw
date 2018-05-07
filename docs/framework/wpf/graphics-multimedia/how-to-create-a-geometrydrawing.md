---
title: 如何：建立 GeometryDrawing
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: 713cecd10bfa62494c50c96cb8cbece69f7e5660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-geometrydrawing"></a>如何：建立 GeometryDrawing
這個範例示範如何建立和顯示<xref:System.Windows.Media.GeometryDrawing>。 A<xref:System.Windows.Media.GeometryDrawing>可讓您建立與填滿外框的圖形關聯<xref:System.Windows.Media.Pen>和<xref:System.Windows.Media.Brush>與<xref:System.Windows.Media.Geometry>。 <xref:System.Windows.Media.GeometryDrawing.Geometry%2A>描述圖形的結構<xref:System.Windows.Media.GeometryDrawing.Brush%2A>描述圖案的填滿，而<xref:System.Windows.Media.GeometryDrawing.Pen%2A>描述圖形外框。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.GeometryDrawing>呈現圖形。 所描述的圖案<xref:System.Windows.Media.GeometryGroup>和兩個<xref:System.Windows.Media.EllipseGeometry>物件。 圖形內部的繪製與<xref:System.Windows.Media.LinearGradientBrush>和使用繪製控制項外框<xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>。 <xref:System.Windows.Media.GeometryDrawing>使用顯示<xref:System.Windows.Media.ImageDrawing>和<xref:System.Windows.Controls.Image>項目。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 下圖顯示所產生<xref:System.Windows.Media.GeometryDrawing>。  
  
 ![橢圓形兩個橢圓形的 GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 若要建立更複雜的繪圖，可以將多個繪圖物件合併成單一複合繪製使用<xref:System.Windows.Media.DrawingGroup>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.DrawingGroup>  
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [建立複合圖形](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
