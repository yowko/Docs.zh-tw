---
title: 使用 ShouldSerialize 和 Reset 方法定義預設值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: 11181bacdb919693ffc82c48c061357463a6343b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336755"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>使用 ShouldSerialize 和 Reset 方法定義預設值
如果屬性不具有簡單的預設值，`ShouldSerialize` 和 `Reset` 就是您可以為屬性提供的選擇性方法。 如果屬性具有簡單的預設值，您應該套用 <xref:System.ComponentModel.DefaultValueAttribute>，並改為將預設值提供給屬性類別的函式。 其中一種機制會在設計工具中啟用下列功能：

- 屬性會在屬性瀏覽器中提供視覺指示（如果它已從其預設值修改）。

- 使用者可以在屬性上按一下滑鼠右鍵，然後選擇 [**重設**]，將屬性還原為預設值。

- 設計工具會產生更有效率的程式碼。

    > [!NOTE]
    > 請套用 <xref:System.ComponentModel.DefaultValueAttribute> 或提供 `Reset`*propertyname*和 `ShouldSerialize`*propertyname*方法。 請勿同時使用兩者。

 `Reset`*PropertyName*方法會將屬性設定為其預設值，如下列程式碼片段所示。

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
> 如果屬性沒有 `Reset` 方法、未以 <xref:System.ComponentModel.DefaultValueAttribute>標記，而且沒有在其宣告中提供預設值，則會在 Visual Studio 之 Windows Form 設計工具的 [**屬性**] 視窗的快捷方式功能表中，停用該屬性的 `Reset` 選項。

 Visual Studio 的設計工具會使用 `ShouldSerialize`*PropertyName*方法來檢查屬性是否已從其預設值變更，並只有在屬性已變更時才將程式碼寫入表單，因而允許更有效率的程式碼產生。 例如：

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

Imports System.Drawing
Imports System.Windows.Forms

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
using System.Drawing;
using System.Windows.Forms;

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

 在此情況下，即使 `MyFont` 屬性所存取之私用變數的值是 `null`，屬性瀏覽器也不會顯示 `null`;相反地，它會顯示父系的 <xref:System.Windows.Forms.Control.Font%2A> 屬性（如果不是 `null`），或 <xref:System.Windows.Forms.Control>中定義的預設 <xref:System.Windows.Forms.Control.Font%2A> 值。 因此，`MyFont` 的預設值不能只是設定，而且無法將 <xref:System.ComponentModel.DefaultValueAttribute> 套用至這個屬性。 相反地，`ShouldSerialize` 和 `Reset` 方法必須針對 `MyFont` 屬性來執行。

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項中的屬性](properties-in-windows-forms-controls.md)
- [定義屬性](defining-a-property-in-windows-forms-controls.md)
- [屬性變更事件](property-changed-events.md)
