---
title: 如何：使用畫筆繪製線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 6a728bcaf9946b2b92ce0ee97599f4c4fd0fea69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522980"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a><span data-ttu-id="7839b-102">如何：使用畫筆繪製線條</span><span class="sxs-lookup"><span data-stu-id="7839b-102">How to: Use a Pen to Draw Lines</span></span>
<span data-ttu-id="7839b-103">若要繪製線條，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="7839b-103">To draw lines, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="7839b-104"><xref:System.Drawing.Graphics>物件提供<xref:System.Drawing.Graphics.DrawLine%2A>方法，而<xref:System.Drawing.Pen>物件儲存的行，例如色彩和寬度的功能。</span><span class="sxs-lookup"><span data-stu-id="7839b-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawLine%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7839b-105">範例</span><span class="sxs-lookup"><span data-stu-id="7839b-105">Example</span></span>  
 <span data-ttu-id="7839b-106">下列範例會繪製線條，以從 20 (10） 到 （300，100）。</span><span class="sxs-lookup"><span data-stu-id="7839b-106">The following example draws a line from (20, 10) to (300, 100).</span></span> <span data-ttu-id="7839b-107">第一個陳述式會使用<xref:System.Drawing.Pen.%23ctor%2A>類別建構函式建立黑色的畫筆。</span><span class="sxs-lookup"><span data-stu-id="7839b-107">The first statement uses the <xref:System.Drawing.Pen.%23ctor%2A> class constructor to create a black pen.</span></span> <span data-ttu-id="7839b-108">一個引數傳遞至<xref:System.Drawing.Pen.%23ctor%2A>建構函式是<xref:System.Drawing.Color>物件以建立<xref:System.Drawing.Color.FromArgb%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="7839b-108">The one argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object created with the <xref:System.Drawing.Color.FromArgb%2A> method.</span></span> <span data-ttu-id="7839b-109">值，用來建立<xref:System.Drawing.Color>物件 — （255，0，0，0）-對應色彩的 alpha、 紅色、 綠色和藍色元件。</span><span class="sxs-lookup"><span data-stu-id="7839b-109">The values used to create the <xref:System.Drawing.Color> object — (255, 0, 0, 0) — correspond to the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="7839b-110">這些值會定義不透明的黑色畫筆。</span><span class="sxs-lookup"><span data-stu-id="7839b-110">These values define an opaque black pen.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7839b-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7839b-111">Compiling the Code</span></span>  
 <span data-ttu-id="7839b-112">上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="7839b-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7839b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7839b-113">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="7839b-114">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="7839b-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="7839b-115">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="7839b-115">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
