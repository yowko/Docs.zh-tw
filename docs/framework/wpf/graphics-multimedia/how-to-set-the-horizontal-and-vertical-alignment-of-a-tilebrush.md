---
title: "如何：設定 TileBrush 的水平和垂直對齊 | Microsoft Docs"
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
  - "對齊, TileBrushes"
  - "TileBrushes 的水平對齊"
  - "TileBrush, 對齊"
  - "TileBrushes 的垂直對齊"
ms.assetid: 65ae89bd-9246-4c9e-bde4-2fb991d4060d
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：設定 TileBrush 的水平和垂直對齊
本範例說明如何控制並排顯示內容的水平和垂直對齊。  若要控制 <xref:System.Windows.Media.TileBrush> 的水平和垂直對齊，請使用它的 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> 和 <xref:System.Windows.Media.TileBrush.AlignmentY%2A> 屬性。  
  
 當下列任何一個情況成立時，會使用 <xref:System.Windows.Media.TileBrush> 的 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> 和 <xref:System.Windows.Media.TileBrush.AlignmentY%2A> 屬性：  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性是 <xref:System.Windows.Media.Stretch> 或 <xref:System.Windows.Media.Stretch>，而 <xref:System.Windows.Media.TileBrush.Viewbox%2A> 和 <xref:System.Windows.Media.TileBrush.Viewport%2A> 則有不同的[外觀比例](GTMT) \(Aspect Ratio\)。  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性是 <xref:System.Windows.Media.Stretch>，而 <xref:System.Windows.Media.TileBrush.Viewbox%2A> 和 <xref:System.Windows.Media.TileBrush.Viewport%2A> 的大小不同。  
  
## 範例  
 下列範例會將 <xref:System.Windows.Media.DrawingBrush> \(<xref:System.Windows.Media.TileBrush> 的一種\) 的內容對齊其並排顯示的左上角。  為對齊內容，此範例會將 <xref:System.Windows.Media.DrawingBrush> 的 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> 屬性設為 <xref:System.Windows.Media.AlignmentX>，並將 <xref:System.Windows.Media.TileBrush.AlignmentY%2A> 屬性設為 <xref:System.Windows.Media.AlignmentY>。  這個範例產生下列輸出。  
  
 ![對齊左上角的 TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm\_TileBrushAlignmentExampleTopLeft")  
TileBrush 的內容對齊左上角  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## 範例  
 下面的範例會將 <xref:System.Windows.Media.DrawingBrush> 的內容對齊其並排顯示的右下角，將 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> 屬性設為 <xref:System.Windows.Media.AlignmentX>，並將 <xref:System.Windows.Media.TileBrush.AlignmentY%2A> 屬性設為 <xref:System.Windows.Media.AlignmentY>。  這個範例會產生下列輸出。  
  
 ![對齊右下角的 TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm\_TileBrushAlignmentExampleBottomRight")  
TileBrush 的內容對齊右下角  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## 範例  
 下面的範例會將 <xref:System.Windows.Media.DrawingBrush> 的內容對齊其並排顯示的左上角，將 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> 屬性設為 <xref:System.Windows.Media.AlignmentX>，並將 <xref:System.Windows.Media.TileBrush.AlignmentY%2A> 屬性設為 <xref:System.Windows.Media.AlignmentY>。  它也會設定 <xref:System.Windows.Media.DrawingBrush> 的 <xref:System.Windows.Media.TileBrush.Viewport%2A> 和 <xref:System.Windows.Media.TileBrush.TileMode%2A>，以產生並排顯示模式。  這個範例會產生下列輸出。  
  
 ![對齊左上角的並排顯示 TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm\_TileBrushAlignmentExampleTopLeftTiled")  
並排顯示的內容對齊基底並排顯示的左上角  
  
 上圖醒目顯示了基底並排顯示，清楚顯示內容是如何對齊的。  請注意，<xref:System.Windows.Media.TileBrush.AlignmentX%2A> 設定沒有作用，因為 <xref:System.Windows.Media.DrawingBrush> 的內容會以水平方式完全填滿基底並排顯示。  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## 範例  
 最後一個範例會將並排顯示 <xref:System.Windows.Media.DrawingBrush> 的內容對齊其基底並排顯示的右下角，將 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> 屬性設為 <xref:System.Windows.Media.AlignmentX>，並將 <xref:System.Windows.Media.TileBrush.AlignmentY%2A> 屬性設為 <xref:System.Windows.Media.AlignmentY>。  這個範例會產生下列輸出。  
  
 ![對齊右下角的並排顯示 TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm\_TileBrushAlignmentExampleBottomRightTiled")  
並排顯示模式的內容對齊基底並排顯示的右下角  
  
 同樣地，<xref:System.Windows.Media.TileBrush.AlignmentX%2A> 設定沒有作用，因為 <xref:System.Windows.Media.DrawingBrush> 的內容會以水平方式完全填滿基底並排顯示。  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 這些範例都使用 <xref:System.Windows.Media.DrawingBrush> 物件示範如何使用 <xref:System.Windows.Media.TileBrush.AlignmentX%2A> 和 <xref:System.Windows.Media.TileBrush.AlignmentY%2A> 屬性。  不過，這些屬性對所有並排顯示筆刷的作用完全相同：<xref:System.Windows.Media.DrawingBrush>、<xref:System.Windows.Media.ImageBrush> 和 <xref:System.Windows.Media.VisualBrush>。  如需並排顯示筆刷的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.DrawingBrush>   
 <xref:System.Windows.Media.ImageBrush>   
 <xref:System.Windows.Media.VisualBrush>   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)