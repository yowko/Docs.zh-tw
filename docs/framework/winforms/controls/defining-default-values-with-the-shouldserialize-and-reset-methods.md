---
title: "使用 ShouldSerialize 和 Reset 方法定義預設值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a654fef461d92c4b93db131e303bb07a1e839d34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>使用 ShouldSerialize 和 Reset 方法定義預設值
`ShouldSerialize`和`Reset`是選擇性屬性，您可以提供的方法，如果屬性未具有簡單的預設值。 如果此屬性有簡單的預設值，您應該套用<xref:System.ComponentModel.DefaultValueAttribute>和改為提供預設值給屬性的類別建構函式。 其中一種機制可讓設計工具中的下列功能：  
  
-   如果已修改預設值，此屬性會提供屬性瀏覽器中的視覺指示。  
  
-   使用者可以在屬性上按一下滑鼠右鍵並選擇**重設**將屬性還原為其預設值。  
  
-   在設計工具會產生更有效率的程式碼。  
  
    > [!NOTE]
    >  套用<xref:System.ComponentModel.DefaultValueAttribute>或提供`Reset` *PropertyName*和`ShouldSerialize` *PropertyName*方法。 請勿使用兩者。  
  
 `Reset` *PropertyName*方法屬性設定為其預設值，如下列程式碼片段所示。  
  
```vb  
Public Sub ResetMyFont()  
   MyFont = Nothing  
End Sub  
```  
  
```csharp  
public void ResetMyFont() {  
   MyFont = null;  
}  
```  
  
> [!NOTE]
>  如果屬性沒有`Reset`方法，不會標示<xref:System.ComponentModel.DefaultValueAttribute>，而且沒有預設值在其宣告中，提供`Reset`選項的快速鍵功能表中的該屬性已停用**屬性**視窗中的 Windows Form 設計工具的[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。  
  
 設計工具，例如[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]使用`ShouldSerialize` *PropertyName*方法來檢查屬性是否已經從其預設值，並撰寫程式碼到表單只有當屬性變更，因此允許更有效率程式碼產生。 例如:   
  
```vb  
'Returns true if the font has changed; otherwise, returns false.  
' The designer writes code to the form only if true is returned.  
Public Function ShouldSerializeMyFont() As Boolean  
   Return Not (thefont Is Nothing)  
End Function  
```  
  
```csharp  
// Returns true if the font has changed; otherwise, returns false.  
// The designer writes code to the form only if true is returned.  
public bool ShouldSerializeMyFont() {  
   return thefont != null;  
}  
```  
  
 完整的程式碼範例如下。  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class MyControl  
   Inherits Control  
  
   ' Declare an instance of the Font class  
   ' and set its default value to Nothing.  
   Private thefont As Font = Nothing  
  
   ' The MyFont property.   
   Public Property MyFont() As Font  
      ' Note that the Font property never  
      ' returns null.  
      Get  
         If Not (thefont Is Nothing) Then  
            Return thefont  
         End If  
         If Not (Parent Is Nothing) Then  
            Return Parent.Font  
         End If  
         Return Control.DefaultFont  
      End Get  
      Set  
         thefont = value  
      End Set  
   End Property  
  
   Public Function ShouldSerializeMyFont() As Boolean  
      Return Not (thefont Is Nothing)  
   End Function  
  
   Public Sub ResetMyFont()  
      MyFont = Nothing  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class MyControl : Control {  
   // Declare an instance of the Font class  
   // and set its default value to null.  
   private Font thefont = null;  
  
   // The MyFont property.      
   public Font MyFont {  
      // Note that the MyFont property never  
      // returns null.  
      get {  
         if (thefont != null) return thefont;  
         if (Parent != null) return Parent.Font;  
         return Control.DefaultFont;  
      }  
      set {  
         thefont = value;  
      }  
   }  
  
   public bool ShouldSerializeMyFont() {  
      return thefont != null;  
   }  
  
   public void ResetMyFont() {  
      MyFont = null;  
   }  
}  
```  
  
 在此情況下，即使所存取的私用變數的值`MyFont`屬性是`null`，屬性瀏覽器不會顯示`null`; 相反地，它會顯示<xref:System.Windows.Forms.Control.Font%2A>屬性的父代，如果不是`null`，預設值或<xref:System.Windows.Forms.Control.Font%2A>中定義值<xref:System.Windows.Forms.Control>。 因此的預設值為`MyFont`，所以無法只需設定和<xref:System.ComponentModel.DefaultValueAttribute>無法套用至這個屬性。 相反地，`ShouldSerialize`和`Reset`方法必須實作`MyFont`屬性。  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [定義屬性](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 [屬性變更事件](../../../../docs/framework/winforms/controls/property-changed-events.md)
