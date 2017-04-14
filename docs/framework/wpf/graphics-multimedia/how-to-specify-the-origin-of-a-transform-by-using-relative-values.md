---
title: "如何：使用相對值指定轉換的原點 | Microsoft Docs"
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
  - "圖形, 轉換的來源"
  - "轉換的來源"
  - "轉換, 來源"
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用相對值指定轉換的原點
本範例說明如何使用相對值指定套用到 <xref:System.Windows.FrameworkElement> 之 <xref:System.Windows.UIElement.RenderTransform%2A> 的原點。  
  
 當您使用 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性旋轉、縮放或[傾斜](GTMT) <xref:System.Windows.FrameworkElement> 時，預設設定會將轉換套用到項目左上角。  如果您要從項目的中心旋轉、縮放或傾斜，可以將轉換的中心設為項目的中心來因應。  不過，這方法需要知道項目的大小。  要將轉換套用到項目中心，更簡單的方式就是將項目的 <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 屬性設為 \(0.5, 0.5\)，而不是在轉換本身設定中心值。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.RotateTransform> 順時針旋轉 <xref:System.Windows.Controls.Button> 45 度。  由於範例沒有指定中心，按鈕會以點 \(0, 0\)，也就是左上角為中心旋轉。  <xref:System.Windows.Media.RotateTransform> 會套用到 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。  
  
 下圖顯示後面所接範例的轉換結果。  
  
 ![使用 RenderTransform 經過轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm\_RenderTransformWithDefaultCenter")  
使用 RenderTransform 屬性順時針旋轉 45 度  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 下列範例也使用 <xref:System.Windows.Media.RotateTransform> 順時針旋轉 <xref:System.Windows.Controls.Button> 45 度，不過，此範例會將按鈕的 <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 設為 \(0.5, 0.5\)。  因此，旋轉會套用到按鈕的中心，而非左上角。  
  
 下圖顯示後面所接範例的轉換結果。  
  
 ![對其中心轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm\_RenderTransformRelativeCenter")  
使用 RenderTransform 屬性以 RenderTransformOrigin 為 \(0.5, 0.5\) 旋轉 45 度  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 如需轉換 <xref:System.Windows.FrameworkElement> 物件的詳細資訊，請參閱[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.Transform>   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)