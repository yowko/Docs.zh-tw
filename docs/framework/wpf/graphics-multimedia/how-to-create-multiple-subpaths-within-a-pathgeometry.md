---
title: "如何：在 PathGeometry 內建立多個子路徑 | Microsoft Docs"
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
  - "類別, PathGeometry"
  - "圖形 [WPF], 子路徑"
  - "多個子路徑"
  - "PathGeometry 類別"
  - "子路徑"
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在 PathGeometry 內建立多個子路徑
本範例示範如何在 <xref:System.Windows.Media.PathGeometry> 中建立多個子路徑。  若要建立多個子路徑，請為每個子路徑建立 <xref:System.Windows.Media.PathFigure>。  
  
## 範例  
 下列範例會建立兩個子路徑，每一個路徑會建立一個三角形。  
  
 [!code-xml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 下列範例示範如何使用 <xref:System.Windows.Shapes.Path> 和 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 屬性語法建立多個子路徑。  每個 `M` 都會建立新的子路徑，因此這個範例會建立兩個子路徑，每個子路徑都會繪製一個三角形。  
  
 [!code-xml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 \(請注意，此屬性語法實際上會建立 <xref:System.Windows.Media.StreamGeometry>，這是 <xref:System.Windows.Media.PathGeometry> 的輕量版。  如需詳細資訊，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)網頁\)。  
  
## 請參閱  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)