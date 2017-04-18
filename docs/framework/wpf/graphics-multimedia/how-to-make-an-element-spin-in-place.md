---
title: "如何：使項目就地旋轉 | Microsoft Docs"
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
  - "類別, DoubleAnimation"
  - "類別, RotateTransform"
  - "DoubleAnimation 類別"
  - "圖形, 旋轉項目"
  - "RotateTransform 類別"
  - "旋轉項目"
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使項目就地旋轉
本範例說明如何使用 <xref:System.Windows.Media.RotateTransform> 和 <xref:System.Windows.Media.Animation.DoubleAnimation> 來使項目旋轉。  
  
 下列範例會將 <xref:System.Windows.Media.RotateTransform> 套用至項目的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。  範例是使用 <xref:System.Windows.Media.Animation.DoubleAnimation>，讓 <xref:System.Windows.Media.RotateTransform> 的 <xref:System.Windows.Media.RotateTransform.Angle%2A> 產生變動以顯示動畫。  為了讓項目就地旋轉，範例會將項目的 <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 屬性設定為點 \(0.5, 0.5\)。  
  
## 範例  
 [!code-xml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 如需包含更多轉換範例的完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252) \(英文\)。  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)