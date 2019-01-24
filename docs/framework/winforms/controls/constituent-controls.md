---
title: 組成控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 28ae15165327a1bd72e1099460a2a1e3d337ca48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739150"
---
# <a name="constituent-controls"></a>組成控制項
進行自訂圖形轉譯時，構成使用者控制項的控制項或所謂的「組成控制項」較不具彈性。 所有 Windows Form 控制項都處理自己透過自己的轉譯<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 因為這個方法受到保護，所以開發人員無法存取它，因此無法在繪製控制項時防止它執行。 不過，這不表示您無法新增程式碼來影響組成控制項的外觀。 新增事件處理常式，即可完成其他轉譯。 例如，假設您正在撰寫<xref:System.Windows.Forms.UserControl>具有名為按鈕`MyButton`。 如果您想要有超過所提供的其他轉譯<xref:System.Web.UI.WebControls.Button>，您會將程式碼加入使用者控制項，如下所示：  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
>  某些 Windows Form 控制項，例如<xref:System.Windows.Forms.TextBox>，由 Windows 直接繪製。 在這些情況下，<xref:System.Windows.Forms.Control.OnPaint%2A>絕不會呼叫方法，並因此絕不會呼叫上述範例中。  
  
 這會建立每次執行 `MyButton.Paint` 事件時都會執行的方法，進而將其他圖形呈現新增至控制項。 請注意，這並不會防止執行 `MyButton.OnPaint`，因此，除了您的自訂繪製之外，仍然會執行通常透過按鈕所執行的所有繪製。 如需 GDI+ 技術和自訂轉譯的詳細資訊，請參閱[使用 GDI+ 建立圖形影像](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)。 如果您想要有控制項的唯一呈現，則最好的做法就是建立繼承的控制項，以及撰寫其自訂轉譯程式碼。 如需詳細資訊，請參閱[使用者自訂描繪控制項](../../../../docs/framework/winforms/controls/user-drawn-controls.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [使用者自訂描繪控制項](../../../../docs/framework/winforms/controls/user-drawn-controls.md)
- [如何：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
