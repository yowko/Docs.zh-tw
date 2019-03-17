---
title: HOW TO：旋轉色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: d3fa49e6129c93df93378fb2b607a87a5a0be087
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125885"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="51de9-102">HOW TO：旋轉色彩</span><span class="sxs-lookup"><span data-stu-id="51de9-102">How to: Rotate Colors</span></span>
<span data-ttu-id="51de9-103">四維色彩空間中的旋轉很難視覺化。</span><span class="sxs-lookup"><span data-stu-id="51de9-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="51de9-104">我們可以輕鬆地視覺化起來要保留固定的色彩元件之一。</span><span class="sxs-lookup"><span data-stu-id="51de9-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="51de9-105">假設同意將固定為 1 的 alpha 元件 （完全不透明）。</span><span class="sxs-lookup"><span data-stu-id="51de9-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="51de9-106">然後我們可以將三維色彩空間視覺化具有紅色、 綠色和藍色的軸，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="51de9-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 ![顯示具有紅色、 綠色和藍色軸的旋轉的圖例。](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 <span data-ttu-id="51de9-108">色彩可以視為在 3d 空間中的點。</span><span class="sxs-lookup"><span data-stu-id="51de9-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="51de9-109">比方說，空間中的點 （1，0，0） 表示的色彩為紅色，並在空間中的點 （0、 1、 0） 代表綠色的色彩。</span><span class="sxs-lookup"><span data-stu-id="51de9-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="51de9-110">下圖顯示旋轉的色彩 （1，0，0） 的意義透過紅色、 綠色分別平面中的 60 度的角度。</span><span class="sxs-lookup"><span data-stu-id="51de9-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="51de9-111">紅色、 綠色分別平面平行的平面中的循環可視為藍色軸旋轉。</span><span class="sxs-lookup"><span data-stu-id="51de9-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 ![顯示藍色軸旋轉的圖例。](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 <span data-ttu-id="51de9-113">下圖顯示如何初始化色彩矩陣，以執行需三個座標的軸 （紅色、 綠色、 藍色） 之每個旋轉：</span><span class="sxs-lookup"><span data-stu-id="51de9-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue):</span></span>  
  
 ![初始化色彩矩陣，以執行需三個座標軸的旋轉。](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a><span data-ttu-id="51de9-115">範例</span><span class="sxs-lookup"><span data-stu-id="51de9-115">Example</span></span>  
 <span data-ttu-id="51de9-116">下列範例會為所有的一種色彩 （1，0，0.6） 與藍色軸 60 度旋轉套用的映像。</span><span class="sxs-lookup"><span data-stu-id="51de9-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="51de9-117">旋轉的角度會是紅色、 綠色分別平面平行的平面中，只要進行清理出。</span><span class="sxs-lookup"><span data-stu-id="51de9-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="51de9-118">下圖顯示原始的映像，在左邊和右邊的旋轉色彩的映像：</span><span class="sxs-lookup"><span data-stu-id="51de9-118">The following illustration shows the original image on the left and the color-rotated image on the right:</span></span>  
  
 ![顯示原始影像和色彩旋轉影像的圖例。](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 <span data-ttu-id="51de9-120">下圖顯示色彩旋轉，執行下列程式碼中的視覺效果：</span><span class="sxs-lookup"><span data-stu-id="51de9-120">The following illustration shows a visualization of the color rotation performed in the following code:</span></span>
  
 ![顯示色彩旋轉的視覺效果的圖例。](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="51de9-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="51de9-122">Compiling the Code</span></span>  
 <span data-ttu-id="51de9-123">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="51de9-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="51de9-124">取代`RotationInput.bmp`映像檔案名稱和您系統上有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="51de9-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51de9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51de9-125">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="51de9-126">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="51de9-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="51de9-127">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="51de9-127">Recoloring Images</span></span>](recoloring-images.md)
