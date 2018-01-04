---
title: "如何：繪製填滿材質的線條"
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
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0aaba7981dc68bf7bdfe6dbd45685e61f7b763a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a><span data-ttu-id="57bc2-102">如何：繪製填滿材質的線條</span><span class="sxs-lookup"><span data-stu-id="57bc2-102">How to: Draw a Line Filled with a Texture</span></span>
<span data-ttu-id="57bc2-103">而不是繪製線條，以利用純色，您可以繪製材質的線條。</span><span class="sxs-lookup"><span data-stu-id="57bc2-103">Instead of drawing a line with a solid color, you can draw a line with a texture.</span></span> <span data-ttu-id="57bc2-104">若要繪製的直線和曲線的紋理，建立<xref:System.Drawing.TextureBrush>物件，並將其傳遞<xref:System.Drawing.TextureBrush>物件<xref:System.Drawing.Pen.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="57bc2-104">To draw lines and curves with a texture, create a <xref:System.Drawing.TextureBrush> object, and pass that <xref:System.Drawing.TextureBrush> object to a <xref:System.Drawing.Pen.%23ctor%2A> constructor.</span></span> <span data-ttu-id="57bc2-105">紋理筆刷與關聯的點陣圖用於磚平面 （不可見），並畫筆筆觸時畫筆繪製線條或曲線時，發現並排紋理的特定像素為單位。</span><span class="sxs-lookup"><span data-stu-id="57bc2-105">The bitmap associated with the texture brush is used to tile the plane (invisibly), and when the pen draws a line or curve, the stroke of the pen uncovers certain pixels of the tiled texture.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57bc2-106">範例</span><span class="sxs-lookup"><span data-stu-id="57bc2-106">Example</span></span>  
 <span data-ttu-id="57bc2-107">下列範例會建立<xref:System.Drawing.Bitmap>物件從檔案`Texture1.jpg`。</span><span class="sxs-lookup"><span data-stu-id="57bc2-107">The following example creates a <xref:System.Drawing.Bitmap> object from the file `Texture1.jpg`.</span></span> <span data-ttu-id="57bc2-108">該點陣圖用來建構<xref:System.Drawing.TextureBrush>物件，而<xref:System.Drawing.TextureBrush>物件用來建構<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="57bc2-108">That bitmap is used to construct a <xref:System.Drawing.TextureBrush> object, and the <xref:System.Drawing.TextureBrush> object is used to construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="57bc2-109">若要呼叫<xref:System.Drawing.Graphics.DrawImage%2A>繪製點陣圖，以在其左上角 （0，0）。</span><span class="sxs-lookup"><span data-stu-id="57bc2-109">The call to <xref:System.Drawing.Graphics.DrawImage%2A> draws the bitmap with its upper-left corner at (0, 0).</span></span> <span data-ttu-id="57bc2-110">若要呼叫<xref:System.Drawing.Graphics.DrawEllipse%2A>使用<xref:System.Drawing.Pen>物件要繪製的材質的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="57bc2-110">The call to <xref:System.Drawing.Graphics.DrawEllipse%2A> uses the <xref:System.Drawing.Pen> object to draw a textured ellipse.</span></span>  
  
 <span data-ttu-id="57bc2-111">下圖顯示點陣圖和紋理的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="57bc2-111">The following illustration shows the bitmap and the textured ellipse.</span></span>  
  
 <span data-ttu-id="57bc2-112">![畫筆](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span><span class="sxs-lookup"><span data-stu-id="57bc2-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57bc2-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="57bc2-113">Compiling the Code</span></span>  
 <span data-ttu-id="57bc2-114">建立 Windows 表單，並處理表單的<xref:System.Windows.Forms.Control.Paint>事件。</span><span class="sxs-lookup"><span data-stu-id="57bc2-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="57bc2-115">貼上上述程式碼到<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="57bc2-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="57bc2-116">取代`Texture.jpg`您系統上有效的映像。</span><span class="sxs-lookup"><span data-stu-id="57bc2-116">Replace `Texture.jpg` with an image valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57bc2-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="57bc2-117">See Also</span></span>  
 [<span data-ttu-id="57bc2-118">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="57bc2-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="57bc2-119">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="57bc2-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
