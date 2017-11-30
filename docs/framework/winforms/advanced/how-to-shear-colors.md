---
title: "如何：切變色彩"
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
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f89bb5d87ef58c5ecda7be4cb9fb41da08e8a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="8aea5-102">如何：切變色彩</span><span class="sxs-lookup"><span data-stu-id="8aea5-102">How to: Shear Colors</span></span>
<span data-ttu-id="8aea5-103">切變增加，或另一個色彩元件等比例的量減少色彩元件。</span><span class="sxs-lookup"><span data-stu-id="8aea5-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="8aea5-104">例如，請考慮的轉換一半的值的藍色元件其中增加的紅色元件。</span><span class="sxs-lookup"><span data-stu-id="8aea5-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="8aea5-105">在這類轉換 （0.7，0.5，1），就會變成 （0.2，0.5，1） 的色彩。</span><span class="sxs-lookup"><span data-stu-id="8aea5-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="8aea5-106">新的紅色元件為 0.2 + (1/2)(1) = 0.7。</span><span class="sxs-lookup"><span data-stu-id="8aea5-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8aea5-107">範例</span><span class="sxs-lookup"><span data-stu-id="8aea5-107">Example</span></span>  
 <span data-ttu-id="8aea5-108">下列範例會建構<xref:System.Drawing.Image>ColorBars4.bmp 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="8aea5-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="8aea5-109">程式碼會接著套用切變映像中的每個像素在上一段所述的轉換。</span><span class="sxs-lookup"><span data-stu-id="8aea5-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="8aea5-110">下圖顯示在右側的原始左側的映像和分歧映像。</span><span class="sxs-lookup"><span data-stu-id="8aea5-110">The following illustration shows the original image on the left and the sheared image on the right.</span></span>  
  
 <span data-ttu-id="8aea5-111">![分歧色彩](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span><span class="sxs-lookup"><span data-stu-id="8aea5-111">![Shear Colors](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span></span>  
  
 <span data-ttu-id="8aea5-112">下表列出四個橫條的色彩向量切變轉換之前和之後。</span><span class="sxs-lookup"><span data-stu-id="8aea5-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="8aea5-113">原始</span><span class="sxs-lookup"><span data-stu-id="8aea5-113">Original</span></span>|<span data-ttu-id="8aea5-114">修剪</span><span class="sxs-lookup"><span data-stu-id="8aea5-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="8aea5-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="8aea5-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="8aea5-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="8aea5-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="8aea5-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="8aea5-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="8aea5-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="8aea5-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="8aea5-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="8aea5-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="8aea5-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="8aea5-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="8aea5-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="8aea5-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="8aea5-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="8aea5-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8aea5-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8aea5-123">Compiling the Code</span></span>  
 <span data-ttu-id="8aea5-124">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="8aea5-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="8aea5-125">取代`ColorBars.bmp`映像名稱與您系統上有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="8aea5-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aea5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8aea5-126">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="8aea5-127">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="8aea5-127">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="8aea5-128">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="8aea5-128">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
