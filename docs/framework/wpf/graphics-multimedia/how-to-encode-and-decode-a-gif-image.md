---
title: HOW TO：編碼和解碼 GIF 影像
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
ms.openlocfilehash: 9b13ac8021b6f2d25209a89ff2ff9b4bb7531ad3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562462"
---
# <a name="how-to-encode-and-decode-a-gif-image"></a>HOW TO：編碼和解碼 GIF 影像
下列範例示範如何編碼和解碼[!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)]映像使用特定<xref:System.Windows.Media.Imaging.GifBitmapDecoder>和<xref:System.Windows.Media.Imaging.GifBitmapEncoder>物件。  
  
## <a name="example"></a>範例  
 此範例示範如何解碼[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]映像使用<xref:System.Windows.Media.Imaging.GifBitmapDecoder>從<xref:System.IO.FileStream>。  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a>範例  
 此範例示範如何編碼<xref:System.Windows.Media.Imaging.BitmapSource>成[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]映像使用<xref:System.Windows.Media.Imaging.GifBitmapEncoder>。  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>另請參閱
- [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
