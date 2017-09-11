---
title: "處理事件 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword, walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b4ad77b3b0236e762fc17b8aba9d34108c8d75b5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="c4188-102">逐步解說：處理事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4188-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="c4188-103">這是示範如何使用事件的兩個主題的第二個。</span><span class="sxs-lookup"><span data-stu-id="c4188-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="c4188-104">第一個主題，[逐步解說︰ 宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)，示範如何宣告和引發事件。</span><span class="sxs-lookup"><span data-stu-id="c4188-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="c4188-105">本節會使用表單和類別，從該逐步解說顯示如何處理事件發生時它們。</span><span class="sxs-lookup"><span data-stu-id="c4188-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="c4188-106">`Widget`類別範例會使用傳統的事件處理陳述式。</span><span class="sxs-lookup"><span data-stu-id="c4188-106">The `Widget` class example uses traditional event-handling statements.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="c4188-107">提供處理事件的其他技術。</span><span class="sxs-lookup"><span data-stu-id="c4188-107"> provides other techniques for working with events.</span></span> <span data-ttu-id="c4188-108">做為練習，您可以修改此範例中使用`AddHandler`和`Handles`陳述式。</span><span class="sxs-lookup"><span data-stu-id="c4188-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="c4188-109">要處理的 Widget 類別 PercentDone 事件</span><span class="sxs-lookup"><span data-stu-id="c4188-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="c4188-110">將下列程式碼中的`Form1`:</span><span class="sxs-lookup"><span data-stu-id="c4188-110">Place the following code in `Form1`:</span></span>  
  
     <span data-ttu-id="c4188-111">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&4;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4188-111">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]</span></span>  
  
     <span data-ttu-id="c4188-112">`WithEvents`關鍵字指定變數`mWidget`用來處理物件的事件。</span><span class="sxs-lookup"><span data-stu-id="c4188-112">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="c4188-113">您可以提供的類別建立物件的名稱指定物件的類型。</span><span class="sxs-lookup"><span data-stu-id="c4188-113">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="c4188-114">變數`mWidget`中宣告`Form1`因為`WithEvents`變數必須是類別層級。</span><span class="sxs-lookup"><span data-stu-id="c4188-114">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="c4188-115">這是不論您置入類別的型別，則為 true。</span><span class="sxs-lookup"><span data-stu-id="c4188-115">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="c4188-116">變數`mblnCancel`用來取消`LongTask`方法。</span><span class="sxs-lookup"><span data-stu-id="c4188-116">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="c4188-117">撰寫程式碼來處理事件</span><span class="sxs-lookup"><span data-stu-id="c4188-117">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="c4188-118">當您宣告變數使用`WithEvents`，變數的名稱會出現在左邊的下拉式清單，此類別的**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="c4188-118">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="c4188-119">當您選取`mWidget`、`Widget`類別的事件會出現在右邊下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="c4188-119">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="c4188-120">選取事件會顯示對應的事件程序，具有前置詞`mWidget`和底線。</span><span class="sxs-lookup"><span data-stu-id="c4188-120">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="c4188-121">相關聯的事件程序`WithEvents`變數指定變數的名稱，做為前置詞。</span><span class="sxs-lookup"><span data-stu-id="c4188-121">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="c4188-122">若要處理的事件</span><span class="sxs-lookup"><span data-stu-id="c4188-122">To handle an event</span></span>  
  
1.  <span data-ttu-id="c4188-123">選取`mWidget`從左邊的下拉式清單中**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="c4188-123">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="c4188-124">選取`PercentDone`右邊下拉式清單中的事件。</span><span class="sxs-lookup"><span data-stu-id="c4188-124">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="c4188-125">**程式碼編輯器**開啟`mWidget_PercentDone`事件程序。</span><span class="sxs-lookup"><span data-stu-id="c4188-125">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c4188-126">**程式碼編輯器**很有用，但非必要，適用於插入新的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c4188-126">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="c4188-127">在本逐步解說中，它是更為直接的方式只是事件處理常式將直接複製到您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c4188-127">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="c4188-128">將下列程式碼加入至 `mWidget_PercentDone` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="c4188-128">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     <span data-ttu-id="c4188-129">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&5;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4188-129">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]</span></span>  
  
     <span data-ttu-id="c4188-130">每當`PercentDone`就會引發事件時，事件程序會顯示在完成百分比`Label`控制項。</span><span class="sxs-lookup"><span data-stu-id="c4188-130">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="c4188-131">`DoEvents`方法可讓重新繪製標籤，並也讓使用者按一下**取消** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4188-131">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="c4188-132">加入下列程式碼`Button2_Click`事件處理常式︰</span><span class="sxs-lookup"><span data-stu-id="c4188-132">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     <span data-ttu-id="c4188-133">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&6;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4188-133">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]</span></span>  
  
 <span data-ttu-id="c4188-134">如果使用者按一下**取消**按鈕時`LongTask`正在執行，`Button2_Click`事件執行儘速`DoEvents`陳述式允許發生的事件處理。</span><span class="sxs-lookup"><span data-stu-id="c4188-134">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="c4188-135">類別層級變數`mblnCancel`設為`True`，而`mWidget_PercentDone`事件然後進行測試，並將`ByRef Cancel`引數`True`。</span><span class="sxs-lookup"><span data-stu-id="c4188-135">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="c4188-136">連接 WithEvents 變數的物件</span><span class="sxs-lookup"><span data-stu-id="c4188-136">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="c4188-137">`Form1`現在來處理設定`Widget`物件的事件。</span><span class="sxs-lookup"><span data-stu-id="c4188-137">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="c4188-138">剩下的就尋找是`Widget`某處。</span><span class="sxs-lookup"><span data-stu-id="c4188-138">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="c4188-139">當您宣告變數`WithEvents`在設計階段沒有物件則有與其相關聯。</span><span class="sxs-lookup"><span data-stu-id="c4188-139">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="c4188-140">A`WithEvents`變數，就如同任何其他物件的變數。</span><span class="sxs-lookup"><span data-stu-id="c4188-140">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="c4188-141">您必須建立物件，並指定它的參考`WithEvents`變數。</span><span class="sxs-lookup"><span data-stu-id="c4188-141">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="c4188-142">建立物件，並指派給它的參考</span><span class="sxs-lookup"><span data-stu-id="c4188-142">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="c4188-143">選取**（Form1 事件）**從左邊的下拉式清單中**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="c4188-143">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="c4188-144">選取`Load`右邊下拉式清單中的事件。</span><span class="sxs-lookup"><span data-stu-id="c4188-144">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="c4188-145">**程式碼編輯器**開啟`Form1_Load`事件程序。</span><span class="sxs-lookup"><span data-stu-id="c4188-145">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="c4188-146">加入下列程式碼`Form1_Load`建立的事件程序`Widget`:</span><span class="sxs-lookup"><span data-stu-id="c4188-146">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     <span data-ttu-id="c4188-147">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&7;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4188-147">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]</span></span>  
  
 <span data-ttu-id="c4188-148">此程式碼執行時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]建立`Widget`物件，並連接事件相關聯的事件程序`mWidget`。</span><span class="sxs-lookup"><span data-stu-id="c4188-148">When this code executes, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="c4188-149">從該點上，每當`Widget`引發其`PercentDone`事件`mWidget_PercentDone`執行事件程序。</span><span class="sxs-lookup"><span data-stu-id="c4188-149">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="c4188-150">若要呼叫 LongTask 方法</span><span class="sxs-lookup"><span data-stu-id="c4188-150">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="c4188-151">將下列程式碼加入至 `Button1_Click` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="c4188-151">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     <span data-ttu-id="c4188-152">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&8;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4188-152">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]</span></span>  
  
 <span data-ttu-id="c4188-153">之前`LongTask`呼叫方法時，標籤，必須先初始化完成的百分比顯示，並在類別層級`Boolean`旗標的取消方法必須設為`False`。</span><span class="sxs-lookup"><span data-stu-id="c4188-153">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="c4188-154">`LongTask`稱為工作持續時間為 12.2 的秒數。</span><span class="sxs-lookup"><span data-stu-id="c4188-154">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="c4188-155">`PercentDone`事件引發一次每三分之一的第二個。</span><span class="sxs-lookup"><span data-stu-id="c4188-155">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="c4188-156">引發事件時，每次`mWidget_PercentDone`執行事件程序。</span><span class="sxs-lookup"><span data-stu-id="c4188-156">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="c4188-157">當`LongTask`完畢後，`mblnCancel`測試是否`LongTask`結束一般來說，或如果它停止，因為`mblnCancel`設為`True`。</span><span class="sxs-lookup"><span data-stu-id="c4188-157">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="c4188-158">前一個案例中只會更新以完成百分比表示。</span><span class="sxs-lookup"><span data-stu-id="c4188-158">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="c4188-159">執行程式</span><span class="sxs-lookup"><span data-stu-id="c4188-159">To run the program</span></span>  
  
1.  <span data-ttu-id="c4188-160">按 f5 鍵，將專案放置在執行模式。</span><span class="sxs-lookup"><span data-stu-id="c4188-160">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="c4188-161">按一下 [**開始工作**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4188-161">Click the **Start Task** button.</span></span> <span data-ttu-id="c4188-162">每次`PercentDone`就會引發事件，標籤會更新已完成工作的百分比。</span><span class="sxs-lookup"><span data-stu-id="c4188-162">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="c4188-163">按一下 [**取消**] 按鈕以停止工作。</span><span class="sxs-lookup"><span data-stu-id="c4188-163">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="c4188-164">請注意，外觀**取消**按鈕不會變更，請立即按一下它。</span><span class="sxs-lookup"><span data-stu-id="c4188-164">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="c4188-165">`Click`事件不會發生直到`My.Application.DoEvents`陳述式可讓事件處理。</span><span class="sxs-lookup"><span data-stu-id="c4188-165">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c4188-166">`My.Application.DoEvents`方法不會處理事件的相同方式表單一樣。</span><span class="sxs-lookup"><span data-stu-id="c4188-166">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="c4188-167">例如，在此逐步解說中，您必須按一下**取消**按鈕兩次。</span><span class="sxs-lookup"><span data-stu-id="c4188-167">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="c4188-168">若要讓表單直接處理事件，您可以使用多執行緒處理。</span><span class="sxs-lookup"><span data-stu-id="c4188-168">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="c4188-169">如需詳細資訊，請參閱[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)。</span><span class="sxs-lookup"><span data-stu-id="c4188-169">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="c4188-170">您可能會發現使用 F11 執行程式，並逐步執行程式碼行一次會更有意義。</span><span class="sxs-lookup"><span data-stu-id="c4188-170">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="c4188-171">您可以清楚看到如何執行進入`LongTask`，又再簡短重新進入`Form1`每次`PercentDone`就會引發事件。</span><span class="sxs-lookup"><span data-stu-id="c4188-171">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="c4188-172">會發生什麼事如果上一步中的程式碼執行時`Form1`、`LongTask`再次呼叫方法？</span><span class="sxs-lookup"><span data-stu-id="c4188-172">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="c4188-173">最糟的情況，如果可能會發生堆疊溢位`LongTask`每次引發事件所呼叫。</span><span class="sxs-lookup"><span data-stu-id="c4188-173">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="c4188-174">您可以使變數`mWidget`來處理事件的不同`Widget`物件的參考指派給新`Widget`到`mWidget`。</span><span class="sxs-lookup"><span data-stu-id="c4188-174">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="c4188-175">事實上，您可以進行中的程式碼`Button1_Click`每次您按一下按鈕，執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="c4188-175">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="c4188-176">若要處理不同的 widget 的事件</span><span class="sxs-lookup"><span data-stu-id="c4188-176">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="c4188-177">加入下列這一行程式碼`Button1_Click`程序，那一行的前置`mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="c4188-177">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     <span data-ttu-id="c4188-178">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&9;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4188-178">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]</span></span>  
  
 <span data-ttu-id="c4188-179">上述程式碼會建立新`Widget`每次按一下按鈕時。</span><span class="sxs-lookup"><span data-stu-id="c4188-179">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="c4188-180">只要`LongTask`方法完成時，若要參考`Widget`已釋放，而`Widget`終結。</span><span class="sxs-lookup"><span data-stu-id="c4188-180">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="c4188-181">A`WithEvents`變數可以包含只有一個物件參考一次，因此，如果您可以指派不同`Widget`物件傳遞給`mWidget`，先前`Widget`將不會再處理物件的事件。</span><span class="sxs-lookup"><span data-stu-id="c4188-181">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="c4188-182">如果`mWidget`是唯一的物件變數包含參考舊`Widget`，終結物件。</span><span class="sxs-lookup"><span data-stu-id="c4188-182">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="c4188-183">如果您想要處理來自數個事件`Widget`物件，使用`AddHandler`陳述式來個別處理每個物件的事件。</span><span class="sxs-lookup"><span data-stu-id="c4188-183">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4188-184">您可以宣告為許多`WithEvents`變數做為您的需要但陣列`WithEvents`不支援變數。</span><span class="sxs-lookup"><span data-stu-id="c4188-184">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4188-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4188-185">See Also</span></span>  
 <span data-ttu-id="c4188-186">[逐步解說︰ 宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md) </span><span class="sxs-lookup"><span data-stu-id="c4188-186">[Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md) </span></span>  
<span data-ttu-id="c4188-187"> [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="c4188-187"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
