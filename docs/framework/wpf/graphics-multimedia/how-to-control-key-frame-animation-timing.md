---
title: "如何：控制主要畫面格動畫執行時間 | Microsoft Docs"
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
  - "主要畫面格 [WPF], 計時"
  - "主要畫面格動畫執行時間"
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：控制主要畫面格動畫執行時間
本範例說明如何控制主要畫面格動畫內的主要動畫格執行時間。  如同其他動畫，主要畫面格動畫也有 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 屬性。  除了指定動畫的持續時間，您還需要指定這段時間的哪一段要分配給動畫的每一個主要畫面格。  若要分配時間，請指定動畫中每個主要畫面格的 <xref:System.Windows.Media.Animation.KeyTime>。  
  
 每個主要畫面格的 <xref:System.Windows.Media.Animation.KeyTime> 會指定主要畫面格結束的時間 \(它不會指定主要畫面格播放的時間長度\)。  您可以將 <xref:System.Windows.Media.Animation.KeyTime> 指定為 <xref:System.TimeSpan> 值、百分比，或是 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> 或 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> 特殊值。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>，讓矩形顯示成移至畫面另一邊的動畫。  主要畫面格的主要時間使用 <xref:System.TimeSpan> 值設定。  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 下圖顯示每個主要畫面格的值到達的時機。  
  
 ![在 3、4 和 10 秒時到達各個主要畫面格](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm\_keyframe\_keytime1\_timespan")  
  
 下面的範例顯示完全相同的動畫，差別在於主要畫面格的主要時間是使用百分比值設定。  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 下圖顯示每個主要畫面格的值到達的時機。  
  
 ![在 3、4 和 10 秒時到達各個主要畫面格](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm\_keyframe\_keytime2\_percentage")  
  
 下面的範例使用 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> 主要時間值。  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 下圖顯示每個主要畫面格的值到達的時機。  
  
 ![在 3.3、6.6 和 9.9 秒時到達各個主要畫面格](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm\_keyframe\_keytime3\_uniform")  
  
 最後一個範例使用 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> 主要時間值。  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 下圖顯示每個主要畫面格的值到達的時機。  
  
 ![在 0、5 和 10 秒時到達各個主要畫面格](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm\_keyframe\_keytime4\_paced")  
  
 為了容易說明，此範例的程式碼版本使用本機動畫而非腳本，這是因為只將單一動畫套用到單一屬性，不過這些範例也可以修改成使用腳本。  如需說明如何在程式碼中宣告腳本的範例，請參閱 [使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)。  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  如需主要畫面格動畫的詳細資訊，請參閱[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
## 請參閱  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)