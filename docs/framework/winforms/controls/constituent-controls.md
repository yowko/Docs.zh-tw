---
title: 組成控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 2865a3d85bd56151038ee90c18d199d3a584b5d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182421"
---
# <a name="constituent-controls"></a><span data-ttu-id="6768c-102">組成控制項</span><span class="sxs-lookup"><span data-stu-id="6768c-102">Constituent Controls</span></span>
<span data-ttu-id="6768c-103">進行自訂圖形轉譯時，構成使用者控制項的控制項或所謂的「組成控制項」\*\* 較不具彈性。</span><span class="sxs-lookup"><span data-stu-id="6768c-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="6768c-104">所有 Windows 表單控制項都通過自己的<xref:System.Windows.Forms.Control.OnPaint%2A>方法處理自己的呈現。</span><span class="sxs-lookup"><span data-stu-id="6768c-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="6768c-105">因為這個方法受到保護，所以開發人員無法存取它，因此無法在繪製控制項時防止它執行。</span><span class="sxs-lookup"><span data-stu-id="6768c-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="6768c-106">不過，這不表示您無法新增程式碼來影響組成控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="6768c-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="6768c-107">新增事件處理常式，即可完成其他轉譯。</span><span class="sxs-lookup"><span data-stu-id="6768c-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="6768c-108">例如，假設您創作的按鈕<xref:System.Windows.Forms.UserControl>名為`MyButton`。</span><span class="sxs-lookup"><span data-stu-id="6768c-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="6768c-109">如果希望具有超出 提供的其他呈現，<xref:System.Web.UI.WebControls.Button>則可以向使用者控制項添加類似于以下內容的代碼：</span><span class="sxs-lookup"><span data-stu-id="6768c-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="6768c-110">某些 Windows 表單控制項（<xref:System.Windows.Forms.TextBox>如 ）由 Windows 直接繪製。</span><span class="sxs-lookup"><span data-stu-id="6768c-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="6768c-111">在這些情況下，永遠不會調用<xref:System.Windows.Forms.Control.OnPaint%2A>該方法，因此永遠不會調用上述示例。</span><span class="sxs-lookup"><span data-stu-id="6768c-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="6768c-112">這會建立每次執行 `MyButton.Paint` 事件時都會執行的方法，進而將其他圖形呈現新增至控制項。</span><span class="sxs-lookup"><span data-stu-id="6768c-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="6768c-113">請注意，這並不會防止執行 `MyButton.OnPaint`，因此，除了您的自訂繪製之外，仍然會執行通常透過按鈕所執行的所有繪製。</span><span class="sxs-lookup"><span data-stu-id="6768c-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="6768c-114">如需 GDI+ 技術和自訂轉譯的詳細資訊，請參閱[使用 GDI+ 建立圖形影像](../advanced/how-to-create-graphics-objects-for-drawing.md)。</span><span class="sxs-lookup"><span data-stu-id="6768c-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="6768c-115">如果您想要有控制項的唯一呈現，則最好的做法就是建立繼承的控制項，以及撰寫其自訂轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="6768c-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="6768c-116">如需詳細資訊，請參閱[使用者自訂描繪控制項](user-drawn-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="6768c-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6768c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6768c-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="6768c-118">使用者自訂描繪控制項</span><span class="sxs-lookup"><span data-stu-id="6768c-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="6768c-119">如何：建立繪製的圖形物件</span><span class="sxs-lookup"><span data-stu-id="6768c-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="6768c-120">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="6768c-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
