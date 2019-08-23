---
title: 作法：複製像素以減少 Windows Forms 的閃爍
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
ms.openlocfilehash: 5a18539153c64a5059d8079f6e245115b026bb91
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950140"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="03389-102">作法：複製像素以減少 Windows Forms 的閃爍</span><span class="sxs-lookup"><span data-stu-id="03389-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="03389-103">當您以動畫顯示簡單的圖形時, 使用者有時可能會遇到閃爍或其他不想要的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="03389-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="03389-104">限制這個問題的其中一種方法是在圖形上使用 "bitblt" 進程。</span><span class="sxs-lookup"><span data-stu-id="03389-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="03389-105">Bitblt 是從原始矩形 (圖元) 到目的地矩形 (以圖元為單位) 的色彩資料的「位區塊傳輸」。</span><span class="sxs-lookup"><span data-stu-id="03389-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="03389-106">使用 Windows Forms 時, 會使用<xref:System.Drawing.Graphics.CopyFromScreen%2A> <xref:System.Drawing.Graphics>類別的方法來完成 bitblt。</span><span class="sxs-lookup"><span data-stu-id="03389-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="03389-107">在方法的參數中, 您可以指定來源和目的地 (以點為單位)、要複製的區域大小, 以及用來繪製新圖形的繪圖物件。</span><span class="sxs-lookup"><span data-stu-id="03389-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="03389-108">在下列範例中, 會在表單的<xref:System.Windows.Forms.Control.Paint>事件處理常式中繪製圖形。</span><span class="sxs-lookup"><span data-stu-id="03389-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="03389-109">然後, <xref:System.Drawing.Graphics.CopyFromScreen%2A>使用方法來複製圖形。</span><span class="sxs-lookup"><span data-stu-id="03389-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03389-110">將表單的<xref:System.Windows.Forms.Control.DoubleBuffered%2A>屬性設定`true`為, 會讓事件中的<xref:System.Windows.Forms.Control.Paint>圖形程式碼進行雙重緩衝處理。</span><span class="sxs-lookup"><span data-stu-id="03389-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="03389-111">雖然當您使用下列程式碼時, 這不會有任何明顯的效能提升, 但是在使用更複雜的圖形操作程式碼時, 這是要牢記在心的事項。</span><span class="sxs-lookup"><span data-stu-id="03389-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03389-112">範例</span><span class="sxs-lookup"><span data-stu-id="03389-112">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="03389-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="03389-113">Compiling the Code</span></span>  
 <span data-ttu-id="03389-114">上述程式碼會在表單的<xref:System.Windows.Forms.Control.Paint>事件處理常式中執行, 以便在重新繪製表單時保存圖形。</span><span class="sxs-lookup"><span data-stu-id="03389-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="03389-115">因此, 請勿在<xref:System.Windows.Forms.Form.Load>事件處理常式中呼叫圖形相關的方法, 因為如果表單已調整大小或遮蔽另一個表單, 則不會重新繪製所繪製的內容。</span><span class="sxs-lookup"><span data-stu-id="03389-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03389-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03389-116">See also</span></span>

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="03389-117">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="03389-117">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="03389-118">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="03389-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
