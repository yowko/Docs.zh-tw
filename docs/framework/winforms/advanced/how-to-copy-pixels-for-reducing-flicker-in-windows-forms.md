---
title: HOW TO：複製像素以減少 Windows Forms 的閃爍
ms.date: 03/30/2017
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
ms.openlocfilehash: e3d1c2b681e98dc7c45467683924dd4022eb377e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094030"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="35db6-102">HOW TO：複製像素以減少 Windows Forms 的閃爍</span><span class="sxs-lookup"><span data-stu-id="35db6-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="35db6-103">當您以動畫顯示簡單的圖形時，使用者可以有時會遇到，閃爍或其他不想要的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="35db6-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="35db6-104">限制此問題的一個方法是在圖形上使用 「 bitblt 」 程序。</span><span class="sxs-lookup"><span data-stu-id="35db6-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="35db6-105">Bitblt 是位元區塊傳輸 的色彩資料從像素原始矩形到目的地矩形的像素為單位。</span><span class="sxs-lookup"><span data-stu-id="35db6-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="35db6-106">使用 Windows Form bitblt 會藉由<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法的<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="35db6-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="35db6-107">在方法的參數中，您可以指定來源和目的地 （以點為單位）、 進行複製，區域的大小和圖形物件用來繪製新的形狀。</span><span class="sxs-lookup"><span data-stu-id="35db6-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="35db6-108">在下列範例中，在表單上繪製的形狀其<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="35db6-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="35db6-109">然後，<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法用來複製圖形。</span><span class="sxs-lookup"><span data-stu-id="35db6-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35db6-110">設定表單的<xref:System.Windows.Forms.Control.DoubleBuffered%2A>屬性，以`true`將進行中的圖形化程式碼<xref:System.Windows.Forms.Control.Paint>是雙重緩衝的事件。</span><span class="sxs-lookup"><span data-stu-id="35db6-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="35db6-111">使用下列程式碼時，這不會有任何顯著的效能提升，而是要牢記在心，使用更複雜的圖形操作程式碼時。</span><span class="sxs-lookup"><span data-stu-id="35db6-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35db6-112">範例</span><span class="sxs-lookup"><span data-stu-id="35db6-112">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="35db6-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="35db6-113">Compiling the Code</span></span>  
 <span data-ttu-id="35db6-114">上述程式碼執行在表單的<xref:System.Windows.Forms.Control.Paint>事件處理常式，讓圖形保存表單會重繪時。</span><span class="sxs-lookup"><span data-stu-id="35db6-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="35db6-115">因此，請勿呼叫圖形相關的方法<xref:System.Windows.Forms.Form.Load>事件處理常式，因為如果調整大小或遮蔽另一種形式的表單時，不重新繪製的繪製的內容。</span><span class="sxs-lookup"><span data-stu-id="35db6-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35db6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35db6-116">See also</span></span>

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="35db6-117">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="35db6-117">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="35db6-118">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="35db6-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
