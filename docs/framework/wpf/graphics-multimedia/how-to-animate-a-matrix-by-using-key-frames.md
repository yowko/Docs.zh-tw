---
title: "如何：使用主要畫面格建立矩陣的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格的 Matrix 屬性"
  - "主要畫面格, 建立 Matrix 屬性動畫"
  - "Matrix 屬性, 使用主要畫面格建立動畫"
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用主要畫面格建立矩陣的動畫
本範例說明如何使用主要畫面格，將 <xref:System.Windows.Media.MatrixTransform> 的 <xref:System.Windows.Media.MatrixTransform.Matrix%2A> 屬性顯示為動畫。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> 類別將 <xref:System.Windows.Media.MatrixTransform> 的 <xref:System.Windows.Media.MatrixTransform.Matrix%2A> 屬性顯示為動畫。  這個範例使用 <xref:System.Windows.Media.MatrixTransform> 物件轉換 <xref:System.Windows.Controls.Button> 的外觀和位置。  
  
 這個動畫使用 <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> 類別建立兩個主要畫面格，並以這兩個畫面格執行下列作業：  
  
1.  讓第一個 <xref:System.Windows.Media.Matrix> 在前 0.2 秒產生動畫效果。  此範例會變更 <xref:System.Windows.Media.Matrix> 的 <xref:System.Windows.Media.Matrix.M11%2A> 和 <xref:System.Windows.Media.Matrix.M12%2A> 屬性。  這項變更會讓按鈕產生延伸及傾斜的效果。  此範例也會變更 <xref:System.Windows.Media.Matrix.OffsetX%2A> 和 <xref:System.Windows.Media.Matrix.OffsetY%2A> 屬性，使按鈕的位置改變。  
  
2.  讓第二個 <xref:System.Windows.Media.Matrix> 在 1.0 秒內產生動畫效果。  按鈕會移到另一個位置，但是按鈕不會延伸也不會傾斜。  
  
3.  不斷重複動畫效果。  
  
> [!NOTE]
>  衍生自 <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> 物件的主要畫面格會在值之間建立突然的跳躍點 \(亦即動畫會變得不穩定\)。  
  
 [!code-xml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>   
 <xref:System.Windows.Media.MatrixTransform>   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)