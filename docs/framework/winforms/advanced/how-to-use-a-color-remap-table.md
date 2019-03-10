---
title: HOW TO：使用色彩重新對應表
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: 72965d6968aab256579929acc00e629bcd3c71f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707328"
---
# <a name="how-to-use-a-color-remap-table"></a><span data-ttu-id="8d7d8-102">HOW TO：使用色彩重新對應表</span><span class="sxs-lookup"><span data-stu-id="8d7d8-102">How to: Use a Color Remap Table</span></span>
<span data-ttu-id="8d7d8-103">重新對應是轉換的色彩，色彩重新對應表根據映像中的程序。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-103">Remapping is the process of converting the colors in an image according to a color remap table.</span></span> <span data-ttu-id="8d7d8-104">色彩重新對應表是陣列<xref:System.Drawing.Imaging.ColorMap>物件。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-104">The color remap table is an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="8d7d8-105">每個<xref:System.Drawing.Imaging.ColorMap>陣列中的物件具有<xref:System.Drawing.Imaging.ColorMap.OldColor%2A>屬性和<xref:System.Drawing.Imaging.ColorMap.NewColor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-105">Each <xref:System.Drawing.Imaging.ColorMap> object in the array has an <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property and a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property.</span></span>  
  
 <span data-ttu-id="8d7d8-106">當[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]繪製映像，映像的每個像素相較於舊的色彩陣列。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-106">When [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] draws an image, each pixel of the image is compared to the array of old colors.</span></span> <span data-ttu-id="8d7d8-107">如果像素的色彩符合舊的色彩，其色彩會變更對應的新色彩。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-107">If a pixel's color matches an old color, its color is changed to the corresponding new color.</span></span> <span data-ttu-id="8d7d8-108">只為了轉譯已變更的色彩，影像本身的色彩值 (儲存在<xref:System.Drawing.Image>或<xref:System.Drawing.Bitmap>物件) 則不會變更。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-108">The colors are changed only for rendering — the color values of the image itself (stored in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object) are not changed.</span></span>  
  
 <span data-ttu-id="8d7d8-109">若要繪製重新對應的影像，初始化陣列<xref:System.Drawing.Imaging.ColorMap>物件。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-109">To draw a remapped image, initialize an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="8d7d8-110">傳遞至該陣列<xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>物件，然後再傳遞<xref:System.Drawing.Imaging.ImageAttributes>物件<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-110">Pass that array to the <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> method of an <xref:System.Drawing.Imaging.ImageAttributes> object, and then pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d7d8-111">範例</span><span class="sxs-lookup"><span data-stu-id="8d7d8-111">Example</span></span>  
 <span data-ttu-id="8d7d8-112">下列範例會建立<xref:System.Drawing.Image>RemapInput.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-112">The following example creates an <xref:System.Drawing.Image> object from the file RemapInput.bmp.</span></span> <span data-ttu-id="8d7d8-113">程式碼會建立包含單一色彩重新對應表<xref:System.Drawing.Imaging.ColorMap>物件。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-113">The code creates a color remap table that consists of a single <xref:System.Drawing.Imaging.ColorMap> object.</span></span> <span data-ttu-id="8d7d8-114"><xref:System.Drawing.Imaging.ColorMap.OldColor%2A>的屬性`ColorRemap`物件為紅色，而<xref:System.Drawing.Imaging.ColorMap.NewColor%2A>屬性則是藍色。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-114">The <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property of the `ColorRemap` object is red, and the <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property is blue.</span></span> <span data-ttu-id="8d7d8-115">影像是繪製一次，而不需要重新對應，另一次重新對應。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-115">The image is drawn once without remapping and once with remapping.</span></span> <span data-ttu-id="8d7d8-116">重新對應的程序變更為藍色所有紅色的像素。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-116">The remapping process changes all the red pixels to blue.</span></span>  
  
 <span data-ttu-id="8d7d8-117">下圖顯示原始的映像，在左邊和重新對應的映像，在右邊。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-117">The following illustration shows the original image on the left and the remapped image on the right.</span></span>  
  
 <span data-ttu-id="8d7d8-118">![色彩重新對應](./media/colortrans7.png "colortrans7")</span><span class="sxs-lookup"><span data-stu-id="8d7d8-118">![Color ReMap](./media/colortrans7.png "colortrans7")</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8d7d8-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8d7d8-119">Compiling the Code</span></span>  
 <span data-ttu-id="8d7d8-120">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="8d7d8-120">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d7d8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d7d8-121">See also</span></span>
- [<span data-ttu-id="8d7d8-122">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="8d7d8-122">Recoloring Images</span></span>](recoloring-images.md)
- [<span data-ttu-id="8d7d8-123">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="8d7d8-123">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
