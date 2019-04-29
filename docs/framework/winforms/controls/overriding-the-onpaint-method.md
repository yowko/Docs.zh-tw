---
title: 覆寫 OnPaint 方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: b1eb24aaa9ed3bfede41fc5a9a80fcbdc9f749a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936444"
---
# <a name="overriding-the-onpaint-method"></a>覆寫 OnPaint 方法
覆寫任何事件中所定義的基本步驟[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]都相同，而且下列清單摘要說明。  
  
#### <a name="to-override-an-inherited-event"></a>若要覆寫繼承的事件  
  
1. 覆寫受保護`On` *EventName*方法。  
  
2. 呼叫`On` *EventName*來自覆寫基底類別方法`On` *EventName*方法，所以已註冊的委派收到事件。  
  
 <xref:System.Windows.Forms.Control.Paint>事件會詳細討論這裡因為每個 Windows Form 控制項必須覆寫<xref:System.Windows.Forms.Control.Paint>它所繼承的事件<xref:System.Windows.Forms.Control>。 基底<xref:System.Windows.Forms.Control>類別並不知道如何衍生的控制項需要繪製，並不提供任何繪製邏輯<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 <xref:System.Windows.Forms.Control.OnPaint%2A>方法<xref:System.Windows.Forms.Control>只會分派<xref:System.Windows.Forms.Control.Paint>事件登錄的事件接收器。  
  
 如果您已完成的範例[How to:開發簡單的 Windows Forms 控制項](how-to-develop-a-simple-windows-forms-control.md)，您已看過會覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 下列程式碼片段是取自該範例。  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <xref:System.Windows.Forms.PaintEventArgs>類別包含資料<xref:System.Windows.Forms.Control.Paint>事件。 下列程式碼所示，它就會有兩個屬性。  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 是要繪製的矩形，<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>屬性會參考<xref:System.Drawing.Graphics>物件。 中的類別<xref:System.Drawing?displayProperty=nameWithType>管理命名空間提供的功能的存取權的類別[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，新的 Windows 圖形程式庫。 <xref:System.Drawing.Graphics>物件具有繪製點、 字串、 線條、 弧線、 省略符號，以及許多其他圖形的方法。  
  
 控制項叫用以其<xref:System.Windows.Forms.Control.OnPaint%2A>每當程式需要變更其視覺顯示的方法。 這個方法接著會引發<xref:System.Windows.Forms.Control.Paint>事件。  
  
## <a name="see-also"></a>另請參閱

- [事件](../../../standard/events/index.md)
- [呈現 Windows Forms 控制項](rendering-a-windows-forms-control.md)
- [定義事件](defining-an-event-in-windows-forms-controls.md)
