---
title: 宣告和引發事件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 20e2b0efbf40597049c515134f408927f18d5603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956327"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="5a022-102">逐步解說：宣告和引發事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a022-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="5a022-103">本逐步解說示範如何針對名為`Widget`的類別宣告和引發事件。</span><span class="sxs-lookup"><span data-stu-id="5a022-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="5a022-104">完成這些步驟之後, 您可能會想要閱讀隨附主題[: 逐步解說:處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), 顯示如何使用`Widget`物件中的事件來提供應用程式中的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="5a022-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="5a022-105">Widget 類別</span><span class="sxs-lookup"><span data-stu-id="5a022-105">The Widget Class</span></span>  
 <span data-ttu-id="5a022-106">假設您有一個`Widget`類別。</span><span class="sxs-lookup"><span data-stu-id="5a022-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="5a022-107">您`Widget`的類別具有可能需要很長時間才能執行的方法, 而且您想要讓應用程式能夠放置某種類型的完成指標。</span><span class="sxs-lookup"><span data-stu-id="5a022-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="5a022-108">當然, 您可以讓物件顯示`Widget` [完成百分比] 對話方塊, 但是您會在`Widget`使用類別的每個專案中, 停滯該對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5a022-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="5a022-109">物件設計的一個良好原則是讓使用物件的應用程式處理使用者介面, 除非物件的整個目的是要管理表單或對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5a022-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="5a022-110">的目的`Widget`是要執行其他工作`PercentDone` , 因此最好新增事件, 然後讓呼叫`Widget`的方法處理該事件並顯示狀態更新的程式。</span><span class="sxs-lookup"><span data-stu-id="5a022-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="5a022-111">`PercentDone`事件也可以提供取消工作的機制。</span><span class="sxs-lookup"><span data-stu-id="5a022-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="5a022-112">若要建立本主題的程式碼範例</span><span class="sxs-lookup"><span data-stu-id="5a022-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="5a022-113">開啟新的 Visual Basic Windows 應用程式專案, 並建立名`Form1`為的表單。</span><span class="sxs-lookup"><span data-stu-id="5a022-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="5a022-114">將兩個按鈕和標籤`Form1`新增至。</span><span class="sxs-lookup"><span data-stu-id="5a022-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="5a022-115">依照下表所示的方式，命名物件。</span><span class="sxs-lookup"><span data-stu-id="5a022-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="5a022-116">物件</span><span class="sxs-lookup"><span data-stu-id="5a022-116">Object</span></span>|<span data-ttu-id="5a022-117">屬性</span><span class="sxs-lookup"><span data-stu-id="5a022-117">Property</span></span>|<span data-ttu-id="5a022-118">設定</span><span class="sxs-lookup"><span data-stu-id="5a022-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="5a022-119">啟動工作</span><span class="sxs-lookup"><span data-stu-id="5a022-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="5a022-120">取消</span><span class="sxs-lookup"><span data-stu-id="5a022-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="5a022-121">`(Name)`、 `Text`</span><span class="sxs-lookup"><span data-stu-id="5a022-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="5a022-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="5a022-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="5a022-123">在 [**專案**] 功能表上, 選擇 [**加入類別**], `Widget.vb`將名為的類別新增至專案。</span><span class="sxs-lookup"><span data-stu-id="5a022-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="5a022-124">若要宣告 Widget 類別的事件</span><span class="sxs-lookup"><span data-stu-id="5a022-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="5a022-125">使用關鍵字來宣告`Widget`類別中的事件。 `Event`</span><span class="sxs-lookup"><span data-stu-id="5a022-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="5a022-126">請注意, 事件可以有`ByVal`和`ByRef`引數, `Widget`如`PercentDone`的事件所示:</span><span class="sxs-lookup"><span data-stu-id="5a022-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="5a022-127">當呼叫物件收到`PercentDone`事件時`Percent` , 引數會包含已完成之工作的百分比。</span><span class="sxs-lookup"><span data-stu-id="5a022-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="5a022-128">引數可以設定為`True` , 以取消引發事件的方法。 `Cancel`</span><span class="sxs-lookup"><span data-stu-id="5a022-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a022-129">您可以宣告事件引數, 就如同執行程式的引數一樣, 但有下列例外狀況:事件不能`Optional`有`ParamArray`或引數, 而且事件沒有傳回值。</span><span class="sxs-lookup"><span data-stu-id="5a022-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="5a022-130">事件是`Widget` `LongTask`由類別的方法引發。 `PercentDone`</span><span class="sxs-lookup"><span data-stu-id="5a022-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="5a022-131">`LongTask`採用兩個引數: 方法假裝執行工作的時間長度, 以及暫停之前`LongTask`的最小時間間隔, 以`PercentDone`引發事件。</span><span class="sxs-lookup"><span data-stu-id="5a022-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="5a022-132">若要引發 PercentDone 事件</span><span class="sxs-lookup"><span data-stu-id="5a022-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="5a022-133">若要簡化這個類別`Timer`所使用之屬性的存取權, `Imports`請在`Class Widget`語句上方的類別模組的宣告區段頂端新增語句。</span><span class="sxs-lookup"><span data-stu-id="5a022-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="5a022-134">將下列程式碼加入 `Widget` 類別：</span><span class="sxs-lookup"><span data-stu-id="5a022-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="5a022-135">當您的`Widget`應用程式`LongTask`呼叫方法時, 類別會`PercentDone`每秒`MinimumInterval`引發事件一次。</span><span class="sxs-lookup"><span data-stu-id="5a022-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="5a022-136">當事件傳回時, `LongTask`會檢查`Cancel`是否已將引數設定為`True`。</span><span class="sxs-lookup"><span data-stu-id="5a022-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="5a022-137">這裡有幾個必要的免責聲明。</span><span class="sxs-lookup"><span data-stu-id="5a022-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="5a022-138">為了簡單起見, `LongTask`此程式會假設您事先知道工作會花多少時間。</span><span class="sxs-lookup"><span data-stu-id="5a022-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="5a022-139">幾乎不會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="5a022-139">This is almost never the case.</span></span> <span data-ttu-id="5a022-140">將工作劃分成甚至大小的區塊可能會很難, 而對使用者而言, 最重要的就是在收到某個專案的指示之前傳遞的時間量。</span><span class="sxs-lookup"><span data-stu-id="5a022-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="5a022-141">您可能已在此範例中發現另一個缺陷。</span><span class="sxs-lookup"><span data-stu-id="5a022-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="5a022-142">`Timer`屬性會傳回從午夜開始的秒數; 因此, 如果在午夜之前啟動應用程式, 就會停滯。</span><span class="sxs-lookup"><span data-stu-id="5a022-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="5a022-143">更小心測量時間的方法會將界限條件 (例如這種情況) 納入考慮, 或使用之類的屬性`Now`加以避免。</span><span class="sxs-lookup"><span data-stu-id="5a022-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="5a022-144">現在, 類別可以引發事件, 您可以移至下一個逐步解說。 `Widget`</span><span class="sxs-lookup"><span data-stu-id="5a022-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="5a022-145">[逐步解說：處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)示範如何使用`WithEvents`將事件處理常式與`PercentDone`事件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="5a022-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a022-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a022-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="5a022-147">逐步解說：處理事件</span><span class="sxs-lookup"><span data-stu-id="5a022-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="5a022-148">事件</span><span class="sxs-lookup"><span data-stu-id="5a022-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
