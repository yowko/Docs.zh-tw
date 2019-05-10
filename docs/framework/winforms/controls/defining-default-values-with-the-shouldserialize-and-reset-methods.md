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
ms.openlocfilehash: 5c95272c672d9b35d61e2fca8cccdbc532ef6776
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211286"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="78d68-102">使用 ShouldSerialize 和 Reset 方法定義預設值</span><span class="sxs-lookup"><span data-stu-id="78d68-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="78d68-103">`ShouldSerialize` 和`Reset`是選擇性屬性，您可以提供的方法，如果屬性未具有簡單的預設值。</span><span class="sxs-lookup"><span data-stu-id="78d68-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="78d68-104">如果屬性具有簡單的預設值，則應套用<xref:System.ComponentModel.DefaultValueAttribute>並改為提供屬性的類別建構函式的預設值。</span><span class="sxs-lookup"><span data-stu-id="78d68-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="78d68-105">是一種機制可讓設計工具中的下列功能：</span><span class="sxs-lookup"><span data-stu-id="78d68-105">Either of these mechanisms enables the following features in the designer:</span></span>

- <span data-ttu-id="78d68-106">如果已修改預設值，此屬性會提供屬性瀏覽器中的視覺指示。</span><span class="sxs-lookup"><span data-stu-id="78d68-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>

- <span data-ttu-id="78d68-107">使用者可以在屬性上按一下滑鼠右鍵，然後選擇**重設**還原為其預設值的屬性。</span><span class="sxs-lookup"><span data-stu-id="78d68-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>

- <span data-ttu-id="78d68-108">設計工具會產生更有效率的程式碼。</span><span class="sxs-lookup"><span data-stu-id="78d68-108">The designer generates more efficient code.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="78d68-109">請套用<xref:System.ComponentModel.DefaultValueAttribute>，或提供`Reset` *PropertyName*並`ShouldSerialize` *PropertyName*方法。</span><span class="sxs-lookup"><span data-stu-id="78d68-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="78d68-110">請勿使用兩者。</span><span class="sxs-lookup"><span data-stu-id="78d68-110">Do not use both.</span></span>

 <span data-ttu-id="78d68-111">`Reset` *PropertyName*方法將屬性設定為預設值，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="78d68-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>

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
>  <span data-ttu-id="78d68-112">如果屬性不一定`Reset`方法，不會標示<xref:System.ComponentModel.DefaultValueAttribute>，而且沒有預設值，在其宣告中，提供`Reset`選項的捷徑功能表中的該屬性已停用**屬性**的 Visual Studio 中的 [Windows Form 設計工具] 視窗。</span><span class="sxs-lookup"><span data-stu-id="78d68-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>

 <span data-ttu-id="78d68-113">使用 Visual Studio 這類的設計工具`ShouldSerialize` *PropertyName*方法來檢查屬性是否已經變更預設值，並撰寫程式碼到表單只有當屬性已變更，因此可允許更有效率的程式碼層代。</span><span class="sxs-lookup"><span data-stu-id="78d68-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="78d68-114">例如：</span><span class="sxs-lookup"><span data-stu-id="78d68-114">For example:</span></span>

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

 <span data-ttu-id="78d68-115">完整的程式碼範例如下。</span><span class="sxs-lookup"><span data-stu-id="78d68-115">A complete code example follows.</span></span>

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

 <span data-ttu-id="78d68-116">在此情況下，藉由存取私用變數的值時，即使`MyFont`屬性是`null`，屬性瀏覽器不會顯示`null`; 相反地，它會顯示<xref:System.Windows.Forms.Control.Font%2A>屬性的父代，如果不是`null`，預設值<xref:System.Windows.Forms.Control.Font%2A>中所定義的值<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="78d68-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="78d68-117">因此的預設值`MyFont`無法直接設定，和<xref:System.ComponentModel.DefaultValueAttribute>無法套用至這個屬性。</span><span class="sxs-lookup"><span data-stu-id="78d68-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="78d68-118">相反地，`ShouldSerialize`並`Reset`方法必須實作`MyFont`屬性。</span><span class="sxs-lookup"><span data-stu-id="78d68-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>

## <a name="see-also"></a><span data-ttu-id="78d68-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78d68-119">See also</span></span>

- [<span data-ttu-id="78d68-120">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="78d68-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="78d68-121">定義屬性</span><span class="sxs-lookup"><span data-stu-id="78d68-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="78d68-122">屬性變更事件</span><span class="sxs-lookup"><span data-stu-id="78d68-122">Property-Changed Events</span></span>](property-changed-events.md)
