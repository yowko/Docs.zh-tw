---
title: "如何：編碼和解碼 BMP 影像 | Microsoft Docs"
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
  - "BMP 解碼"
  - "BMP 編碼"
  - "解碼 BMP 影像"
  - "解碼影像格式"
  - "編碼 BMP 影像"
  - "編碼影像格式"
ms.assetid: feb5ef27-28ac-40ab-bfc2-e0456990d32c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：編碼和解碼 BMP 影像
下列範例示範如何使用特定的 <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> 和 <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> 物件，對 [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)] 影像進行解碼和編碼。  
  
## 範例  
 此範例示範如何使用 <xref:System.Uri> 中的 <xref:System.Windows.Media.Imaging.BmpBitmapDecoder>，對 [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] 影像進行解碼。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## 範例  
 此範例示範如何使用 <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>，將 <xref:System.Windows.Media.Imaging.BitmapSource> 編碼成 [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] 影像。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## 請參閱  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)