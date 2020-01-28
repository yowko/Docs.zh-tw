---
title: 如何：複製圖元以減少閃爍
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
ms.openlocfilehash: 299041e7038d5bd5b9824d668b3f47d842030ac7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746480"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>如何：複製像素以降低 Windows Form 的閃動
當您以動畫顯示簡單的圖形時，使用者有時可能會遇到閃爍或其他不想要的視覺效果。 限制這個問題的其中一種方法是在圖形上使用 "bitblt" 進程。 Bitblt 是從原始矩形（圖元）到目的地矩形（以圖元為單位）的色彩資料的「位區塊傳輸」。  
  
 使用 Windows Forms 時，會使用 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.CopyFromScreen%2A> 方法來完成 bitblt。 在方法的參數中，您可以指定來源和目的地（以點為單位）、要複製的區域大小，以及用來繪製新圖形的繪圖物件。  
  
 在下列範例中，會在表單的 <xref:System.Windows.Forms.Control.Paint> 事件處理常式中繪製圖形。 然後，使用 <xref:System.Drawing.Graphics.CopyFromScreen%2A> 方法來複製圖形。  
  
> [!NOTE]
> 將表單的 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 屬性設定為 `true` 會使 <xref:System.Windows.Forms.Control.Paint> 事件中以圖形為基礎的程式碼進行雙重緩衝處理。 雖然當您使用下列程式碼時，這不會有任何明顯的效能提升，但是在使用更複雜的圖形操作程式碼時，這是要牢記在心的事項。  
  
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
 上述程式碼會在表單的 <xref:System.Windows.Forms.Control.Paint> 事件處理常式中執行，以便在重新繪製表單時保存圖形。 因此，請勿在 <xref:System.Windows.Forms.Form.Load> 事件處理常式中呼叫與圖形相關的方法，因為如果表單調整大小或遮蔽另一個表單，則不會重新繪製所繪製的內容。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
