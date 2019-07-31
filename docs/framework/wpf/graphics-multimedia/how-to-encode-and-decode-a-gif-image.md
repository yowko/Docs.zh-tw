---
title: 作法：編碼和解碼 GIF 影像
ms.date: 03/30/2017
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
ms.openlocfilehash: ec509a03d95e5f72af0b1f362e253799b07edc1f
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671684"
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="58b8d-102">HOW TO：編碼和解碼 GIF 影像</span><span class="sxs-lookup"><span data-stu-id="58b8d-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="58b8d-103">下列範例示範如何使用特定<xref:System.Windows.Media.Imaging.GifBitmapDecoder>的和<xref:System.Windows.Media.Imaging.GifBitmapEncoder>物件, 對圖形交換格式 (GIF) 影像進行解碼和編碼。</span><span class="sxs-lookup"><span data-stu-id="58b8d-103">The following examples show how to decode and encode a Graphics Interchange Format (GIF) image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58b8d-104">範例</span><span class="sxs-lookup"><span data-stu-id="58b8d-104">Example</span></span>  
 <span data-ttu-id="58b8d-105">這個範例示範如何使用<xref:System.Windows.Media.Imaging.GifBitmapDecoder> <xref:System.IO.FileStream>從來解碼 GIF 影像。</span><span class="sxs-lookup"><span data-stu-id="58b8d-105">This example demonstrates how to decode a GIF image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="58b8d-106">範例</span><span class="sxs-lookup"><span data-stu-id="58b8d-106">Example</span></span>  
 <span data-ttu-id="58b8d-107">這個範例示範如何<xref:System.Windows.Media.Imaging.BitmapSource> <xref:System.Windows.Media.Imaging.GifBitmapEncoder>使用將編碼成 GIF 影像。</span><span class="sxs-lookup"><span data-stu-id="58b8d-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a GIF image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="58b8d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58b8d-108">See also</span></span>

- [<span data-ttu-id="58b8d-109">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="58b8d-109">Imaging Overview</span></span>](imaging-overview.md)
