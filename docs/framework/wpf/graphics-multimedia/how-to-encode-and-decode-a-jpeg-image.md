---
title: HOW TO：編碼和解碼 JPEG 影像
ms.date: 03/30/2017
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
ms.openlocfilehash: db42411f71e2934f3e5f86a06f434da220f1882e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603504"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a><span data-ttu-id="a1eca-102">HOW TO：編碼和解碼 JPEG 影像</span><span class="sxs-lookup"><span data-stu-id="a1eca-102">How to: Encode and decode a JPEG image</span></span>

<span data-ttu-id="a1eca-103">下列範例示範如何使用特定的 JPEG 影像的編碼和解碼<xref:System.Windows.Media.Imaging.JpegBitmapDecoder>和<xref:System.Windows.Media.Imaging.JpegBitmapEncoder>物件。</span><span class="sxs-lookup"><span data-stu-id="a1eca-103">The following examples show how to decode and encode a JPEG image using the specific <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> and <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objects.</span></span>  
  
## <a name="example---decode-a-jpeg-image"></a><span data-ttu-id="a1eca-104">範例-解碼 JPEG 影像</span><span class="sxs-lookup"><span data-stu-id="a1eca-104">Example - Decode a JPEG image</span></span>

<span data-ttu-id="a1eca-105">此範例示範如何解碼 JPEG 影像 using<xref:System.Windows.Media.Imaging.JpegBitmapDecoder>從<xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="a1eca-105">This example demonstrates how to decode a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a><span data-ttu-id="a1eca-106">範例-將編碼 JPEG 影像</span><span class="sxs-lookup"><span data-stu-id="a1eca-106">Example - Encode a JPEG image</span></span>

<span data-ttu-id="a1eca-107">此範例示範如何編碼<xref:System.Windows.Media.Imaging.BitmapSource>成 JPEG 影像使用<xref:System.Windows.Media.Imaging.JpegBitmapEncoder>。</span><span class="sxs-lookup"><span data-stu-id="a1eca-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a1eca-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1eca-108">See also</span></span>

- [<span data-ttu-id="a1eca-109">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="a1eca-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
