---
title: 在控制項中定義事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: d45c369e1fc82ee009a85b5b35fe6aa754873436
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746085"
---
# <a name="defining-an-event-in-windows-forms-controls"></a>定義 Windows Form 控制項中的事件
如需定義自訂事件的詳細資訊，請參閱[事件](../../../standard/events/index.md)。 若定義的事件沒有任何相關聯的資料，請為事件資料使用基底類型 <xref:System.EventArgs>，並以 <xref:System.EventHandler> 做為事件委派。 剩下的工作就是定義事件成員，以及會引發事件的受保護 `On`*事件名稱*方法。  
  
 下列程式碼片段示範 `FlashTrackBar` 自訂控制項如何定義自訂事件 `ValueChanged`。 如需 `FlashTrackBar` 範例的完整程式碼，請參閱[如何：建立顯示進度的 Windows Forms 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class FlashTrackBar  
   Inherits Control  
  
   ' The event does not have any data, so EventHandler is adequate   
   ' as the event delegate.          
   ' Define the event member using the event keyword.  
   ' In this case, for efficiency, the event is defined   
   ' using the event property construct.  
   Public Event ValueChanged As EventHandler  
   ' The protected method that raises the ValueChanged   
   ' event when the value has actually   
   ' changed. Derived controls can override this method.    
   Protected Overridable Sub OnValueChanged(e As EventArgs)  
      RaiseEvent ValueChanged(Me, e)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class FlashTrackBar : Control {  
   // The event does not have any data, so EventHandler is adequate   
   // as the event delegate.  
   private EventHandler onValueChanged;  
   // Define the event member using the event keyword.  
   // In this case, for efficiency, the event is defined   
   // using the event property construct.  
   public event EventHandler ValueChanged {  
            add {  
                onValueChanged += value;  
            }  
            remove {  
                onValueChanged -= value;  
            }  
        }  
   // The protected method that raises the ValueChanged  
   // event when the value has actually   
   // changed. Derived controls can override this method.    
   protected virtual void OnValueChanged(EventArgs e) 
   {  
       ValueChanged?.Invoke(this, e);  
   }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項中的事件](events-in-windows-forms-controls.md)
- [事件](../../../standard/events/index.md)
