---
title: "如何：公開組成控制項的屬性"
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
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a970864a406f98477fa3e09bdefcf959d2078fe6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="1724a-102">如何：公開組成控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="1724a-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="1724a-103">複合控制項所組成的控制項稱為*構成控制項*。</span><span class="sxs-lookup"><span data-stu-id="1724a-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="1724a-104">這些控制項通常宣告為私用，因此開發人員無法存取。</span><span class="sxs-lookup"><span data-stu-id="1724a-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="1724a-105">如果您想要讓未來的使用者可以使用這些控制項的屬性，您必須公開給使用者。</span><span class="sxs-lookup"><span data-stu-id="1724a-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="1724a-106">組成控制項的屬性由使用者控制項，以建立屬性，然後使用`get`和`set`該屬性的存取子中組成控制項的私用屬性的變更生效。</span><span class="sxs-lookup"><span data-stu-id="1724a-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="1724a-107">假設使用者控制項，請考慮使用構成按鈕名為`MyButton`。</span><span class="sxs-lookup"><span data-stu-id="1724a-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="1724a-108">在此範例中，當使用者要求`ConstituentButtonBackColor`屬性、 值儲存在<xref:System.Windows.Forms.Control.BackColor%2A>屬性`MyButton`傳遞。</span><span class="sxs-lookup"><span data-stu-id="1724a-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="1724a-109">當使用者指派給這個屬性的值時，這個值自動傳遞給<xref:System.Windows.Forms.Control.BackColor%2A>屬性`MyButton`和`set`會執行程式碼，變更的色彩`MyButton`。</span><span class="sxs-lookup"><span data-stu-id="1724a-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="1724a-110">下列範例示範如何公開<xref:System.Windows.Forms.Control.BackColor%2A>構成按鈕的屬性：</span><span class="sxs-lookup"><span data-stu-id="1724a-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="1724a-111">公開構成控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="1724a-111">To expose a property of a constituent control</span></span>  
  
1.  <span data-ttu-id="1724a-112">建立使用者控制項的公用屬性。</span><span class="sxs-lookup"><span data-stu-id="1724a-112">Create a public property for your user control.</span></span>  
  
2.  <span data-ttu-id="1724a-113">在`get`屬性，可擷取您想要公開的屬性值撰寫程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="1724a-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3.  <span data-ttu-id="1724a-114">在`set`屬性，會將屬性的值傳遞給公開的屬性組成控制項撰寫程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="1724a-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1724a-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="1724a-115">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="1724a-116">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="1724a-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="1724a-117">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="1724a-117">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
