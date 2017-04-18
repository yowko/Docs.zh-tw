---
title: "如何：建立橢圓弧形 | Microsoft Docs"
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
  - "弧形, 橢圓形"
  - "橢圓弧形, 建立"
  - "圖形 [WPF], 橢圓弧形"
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：建立橢圓弧形
本範例示範如何繪製橢圓弧形。  若要建立橢圓弧形，請使用 <xref:System.Windows.Media.PathGeometry>、<xref:System.Windows.Media.PathFigure> 和 <xref:System.Windows.Media.ArcSegment> 類別。  
  
## 範例  
 在下列範例中，會從 \(10,100\) 繪製橢圓弧形至 \(200,100\)。  此弧形的 <xref:System.Windows.Media.ArcSegment.Size%2A> 為 100 x 50 與裝置無關 \(Device\-Independent\) 的像素、<xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 為 45 度角、<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> 設定為 `true`，以及 <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> 為 <xref:System.Windows.Media.SweepDirection>。  
  
 \[xaml\]  
  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，您可以使用屬性語法來描述路徑。  
  
 [!code-xml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 \[xaml\]  
  
 \(請注意，此屬性語法實際上會建立 <xref:System.Windows.Media.StreamGeometry>，這是 <xref:System.Windows.Media.PathGeometry> 的輕量版。  如需詳細資訊，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)網頁\)。  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，您也可以明確使用物件標記繪製橢圓弧形。  以下相當於前面的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記。  
  
 [!code-xml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 這個範例是完整範例的一部分。  如需完整範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989) \(英文\)。  
  
## 請參閱  
 [建立二次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)   
 [建立三次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)