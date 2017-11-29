---
title: "影像、點陣圖和中繼檔"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], about metafiles
- bitmaps [Windows Forms], about bitmaps
- images [Windows Forms], about images
- Windows Forms, images
ms.assetid: 7152b45b-a55c-49bc-8c78-ae002a844f71
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f48027e413f9573158cfa2c3748fc93408b3f83
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="images-bitmaps-and-metafiles"></a><span data-ttu-id="0a191-102">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="0a191-102">Images, Bitmaps, and Metafiles</span></span>
<span data-ttu-id="0a191-103">`Image` 類別為抽象基底類別，提供使用點陣影像 (點陣圖) 和向量影像 (中繼檔) 的方法。</span><span class="sxs-lookup"><span data-stu-id="0a191-103">The `Image` class is an abstract base class that provides methods for working with raster images (bitmaps) and vector images (metafiles).</span></span> <span data-ttu-id="0a191-104">`Bitmap` 類別和 <xref:System.Drawing.Imaging.Metafile> 類別都是繼承自 `Image` 類別。</span><span class="sxs-lookup"><span data-stu-id="0a191-104">The `Bitmap` class and the <xref:System.Drawing.Imaging.Metafile> class both inherit from the `Image` class.</span></span> <span data-ttu-id="0a191-105">`Bitmap` 類別透過提供載入、儲存和管理點陣影像的其他方法，來擴充 `Image` 類別的功能。</span><span class="sxs-lookup"><span data-stu-id="0a191-105">The `Bitmap` class expands on the capabilities of the `Image` class by providing additional methods for loading, saving, and manipulating raster images.</span></span> <span data-ttu-id="0a191-106"><xref:System.Drawing.Imaging.Metafile> 類別透過提供記錄和檢查向量影像的其他方法，來擴充 `Image` 類別的功能。</span><span class="sxs-lookup"><span data-stu-id="0a191-106">The <xref:System.Drawing.Imaging.Metafile> class expands on the capabilities of the `Image` class by providing additional methods for recording and examining vector images.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a191-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="0a191-107">In This Section</span></span>  
 [<span data-ttu-id="0a191-108">點陣圖類型</span><span class="sxs-lookup"><span data-stu-id="0a191-108">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 <span data-ttu-id="0a191-109">討論各種影像格式。</span><span class="sxs-lookup"><span data-stu-id="0a191-109">Discusses the various image formats.</span></span>  
  
 [<span data-ttu-id="0a191-110">GDI+ 中的中繼檔</span><span class="sxs-lookup"><span data-stu-id="0a191-110">Metafiles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/metafiles-in-gdi.md)  
 <span data-ttu-id="0a191-111">討論 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 對中繼檔的支援。</span><span class="sxs-lookup"><span data-stu-id="0a191-111">Discusses [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] support for metafiles.</span></span>  
  
 [<span data-ttu-id="0a191-112">在 GDI+ 中繪製、定位和複製影像</span><span class="sxs-lookup"><span data-stu-id="0a191-112">Drawing, Positioning, and Cloning Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/drawing-positioning-and-cloning-images-in-gdi.md)  
 <span data-ttu-id="0a191-113">討論使用 Managed 程式碼繪製向量和點陣影像的方法。</span><span class="sxs-lookup"><span data-stu-id="0a191-113">Discusses methods for drawing vector and raster images with managed code.</span></span>  
  
 [<span data-ttu-id="0a191-114">在 GDI+ 中裁剪和縮放影像</span><span class="sxs-lookup"><span data-stu-id="0a191-114">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="0a191-115">討論使用 Managed 程式碼裁剪和縮放向量和點陣影像的方法。</span><span class="sxs-lookup"><span data-stu-id="0a191-115">Discusses methods for cropping and scaling vector and raster images with managed code</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0a191-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="0a191-116">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="0a191-117">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="0a191-117">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="0a191-118">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="0a191-118">Describes this class and has links to all of its members</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0a191-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="0a191-119">Related Sections</span></span>  
 [<span data-ttu-id="0a191-120">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="0a191-120">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="0a191-121">包含示範如何在您的應用程式中使用影像的主題連結。</span><span class="sxs-lookup"><span data-stu-id="0a191-121">Contains links to topics that demonstrate how to use images in your application.</span></span>
