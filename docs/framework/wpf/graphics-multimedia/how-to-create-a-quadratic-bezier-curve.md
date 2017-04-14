---
title: "如何：建立二次方貝茲曲線 | Microsoft Docs"
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
  - "貝茲曲線, 建立"
  - "圖形 [WPF], 二次方貝茲曲線"
  - "二次方貝茲曲線, 建立"
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立二次方貝茲曲線
本範例顯示如何建立二次方貝茲曲線。  若要建立二次方貝茲曲線，請使用 <xref:System.Windows.Media.PathGeometry>、<xref:System.Windows.Media.PathFigure> 和 <xref:System.Windows.Media.QuadraticBezierSegment> 類別。  
  
## 範例  
 在下列範例中，會繪製從 \(10,100\) 到 \(300,100\) 的二次方貝茲曲線。  曲線具有控制點 \(200,200\)。  
  
 \[xaml\]  
  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，您可以使用屬性語法來描述路徑。  
  
 [!code-xml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 \[xaml\]  
  
 \(請注意，此屬性語法實際上會建立 <xref:System.Windows.Media.StreamGeometry>，這是 <xref:System.Windows.Media.PathGeometry> 的輕量版。  如需詳細資訊，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)網頁\)。  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，您也可以使用物件項目語法繪製二次方貝茲曲線。  以下內容相當於前一個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例。  
  
 [!code-xml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 這個範例是完整範例的一部分。如需完整範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989) \(英文\)。  
  
## 請參閱  
 [建立橢圓弧形](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)   
 [建立三次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)