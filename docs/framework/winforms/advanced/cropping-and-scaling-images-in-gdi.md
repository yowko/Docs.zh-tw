---
title: "在 GDI+ 中裁剪和縮放影像"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0bbe7ac4b8c541ea76392f94f538e41816cf5c3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="72502-102">在 GDI+ 中裁剪和縮放影像</span><span class="sxs-lookup"><span data-stu-id="72502-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="72502-103">您可以使用<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>繪製及定位向量影像和點陣影像的類別。</span><span class="sxs-lookup"><span data-stu-id="72502-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="72502-104"><xref:System.Drawing.Graphics.DrawImage%2A>是多載的方法，因此沒有提供引數的數種方式。</span><span class="sxs-lookup"><span data-stu-id="72502-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="72502-105">DrawImage 變化</span><span class="sxs-lookup"><span data-stu-id="72502-105">DrawImage Variations</span></span>  
 <span data-ttu-id="72502-106">其中一個變化<xref:System.Drawing.Graphics.DrawImage%2A>方法會接收<xref:System.Drawing.Bitmap>和<xref:System.Drawing.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="72502-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="72502-107">矩形指定的目的地繪圖作業。也就是說，它會指定要在其中繪製影像的矩形。</span><span class="sxs-lookup"><span data-stu-id="72502-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="72502-108">如果目的矩形的大小不同於原始的映像的大小，以符合目的地矩形縮放影像。</span><span class="sxs-lookup"><span data-stu-id="72502-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="72502-109">下列程式碼範例示範如何繪製相同的映像三次： 一次沒有縮放、 另一次使用的擴充和另一次使用的壓縮：</span><span class="sxs-lookup"><span data-stu-id="72502-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="72502-110">下圖顯示三個圖片。</span><span class="sxs-lookup"><span data-stu-id="72502-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="72502-111">![調整](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="72502-111">![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="72502-112">一些變化<xref:System.Drawing.Graphics.DrawImage%2A>方法有來源矩形參數，以及目的地矩形參數。</span><span class="sxs-lookup"><span data-stu-id="72502-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="72502-113">來源矩形參數會指定要繪製之原始影像的一部分。</span><span class="sxs-lookup"><span data-stu-id="72502-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="72502-114">目的矩形指定要在其中繪製影像的該部分。</span><span class="sxs-lookup"><span data-stu-id="72502-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="72502-115">如果目的矩形的大小不同於來源矩形的大小，圖片會調整為適合滿目的矩形。</span><span class="sxs-lookup"><span data-stu-id="72502-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="72502-116">下列程式碼範例示範如何建構<xref:System.Drawing.Bitmap>Runner.jpg 檔案中。</span><span class="sxs-lookup"><span data-stu-id="72502-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="72502-117">在沒有縮放繪製整個影像 （0，0）。</span><span class="sxs-lookup"><span data-stu-id="72502-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="72502-118">然後一小部分的影像繪製兩次： 一次使用壓縮，另一次使用放大。</span><span class="sxs-lookup"><span data-stu-id="72502-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="72502-119">下圖顯示未縮放的影像，以及壓縮和展開的影像部分。</span><span class="sxs-lookup"><span data-stu-id="72502-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="72502-120">![裁剪和縮放](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="72502-120">![Cropping and Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72502-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="72502-121">See Also</span></span>  
 [<span data-ttu-id="72502-122">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="72502-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="72502-123">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="72502-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
