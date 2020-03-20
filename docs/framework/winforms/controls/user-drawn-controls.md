---
title: 使用者自訂描繪控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182015"
---
# <a name="user-drawn-controls"></a>使用者自訂描繪控制項
.NET 框架使您能夠輕鬆開發自己的控制項。 您可以創建使用者控制項，這是一組由代碼綁定在一起的標準控制項，也可以從零開始設計自己的控制項。 您甚至可以使用繼承創建從現有控制項繼承的控制項，並添加到其固有功能。 無論您使用何種方法，.NET Framework 都提供了為創建的任何控制項繪製自訂圖形介面的功能。  
  
 控制項的繪製是通過在控制項方法中執行代碼來完成的<xref:System.Windows.Forms.Control.OnPaint%2A>。 <xref:System.Windows.Forms.Control.OnPaint%2A>方法的單個參數是一個<xref:System.Windows.Forms.PaintEventArgs>物件，該物件提供呈現控制項所需的所有資訊和功能。 提供<xref:System.Windows.Forms.PaintEventArgs>將在呈現控制項時使用的兩個主體物件作為屬性：  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件 - 表示將繪製的控制項部分的矩形。 這可以是整個控制項，也可以是控制項的一部分，具體取決於控制項的繪製方式。  
  
- <xref:System.Drawing.Graphics>物件 - 封裝多個面向圖形的物件和方法，這些物件和方法提供了繪製控制項所需的功能。  
  
 有關<xref:System.Drawing.Graphics>物件以及如何使用它的詳細資訊，請參閱[如何：為繪圖創建繪圖物件](../advanced/how-to-create-graphics-objects-for-drawing.md)。  
  
 每當<xref:System.Windows.Forms.Control.OnPaint%2A>在螢幕上繪製或刷新控制項時，都會觸發該事件，並且<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件表示將在其中進行繪製的矩形。 如果需要刷新整個控制項，將<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>表示整個控制項的大小。 但是，如果只需要刷新控制項的一部分，則<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件將僅表示需要重繪的區域。 這種情況的一個示例是，當控制項被使用者介面中的另一個控制項或表單部分遮蓋時。  
  
 從<xref:System.Windows.Forms.Control>類繼承時，必須重寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法並在 其中提供圖形呈現代碼。 如果要向使用者控制項或繼承的控制項提供自訂圖形介面，還可以重寫<xref:System.Windows.Forms.Control.OnPaint%2A>該方法。 範例如下所示：  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,
         this.Size));  
   }
}  
```  
  
 前面的示例演示如何使用非常簡單的圖形表示形式呈現控制項。 它調用基<xref:System.Windows.Forms.Control.OnPaint%2A>類的方法，它創建一個<xref:System.Drawing.Pen>要用來繪製的物件，最後在由 和<xref:System.Windows.Forms.Control.Location%2A><xref:System.Windows.Forms.Control.Size%2A>的 控制項確定的矩形中繪製橢圓。 儘管大多數呈現代碼將明顯比這更複雜，但此示例演示了<xref:System.Drawing.Graphics><xref:System.Windows.Forms.PaintEventArgs>物件中包含的物件的使用。 請注意，如果要從已具有圖形表示形式（如<xref:System.Windows.Forms.UserControl>或<xref:System.Windows.Forms.Button>）的類繼承，並且不希望將該表示形式合併到渲染中，則不應調用基類<xref:System.Windows.Forms.Control.OnPaint%2A>的方法。  
  
 控制項方法中<xref:System.Windows.Forms.Control.OnPaint%2A>的代碼將在首次繪製控制項時以及刷新控制項時執行。 為確保每次調整控制項大小時重新繪製控制項，請向控制項的建構函式添加以下行：  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> 使用<xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType>屬性實現非矩形控制項。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [如何：建立繪製的圖形物件](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [組成控制項](constituent-controls.md)
- [各種自訂控制項](varieties-of-custom-controls.md)
