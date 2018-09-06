---
title: 如何：裁剪影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
ms.openlocfilehash: 189cb92d581ccc9209ebdb4de18487951d17818a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779980"
---
# <a name="how-to-crop-an-image"></a><span data-ttu-id="c8071-102">如何：裁剪影像</span><span class="sxs-lookup"><span data-stu-id="c8071-102">How to: Crop an Image</span></span>
<span data-ttu-id="c8071-103">此範例示範如何裁剪影像使用<xref:System.Windows.Media.Imaging.CroppedBitmap>。</span><span class="sxs-lookup"><span data-stu-id="c8071-103">This example shows how to crop an image using <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span></span>  
  
 <span data-ttu-id="c8071-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> 是主要用於編碼影像的裁剪的版本時儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="c8071-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> is primarily used when encoding a cropped version of an image to save out to a file.</span></span> <span data-ttu-id="c8071-105">若要裁剪的影像顯示用途，請參閱[建立的裁剪區域](https://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376)主題。</span><span class="sxs-lookup"><span data-stu-id="c8071-105">To crop an image for display purposes see the [Create a Clip Region](https://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8071-106">範例</span><span class="sxs-lookup"><span data-stu-id="c8071-106">Example</span></span>  
 <span data-ttu-id="c8071-107">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]下面的範例中使用的資源進行定義。</span><span class="sxs-lookup"><span data-stu-id="c8071-107">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] defines resources used within the samples below.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 <span data-ttu-id="c8071-108">下列範例會建立映像使用<xref:System.Windows.Media.Imaging.CroppedBitmap>做為其來源。</span><span class="sxs-lookup"><span data-stu-id="c8071-108">The following example creates an image using a <xref:System.Windows.Media.Imaging.CroppedBitmap> as its source.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <span data-ttu-id="c8071-109"><xref:System.Windows.Media.Imaging.CroppedBitmap>也可用來當做另一個來源<xref:System.Windows.Media.Imaging.CroppedBitmap>，鏈結裁剪。</span><span class="sxs-lookup"><span data-stu-id="c8071-109">The <xref:System.Windows.Media.Imaging.CroppedBitmap> can also be used as the source of another <xref:System.Windows.Media.Imaging.CroppedBitmap>, chaining the cropping.</span></span> <span data-ttu-id="c8071-110">請注意，<xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A>使用相對於來源點陣圖和不初始映像將裁剪的值。</span><span class="sxs-lookup"><span data-stu-id="c8071-110">Note that the <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> uses values that are relative to the source cropped bitmap and not the initial image.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a><span data-ttu-id="c8071-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8071-111">See Also</span></span>  
 [<span data-ttu-id="c8071-112">建立裁剪區域</span><span class="sxs-lookup"><span data-stu-id="c8071-112">Create a Clip Region</span></span>](https://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376)
