---
title: "如何：建立 SolidColorBrush 色彩或不透明效果的動畫 | Microsoft Docs"
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
  - "動畫, SolidColorBrush 的色彩"
  - "動畫, SolidColorBrush 的不透明度"
  - "色彩, 動畫"
  - "不透明度, 動畫"
  - "SolidColorBrush, 建立色彩動畫"
  - "SolidColorBrush, 建立不透明度動畫"
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立 SolidColorBrush 色彩或不透明效果的動畫
本範例顯示如何建立 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 和 <xref:System.Windows.Media.Brush.Opacity%2A> 的動畫。  
  
## 範例  
 下列範例使用三個動畫來建立 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 和 <xref:System.Windows.Media.Brush.Opacity%2A> 的動畫。  
  
-   第一個動畫 <xref:System.Windows.Media.Animation.ColorAnimation> 會在滑鼠進入矩形時變更筆刷的色彩為 <xref:System.Windows.Media.Colors.Gray%2A>。  
  
-   下一個動畫是另一個 <xref:System.Windows.Media.Animation.ColorAnimation>，會在滑鼠離開矩形時變更筆刷的色彩為 <xref:System.Windows.Media.Colors.Orange%2A>。  
  
-   最後一個動畫 <xref:System.Windows.Media.Animation.DoubleAnimation>，會在按下滑鼠左鍵時變更筆刷的不透明度為 0.0。  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 如需如何建立不同類型筆刷之動畫的完整範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973) \(英文\)。  如需動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 為了保持與其他動畫範例的一致性，這個範例的程式碼版本是使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來套用其動畫。  不過，在程式碼中套用單一動畫時，使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法會比使用 <xref:System.Windows.Media.Animation.Storyboard> 更簡單。  如需範例，請參閱 [不使用腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973)