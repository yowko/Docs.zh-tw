---
title: 定義 Windows Form 控制項中的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: 4235c8b3c513509023388112071e78cfd079ec6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972337"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="74bc3-102">定義 Windows Form 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="74bc3-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="74bc3-103">如需如何定義自訂事件的詳細資訊，請參閱 <<c0> [ 事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="74bc3-103">For details about defining custom events, see [Events](../../../standard/events/index.md).</span></span> <span data-ttu-id="74bc3-104">若定義的事件沒有任何相關聯的資料，請為事件資料使用基底類型 <xref:System.EventArgs>，並以 <xref:System.EventHandler> 做為事件委派。</span><span class="sxs-lookup"><span data-stu-id="74bc3-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="74bc3-105">就是定義事件成員及受保護的所有`On` *EventName*引發事件的方法。</span><span class="sxs-lookup"><span data-stu-id="74bc3-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="74bc3-106">下列程式碼片段示範 `FlashTrackBar` 自訂控制項如何定義自訂事件 `ValueChanged`。</span><span class="sxs-lookup"><span data-stu-id="74bc3-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="74bc3-107">完整程式碼`FlashTrackBar`範例，請參閱[How to:建立顯示進度的 Windows Form 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="74bc3-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74bc3-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74bc3-108">See also</span></span>

- [<span data-ttu-id="74bc3-109">Windows Forms 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="74bc3-109">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="74bc3-110">事件</span><span class="sxs-lookup"><span data-stu-id="74bc3-110">Events</span></span>](../../../standard/events/index.md)
