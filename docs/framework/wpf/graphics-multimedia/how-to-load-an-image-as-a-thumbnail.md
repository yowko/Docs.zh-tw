---
title: 如何：將影像當做縮圖載入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: 349a602a10b89931701e24334bf5ac5536f26400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562319"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="a24c9-102">如何：將影像當做縮圖載入</span><span class="sxs-lookup"><span data-stu-id="a24c9-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="a24c9-103">下列範例顯示如何載入<xref:System.Windows.Controls.Image>縮圖，以節省記憶體的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a24c9-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a24c9-104">範例</span><span class="sxs-lookup"><span data-stu-id="a24c9-104">Example</span></span>  
 <span data-ttu-id="a24c9-105">下列範例會設定<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>屬性<xref:System.Windows.Media.Imaging.BitmapImage>中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]降低載入影像時所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a24c9-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="a24c9-106">範例</span><span class="sxs-lookup"><span data-stu-id="a24c9-106">Example</span></span>  
 <span data-ttu-id="a24c9-107">下列範例會設定<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>屬性<xref:System.Windows.Media.Imaging.BitmapImage>程式碼是為了減少載入影像時所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a24c9-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="a24c9-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a24c9-108">See Also</span></span>  
 [<span data-ttu-id="a24c9-109">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="a24c9-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
