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
# <a name="how-to-encode-and-decode-a-tiff-image"></a>HOW TO：編碼和解碼 TIFF 影像
下列範例示範如何使用特定的 <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> 和 <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> 物件來解碼和編碼標記的影像檔案格式（TIFF）影像。  
  
## <a name="example"></a>範例  
 這個範例示範如何使用 <xref:System.Uri> 的 <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> 來解碼 TIFF 影像。  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a>範例  
 這個範例示範如何使用 <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>，將 <xref:System.Windows.Media.Imaging.BitmapSource> 編碼成 TIFF 影像。  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [影像處理概觀](imaging-overview.md)
