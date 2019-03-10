---
title: 在 GDI+ 中裁剪和縮放影像
ms.date: 03/30/2017
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
ms.openlocfilehash: 311673c30283cdf3e0206d143daab8c01adc2bce
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718788"
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="47192-102">在 GDI+ 中裁剪和縮放影像</span><span class="sxs-lookup"><span data-stu-id="47192-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="47192-103">您可以使用<xref:System.Drawing.Graphics.DrawImage%2A>方法的<xref:System.Drawing.Graphics>類別，以繪製和向量映像和點陣影像的位置。</span><span class="sxs-lookup"><span data-stu-id="47192-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="47192-104"><xref:System.Drawing.Graphics.DrawImage%2A> 是多載的方法，因此沒有提供引數的數種方式。</span><span class="sxs-lookup"><span data-stu-id="47192-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="47192-105">DrawImage 變化</span><span class="sxs-lookup"><span data-stu-id="47192-105">DrawImage Variations</span></span>  
 <span data-ttu-id="47192-106">其中一個變化<xref:System.Drawing.Graphics.DrawImage%2A>方法會接收<xref:System.Drawing.Bitmap>和<xref:System.Drawing.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="47192-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="47192-107">矩形指定的目的地，繪製作業;也就是說，它會指定在其中繪製影像的矩形。</span><span class="sxs-lookup"><span data-stu-id="47192-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="47192-108">如果目的地矩形的大小不同於原始的映像的大小，影像會縮放以符合目的地矩形。</span><span class="sxs-lookup"><span data-stu-id="47192-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="47192-109">下列程式碼範例示範如何繪製相同的映像三次： 一次，且不進行縮放，另一次展開時，使用，另一次壓縮：</span><span class="sxs-lookup"><span data-stu-id="47192-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="47192-110">下圖顯示三個的圖片。</span><span class="sxs-lookup"><span data-stu-id="47192-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="47192-111">![Scaling](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="47192-111">![Scaling](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="47192-112">一些變化<xref:System.Drawing.Graphics.DrawImage%2A>方法有來源矩形的參數，以及目的地矩形的參數。</span><span class="sxs-lookup"><span data-stu-id="47192-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="47192-113">來源矩形參數會指定要繪製之原始影像的部分。</span><span class="sxs-lookup"><span data-stu-id="47192-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="47192-114">目的矩形會指定要在其中繪製影像的該部分的矩形。</span><span class="sxs-lookup"><span data-stu-id="47192-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="47192-115">如果目的地矩形的大小是不同於來源矩形的大小，圖片會調整為適合滿目的矩形。</span><span class="sxs-lookup"><span data-stu-id="47192-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="47192-116">下列程式碼範例示範如何建構<xref:System.Drawing.Bitmap>Runner.jpg 檔案中。</span><span class="sxs-lookup"><span data-stu-id="47192-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="47192-117">在沒有縮放繪製整個影像 （0，0）。</span><span class="sxs-lookup"><span data-stu-id="47192-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="47192-118">然後映像的一小部分繪製兩次： 一次使用壓縮，另一次使用擴充功能。</span><span class="sxs-lookup"><span data-stu-id="47192-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="47192-119">下圖顯示未縮放的影像，並壓縮和展開的影像部分。</span><span class="sxs-lookup"><span data-stu-id="47192-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="47192-120">![裁剪和縮放](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="47192-120">![Cropping and Scaling](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47192-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47192-121">See also</span></span>
- [<span data-ttu-id="47192-122">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="47192-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="47192-123">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="47192-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
