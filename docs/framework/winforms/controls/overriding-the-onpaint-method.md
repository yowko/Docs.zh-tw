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
ms.openlocfilehash: 863726a6264f01de9f00296b4a64b9fd1bb96765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182040"
---
# <a name="overriding-the-onpaint-method"></a>覆寫 OnPaint 方法
重寫 .NET 框架中定義的任何事件的基本步驟相同，並匯總如下清單中。  
  
#### <a name="to-override-an-inherited-event"></a>重寫繼承的事件  
  
1. 重寫受保護的`On`*事件名稱*方法。  
  
2. `On`從重寫`On`*的 EventName*方法調用基類的*EventName*方法，以便註冊代理接收事件。  
  
 此處<xref:System.Windows.Forms.Control.Paint>將詳細討論該事件，因為每個 Windows 表單控制項都必須<xref:System.Windows.Forms.Control.Paint>覆蓋從 繼承的事件<xref:System.Windows.Forms.Control>。 基<xref:System.Windows.Forms.Control>類不知道如何繪製派生控制項，也不在<xref:System.Windows.Forms.Control.OnPaint%2A>方法中提供任何繪製邏輯。 <xref:System.Windows.Forms.Control>簡單地將<xref:System.Windows.Forms.Control.Paint>事件調度給已註冊的事件接收器<xref:System.Windows.Forms.Control.OnPaint%2A>的方法。  
  
 如果您通過["如何：開發一個簡單的 Windows 表單控制項"](how-to-develop-a-simple-windows-forms-control.md)中的示例，則您看到了重寫<xref:System.Windows.Forms.Control.OnPaint%2A>該方法的示例。 以下代碼片段取自該示例。  
  
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
  
 類<xref:System.Windows.Forms.PaintEventArgs>包含<xref:System.Windows.Forms.Control.Paint>事件的資料。 它有兩個屬性，如下代碼所示。  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>是要繪製的矩形，<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>屬性引用<xref:System.Drawing.Graphics>物件。 命名空間中的<xref:System.Drawing?displayProperty=nameWithType>類是託管類，提供對 GDI+ 功能（新的 Windows 圖形庫）的功能的訪問。 該<xref:System.Drawing.Graphics>物件具有繪製點、字串、線條、圓弧、橢圓和許多其他形狀的方法。  
  
 控制項每當需要更改其<xref:System.Windows.Forms.Control.OnPaint%2A>可視顯示時調用其方法。 此方法反過來引發事件<xref:System.Windows.Forms.Control.Paint>。  
  
## <a name="see-also"></a>另請參閱

- [事件](../../../standard/events/index.md)
- [呈現 Windows Forms 控制項](rendering-a-windows-forms-control.md)
- [定義事件](defining-an-event-in-windows-forms-controls.md)
