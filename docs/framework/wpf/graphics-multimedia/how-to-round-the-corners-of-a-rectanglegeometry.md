---
title: "如何：將 RectangleGeometry 的邊角設為圓角 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "邊角, 進位"
  - "圖形, 將 RectangleGeometry 物件的邊角設為圓角"
  - "RectangleGeometry 類別, 將邊角設為圓角"
  - "將 RectangleGeometry 物件的邊角設為圓角"
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：將 RectangleGeometry 的邊角設為圓角
若要將 <xref:System.Windows.Media.RectangleGeometry> 的邊角設為圓角，請將其 <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> 和 <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> 屬性設定成大於零的值。  值愈大，矩形的邊角愈圓。  
  
## 範例  
 下列範例顯示具有不同 <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> 和 <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> 設定的幾個 <xref:System.Windows.Media.RectangleGeometry> 物件。  <xref:System.Windows.Media.RectangleGeometry> 物件會透過 <xref:System.Windows.Shapes.Path> 項目顯示。  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![具有不同 RadiusX&#47;RadiusY 設定的矩形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm\_rounded")  
具有圓角的矩形  
  
## 請參閱  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [建立複合圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)   
 [使用 PathGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)