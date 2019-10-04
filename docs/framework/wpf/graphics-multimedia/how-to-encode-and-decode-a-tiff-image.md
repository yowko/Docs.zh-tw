---
title: HOW TO：編碼和解碼 TIFF 影像
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
ms.openlocfilehash: 173a30e785b16a3617b82b771c463083356d6e6e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835296"
---
# <a name="how-to-encode-and-decode-a-tiff-image"></a><span data-ttu-id="00ad5-102">HOW TO：編碼和解碼 TIFF 影像</span><span class="sxs-lookup"><span data-stu-id="00ad5-102">How to: Encode and Decode a TIFF Image</span></span>
<span data-ttu-id="00ad5-103">下列範例示範如何使用特定的 <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> 和 <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> 物件來解碼和編碼標記的影像檔案格式（TIFF）影像。</span><span class="sxs-lookup"><span data-stu-id="00ad5-103">The following examples show how to decode and encode a Tagged Image File Format (TIFF) image using the specific <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> and <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00ad5-104">範例</span><span class="sxs-lookup"><span data-stu-id="00ad5-104">Example</span></span>  
 <span data-ttu-id="00ad5-105">這個範例示範如何使用 <xref:System.Uri> 的 <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> 來解碼 TIFF 影像。</span><span class="sxs-lookup"><span data-stu-id="00ad5-105">This example demonstrates how to decode a TIFF image using a <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="00ad5-106">範例</span><span class="sxs-lookup"><span data-stu-id="00ad5-106">Example</span></span>  
 <span data-ttu-id="00ad5-107">這個範例示範如何使用 <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>，將 <xref:System.Windows.Media.Imaging.BitmapSource> 編碼成 TIFF 影像。</span><span class="sxs-lookup"><span data-stu-id="00ad5-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a TIFF image using a <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="00ad5-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00ad5-108">See also</span></span>

- [<span data-ttu-id="00ad5-109">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="00ad5-109">Imaging Overview</span></span>](imaging-overview.md)
