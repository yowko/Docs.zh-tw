---
title: "如何：指定腳本動畫之間的傳遞行為 | Microsoft Docs"
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
  - "動畫, 之間的傳遞行為"
  - "分鏡腳本, 動畫之間的傳遞行為"
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：指定腳本動畫之間的傳遞行為
這個範例說明如何指定腳本動畫之間的傳遞行為。  <xref:System.Windows.Media.Animation.BeginStoryboard> 的 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> 屬性，指定新的動畫如何與已套用至屬性的任何現有動畫進行互動。  
  
## 範例  
 下列範例會建立兩個按鈕，當滑鼠移至按鈕上時按鈕會變大，滑鼠離開時按鈕會變小。  如果您將滑鼠移至按鈕上然後快速移走游標，則在第一個動畫結束前就會套用第二個動畫。  當兩個動畫像這樣重疊時，您就可以看到 <xref:System.Windows.Media.Animation.HandoffBehavior> 和 <xref:System.Windows.Media.Animation.HandoffBehavior> 的 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> 值之間的差異。  <xref:System.Windows.Media.Animation.HandoffBehavior> 的值結合了重疊的動畫，可使動畫的轉換更平順，而 <xref:System.Windows.Media.Animation.HandoffBehavior> 的值可使新的動畫立即取代之前的重疊動畫。  
  
 [!code-xml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.BeginStoryboard>   
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/zh-tw/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)