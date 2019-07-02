---
title: 使用 Managed GDI+ 中的影像編碼器和解碼器
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: 8cd66f3ce3da462867da9e23c38b3f6d877c058c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505085"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="f1dee-102">使用 Managed GDI+ 中的影像編碼器和解碼器</span><span class="sxs-lookup"><span data-stu-id="f1dee-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="f1dee-103"><xref:System.Drawing>命名空間提供<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>來儲存及操作影像的類別。</span><span class="sxs-lookup"><span data-stu-id="f1dee-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="f1dee-104">藉由使用 GDI + 中的影像編碼器，您可以將映像從記憶體寫入磁碟。</span><span class="sxs-lookup"><span data-stu-id="f1dee-104">By using image encoders in GDI+, you can write images from memory to disk.</span></span> <span data-ttu-id="f1dee-105">藉由使用 GDI + 中的影像解碼器，您可以從磁碟載入映像載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="f1dee-105">By using image decoders in GDI+, you can load images from disk into memory.</span></span> <span data-ttu-id="f1dee-106">編碼器會將轉譯中的資料<xref:System.Drawing.Image>或<xref:System.Drawing.Bitmap>到指定的磁碟檔案格式的物件。</span><span class="sxs-lookup"><span data-stu-id="f1dee-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="f1dee-107">解碼器會轉譯檔案中的資料磁碟所需的格式來<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>物件。</span><span class="sxs-lookup"><span data-stu-id="f1dee-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="f1dee-108">GDI + 具有內建的編碼器和解碼器，支援下列檔案類型：</span><span class="sxs-lookup"><span data-stu-id="f1dee-108">GDI+ has built-in encoders and decoders that support the following file types:</span></span>  
  
- <span data-ttu-id="f1dee-109">BMP</span><span class="sxs-lookup"><span data-stu-id="f1dee-109">BMP</span></span>  
  
- <span data-ttu-id="f1dee-110">GIF</span><span class="sxs-lookup"><span data-stu-id="f1dee-110">GIF</span></span>  
  
- <span data-ttu-id="f1dee-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="f1dee-111">JPEG</span></span>  
  
- <span data-ttu-id="f1dee-112">PNG</span><span class="sxs-lookup"><span data-stu-id="f1dee-112">PNG</span></span>  
  
- <span data-ttu-id="f1dee-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="f1dee-113">TIFF</span></span>  
  
 <span data-ttu-id="f1dee-114">GDI + 還有內建解碼器，支援下列檔案類型：</span><span class="sxs-lookup"><span data-stu-id="f1dee-114">GDI+ also has built-in decoders that support the following file types:</span></span>  
  
- <span data-ttu-id="f1dee-115">WMF</span><span class="sxs-lookup"><span data-stu-id="f1dee-115">WMF</span></span>  
  
- <span data-ttu-id="f1dee-116">EMF</span><span class="sxs-lookup"><span data-stu-id="f1dee-116">EMF</span></span>  
  
- <span data-ttu-id="f1dee-117">圖示</span><span class="sxs-lookup"><span data-stu-id="f1dee-117">ICON</span></span>  
  
 <span data-ttu-id="f1dee-118">下列主題將討論編碼器與解碼器的更多詳細資料：</span><span class="sxs-lookup"><span data-stu-id="f1dee-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1dee-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="f1dee-119">In This Section</span></span>  
 [<span data-ttu-id="f1dee-120">如何：列出已安裝的編碼器</span><span class="sxs-lookup"><span data-stu-id="f1dee-120">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)  
 <span data-ttu-id="f1dee-121">描述如何列出電腦上可用的編碼器。</span><span class="sxs-lookup"><span data-stu-id="f1dee-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="f1dee-122">如何：列出已安裝的解碼器</span><span class="sxs-lookup"><span data-stu-id="f1dee-122">How to: List Installed Decoders</span></span>](how-to-list-installed-decoders.md)  
 <span data-ttu-id="f1dee-123">描述如何列出電腦上可用解碼器。</span><span class="sxs-lookup"><span data-stu-id="f1dee-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="f1dee-124">如何：判斷編碼器所支援的參數</span><span class="sxs-lookup"><span data-stu-id="f1dee-124">How to: Determine the Parameters Supported by an Encoder</span></span>](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="f1dee-125">描述如何列出<xref:System.Drawing.Imaging.EncoderParameters>編碼器所支援。</span><span class="sxs-lookup"><span data-stu-id="f1dee-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="f1dee-126">如何：將 BMP 影像轉換為 PNG 影像</span><span class="sxs-lookup"><span data-stu-id="f1dee-126">How to: Convert a BMP image to a PNG image</span></span>](how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="f1dee-127">描述如何將影像儲存在不同的影像格式。</span><span class="sxs-lookup"><span data-stu-id="f1dee-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="f1dee-128">如何：設定 JPEG 壓縮層級</span><span class="sxs-lookup"><span data-stu-id="f1dee-128">How to: Set JPEG Compression Level</span></span>](how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="f1dee-129">描述如何變更影像的品質等級。</span><span class="sxs-lookup"><span data-stu-id="f1dee-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f1dee-130">參考資料</span><span class="sxs-lookup"><span data-stu-id="f1dee-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="f1dee-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="f1dee-131">Related Sections</span></span>  
 [<span data-ttu-id="f1dee-132">關於 GDI+ Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="f1dee-132">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
  
 [<span data-ttu-id="f1dee-133">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="f1dee-133">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
