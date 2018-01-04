---
title: "如何：編碼和解碼 JPEG 影像"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding image formats [WPF]
- decoding JPEG images [WPF]
- encoding JPEG images [WPF]
- decoding image formats [WPF]
- JPEG decoding [WPF]
- JPEG encoding [WPF]
ms.assetid: b8cfde37-9f68-4911-a05e-51d8d7bdec7b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e982c09a27789bcf4a679fd9d237bf1a2b113f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a><span data-ttu-id="0658b-102">如何：編碼和解碼 JPEG 影像</span><span class="sxs-lookup"><span data-stu-id="0658b-102">How to: Encode and Decode a JPEG Image</span></span>
<span data-ttu-id="0658b-103">下列範例示範如何解碼和編碼[!INCLUDE[TLA#tla_jpeg](../../../../includes/tlasharptla-jpeg-md.md)]映像使用特定<xref:System.Windows.Media.Imaging.JpegBitmapDecoder>和<xref:System.Windows.Media.Imaging.JpegBitmapEncoder>物件。</span><span class="sxs-lookup"><span data-stu-id="0658b-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_jpeg](../../../../includes/tlasharptla-jpeg-md.md)] image using the specific <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> and <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0658b-104">範例</span><span class="sxs-lookup"><span data-stu-id="0658b-104">Example</span></span>  
 <span data-ttu-id="0658b-105">這個範例示範如何解碼[!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]映像使用<xref:System.Windows.Media.Imaging.JpegBitmapDecoder>從<xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="0658b-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)] image using a <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
 [!code-csharp[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
 [!code-vb[JpegBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="0658b-106">範例</span><span class="sxs-lookup"><span data-stu-id="0658b-106">Example</span></span>  
 <span data-ttu-id="0658b-107">此範例示範如何編碼<xref:System.Windows.Media.Imaging.BitmapSource>到[!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]映像使用<xref:System.Windows.Media.Imaging.JpegBitmapEncoder>。</span><span class="sxs-lookup"><span data-stu-id="0658b-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)] image using a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span></span>  
  
 [!code-cpp[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
 [!code-csharp[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
 [!code-vb[JpegBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="0658b-108">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="0658b-108">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0658b-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="0658b-109">See Also</span></span>  
 [<span data-ttu-id="0658b-110">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="0658b-110">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
