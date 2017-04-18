---
title: "使用 ShouldSerialize 和 Reset 方法定義預設值 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 屬性方法"
  - "Reset 方法"
  - "ShouldPersist 方法"
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 使用 ShouldSerialize 和 Reset 方法定義預設值
如果屬性沒有簡單的預設值，則 `ShouldSerialize` 和 `Reset` 是可以提供給屬性的選擇性方法。  如果屬性具有簡單的預設值，您應該套用 <xref:System.ComponentModel.DefaultValueAttribute>，並提供預設值給屬性類別建構函式。  這兩個機制的其中之一會在設計工具中啟用下列功能：  
  
-   如果屬性已被修改而與預設值不同，則屬性會在屬性瀏覽器中提供視覺化的表示。  
  
-   使用者可以在屬性上按一下滑鼠右鍵，並選擇 \[**重設**\] 將屬性還原為預設值。  
  
-   設計工具會產生較有效率的程式碼。  
  
    > [!NOTE]
    >  套用 <xref:System.ComponentModel.DefaultValueAttribute> 或提供 `Reset`*PropertyName* 和 `ShouldSerialize`*PropertyName* 方法。  不要兩者都使用。  
  
 `Reset` *PropertyName* 方法設定屬性為其預設值，如下列程式碼片段所示。  
  
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
>  如果屬性沒有 `Reset` 方法、未標記為 <xref:System.ComponentModel.DefaultValueAttribute>，且在宣告中沒有提供預設值，則在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中 Windows Form 設計工具的 \[**屬性**\] 視窗的捷徑功能表內，會停用該屬性的 `Reset` 選項。  
  
 設計工具 \(例如 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]\) 會使用 `ShouldSerialize`*PropertyName* 方法來檢查屬性的預設值是否已經變更，並且只有變更屬性時，才會將程式碼寫入表單中，因此能更有效率地產生程式碼。  例如：  
  
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
  
 完整程式碼範例如下。  
  
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
  
 在這個案例中，即使當 `MyFont` 屬性所存取的私用變數為 `null` 時，屬性瀏覽器也不會顯示 `null`；相反地，如果它不是 `null`、或在 <xref:System.Windows.Forms.Control> 中所定義的預設 <xref:System.Windows.Forms.Control.Font%2A> 值，便會顯示父代 \(Parent\) 的 <xref:System.Windows.Forms.Control.Font%2A> 屬性。  因此，無法簡單設定 `MyFont`  的預設值，且無法套用 <xref:System.ComponentModel.DefaultValueAttribute> 至這個屬性，  反而必須為 `MyFont` 屬性實作 `ShouldSerialize` 和 `Reset` 方法。  
  
## 請參閱  
 [Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [定義屬性](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)   
 [屬性變更事件](../../../../docs/framework/winforms/controls/property-changed-events.md)