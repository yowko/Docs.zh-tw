---
title: 處理事件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 3ade8eae67d29e2f3cb42911e42ed8696623db62
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507894"
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="b811e-102">逐步解說：處理事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b811e-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="b811e-103">這是示範如何使用事件的兩個主題的第二個。</span><span class="sxs-lookup"><span data-stu-id="b811e-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="b811e-104">第一個主題中，[逐步解說： 宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)，示範如何宣告及引發事件。</span><span class="sxs-lookup"><span data-stu-id="b811e-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="b811e-105">本節會使用表單和類別，從該逐步解說示範如何處理它們發生的事件。</span><span class="sxs-lookup"><span data-stu-id="b811e-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="b811e-106">`Widget`類別的範例會使用傳統的事件處理陳述式。</span><span class="sxs-lookup"><span data-stu-id="b811e-106">The `Widget` class example uses traditional event-handling statements.</span></span> <span data-ttu-id="b811e-107">Visual Basic 會提供其他技術來處理事件。</span><span class="sxs-lookup"><span data-stu-id="b811e-107">Visual Basic provides other techniques for working with events.</span></span> <span data-ttu-id="b811e-108">在練習中，您可以修改此範例中使用`AddHandler`和`Handles`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b811e-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="b811e-109">若要處理 PercentDone 類別之事件的小工具</span><span class="sxs-lookup"><span data-stu-id="b811e-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="b811e-110">將下列程式碼中的`Form1`:</span><span class="sxs-lookup"><span data-stu-id="b811e-110">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     <span data-ttu-id="b811e-111">`WithEvents`關鍵字指定變數`mWidget`用來處理物件的事件。</span><span class="sxs-lookup"><span data-stu-id="b811e-111">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="b811e-112">您可以提供將從中建立物件的類別名稱指定物件的類型。</span><span class="sxs-lookup"><span data-stu-id="b811e-112">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="b811e-113">變數`mWidget`中宣告`Form1`因為`WithEvents`變數必須是類別層級。</span><span class="sxs-lookup"><span data-stu-id="b811e-113">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="b811e-114">這是不論您將它們放入類別的型別，則為 true。</span><span class="sxs-lookup"><span data-stu-id="b811e-114">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="b811e-115">變數`mblnCancel`用來取消`LongTask`方法。</span><span class="sxs-lookup"><span data-stu-id="b811e-115">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="b811e-116">撰寫程式碼來處理事件</span><span class="sxs-lookup"><span data-stu-id="b811e-116">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="b811e-117">當您宣告變數 using `WithEvents`，變數的名稱會出現在左邊的下拉式清單，此類別的**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="b811e-117">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="b811e-118">當您選取`mWidget`，則`Widget`類別的事件會出現在右邊下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="b811e-118">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="b811e-119">選取的事件會顯示對應的事件程序，以首碼`mWidget`和底線。</span><span class="sxs-lookup"><span data-stu-id="b811e-119">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="b811e-120">與相關聯的所有事件程序`WithEvents`變數指定變數的名稱，做為前置詞。</span><span class="sxs-lookup"><span data-stu-id="b811e-120">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="b811e-121">若要處理的事件</span><span class="sxs-lookup"><span data-stu-id="b811e-121">To handle an event</span></span>  
  
1.  <span data-ttu-id="b811e-122">選取 `mWidget`左邊的下拉式清單中從**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="b811e-122">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="b811e-123">選取`PercentDone`右邊下拉式清單中的事件。</span><span class="sxs-lookup"><span data-stu-id="b811e-123">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="b811e-124">**程式碼編輯器**開啟`mWidget_PercentDone`事件程序。</span><span class="sxs-lookup"><span data-stu-id="b811e-124">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b811e-125">**程式碼編輯器**十分有用，但並非必要，插入新的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b811e-125">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="b811e-126">在此逐步解說中，它是更為直接的方式只是事件處理常式將直接複製到您的程式碼項目。</span><span class="sxs-lookup"><span data-stu-id="b811e-126">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="b811e-127">將下列程式碼加入至 `mWidget_PercentDone` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="b811e-127">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     <span data-ttu-id="b811e-128">每當`PercentDone`就會引發事件時，將事件程序會顯示完成百分比`Label`控制項。</span><span class="sxs-lookup"><span data-stu-id="b811e-128">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="b811e-129">`DoEvents`方法可讓標籤以重新繪製，並提供使用者有機會按一下 [**取消**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b811e-129">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="b811e-130">新增下列程式碼`Button2_Click`事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="b811e-130">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 <span data-ttu-id="b811e-131">如果使用者按一下**取消**按鈕時`LongTask`正在執行，`Button2_Click`執行事件，只要`DoEvents`陳述式可讓發生的事件處理。</span><span class="sxs-lookup"><span data-stu-id="b811e-131">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="b811e-132">類別層級變數`mblnCancel`設定為`True`，而`mWidget_PercentDone`事件然後測試它，並設定`ByRef Cancel`引數`True`。</span><span class="sxs-lookup"><span data-stu-id="b811e-132">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="b811e-133">連接 WithEvents 變數的物件</span><span class="sxs-lookup"><span data-stu-id="b811e-133">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="b811e-134">`Form1` 現在來處理設定`Widget`物件的事件。</span><span class="sxs-lookup"><span data-stu-id="b811e-134">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="b811e-135">剩下的就尋找是`Widget`某處。</span><span class="sxs-lookup"><span data-stu-id="b811e-135">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="b811e-136">當您宣告變數時`WithEvents`在設計階段物件不是與它相關聯。</span><span class="sxs-lookup"><span data-stu-id="b811e-136">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="b811e-137">A`WithEvents`變數，就如同任何其他物件的變數。</span><span class="sxs-lookup"><span data-stu-id="b811e-137">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="b811e-138">您必須建立物件，並將參考指派給它與`WithEvents`變數。</span><span class="sxs-lookup"><span data-stu-id="b811e-138">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="b811e-139">若要建立物件，並指派給它的參考</span><span class="sxs-lookup"><span data-stu-id="b811e-139">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="b811e-140">選取  **（Form1 事件）** 左邊的下拉式清單中從**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="b811e-140">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="b811e-141">選取`Load`右邊下拉式清單中的事件。</span><span class="sxs-lookup"><span data-stu-id="b811e-141">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="b811e-142">**程式碼編輯器**開啟`Form1_Load`事件程序。</span><span class="sxs-lookup"><span data-stu-id="b811e-142">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="b811e-143">新增下列程式碼`Form1_Load`事件的程序來建立`Widget`:</span><span class="sxs-lookup"><span data-stu-id="b811e-143">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 <span data-ttu-id="b811e-144">此程式碼執行時，Visual Basic 建立`Widget`物件，並將其事件連接至相關聯的事件程序`mWidget`。</span><span class="sxs-lookup"><span data-stu-id="b811e-144">When this code executes, Visual Basic creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="b811e-145">從該點上，每當`Widget`引發其`PercentDone`事件，`mWidget_PercentDone`事件程序執行。</span><span class="sxs-lookup"><span data-stu-id="b811e-145">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="b811e-146">若要呼叫 LongTask 方法</span><span class="sxs-lookup"><span data-stu-id="b811e-146">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="b811e-147">將下列程式碼加入至 `Button1_Click` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="b811e-147">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 <span data-ttu-id="b811e-148">再`LongTask`呼叫方法時，標籤必須初始化完成的百分比，顯示項目，以及類別層級`Boolean`旗標的取消方法必須設為`False`。</span><span class="sxs-lookup"><span data-stu-id="b811e-148">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="b811e-149">`LongTask` 稱為工作持續時間為 12.2 的秒數。</span><span class="sxs-lookup"><span data-stu-id="b811e-149">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="b811e-150">`PercentDone`事件引發一次每三分之一的第二個。</span><span class="sxs-lookup"><span data-stu-id="b811e-150">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="b811e-151">引發事件時，每次`mWidget_PercentDone`事件程序執行。</span><span class="sxs-lookup"><span data-stu-id="b811e-151">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="b811e-152">當`LongTask`完成後，`mblnCancel`測試是否`LongTask`一般來說，結束或如果它停止，因為`mblnCancel`已設為`True`。</span><span class="sxs-lookup"><span data-stu-id="b811e-152">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="b811e-153">前一個案例中只會更新以完成百分比表示。</span><span class="sxs-lookup"><span data-stu-id="b811e-153">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="b811e-154">執行程式</span><span class="sxs-lookup"><span data-stu-id="b811e-154">To run the program</span></span>  
  
1.  <span data-ttu-id="b811e-155">若要將專案放在執行模式中按 f5 鍵。</span><span class="sxs-lookup"><span data-stu-id="b811e-155">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="b811e-156">按一下 [**開始工作**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b811e-156">Click the **Start Task** button.</span></span> <span data-ttu-id="b811e-157">每次`PercentDone`就會引發事件，標籤已更新之工作的完成百分比。</span><span class="sxs-lookup"><span data-stu-id="b811e-157">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="b811e-158">按一下 **取消**按鈕以停止工作。</span><span class="sxs-lookup"><span data-stu-id="b811e-158">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="b811e-159">請注意的外觀**取消**按鈕不會變更，請立即按一下它。</span><span class="sxs-lookup"><span data-stu-id="b811e-159">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="b811e-160">`Click`事件不會發生之前`My.Application.DoEvents`陳述式可讓事件處理。</span><span class="sxs-lookup"><span data-stu-id="b811e-160">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b811e-161">`My.Application.DoEvents`方法不會處理事件中完全相同的方式像表單一樣。</span><span class="sxs-lookup"><span data-stu-id="b811e-161">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="b811e-162">例如，在此逐步解說中，您必須按一下**取消**按鈕兩次。</span><span class="sxs-lookup"><span data-stu-id="b811e-162">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="b811e-163">若要允許表單以直接處理事件，您可以使用多執行緒處理。</span><span class="sxs-lookup"><span data-stu-id="b811e-163">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="b811e-164">如需詳細資訊，請參閱 <<c0> [ 執行緒](https://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)。</span><span class="sxs-lookup"><span data-stu-id="b811e-164">For more information, see [Threading](https://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="b811e-165">您可能會發現使用 f11 鍵執行程式，並逐步執行程式碼行一次會更有意義。</span><span class="sxs-lookup"><span data-stu-id="b811e-165">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="b811e-166">您可以清楚地看到如何執行進入`LongTask`，，然後簡短重新進入`Form1`每次`PercentDone`就會引發事件。</span><span class="sxs-lookup"><span data-stu-id="b811e-166">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="b811e-167">會發生什麼事如果時執行的程式碼中的上一步`Form1`，則`LongTask`方法所呼叫一次？</span><span class="sxs-lookup"><span data-stu-id="b811e-167">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="b811e-168">最糟的情況，如果可能會發生堆疊溢位`LongTask`每次引發事件所呼叫。</span><span class="sxs-lookup"><span data-stu-id="b811e-168">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="b811e-169">您可能會導致變數`mWidget`來處理事件的不同`Widget`物件至新的參考指派`Widget`至`mWidget`。</span><span class="sxs-lookup"><span data-stu-id="b811e-169">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="b811e-170">事實上，您可以在其中進行中的程式碼`Button1_Click`這樣做，每次您按一下按鈕。</span><span class="sxs-lookup"><span data-stu-id="b811e-170">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="b811e-171">若要處理不同的小工具的事件</span><span class="sxs-lookup"><span data-stu-id="b811e-171">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="b811e-172">新增下列一行程式碼`Button1_Click`程序中，緊接在之前讀取一行`mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="b811e-172">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 <span data-ttu-id="b811e-173">上述程式碼會建立新`Widget`每當按一下按鈕時。</span><span class="sxs-lookup"><span data-stu-id="b811e-173">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="b811e-174">一旦`LongTask`方法完成時，若要參考`Widget`已釋放，而`Widget`終結。</span><span class="sxs-lookup"><span data-stu-id="b811e-174">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="b811e-175">A`WithEvents`變數可以包含只有一個物件參考一次，因此，如果您可以指派不同`Widget`物件`mWidget`，先前`Widget`物件的事件將不會再進行處理。</span><span class="sxs-lookup"><span data-stu-id="b811e-175">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="b811e-176">如果`mWidget`是唯一的物件變數包含舊的參考`Widget`，終結物件。</span><span class="sxs-lookup"><span data-stu-id="b811e-176">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="b811e-177">如果您想要處理來自數個事件`Widget`物件，使用`AddHandler`陳述式來個別處理每個物件的事件。</span><span class="sxs-lookup"><span data-stu-id="b811e-177">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b811e-178">您可以宣告多個`WithEvents`變數做為您的需要但陣列`WithEvents`不支援變數。</span><span class="sxs-lookup"><span data-stu-id="b811e-178">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b811e-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b811e-179">See Also</span></span>  
 [<span data-ttu-id="b811e-180">逐步解說：宣告和引發事件</span><span class="sxs-lookup"><span data-stu-id="b811e-180">Walkthrough: Declaring and Raising Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [<span data-ttu-id="b811e-181">事件</span><span class="sxs-lookup"><span data-stu-id="b811e-181">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
