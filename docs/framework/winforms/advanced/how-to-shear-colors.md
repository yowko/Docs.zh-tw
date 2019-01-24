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
ms.openlocfilehash: bde3271398c6bc6a37c975476b76acb85511c1a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589828"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="62c66-102">HOW TO：分歧色彩</span><span class="sxs-lookup"><span data-stu-id="62c66-102">How to: Shear Colors</span></span>
<span data-ttu-id="62c66-103">切變增加，或另一個色彩元件等比例的量減少色彩元件。</span><span class="sxs-lookup"><span data-stu-id="62c66-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="62c66-104">例如，請考慮其中紅色元件會增加一倍的藍色元件值的轉換。</span><span class="sxs-lookup"><span data-stu-id="62c66-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="62c66-105">在這類轉換 （0.7，0.5，1），就會變成 （0.2，0.5，1） 的色彩。</span><span class="sxs-lookup"><span data-stu-id="62c66-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="62c66-106">新的紅色元件是 0.2 版 + (1/2)(1) = 0.7。</span><span class="sxs-lookup"><span data-stu-id="62c66-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62c66-107">範例</span><span class="sxs-lookup"><span data-stu-id="62c66-107">Example</span></span>  
 <span data-ttu-id="62c66-108">下列範例會建構<xref:System.Drawing.Image>ColorBars4.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="62c66-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="62c66-109">然後程式碼會套用至映像中的每個像素上的一段所述的切變轉換。</span><span class="sxs-lookup"><span data-stu-id="62c66-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="62c66-110">下圖顯示原始的映像，在左邊和分歧的映像，在右邊。</span><span class="sxs-lookup"><span data-stu-id="62c66-110">The following illustration shows the original image on the left and the sheared image on the right.</span></span>  
  
 <span data-ttu-id="62c66-111">![分歧色彩](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span><span class="sxs-lookup"><span data-stu-id="62c66-111">![Shear Colors](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span></span>  
  
 <span data-ttu-id="62c66-112">下表列出四個橫條的色彩向量之前, 和之後切變的轉換。</span><span class="sxs-lookup"><span data-stu-id="62c66-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="62c66-113">原始</span><span class="sxs-lookup"><span data-stu-id="62c66-113">Original</span></span>|<span data-ttu-id="62c66-114">修剪</span><span class="sxs-lookup"><span data-stu-id="62c66-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="62c66-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="62c66-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="62c66-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="62c66-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="62c66-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="62c66-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="62c66-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="62c66-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="62c66-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="62c66-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="62c66-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="62c66-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="62c66-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="62c66-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="62c66-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="62c66-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62c66-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="62c66-123">Compiling the Code</span></span>  
 <span data-ttu-id="62c66-124">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="62c66-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="62c66-125">取代`ColorBars.bmp`映像名稱和您系統上有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="62c66-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c66-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62c66-126">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="62c66-127">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="62c66-127">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="62c66-128">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="62c66-128">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
