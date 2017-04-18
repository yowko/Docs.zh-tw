---
title: "如何：傾斜項目 | Microsoft Docs"
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
  - "類別, SkewTransform"
  - "圖形, 傾斜項目"
  - "傾斜項目"
  - "SkewTransform 類別"
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：傾斜項目
本範例說明如何使用 <xref:System.Windows.Media.SkewTransform> 傾斜項目。  [傾斜](GTMT)也稱為切變，這種轉換會以非一致的方式延伸座標空間。  <xref:System.Windows.Media.SkewTransform> 的常見使用方式就是在 [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] 物件中模擬[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]深度。  
  
 使用 <xref:System.Windows.Media.SkewTransform.CenterX%2A> 和 <xref:System.Windows.Media.SkewTransform.CenterY%2A> 屬性指定 <xref:System.Windows.Media.SkewTransform> 的中心點。  
  
 使用 <xref:System.Windows.Media.SkewTransform.AngleX%2A> 和 <xref:System.Windows.Media.SkewTransform.AngleY%2A> 屬性指定 X 軸和 Y 軸的傾斜角度，將目前的座標系統沿著這些軸傾斜。  
  
 若要預測傾斜轉換的效果，可以將 <xref:System.Windows.Media.SkewTransform.AngleX%2A> 想成是相對於原始座標系統傾斜 X 軸值。  因此，若 <xref:System.Windows.Media.SkewTransform.AngleX%2A> 為 30，Y 軸會穿過原點旋轉 30 度，然後從該原點傾斜 X 軸的值 30 度。  同樣地，若 <xref:System.Windows.Media.SkewTransform.AngleY%2A> 為 30，會將圖案的 Y 軸值從原點開始傾斜 30 度。  請注意，這與轉移 \(移動\) 座標系統的 X 軸或 Y 軸 30 度的效果不同。  
  
 下列範例會將 45 度的水平傾斜套用到 <xref:System.Windows.Shapes.Rectangle>，從中心點 \(0,0\) 開始。  
  
## 範例  
 [!code-xml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 下列範例會將 45 度的水平傾斜套用到 <xref:System.Windows.Shapes.Rectangle>，從中心點 \(25,25\) 開始。  
  
 [!code-xml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 下列範例會將 45 度的垂直傾斜套用到 <xref:System.Windows.Shapes.Rectangle>，從中心點 \(25,25\) 開始。  
  
 [!code-xml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 下圖顯示本範例所使用的不同傾斜。  
  
 ![SkewTransform 範例](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.png "img\_wcpsdk\_graphicsmm\_skewtransformexample")  
三個 SkewTransform 範例示意圖  
  
 如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.SkewTransform>   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)