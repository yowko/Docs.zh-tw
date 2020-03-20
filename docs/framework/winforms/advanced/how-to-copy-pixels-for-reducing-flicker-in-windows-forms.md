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
ms.openlocfilehash: a25295532d7123d92bcacc6828d3e8cfcc839d6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182578"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>如何：複製像素以降低 Windows Form 的閃動
為簡單圖形設置動畫時，使用者有時會遇到閃爍或其他不良視覺效果。 限制此問題的一種方法是在圖形上使用"bitblt"進程。 Bitblt 是顏色資料從圖元源矩形到圖元目標矩形的"位塊傳輸"。  
  
 使用 Windows 表單，使用<xref:System.Drawing.Graphics.CopyFromScreen%2A><xref:System.Drawing.Graphics>類的方法完成 bitblt。 在方法的參數中，指定源和目標（作為點）、要複製的區域的大小以及用於繪製新形狀的繪圖物件。  
  
 在下面的示例中，在其<xref:System.Windows.Forms.Control.Paint>事件處理常式中，表單上繪製了一個形狀。 然後，<xref:System.Drawing.Graphics.CopyFromScreen%2A>該方法用於複製形狀。  
  
> [!NOTE]
> 將表單的屬性<xref:System.Windows.Forms.Control.DoubleBuffered%2A>設置為`true`將使<xref:System.Windows.Forms.Control.Paint>事件中基於圖形的代碼加倍緩衝。 雖然使用以下代碼時，性能不會有任何明顯的提升，但在使用更複雜的圖形操作代碼時，需要牢記這一點。  
  
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
 上面的代碼在表單<xref:System.Windows.Forms.Control.Paint>的事件處理常式中運行，以便在重繪表單時圖形保留。 因此，不要在<xref:System.Windows.Forms.Form.Load>事件處理常式中調用與圖形相關的方法，因為如果表單被另一種形式調整大小或遮蓋，將不會重新繪製繪製的內容。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
