---
title: 宣告和引發事件 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27db585084703607a7389f5a0aa3eba6f70dd793
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="c2850-102">逐步解說：宣告和引發事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2850-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="c2850-103">本逐步解說示範如何宣告和引發事件的類別，名為`Widget`。</span><span class="sxs-lookup"><span data-stu-id="c2850-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="c2850-104">完成步驟之後，您可能想要閱讀附屬主題: <<c0> [ 逐步解說： 處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)，其示範如何使用事件`Widget`來提供應用程式中的狀態資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="c2850-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="c2850-105">Widget 類別</span><span class="sxs-lookup"><span data-stu-id="c2850-105">The Widget Class</span></span>  
 <span data-ttu-id="c2850-106">假設您有目前`Widget`類別。</span><span class="sxs-lookup"><span data-stu-id="c2850-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="c2850-107">您`Widget`類別具有的方法，可能需要很長的時間執行，而且您希望能夠將某種類型的指標完成建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2850-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="c2850-108">當然，您可以進行`Widget`物件顯示完成百分比的對話方塊，但接著您會當機與該對話方塊在您使用每個專案`Widget`類別。</span><span class="sxs-lookup"><span data-stu-id="c2850-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="c2850-109">物件設計好原則就是讓使用的物件控制代碼的使用者介面的應用程式，除非該物件的目的是為了管理表單或對話方塊方塊。</span><span class="sxs-lookup"><span data-stu-id="c2850-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="c2850-110">目的`Widget`是執行其他工作，因此最好是將`PercentDone`事件，然後讓呼叫的程序`Widget`的方法會處理事件和顯示狀態更新。</span><span class="sxs-lookup"><span data-stu-id="c2850-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="c2850-111">`PercentDone`事件也可以提供機制來取消工作。</span><span class="sxs-lookup"><span data-stu-id="c2850-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="c2850-112">若要建立本主題的程式碼範例</span><span class="sxs-lookup"><span data-stu-id="c2850-112">To build the code example for this topic</span></span>  
  
1.  <span data-ttu-id="c2850-113">開啟新的 Visual Basic Windows 應用程式專案，並建立名為表單`Form1`。</span><span class="sxs-lookup"><span data-stu-id="c2850-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="c2850-114">加入兩個按鈕和標籤以`Form1`。</span><span class="sxs-lookup"><span data-stu-id="c2850-114">Add two buttons and a label to `Form1`.</span></span>  
  
3.  <span data-ttu-id="c2850-115">依照下表所示的方式，命名物件。</span><span class="sxs-lookup"><span data-stu-id="c2850-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="c2850-116">物件</span><span class="sxs-lookup"><span data-stu-id="c2850-116">Object</span></span>|<span data-ttu-id="c2850-117">屬性</span><span class="sxs-lookup"><span data-stu-id="c2850-117">Property</span></span>|<span data-ttu-id="c2850-118">設定</span><span class="sxs-lookup"><span data-stu-id="c2850-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="c2850-119">啟動工作</span><span class="sxs-lookup"><span data-stu-id="c2850-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="c2850-120">取消</span><span class="sxs-lookup"><span data-stu-id="c2850-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="c2850-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="c2850-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="c2850-122">lblPercentDone 0</span><span class="sxs-lookup"><span data-stu-id="c2850-122">lblPercentDone, 0</span></span>|  
  
4.  <span data-ttu-id="c2850-123">在**專案**功能表上，選擇**加入類別**將類別命名為`Widget.vb`至專案。</span><span class="sxs-lookup"><span data-stu-id="c2850-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="c2850-124">宣告事件，以供 Widget 類別</span><span class="sxs-lookup"><span data-stu-id="c2850-124">To declare an event for the Widget class</span></span>  
  
-   <span data-ttu-id="c2850-125">使用`Event`關鍵字來宣告中的事件`Widget`類別。</span><span class="sxs-lookup"><span data-stu-id="c2850-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="c2850-126">請注意，事件可以有`ByVal`和`ByRef`引數，做為`Widget`的`PercentDone`事件示範：</span><span class="sxs-lookup"><span data-stu-id="c2850-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 <span data-ttu-id="c2850-127">當呼叫的物件接收`PercentDone`事件，`Percent`引數包含已完成工作的百分比。</span><span class="sxs-lookup"><span data-stu-id="c2850-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="c2850-128">`Cancel`引數可以設定為`True`取消引發事件的方法。</span><span class="sxs-lookup"><span data-stu-id="c2850-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2850-129">您可以宣告事件引數，就像您一樣引數的程序，但有下列例外狀況： 事件不可以有`Optional`或`ParamArray`引數和事件不會有傳回值。</span><span class="sxs-lookup"><span data-stu-id="c2850-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="c2850-130">`PercentDone`就會引發事件`LongTask`方法`Widget`類別。</span><span class="sxs-lookup"><span data-stu-id="c2850-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="c2850-131">`LongTask` 會採用兩個引數： 做的動作 （work) 和之前的最小時間間隔的時間長度方法偽裝`LongTask`引發暫停`PercentDone`事件。</span><span class="sxs-lookup"><span data-stu-id="c2850-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="c2850-132">若要引發 PercentDone 事件</span><span class="sxs-lookup"><span data-stu-id="c2850-132">To raise the PercentDone event</span></span>  
  
1.  <span data-ttu-id="c2850-133">若要簡化存取`Timer`此類別中，所使用的屬性加入`Imports`陳述式加入您的類別模組中的宣告區段頂端上方`Class Widget`陳述式。</span><span class="sxs-lookup"><span data-stu-id="c2850-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  <span data-ttu-id="c2850-134">將下列程式碼加入 `Widget` 類別：</span><span class="sxs-lookup"><span data-stu-id="c2850-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 <span data-ttu-id="c2850-135">當您的應用程式呼叫`LongTask`方法，`Widget`類別所引發`PercentDone`事件每`MinimumInterval`秒。</span><span class="sxs-lookup"><span data-stu-id="c2850-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="c2850-136">事件會傳回`LongTask`檢查`Cancel`引數設定為`True`。</span><span class="sxs-lookup"><span data-stu-id="c2850-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="c2850-137">以下幾個免責聲明是必要的。</span><span class="sxs-lookup"><span data-stu-id="c2850-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="c2850-138">為了簡單起見，`LongTask`程序假設您事先知道工作大約需要多久。</span><span class="sxs-lookup"><span data-stu-id="c2850-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="c2850-139">這幾乎是大小寫。</span><span class="sxs-lookup"><span data-stu-id="c2850-139">This is almost never the case.</span></span> <span data-ttu-id="c2850-140">將工作分割成區塊的大小可能很困難，而且通常最重要的使用者只要他們取得表示項目發生之前，所經過的時間量。</span><span class="sxs-lookup"><span data-stu-id="c2850-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="c2850-141">您可能在此範例中發現其他缺陷。</span><span class="sxs-lookup"><span data-stu-id="c2850-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="c2850-142">`Timer`屬性會傳回自午夜以來已經過的秒數，因此，應用程式時遇如果午夜之前啟動。</span><span class="sxs-lookup"><span data-stu-id="c2850-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="c2850-143">測量時間更謹慎地方法會列入考量，這類的界限條件或避免發生，請使用下列屬性`Now`。</span><span class="sxs-lookup"><span data-stu-id="c2850-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="c2850-144">既然`Widget`類別可以引發事件，您可以移至下一個逐步解說。</span><span class="sxs-lookup"><span data-stu-id="c2850-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="c2850-145">[逐步解說： 處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)示範如何使用`WithEvents`相關聯的事件處理常式和`PercentDone`事件。</span><span class="sxs-lookup"><span data-stu-id="c2850-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2850-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2850-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>  
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>  
 [<span data-ttu-id="c2850-147">逐步解說：處理事件</span><span class="sxs-lookup"><span data-stu-id="c2850-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)  
 [<span data-ttu-id="c2850-148">事件</span><span class="sxs-lookup"><span data-stu-id="c2850-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
