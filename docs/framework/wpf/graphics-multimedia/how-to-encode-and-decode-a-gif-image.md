---
title: "操作說明：編碼和解碼 GIF 影像"
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
- encoding GIF images [WPF]
- encoding image formats [WPF]
- decoding GIF images [WPF]
- decoding image formats [WPF]
- GIF decoding [WPF]
- GIF encoding [WPF]
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d098faf45edade4a37a4d8a6004d1e7b8acbd86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="9bf16-102">操作說明：編碼和解碼 GIF 影像</span><span class="sxs-lookup"><span data-stu-id="9bf16-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="9bf16-103">下列範例示範如何解碼和編碼[!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)]映像使用特定<xref:System.Windows.Media.Imaging.GifBitmapDecoder>和<xref:System.Windows.Media.Imaging.GifBitmapEncoder>物件。</span><span class="sxs-lookup"><span data-stu-id="9bf16-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bf16-104">範例</span><span class="sxs-lookup"><span data-stu-id="9bf16-104">Example</span></span>  
 <span data-ttu-id="9bf16-105">這個範例示範如何解碼[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]映像使用<xref:System.Windows.Media.Imaging.GifBitmapDecoder>從<xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="9bf16-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9bf16-106">範例</span><span class="sxs-lookup"><span data-stu-id="9bf16-106">Example</span></span>  
 <span data-ttu-id="9bf16-107">此範例示範如何編碼<xref:System.Windows.Media.Imaging.BitmapSource>到[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]映像使用<xref:System.Windows.Media.Imaging.GifBitmapEncoder>。</span><span class="sxs-lookup"><span data-stu-id="9bf16-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9bf16-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="9bf16-108">See Also</span></span>  
 [<span data-ttu-id="9bf16-109">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="9bf16-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
