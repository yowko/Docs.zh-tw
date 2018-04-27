---
title: 處理事件 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c1743e5f5d9dcdf83ab646407cd1fcdc77ff71cd
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="26e26-102">逐步解說：處理事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26e26-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="26e26-103">這是兩個主題會示範如何使用事件的第二個。</span><span class="sxs-lookup"><span data-stu-id="26e26-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="26e26-104">第一個主題，[逐步解說： 宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)，示範如何宣告和引發事件。</span><span class="sxs-lookup"><span data-stu-id="26e26-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="26e26-105">本節會使用表單和類別，從該逐步解說顯示如何處理時就會發生的事件。</span><span class="sxs-lookup"><span data-stu-id="26e26-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="26e26-106">`Widget`類別範例會使用傳統的事件處理陳述式。</span><span class="sxs-lookup"><span data-stu-id="26e26-106">The `Widget` class example uses traditional event-handling statements.</span></span> <span data-ttu-id="26e26-107">Visual Basic 提供其他技術使用的事件。</span><span class="sxs-lookup"><span data-stu-id="26e26-107">Visual Basic provides other techniques for working with events.</span></span> <span data-ttu-id="26e26-108">做為練習，您可以修改此範例中使用`AddHandler`和`Handles`陳述式。</span><span class="sxs-lookup"><span data-stu-id="26e26-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="26e26-109">若要處理 PercentDone 類別之事件的小工具</span><span class="sxs-lookup"><span data-stu-id="26e26-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="26e26-110">將下列程式碼中的`Form1`:</span><span class="sxs-lookup"><span data-stu-id="26e26-110">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     <span data-ttu-id="26e26-111">`WithEvents`關鍵字指定變數`mWidget`用來處理物件的事件。</span><span class="sxs-lookup"><span data-stu-id="26e26-111">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="26e26-112">您可以提供要從中建立物件的類別名稱指定物件的類型。</span><span class="sxs-lookup"><span data-stu-id="26e26-112">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="26e26-113">變數`mWidget`中宣告`Form1`因為`WithEvents`變數必須是類別層級。</span><span class="sxs-lookup"><span data-stu-id="26e26-113">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="26e26-114">這是不論您放在類別的型別，則為 true。</span><span class="sxs-lookup"><span data-stu-id="26e26-114">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="26e26-115">變數`mblnCancel`用來取消`LongTask`方法。</span><span class="sxs-lookup"><span data-stu-id="26e26-115">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="26e26-116">撰寫程式碼以處理事件</span><span class="sxs-lookup"><span data-stu-id="26e26-116">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="26e26-117">當您宣告變數使用`WithEvents`，變數的名稱會出現在左邊的下拉式清單，此類別的**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="26e26-117">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="26e26-118">當您選取`mWidget`、`Widget`類別的事件會出現在右邊下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="26e26-118">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="26e26-119">選取的事件會顯示對應的事件程序，具有該前置詞`mWidget`和底線。</span><span class="sxs-lookup"><span data-stu-id="26e26-119">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="26e26-120">與相關聯的所有事件程序`WithEvents`變數指定變數的名稱，做為前置詞。</span><span class="sxs-lookup"><span data-stu-id="26e26-120">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="26e26-121">若要處理的事件</span><span class="sxs-lookup"><span data-stu-id="26e26-121">To handle an event</span></span>  
  
1.  <span data-ttu-id="26e26-122">選取`mWidget`左邊的下拉式清單中從**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="26e26-122">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="26e26-123">選取`PercentDone`右邊下拉式清單中的事件。</span><span class="sxs-lookup"><span data-stu-id="26e26-123">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="26e26-124">**程式碼編輯器**開啟`mWidget_PercentDone`事件程序。</span><span class="sxs-lookup"><span data-stu-id="26e26-124">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26e26-125">**程式碼編輯器**十分有用，但不是必要插入新的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="26e26-125">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="26e26-126">在本逐步解說中，它是更為直接的方式只複製直接插入程式碼的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="26e26-126">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="26e26-127">將下列程式碼加入至 `mWidget_PercentDone` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="26e26-127">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     <span data-ttu-id="26e26-128">每當`PercentDone`就會引發事件，將事件程序會顯示在完成百分比`Label`控制項。</span><span class="sxs-lookup"><span data-stu-id="26e26-128">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="26e26-129">`DoEvents`方法可讓重新繪製，標籤，也可讓使用者得以按一下**取消** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="26e26-129">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="26e26-130">加入下列程式碼`Button2_Click`事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="26e26-130">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 <span data-ttu-id="26e26-131">如果使用者按一下**取消**按鈕時`LongTask`正在執行，`Button2_Click`事件執行儘速`DoEvents`陳述式可讓事件處理發生。</span><span class="sxs-lookup"><span data-stu-id="26e26-131">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="26e26-132">類別層級變數`mblnCancel`設`True`，而`mWidget_PercentDone`事件進行測試，然後設定`ByRef Cancel`引數`True`。</span><span class="sxs-lookup"><span data-stu-id="26e26-132">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="26e26-133">連接 WithEvents 變數的物件</span><span class="sxs-lookup"><span data-stu-id="26e26-133">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="26e26-134">`Form1` 現在設定為處理`Widget`物件的事件。</span><span class="sxs-lookup"><span data-stu-id="26e26-134">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="26e26-135">若要尋找的剩下的只有`Widget`某處。</span><span class="sxs-lookup"><span data-stu-id="26e26-135">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="26e26-136">當您宣告變數`WithEvents`在設計階段物件不是有與其相關聯。</span><span class="sxs-lookup"><span data-stu-id="26e26-136">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="26e26-137">A`WithEvents`變數，就如同任何其他物件的變數。</span><span class="sxs-lookup"><span data-stu-id="26e26-137">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="26e26-138">您必須建立的物件，並將參考指派給它與`WithEvents`變數。</span><span class="sxs-lookup"><span data-stu-id="26e26-138">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="26e26-139">若要建立的物件，並指派給它的參考</span><span class="sxs-lookup"><span data-stu-id="26e26-139">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="26e26-140">選取**（Form1 事件）**左邊的下拉式清單中從**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="26e26-140">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="26e26-141">選取`Load`右邊下拉式清單中的事件。</span><span class="sxs-lookup"><span data-stu-id="26e26-141">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="26e26-142">**程式碼編輯器**開啟`Form1_Load`事件程序。</span><span class="sxs-lookup"><span data-stu-id="26e26-142">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="26e26-143">加入下列程式碼`Form1_Load`事件程序來建立`Widget`:</span><span class="sxs-lookup"><span data-stu-id="26e26-143">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 <span data-ttu-id="26e26-144">此程式碼執行時，Visual Basic 建立`Widget`物件，並連接其事件相關聯的事件程序`mWidget`。</span><span class="sxs-lookup"><span data-stu-id="26e26-144">When this code executes, Visual Basic creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="26e26-145">從該點上，每當`Widget`引發其`PercentDone`事件，`mWidget_PercentDone`執行事件程序。</span><span class="sxs-lookup"><span data-stu-id="26e26-145">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="26e26-146">若要呼叫 LongTask 方法</span><span class="sxs-lookup"><span data-stu-id="26e26-146">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="26e26-147">將下列程式碼加入至 `Button1_Click` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="26e26-147">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 <span data-ttu-id="26e26-148">之前`LongTask`呼叫方法時，標籤，必須先初始化的顯示完成百分比，以及類別層級`Boolean`旗標的取消方法必須設為`False`。</span><span class="sxs-lookup"><span data-stu-id="26e26-148">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="26e26-149">`LongTask` 會呼叫工作持續時間為 12.2 秒。</span><span class="sxs-lookup"><span data-stu-id="26e26-149">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="26e26-150">`PercentDone`引發一次每三分之一的第二個。</span><span class="sxs-lookup"><span data-stu-id="26e26-150">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="26e26-151">引發事件時，每次`mWidget_PercentDone`執行事件程序。</span><span class="sxs-lookup"><span data-stu-id="26e26-151">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="26e26-152">當`LongTask`完畢後，`mblnCancel`測試是否`LongTask`正常，結束或它停止，因為如果`mblnCancel`已設為`True`。</span><span class="sxs-lookup"><span data-stu-id="26e26-152">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="26e26-153">前一個案例中只會更新以完成百分比表示。</span><span class="sxs-lookup"><span data-stu-id="26e26-153">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="26e26-154">執行程式</span><span class="sxs-lookup"><span data-stu-id="26e26-154">To run the program</span></span>  
  
1.  <span data-ttu-id="26e26-155">按 f5 鍵，將專案放在執行模式。</span><span class="sxs-lookup"><span data-stu-id="26e26-155">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="26e26-156">按一下**開始工作** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="26e26-156">Click the **Start Task** button.</span></span> <span data-ttu-id="26e26-157">每次`PercentDone`就會引發事件，標籤已更新工作已完成的百分比。</span><span class="sxs-lookup"><span data-stu-id="26e26-157">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="26e26-158">按一下**取消**按鈕以停止工作。</span><span class="sxs-lookup"><span data-stu-id="26e26-158">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="26e26-159">請注意，外觀**取消**立即當您按一下按鈕不會變更。</span><span class="sxs-lookup"><span data-stu-id="26e26-159">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="26e26-160">`Click`事件發生之前`My.Application.DoEvents`陳述式可讓事件處理。</span><span class="sxs-lookup"><span data-stu-id="26e26-160">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26e26-161">`My.Application.DoEvents`方法不會處理事件中完全相同的方式與表單。</span><span class="sxs-lookup"><span data-stu-id="26e26-161">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="26e26-162">例如，在此逐步解說中，您必須按一下**取消**按鈕兩次。</span><span class="sxs-lookup"><span data-stu-id="26e26-162">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="26e26-163">若要允許表單以直接處理事件，您可以使用多執行緒處理。</span><span class="sxs-lookup"><span data-stu-id="26e26-163">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="26e26-164">如需詳細資訊，請參閱[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)。</span><span class="sxs-lookup"><span data-stu-id="26e26-164">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="26e26-165">您可能會發現 F11 執行程式並逐步執行程式碼行一次會更有意義。</span><span class="sxs-lookup"><span data-stu-id="26e26-165">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="26e26-166">您可以清楚地查看如何執行輸入`LongTask`，又再簡短重新進入`Form1`每次`PercentDone`就會引發事件。</span><span class="sxs-lookup"><span data-stu-id="26e26-166">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="26e26-167">會發生什麼事如果上一步的程式碼中執行時`Form1`、`LongTask`方法所呼叫一次？</span><span class="sxs-lookup"><span data-stu-id="26e26-167">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="26e26-168">最糟的情況，如果可能會發生堆疊溢位`LongTask`每次引發事件所呼叫。</span><span class="sxs-lookup"><span data-stu-id="26e26-168">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="26e26-169">您可以使變數`mWidget`來處理事件的不同`Widget`藉由指派新的參考物件`Widget`至`mWidget`。</span><span class="sxs-lookup"><span data-stu-id="26e26-169">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="26e26-170">事實上，您可以進行中的程式碼`Button1_Click`每次您按一下按鈕時執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="26e26-170">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="26e26-171">若要處理不同的小工具事件</span><span class="sxs-lookup"><span data-stu-id="26e26-171">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="26e26-172">加入下列一行程式碼`Button1_Click`程序中前讀取的行, `mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="26e26-172">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 <span data-ttu-id="26e26-173">上述程式碼建立新`Widget`每次按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="26e26-173">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="26e26-174">只要`LongTask`方法完成時，若要參考`Widget`已發行，而`Widget`終結。</span><span class="sxs-lookup"><span data-stu-id="26e26-174">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="26e26-175">A`WithEvents`變數可以包含只有一個物件參考一次，因此，如果您可以指派不同`Widget`物件`mWidget`，先前`Widget`將不會再處理物件的事件。</span><span class="sxs-lookup"><span data-stu-id="26e26-175">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="26e26-176">如果`mWidget`是唯一的物件變數包含參考舊`Widget`，就會終結物件。</span><span class="sxs-lookup"><span data-stu-id="26e26-176">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="26e26-177">如果您想要處理事件從幾個`Widget`物件，使用`AddHandler`陳述式來分別處理每個物件中的事件。</span><span class="sxs-lookup"><span data-stu-id="26e26-177">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26e26-178">您可以宣告許多`WithEvents`變數做為您的需要但陣列`WithEvents`不支援變數。</span><span class="sxs-lookup"><span data-stu-id="26e26-178">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e26-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26e26-179">See Also</span></span>  
 [<span data-ttu-id="26e26-180">逐步解說：宣告和引發事件</span><span class="sxs-lookup"><span data-stu-id="26e26-180">Walkthrough: Declaring and Raising Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [<span data-ttu-id="26e26-181">事件</span><span class="sxs-lookup"><span data-stu-id="26e26-181">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
