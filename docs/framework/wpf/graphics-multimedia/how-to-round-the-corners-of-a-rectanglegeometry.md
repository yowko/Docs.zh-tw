---
title: HOW TO：將 RectangleGeometry 的邊角設為圓角
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: f00d7a7cd6117318efb17645bbb9df279c97adff
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378531"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>HOW TO：將 RectangleGeometry 的邊角設為圓角
要四捨五入的邊角<xref:System.Windows.Media.RectangleGeometry>，將其<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>屬性小於或等於零的值。 值愈大，愈矩形邊角。  
  
## <a name="example"></a>範例  
 下列範例將示範數個<xref:System.Windows.Media.RectangleGeometry>具有不同的物件<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>設定。 <xref:System.Windows.Media.RectangleGeometry>物件會顯示使用<xref:System.Windows.Shapes.Path>項目。  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![具有不同 RadiusX 的矩形&#47;RadiusY 設定](./media/graphicsmm-rounded.png "graphicsmm_rounded")  
具有圓角矩形  
  
## <a name="see-also"></a>另請參閱
- [幾何概觀](geometry-overview.md)
- [建立複合圖案](how-to-create-a-composite-shape.md)
- [使用 PathGeometry 建立圖案](how-to-create-a-shape-by-using-a-pathgeometry.md)
