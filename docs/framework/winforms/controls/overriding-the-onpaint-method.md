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
ms.openlocfilehash: fc41158e9a3d5d331b391f0f28701612012becf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537212"
---
# <a name="overriding-the-onpaint-method"></a>覆寫 OnPaint 方法
覆寫中定義的任何事件的基本步驟[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]是一樣的並在下列清單摘要說明。  
  
#### <a name="to-override-an-inherited-event"></a>若要覆寫繼承的事件  
  
1.  覆寫的受保護`On` *EventName*方法。  
  
2.  呼叫`On` *EventName*從覆寫基底類別方法`On` *EventName*方法，使已註冊的委派能接收到事件。  
  
 <xref:System.Windows.Forms.Control.Paint>必須覆寫的每個 Windows Form 控制項，因為此處詳細討論事件<xref:System.Windows.Forms.Control.Paint>它所繼承的事件<xref:System.Windows.Forms.Control>。 基底<xref:System.Windows.Forms.Control>類別並不知道如何衍生的控制項必須繪製，並不會提供中的任何繪製邏輯<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 <xref:System.Windows.Forms.Control.OnPaint%2A>方法<xref:System.Windows.Forms.Control>只會分派<xref:System.Windows.Forms.Control.Paint>已註冊的事件接收器的事件。  
  
 如果您已完成中的範例[How to： 開發簡單的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)，您所見的覆寫範例<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 下列程式碼片段是取自該範例。  
  
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
public class FirstControl : Control{  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <xref:System.Windows.Forms.PaintEventArgs>類別包含的資料<xref:System.Windows.Forms.Control.Paint>事件。 它有兩個屬性，如下列程式碼所示。  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 是要繪製的矩形和<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>屬性參考到<xref:System.Drawing.Graphics>物件。 中的類別<xref:System.Drawing?displayProperty=nameWithType>命名空間所管理的功能提供存取的類別[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，新的 Windows 圖形文件庫。 <xref:System.Drawing.Graphics>物件有方法可以繪製點、 字串、 線條、 弧線、 省略符號，以及許多其他圖形。  
  
 控制項叫用其<xref:System.Windows.Forms.Control.OnPaint%2A>方法每當程式需要變更其視覺顯示。 此方法接著就會引發<xref:System.Windows.Forms.Control.Paint>事件。  
  
## <a name="see-also"></a>另請參閱  
 [事件](../../../../docs/standard/events/index.md)  
 [呈現 Windows Forms 控制項](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [定義事件](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
