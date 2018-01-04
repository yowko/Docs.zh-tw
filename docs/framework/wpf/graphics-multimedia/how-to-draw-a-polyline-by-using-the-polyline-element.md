---
title: "如何：使用 Polyline 項目繪製聚合線"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b0b027aa34b310413fa02e81149292fabb40f79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>如何：使用 Polyline 項目繪製聚合線
此範例顯示如何畫聚合線條，這是使用一系列連接的直線<xref:System.Windows.Shapes.Polyline>項目。  
  
 若要繪製的聚合線條，請建立<xref:System.Windows.Shapes.Polyline>項目，並使用其<xref:System.Windows.Shapes.Polyline.Points%2A>屬性可指定圖形頂點。 最後，使用<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>來描述聚合線條的內容大綱，因為沒有筆觸線條是不可見。  
  
> [!NOTE]
>  因為<xref:System.Windows.Shapes.Polyline>元素不是封閉的圖形，<xref:System.Windows.Shapes.Shape.Fill%2A>屬性有任何作用，即使您刻意關閉圖形外框。 若要建立具有封閉的圖形<xref:System.Windows.Shapes.Shape.Fill%2A>，使用<xref:System.Windows.Shapes.Polygon>項目。  
  
 下列範例會繪製兩個<xref:System.Windows.Shapes.Polyline>內的項目<xref:System.Windows.Controls.Canvas>。  
  
## <a name="example"></a>範例  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，點的有效語法是以空格分隔清單的逗號分隔 x 和 y 座標組。  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 雖然這個範例會使用<xref:System.Windows.Controls.Canvas>包含聚合線條，您可以使用聚合線條元素 （和其他所有圖形項目） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。  
  
 這個範例是較大範例的一部分如需完整範例，請參閱[圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Shapes.Polygon>  
 <xref:System.Windows.Shapes.Shape>  
 [圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
