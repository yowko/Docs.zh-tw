---
title: "如何：建立合併幾何 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "合併幾何"
  - "幾何, 組合"
  - "圖形, 合併幾何"
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立合併幾何
本範例示範如何合併幾何。  若要合併兩個幾何，請使用 <xref:System.Windows.Media.CombinedGeometry> 物件。  請使用要合併的兩個幾何設定該物件的 <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> 和 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 屬性，並將決定幾何合併方式的 <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> 屬性設定為 `Union`、`Intersect`、`Exclude` 或 `Xor`。  
  
 若要從兩個以上的幾何建立複合幾何，請使用 <xref:System.Windows.Media.GeometryGroup>。  
  
## 範例  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry> 是以 `Exclude` 的幾何合併模式定義。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> 和 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 都定義為相同半徑的圓形，但是中心相差 50。  
  
 [!code-xml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![Exclude 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.png "mil\_task\_combined\_geometry\_exclude")  
合併幾何：Exclude  
  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry> 是以 `Intersect` 合併模式定義。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> 和 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 都定義為相同半徑的圓形，但是中心相差 50。  
  
 [!code-xml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![Intersect 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.png "mil\_task\_combined\_geometry\_intersect")  
合併幾何：Intersect  
  
 在下列標記中，<xref:System.Windows.Media.CombinedGeometry> 是以 `Union` 的合併模式定義。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> 和 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 都定義為相同半徑的圓形，但是中心相差 50。  
  
 [!code-xml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Union 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.png "mil\_task\_combined\_geometry\_union")  
合併幾何：Union  
  
 在下列標記中，<xref:System.Windows.Media.CombinedGeometry> 是以 `Xor` 的合併模式定義。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> 和 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 都定義為相同半徑的圓形，但是中心相差 50。  
  
 [!code-xml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.png "mil\_task\_combined\_geometry\_xor")  
合併幾何：Xor