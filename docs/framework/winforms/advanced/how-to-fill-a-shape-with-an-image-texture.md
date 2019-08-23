---
title: HOW TO：使用影像材質填滿形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911681"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="40b0e-102">作法：使用影像材質填滿形狀</span><span class="sxs-lookup"><span data-stu-id="40b0e-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="40b0e-103">您可以使用<xref:System.Drawing.Image>類別<xref:System.Drawing.TextureBrush>和類別, 以材質填滿封閉圖形。</span><span class="sxs-lookup"><span data-stu-id="40b0e-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40b0e-104">範例</span><span class="sxs-lookup"><span data-stu-id="40b0e-104">Example</span></span>  
 <span data-ttu-id="40b0e-105">下列範例會以影像填滿橢圓形。</span><span class="sxs-lookup"><span data-stu-id="40b0e-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="40b0e-106">程式<xref:System.Drawing.Image>代碼會建立物件, 然後將該<xref:System.Drawing.Image>物件的位址當做引數傳遞至<xref:System.Drawing.TextureBrush.%23ctor%2A>函式。</span><span class="sxs-lookup"><span data-stu-id="40b0e-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="40b0e-107">第三個語句會縮放影像, 而第四個語句會以重複的縮放影像複本來填滿橢圓形。</span><span class="sxs-lookup"><span data-stu-id="40b0e-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="40b0e-108">在下列程式碼中, <xref:System.Drawing.TextureBrush.Transform%2A>屬性包含在繪製之前套用至影像的轉換。</span><span class="sxs-lookup"><span data-stu-id="40b0e-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="40b0e-109">假設原始影像的寬度為640圖元, 而高度為480圖元。</span><span class="sxs-lookup"><span data-stu-id="40b0e-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="40b0e-110">轉換會藉由設定水準和垂直縮放值, 將影像縮小為75×75。</span><span class="sxs-lookup"><span data-stu-id="40b0e-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40b0e-111">在下列範例中, 影像大小為75× 75, 而橢圓形大小為150×250。</span><span class="sxs-lookup"><span data-stu-id="40b0e-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="40b0e-112">因為影像小於所填滿的橢圓形, 所以橢圓形會與影像並排顯示。</span><span class="sxs-lookup"><span data-stu-id="40b0e-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="40b0e-113">並排表示影像會以水準和垂直方式重複, 直到達到圖形的邊界為止。</span><span class="sxs-lookup"><span data-stu-id="40b0e-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="40b0e-114">如需並排顯示的詳細資訊[, 請參閱如何:以影像](how-to-tile-a-shape-with-an-image.md)並排顯示圖形。</span><span class="sxs-lookup"><span data-stu-id="40b0e-114">For more information about tiling, see [How to: Tile a Shape with an Image](how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40b0e-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="40b0e-115">Compiling the Code</span></span>  
 <span data-ttu-id="40b0e-116">上述範例是針對與 Windows Forms 搭配使用所設計, 而且它<xref:System.Windows.Forms.PaintEventArgs>需要`e`, 這<xref:System.Windows.Forms.Control.Paint>是事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="40b0e-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b0e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40b0e-117">See also</span></span>

- [<span data-ttu-id="40b0e-118">使用筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="40b0e-118">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
