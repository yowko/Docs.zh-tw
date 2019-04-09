---
title: HOW TO：分歧色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: bf645cf88c4905cd5cf47c2a6c7af088fa428c8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076238"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="c8d72-102">HOW TO：分歧色彩</span><span class="sxs-lookup"><span data-stu-id="c8d72-102">How to: Shear Colors</span></span>
<span data-ttu-id="c8d72-103">切變增加，或另一個色彩元件等比例的量減少色彩元件。</span><span class="sxs-lookup"><span data-stu-id="c8d72-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="c8d72-104">例如，請考慮其中紅色元件會增加一倍的藍色元件值的轉換。</span><span class="sxs-lookup"><span data-stu-id="c8d72-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="c8d72-105">在這類轉換 （0.7，0.5，1），就會變成 （0.2，0.5，1） 的色彩。</span><span class="sxs-lookup"><span data-stu-id="c8d72-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="c8d72-106">新的紅色元件是 0.2 版 + (1/2)(1) = 0.7。</span><span class="sxs-lookup"><span data-stu-id="c8d72-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8d72-107">範例</span><span class="sxs-lookup"><span data-stu-id="c8d72-107">Example</span></span>  
 <span data-ttu-id="c8d72-108">下列範例會建構<xref:System.Drawing.Image>ColorBars4.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="c8d72-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="c8d72-109">然後程式碼會套用至映像中的每個像素上的一段所述的切變轉換。</span><span class="sxs-lookup"><span data-stu-id="c8d72-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="c8d72-110">下圖顯示原始的映像，在左邊和分歧的映像，在右側：</span><span class="sxs-lookup"><span data-stu-id="c8d72-110">The following illustration shows the original image on the left and the sheared image on the right:</span></span> 
  
 ![使用彩色的等量分散-並存說明原始映像和分歧的映像的兩個正方形。](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 <span data-ttu-id="c8d72-112">下表列出四個橫條的色彩向量之前, 和之後切變的轉換。</span><span class="sxs-lookup"><span data-stu-id="c8d72-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="c8d72-113">原始</span><span class="sxs-lookup"><span data-stu-id="c8d72-113">Original</span></span>|<span data-ttu-id="c8d72-114">修剪</span><span class="sxs-lookup"><span data-stu-id="c8d72-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="c8d72-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="c8d72-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="c8d72-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="c8d72-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="c8d72-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="c8d72-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="c8d72-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="c8d72-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="c8d72-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="c8d72-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="c8d72-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="c8d72-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="c8d72-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="c8d72-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="c8d72-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="c8d72-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c8d72-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c8d72-123">Compiling the Code</span></span>  
 <span data-ttu-id="c8d72-124">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c8d72-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="c8d72-125">取代`ColorBars.bmp`映像名稱和您系統上有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="c8d72-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8d72-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8d72-126">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="c8d72-127">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="c8d72-127">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="c8d72-128">將影像重新著色</span><span class="sxs-lookup"><span data-stu-id="c8d72-128">Recoloring Images</span></span>](recoloring-images.md)
