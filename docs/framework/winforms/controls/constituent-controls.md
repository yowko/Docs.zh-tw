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
ms.openlocfilehash: 76a5a4f9b02a71616d247a1bb0f03cc0aec1d70d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956067"
---
# <a name="constituent-controls"></a><span data-ttu-id="e930f-102">組成控制項</span><span class="sxs-lookup"><span data-stu-id="e930f-102">Constituent Controls</span></span>
<span data-ttu-id="e930f-103">進行自訂圖形轉譯時，構成使用者控制項的控制項或所謂的「組成控制項」較不具彈性。</span><span class="sxs-lookup"><span data-stu-id="e930f-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="e930f-104">所有 Windows Form 控制項都處理自己透過自己的轉譯<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e930f-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="e930f-105">因為這個方法受到保護，所以開發人員無法存取它，因此無法在繪製控制項時防止它執行。</span><span class="sxs-lookup"><span data-stu-id="e930f-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="e930f-106">不過，這不表示您無法新增程式碼來影響組成控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="e930f-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="e930f-107">新增事件處理常式，即可完成其他轉譯。</span><span class="sxs-lookup"><span data-stu-id="e930f-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="e930f-108">例如，假設您正在撰寫<xref:System.Windows.Forms.UserControl>具有名為按鈕`MyButton`。</span><span class="sxs-lookup"><span data-stu-id="e930f-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="e930f-109">如果您想要有超過所提供的其他轉譯<xref:System.Web.UI.WebControls.Button>，您會將程式碼加入使用者控制項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e930f-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
>  <span data-ttu-id="e930f-110">某些 Windows Form 控制項，例如<xref:System.Windows.Forms.TextBox>，由 Windows 直接繪製。</span><span class="sxs-lookup"><span data-stu-id="e930f-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="e930f-111">在這些情況下，<xref:System.Windows.Forms.Control.OnPaint%2A>絕不會呼叫方法，並因此絕不會呼叫上述範例中。</span><span class="sxs-lookup"><span data-stu-id="e930f-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="e930f-112">這會建立每次執行 `MyButton.Paint` 事件時都會執行的方法，進而將其他圖形呈現新增至控制項。</span><span class="sxs-lookup"><span data-stu-id="e930f-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="e930f-113">請注意，這並不會防止執行 `MyButton.OnPaint`，因此，除了您的自訂繪製之外，仍然會執行通常透過按鈕所執行的所有繪製。</span><span class="sxs-lookup"><span data-stu-id="e930f-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="e930f-114">如需 GDI+ 技術和自訂轉譯的詳細資訊，請參閱[使用 GDI+ 建立圖形影像](../advanced/how-to-create-graphics-objects-for-drawing.md)。</span><span class="sxs-lookup"><span data-stu-id="e930f-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="e930f-115">如果您想要有控制項的唯一呈現，則最好的做法就是建立繼承的控制項，以及撰寫其自訂轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="e930f-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="e930f-116">如需詳細資訊，請參閱[使用者自訂描繪控制項](user-drawn-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="e930f-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e930f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e930f-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="e930f-118">使用者自訂描繪控制項</span><span class="sxs-lookup"><span data-stu-id="e930f-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="e930f-119">如何：建立繪圖的圖形物件</span><span class="sxs-lookup"><span data-stu-id="e930f-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="e930f-120">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="e930f-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
