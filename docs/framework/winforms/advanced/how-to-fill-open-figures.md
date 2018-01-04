---
title: "如何：填滿開放圖形"
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
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c020e5f7306e73ee97dff0b492b04b5a153059cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="b1f06-102">如何：填滿開放圖形</span><span class="sxs-lookup"><span data-stu-id="b1f06-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="b1f06-103">您可以藉由傳遞填滿路徑<xref:System.Drawing.Drawing2D.GraphicsPath>物件<xref:System.Drawing.Graphics.FillPath%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b1f06-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="b1f06-104"><xref:System.Drawing.Graphics.FillPath%2A>方法填入填滿模式 （替代或捲繞） 根據目前設定路徑的路徑。</span><span class="sxs-lookup"><span data-stu-id="b1f06-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="b1f06-105">如果路徑有任何開啟的數字，如同這些數字已關閉，已填入的路徑。</span><span class="sxs-lookup"><span data-stu-id="b1f06-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="b1f06-106">關閉圖繪製直線其結束點從它的起點。</span><span class="sxs-lookup"><span data-stu-id="b1f06-106"> closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1f06-107">範例</span><span class="sxs-lookup"><span data-stu-id="b1f06-107">Example</span></span>  
 <span data-ttu-id="b1f06-108">下列範例會建立一個開放的圖表 （弧形） 和一個封閉的圖形 （橢圓形） 的路徑。</span><span class="sxs-lookup"><span data-stu-id="b1f06-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="b1f06-109"><xref:System.Drawing.Graphics.FillPath%2A>方法中填入預設填滿模式，這是根據路徑<xref:System.Drawing.Drawing2D.FillMode.Alternate>。</span><span class="sxs-lookup"><span data-stu-id="b1f06-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="b1f06-110">下圖顯示的範例程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="b1f06-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="b1f06-111">請注意，要填滿的路徑 (根據<xref:System.Drawing.Drawing2D.FillMode.Alternate>) 如同開放的圖表已關閉直線從其結束點至它的起點。</span><span class="sxs-lookup"><span data-stu-id="b1f06-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 <span data-ttu-id="b1f06-112">![填入開啟路徑](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span><span class="sxs-lookup"><span data-stu-id="b1f06-112">![Fill Open Path](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1f06-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b1f06-113">Compiling the Code</span></span>  
 <span data-ttu-id="b1f06-114">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="b1f06-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f06-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1f06-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="b1f06-116">GDI+ 中的圖形路徑</span><span class="sxs-lookup"><span data-stu-id="b1f06-116">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
