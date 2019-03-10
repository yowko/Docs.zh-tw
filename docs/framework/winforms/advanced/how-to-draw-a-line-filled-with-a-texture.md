---
title: HOW TO：繪製填滿材質的線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: fd7a2aa2f6d930b0de29d8b8cbd3feacdb7a81e3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718593"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a><span data-ttu-id="b54e9-102">HOW TO：繪製填滿材質的線條</span><span class="sxs-lookup"><span data-stu-id="b54e9-102">How to: Draw a Line Filled with a Texture</span></span>
<span data-ttu-id="b54e9-103">而不是繪圖線，以使用純色，則可以繪製含有材質的線條。</span><span class="sxs-lookup"><span data-stu-id="b54e9-103">Instead of drawing a line with a solid color, you can draw a line with a texture.</span></span> <span data-ttu-id="b54e9-104">若要繪製的直線和曲線滿材質，建立<xref:System.Drawing.TextureBrush>物件，並將其傳遞<xref:System.Drawing.TextureBrush>物件到<xref:System.Drawing.Pen.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="b54e9-104">To draw lines and curves with a texture, create a <xref:System.Drawing.TextureBrush> object, and pass that <xref:System.Drawing.TextureBrush> object to a <xref:System.Drawing.Pen.%23ctor%2A> constructor.</span></span> <span data-ttu-id="b54e9-105">點陣圖相關聯的材質筆刷用來 （不可見），圖格的平面與畫筆筆觸畫筆繪製線條或曲線時，當發現拼接材質的特定像素為單位。</span><span class="sxs-lookup"><span data-stu-id="b54e9-105">The bitmap associated with the texture brush is used to tile the plane (invisibly), and when the pen draws a line or curve, the stroke of the pen uncovers certain pixels of the tiled texture.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b54e9-106">範例</span><span class="sxs-lookup"><span data-stu-id="b54e9-106">Example</span></span>  
 <span data-ttu-id="b54e9-107">下列範例會建立<xref:System.Drawing.Bitmap>檔案中的物件`Texture1.jpg`。</span><span class="sxs-lookup"><span data-stu-id="b54e9-107">The following example creates a <xref:System.Drawing.Bitmap> object from the file `Texture1.jpg`.</span></span> <span data-ttu-id="b54e9-108">該點陣圖用來建構<xref:System.Drawing.TextureBrush>物件，而<xref:System.Drawing.TextureBrush>物件可用來建構<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="b54e9-108">That bitmap is used to construct a <xref:System.Drawing.TextureBrush> object, and the <xref:System.Drawing.TextureBrush> object is used to construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="b54e9-109">若要呼叫<xref:System.Drawing.Graphics.DrawImage%2A>繪製點陣圖，包含在其左上角 （0，0）。</span><span class="sxs-lookup"><span data-stu-id="b54e9-109">The call to <xref:System.Drawing.Graphics.DrawImage%2A> draws the bitmap with its upper-left corner at (0, 0).</span></span> <span data-ttu-id="b54e9-110">若要在呼叫<xref:System.Drawing.Graphics.DrawEllipse%2A>使用<xref:System.Drawing.Pen>物件要繪製紋理的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="b54e9-110">The call to <xref:System.Drawing.Graphics.DrawEllipse%2A> uses the <xref:System.Drawing.Pen> object to draw a textured ellipse.</span></span>  
  
 <span data-ttu-id="b54e9-111">下圖顯示點陣圖和紋理的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="b54e9-111">The following illustration shows the bitmap and the textured ellipse.</span></span>  
  
 <span data-ttu-id="b54e9-112">![畫筆](./media/pens7.png "pens7")</span><span class="sxs-lookup"><span data-stu-id="b54e9-112">![Pens](./media/pens7.png "pens7")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b54e9-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b54e9-113">Compiling the Code</span></span>  
 <span data-ttu-id="b54e9-114">建立 Windows 表單，並處理表單的<xref:System.Windows.Forms.Control.Paint>事件。</span><span class="sxs-lookup"><span data-stu-id="b54e9-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="b54e9-115">貼上上述程式碼到<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b54e9-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="b54e9-116">取代`Texture.jpg`您系統上有效的映像。</span><span class="sxs-lookup"><span data-stu-id="b54e9-116">Replace `Texture.jpg` with an image valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b54e9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b54e9-117">See also</span></span>
- [<span data-ttu-id="b54e9-118">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="b54e9-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="b54e9-119">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="b54e9-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
