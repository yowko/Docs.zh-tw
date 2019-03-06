---
title: HOW TO：編碼和解碼 WDP 影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WDP encoding [WPF]
- WDP decoding [WPF]
- encoding image formats [WPF]
- decoding WDP images [WPF]
- decoding image formats [WPF]
- encoding WDP images [WPF]
ms.assetid: 911777d1-516b-49db-a87b-b54e31b18532
ms.openlocfilehash: a9a65c0505b5fd6ad4aac31108a01d5f83f8fe91
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356919"
---
# <a name="how-to-encode-and-decode-a-wdp-image"></a>HOW TO：編碼和解碼 WDP 影像
下列範例示範如何編碼和解碼[!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)]映像使用特定<xref:System.Windows.Media.Imaging.WmpBitmapDecoder>和<xref:System.Windows.Media.Imaging.WmpBitmapEncoder>物件。  
  
## <a name="example"></a>範例  
 此範例示範如何解碼[!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)]映像使用<xref:System.Windows.Media.Imaging.WmpBitmapDecoder>從<xref:System.Uri>。  
  
 [!code-cpp[WdpBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#1)]
 [!code-csharp[WdpBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#1)]
 [!code-vb[WdpBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#1)]  
  
## <a name="example"></a>範例  
 此範例示範如何編碼<xref:System.Windows.Media.Imaging.BitmapSource>成[!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)]映像使用<xref:System.Windows.Media.Imaging.WmpBitmapEncoder>。  
  
 [!code-cpp[WdpBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#4)]
 [!code-csharp[WdpBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#4)]
 [!code-vb[WdpBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>另請參閱
- [影像處理概觀](imaging-overview.md)
