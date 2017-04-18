---
title: "如何：編碼和解碼 TIFF 影像 | Microsoft Docs"
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
  - "解碼 TIFF 影像"
  - "編碼影像格式"
  - "編碼 TIFF 影像"
  - "TIFF 解碼"
  - "TIFF 編碼"
ms.assetid: 1dfe3209-fc73-40e6-ad1c-71c1c58b3364
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：編碼和解碼 TIFF 影像
下列範例示範如何使用特定的 <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> 和 <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> 物件，對 [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] 影像進行解碼和編碼。  
  
## 範例  
 此範例示範如何使用 <xref:System.Uri> 中的 <xref:System.Windows.Media.Imaging.TiffBitmapDecoder>，對 [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] 影像進行解碼。  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## 範例  
 此範例示範如何使用 <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>，將 <xref:System.Windows.Media.Imaging.BitmapSource> 編碼成 [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] 影像。  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## 請參閱  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)