---
title: 如何：複製像素以降低 Windows Form 的閃動
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
ms.openlocfilehash: 65428132c885191b62c3b4a76c8937bf8f3f6732
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522040"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>如何：複製像素以降低 Windows Form 的閃動
當您以動畫顯示簡單的圖形時，使用者可以有時會遇到，閃爍或其他不想要的視覺效果。 限制這個問題的一種方式是在圖形上使用 「 bitblt 」 程序。 Bitblt 即是 」 位元區塊傳送 」 的色彩資料從起點的像素矩形到目的地矩形的像素為單位。  
  
 使用 Windows Form bitblt 會藉由<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法<xref:System.Drawing.Graphics>類別。 在方法的參數，您可以指定來源和目的地 （以點為單位）、 要複製區域的大小和用來繪製新圖形的圖形物件。  
  
 在下列範例在表單上繪製的形狀其<xref:System.Windows.Forms.Control.Paint>事件處理常式。 然後，<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法用來複製圖形。  
  
> [!NOTE]
>  設定表單的<xref:System.Windows.Forms.Control.DoubleBuffered%2A>屬性`true`將圖形化中的程式碼<xref:System.Windows.Forms.Control.Paint>事件是雙重緩衝。 雖然這不會有任何明顯效能提升使用下列程式碼時，卻是某個動作，請記住，使用更複雜的圖形操作類型程式碼時。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述程式碼執行的表單中<xref:System.Windows.Forms.Control.Paint>事件處理常式，讓圖形保存表單會重新繪製時。 因此，請勿呼叫圖形相關的方法<xref:System.Windows.Forms.Form.Load>事件處理常式，因為內容將不會重新繪製如果調整大小或遮蔽另一種形式的形式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.CopyPixelOperation>  
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
