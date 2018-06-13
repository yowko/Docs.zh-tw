---
title: 使用 Managed GDI+ 中的影像編碼器和解碼器
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: b2e51587209cb4df41ea1fd18ce5c2088ee07a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524497"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="90abd-102">使用 Managed GDI+ 中的影像編碼器和解碼器</span><span class="sxs-lookup"><span data-stu-id="90abd-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="90abd-103"><xref:System.Drawing>命名空間提供<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>類別來儲存和管理影像。</span><span class="sxs-lookup"><span data-stu-id="90abd-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="90abd-104">使用中的影像編碼器[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以從記憶體寫入映像至磁碟。</span><span class="sxs-lookup"><span data-stu-id="90abd-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="90abd-105">使用中的影像解碼器[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以將記憶體從磁碟載入影像。</span><span class="sxs-lookup"><span data-stu-id="90abd-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="90abd-106">編碼器將在資料轉譯<xref:System.Drawing.Image>或<xref:System.Drawing.Bitmap>到指定的磁碟檔案格式的物件。</span><span class="sxs-lookup"><span data-stu-id="90abd-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="90abd-107">解碼器會將轉譯檔案中的資料磁碟所需的格式來<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>物件。</span><span class="sxs-lookup"><span data-stu-id="90abd-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="90abd-108"> 具有內建編碼器和解碼器支援下列檔案類型：</span><span class="sxs-lookup"><span data-stu-id="90abd-108"> has built-in encoders and decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="90abd-109">BMP</span><span class="sxs-lookup"><span data-stu-id="90abd-109">BMP</span></span>  
  
-   <span data-ttu-id="90abd-110">GIF</span><span class="sxs-lookup"><span data-stu-id="90abd-110">GIF</span></span>  
  
-   <span data-ttu-id="90abd-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="90abd-111">JPEG</span></span>  
  
-   <span data-ttu-id="90abd-112">PNG</span><span class="sxs-lookup"><span data-stu-id="90abd-112">PNG</span></span>  
  
-   <span data-ttu-id="90abd-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="90abd-113">TIFF</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="90abd-114"> 也有支援下列檔案類型的內建解碼器：</span><span class="sxs-lookup"><span data-stu-id="90abd-114"> also has built-in decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="90abd-115">WMF</span><span class="sxs-lookup"><span data-stu-id="90abd-115">WMF</span></span>  
  
-   <span data-ttu-id="90abd-116">EMF</span><span class="sxs-lookup"><span data-stu-id="90abd-116">EMF</span></span>  
  
-   <span data-ttu-id="90abd-117">圖示</span><span class="sxs-lookup"><span data-stu-id="90abd-117">ICON</span></span>  
  
 <span data-ttu-id="90abd-118">下列主題將討論編碼器與解碼器的更多詳細資料：</span><span class="sxs-lookup"><span data-stu-id="90abd-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90abd-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="90abd-119">In This Section</span></span>  
 [<span data-ttu-id="90abd-120">操作說明：列出已安裝的編碼器</span><span class="sxs-lookup"><span data-stu-id="90abd-120">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 <span data-ttu-id="90abd-121">描述如何列出電腦上可用的編碼器。</span><span class="sxs-lookup"><span data-stu-id="90abd-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="90abd-122">操作說明：列出已安裝的解碼器</span><span class="sxs-lookup"><span data-stu-id="90abd-122">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 <span data-ttu-id="90abd-123">描述如何列出電腦上可用的解碼器。</span><span class="sxs-lookup"><span data-stu-id="90abd-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="90abd-124">操作說明：判斷編碼器所支援的參數</span><span class="sxs-lookup"><span data-stu-id="90abd-124">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="90abd-125">描述如何列出<xref:System.Drawing.Imaging.EncoderParameters>編碼器所支援。</span><span class="sxs-lookup"><span data-stu-id="90abd-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="90abd-126">操作說明：將 BMP 影像轉換為 PNG 影像</span><span class="sxs-lookup"><span data-stu-id="90abd-126">How to: Convert a BMP image to a PNG image</span></span>](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="90abd-127">描述如何將影像儲存為不同的影像格式。</span><span class="sxs-lookup"><span data-stu-id="90abd-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="90abd-128">操作說明：設定 JPEG 壓縮層級</span><span class="sxs-lookup"><span data-stu-id="90abd-128">How to: Set JPEG Compression Level</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="90abd-129">描述如何變更影像的品質等級。</span><span class="sxs-lookup"><span data-stu-id="90abd-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="90abd-130">參考資料</span><span class="sxs-lookup"><span data-stu-id="90abd-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="90abd-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="90abd-131">Related Sections</span></span>  
 [<span data-ttu-id="90abd-132">關於 GDI+ Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="90abd-132">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [<span data-ttu-id="90abd-133">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="90abd-133">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
