---
title: 如何：編碼和解碼 TIFF 影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TIFF encoding [WPF]
- encoding TIFF images [WPF]
- encoding image formats [WPF]
- decoding TIFF images [WPF]
- decoding image formats [WPF]
- TIFF decoding [WPF]
ms.assetid: 1dfe3209-fc73-40e6-ad1c-71c1c58b3364
ms.openlocfilehash: 94bea19b997f0ee266176ba985a3cd8ff6781cfd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encode-and-decode-a-tiff-image"></a><span data-ttu-id="a90b9-102">如何：編碼和解碼 TIFF 影像</span><span class="sxs-lookup"><span data-stu-id="a90b9-102">How to: Encode and Decode a TIFF Image</span></span>
<span data-ttu-id="a90b9-103">下列範例示範如何解碼和編碼[!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)]映像使用特定<xref:System.Windows.Media.Imaging.TiffBitmapDecoder>和<xref:System.Windows.Media.Imaging.TiffBitmapEncoder>物件。</span><span class="sxs-lookup"><span data-stu-id="a90b9-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] image using the specific <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> and <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a90b9-104">範例</span><span class="sxs-lookup"><span data-stu-id="a90b9-104">Example</span></span>  
 <span data-ttu-id="a90b9-105">這個範例示範如何解碼[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]映像使用<xref:System.Windows.Media.Imaging.TiffBitmapDecoder>從<xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="a90b9-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="a90b9-106">範例</span><span class="sxs-lookup"><span data-stu-id="a90b9-106">Example</span></span>  
 <span data-ttu-id="a90b9-107">此範例示範如何編碼<xref:System.Windows.Media.Imaging.BitmapSource>到[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]映像使用<xref:System.Windows.Media.Imaging.TiffBitmapEncoder>。</span><span class="sxs-lookup"><span data-stu-id="a90b9-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a90b9-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a90b9-108">See Also</span></span>  
 [<span data-ttu-id="a90b9-109">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="a90b9-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
