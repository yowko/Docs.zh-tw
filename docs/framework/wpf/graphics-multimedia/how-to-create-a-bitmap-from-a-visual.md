---
title: "如何：從 Visual 建立點陣圖 | Microsoft Docs"
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
  - "點陣圖, 視覺呈現"
  - "視覺效果, 呈現為點陣圖"
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：從 Visual 建立點陣圖
本範例顯示如何從 <xref:System.Windows.Media.Visual> 建立點陣圖。  <xref:System.Windows.Media.DrawingVisual> 會使用 <xref:System.Windows.Media.FormattedText> 呈現。  <xref:System.Windows.Media.Visual> 接著再呈現在 <xref:System.Windows.Media.Imaging.RenderTargetBitmap>，建立所指定文字的點陣圖。  
  
## 範例  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## 請參閱  
 <xref:System.Windows.Media.DrawingContext>   
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [使用 DrawingVisual 物件](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)