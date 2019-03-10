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
ms.openlocfilehash: cb3824d8a5a5674b83124301dbfbd5a3ba60effa
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720614"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="b582f-102">HOW TO：旋轉色彩</span><span class="sxs-lookup"><span data-stu-id="b582f-102">How to: Rotate Colors</span></span>
<span data-ttu-id="b582f-103">四維色彩空間中的旋轉很難視覺化。</span><span class="sxs-lookup"><span data-stu-id="b582f-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="b582f-104">我們可以輕鬆地視覺化起來要保留固定的色彩元件之一。</span><span class="sxs-lookup"><span data-stu-id="b582f-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="b582f-105">假設同意將固定為 1 的 alpha 元件 （完全不透明）。</span><span class="sxs-lookup"><span data-stu-id="b582f-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="b582f-106">然後我們可以將三維色彩空間視覺化具有紅色、 綠色和藍色的軸，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b582f-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="b582f-107">![重新著色](./media/recoloring03.gif "recoloring03")</span><span class="sxs-lookup"><span data-stu-id="b582f-107">![Recoloring](./media/recoloring03.gif "recoloring03")</span></span>  
  
 <span data-ttu-id="b582f-108">色彩可以視為在 3d 空間中的點。</span><span class="sxs-lookup"><span data-stu-id="b582f-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="b582f-109">比方說，空間中的點 （1，0，0） 表示的色彩為紅色，並在空間中的點 （0、 1、 0） 代表綠色的色彩。</span><span class="sxs-lookup"><span data-stu-id="b582f-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="b582f-110">下圖顯示旋轉的色彩 （1，0，0） 的意義透過紅色、 綠色分別平面中的 60 度的角度。</span><span class="sxs-lookup"><span data-stu-id="b582f-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="b582f-111">紅色、 綠色分別平面平行的平面中的循環可視為藍色軸旋轉。</span><span class="sxs-lookup"><span data-stu-id="b582f-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 <span data-ttu-id="b582f-112">![重新著色](./media/recoloring04.gif "recoloring04")</span><span class="sxs-lookup"><span data-stu-id="b582f-112">![Recoloring](./media/recoloring04.gif "recoloring04")</span></span>  
  
 <span data-ttu-id="b582f-113">下圖顯示如何初始化色彩矩陣，以執行每一個的三個座標的軸 （紅色、 綠色、 藍色） 的旋轉。</span><span class="sxs-lookup"><span data-stu-id="b582f-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue).</span></span>  
  
 <span data-ttu-id="b582f-114">![重新著色](./media/recoloring05.gif "recoloring05")</span><span class="sxs-lookup"><span data-stu-id="b582f-114">![Recoloring](./media/recoloring05.gif "recoloring05")</span></span>  
  
## <a name="example"></a><span data-ttu-id="b582f-115">範例</span><span class="sxs-lookup"><span data-stu-id="b582f-115">Example</span></span>  
 <span data-ttu-id="b582f-116">下列範例會為所有的一種色彩 （1，0，0.6） 與藍色軸 60 度旋轉套用的映像。</span><span class="sxs-lookup"><span data-stu-id="b582f-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="b582f-117">旋轉的角度會是紅色、 綠色分別平面平行的平面中，只要進行清理出。</span><span class="sxs-lookup"><span data-stu-id="b582f-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="b582f-118">下圖顯示原始的映像，在左邊和右邊的旋轉色彩的映像。</span><span class="sxs-lookup"><span data-stu-id="b582f-118">The following illustration shows the original image on the left and the color-rotated image on the right.</span></span>  
  
 <span data-ttu-id="b582f-119">![旋轉色彩](./media/colortrans5.png "colortrans5")</span><span class="sxs-lookup"><span data-stu-id="b582f-119">![Rotate Colors](./media/colortrans5.png "colortrans5")</span></span>  
  
 <span data-ttu-id="b582f-120">下圖顯示色彩旋轉，執行下列程式碼中的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="b582f-120">The following illustration shows a visualization of the color rotation performed in the following code.</span></span>  
  
 <span data-ttu-id="b582f-121">![重新著色](./media/recoloring06.gif "recoloring06")</span><span class="sxs-lookup"><span data-stu-id="b582f-121">![Recoloring](./media/recoloring06.gif "recoloring06")</span></span>  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b582f-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b582f-122">Compiling the Code</span></span>  
 <span data-ttu-id="b582f-123">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="b582f-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="b582f-124">取代`RotationInput.bmp`映像檔案名稱和您系統上有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="b582f-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b582f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b582f-125">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="b582f-126">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="b582f-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="b582f-127">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="b582f-127">Recoloring Images</span></span>](recoloring-images.md)
