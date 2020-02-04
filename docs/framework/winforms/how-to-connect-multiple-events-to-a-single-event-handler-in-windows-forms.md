---
title: 如何：將多個事件連接到單一事件處理常式
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
ms.openlocfilehash: 0591291522ab1da04fef90bf1c0a73cf33ba0518
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739602"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="a69d8-102">如何：在 Windows Form 中將多個事件連接到單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="a69d8-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="a69d8-103">在您的應用程式設計中，您可能會發現需要針對多個事件使用單一事件處理常式，或有多個事件執行相同程式。</span><span class="sxs-lookup"><span data-stu-id="a69d8-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="a69d8-104">例如，這通常是一種強大的時間保護，讓功能表命令引發相同的事件，就像表單上的按鈕一樣，如果它們公開相同的功能。</span><span class="sxs-lookup"><span data-stu-id="a69d8-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="a69d8-105">若要這麼做，您可以使用中C#屬性視窗的 [事件] 視圖，或使用 [Visual Basic 程式碼編輯器] 中的 [`Handles` 關鍵字] 和 [**類別名稱**] 和 [**方法名稱**] 下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="a69d8-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="a69d8-106">若要在 Visual Basic 中將多個事件連接到單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="a69d8-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="a69d8-107">以滑鼠右鍵按一下表單，然後選擇 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="a69d8-107">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="a69d8-108">從 [**類別名稱**] 下拉方塊中，選取您想要讓事件處理常式處理的其中一個控制項。</span><span class="sxs-lookup"><span data-stu-id="a69d8-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="a69d8-109">從 [**方法名稱**] 下拉方塊中，選取您想要事件處理常式處理的其中一個事件。</span><span class="sxs-lookup"><span data-stu-id="a69d8-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="a69d8-110">[程式碼編輯器] 會插入適當的事件處理常式，並將插入點置於方法內。</span><span class="sxs-lookup"><span data-stu-id="a69d8-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="a69d8-111">在下列範例中，這是 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="a69d8-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="a69d8-112">將您想要處理的其他事件附加至 `Handles` 子句。</span><span class="sxs-lookup"><span data-stu-id="a69d8-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="a69d8-113">將適當的程式碼加入事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a69d8-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="a69d8-114">若要將多個事件連接到 C\# 中的單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="a69d8-114">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="a69d8-115">選取您要連接事件處理常式的控制項。</span><span class="sxs-lookup"><span data-stu-id="a69d8-115">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="a69d8-116">在 屬性視窗中，按一下 **事件** 按鈕（[![事件] 按鈕](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")）。</span><span class="sxs-lookup"><span data-stu-id="a69d8-116">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="a69d8-117">按一下您要處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="a69d8-117">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="a69d8-118">在事件名稱旁的 [值] 區段中，按一下下拉式按鈕，顯示符合您要處理之事件之方法簽章的現有事件處理常式清單。</span><span class="sxs-lookup"><span data-stu-id="a69d8-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="a69d8-119">從清單中選取適當的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a69d8-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="a69d8-120">系統會將程式碼加入至表單，以將事件系結至現有的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a69d8-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a69d8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a69d8-121">See also</span></span>

- [<span data-ttu-id="a69d8-122">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="a69d8-122">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="a69d8-123">事件處理常式概觀</span><span class="sxs-lookup"><span data-stu-id="a69d8-123">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
