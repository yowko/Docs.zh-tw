---
title: "如何：編碼和解碼 PNG 影像"
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
- PNG encoding [WPF]
- decoding PNG images [WPF]
- PNG decoding [WPF]
- encoding image formats [WPF]
- decoding image formats [WPF]
- encoding PNG images [WPF]
ms.assetid: 3d31d186-af73-47f0-b5a7-c26ae46409a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fa304515e508fab246a6946c5a8026369cda250
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-encode-and-decode-a-png-image"></a><span data-ttu-id="a75d4-102">如何：編碼和解碼 PNG 影像</span><span class="sxs-lookup"><span data-stu-id="a75d4-102">How to: Encode and Decode a PNG Image</span></span>
<span data-ttu-id="a75d4-103">下列範例示範如何解碼和編碼[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]映像使用特定<xref:System.Windows.Media.Imaging.PngBitmapDecoder>和<xref:System.Windows.Media.Imaging.PngBitmapEncoder>物件。</span><span class="sxs-lookup"><span data-stu-id="a75d4-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] image using the specific <xref:System.Windows.Media.Imaging.PngBitmapDecoder> and <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a75d4-104">範例</span><span class="sxs-lookup"><span data-stu-id="a75d4-104">Example</span></span>  
 <span data-ttu-id="a75d4-105">這個範例示範如何解碼[!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]映像使用<xref:System.Windows.Media.Imaging.PngBitmapDecoder>從<xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="a75d4-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="a75d4-106">範例</span><span class="sxs-lookup"><span data-stu-id="a75d4-106">Example</span></span>  
 <span data-ttu-id="a75d4-107">此範例示範如何編碼<xref:System.Windows.Media.Imaging.BitmapSource>到[!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]映像使用<xref:System.Windows.Media.Imaging.PngBitmapEncoder>。</span><span class="sxs-lookup"><span data-stu-id="a75d4-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a75d4-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="a75d4-108">See Also</span></span>  
 [<span data-ttu-id="a75d4-109">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="a75d4-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
