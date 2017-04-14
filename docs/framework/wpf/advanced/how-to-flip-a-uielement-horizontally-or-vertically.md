---
title: "如何：水平或垂直翻轉 UIElement | Microsoft Docs"
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
  - "翻轉 UIElements"
  - "UIElements, 翻轉"
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：水平或垂直翻轉 UIElement
本範例示範如何使用 <xref:System.Windows.Media.ScaleTransform> 水平或垂直翻轉 <xref:System.Windows.UIElement>。  在這個範例中，<xref:System.Windows.Controls.Button> 控制項 \(型別為 <xref:System.Windows.UIElement>\) 會藉由套用 <xref:System.Windows.Media.ScaleTransform> 至其 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性來翻轉。  
  
## 範例  
 下圖顯示要翻轉的按鈕。  
  
 ![不含轉換的按鈕](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.png "graphicsmm\_buttonflipbeforeflip")  
要翻轉的 UIElement  
  
 以下是建立按鈕的程式碼。  
  
 [!code-xml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## 範例  
 若要水平翻轉按鈕，請建立 <xref:System.Windows.Media.ScaleTransform> 並將其 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 屬性設為 \-1。  將 <xref:System.Windows.Media.ScaleTransform> 套用到按鈕的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。  
  
 [!code-xml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![對 &#40;0,0&#41; 水平翻轉的按鈕](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.png "graphicsmm\_buttonfliphorizontalflip\_displaced")  
套用 ScaleTransform 之後的按鈕  
  
## 範例  
 如上圖所示，按鈕不但翻轉，也移動了。  這是因為按鈕是以左上角為中心翻轉。  若要就地翻轉按鈕，請將 <xref:System.Windows.Media.ScaleTransform> 套用到其中心點，而非邊角。  要將 <xref:System.Windows.Media.ScaleTransform> 套用到按鈕中心點，最簡單的方式就是將按鈕的 <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 屬性設為 0.5, 0.5。  
  
 [!code-xml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![對其中心水平翻轉的按鈕](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.png "graphicsmm\_buttonfliphorizontalflip\_inplace")  
RenderTransformOrigin 設為 0.5, 0.5 的按鈕  
  
## 範例  
 若要垂直翻轉按鈕，請設定 <xref:System.Windows.Media.ScaleTransform> 物件的 <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 屬性，而非 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 屬性。  
  
 [!code-xml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![對其中心垂直翻轉的按鈕](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.png "graphicsmm\_buttonflipverticalflip\_inplace")  
垂直翻轉的按鈕  
  
## 請參閱  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)