---
title: HOW TO：轉譯影像色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 04e61383ef79b17ea6e1523588cd9593ec9b082c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132635"
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="e19b0-102">HOW TO：轉譯影像色彩</span><span class="sxs-lookup"><span data-stu-id="e19b0-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="e19b0-103">翻譯加入到一或多個四個色彩元件的值。</span><span class="sxs-lookup"><span data-stu-id="e19b0-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="e19b0-104">下表提供色彩矩陣項目表示的翻譯。</span><span class="sxs-lookup"><span data-stu-id="e19b0-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="e19b0-105">要轉換的元素</span><span class="sxs-lookup"><span data-stu-id="e19b0-105">Component to be translated</span></span>|<span data-ttu-id="e19b0-106">矩陣項目</span><span class="sxs-lookup"><span data-stu-id="e19b0-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="e19b0-107">紅色</span><span class="sxs-lookup"><span data-stu-id="e19b0-107">Red</span></span>|<span data-ttu-id="e19b0-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="e19b0-108">[4][0]</span></span>|  
|<span data-ttu-id="e19b0-109">綠色</span><span class="sxs-lookup"><span data-stu-id="e19b0-109">Green</span></span>|<span data-ttu-id="e19b0-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="e19b0-110">[4][1]</span></span>|  
|<span data-ttu-id="e19b0-111">藍色</span><span class="sxs-lookup"><span data-stu-id="e19b0-111">Blue</span></span>|<span data-ttu-id="e19b0-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="e19b0-112">[4][2]</span></span>|  
|<span data-ttu-id="e19b0-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="e19b0-113">Alpha</span></span>|<span data-ttu-id="e19b0-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="e19b0-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e19b0-115">範例</span><span class="sxs-lookup"><span data-stu-id="e19b0-115">Example</span></span>  
 <span data-ttu-id="e19b0-116">下列範例會建構<xref:System.Drawing.Image>ColorBars.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="e19b0-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="e19b0-117">然後程式碼會新增至映像中的每個像素的紅色元件 0.75。</span><span class="sxs-lookup"><span data-stu-id="e19b0-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="e19b0-118">原始的映像與已轉換的映像一起繪製。</span><span class="sxs-lookup"><span data-stu-id="e19b0-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="e19b0-119">下圖顯示原始的映像，在左邊和轉換後的映像，在右側：</span><span class="sxs-lookup"><span data-stu-id="e19b0-119">The following illustration shows the original image on the left and the transformed image on the right:</span></span>  
  
 ![螢幕擷取畫面的原始和轉換好的映像。](./media/how-to-translate-image-colors/original-image-translate-colors.png)  
  
 <span data-ttu-id="e19b0-121">下表列出四個橫條的色彩向量之前, 和之後的紅色的翻譯。</span><span class="sxs-lookup"><span data-stu-id="e19b0-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="e19b0-122">請注意，因為色彩元件的最大值為 1，第二個資料列中的紅色元件不會變更。</span><span class="sxs-lookup"><span data-stu-id="e19b0-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="e19b0-123">（同樣地，色彩元件的最小值是 0）。</span><span class="sxs-lookup"><span data-stu-id="e19b0-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="e19b0-124">原始</span><span class="sxs-lookup"><span data-stu-id="e19b0-124">Original</span></span>|<span data-ttu-id="e19b0-125">轉譯</span><span class="sxs-lookup"><span data-stu-id="e19b0-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="e19b0-126">黑色 （0，0，0，1）</span><span class="sxs-lookup"><span data-stu-id="e19b0-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="e19b0-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="e19b0-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="e19b0-128">紅色 （1，0，0，1）</span><span class="sxs-lookup"><span data-stu-id="e19b0-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="e19b0-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="e19b0-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="e19b0-130">綠色 （0、 1、 0、 1）</span><span class="sxs-lookup"><span data-stu-id="e19b0-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="e19b0-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="e19b0-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="e19b0-132">藍色 （0，0，1，1）</span><span class="sxs-lookup"><span data-stu-id="e19b0-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="e19b0-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="e19b0-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e19b0-134">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e19b0-134">Compiling the Code</span></span>  
 <span data-ttu-id="e19b0-135">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="e19b0-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="e19b0-136">取代`ColorBars.bmp`映像檔案名稱與您系統為有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="e19b0-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e19b0-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e19b0-137">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="e19b0-138">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="e19b0-138">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="e19b0-139">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="e19b0-139">Recoloring Images</span></span>](recoloring-images.md)
