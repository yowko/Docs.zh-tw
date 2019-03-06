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
ms.openlocfilehash: 0f64ef8537f22ea996cbcf274885de1f3968267a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373786"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a>HOW TO：編碼和解碼 JPEG 影像

下列範例示範如何使用特定的 JPEG 影像的編碼和解碼<xref:System.Windows.Media.Imaging.JpegBitmapDecoder>和<xref:System.Windows.Media.Imaging.JpegBitmapEncoder>物件。  
  
## <a name="example---decode-a-jpeg-image"></a>範例-解碼 JPEG 影像

此範例示範如何解碼 JPEG 影像 using<xref:System.Windows.Media.Imaging.JpegBitmapDecoder>從<xref:System.IO.FileStream>。  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a>範例-將編碼 JPEG 影像

此範例示範如何編碼<xref:System.Windows.Media.Imaging.BitmapSource>成 JPEG 影像使用<xref:System.Windows.Media.Imaging.JpegBitmapEncoder>。  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [影像處理概觀](imaging-overview.md)
