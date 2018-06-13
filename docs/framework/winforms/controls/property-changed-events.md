---
title: 屬性變更事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: f4e6a6267df88cdd33a58093f276c6005209f38d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536237"
---
# <a name="property-changed-events"></a><span data-ttu-id="f2f8f-102">屬性變更事件</span><span class="sxs-lookup"><span data-stu-id="f2f8f-102">Property-Changed Events</span></span>
<span data-ttu-id="f2f8f-103">如果您要傳送通知的屬性，名為控制項*PropertyName*變更，定義名為事件*PropertyName* `Changed`和方法，名為`On` *PropertyName* `Changed`會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="f2f8f-103">If you want your control to send notifications when a property named *PropertyName* changes, define an event named *PropertyName*`Changed` and a method named `On`*PropertyName*`Changed` that raises the event.</span></span> <span data-ttu-id="f2f8f-104">在 Windows Form 中的命名慣例是將文字附加*Changed*屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2f8f-104">The naming convention in Windows Forms is to append the word *Changed* to the name of the property.</span></span> <span data-ttu-id="f2f8f-105">屬性變更事件的相關聯的事件委派類型是<xref:System.EventHandler>，和事件的資料型別是<xref:System.EventArgs>。</span><span class="sxs-lookup"><span data-stu-id="f2f8f-105">The associated event delegate type for property-changed events is <xref:System.EventHandler>, and the event data type is <xref:System.EventArgs>.</span></span> <span data-ttu-id="f2f8f-106">基底類別<xref:System.Windows.Forms.Control>定義許多屬性變更事件，例如<xref:System.Windows.Forms.Control.BackColorChanged>， <xref:System.Windows.Forms.Control.BackgroundImageChanged>， <xref:System.Windows.Forms.Control.FontChanged>， <xref:System.Windows.Forms.Control.LocationChanged>，和其他人。</span><span class="sxs-lookup"><span data-stu-id="f2f8f-106">The base class <xref:System.Windows.Forms.Control> defines many property-changed events, such as <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, and others.</span></span> <span data-ttu-id="f2f8f-107">如需事件的背景資訊，請參閱[事件](../../../../docs/standard/events/index.md)和[Windows Form 控制項中的事件](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="f2f8f-107">For background information about events, see [Events](../../../../docs/standard/events/index.md) and [Events in Windows Forms Controls](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="f2f8f-108">屬性變更事件很實用是因為它們允許控制項的取用者附加到變更回應的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f2f8f-108">Property-changed events are useful because they allow consumers of a control to attach event handlers that respond to the change.</span></span> <span data-ttu-id="f2f8f-109">如果控制項需要回應，便會產生屬性變更事件，請覆寫對應的`On` *PropertyName* `Changed`方法，而非附加至事件的委派。</span><span class="sxs-lookup"><span data-stu-id="f2f8f-109">If your control needs to respond to a property-changed event that it raises, override the corresponding `On`*PropertyName*`Changed` method instead of attaching a delegate to the event.</span></span> <span data-ttu-id="f2f8f-110">更新其他屬性，或重新繪製部分或所有的繪圖介面，則控制項通常會回應屬性變更事件。</span><span class="sxs-lookup"><span data-stu-id="f2f8f-110">A control typically responds to a property-changed event by updating other properties or by redrawing some or all of its drawing surface.</span></span>  
  
 <span data-ttu-id="f2f8f-111">下列範例會示範如何`FlashTrackBar`自訂控制項的回應它所繼承的屬性變更事件的一些<xref:System.Windows.Forms.Control>。</span><span class="sxs-lookup"><span data-stu-id="f2f8f-111">The following example shows how the `FlashTrackBar` custom control responds to some of the property-changed events that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="f2f8f-112">如需完整範例，請參閱[How to： 建立 Windows Form 控制項，顯示進度](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="f2f8f-112">For the complete sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f2f8f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2f8f-113">See Also</span></span>  
 [<span data-ttu-id="f2f8f-114">事件</span><span class="sxs-lookup"><span data-stu-id="f2f8f-114">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="f2f8f-115">Windows Forms 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="f2f8f-115">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="f2f8f-116">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="f2f8f-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
