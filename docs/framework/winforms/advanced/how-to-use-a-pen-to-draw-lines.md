---
title: HOW TO：使用畫筆繪製線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: e24d02c2c6ab7537f968c013eb91838eb0bb812a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730928"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a><span data-ttu-id="b324e-102">HOW TO：使用畫筆繪製線條</span><span class="sxs-lookup"><span data-stu-id="b324e-102">How to: Use a Pen to Draw Lines</span></span>
<span data-ttu-id="b324e-103">若要繪製線條，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="b324e-103">To draw lines, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="b324e-104"><xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.DrawLine%2A>方法，而<xref:System.Drawing.Pen>物件會儲存的行，例如色彩和寬度的功能。</span><span class="sxs-lookup"><span data-stu-id="b324e-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawLine%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b324e-105">範例</span><span class="sxs-lookup"><span data-stu-id="b324e-105">Example</span></span>  
 <span data-ttu-id="b324e-106">下列範例會繪製中的行 20 (10） 到 （300，100）。</span><span class="sxs-lookup"><span data-stu-id="b324e-106">The following example draws a line from (20, 10) to (300, 100).</span></span> <span data-ttu-id="b324e-107">第一個陳述式會使用<xref:System.Drawing.Pen.%23ctor%2A>類別建構函式建立黑色的畫筆。</span><span class="sxs-lookup"><span data-stu-id="b324e-107">The first statement uses the <xref:System.Drawing.Pen.%23ctor%2A> class constructor to create a black pen.</span></span> <span data-ttu-id="b324e-108">一個引數傳遞給<xref:System.Drawing.Pen.%23ctor%2A>建構函式<xref:System.Drawing.Color>物件以建立<xref:System.Drawing.Color.FromArgb%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b324e-108">The one argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object created with the <xref:System.Drawing.Color.FromArgb%2A> method.</span></span> <span data-ttu-id="b324e-109">值，用來建立<xref:System.Drawing.Color>物件 — （255，0，0，0），對應色彩的 alpha、 紅色、 綠色和藍色元件。</span><span class="sxs-lookup"><span data-stu-id="b324e-109">The values used to create the <xref:System.Drawing.Color> object — (255, 0, 0, 0) — correspond to the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="b324e-110">這些值會定義不透明的黑色畫筆。</span><span class="sxs-lookup"><span data-stu-id="b324e-110">These values define an opaque black pen.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b324e-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b324e-111">Compiling the Code</span></span>  
 <span data-ttu-id="b324e-112">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b324e-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b324e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b324e-113">See also</span></span>
- <xref:System.Drawing.Pen>
- [<span data-ttu-id="b324e-114">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="b324e-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="b324e-115">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="b324e-115">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
