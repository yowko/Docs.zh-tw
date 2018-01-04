---
title: "如何：複製像素以降低 Windows Form 的閃動"
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
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17253e21739911d4aa0541fde9ae205b0be1c5a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="0edbc-102">如何：複製像素以降低 Windows Form 的閃動</span><span class="sxs-lookup"><span data-stu-id="0edbc-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="0edbc-103">當您以動畫顯示簡單的圖形時，使用者可以有時會遇到，閃爍或其他不想要的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="0edbc-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="0edbc-104">限制這個問題的一種方式是在圖形上使用 「 bitblt 」 程序。</span><span class="sxs-lookup"><span data-stu-id="0edbc-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="0edbc-105">Bitblt 即是 」 位元區塊傳送 」 的色彩資料從起點的像素矩形到目的地矩形的像素為單位。</span><span class="sxs-lookup"><span data-stu-id="0edbc-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="0edbc-106">使用 Windows Form bitblt 會藉由<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="0edbc-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="0edbc-107">在方法的參數，您可以指定來源和目的地 （以點為單位）、 要複製區域的大小和用來繪製新圖形的圖形物件。</span><span class="sxs-lookup"><span data-stu-id="0edbc-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="0edbc-108">在下列範例在表單上繪製的形狀其<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="0edbc-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="0edbc-109">然後，<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法用來複製圖形。</span><span class="sxs-lookup"><span data-stu-id="0edbc-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0edbc-110">設定表單的<xref:System.Windows.Forms.Control.DoubleBuffered%2A>屬性`true`將圖形化中的程式碼<xref:System.Windows.Forms.Control.Paint>事件是雙重緩衝。</span><span class="sxs-lookup"><span data-stu-id="0edbc-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="0edbc-111">雖然這不會有任何明顯效能提升使用下列程式碼時，卻是某個動作，請記住，使用更複雜的圖形操作類型程式碼時。</span><span class="sxs-lookup"><span data-stu-id="0edbc-111">While this will not have any discernable performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0edbc-112">範例</span><span class="sxs-lookup"><span data-stu-id="0edbc-112">Example</span></span>  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0edbc-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0edbc-113">Compiling the Code</span></span>  
 <span data-ttu-id="0edbc-114">上述程式碼執行的表單中<xref:System.Windows.Forms.Control.Paint>事件處理常式，讓圖形保存表單會重新繪製時。</span><span class="sxs-lookup"><span data-stu-id="0edbc-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="0edbc-115">因此，請勿呼叫圖形相關的方法<xref:System.Windows.Forms.Form.Load>事件處理常式，因為內容將不會重新繪製如果調整大小或遮蔽另一種形式的形式。</span><span class="sxs-lookup"><span data-stu-id="0edbc-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0edbc-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="0edbc-116">See Also</span></span>  
 <xref:System.Drawing.CopyPixelOperation>  
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="0edbc-117">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="0edbc-117">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="0edbc-118">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="0edbc-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
