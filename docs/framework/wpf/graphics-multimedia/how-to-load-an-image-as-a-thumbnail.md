---
title: HOW TO：將影像當做縮圖載入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: 0b5435e9b06f37dae7dc762e9035b1eca8156ca6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353384"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a>HOW TO：將影像當做縮圖載入
下列範例示範如何載入<xref:System.Windows.Controls.Image>當做縮圖以節省記憶體的應用程式。  
  
## <a name="example"></a>範例  
 下列範例會設定<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>的屬性<xref:System.Windows.Media.Imaging.BitmapImage>在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]以降低載入影像時所需的記憶體。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>範例  
 下列範例會設定<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>屬性<xref:System.Windows.Media.Imaging.BitmapImage>中程式碼，以降低載入影像時所需的記憶體。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>另請參閱
- [影像處理概觀](imaging-overview.md)
