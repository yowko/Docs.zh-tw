---
title: "如何：複製像素以降低 Windows Form 的閃動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "位元區塊轉送"
  - "bitblt"
  - "重繪閃動"
  - "重繪閃動, 在 Windows Form 中減少"
  - "圖形, 複製"
  - "圖形, 減少重繪閃動"
  - "像素, 複製"
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：複製像素以降低 Windows Form 的閃動
當以動畫顯示簡單圖形時，使用者有時可能會遇到重繪閃動或其他不希望發生的視覺效果。  避免這個問題的其中一個方式是在圖形上使用 "bitblt" 處理。  Bitblt 是色彩資料由像素起點矩形到像素目的矩形的「位元區塊轉送」。  
  
 在 Windows Form 中，可利用 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.CopyFromScreen%2A> 方法來完成 bitblt。  在方法的參數中，可以指定來源和目的 \(當做點\)、要複製的區域大小和用來繪製新形狀的圖形物件。  
  
 下列範例示範在表單的 <xref:System.Windows.Forms.Control.Paint> 事件處理常式中繪製形狀。  接著再使用 <xref:System.Drawing.Graphics.CopyFromScreen%2A> 方法來複製這個形狀。  
  
> [!NOTE]
>  如果將表單的 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 屬性設為 `true`，將會使 <xref:System.Windows.Forms.Control.Paint> 事件中的圖形架構程式碼具有雙重緩衝。  由於使用以下程式碼時這個作用並不會帶來任何明顯效能，因此當您使用更多複雜的圖形管理程式碼時必須記住這一點。  
  
## 範例  
  
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
  
## 編譯程式碼  
 上述的程式碼是在表單的 <xref:System.Windows.Forms.Control.Paint> 事件處理常式中執行，如此一來重繪表單時將會保存圖形。  因此，請勿呼叫 <xref:System.Windows.Forms.Form.Load> 事件處理常式中與圖形相關的方法，否則當表單被重新調整或被另一表單遮住時，將不會重新繪製表單的內容。  
  
## 請參閱  
 <xref:System.Drawing.CopyPixelOperation>   
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=fullName>   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)