---
title: "如何：將 Visual 編碼為影像檔 | Microsoft Docs"
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
  - "編碼影像格式"
  - "影像檔案, 從視覺編碼"
  - "視覺效果, 編碼為影像檔"
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：將 Visual 編碼為影像檔
本範例示範如何用使用 <xref:System.Windows.Media.Imaging.RenderTargetBitmap> 和 <xref:System.Windows.Media.Imaging.PngBitmapEncoder>，將 <xref:System.Windows.Media.Visual> 物件編碼成影像檔。  
  
## 範例  
 <xref:System.Windows.Media.DrawingVisual> 是使用 <xref:System.Windows.Media.Imaging.BitmapImage> 和 <xref:System.Windows.Media.FormattedText> 建立的，接著會呈現為 <xref:System.Windows.Media.Imaging.RenderTargetBitmap>。  呈現的點陣圖會用來建立 <xref:System.Windows.Media.Imaging.BitmapFrame>，這會再加入到 <xref:System.Windows.Media.Imaging.PngBitmapEncoder>，以建立新的 [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] 檔案。  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 這個範例使用的是 <xref:System.Windows.Media.Imaging.PngBitmapEncoder>，不過任何衍生的 <xref:System.Windows.Media.Imaging.BitmapEncoder> 物件都可以用來建立影像檔。  
  
## 請參閱  
 <xref:System.Windows.Media.DrawingContext>   
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [使用 DrawingVisual 物件](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)