---
title: "如何：編碼和解碼 PNG 影像 | Microsoft Docs"
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
  - "解碼影像格式"
  - "解碼 PNG 影像"
  - "編碼影像格式"
  - "編碼 PNG 影像"
  - "PNG 解碼"
  - "PNG 編碼"
ms.assetid: 3d31d186-af73-47f0-b5a7-c26ae46409a6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：編碼和解碼 PNG 影像
下列範例示範如何使用特定的 <xref:System.Windows.Media.Imaging.PngBitmapDecoder> 和 <xref:System.Windows.Media.Imaging.PngBitmapEncoder> 物件，對 [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] 影像進行解碼和編碼。  
  
## 範例  
 此範例示範如何使用 <xref:System.IO.FileStream> 中的 <xref:System.Windows.Media.Imaging.PngBitmapDecoder>，對 [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] 影像進行解碼。  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## 範例  
 此範例示範如何使用 <xref:System.Windows.Media.Imaging.PngBitmapEncoder>，將 <xref:System.Windows.Media.Imaging.BitmapSource> 編碼成 [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] 影像。  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## 請參閱  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)