---
title: "如何：縮放項目 | Microsoft Docs"
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
  - "類別, ScaleTransform"
  - "圖形, 縮放比例項目"
  - "ScaleTransform 類別"
  - "縮放比例, 項目"
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：縮放項目
本範例顯示如何使用 <xref:System.Windows.Media.ScaleTransform> 縮放項目。  
  
 請使用 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 和 <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 屬性，以您指定的因數調整項目的大小。  例如，如果 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 值為 1.5，會將項目放大成原始寬度的 150%。  如果 <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 值為 0.5，則會將物件的高度壓縮為 50%。  
  
 請使用 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> 和 <xref:System.Windows.Media.ScaleTransform.CenterY%2A> 屬性來指定縮放作業的中心點。  根據預設，<xref:System.Windows.Media.ScaleTransform> 會以點 \(0,0\) 為中心，這也就是矩形的左上角。  這會有移動項目的效果，而且也會讓它看起來更大，因為當您套用 <xref:System.Windows.Media.Transform> 時，就變更了物件所在的座標空間。  
  
 下列範例會使用 <xref:System.Windows.Media.ScaleTransform> 將 50 x 50 的 <xref:System.Windows.Shapes.Rectangle> 放大成兩倍。  <xref:System.Windows.Media.ScaleTransform> 的 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> 和 <xref:System.Windows.Media.ScaleTransform.CenterY%2A> 的值都是 0 \(預設值\)。  
  
## 範例  
 [!code-xml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 通常，您會將 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> 和 <xref:System.Windows.Media.ScaleTransform.CenterY%2A> 設為要縮放之物件的中心：\(<xref:System.Windows.FrameworkElement.Width%2A>\/2, <xref:System.Windows.FrameworkElement.Height%2A>\/2\)。  
  
 下列範例顯示另一個放大兩倍的 <xref:System.Windows.Shapes.Rectangle>，不過，這次 <xref:System.Windows.Media.ScaleTransform> 的 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> 和 <xref:System.Windows.Media.ScaleTransform.CenterY%2A> 的值為 25，也就是矩形的中心點。  
  
 [!code-xml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 下圖顯示這兩個 <xref:System.Windows.Media.ScaleTransform> 作業的差別。  虛線顯示的是矩形在縮放之前的大小和位置。  
  
 ![採用不同中心點的 2 倍縮放](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.png "wcpsdk\_graphicsmm\_scalecenter")  
ScaleX 和 ScaleY 值完全相同但中心點不同的兩個 ScaleTransform 作業  
  
 如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.ScaleTransform>   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)