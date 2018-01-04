---
title: "處理使用者輸入"
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
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0102bab4fad3b224100ae054f572d9b07102fc15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="handling-user-input"></a><span data-ttu-id="39a78-102">處理使用者輸入</span><span class="sxs-lookup"><span data-stu-id="39a78-102">Handling User Input</span></span>
<span data-ttu-id="39a78-103">本主題描述所提供的主要鍵盤和滑鼠事件<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="39a78-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="39a78-104">處理事件時，控制項作者應覆寫受保護的 `On`*EventName* 方法，而不是將委派附加至事件。</span><span class="sxs-lookup"><span data-stu-id="39a78-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="39a78-105">如需檢閱事件，請參閱[從元件引發事件](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0)。</span><span class="sxs-lookup"><span data-stu-id="39a78-105">For a review of events, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39a78-106">如果沒有與某個事件時，基底類別的執行個體相關聯的資料<xref:System.EventArgs>做為引數會傳遞`On` *EventName*方法。</span><span class="sxs-lookup"><span data-stu-id="39a78-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="39a78-107">鍵盤事件</span><span class="sxs-lookup"><span data-stu-id="39a78-107">Keyboard Events</span></span>  
 <span data-ttu-id="39a78-108">通用控制項可以處理的鍵盤事件<xref:System.Windows.Forms.Control.KeyDown>， <xref:System.Windows.Forms.Control.KeyPress>，和<xref:System.Windows.Forms.Control.KeyUp>。</span><span class="sxs-lookup"><span data-stu-id="39a78-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="39a78-109">事件名稱</span><span class="sxs-lookup"><span data-stu-id="39a78-109">Event Name</span></span>|<span data-ttu-id="39a78-110">要覆寫的方法</span><span class="sxs-lookup"><span data-stu-id="39a78-110">Method to Override</span></span>|<span data-ttu-id="39a78-111">事件的描述</span><span class="sxs-lookup"><span data-stu-id="39a78-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="39a78-112">只在最初按下按鍵時引發。</span><span class="sxs-lookup"><span data-stu-id="39a78-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="39a78-113">每次按下按鍵時引發。</span><span class="sxs-lookup"><span data-stu-id="39a78-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="39a78-114">如果按住按鍵，<xref:System.Windows.Forms.Control.KeyPress>在作業系統所定義的重複率引發事件。</span><span class="sxs-lookup"><span data-stu-id="39a78-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="39a78-115">在放開按鍵時引發。</span><span class="sxs-lookup"><span data-stu-id="39a78-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="39a78-116">相較於覆寫上表中的事件，處理鍵盤輸入更為複雜，而且已超出本主題的範圍。</span><span class="sxs-lookup"><span data-stu-id="39a78-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="39a78-117">如需詳細資訊，請參閱 [Windows Forms 中的使用者輸入](../../../../docs/framework/winforms/user-input-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="39a78-117">For more information, see [User Input in Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="39a78-118">滑鼠事件</span><span class="sxs-lookup"><span data-stu-id="39a78-118">Mouse Events</span></span>  
 <span data-ttu-id="39a78-119">您的控制項可以處理的滑鼠事件是<xref:System.Windows.Forms.Control.MouseDown>， <xref:System.Windows.Forms.Control.MouseEnter>， <xref:System.Windows.Forms.Control.MouseHover>， <xref:System.Windows.Forms.Control.MouseLeave>， <xref:System.Windows.Forms.Control.MouseMove>，和<xref:System.Windows.Forms.Control.MouseUp>。</span><span class="sxs-lookup"><span data-stu-id="39a78-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="39a78-120">事件名稱</span><span class="sxs-lookup"><span data-stu-id="39a78-120">Event Name</span></span>|<span data-ttu-id="39a78-121">要覆寫的方法</span><span class="sxs-lookup"><span data-stu-id="39a78-121">Method to Override</span></span>|<span data-ttu-id="39a78-122">事件的描述</span><span class="sxs-lookup"><span data-stu-id="39a78-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="39a78-123">當滑鼠指標位於控制項上並按下滑鼠按鈕時引發。</span><span class="sxs-lookup"><span data-stu-id="39a78-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="39a78-124">當滑鼠指標第一次進入控制項的區域時引發。</span><span class="sxs-lookup"><span data-stu-id="39a78-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="39a78-125">當滑鼠指標停留在控制項上時引發。</span><span class="sxs-lookup"><span data-stu-id="39a78-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="39a78-126">當滑鼠指標離開控制項的區域時引發。</span><span class="sxs-lookup"><span data-stu-id="39a78-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="39a78-127">當滑鼠指標移入控制項的區域時引發。</span><span class="sxs-lookup"><span data-stu-id="39a78-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="39a78-128">當滑鼠指標位於控制項上並放開滑鼠按鈕時或當滑鼠指標離開控制項的區域時引發。</span><span class="sxs-lookup"><span data-stu-id="39a78-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="39a78-129">下列程式碼片段顯示的覆寫範例<xref:System.Windows.Forms.Control.MouseDown>事件。</span><span class="sxs-lookup"><span data-stu-id="39a78-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="39a78-130">下列程式碼片段顯示的覆寫範例<xref:System.Windows.Forms.Control.MouseMove>事件。</span><span class="sxs-lookup"><span data-stu-id="39a78-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="39a78-131">下列程式碼片段顯示的覆寫範例<xref:System.Windows.Forms.Control.MouseUp>事件。</span><span class="sxs-lookup"><span data-stu-id="39a78-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="39a78-132">如需 `FlashTrackBar` 的完整原始程式碼，請參閱[如何：建立可顯示進度的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。</span><span class="sxs-lookup"><span data-stu-id="39a78-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a78-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="39a78-133">See Also</span></span>  
 [<span data-ttu-id="39a78-134">Windows Forms 控制項中的事件</span><span class="sxs-lookup"><span data-stu-id="39a78-134">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="39a78-135">定義事件</span><span class="sxs-lookup"><span data-stu-id="39a78-135">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="39a78-136">事件</span><span class="sxs-lookup"><span data-stu-id="39a78-136">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="39a78-137">Windows Forms 中的使用者輸入</span><span class="sxs-lookup"><span data-stu-id="39a78-137">User Input in Windows Forms</span></span>](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
