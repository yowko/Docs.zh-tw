---
title: 覆寫 OnPaint 方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: b1eb24aaa9ed3bfede41fc5a9a80fcbdc9f749a6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302181"
---
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="c2105-102">覆寫 OnPaint 方法</span><span class="sxs-lookup"><span data-stu-id="c2105-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="c2105-103">覆寫任何事件中所定義的基本步驟[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]都相同，而且下列清單摘要說明。</span><span class="sxs-lookup"><span data-stu-id="c2105-103">The basic steps for overriding any event defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="c2105-104">若要覆寫繼承的事件</span><span class="sxs-lookup"><span data-stu-id="c2105-104">To override an inherited event</span></span>  
  
1. <span data-ttu-id="c2105-105">覆寫受保護`On` *EventName*方法。</span><span class="sxs-lookup"><span data-stu-id="c2105-105">Override the protected `On`*EventName* method.</span></span>  
  
2. <span data-ttu-id="c2105-106">呼叫`On` *EventName*來自覆寫基底類別方法`On` *EventName*方法，所以已註冊的委派收到事件。</span><span class="sxs-lookup"><span data-stu-id="c2105-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="c2105-107"><xref:System.Windows.Forms.Control.Paint>事件會詳細討論這裡因為每個 Windows Form 控制項必須覆寫<xref:System.Windows.Forms.Control.Paint>它所繼承的事件<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="c2105-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="c2105-108">基底<xref:System.Windows.Forms.Control>類別並不知道如何衍生的控制項需要繪製，並不提供任何繪製邏輯<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c2105-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="c2105-109"><xref:System.Windows.Forms.Control.OnPaint%2A>方法<xref:System.Windows.Forms.Control>只會分派<xref:System.Windows.Forms.Control.Paint>事件登錄的事件接收器。</span><span class="sxs-lookup"><span data-stu-id="c2105-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="c2105-110">如果您已完成的範例[How to:開發簡單的 Windows Forms 控制項](how-to-develop-a-simple-windows-forms-control.md)，您已看過會覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c2105-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="c2105-111">下列程式碼片段是取自該範例。</span><span class="sxs-lookup"><span data-stu-id="c2105-111">The following code fragment is taken from that sample.</span></span>  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <span data-ttu-id="c2105-112"><xref:System.Windows.Forms.PaintEventArgs>類別包含資料<xref:System.Windows.Forms.Control.Paint>事件。</span><span class="sxs-lookup"><span data-stu-id="c2105-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="c2105-113">下列程式碼所示，它就會有兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="c2105-113">It has two properties, as shown in the following code.</span></span>  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> <span data-ttu-id="c2105-114">是要繪製的矩形，<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>屬性會參考<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="c2105-114">is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c2105-115">中的類別<xref:System.Drawing?displayProperty=nameWithType>管理命名空間提供的功能的存取權的類別[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，新的 Windows 圖形程式庫。</span><span class="sxs-lookup"><span data-stu-id="c2105-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], the new Windows graphics library.</span></span> <span data-ttu-id="c2105-116"><xref:System.Drawing.Graphics>物件具有繪製點、 字串、 線條、 弧線、 省略符號，以及許多其他圖形的方法。</span><span class="sxs-lookup"><span data-stu-id="c2105-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="c2105-117">控制項叫用以其<xref:System.Windows.Forms.Control.OnPaint%2A>每當程式需要變更其視覺顯示的方法。</span><span class="sxs-lookup"><span data-stu-id="c2105-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="c2105-118">這個方法接著會引發<xref:System.Windows.Forms.Control.Paint>事件。</span><span class="sxs-lookup"><span data-stu-id="c2105-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2105-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2105-119">See also</span></span>

- [<span data-ttu-id="c2105-120">事件</span><span class="sxs-lookup"><span data-stu-id="c2105-120">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="c2105-121">呈現 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="c2105-121">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)
- [<span data-ttu-id="c2105-122">定義事件</span><span class="sxs-lookup"><span data-stu-id="c2105-122">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
