---
title: 作法：公開組成控制項的屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: f006e42771a5ecc71f6a508fd78d0e2dd8f2d2f2
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015884"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="f7d66-102">HOW TO：公開組成控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="f7d66-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="f7d66-103">組成複合控制項的控制項稱為「*組成控制項*」。</span><span class="sxs-lookup"><span data-stu-id="f7d66-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="f7d66-104">這些控制項通常會宣告為私用, 因此開發人員無法存取。</span><span class="sxs-lookup"><span data-stu-id="f7d66-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="f7d66-105">如果您想要讓這些控制項的屬性可供未來的使用者使用, 您必須將它們公開給使用者。</span><span class="sxs-lookup"><span data-stu-id="f7d66-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="f7d66-106">組成控制項的屬性會藉由在使用者控制項中建立屬性來公開, 並使用該屬性`get`的`set`和存取子來影響組成控制項之私用屬性的變更。</span><span class="sxs-lookup"><span data-stu-id="f7d66-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>

 <span data-ttu-id="f7d66-107">假設有一個具有名為`MyButton`之組成按鈕的假設使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="f7d66-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="f7d66-108">在此範例中, 當使用者要求`ConstituentButtonBackColor`屬性時, 會傳遞儲存<xref:System.Windows.Forms.Control.BackColor%2A>在之`MyButton`屬性中的值。</span><span class="sxs-lookup"><span data-stu-id="f7d66-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="f7d66-109">當使用者將值指派給這個屬性時, 該值會自動傳遞<xref:System.Windows.Forms.Control.BackColor%2A>至的`MyButton`屬性, 而程式`set` `MyButton`代碼將會執行, 並變更的色彩。</span><span class="sxs-lookup"><span data-stu-id="f7d66-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>

 <span data-ttu-id="f7d66-110">下列範例顯示如何公開<xref:System.Windows.Forms.Control.BackColor%2A> [構成] 按鈕的屬性:</span><span class="sxs-lookup"><span data-stu-id="f7d66-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>

```vb
Public Property ButtonColor() as System.Drawing.Color
   Get
      Return MyButton.BackColor
   End Get
   Set(Value as System.Drawing.Color)
      MyButton.BackColor = Value
   End Set
End Property
```

```csharp
public Color ButtonColor
{
   get
   {
      return(myButton.BackColor);
   }
   set
   {
      myButton.BackColor = value;
   }
}
```

### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="f7d66-111">公開組成控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="f7d66-111">To expose a property of a constituent control</span></span>

1. <span data-ttu-id="f7d66-112">建立使用者控制項的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="f7d66-112">Create a public property for your user control.</span></span>

2. <span data-ttu-id="f7d66-113">在屬性的區段中, 撰寫程式碼來抓取您想要公開之屬性的值。 `get`</span><span class="sxs-lookup"><span data-stu-id="f7d66-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>

3. <span data-ttu-id="f7d66-114">在屬性`set`的區段中, 撰寫程式碼, 將屬性的值傳遞給組成控制項的公開屬性。</span><span class="sxs-lookup"><span data-stu-id="f7d66-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7d66-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7d66-115">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="f7d66-116">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="f7d66-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="f7d66-117">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="f7d66-117">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
