---
title: 如何：切變色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142390"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="c6abb-102">如何：切變色彩</span><span class="sxs-lookup"><span data-stu-id="c6abb-102">How to: Shear Colors</span></span>
<span data-ttu-id="c6abb-103">剪切會增加或減少顏色分量，以與另一種顏色分量成正比。</span><span class="sxs-lookup"><span data-stu-id="c6abb-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="c6abb-104">例如，考慮紅色分量增加藍色分量值一半的轉換。</span><span class="sxs-lookup"><span data-stu-id="c6abb-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="c6abb-105">在這樣的轉換下，顏色（0.2，0.5，1）將成為（0.7，0.5，1）。</span><span class="sxs-lookup"><span data-stu-id="c6abb-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="c6abb-106">新的紅色分量為 0.2 = （1/2）（1） = 0.7。</span><span class="sxs-lookup"><span data-stu-id="c6abb-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6abb-107">範例</span><span class="sxs-lookup"><span data-stu-id="c6abb-107">Example</span></span>  
 <span data-ttu-id="c6abb-108">下面的示例從檔 ColorBars4.bmp 構造物件<xref:System.Drawing.Image>。</span><span class="sxs-lookup"><span data-stu-id="c6abb-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="c6abb-109">然後，代碼將前一段中描述的剪切變換應用於圖像中的每個圖元。</span><span class="sxs-lookup"><span data-stu-id="c6abb-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="c6abb-110">下圖顯示了左側的原始圖像和右側的謝線圖像：</span><span class="sxs-lookup"><span data-stu-id="c6abb-110">The following illustration shows the original image on the left and the sheared image on the right:</span></span>
  
 ![兩個正方形，帶彩色條紋並排顯示原始圖像和謝線圖像。](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 <span data-ttu-id="c6abb-112">下表列出了剪切變換前後四個條形的顏色向量。</span><span class="sxs-lookup"><span data-stu-id="c6abb-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="c6abb-113">原始</span><span class="sxs-lookup"><span data-stu-id="c6abb-113">Original</span></span>|<span data-ttu-id="c6abb-114">剪切</span><span class="sxs-lookup"><span data-stu-id="c6abb-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="c6abb-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="c6abb-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="c6abb-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="c6abb-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="c6abb-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="c6abb-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="c6abb-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="c6abb-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="c6abb-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="c6abb-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="c6abb-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="c6abb-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="c6abb-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="c6abb-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="c6abb-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="c6abb-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c6abb-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c6abb-123">Compiling the Code</span></span>  
 <span data-ttu-id="c6abb-124">前面的示例設計用於 Windows 表單，它需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是事件處理常式的<xref:System.Windows.Forms.Control.Paint>參數。</span><span class="sxs-lookup"><span data-stu-id="c6abb-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="c6abb-125">替換為`ColorBars.bmp`系統上有效的圖像名稱和路徑。</span><span class="sxs-lookup"><span data-stu-id="c6abb-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6abb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6abb-126">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="c6abb-127">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="c6abb-127">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="c6abb-128">將影像重新著色</span><span class="sxs-lookup"><span data-stu-id="c6abb-128">Recoloring Images</span></span>](recoloring-images.md)
