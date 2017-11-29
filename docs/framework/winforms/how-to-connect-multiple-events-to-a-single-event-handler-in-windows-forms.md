---
title: "如何：在 Windows Form 中連接多個事件至單一事件處理常式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4aa22b011b895a20cefdcc5a7c9e6c1cd0531923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="8e0ce-102">如何：在 Windows Form 中連接多個事件至單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="8e0ce-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="8e0ce-103">設計您的應用程式，您可能會發現需要將多個事件使用單一事件處理常式，或是必須執行相同的程序的多個事件。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="8e0ce-104">比方說，它通常是功能強大的節省時間讓功能表命令，您的表單上的按鈕不會公開相同的功能像引發相同的事件。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="8e0ce-105">您可以使用 C# 中的 [屬性] 視窗的 [事件] 檢視或使用`Handles`關鍵字和**類別名稱**和**方法名稱**下拉式清單方塊在 Visual Basic 程式碼編輯器中。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="8e0ce-106">若要連接到單一事件處理常式，在 Visual Basic 中的多個事件</span><span class="sxs-lookup"><span data-stu-id="8e0ce-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1.  <span data-ttu-id="8e0ce-107">以滑鼠右鍵按一下表單，然後選擇 **檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-107">Right-click the form and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="8e0ce-108">從**類別名稱**下拉式清單方塊中，選取您想要處理此事件處理常式的控制項的其中一個。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3.  <span data-ttu-id="8e0ce-109">從**方法名稱**下拉式清單方塊中，選取其中一個要處理的事件處理常式的事件。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4.  <span data-ttu-id="8e0ce-110">程式碼編輯器會插入適當的事件處理常式，並將插入點置於方法內。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="8e0ce-111">在下列範例中，它是<xref:System.Windows.Forms.Control.Click>事件<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  <span data-ttu-id="8e0ce-112">新增其他您想要處理的事件至`Handles`子句。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  <span data-ttu-id="8e0ce-113">事件處理常式中加入適當的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="8e0ce-114">若要連接到單一事件處理常式在 C# 中的多個事件</span><span class="sxs-lookup"><span data-stu-id="8e0ce-114">To connect multiple events to a single event handler in C#</span></span>  
  
1.  <span data-ttu-id="8e0ce-115">選取您要連接的事件處理常式的控制項。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-115">Select the control to which you want to connect an event handler.</span></span>  
  
2.  <span data-ttu-id="8e0ce-116">在 [屬性] 視窗中，按一下**事件**按鈕 (![事件按鈕](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow"))。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-116">In the Properties window, click the **Events** button (![Events Button](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3.  <span data-ttu-id="8e0ce-117">按一下您想要處理之事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-117">Click the name of the event that you want to handle.</span></span>  
  
4.  <span data-ttu-id="8e0ce-118">在事件名稱旁的 [值] 區段中，按一下下拉式按鈕，以顯示符合您想要處理事件的方法簽章的現有事件處理常式的清單。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5.  <span data-ttu-id="8e0ce-119">從清單中選取適當的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="8e0ce-120">程式碼會加入至表單，以將事件繫結至現有的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e0ce-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e0ce-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e0ce-121">See Also</span></span>  
 [<span data-ttu-id="8e0ce-122">在 Windows Forms 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="8e0ce-122">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="8e0ce-123">事件處理常式概觀</span><span class="sxs-lookup"><span data-stu-id="8e0ce-123">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
