---
title: 影像、點陣圖和中繼檔
ms.date: 03/30/2017
helpviewer_keywords:
- metafiles [Windows Forms], about metafiles
- bitmaps [Windows Forms], about bitmaps
- images [Windows Forms], about images
- Windows Forms, images
ms.assetid: 7152b45b-a55c-49bc-8c78-ae002a844f71
ms.openlocfilehash: 2ce19642b37946db7a172e61004688059dba61db
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717423"
---
# <a name="images-bitmaps-and-metafiles"></a><span data-ttu-id="55214-102">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="55214-102">Images, Bitmaps, and Metafiles</span></span>
<span data-ttu-id="55214-103">
  `Image\` 類別為抽象基底類別，提供使用點陣影像 (點陣圖) 和向量影像 (中繼檔) 的方法。</span><span class="sxs-lookup"><span data-stu-id="55214-103">The `Image` class is an abstract base class that provides methods for working with raster images (bitmaps) and vector images (metafiles).</span></span> <span data-ttu-id="55214-104">`Bitmap` 類別和 <xref:System.Drawing.Imaging.Metafile> 類別都是繼承自 `Image` 類別。</span><span class="sxs-lookup"><span data-stu-id="55214-104">The `Bitmap` class and the <xref:System.Drawing.Imaging.Metafile> class both inherit from the `Image` class.</span></span> <span data-ttu-id="55214-105">`Bitmap` 類別透過提供載入、儲存和管理點陣影像的其他方法，來擴充 `Image` 類別的功能。</span><span class="sxs-lookup"><span data-stu-id="55214-105">The `Bitmap` class expands on the capabilities of the `Image` class by providing additional methods for loading, saving, and manipulating raster images.</span></span> <span data-ttu-id="55214-106">
  <xref:System.Drawing.Imaging.Metafile> 類別透過提供記錄和檢查向量影像的其他方法，來擴充 `Image\` 類別的功能。</span><span class="sxs-lookup"><span data-stu-id="55214-106">The <xref:System.Drawing.Imaging.Metafile> class expands on the capabilities of the `Image` class by providing additional methods for recording and examining vector images.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55214-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="55214-107">In This Section</span></span>  
 [<span data-ttu-id="55214-108">點陣圖類型</span><span class="sxs-lookup"><span data-stu-id="55214-108">Types of Bitmaps</span></span>](types-of-bitmaps.md)  
 <span data-ttu-id="55214-109">討論各種影像格式。</span><span class="sxs-lookup"><span data-stu-id="55214-109">Discusses the various image formats.</span></span>  
  
 [<span data-ttu-id="55214-110">GDI+ 中的中繼檔</span><span class="sxs-lookup"><span data-stu-id="55214-110">Metafiles in GDI+</span></span>](metafiles-in-gdi.md)  
 <span data-ttu-id="55214-111">討論 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 對中繼檔的支援。</span><span class="sxs-lookup"><span data-stu-id="55214-111">Discusses [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] support for metafiles.</span></span>  
  
 [<span data-ttu-id="55214-112">在 GDI+ 中繪製、定位和複製影像</span><span class="sxs-lookup"><span data-stu-id="55214-112">Drawing, Positioning, and Cloning Images in GDI+</span></span>](drawing-positioning-and-cloning-images-in-gdi.md)  
 <span data-ttu-id="55214-113">討論使用 Managed 程式碼繪製向量和點陣影像的方法。</span><span class="sxs-lookup"><span data-stu-id="55214-113">Discusses methods for drawing vector and raster images with managed code.</span></span>  
  
 [<span data-ttu-id="55214-114">在 GDI+ 中裁剪和縮放影像</span><span class="sxs-lookup"><span data-stu-id="55214-114">Cropping and Scaling Images in GDI+</span></span>](cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="55214-115">討論使用 Managed 程式碼裁剪和縮放向量和點陣影像的方法。</span><span class="sxs-lookup"><span data-stu-id="55214-115">Discusses methods for cropping and scaling vector and raster images with managed code</span></span>  
  
## <a name="reference"></a><span data-ttu-id="55214-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="55214-116">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="55214-117">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="55214-117">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="55214-118">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="55214-118">Describes this class and has links to all of its members</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="55214-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="55214-119">Related Sections</span></span>  
 [<span data-ttu-id="55214-120">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="55214-120">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="55214-121">包含示範如何在您的應用程式中使用影像的主題連結。</span><span class="sxs-lookup"><span data-stu-id="55214-121">Contains links to topics that demonstrate how to use images in your application.</span></span>
