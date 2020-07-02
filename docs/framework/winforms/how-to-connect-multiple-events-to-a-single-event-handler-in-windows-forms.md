---
title: 如何：將多個事件連接到單一事件處理常式
description: '瞭解如何使用 c # 中屬性視窗的事件檢視，將多個事件連接到 Windows Forms 中的單一事件處理常式。'
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
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621882"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="e58d3-103">作法：在 Windows Forms 中將多個事件連接到單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="e58d3-103">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="e58d3-104">在您的應用程式設計中，您可能會發現需要針對多個事件使用單一事件處理常式，或有多個事件執行相同程式。</span><span class="sxs-lookup"><span data-stu-id="e58d3-104">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="e58d3-105">例如，這通常是一種強大的時間保護，讓功能表命令引發相同的事件，就像表單上的按鈕一樣，如果它們公開相同的功能。</span><span class="sxs-lookup"><span data-stu-id="e58d3-105">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="e58d3-106">若要這麼做，您可以使用 c # 中屬性視窗的 [事件] 視圖，或在 `Handles` [Visual Basic 程式碼編輯器] 中使用關鍵字和 [**類別名稱**] 和 [**方法名稱**] 下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="e58d3-106">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="e58d3-107">若要在 Visual Basic 中將多個事件連接到單一事件處理常式</span><span class="sxs-lookup"><span data-stu-id="e58d3-107">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="e58d3-108">以滑鼠右鍵按一下表單，然後選擇 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="e58d3-108">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="e58d3-109">從 [**類別名稱**] 下拉方塊中，選取您想要讓事件處理常式處理的其中一個控制項。</span><span class="sxs-lookup"><span data-stu-id="e58d3-109">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="e58d3-110">從 [**方法名稱**] 下拉方塊中，選取您想要事件處理常式處理的其中一個事件。</span><span class="sxs-lookup"><span data-stu-id="e58d3-110">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="e58d3-111">[程式碼編輯器] 會插入適當的事件處理常式，並將插入點置於方法內。</span><span class="sxs-lookup"><span data-stu-id="e58d3-111">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="e58d3-112">在下列範例中，這是 <xref:System.Windows.Forms.Control.Click> 控制項的事件 <xref:System.Windows.Forms.Button> 。</span><span class="sxs-lookup"><span data-stu-id="e58d3-112">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="e58d3-113">將您想要處理的其他事件附加至 `Handles` 子句。</span><span class="sxs-lookup"><span data-stu-id="e58d3-113">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="e58d3-114">將適當的程式碼加入事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e58d3-114">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="e58d3-115">若要將多個事件連接到 C 中的單一事件處理常式\#</span><span class="sxs-lookup"><span data-stu-id="e58d3-115">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="e58d3-116">選取您要連接事件處理常式的控制項。</span><span class="sxs-lookup"><span data-stu-id="e58d3-116">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="e58d3-117">在 [屬性視窗中，按一下 [**事件**] 按鈕（[![事件] 按鈕](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")）。</span><span class="sxs-lookup"><span data-stu-id="e58d3-117">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="e58d3-118">按一下您要處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="e58d3-118">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="e58d3-119">在事件名稱旁的 [值] 區段中，按一下下拉式按鈕，顯示符合您要處理之事件之方法簽章的現有事件處理常式清單。</span><span class="sxs-lookup"><span data-stu-id="e58d3-119">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="e58d3-120">從清單中選取適當的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e58d3-120">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="e58d3-121">系統會將程式碼加入至表單，以將事件系結至現有的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e58d3-121">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e58d3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e58d3-122">See also</span></span>

- [<span data-ttu-id="e58d3-123">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="e58d3-123">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="e58d3-124">事件處理常式概觀</span><span class="sxs-lookup"><span data-stu-id="e58d3-124">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
