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
ms.openlocfilehash: 609fe4896a2b01b8a69ff8a3d0854c85ddbd6a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969088"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="79f65-102">使用 ShouldSerialize 和 Reset 方法定義預設值</span><span class="sxs-lookup"><span data-stu-id="79f65-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="79f65-103">`ShouldSerialize`如果`Reset`屬性不具有簡單的預設值, 和就是您可以為屬性提供的選擇性方法。</span><span class="sxs-lookup"><span data-stu-id="79f65-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="79f65-104">如果屬性具有簡單的預設值, 您應該<xref:System.ComponentModel.DefaultValueAttribute>套用, 並改為將預設值提供給屬性類別的函式。</span><span class="sxs-lookup"><span data-stu-id="79f65-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="79f65-105">其中一種機制會在設計工具中啟用下列功能:</span><span class="sxs-lookup"><span data-stu-id="79f65-105">Either of these mechanisms enables the following features in the designer:</span></span>

- <span data-ttu-id="79f65-106">屬性會在屬性瀏覽器中提供視覺指示 (如果它已從其預設值修改)。</span><span class="sxs-lookup"><span data-stu-id="79f65-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>

- <span data-ttu-id="79f65-107">使用者可以在屬性上按一下滑鼠右鍵, 然後選擇 [**重設**], 將屬性還原為預設值。</span><span class="sxs-lookup"><span data-stu-id="79f65-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>

- <span data-ttu-id="79f65-108">設計工具會產生更有效率的程式碼。</span><span class="sxs-lookup"><span data-stu-id="79f65-108">The designer generates more efficient code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="79f65-109">`Reset` `ShouldSerialize`請套用或提供 propertyname 和 propertyname 方法。 <xref:System.ComponentModel.DefaultValueAttribute></span><span class="sxs-lookup"><span data-stu-id="79f65-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="79f65-110">請勿同時使用兩者。</span><span class="sxs-lookup"><span data-stu-id="79f65-110">Do not use both.</span></span>

 <span data-ttu-id="79f65-111">PropertyName 方法會將屬性設定為其預設值, 如下列程式碼片段所示。 `Reset`</span><span class="sxs-lookup"><span data-stu-id="79f65-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>

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
> <span data-ttu-id="79f65-112">如果屬性`Reset`沒有方法、未<xref:System.ComponentModel.DefaultValueAttribute>以標記, 而且沒有`Reset`在其宣告中提供預設值, 則該屬性的選項會在的 [**屬性**] 視窗的快捷方式功能表中停用。Visual Studio 中的 Windows Form 設計工具。</span><span class="sxs-lookup"><span data-stu-id="79f65-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>

 <span data-ttu-id="79f65-113">Visual Studio 的`ShouldSerialize`設計工具會使用*PropertyName*方法來檢查屬性是否已從其預設值變更, 並只有在屬性已變更時才將程式碼寫入表單, 因而允許更有效率的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="79f65-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="79f65-114">例如：</span><span class="sxs-lookup"><span data-stu-id="79f65-114">For example:</span></span>

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

 <span data-ttu-id="79f65-115">完整的程式碼範例如下。</span><span class="sxs-lookup"><span data-stu-id="79f65-115">A complete code example follows.</span></span>

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

 <span data-ttu-id="79f65-116">在此情況下, 即使`MyFont`屬性所存取之私用變數的值為`null`, 屬性瀏覽器也不會顯示`null`; 相反地, 它會<xref:System.Windows.Forms.Control.Font%2A>顯示父系的屬性 (如果沒有`null`的話)。或中<xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control>定義的預設值。</span><span class="sxs-lookup"><span data-stu-id="79f65-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="79f65-117">因此, 的預設值`MyFont`不能只是設定, <xref:System.ComponentModel.DefaultValueAttribute>而無法套用至這個屬性。</span><span class="sxs-lookup"><span data-stu-id="79f65-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="79f65-118">而是`Reset`必須針對 `ShouldSerialize` 屬性實`MyFont`作為和方法。</span><span class="sxs-lookup"><span data-stu-id="79f65-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>

## <a name="see-also"></a><span data-ttu-id="79f65-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79f65-119">See also</span></span>

- [<span data-ttu-id="79f65-120">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="79f65-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="79f65-121">定義屬性</span><span class="sxs-lookup"><span data-stu-id="79f65-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="79f65-122">屬性變更事件</span><span class="sxs-lookup"><span data-stu-id="79f65-122">Property-Changed Events</span></span>](property-changed-events.md)
