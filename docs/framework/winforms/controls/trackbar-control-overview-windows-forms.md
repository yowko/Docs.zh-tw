---
title: "TrackBar 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TrackBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "滑桿, 關於滑桿控制項"
  - "滑桿, 關於滑桿"
  - "TrackBar 控制項 [Windows Form], 關於 TrackBar 控制項"
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# TrackBar 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.TrackBar> 控制項 \(有時也稱為「滑桿」\(Slider\) 控制項\) 是用來瀏覽大量資訊或視覺調整數字設定。  <xref:System.Windows.Forms.TrackBar> 控制項是由兩個部分組成：縮圖 \(也稱為滑桿\) 和刻度標記。  縮圖是可以調整的部分。  它的位置和 <xref:System.Windows.Forms.TrackBar.Value%2A> 屬性對應。  刻度標記則是有著固定間距的視覺指示器 \(Indicator\)。  Trackbar 可依您指定來遞增移動距離，也可水平或垂直調整。  例如，您可能使用滑動軸來控制系統的游標閃爍速率或是滑鼠速度。  
  
## 主要屬性  
 <xref:System.Windows.Forms.TrackBar> 控制項的主要屬性是 <xref:System.Windows.Forms.TrackBar.Value%2A>、<xref:System.Windows.Forms.TrackBar.TickFrequency%2A>、<xref:System.Windows.Forms.TrackBar.Minimum%2A> 和 <xref:System.Windows.Forms.TrackBar.Maximum%2A>。  <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> 是刻度的間距。  <xref:System.Windows.Forms.TrackBar.Minimum%2A> 和 <xref:System.Windows.Forms.TrackBar.Maximum%2A> 則是滑動軸上可表示的最小及最大值。  
  
 其他兩個重要屬性為 <xref:System.Windows.Forms.TrackBar.SmallChange%2A> 和 <xref:System.Windows.Forms.TrackBar.LargeChange%2A>。  <xref:System.Windows.Forms.TrackBar.SmallChange%2A> 屬性的值是縮圖依據按向左鍵或向右鍵次數來移動的位置數。  <xref:System.Windows.Forms.TrackBar.LargeChange%2A> 屬性的值是縮圖依據按 PAGE UP 或 PAGE DOWN 鍵次數，或在縮圖兩邊的滑動軸上按滑鼠的次數來移動的位置數。  
  
## 請參閱  
 <xref:System.Windows.Forms.TrackBar>   
 [TrackBar 控制項](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)