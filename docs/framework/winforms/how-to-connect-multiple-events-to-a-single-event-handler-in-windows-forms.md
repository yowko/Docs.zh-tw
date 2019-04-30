---
title: HOW TO：在 Windows Forms 中將多個事件連接到單一事件處理常式
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: eec6a754b885cd169e5542221caefb3233c4c8af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967010"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="e0b9f-102">HOW TO：在 Windows Forms 中將多個事件連接到單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="e0b9f-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="e0b9f-103">在您的應用程式的設計，您可能會發現需要使用多個事件的單一事件處理常式，或有多個執行相同的程序的事件。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="e0b9f-104">比方說，它通常是功能強大時間的好幫手能夠引發相同的事件，如您在表單上的按鈕執行作業，如果它們在相同的功能公開 （expose） 的功能表命令。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="e0b9f-105">您可以使用 [事件] 檢視中的 [屬性] 視窗的C#或使用`Handles`關鍵字和**類別名稱**並**方法名稱**下拉式清單方塊，在 Visual Basic 程式碼編輯器中。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="e0b9f-106">若要將多個事件連線至 Visual Basic 中的單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="e0b9f-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="e0b9f-107">以滑鼠右鍵按一下表單，然後選擇 **檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-107">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="e0b9f-108">從**類別名稱**下拉式清單方塊中，選取其中一個您想要處理的事件處理常式的控制項。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="e0b9f-109">從**方法名稱**下拉式清單方塊中，選取其中一個您想要處理的事件處理常式的事件。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="e0b9f-110">程式碼編輯器會插入適當的事件處理常式，並將插入點置於方法中。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="e0b9f-111">在下列範例中，很<xref:System.Windows.Forms.Control.Click>事件<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="e0b9f-112">附加其他您想要處理的事件至`Handles`子句。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="e0b9f-113">事件處理常式中加入適當的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="e0b9f-114">若要將多個事件連線至在 C 中的單一事件處理常式\#</span><span class="sxs-lookup"><span data-stu-id="e0b9f-114">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="e0b9f-115">選取您要連接的事件處理常式的控制項。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-115">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="e0b9f-116">在 [屬性] 視窗中，按一下**事件** 按鈕 (![事件按鈕](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow"))。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-116">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="e0b9f-117">按一下您想要處理之事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-117">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="e0b9f-118">在 事件名稱旁的 值 區段中，按一下下拉式按鈕，以顯示符合您想要處理事件的方法簽章的現有事件處理常式的清單。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="e0b9f-119">從清單中選取適當的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="e0b9f-120">程式碼會加入至表單，以將事件繫結至現有的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e0b9f-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0b9f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0b9f-121">See also</span></span>

- [<span data-ttu-id="e0b9f-122">在 Windows Forms 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="e0b9f-122">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="e0b9f-123">事件處理常式概觀</span><span class="sxs-lookup"><span data-stu-id="e0b9f-123">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
