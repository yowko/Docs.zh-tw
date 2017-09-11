---
title: "宣告和引發事件 (Visual Basic) |Microsoft 文件"
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
- declarations, events
- events [Visual Basic], walkthroughs
- declaring events, walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events, walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
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
ms.openlocfilehash: eca112aca39bd998697d379a1705845e8f607367
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="d0744-102">逐步解說：宣告和引發事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0744-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="d0744-103">本逐步解說示範如何宣告和引發事件的類別，名為`Widget`。</span><span class="sxs-lookup"><span data-stu-id="d0744-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="d0744-104">完成的步驟之後，您可能要讀取的系列主題，[逐步解說︰ 處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)，以了解如何使用事件`Widget`來提供應用程式中的狀態資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="d0744-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="d0744-105">Widget 類別</span><span class="sxs-lookup"><span data-stu-id="d0744-105">The Widget Class</span></span>  
 <span data-ttu-id="d0744-106">假設您有時間`Widget`類別。</span><span class="sxs-lookup"><span data-stu-id="d0744-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="d0744-107">您`Widget`類別具有一種方法，可能需要很長的時間執行，以及您希望能夠建立某種類型的指標完成的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d0744-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="d0744-108">當然，您可以建立`Widget`物件顯示完成百分比的對話方塊，但之後您就會停在每個專案中使用該對話方塊`Widget`類別。</span><span class="sxs-lookup"><span data-stu-id="d0744-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="d0744-109">良好的物件設計原則就是讓使用物件控制代碼的使用者介面的應用程式，除非物件的目的就是在管理表單或對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d0744-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="d0744-110">目的`Widget`是執行其他工作，因此最好是將`PercentDone`事件，然後讓呼叫的程序`Widget`的方法會處理事件和顯示狀態更新。</span><span class="sxs-lookup"><span data-stu-id="d0744-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="d0744-111">`PercentDone`事件也可以提供一個機制來取消工作。</span><span class="sxs-lookup"><span data-stu-id="d0744-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="d0744-112">若要建立本主題的程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d0744-112">To build the code example for this topic</span></span>  
  
1.  <span data-ttu-id="d0744-113">開啟新[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows 應用程式專案，並建立名為的表單`Form1`。</span><span class="sxs-lookup"><span data-stu-id="d0744-113">Open a new [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="d0744-114">加入兩個按鈕和標籤`Form1`。</span><span class="sxs-lookup"><span data-stu-id="d0744-114">Add two buttons and a label to `Form1`.</span></span>  
  
3.  <span data-ttu-id="d0744-115">下表所示，為物件命名。</span><span class="sxs-lookup"><span data-stu-id="d0744-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="d0744-116">物件</span><span class="sxs-lookup"><span data-stu-id="d0744-116">Object</span></span>|<span data-ttu-id="d0744-117">屬性</span><span class="sxs-lookup"><span data-stu-id="d0744-117">Property</span></span>|<span data-ttu-id="d0744-118">設定</span><span class="sxs-lookup"><span data-stu-id="d0744-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="d0744-119">啟動工作</span><span class="sxs-lookup"><span data-stu-id="d0744-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="d0744-120">取消</span><span class="sxs-lookup"><span data-stu-id="d0744-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="d0744-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="d0744-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="d0744-122">lblPercentDone 0</span><span class="sxs-lookup"><span data-stu-id="d0744-122">lblPercentDone, 0</span></span>|  
  
4.  <span data-ttu-id="d0744-123">在**專案** 功能表上，選擇**加入類別**加入類別，名為`Widget.vb`至專案。</span><span class="sxs-lookup"><span data-stu-id="d0744-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="d0744-124">若要宣告事件，以供 Widget 類別</span><span class="sxs-lookup"><span data-stu-id="d0744-124">To declare an event for the Widget class</span></span>  
  
-   <span data-ttu-id="d0744-125">使用`Event`關鍵字來宣告中的事件`Widget`類別。</span><span class="sxs-lookup"><span data-stu-id="d0744-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="d0744-126">請注意，事件可以有`ByVal`和`ByRef`引數，做為`Widget`的`PercentDone`事件示範︰</span><span class="sxs-lookup"><span data-stu-id="d0744-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     <span data-ttu-id="d0744-127">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&1;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d0744-127">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]</span></span>  
  
 <span data-ttu-id="d0744-128">當呼叫物件收到`PercentDone`事件`Percent`引數包含已完成工作的百分比。</span><span class="sxs-lookup"><span data-stu-id="d0744-128">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="d0744-129">`Cancel`引數可以設定為`True`取消引發事件的方法。</span><span class="sxs-lookup"><span data-stu-id="d0744-129">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0744-130">您可以宣告事件引數，就如同引數的程序，但有下列例外狀況︰ 事件不可以有`Optional`或`ParamArray`引數，以及事件不會有傳回值。</span><span class="sxs-lookup"><span data-stu-id="d0744-130">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="d0744-131">`PercentDone`引發事件`LongTask`方法`Widget`類別。</span><span class="sxs-lookup"><span data-stu-id="d0744-131">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="d0744-132">`LongTask`會採用兩個引數︰ 工作 （work) 和之前的最小時間間隔的時間長度方法偽裝`LongTask`暫停引發`PercentDone`事件。</span><span class="sxs-lookup"><span data-stu-id="d0744-132">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="d0744-133">若要引發 PercentDone 事件</span><span class="sxs-lookup"><span data-stu-id="d0744-133">To raise the PercentDone event</span></span>  
  
1.  <span data-ttu-id="d0744-134">若要簡化對存取`Timer`這個類別所使用的屬性加入`Imports`陳述式的類別模組中，「 宣告 」 區段頂端上方`Class Widget`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d0744-134">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     <span data-ttu-id="d0744-135">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&2;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d0744-135">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]</span></span>  
  
2.  <span data-ttu-id="d0744-136">將下列程式碼加入 `Widget` 類別：</span><span class="sxs-lookup"><span data-stu-id="d0744-136">Add the following code to the `Widget` class:</span></span>  
  
     <span data-ttu-id="d0744-137">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&3;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d0744-137">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]</span></span>  
  
 <span data-ttu-id="d0744-138">當您的應用程式呼叫`LongTask`方法，`Widget`類別會引發`PercentDone`事件每`MinimumInterval`秒。</span><span class="sxs-lookup"><span data-stu-id="d0744-138">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="d0744-139">此事件會傳回`LongTask`檢查，看看是否`Cancel`引數設為`True`。</span><span class="sxs-lookup"><span data-stu-id="d0744-139">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="d0744-140">以下幾個免責聲明是必要的。</span><span class="sxs-lookup"><span data-stu-id="d0744-140">A few disclaimers are necessary here.</span></span> <span data-ttu-id="d0744-141">為了簡單起見，`LongTask`程序假設您事先知道工作將會花多少時間。</span><span class="sxs-lookup"><span data-stu-id="d0744-141">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="d0744-142">這通常不是如此。</span><span class="sxs-lookup"><span data-stu-id="d0744-142">This is almost never the case.</span></span> <span data-ttu-id="d0744-143">工作分割成多個區塊的大小可能很困難，而且通常最重要的使用者所取得表示項目發生之前經過的時間量。</span><span class="sxs-lookup"><span data-stu-id="d0744-143">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="d0744-144">您可以在此範例中發現另一個缺點。</span><span class="sxs-lookup"><span data-stu-id="d0744-144">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="d0744-145">`Timer`屬性會傳回從午夜的秒數，因此，應用程式一直顯示如果午夜之前啟動。</span><span class="sxs-lookup"><span data-stu-id="d0744-145">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="d0744-146">以更仔細的方法來測量時間會列入考量，這類的界限條件或完全避免使用它們，例如使用屬性`Now`。</span><span class="sxs-lookup"><span data-stu-id="d0744-146">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="d0744-147">既然`Widget`類別可以引發事件，您可以移至下一個逐步解說。</span><span class="sxs-lookup"><span data-stu-id="d0744-147">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="d0744-148">[逐步解說︰ 處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)示範如何使用`WithEvents`與事件處理常式關聯`PercentDone`事件。</span><span class="sxs-lookup"><span data-stu-id="d0744-148">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0744-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0744-149">See Also</span></span>  
 <span data-ttu-id="d0744-150"><xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></span><span class="sxs-lookup"><span data-stu-id="d0744-150"><xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></span></span>   
 <span data-ttu-id="d0744-151"><xref:Microsoft.VisualBasic.DateAndTime.Now%2A></xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span><span class="sxs-lookup"><span data-stu-id="d0744-151"><xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span></span>   
<span data-ttu-id="d0744-152"> [逐步解說︰ 處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) </span><span class="sxs-lookup"><span data-stu-id="d0744-152"> [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) </span></span>  
<span data-ttu-id="d0744-153"> [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="d0744-153"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
