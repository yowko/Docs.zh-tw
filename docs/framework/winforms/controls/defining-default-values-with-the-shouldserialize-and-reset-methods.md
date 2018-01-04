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
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="f7836-102">使用 ShouldSerialize 和 Reset 方法定義預設值</span><span class="sxs-lookup"><span data-stu-id="f7836-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="f7836-103">`ShouldSerialize`和`Reset`是選擇性屬性，您可以提供的方法，如果屬性未具有簡單的預設值。</span><span class="sxs-lookup"><span data-stu-id="f7836-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="f7836-104">如果此屬性有簡單的預設值，您應該套用<xref:System.ComponentModel.DefaultValueAttribute>和改為提供預設值給屬性的類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="f7836-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="f7836-105">其中一種機制可讓設計工具中的下列功能：</span><span class="sxs-lookup"><span data-stu-id="f7836-105">Either of these mechanisms enables the following features in the designer:</span></span>  
  
-   <span data-ttu-id="f7836-106">如果已修改預設值，此屬性會提供屬性瀏覽器中的視覺指示。</span><span class="sxs-lookup"><span data-stu-id="f7836-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>  
  
-   <span data-ttu-id="f7836-107">使用者可以在屬性上按一下滑鼠右鍵並選擇**重設**將屬性還原為其預設值。</span><span class="sxs-lookup"><span data-stu-id="f7836-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>  
  
-   <span data-ttu-id="f7836-108">在設計工具會產生更有效率的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f7836-108">The designer generates more efficient code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7836-109">套用<xref:System.ComponentModel.DefaultValueAttribute>或提供`Reset` *PropertyName*和`ShouldSerialize` *PropertyName*方法。</span><span class="sxs-lookup"><span data-stu-id="f7836-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="f7836-110">請勿使用兩者。</span><span class="sxs-lookup"><span data-stu-id="f7836-110">Do not use both.</span></span>  
  
 <span data-ttu-id="f7836-111">`Reset` *PropertyName*方法屬性設定為其預設值，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="f7836-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>  
  
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
>  <span data-ttu-id="f7836-112">如果屬性沒有`Reset`方法，不會標示<xref:System.ComponentModel.DefaultValueAttribute>，而且沒有預設值在其宣告中，提供`Reset`選項的快速鍵功能表中的該屬性已停用**屬性**視窗中的 Windows Form 設計工具的[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f7836-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="f7836-113">設計工具，例如[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]使用`ShouldSerialize` *PropertyName*方法來檢查屬性是否已經從其預設值，並撰寫程式碼到表單只有當屬性變更，因此允許更有效率程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="f7836-113">Designers such as [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="f7836-114">例如: </span><span class="sxs-lookup"><span data-stu-id="f7836-114">For example:</span></span>  
  
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
  
 <span data-ttu-id="f7836-115">完整的程式碼範例如下。</span><span class="sxs-lookup"><span data-stu-id="f7836-115">A complete code example follows.</span></span>  
  
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
  
 <span data-ttu-id="f7836-116">在此情況下，即使所存取的私用變數的值`MyFont`屬性是`null`，屬性瀏覽器不會顯示`null`; 相反地，它會顯示<xref:System.Windows.Forms.Control.Font%2A>屬性的父代，如果不是`null`，預設值或<xref:System.Windows.Forms.Control.Font%2A>中定義值<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="f7836-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="f7836-117">因此的預設值為`MyFont`，所以無法只需設定和<xref:System.ComponentModel.DefaultValueAttribute>無法套用至這個屬性。</span><span class="sxs-lookup"><span data-stu-id="f7836-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="f7836-118">相反地，`ShouldSerialize`和`Reset`方法必須實作`MyFont`屬性。</span><span class="sxs-lookup"><span data-stu-id="f7836-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7836-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="f7836-119">See Also</span></span>  
 [<span data-ttu-id="f7836-120">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="f7836-120">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="f7836-121">定義屬性</span><span class="sxs-lookup"><span data-stu-id="f7836-121">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 [<span data-ttu-id="f7836-122">屬性變更事件</span><span class="sxs-lookup"><span data-stu-id="f7836-122">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)
