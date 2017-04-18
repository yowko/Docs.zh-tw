---
title: "如何：編碼和解碼 GIF 影像 | Microsoft Docs"
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
  - "解碼 GIF 影像"
  - "解碼影像格式"
  - "編碼 GIF 影像"
  - "編碼影像格式"
  - "GIF 解碼"
  - "GIF 編碼"
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：編碼和解碼 GIF 影像
下列範例示範如何使用特定的 <xref:System.Windows.Media.Imaging.GifBitmapDecoder> 和 <xref:System.Windows.Media.Imaging.GifBitmapEncoder> 物件，對 [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] 影像進行解碼和編碼。  
  
## 範例  
 此範例示範如何使用 <xref:System.IO.FileStream> 中的 <xref:System.Windows.Media.Imaging.GifBitmapDecoder>，對 [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] 影像進行解碼。  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## 範例  
 此範例示範如何使用 <xref:System.Windows.Media.Imaging.GifBitmapEncoder>，將 <xref:System.Windows.Media.Imaging.BitmapSource> 編碼成 [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] 影像。  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## 請參閱  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)