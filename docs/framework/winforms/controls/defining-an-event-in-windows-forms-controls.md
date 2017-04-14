---
title: "定義 Windows Form 控制項中的事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "自訂控制項 [Windows Form], 使用程式碼的事件"
  - "事件 [Windows Form], 在 Windows Form 自訂控制項中定義"
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 定義 Windows Form 控制項中的事件
如需如何定義自訂事件的詳細資料，請參閱 [事件](../../../../docs/standard/events/index.md)。  若定義的事件沒有任何相關聯的資料，請為事件資料使用基底類型 <xref:System.EventArgs>，並以 <xref:System.EventHandler> 做為事件委派。  接著就是定義事件成員及受保護的 `On`*EventName* 方法 \(引發事件用\)。  
  
 下列程式碼片段示範 `FlashTrackBar` 自訂控制項如何定義自訂事件 `ValueChanged`。  如需 `FlashTrackBar` 範例的完整程式碼，請參閱 [如何：建立顯示進度的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
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
   protected virtual void OnValueChanged(EventArgs e) {  
      if (ValueChanged != null) {  
         ValueChanged(this, e);  
      }  
   }  
}  
```  
  
## 請參閱  
 [Windows Form 控制項中的事件](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)   
 [事件](../../../../docs/standard/events/index.md)   
 [事件](../../../../docs/standard/events/index.md)