---
title: 使用轉換調整色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 9c8f2392137d04f56096120cec64b60c42c47419
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107976"
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="89591-102">使用轉換調整色彩</span><span class="sxs-lookup"><span data-stu-id="89591-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="89591-103">一或多個所提供的數字的四個色彩元件，將乘上縮放轉換。</span><span class="sxs-lookup"><span data-stu-id="89591-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="89591-104">下表提供代表調整色彩矩陣項目。</span><span class="sxs-lookup"><span data-stu-id="89591-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="89591-105">若要調整的元件</span><span class="sxs-lookup"><span data-stu-id="89591-105">Component to be scaled</span></span>|<span data-ttu-id="89591-106">矩陣項目</span><span class="sxs-lookup"><span data-stu-id="89591-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="89591-107">紅色</span><span class="sxs-lookup"><span data-stu-id="89591-107">Red</span></span>|<span data-ttu-id="89591-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="89591-108">[0][0]</span></span>|  
|<span data-ttu-id="89591-109">綠色</span><span class="sxs-lookup"><span data-stu-id="89591-109">Green</span></span>|<span data-ttu-id="89591-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="89591-110">[1][1]</span></span>|  
|<span data-ttu-id="89591-111">藍色</span><span class="sxs-lookup"><span data-stu-id="89591-111">Blue</span></span>|<span data-ttu-id="89591-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="89591-112">[2][2]</span></span>|  
|<span data-ttu-id="89591-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="89591-113">Alpha</span></span>|<span data-ttu-id="89591-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="89591-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="89591-115">調整的一種色彩</span><span class="sxs-lookup"><span data-stu-id="89591-115">Scaling One Color</span></span>  
 <span data-ttu-id="89591-116">下列範例會建構<xref:System.Drawing.Image>ColorBars2.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="89591-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="89591-117">然後程式碼會調整每個像素的藍色元件映像中的 2 倍。</span><span class="sxs-lookup"><span data-stu-id="89591-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="89591-118">原始的映像與已轉換的映像一起繪製。</span><span class="sxs-lookup"><span data-stu-id="89591-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="89591-119">下圖顯示在右側的原始的映像，在左邊和縮放的影像：</span><span class="sxs-lookup"><span data-stu-id="89591-119">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![如果螢幕擷取畫面會比較原始和調整色彩。](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 <span data-ttu-id="89591-121">下表列出四個橫條的色彩向量之前, 和之後的藍色的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="89591-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="89591-122">請注意，在第四個彩色橫條的藍色元件發生從 0.8 0.6。</span><span class="sxs-lookup"><span data-stu-id="89591-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="89591-123">這是因為[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]會保留結果的小數部分。</span><span class="sxs-lookup"><span data-stu-id="89591-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="89591-124">例如，(2)(0.8) version=1.6 應用程式，而 1.6 的小數部分是 0.6。</span><span class="sxs-lookup"><span data-stu-id="89591-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="89591-125">保留小數部分，可確保結果一定是在間隔 [0，1]。</span><span class="sxs-lookup"><span data-stu-id="89591-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="89591-126">原始</span><span class="sxs-lookup"><span data-stu-id="89591-126">Original</span></span>|<span data-ttu-id="89591-127">調整</span><span class="sxs-lookup"><span data-stu-id="89591-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="89591-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="89591-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="89591-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="89591-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="89591-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="89591-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="89591-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="89591-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="89591-136">多個色彩調整</span><span class="sxs-lookup"><span data-stu-id="89591-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="89591-137">下列範例會建構<xref:System.Drawing.Image>ColorBars2.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="89591-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="89591-138">然後程式碼會調整映像中每個像素的紅色、 綠色和藍色元件。</span><span class="sxs-lookup"><span data-stu-id="89591-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="89591-139">紅色元件相應減少百分之 25 的綠色元件相應減少 35%，藍色元件相應減少 50%。</span><span class="sxs-lookup"><span data-stu-id="89591-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="89591-140">下圖顯示在右側的原始的映像，在左邊和縮放的影像：</span><span class="sxs-lookup"><span data-stu-id="89591-140">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![如果螢幕擷取畫面會比較原始和調整色彩。](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 <span data-ttu-id="89591-142">下表列出四個橫條的色彩向量之前, 和之後紅色、 綠色和藍色的調整。</span><span class="sxs-lookup"><span data-stu-id="89591-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="89591-143">原始</span><span class="sxs-lookup"><span data-stu-id="89591-143">Original</span></span>|<span data-ttu-id="89591-144">調整</span><span class="sxs-lookup"><span data-stu-id="89591-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="89591-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="89591-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="89591-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="89591-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="89591-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="89591-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="89591-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="89591-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="89591-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89591-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89591-153">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="89591-154">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="89591-154">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="89591-155">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="89591-155">Recoloring Images</span></span>](recoloring-images.md)
