---
title: "如何：轉譯影像色彩"
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
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a2147b9bc86aa7ec03e8455bb0dc51c89a8b282
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="000e7-102">如何：轉譯影像色彩</span><span class="sxs-lookup"><span data-stu-id="000e7-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="000e7-103">翻譯將值加入至一個以上的四個色彩元件。</span><span class="sxs-lookup"><span data-stu-id="000e7-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="000e7-104">下表中，可以代表轉譯的色彩矩陣項目。</span><span class="sxs-lookup"><span data-stu-id="000e7-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="000e7-105">要轉換的元素</span><span class="sxs-lookup"><span data-stu-id="000e7-105">Component to be translated</span></span>|<span data-ttu-id="000e7-106">矩陣項目</span><span class="sxs-lookup"><span data-stu-id="000e7-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="000e7-107">紅色</span><span class="sxs-lookup"><span data-stu-id="000e7-107">Red</span></span>|<span data-ttu-id="000e7-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="000e7-108">[4][0]</span></span>|  
|<span data-ttu-id="000e7-109">綠色</span><span class="sxs-lookup"><span data-stu-id="000e7-109">Green</span></span>|<span data-ttu-id="000e7-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="000e7-110">[4][1]</span></span>|  
|<span data-ttu-id="000e7-111">藍色</span><span class="sxs-lookup"><span data-stu-id="000e7-111">Blue</span></span>|<span data-ttu-id="000e7-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="000e7-112">[4][2]</span></span>|  
|<span data-ttu-id="000e7-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="000e7-113">Alpha</span></span>|<span data-ttu-id="000e7-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="000e7-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="000e7-115">範例</span><span class="sxs-lookup"><span data-stu-id="000e7-115">Example</span></span>  
 <span data-ttu-id="000e7-116">下列範例會建構<xref:System.Drawing.Image>ColorBars.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="000e7-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="000e7-117">然後程式碼會加入 0.75 到映像中的每個像素的紅色元件。</span><span class="sxs-lookup"><span data-stu-id="000e7-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="000e7-118">在原始圖像是繪製轉換後的映像的旁邊。</span><span class="sxs-lookup"><span data-stu-id="000e7-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="000e7-119">下圖顯示在右側的原始左側映像，而且已轉換的映像。</span><span class="sxs-lookup"><span data-stu-id="000e7-119">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="000e7-120">![轉譯色彩](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span><span class="sxs-lookup"><span data-stu-id="000e7-120">![Translate Colors](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span></span>  
  
 <span data-ttu-id="000e7-121">下表列出四個橫條的色彩向量之前和之後的紅色的翻譯。</span><span class="sxs-lookup"><span data-stu-id="000e7-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="000e7-122">請注意，因為色彩元件的最大值為 1，第二個資料列中的紅色元件不會變更。</span><span class="sxs-lookup"><span data-stu-id="000e7-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="000e7-123">（同樣地，色彩元件的最小值為 0）。</span><span class="sxs-lookup"><span data-stu-id="000e7-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="000e7-124">原始</span><span class="sxs-lookup"><span data-stu-id="000e7-124">Original</span></span>|<span data-ttu-id="000e7-125">轉譯</span><span class="sxs-lookup"><span data-stu-id="000e7-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="000e7-126">黑色 （0，0，0，1）</span><span class="sxs-lookup"><span data-stu-id="000e7-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="000e7-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="000e7-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="000e7-128">紅色 （1，0，0，1）</span><span class="sxs-lookup"><span data-stu-id="000e7-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="000e7-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="000e7-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="000e7-130">綠色 （0、 1、 0，1）</span><span class="sxs-lookup"><span data-stu-id="000e7-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="000e7-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="000e7-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="000e7-132">藍色 （0，0，1，1）</span><span class="sxs-lookup"><span data-stu-id="000e7-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="000e7-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="000e7-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="000e7-134">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="000e7-134">Compiling the Code</span></span>  
 <span data-ttu-id="000e7-135">上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="000e7-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="000e7-136">取代`ColorBars.bmp`映像檔案名稱與您系統為有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="000e7-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="000e7-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="000e7-137">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="000e7-138">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="000e7-138">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="000e7-139">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="000e7-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
