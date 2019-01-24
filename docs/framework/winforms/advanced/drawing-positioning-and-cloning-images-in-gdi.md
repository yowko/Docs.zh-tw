---
title: 在 GDI+ 中繪製、定位和複製影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
ms.openlocfilehash: afd5be1fd56382ba0dcbb2938a7e466d1584ae7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548215"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a><span data-ttu-id="72332-102">在 GDI+ 中繪製、定位和複製影像</span><span class="sxs-lookup"><span data-stu-id="72332-102">Drawing, Positioning, and Cloning Images in GDI+</span></span>
<span data-ttu-id="72332-103">您可以使用<xref:System.Drawing.Bitmap>類別來載入和顯示點陣影像，以及您可以使用<xref:System.Drawing.Imaging.Metafile>類別來載入和顯示向量影像。</span><span class="sxs-lookup"><span data-stu-id="72332-103">You can use the <xref:System.Drawing.Bitmap> class to load and display raster images, and you can use the <xref:System.Drawing.Imaging.Metafile> class to load and display vector images.</span></span> <span data-ttu-id="72332-104"><xref:System.Drawing.Bitmap>並<xref:System.Drawing.Imaging.Metafile>類別繼承自<xref:System.Drawing.Image>類別。</span><span class="sxs-lookup"><span data-stu-id="72332-104">The <xref:System.Drawing.Bitmap> and <xref:System.Drawing.Imaging.Metafile> classes inherit from the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="72332-105">若要顯示的向量映像，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Imaging.Metafile>。</span><span class="sxs-lookup"><span data-stu-id="72332-105">To display a vector image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="72332-106">若要顯示點陣影像，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Bitmap>。</span><span class="sxs-lookup"><span data-stu-id="72332-106">To display a raster image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="72332-107">執行個體<xref:System.Drawing.Graphics>類別會提供<xref:System.Drawing.Graphics.DrawImage%2A>方法，它會接收<xref:System.Drawing.Imaging.Metafile>或<xref:System.Drawing.Bitmap>做為引數。</span><span class="sxs-lookup"><span data-stu-id="72332-107">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawImage%2A> method, which receives the <xref:System.Drawing.Imaging.Metafile> or <xref:System.Drawing.Bitmap> as an argument.</span></span>  
  
## <a name="file-types-and-cloning"></a><span data-ttu-id="72332-108">檔案類型，以及複製</span><span class="sxs-lookup"><span data-stu-id="72332-108">File Types and Cloning</span></span>  
 <span data-ttu-id="72332-109">下列程式碼範例示範如何建構<xref:System.Drawing.Bitmap>從 Climber.jpg 檔案，並顯示點陣圖。</span><span class="sxs-lookup"><span data-stu-id="72332-109">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Climber.jpg and displays the bitmap.</span></span> <span data-ttu-id="72332-110">映像，左上角的目的點 （10，10），第二個和第三個參數中指定。</span><span class="sxs-lookup"><span data-stu-id="72332-110">The destination point for the upper-left corner of the image, (10, 10), is specified in the second and third parameters.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 <span data-ttu-id="72332-111">下圖顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="72332-111">The following illustration shows the image.</span></span>  
  
 <span data-ttu-id="72332-112">![影像範例](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span><span class="sxs-lookup"><span data-stu-id="72332-112">![Image Sample](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span></span>  
  
 <span data-ttu-id="72332-113">您可以建構<xref:System.Drawing.Bitmap>各式各樣的圖形物件檔案格式：BMP、 GIF、 JPEG、 EXIF、 PNG、 TIFF 和圖示。</span><span class="sxs-lookup"><span data-stu-id="72332-113">You can construct <xref:System.Drawing.Bitmap> objects from a variety of graphics file formats: BMP, GIF, JPEG, EXIF, PNG, TIFF, and ICON.</span></span>  
  
 <span data-ttu-id="72332-114">下列程式碼範例示範如何建構<xref:System.Drawing.Bitmap>各種檔案類型的物件，並顯示點陣圖。</span><span class="sxs-lookup"><span data-stu-id="72332-114">The following code example shows how to construct <xref:System.Drawing.Bitmap> objects from a variety of file types and then displays the bitmaps.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <span data-ttu-id="72332-115"><xref:System.Drawing.Bitmap>類別會提供<xref:System.Drawing.Bitmap.Clone%2A>方法，可用來建立一份現有<xref:System.Drawing.Bitmap>。</span><span class="sxs-lookup"><span data-stu-id="72332-115">The <xref:System.Drawing.Bitmap> class provides a <xref:System.Drawing.Bitmap.Clone%2A> method that you can use to make a copy of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="72332-116"><xref:System.Drawing.Bitmap.Clone%2A>方法具有可用來指定您想要複製的原始點陣圖一部分的來源矩形參數。</span><span class="sxs-lookup"><span data-stu-id="72332-116">The <xref:System.Drawing.Bitmap.Clone%2A> method has a source rectangle parameter that you can use to specify the portion of the original bitmap that you want to copy.</span></span> <span data-ttu-id="72332-117">下列程式碼範例示範如何建立<xref:System.Drawing.Bitmap>藉由複製現有的上半部<xref:System.Drawing.Bitmap>。</span><span class="sxs-lookup"><span data-stu-id="72332-117">The following code example shows how to create a <xref:System.Drawing.Bitmap> by cloning the top half of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="72332-118">然後會繪製這兩個映像。</span><span class="sxs-lookup"><span data-stu-id="72332-118">Then both images are drawn.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 <span data-ttu-id="72332-119">下圖顯示兩個映像。</span><span class="sxs-lookup"><span data-stu-id="72332-119">The following illustration shows the two images.</span></span>  
  
 <span data-ttu-id="72332-120">![Cropping](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span><span class="sxs-lookup"><span data-stu-id="72332-120">![Cropping](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72332-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72332-121">See also</span></span>
- [<span data-ttu-id="72332-122">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="72332-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="72332-123">如何：建立繪圖的圖形物件</span><span class="sxs-lookup"><span data-stu-id="72332-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="72332-124">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="72332-124">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
