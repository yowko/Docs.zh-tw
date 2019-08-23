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
ms.openlocfilehash: 522a1012fc7bdd54860b0538064ee073f7a761f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918419"
---
# <a name="constituent-controls"></a>組成控制項
進行自訂圖形轉譯時，構成使用者控制項的控制項或所謂的「組成控制項」較不具彈性。 所有的 Windows Forms 控制項都會透過自己<xref:System.Windows.Forms.Control.OnPaint%2A>的方法來處理自己的呈現。 因為這個方法受到保護，所以開發人員無法存取它，因此無法在繪製控制項時防止它執行。 不過，這不表示您無法新增程式碼來影響組成控制項的外觀。 新增事件處理常式，即可完成其他轉譯。 例如, 假設您<xref:System.Windows.Forms.UserControl>使用名`MyButton`為的按鈕撰寫。 如果您想要讓其他轉譯超出所提供的<xref:System.Web.UI.WebControls.Button>內容, 您可以將程式碼新增至您的使用者控制項, 如下所示:  
  
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
> 有些 Windows Forms 控制項 (例如<xref:System.Windows.Forms.TextBox>) 則是由 Windows 直接繪製。 在這些情況下, <xref:System.Windows.Forms.Control.OnPaint%2A>永遠不會呼叫方法, 因此不會呼叫上述範例。  
  
 這會建立每次執行 `MyButton.Paint` 事件時都會執行的方法，進而將其他圖形呈現新增至控制項。 請注意，這並不會防止執行 `MyButton.OnPaint`，因此，除了您的自訂繪製之外，仍然會執行通常透過按鈕所執行的所有繪製。 如需 GDI+ 技術和自訂轉譯的詳細資訊，請參閱[使用 GDI+ 建立圖形影像](../advanced/how-to-create-graphics-objects-for-drawing.md)。 如果您想要有控制項的唯一呈現，則最好的做法就是建立繼承的控制項，以及撰寫其自訂轉譯程式碼。 如需詳細資訊，請參閱[使用者自訂描繪控制項](user-drawn-controls.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [使用者自訂描繪控制項](user-drawn-controls.md)
- [如何：建立繪圖的繪圖物件](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [各種自訂控制項](varieties-of-custom-controls.md)
