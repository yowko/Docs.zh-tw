---
title: "如何：建立複合圖形 | Microsoft Docs"
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
  - "類別, DrawingGroup"
  - "複合繪圖"
  - "DrawingGroup 類別"
  - "繪圖, 複合"
  - "圖形, 複合繪圖"
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：建立複合圖形
本範例示範如何使用 <xref:System.Windows.Media.DrawingGroup>，將多個 <xref:System.Windows.Media.Drawing> 物件合併到單一複合繪圖，以建立複雜的繪圖。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.DrawingGroup>，從 <xref:System.Windows.Media.GeometryDrawing> 和 <xref:System.Windows.Media.ImageDrawing> 物件建立複合繪圖。  下圖顯示的是這個範例產生的輸出。  
  
 ![包含多個圖形的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.png "graphicsmm\_simple")  
使用 DrawingGroup 建立的複合繪圖  
  
 請注意灰色框線，這是繪圖的界限。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 您可以使用 <xref:System.Windows.Media.DrawingGroup>，將 <xref:System.Windows.Media.DrawingGroup.Transform%2A>、<xref:System.Windows.Media.DrawingGroup.Opacity%2A> 設定、<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>、<xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> 或 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> 套用到它所包含的繪圖。  由於 <xref:System.Windows.Media.DrawingGroup> 也是 <xref:System.Windows.Media.Drawing>，因此可以包含其他 <xref:System.Windows.Media.DrawingGroup> 物件。  
  
 下列範例與上面範例類似，不同的是它使用了更多的 <xref:System.Windows.Media.DrawingGroup> 物件，將點陣圖效果和不透明遮罩套用到部分繪圖。  下圖顯示的是這個範例產生的輸出。  
  
 ![包含多個圖形的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.png "graphicsmm\_multiple")  
有多個 DrawingGroup 物件的複合繪圖  
  
 請注意灰色框線，這是繪圖的界限。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 如需 <xref:System.Windows.Media.Drawing> 物件的詳細資訊，請參閱[繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>   
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>   
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>   
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>   
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>   
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)