---
title: "如何：使用腳本建立屬性的動畫後進行設定 | Microsoft Docs"
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
  - "動畫, 之後變更屬性值"
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用腳本建立屬性的動畫後進行設定
在某些情況下，建立屬性值的動畫之後，可能會出現看似無法變更該屬性值的狀況。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Media.Animation.Storyboard> 建立 <xref:System.Windows.Media.SolidColorBrush> 的色彩動畫。  按一下按鈕時，便會觸發此腳本。  系統會處理 <xref:System.Windows.Media.Animation.Timeline.Completed>，讓程式在 <xref:System.Windows.Media.Animation.ColorAnimation> 完成時收到通知。  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## 範例  
 在 <xref:System.Windows.Media.Animation.ColorAnimation> 完成之後，程式會嘗試將筆刷的色彩變更為藍色。  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 前述程式碼看似沒有任何效果：筆刷仍為黃色，也就是建立筆刷動畫效果之 <xref:System.Windows.Media.Animation.ColorAnimation> 所提供的值。  實際上基礎屬性值 \(基底值\) 已經變更為藍色。  但是有效的值或是目前的值仍然是黃色，因為 <xref:System.Windows.Media.Animation.ColorAnimation> 還是會覆寫基底值。  如果要讓基底值再次變成有效值，您必須停止動畫對屬性的影響。  有三種方式可以對腳本動畫執行這個動作：  
  
-   將動畫的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性設定為 <xref:System.Windows.Media.Animation.FillBehavior>。  
  
-   移除整個腳本。  
  
-   從個別屬性移除動畫。  
  
## 將動畫的 FillBehavior 屬性設定為 Stop  
 將 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 設定為 <xref:System.Windows.Media.Animation.FillBehavior>，可以指示動畫在其作用期結束後停止影響它的目標屬性。  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## 移除整個腳本  
 使用 <xref:System.Windows.Media.Animation.RemoveStoryboard> 觸發程序 \(Trigger\) 或 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=fullName> 方法，可以指示腳本動畫停止影響其目標屬性。  這個方法和設定 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性的差別是您可以隨時移除腳本，而 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性只在動畫的作用期結束時才有作用。  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## 從個別屬性移除動畫  
 讓動畫停止影響屬性的另一種方法是使用顯示為動畫之物件的 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> 方法。  請將顯示動畫的屬性指定為第一個參數，而 `null` 則為第二個參數。  
  
 [!code-xml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 這個方法也適用於非腳本動畫。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>   
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=fullName>   
 <xref:System.Windows.Media.Animation.RemoveStoryboard>   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)