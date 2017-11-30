---
title: "如何：使用色彩重新對應表"
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
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1c4399e98504a675cfbf63462b8dc964c677488e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-remap-table"></a><span data-ttu-id="e7573-102">如何：使用色彩重新對應表</span><span class="sxs-lookup"><span data-stu-id="e7573-102">How to: Use a Color Remap Table</span></span>
<span data-ttu-id="e7573-103">重新對應是轉換的色彩，色彩重新對應表根據映像中的程序。</span><span class="sxs-lookup"><span data-stu-id="e7573-103">Remapping is the process of converting the colors in an image according to a color remap table.</span></span> <span data-ttu-id="e7573-104">色彩重新對應表是陣列<xref:System.Drawing.Imaging.ColorMap>物件。</span><span class="sxs-lookup"><span data-stu-id="e7573-104">The color remap table is an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="e7573-105">每個<xref:System.Drawing.Imaging.ColorMap>陣列中的物件具有<xref:System.Drawing.Imaging.ColorMap.OldColor%2A>屬性和<xref:System.Drawing.Imaging.ColorMap.NewColor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e7573-105">Each <xref:System.Drawing.Imaging.ColorMap> object in the array has an <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property and a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property.</span></span>  
  
 <span data-ttu-id="e7573-106">當[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]繪製影像，影像的每個像素會與舊的色彩的陣列。</span><span class="sxs-lookup"><span data-stu-id="e7573-106">When [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] draws an image, each pixel of the image is compared to the array of old colors.</span></span> <span data-ttu-id="e7573-107">如果像素的色彩符合舊的色彩，其色彩會變更為對應的新色彩。</span><span class="sxs-lookup"><span data-stu-id="e7573-107">If a pixel's color matches an old color, its color is changed to the corresponding new color.</span></span> <span data-ttu-id="e7573-108">僅針對轉譯來變更色彩，影像本身的色彩值 (儲存在<xref:System.Drawing.Image>或<xref:System.Drawing.Bitmap>物件) 不會變更。</span><span class="sxs-lookup"><span data-stu-id="e7573-108">The colors are changed only for rendering — the color values of the image itself (stored in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object) are not changed.</span></span>  
  
 <span data-ttu-id="e7573-109">若要繪製重新對應的影像，初始化陣列<xref:System.Drawing.Imaging.ColorMap>物件。</span><span class="sxs-lookup"><span data-stu-id="e7573-109">To draw a remapped image, initialize an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="e7573-110">傳遞至該陣列<xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>物件，並將傳遞<xref:System.Drawing.Imaging.ImageAttributes>物件<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="e7573-110">Pass that array to the <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> method of an <xref:System.Drawing.Imaging.ImageAttributes> object, and then pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7573-111">範例</span><span class="sxs-lookup"><span data-stu-id="e7573-111">Example</span></span>  
 <span data-ttu-id="e7573-112">下列範例會建立<xref:System.Drawing.Image>RemapInput.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="e7573-112">The following example creates an <xref:System.Drawing.Image> object from the file RemapInput.bmp.</span></span> <span data-ttu-id="e7573-113">程式碼會建立包含單一色彩重新對應表<xref:System.Drawing.Imaging.ColorMap>物件。</span><span class="sxs-lookup"><span data-stu-id="e7573-113">The code creates a color remap table that consists of a single <xref:System.Drawing.Imaging.ColorMap> object.</span></span> <span data-ttu-id="e7573-114"><xref:System.Drawing.Imaging.ColorMap.OldColor%2A>屬性`ColorRemap`物件為紅色，而<xref:System.Drawing.Imaging.ColorMap.NewColor%2A>屬性是藍色。</span><span class="sxs-lookup"><span data-stu-id="e7573-114">The <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property of the `ColorRemap` object is red, and the <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property is blue.</span></span> <span data-ttu-id="e7573-115">影像是不含重新對應的繪製一次，另一次重新對應。</span><span class="sxs-lookup"><span data-stu-id="e7573-115">The image is drawn once without remapping and once with remapping.</span></span> <span data-ttu-id="e7573-116">重新對應的程序變更為藍色所有紅色的像素。</span><span class="sxs-lookup"><span data-stu-id="e7573-116">The remapping process changes all the red pixels to blue.</span></span>  
  
 <span data-ttu-id="e7573-117">下圖顯示在右側的原始左側的映像和重新對應的影像。</span><span class="sxs-lookup"><span data-stu-id="e7573-117">The following illustration shows the original image on the left and the remapped image on the right.</span></span>  
  
 <span data-ttu-id="e7573-118">![色彩重新對應](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span><span class="sxs-lookup"><span data-stu-id="e7573-118">![Color ReMap](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7573-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e7573-119">Compiling the Code</span></span>  
 <span data-ttu-id="e7573-120">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="e7573-120">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7573-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7573-121">See Also</span></span>  
 [<span data-ttu-id="e7573-122">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="e7573-122">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="e7573-123">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="e7573-123">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
