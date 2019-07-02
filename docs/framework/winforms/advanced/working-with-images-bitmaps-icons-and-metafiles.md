---
title: 使用影像、點陣圖、圖示和中繼檔
ms.date: 03/30/2017
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
ms.openlocfilehash: 8c778018a2d78fbec67a3bf41b5cbaa8e4bfb606
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504853"
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="6437c-102">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="6437c-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
<span data-ttu-id="6437c-103">GDI + 提供`Bitmap`類別使用點陣影像和`Metafile`使用向量影像的類別。</span><span class="sxs-lookup"><span data-stu-id="6437c-103">GDI+ provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="6437c-104">`Bitmap` 類別和 `Metafile` 類別都是繼承自 `Image` 類別。</span><span class="sxs-lookup"><span data-stu-id="6437c-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6437c-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="6437c-105">In This Section</span></span>  
 [<span data-ttu-id="6437c-106">如何：將現有點陣圖描繪至螢幕</span><span class="sxs-lookup"><span data-stu-id="6437c-106">How to: Draw an Existing Bitmap to the Screen</span></span>](how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="6437c-107">描述如何載入及繪製點陣圖。</span><span class="sxs-lookup"><span data-stu-id="6437c-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="6437c-108">如何：載入和顯示中繼檔</span><span class="sxs-lookup"><span data-stu-id="6437c-108">How to: Load and Display Metafiles</span></span>](how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="6437c-109">顯示如何載入及繪製中繼檔。</span><span class="sxs-lookup"><span data-stu-id="6437c-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="6437c-110">在 GDI+ 中裁剪和縮放影像</span><span class="sxs-lookup"><span data-stu-id="6437c-110">Cropping and Scaling Images in GDI+</span></span>](cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="6437c-111">說明如何裁剪及縮放向量和點陣影像。</span><span class="sxs-lookup"><span data-stu-id="6437c-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="6437c-112">如何：旋轉、 反射和傾斜影像</span><span class="sxs-lookup"><span data-stu-id="6437c-112">How to: Rotate, Reflect, and Skew Images</span></span>](how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="6437c-113">描述如何繪製旋轉、反射和傾斜的影像。</span><span class="sxs-lookup"><span data-stu-id="6437c-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="6437c-114">如何：在調整期間使用插補法模式控制影像品質</span><span class="sxs-lookup"><span data-stu-id="6437c-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="6437c-115">示範如何使用 <xref:System.Drawing.Drawing2D.InterpolationMode> 列舉變更影像品質。</span><span class="sxs-lookup"><span data-stu-id="6437c-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="6437c-116">如何：建立縮圖影像</span><span class="sxs-lookup"><span data-stu-id="6437c-116">How to: Create Thumbnail Images</span></span>](how-to-create-thumbnail-images.md)  
 <span data-ttu-id="6437c-117">描述如何建立縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="6437c-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="6437c-118">如何：避免自動縮放來改善效能</span><span class="sxs-lookup"><span data-stu-id="6437c-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="6437c-119">說明如何在沒有自動縮放比例的情況下繪製影像。</span><span class="sxs-lookup"><span data-stu-id="6437c-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="6437c-120">如何：讀取影像中繼資料</span><span class="sxs-lookup"><span data-stu-id="6437c-120">How to: Read Image Metadata</span></span>](how-to-read-image-metadata.md)  
 <span data-ttu-id="6437c-121">描述如何讀取影像的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6437c-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="6437c-122">如何：在執行階段建立點陣圖</span><span class="sxs-lookup"><span data-stu-id="6437c-122">How to: Create a Bitmap at Run Time</span></span>](how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="6437c-123">示範如何在執行階段繪製點陣圖。</span><span class="sxs-lookup"><span data-stu-id="6437c-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="6437c-124">如何：擷取與 Windows Form 中檔案相關聯的圖示</span><span class="sxs-lookup"><span data-stu-id="6437c-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="6437c-125">描述如何擷取檔案內嵌資源的圖示。</span><span class="sxs-lookup"><span data-stu-id="6437c-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6437c-126">參考資料</span><span class="sxs-lookup"><span data-stu-id="6437c-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="6437c-127">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="6437c-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="6437c-128">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="6437c-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="6437c-129">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="6437c-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6437c-130">相關章節</span><span class="sxs-lookup"><span data-stu-id="6437c-130">Related Sections</span></span>  
 [<span data-ttu-id="6437c-131">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="6437c-131">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="6437c-132">包含主題連結，討論不同類型的點陣圖和在您的應用程式中管理它們。</span><span class="sxs-lookup"><span data-stu-id="6437c-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
