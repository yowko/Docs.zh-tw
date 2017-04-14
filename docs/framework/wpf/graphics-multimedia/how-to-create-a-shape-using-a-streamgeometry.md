---
title: "如何：使用 StreamGeometry 建立圖案 | Microsoft Docs"
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
  - "類別, StreamGeometry"
  - "圖形 [WPF], 圖案"
  - "圖案, 使用 StreamGeometry 類別建立"
  - "StreamGeometry 類別"
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用 StreamGeometry 建立圖案
<xref:System.Windows.Media.StreamGeometry> 是 <xref:System.Windows.Media.PathGeometry> 的輕量 \(Light\-Weight\) 替代方式，用於建立幾何圖案。  當您需要描述複雜幾何圖案，但是不想要有支援資料繫結、動畫或修改的額外負荷時，請使用 <xref:System.Windows.Media.StreamGeometry>。  例如，<xref:System.Windows.Media.StreamGeometry> 類別因為十分具有效率，所以是描述 Adorner 的好選擇。  
  
## 範例  
 下列範例使用屬性語法，在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中建立三角形 <xref:System.Windows.Media.StreamGeometry>。  
  
 [!code-xml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 如需 <xref:System.Windows.Media.StreamGeometry> 屬性語法的詳細資訊，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)頁面。  
  
## 範例  
 下一個範例使用 <xref:System.Windows.Media.StreamGeometry>，以程式碼定義三角形。  範例會先建立 <xref:System.Windows.Media.StreamGeometry>，然後取得 <xref:System.Windows.Media.StreamGeometryContext>，再使用它來描述三角形。  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## 範例  
 下一個範例建立的方法會使用 <xref:System.Windows.Media.StreamGeometry> 和 <xref:System.Windows.Media.StreamGeometryContext>，根據所指定的參數來定義幾何圖案。  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## 請參閱  
 <xref:System.Windows.Media.PathGeometry>   
 <xref:System.Windows.Media.StreamGeometry>   
 <xref:System.Windows.Media.StreamGeometryContext>   
 [使用 PathGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)   
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)