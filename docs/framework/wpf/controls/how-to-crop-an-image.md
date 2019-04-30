---
title: HOW TO：裁剪影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
ms.openlocfilehash: e672c7e24ec4db2d6424fa0b611cb1c135cf8eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053388"
---
# <a name="how-to-crop-an-image"></a><span data-ttu-id="94fd4-102">HOW TO：裁剪影像</span><span class="sxs-lookup"><span data-stu-id="94fd4-102">How to: Crop an Image</span></span>
<span data-ttu-id="94fd4-103">此範例示範如何裁剪影像使用<xref:System.Windows.Media.Imaging.CroppedBitmap>。</span><span class="sxs-lookup"><span data-stu-id="94fd4-103">This example shows how to crop an image using <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span></span>  
  
 <span data-ttu-id="94fd4-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> 是主要用於編碼影像的裁剪的版本時儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="94fd4-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> is primarily used when encoding a cropped version of an image to save out to a file.</span></span> <span data-ttu-id="94fd4-105">若要裁剪的影像顯示用途，請參閱[How to:建立裁剪區域](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90))主題。</span><span class="sxs-lookup"><span data-stu-id="94fd4-105">To crop an image for display purposes see the [How to: Create a Clip Region](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90)) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94fd4-106">範例</span><span class="sxs-lookup"><span data-stu-id="94fd4-106">Example</span></span>  
 <span data-ttu-id="94fd4-107">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]下面的範例中使用的資源進行定義。</span><span class="sxs-lookup"><span data-stu-id="94fd4-107">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] defines resources used within the samples below.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 <span data-ttu-id="94fd4-108">下列範例會建立映像使用<xref:System.Windows.Media.Imaging.CroppedBitmap>做為其來源。</span><span class="sxs-lookup"><span data-stu-id="94fd4-108">The following example creates an image using a <xref:System.Windows.Media.Imaging.CroppedBitmap> as its source.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <span data-ttu-id="94fd4-109"><xref:System.Windows.Media.Imaging.CroppedBitmap>也可用來當做另一個來源<xref:System.Windows.Media.Imaging.CroppedBitmap>，鏈結裁剪。</span><span class="sxs-lookup"><span data-stu-id="94fd4-109">The <xref:System.Windows.Media.Imaging.CroppedBitmap> can also be used as the source of another <xref:System.Windows.Media.Imaging.CroppedBitmap>, chaining the cropping.</span></span> <span data-ttu-id="94fd4-110">請注意，<xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A>使用相對於來源點陣圖和不初始映像將裁剪的值。</span><span class="sxs-lookup"><span data-stu-id="94fd4-110">Note that the <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> uses values that are relative to the source cropped bitmap and not the initial image.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a><span data-ttu-id="94fd4-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94fd4-111">See also</span></span>

- <span data-ttu-id="94fd4-112">[如何：建立裁剪區域](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="94fd4-112">[How to: Create a Clip Region](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90))</span></span>
