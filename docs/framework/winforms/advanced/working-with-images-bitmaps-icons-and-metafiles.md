---
title: "使用影像、點陣圖、圖示和中繼檔"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53dc25d6a23c5cdbba1c640905eadbdc6b1acb71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="a0d18-102">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="a0d18-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="a0d18-103"> 提供 `Bitmap` 類別來使用點陣影像，且提供 `Metafile` 類別來使用向量影像。</span><span class="sxs-lookup"><span data-stu-id="a0d18-103"> provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="a0d18-104">`Bitmap` 類別和 `Metafile` 類別都是繼承自 `Image` 類別。</span><span class="sxs-lookup"><span data-stu-id="a0d18-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0d18-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="a0d18-105">In This Section</span></span>  
 [<span data-ttu-id="a0d18-106">操作說明：將現有點陣圖描繪至螢幕</span><span class="sxs-lookup"><span data-stu-id="a0d18-106">How to: Draw an Existing Bitmap to the Screen</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="a0d18-107">描述如何載入及繪製點陣圖。</span><span class="sxs-lookup"><span data-stu-id="a0d18-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="a0d18-108">操作說明：載入和顯示中繼檔</span><span class="sxs-lookup"><span data-stu-id="a0d18-108">How to: Load and Display Metafiles</span></span>](../../../../docs/framework/winforms/advanced/how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="a0d18-109">顯示如何載入及繪製中繼檔。</span><span class="sxs-lookup"><span data-stu-id="a0d18-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="a0d18-110">在 GDI+ 中裁剪和縮放影像</span><span class="sxs-lookup"><span data-stu-id="a0d18-110">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="a0d18-111">說明如何裁剪及縮放向量和點陣影像。</span><span class="sxs-lookup"><span data-stu-id="a0d18-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="a0d18-112">操作說明：旋轉、反射和傾斜影像</span><span class="sxs-lookup"><span data-stu-id="a0d18-112">How to: Rotate, Reflect, and Skew Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="a0d18-113">描述如何繪製旋轉、反射和傾斜的影像。</span><span class="sxs-lookup"><span data-stu-id="a0d18-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="a0d18-114">操作說明：縮放期間使用插補法模式控制影像品質</span><span class="sxs-lookup"><span data-stu-id="a0d18-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="a0d18-115">示範如何使用 <xref:System.Drawing.Drawing2D.InterpolationMode> 列舉變更影像品質。</span><span class="sxs-lookup"><span data-stu-id="a0d18-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="a0d18-116">操作說明：建立縮圖影像</span><span class="sxs-lookup"><span data-stu-id="a0d18-116">How to: Create Thumbnail Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-thumbnail-images.md)  
 <span data-ttu-id="a0d18-117">描述如何建立縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="a0d18-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="a0d18-118">操作說明：避免自動縮放以提高效能</span><span class="sxs-lookup"><span data-stu-id="a0d18-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="a0d18-119">說明如何在沒有自動縮放比例的情況下繪製影像。</span><span class="sxs-lookup"><span data-stu-id="a0d18-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="a0d18-120">操作說明：讀取影像中繼資料</span><span class="sxs-lookup"><span data-stu-id="a0d18-120">How to: Read Image Metadata</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-image-metadata.md)  
 <span data-ttu-id="a0d18-121">描述如何讀取影像的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a0d18-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="a0d18-122">操作說明：在執行階段時建立點陣圖</span><span class="sxs-lookup"><span data-stu-id="a0d18-122">How to: Create a Bitmap at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="a0d18-123">示範如何在執行階段繪製點陣圖。</span><span class="sxs-lookup"><span data-stu-id="a0d18-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="a0d18-124">操作說明：擷取與 Windows Forms 中檔案相關的圖示</span><span class="sxs-lookup"><span data-stu-id="a0d18-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="a0d18-125">描述如何擷取檔案內嵌資源的圖示。</span><span class="sxs-lookup"><span data-stu-id="a0d18-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a0d18-126">參考資料</span><span class="sxs-lookup"><span data-stu-id="a0d18-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="a0d18-127">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="a0d18-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="a0d18-128">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="a0d18-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="a0d18-129">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="a0d18-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a0d18-130">相關章節</span><span class="sxs-lookup"><span data-stu-id="a0d18-130">Related Sections</span></span>  
 [<span data-ttu-id="a0d18-131">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="a0d18-131">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="a0d18-132">包含主題連結，討論不同類型的點陣圖和在您的應用程式中管理它們。</span><span class="sxs-lookup"><span data-stu-id="a0d18-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
