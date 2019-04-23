---
title: HOW TO：填滿開放圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: addcf959e429974b9306353abb743bb2bb3114e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174560"
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="8beea-102">HOW TO：填滿開放圖形</span><span class="sxs-lookup"><span data-stu-id="8beea-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="8beea-103">您可以藉由傳遞填滿的路徑<xref:System.Drawing.Drawing2D.GraphicsPath>物件至<xref:System.Drawing.Graphics.FillPath%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8beea-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="8beea-104"><xref:System.Drawing.Graphics.FillPath%2A>方法填入填滿模式 （替代或捲繞） 根據目前設定路徑的路徑。</span><span class="sxs-lookup"><span data-stu-id="8beea-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="8beea-105">如果路徑中有任何開啟的數字，如同這些數字都已關閉，會填滿的路徑。</span><span class="sxs-lookup"><span data-stu-id="8beea-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="8beea-106">關閉圖表，藉由透過其結束點繪製一條直線，到它的起點。</span><span class="sxs-lookup"><span data-stu-id="8beea-106">closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8beea-107">範例</span><span class="sxs-lookup"><span data-stu-id="8beea-107">Example</span></span>  
 <span data-ttu-id="8beea-108">下列範例會建立一個開放的圖表 （弧線） 和一個封閉的圖形 （橢圓形） 的路徑。</span><span class="sxs-lookup"><span data-stu-id="8beea-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="8beea-109"><xref:System.Drawing.Graphics.FillPath%2A>方法中填入預設填滿模式中，也就是根據路徑<xref:System.Drawing.Drawing2D.FillMode.Alternate>。</span><span class="sxs-lookup"><span data-stu-id="8beea-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="8beea-110">下圖顯示的範例程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="8beea-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="8beea-111">請注意，要填滿的路徑 (根據<xref:System.Drawing.Drawing2D.FillMode.Alternate>) 一樣開放的圖表已關閉一條直線透過其結束點至它的起點。</span><span class="sxs-lookup"><span data-stu-id="8beea-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 ![此圖顯示 FillPath 方法的輸出](./media/how-to-fill-open-figures/fill-path-alternate-mode.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8beea-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8beea-113">Compiling the Code</span></span>  
 <span data-ttu-id="8beea-114">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8beea-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8beea-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8beea-115">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [<span data-ttu-id="8beea-116">GDI+ 中的圖形路徑</span><span class="sxs-lookup"><span data-stu-id="8beea-116">Graphics Paths in GDI+</span></span>](graphics-paths-in-gdi.md)
