---
title: HOW TO：將影像作為縮圖載入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: f984293a395e925368b20cef6aa0cd902bd6fc15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134039"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="68e87-102">HOW TO：將影像作為縮圖載入</span><span class="sxs-lookup"><span data-stu-id="68e87-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="68e87-103">下列範例示範如何載入<xref:System.Windows.Controls.Image>當做縮圖以節省記憶體的應用程式。</span><span class="sxs-lookup"><span data-stu-id="68e87-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68e87-104">範例</span><span class="sxs-lookup"><span data-stu-id="68e87-104">Example</span></span>  
 <span data-ttu-id="68e87-105">下列範例會設定<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>的屬性<xref:System.Windows.Media.Imaging.BitmapImage>在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]以降低載入影像時所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="68e87-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="68e87-106">範例</span><span class="sxs-lookup"><span data-stu-id="68e87-106">Example</span></span>  
 <span data-ttu-id="68e87-107">下列範例會設定<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>屬性<xref:System.Windows.Media.Imaging.BitmapImage>中程式碼，以降低載入影像時所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="68e87-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="68e87-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68e87-108">See also</span></span>

- [<span data-ttu-id="68e87-109">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="68e87-109">Imaging Overview</span></span>](imaging-overview.md)
