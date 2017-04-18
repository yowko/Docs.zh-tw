---
title: "如何：建立反映 | Microsoft Docs"
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
  - "筆刷, 建立反映"
  - "建立反映"
  - "反映, 建立"
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：建立反映
本範例說明如何使用 <xref:System.Windows.Media.VisualBrush> 建立反映。  由於 <xref:System.Windows.Media.VisualBrush> 可以顯示現有的圖形，您可以用它來產生有趣的視覺效果，例如反射和放大。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.VisualBrush> 來建立包含幾個項目之 <xref:System.Windows.Controls.Border> 的反映。  下圖顯示的是這個範例產生的輸出。  
  
 ![反映後的 Visual 物件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.png "graphicsmm\_visualbrush\_reflection\_small")  
反映的 Visual 物件  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 如需完整範例，包括說明如何放大螢幕某些區域以及如何建立反映的範例，請參閱 [VisualBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160049) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.VisualBrush>   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)