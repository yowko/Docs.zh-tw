---
title: 如何：旋轉色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 8d2717dd7b819e963126072279b361fda02188bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111331"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="7985c-102">如何：旋轉色彩</span><span class="sxs-lookup"><span data-stu-id="7985c-102">How to: Rotate Colors</span></span>
<span data-ttu-id="7985c-103">四維色彩空間中的旋轉很難視覺化。</span><span class="sxs-lookup"><span data-stu-id="7985c-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="7985c-104">通過同意固定其中一種顏色元件，我們可以更輕鬆地視覺化旋轉。</span><span class="sxs-lookup"><span data-stu-id="7985c-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="7985c-105">假設我們同意將 Alpha 元件固定為 1（完全不透明）。</span><span class="sxs-lookup"><span data-stu-id="7985c-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="7985c-106">然後，我們可以用紅色、綠色和藍色軸視覺化三維色彩空間，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="7985c-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 ![顯示紅色、綠色和藍色軸旋轉的插圖。](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 <span data-ttu-id="7985c-108">顏色可以被視為 3D 空間中的點。</span><span class="sxs-lookup"><span data-stu-id="7985c-108">A color can be thought of as a point in 3D space.</span></span> <span data-ttu-id="7985c-109">例如，空格中的點 （1， 0， 0） 表示紅色，空格中的點 （0， 1， 0） 表示綠色。</span><span class="sxs-lookup"><span data-stu-id="7985c-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="7985c-110">下圖顯示了在紅綠平面中通過 60 度角旋轉顏色 （1， 0， 0） 的含義。</span><span class="sxs-lookup"><span data-stu-id="7985c-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="7985c-111">與紅-綠平面平行的平面上的旋轉可視為藍色軸的旋轉。</span><span class="sxs-lookup"><span data-stu-id="7985c-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 ![顯示藍色軸旋轉的插圖。](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 <span data-ttu-id="7985c-113">下圖演示如何初始化顏色矩陣以對三個座標軸（紅色、綠色、藍色）執行每個座標軸的旋轉：</span><span class="sxs-lookup"><span data-stu-id="7985c-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue):</span></span>  
  
 ![初始化顏色矩陣以執行大約三個軸的旋轉。](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a><span data-ttu-id="7985c-115">範例</span><span class="sxs-lookup"><span data-stu-id="7985c-115">Example</span></span>  
 <span data-ttu-id="7985c-116">下面的示例採用一個全部為一種顏色（1，0，0.6）的圖像，並應用 60 度旋轉藍色軸。</span><span class="sxs-lookup"><span data-stu-id="7985c-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="7985c-117">旋轉角度在與紅綠色平面平行的平面中掃出。</span><span class="sxs-lookup"><span data-stu-id="7985c-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="7985c-118">下圖顯示了左側的原始圖像和右側的顏色旋轉圖像：</span><span class="sxs-lookup"><span data-stu-id="7985c-118">The following illustration shows the original image on the left and the color-rotated image on the right:</span></span>  
  
 ![顯示原始圖像和顏色旋轉圖像的插圖。](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 <span data-ttu-id="7985c-120">下圖顯示了以下代碼中執行的顏色旋轉的視覺化效果：</span><span class="sxs-lookup"><span data-stu-id="7985c-120">The following illustration shows a visualization of the color rotation performed in the following code:</span></span>
  
 ![顯示顏色旋轉視覺化的插圖。](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7985c-122">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7985c-122">Compiling the Code</span></span>  
 <span data-ttu-id="7985c-123">前面的示例設計用於 Windows 表單，它需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是事件處理常式的<xref:System.Windows.Forms.Control.Paint>參數。</span><span class="sxs-lookup"><span data-stu-id="7985c-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="7985c-124">替換為`RotationInput.bmp`系統上有效的映射檔案名和路徑。</span><span class="sxs-lookup"><span data-stu-id="7985c-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7985c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7985c-125">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="7985c-126">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="7985c-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="7985c-127">將影像重新著色</span><span class="sxs-lookup"><span data-stu-id="7985c-127">Recoloring Images</span></span>](recoloring-images.md)
