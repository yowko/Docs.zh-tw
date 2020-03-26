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
ms.openlocfilehash: a4738373b10fbcb1d2406406d30f10b795aeb914
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228846"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="fac22-102">定義 Windows Form 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="fac22-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="fac22-103">有關定義自訂事件的詳細資訊，請參閱[事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fac22-103">For details about defining custom events, see [Events](../../../standard/events/index.md).</span></span> <span data-ttu-id="fac22-104">若定義的事件沒有任何相關聯的資料，請為事件資料使用基底類型 <xref:System.EventArgs>，並以 <xref:System.EventHandler> 做為事件委派。</span><span class="sxs-lookup"><span data-stu-id="fac22-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="fac22-105">剩下的就是定義事件成員和引發事件的受保護`On`*事件Name*方法。</span><span class="sxs-lookup"><span data-stu-id="fac22-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="fac22-106">下列程式碼片段示範 `FlashTrackBar` 自訂控制項如何定義自訂事件 `ValueChanged`。</span><span class="sxs-lookup"><span data-stu-id="fac22-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="fac22-107">有關`FlashTrackBar`示例的完整代碼，請參閱["如何：創建顯示進度的 Windows 表單控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)"。</span><span class="sxs-lookup"><span data-stu-id="fac22-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
       onValueChanged?.Invoke(this, e);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fac22-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fac22-108">See also</span></span>

- [<span data-ttu-id="fac22-109">Windows Form 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="fac22-109">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="fac22-110">事件</span><span class="sxs-lookup"><span data-stu-id="fac22-110">Events</span></span>](../../../standard/events/index.md)
