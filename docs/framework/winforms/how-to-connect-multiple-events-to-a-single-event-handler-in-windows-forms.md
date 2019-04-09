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
ms.openlocfilehash: d55ccc21efb92ba1e51f4ae88be5025f2f80905b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117958"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="d77c8-102">HOW TO：在 Windows Forms 中將多個事件連接到單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="d77c8-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="d77c8-103">在您的應用程式的設計，您可能會發現需要使用多個事件的單一事件處理常式，或有多個執行相同的程序的事件。</span><span class="sxs-lookup"><span data-stu-id="d77c8-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="d77c8-104">比方說，它通常是功能強大時間的好幫手能夠引發相同的事件，如您在表單上的按鈕執行作業，如果它們在相同的功能公開 （expose） 的功能表命令。</span><span class="sxs-lookup"><span data-stu-id="d77c8-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="d77c8-105">您可以使用 [事件] 檢視中的 [屬性] 視窗的C#或使用`Handles`關鍵字和**類別名稱**並**方法名稱**下拉式清單方塊，在 Visual Basic 程式碼編輯器中。</span><span class="sxs-lookup"><span data-stu-id="d77c8-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="d77c8-106">若要將多個事件連線至 Visual Basic 中的單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="d77c8-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1.  <span data-ttu-id="d77c8-107">以滑鼠右鍵按一下表單，然後選擇 **檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="d77c8-107">Right-click the form and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="d77c8-108">從**類別名稱**下拉式清單方塊中，選取其中一個您想要處理的事件處理常式的控制項。</span><span class="sxs-lookup"><span data-stu-id="d77c8-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3.  <span data-ttu-id="d77c8-109">從**方法名稱**下拉式清單方塊中，選取其中一個您想要處理的事件處理常式的事件。</span><span class="sxs-lookup"><span data-stu-id="d77c8-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4.  <span data-ttu-id="d77c8-110">程式碼編輯器會插入適當的事件處理常式，並將插入點置於方法中。</span><span class="sxs-lookup"><span data-stu-id="d77c8-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="d77c8-111">在下列範例中，很<xref:System.Windows.Forms.Control.Click>事件<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="d77c8-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  <span data-ttu-id="d77c8-112">附加其他您想要處理的事件至`Handles`子句。</span><span class="sxs-lookup"><span data-stu-id="d77c8-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  <span data-ttu-id="d77c8-113">事件處理常式中加入適當的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d77c8-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="d77c8-114">若要將多個事件連線至在 C 中的單一事件處理常式\#</span><span class="sxs-lookup"><span data-stu-id="d77c8-114">To connect multiple events to a single event handler in C\#</span></span>
  
1.  <span data-ttu-id="d77c8-115">選取您要連接的事件處理常式的控制項。</span><span class="sxs-lookup"><span data-stu-id="d77c8-115">Select the control to which you want to connect an event handler.</span></span>  
  
2.  <span data-ttu-id="d77c8-116">在 [屬性] 視窗中，按一下**事件** 按鈕 (![事件按鈕](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow"))。</span><span class="sxs-lookup"><span data-stu-id="d77c8-116">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3.  <span data-ttu-id="d77c8-117">按一下您想要處理之事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="d77c8-117">Click the name of the event that you want to handle.</span></span>  
  
4.  <span data-ttu-id="d77c8-118">在 事件名稱旁的 值 區段中，按一下下拉式按鈕，以顯示符合您想要處理事件的方法簽章的現有事件處理常式的清單。</span><span class="sxs-lookup"><span data-stu-id="d77c8-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5.  <span data-ttu-id="d77c8-119">從清單中選取適當的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d77c8-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="d77c8-120">程式碼會加入至表單，以將事件繫結至現有的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d77c8-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d77c8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d77c8-121">See also</span></span>

- [<span data-ttu-id="d77c8-122">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="d77c8-122">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="d77c8-123">事件處理常式概觀</span><span class="sxs-lookup"><span data-stu-id="d77c8-123">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
