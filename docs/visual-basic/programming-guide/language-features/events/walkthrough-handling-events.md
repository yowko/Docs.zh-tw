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
ms.openlocfilehash: 12267e0a70419298bc581421c4f3a220088d205f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956304"
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="bb519-102">逐步解說：處理事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb519-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="bb519-103">這是示範如何處理事件的兩個主題的第二個。</span><span class="sxs-lookup"><span data-stu-id="bb519-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="bb519-104">第一個主題, [逐步解說:宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)會顯示如何宣告和引發事件。</span><span class="sxs-lookup"><span data-stu-id="bb519-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="bb519-105">本節使用該逐步解說中的表單和類別, 以示範如何在事件發生時加以處理。</span><span class="sxs-lookup"><span data-stu-id="bb519-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="bb519-106">`Widget`類別範例會使用傳統的事件處理語句。</span><span class="sxs-lookup"><span data-stu-id="bb519-106">The `Widget` class example uses traditional event-handling statements.</span></span> <span data-ttu-id="bb519-107">Visual Basic 提供處理事件的其他技術。</span><span class="sxs-lookup"><span data-stu-id="bb519-107">Visual Basic provides other techniques for working with events.</span></span> <span data-ttu-id="bb519-108">在練習中, 您可以修改此範例以使用`AddHandler`和`Handles`語句。</span><span class="sxs-lookup"><span data-stu-id="bb519-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="bb519-109">若要處理 Widget 類別的 PercentDone 事件</span><span class="sxs-lookup"><span data-stu-id="bb519-109">To handle the PercentDone event of the Widget class</span></span>  
  
1. <span data-ttu-id="bb519-110">將下列程式碼放`Form1`入:</span><span class="sxs-lookup"><span data-stu-id="bb519-110">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     <span data-ttu-id="bb519-111">關鍵字會指定使用變數`mWidget`來處理物件的事件。 `WithEvents`</span><span class="sxs-lookup"><span data-stu-id="bb519-111">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="bb519-112">您可以藉由提供要從中建立物件之類別的名稱, 來指定物件的種類。</span><span class="sxs-lookup"><span data-stu-id="bb519-112">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="bb519-113">變數`mWidget`會在中`Form1`宣告, `WithEvents`因為變數必須是類別層級。</span><span class="sxs-lookup"><span data-stu-id="bb519-113">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="bb519-114">無論您將它們放置在哪一種類別, 都是如此。</span><span class="sxs-lookup"><span data-stu-id="bb519-114">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="bb519-115">變數`mblnCancel`是用來`LongTask`取消方法。</span><span class="sxs-lookup"><span data-stu-id="bb519-115">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="bb519-116">撰寫程式碼來處理事件</span><span class="sxs-lookup"><span data-stu-id="bb519-116">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="bb519-117">一旦您使用`WithEvents`來宣告變數, 變數名稱就會出現在類別程式**代碼編輯器**的左側下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="bb519-117">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="bb519-118">當您選取`mWidget`時`Widget` , 類別的事件會顯示在右邊的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="bb519-118">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="bb519-119">選取事件會顯示對應的事件程式, 並加上`mWidget`前置詞和底線。</span><span class="sxs-lookup"><span data-stu-id="bb519-119">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="bb519-120">與`WithEvents`變數相關聯的所有事件程式都會被指定變數名稱做為前置詞。</span><span class="sxs-lookup"><span data-stu-id="bb519-120">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="bb519-121">若要處理事件</span><span class="sxs-lookup"><span data-stu-id="bb519-121">To handle an event</span></span>  
  
1. <span data-ttu-id="bb519-122">從`mWidget` [程式**代碼編輯器**] 的左側下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="bb519-122">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2. <span data-ttu-id="bb519-123">從右邊的下拉式清單中選取事件。`PercentDone`</span><span class="sxs-lookup"><span data-stu-id="bb519-123">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="bb519-124">[程式**代碼編輯器**] `mWidget_PercentDone`會開啟事件程式。</span><span class="sxs-lookup"><span data-stu-id="bb519-124">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bb519-125">[程式**代碼編輯器**] 在插入新的事件處理常式時很有用, 但並不是必要的。</span><span class="sxs-lookup"><span data-stu-id="bb519-125">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="bb519-126">在本逐步解說中, 您可以直接將事件處理常式直接複製到程式碼中。</span><span class="sxs-lookup"><span data-stu-id="bb519-126">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3. <span data-ttu-id="bb519-127">將下列程式碼加入至 `mWidget_PercentDone` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="bb519-127">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     <span data-ttu-id="bb519-128">每當引發`Label`事件時, 事件程式就會在控制項中顯示完成百分比。 `PercentDone`</span><span class="sxs-lookup"><span data-stu-id="bb519-128">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="bb519-129">方法允許重新繪製標籤, 也會讓使用者有機會按一下 [取消] 按鈕。 `DoEvents`</span><span class="sxs-lookup"><span data-stu-id="bb519-129">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="bb519-130">為`Button2_Click`事件處理常式新增下列程式碼:</span><span class="sxs-lookup"><span data-stu-id="bb519-130">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 <span data-ttu-id="bb519-131">如果使用者在執行時 `LongTask`按一下 [取消] 按鈕, `Button2_Click`當`DoEvents`語句允許事件處理發生時, 就會立即執行事件。</span><span class="sxs-lookup"><span data-stu-id="bb519-131">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="bb519-132">類別層`mblnCancel`級變數會設定為`True`, `mWidget_PercentDone`然後事件會進行測試, 並將`ByRef Cancel`引數設定為`True`。</span><span class="sxs-lookup"><span data-stu-id="bb519-132">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="bb519-133">將 WithEvents 變數連接至物件</span><span class="sxs-lookup"><span data-stu-id="bb519-133">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="bb519-134">`Form1`現在已設定為可處理`Widget`物件的事件。</span><span class="sxs-lookup"><span data-stu-id="bb519-134">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="bb519-135">剩下的就是尋找一個`Widget`地方。</span><span class="sxs-lookup"><span data-stu-id="bb519-135">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="bb519-136">當您在設計階段`WithEvents`宣告變數時, 不會有任何物件與其相關聯。</span><span class="sxs-lookup"><span data-stu-id="bb519-136">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="bb519-137">`WithEvents`變數就像任何其他物件變數一樣。</span><span class="sxs-lookup"><span data-stu-id="bb519-137">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="bb519-138">您必須建立物件, 並使用`WithEvents`變數來指派它的參考。</span><span class="sxs-lookup"><span data-stu-id="bb519-138">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="bb519-139">建立物件並指派其參考</span><span class="sxs-lookup"><span data-stu-id="bb519-139">To create an object and assign a reference to it</span></span>  
  
1. <span data-ttu-id="bb519-140">從 [程式**代碼編輯器**] 的左側下拉式清單中, 選取 [ **(Form1 事件)** ]。</span><span class="sxs-lookup"><span data-stu-id="bb519-140">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2. <span data-ttu-id="bb519-141">從右邊的下拉式清單中選取事件。`Load`</span><span class="sxs-lookup"><span data-stu-id="bb519-141">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="bb519-142">[程式**代碼編輯器**] `Form1_Load`會開啟事件程式。</span><span class="sxs-lookup"><span data-stu-id="bb519-142">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3. <span data-ttu-id="bb519-143">新增下列程式碼, 以`Form1_Load`供事件程式`Widget`建立:</span><span class="sxs-lookup"><span data-stu-id="bb519-143">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 <span data-ttu-id="bb519-144">當此程式碼執行時, Visual Basic `Widget`會建立物件, 並將其事件連接至與`mWidget`相關聯的事件程式。</span><span class="sxs-lookup"><span data-stu-id="bb519-144">When this code executes, Visual Basic creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="bb519-145">從該時間點開始, 每當`Widget`引發其`PercentDone`事件時, `mWidget_PercentDone`就會執行事件程式。</span><span class="sxs-lookup"><span data-stu-id="bb519-145">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="bb519-146">呼叫 LongTask 方法</span><span class="sxs-lookup"><span data-stu-id="bb519-146">To call the LongTask method</span></span>  
  
- <span data-ttu-id="bb519-147">將下列程式碼加入至 `Button1_Click` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="bb519-147">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 <span data-ttu-id="bb519-148">在呼叫`Boolean` `False`方法之前, 必須先初始化顯示完成百分比的標籤, 而且取消方法的類別層級旗標必須設定為。 `LongTask`</span><span class="sxs-lookup"><span data-stu-id="bb519-148">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="bb519-149">`LongTask`呼叫的工作持續時間為12.2 秒。</span><span class="sxs-lookup"><span data-stu-id="bb519-149">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="bb519-150">`PercentDone`事件每隔一秒引發一次。</span><span class="sxs-lookup"><span data-stu-id="bb519-150">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="bb519-151">每次引發事件時, `mWidget_PercentDone`就會執行事件程式。</span><span class="sxs-lookup"><span data-stu-id="bb519-151">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="bb519-152">完成`LongTask`時, `mblnCancel`會測試以查看是否`LongTask`正常結束, 或是否因為`mblnCancel`已設定為`True`而停止。</span><span class="sxs-lookup"><span data-stu-id="bb519-152">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="bb519-153">完成的百分比只會在先前的情況下更新。</span><span class="sxs-lookup"><span data-stu-id="bb519-153">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="bb519-154">執行程式</span><span class="sxs-lookup"><span data-stu-id="bb519-154">To run the program</span></span>  
  
1. <span data-ttu-id="bb519-155">按 F5 將專案置於執行模式。</span><span class="sxs-lookup"><span data-stu-id="bb519-155">Press F5 to put the project in run mode.</span></span>  
  
2. <span data-ttu-id="bb519-156">按一下 [**啟動**工作] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bb519-156">Click the **Start Task** button.</span></span> <span data-ttu-id="bb519-157">每次`PercentDone`引發事件時, 就會以完成工作的百分比來更新標籤。</span><span class="sxs-lookup"><span data-stu-id="bb519-157">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3. <span data-ttu-id="bb519-158">按一下 [**取消**] 按鈕以停止工作。</span><span class="sxs-lookup"><span data-stu-id="bb519-158">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="bb519-159">請注意, 當您按一下 [**取消**] 按鈕時, 其外觀不會立即變更。</span><span class="sxs-lookup"><span data-stu-id="bb519-159">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="bb519-160">直到語句允許事件處理時, 才會發生此`Click`事件。 `My.Application.DoEvents`</span><span class="sxs-lookup"><span data-stu-id="bb519-160">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bb519-161">`My.Application.DoEvents`方法不會以與表單相同的方式來處理事件。</span><span class="sxs-lookup"><span data-stu-id="bb519-161">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="bb519-162">例如, 在此逐步解說中, 您必須按兩次 [**取消**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bb519-162">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="bb519-163">若要允許表單直接處理事件, 您可以使用多執行緒。</span><span class="sxs-lookup"><span data-stu-id="bb519-163">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="bb519-164">如需詳細資訊, 請參閱[Managed 執行緒](../../../../standard/threading/index.md)。</span><span class="sxs-lookup"><span data-stu-id="bb519-164">For more information, see [Managed Threading](../../../../standard/threading/index.md).</span></span>
  
 <span data-ttu-id="bb519-165">您可能會發現使用 F11 來執行程式, 以及一次逐步執行一行程式碼, 會有其意義。</span><span class="sxs-lookup"><span data-stu-id="bb519-165">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="bb519-166">您可以清楚地看到執行如何`LongTask`進入, 然後在`PercentDone`每次引發`Form1`事件時短暫重新進入。</span><span class="sxs-lookup"><span data-stu-id="bb519-166">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="bb519-167">如果在的程式碼`Form1`中執行時`LongTask` , 會發生什麼情況, 再次呼叫方法？</span><span class="sxs-lookup"><span data-stu-id="bb519-167">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="bb519-168">在最糟的情況下, 如果`LongTask`在每次引發事件時呼叫, 則可能會發生堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="bb519-168">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="bb519-169">您可以藉由將`mWidget`新`Widget`的`mWidget`參考指派給, `Widget`讓變數處理不同物件的事件。</span><span class="sxs-lookup"><span data-stu-id="bb519-169">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="bb519-170">事實上, 您可以在`Button1_Click`每次按一下按鈕時, 讓程式碼執行此動作。</span><span class="sxs-lookup"><span data-stu-id="bb519-170">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="bb519-171">處理不同 widget 的事件</span><span class="sxs-lookup"><span data-stu-id="bb519-171">To handle events for a different widget</span></span>  
  
- <span data-ttu-id="bb519-172">將下列程式程式碼新增至`Button1_Click`程式, 緊接在讀取`mWidget.LongTask(12.2, 0.33)`的那一行前面:</span><span class="sxs-lookup"><span data-stu-id="bb519-172">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 <span data-ttu-id="bb519-173">上述程式碼會在每`Widget`次按一下按鈕時建立新的。</span><span class="sxs-lookup"><span data-stu-id="bb519-173">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="bb519-174">一旦方法完成, 就`Widget` `Widget`會釋放的參考, 並終結。 `LongTask`</span><span class="sxs-lookup"><span data-stu-id="bb519-174">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="bb519-175">一個變數一次只能包含一個物件參考, 因此, 如果您將不同`Widget`的物件指派給`mWidget`, 就不`Widget`會再處理上一個物件的事件。 `WithEvents`</span><span class="sxs-lookup"><span data-stu-id="bb519-175">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="bb519-176">如果`mWidget`是唯一包含舊`Widget`的參考的物件變數, 則會終結物件。</span><span class="sxs-lookup"><span data-stu-id="bb519-176">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="bb519-177">如果您想要處理來自數個`Widget`物件的事件, `AddHandler`請使用語句, 分別處理每個物件的事件。</span><span class="sxs-lookup"><span data-stu-id="bb519-177">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb519-178">您可以視需要宣告`WithEvents`多個變數, 但不支援`WithEvents`變數陣列。</span><span class="sxs-lookup"><span data-stu-id="bb519-178">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb519-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb519-179">See also</span></span>

- [<span data-ttu-id="bb519-180">逐步解說：宣告和引發事件</span><span class="sxs-lookup"><span data-stu-id="bb519-180">Walkthrough: Declaring and Raising Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [<span data-ttu-id="bb519-181">事件</span><span class="sxs-lookup"><span data-stu-id="bb519-181">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
