---
title: "如何：轉換筆刷 | Microsoft Docs"
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
  - "筆刷, 旋轉內容"
  - "筆刷, Transform 屬性"
  - "旋轉筆刷內容"
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：轉換筆刷
本範例說明如何使用 <xref:System.Windows.Media.Brush> 物件的兩個轉換屬性：<xref:System.Windows.Media.Brush.RelativeTransform%2A> 和 <xref:System.Windows.Media.Brush.Transform%2A>，來轉換物件。  
  
 下列範例會使用 <xref:System.Windows.Media.RotateTransform> 旋轉 <xref:System.Windows.Media.ImageBrush> 的內容 45 度。  
  
 下圖顯示的 <xref:System.Windows.Media.ImageBrush> 分別是沒有 <xref:System.Windows.Media.RotateTransform>、將 <xref:System.Windows.Media.RotateTransform> 套用到 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性，以及將 <xref:System.Windows.Media.RotateTransform> 套用到 <xref:System.Windows.Media.Brush.Transform%2A> 屬性。  
  
 ![筆刷的 RelativeTransform 和 Transform 設定](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk\_graphicsmm\_transformandrelativetransform")  
  
## 範例  
 第一個範例將 <xref:System.Windows.Media.RotateTransform> 套用到 <xref:System.Windows.Media.ImageBrush> 的 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性。  <xref:System.Windows.Media.RotateTransform> 物件的 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 屬性都設為 0.5，這是此內容中心點的相對座標。  因此，<xref:System.Windows.Media.ImageBrush> 內容會以其中心進行旋轉。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 第二個範例也將 <xref:System.Windows.Media.RotateTransform> 套用到 <xref:System.Windows.Media.ImageBrush>，不過，這個範例使用 <xref:System.Windows.Media.Brush.Transform%2A> 屬性，而非 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 屬性。  
  
 為了以中心為準旋轉筆刷，此範例將 <xref:System.Windows.Media.RotateTransform> 物件的 <xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 屬性設為絕對座標。  由於筆刷會繪製 175 x 90 [像素](GTMT)大的矩形，矩形的中心點為 \(87.5, 45\)。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 如需 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 和 <xref:System.Windows.Media.Brush.Transform%2A> 屬性運作方式的描述，請參閱[筆刷轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)。  
  
 如需完整範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973) \(英文\)。  如需筆刷的詳細資訊，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。  
  
## 請參閱  
 [筆刷轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)   
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)