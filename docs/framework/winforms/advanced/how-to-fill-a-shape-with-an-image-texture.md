---
title: 如何：使用影像材質填滿圖案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: c1eb090bebcced125193c1db16087b6165d27ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523286"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="5230e-102">如何：使用影像材質填滿圖案</span><span class="sxs-lookup"><span data-stu-id="5230e-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="5230e-103">您也可以使用與紋理填入封閉的圖形<xref:System.Drawing.Image>類別和<xref:System.Drawing.TextureBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="5230e-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5230e-104">範例</span><span class="sxs-lookup"><span data-stu-id="5230e-104">Example</span></span>  
 <span data-ttu-id="5230e-105">下列範例會填滿橢圓形使用的映像。</span><span class="sxs-lookup"><span data-stu-id="5230e-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="5230e-106">程式碼會建構<xref:System.Drawing.Image>物件，並接著會將該位址傳遞<xref:System.Drawing.Image>物件做為引數<xref:System.Drawing.TextureBrush.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="5230e-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="5230e-107">第三個陳述式將映像，而第四個陳述式填滿橢圓形縮放影像的重複複本 %。</span><span class="sxs-lookup"><span data-stu-id="5230e-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="5230e-108">下列程式碼，<xref:System.Drawing.TextureBrush.Transform%2A>屬性包含它繪製前套用到影像的轉換。</span><span class="sxs-lookup"><span data-stu-id="5230e-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="5230e-109">假設原始的映像有 640 像素寬度和高度 480 像素。</span><span class="sxs-lookup"><span data-stu-id="5230e-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="5230e-110">轉換將影像縮小為 75 × 75 藉由設定水平和垂直縮放比例值。</span><span class="sxs-lookup"><span data-stu-id="5230e-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5230e-111">在下列範例中，映像大小為 75 × 75，而橢圓形的大小為 150 × 250。</span><span class="sxs-lookup"><span data-stu-id="5230e-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="5230e-112">因為映像是小於它正在填滿的橢圓形，橢圓形會並排顯示與映像。</span><span class="sxs-lookup"><span data-stu-id="5230e-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="5230e-113">已達到並排方式映像會水平及垂直重複直到圖形的界限。</span><span class="sxs-lookup"><span data-stu-id="5230e-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="5230e-114">如需可並排顯示的詳細資訊，請參閱[如何： 並排顯示影像與圖案](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md)。</span><span class="sxs-lookup"><span data-stu-id="5230e-114">For more information about tiling, see [How to: Tile a Shape with an Image](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5230e-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5230e-115">Compiling the Code</span></span>  
 <span data-ttu-id="5230e-116">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="5230e-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5230e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5230e-117">See Also</span></span>  
 [<span data-ttu-id="5230e-118">使用筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="5230e-118">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
