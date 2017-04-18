---
title: "如何：編碼和解碼 WDP 影像 | Microsoft Docs"
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
  - "解碼 WDP 影像"
  - "編碼影像格式"
  - "編碼 WDP 影像"
  - "WDP 解碼"
  - "WDP 編碼"
ms.assetid: 911777d1-516b-49db-a87b-b54e31b18532
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：編碼和解碼 WDP 影像
下列範例示範如何使用特定的 <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> 和 <xref:System.Windows.Media.Imaging.WmpBitmapEncoder> 物件，對 [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)] 影像進行解碼和編碼。  
  
## 範例  
 此範例示範如何使用 <xref:System.Uri> 中的 <xref:System.Windows.Media.Imaging.WmpBitmapDecoder>，對 [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] 影像進行解碼。  
  
 [!code-cpp[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#1)]
 [!code-csharp[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#1)]
 [!code-vb[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#1)]  
  
## 範例  
 此範例示範如何使用 <xref:System.Windows.Media.Imaging.WmpBitmapEncoder>，將 <xref:System.Windows.Media.Imaging.BitmapSource> 編碼成 [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] 影像。  
  
 [!code-cpp[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#4)]
 [!code-csharp[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#4)]
 [!code-vb[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#4)]  
  
## 請參閱  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)