---
title: "使用轉換調整色彩"
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
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7515f34858ef6f4b0495ac6fc545ae498d45c7f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="d6047-102">使用轉換調整色彩</span><span class="sxs-lookup"><span data-stu-id="d6047-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="d6047-103">一或多個四個色彩元件的數字會乘以縮放轉換。</span><span class="sxs-lookup"><span data-stu-id="d6047-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="d6047-104">下表提供代表調整色彩矩陣項目。</span><span class="sxs-lookup"><span data-stu-id="d6047-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="d6047-105">要調整大小的元件</span><span class="sxs-lookup"><span data-stu-id="d6047-105">Component to be scaled</span></span>|<span data-ttu-id="d6047-106">矩陣項目</span><span class="sxs-lookup"><span data-stu-id="d6047-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="d6047-107">紅色</span><span class="sxs-lookup"><span data-stu-id="d6047-107">Red</span></span>|<span data-ttu-id="d6047-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="d6047-108">[0][0]</span></span>|  
|<span data-ttu-id="d6047-109">綠色</span><span class="sxs-lookup"><span data-stu-id="d6047-109">Green</span></span>|<span data-ttu-id="d6047-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="d6047-110">[1][1]</span></span>|  
|<span data-ttu-id="d6047-111">藍色</span><span class="sxs-lookup"><span data-stu-id="d6047-111">Blue</span></span>|<span data-ttu-id="d6047-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="d6047-112">[2][2]</span></span>|  
|<span data-ttu-id="d6047-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="d6047-113">Alpha</span></span>|<span data-ttu-id="d6047-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="d6047-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="d6047-115">調整一種色彩</span><span class="sxs-lookup"><span data-stu-id="d6047-115">Scaling One Color</span></span>  
 <span data-ttu-id="d6047-116">下列範例會建構<xref:System.Drawing.Image>ColorBars2.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="d6047-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="d6047-117">然後程式碼可調整每個像素的藍色元件映像中的 2 倍。</span><span class="sxs-lookup"><span data-stu-id="d6047-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="d6047-118">在原始圖像是繪製轉換後的映像的旁邊。</span><span class="sxs-lookup"><span data-stu-id="d6047-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="d6047-119">下圖顯示在右側的原始左側的映像和縮放的影像。</span><span class="sxs-lookup"><span data-stu-id="d6047-119">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="d6047-120">![調整色彩](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span><span class="sxs-lookup"><span data-stu-id="d6047-120">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span></span>  
  
 <span data-ttu-id="d6047-121">下表列出四個橫條的色彩向量之前和之後藍色的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="d6047-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="d6047-122">請注意，在第四個彩色橫條的藍色元件發生從 0.8 0.6。</span><span class="sxs-lookup"><span data-stu-id="d6047-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="d6047-123">這是因為[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]保留結果的小數部分。</span><span class="sxs-lookup"><span data-stu-id="d6047-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="d6047-124">例如，(2)(0.8) = 1.6，和 1.6 的小數部分是 0.6。</span><span class="sxs-lookup"><span data-stu-id="d6047-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="d6047-125">保留僅小數部分，可確保結果一律會在間隔 [0，1]。</span><span class="sxs-lookup"><span data-stu-id="d6047-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="d6047-126">原始</span><span class="sxs-lookup"><span data-stu-id="d6047-126">Original</span></span>|<span data-ttu-id="d6047-127">縮放</span><span class="sxs-lookup"><span data-stu-id="d6047-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="d6047-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="d6047-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="d6047-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="d6047-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="d6047-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="d6047-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="d6047-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="d6047-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="d6047-136">多個色彩調整</span><span class="sxs-lookup"><span data-stu-id="d6047-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="d6047-137">下列範例會建構<xref:System.Drawing.Image>ColorBars2.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="d6047-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="d6047-138">然後程式碼會縮放映像中的每個像素的紅色、 綠色和藍色元件。</span><span class="sxs-lookup"><span data-stu-id="d6047-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="d6047-139">紅色元件會縮小 25%、 綠色元件會縮小 35%和藍色元件會縮小 50%。</span><span class="sxs-lookup"><span data-stu-id="d6047-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="d6047-140">下圖顯示在右側的原始左側的映像和縮放的影像。</span><span class="sxs-lookup"><span data-stu-id="d6047-140">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="d6047-141">![調整色彩](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span><span class="sxs-lookup"><span data-stu-id="d6047-141">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span></span>  
  
 <span data-ttu-id="d6047-142">下表列出四個橫條的色彩向量之前和之後紅色、 綠色和藍色的調整。</span><span class="sxs-lookup"><span data-stu-id="d6047-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="d6047-143">原始</span><span class="sxs-lookup"><span data-stu-id="d6047-143">Original</span></span>|<span data-ttu-id="d6047-144">縮放</span><span class="sxs-lookup"><span data-stu-id="d6047-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="d6047-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="d6047-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="d6047-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="d6047-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="d6047-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="d6047-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="d6047-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="d6047-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="d6047-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6047-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="d6047-153">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="d6047-154">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="d6047-154">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="d6047-155">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="d6047-155">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
