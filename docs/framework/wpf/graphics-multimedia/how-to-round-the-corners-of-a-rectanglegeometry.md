---
title: 如何：將 RectangleGeometry 的邊角設為圓角
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: e4f1d37e2c0f26967affff14ed6475fc8c0cb28c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>如何：將 RectangleGeometry 的邊角設為圓角
若要圓角<xref:System.Windows.Media.RectangleGeometry>，將其<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>屬性的值小於或等於零。 值愈大，愈矩形的圓角。  
  
## <a name="example"></a>範例  
 下列範例示範數個<xref:System.Windows.Media.RectangleGeometry>物件具有不同<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>設定。 <xref:System.Windows.Media.RectangleGeometry>物件會使用顯示<xref:System.Windows.Shapes.Path>項目。  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![具有不同 RadiusX 矩形&#47;RadiusY 設定](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")  
具有圓角矩形  
  
## <a name="see-also"></a>另請參閱  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [建立複合圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [使用 PathGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
