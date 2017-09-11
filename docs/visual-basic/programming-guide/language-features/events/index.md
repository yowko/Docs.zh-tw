---
title: "事件 (Visual Basic)"
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
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
caps.latest.revision: 12
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 84f8385e1b2f16c4bcfa53ef2c77e1f0cf61e5e3
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="events-visual-basic"></a><span data-ttu-id="73998-102">事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73998-102">Events (Visual Basic)</span></span>
<span data-ttu-id="73998-103">雖然您可以視覺化方式將 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 專案顯示為一系列依序執行的程序，但實際上，大部分程式都是事件驅動的，亦即執行的流程是由稱為「事件」的外部發生項目所判斷。</span><span class="sxs-lookup"><span data-stu-id="73998-103">While you might visualize a [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] project as a series of procedures that execute in a sequence, in reality, most programs are event driven—meaning the flow of execution is determined by external occurrences called *events*.</span></span>  
  
 <span data-ttu-id="73998-104">事件是通知應用程式發生重要事件的信號。</span><span class="sxs-lookup"><span data-stu-id="73998-104">An event is a signal that informs an application that something important has occurred.</span></span> <span data-ttu-id="73998-105">例如，當使用者按一下表單上的控制項時，表單可以引發 `Click` 事件，並呼叫處理事件的程序。</span><span class="sxs-lookup"><span data-stu-id="73998-105">For example, when a user clicks a control on a form, the form can raise a `Click` event and call a procedure that handles the event.</span></span> <span data-ttu-id="73998-106">事件也允許個別工作進行通訊。</span><span class="sxs-lookup"><span data-stu-id="73998-106">Events also allow separate tasks to communicate.</span></span> <span data-ttu-id="73998-107">例如，假設您的應用程式與主應用程式個別執行排序工作。</span><span class="sxs-lookup"><span data-stu-id="73998-107">Say, for example, that your application performs a sort task separately from the main application.</span></span> <span data-ttu-id="73998-108">如果使用者取消排序，則您的應用程式可以傳送取消事件，以指示排序處理序停止。</span><span class="sxs-lookup"><span data-stu-id="73998-108">If a user cancels the sort, your application can send a cancel event instructing the sort process to stop.</span></span>  
  
## <a name="event-terms-and-concepts"></a><span data-ttu-id="73998-109">事件詞彙和概念</span><span class="sxs-lookup"><span data-stu-id="73998-109">Event Terms and Concepts</span></span>  
 <span data-ttu-id="73998-110">本節描述的詞彙和概念可與 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 中的事件搭配使用。</span><span class="sxs-lookup"><span data-stu-id="73998-110">This section describes the terms and concepts used with events in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="declaring-events"></a><span data-ttu-id="73998-111">宣告事件</span><span class="sxs-lookup"><span data-stu-id="73998-111">Declaring Events</span></span>  
 <span data-ttu-id="73998-112">您可以在類別、結構、模組和介面內，使用 `Event` 關鍵字宣告事件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73998-112">You declare events within classes, structures, modules, and interfaces using the `Event` keyword, as in the following example:</span></span>  
  
 <span data-ttu-id="73998-113">[!code-vb[VbVbalrEvents#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="73998-113">[!code-vb[VbVbalrEvents#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_1.vb)]</span></span>  
  
### <a name="raising-events"></a><span data-ttu-id="73998-114">引發事件</span><span class="sxs-lookup"><span data-stu-id="73998-114">Raising Events</span></span>  
 <span data-ttu-id="73998-115">事件就像是訊息，會告知發生了重要事件。</span><span class="sxs-lookup"><span data-stu-id="73998-115">An event is like a message announcing that something important has occurred.</span></span> <span data-ttu-id="73998-116">廣播訊息的動作稱為「引發」事件。</span><span class="sxs-lookup"><span data-stu-id="73998-116">The act of broadcasting the message is called *raising* the event.</span></span> <span data-ttu-id="73998-117">在 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 中，您可以利用 `RaiseEvent` 陳述式引發事件，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73998-117">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], you raise events with the `RaiseEvent` statement, as in the following example:</span></span>  
  
 <span data-ttu-id="73998-118">[!code-vb[VbVbalrEvents#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="73998-118">[!code-vb[VbVbalrEvents#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_2.vb)]</span></span>  
  
 <span data-ttu-id="73998-119">事件必須在其宣告所在的類別、模組或結構範圍內引發。</span><span class="sxs-lookup"><span data-stu-id="73998-119">Events must be raised within the scope of the class, module, or structure where they are declared.</span></span> <span data-ttu-id="73998-120">例如，衍生的類別無法引發繼承自基底類別的事件。</span><span class="sxs-lookup"><span data-stu-id="73998-120">For example, a derived class cannot raise events inherited from a base class.</span></span>  
  
### <a name="event-senders"></a><span data-ttu-id="73998-121">事件傳送者</span><span class="sxs-lookup"><span data-stu-id="73998-121">Event Senders</span></span>  
 <span data-ttu-id="73998-122">任何可引發事件的物件都是「事件傳送者」，亦稱為「事件來源」。</span><span class="sxs-lookup"><span data-stu-id="73998-122">Any object capable of raising an event is an *event sender*, also known as an *event source*.</span></span> <span data-ttu-id="73998-123">表單、控制項和使用者定義的物件都是事件傳送者的範例。</span><span class="sxs-lookup"><span data-stu-id="73998-123">Forms, controls, and user-defined objects are examples of event senders.</span></span>  
  
### <a name="event-handlers"></a><span data-ttu-id="73998-124">事件處理常式</span><span class="sxs-lookup"><span data-stu-id="73998-124">Event Handlers</span></span>  
 <span data-ttu-id="73998-125">「事件處理常式」是在發生相對應事件時所呼叫的程序。</span><span class="sxs-lookup"><span data-stu-id="73998-125">*Event handlers* are procedures that are called when a corresponding event occurs.</span></span> <span data-ttu-id="73998-126">您可以使用具有相符簽章的任何有效副程式，做為事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="73998-126">You can use any valid subroutine with a matching signature as an event handler.</span></span> <span data-ttu-id="73998-127">不過，您無法使用函式做為事件處理常式，因為它無法將值傳回事件來源。</span><span class="sxs-lookup"><span data-stu-id="73998-127">You cannot use a function as an event handler, however, because it cannot return a value to the event source.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="73998-128"> 會針對結合了事件傳送者名稱、底線和事件名稱的事件處理常式使用標準命名慣例。</span><span class="sxs-lookup"><span data-stu-id="73998-128"> uses a standard naming convention for event handlers that combines the name of the event sender, an underscore, and the name of the event.</span></span> <span data-ttu-id="73998-129">例如，將名為 `button1` 的按鈕 `Click` 事件命名為 `Sub button1_Click`。</span><span class="sxs-lookup"><span data-stu-id="73998-129">For example, the `Click` event of a button named `button1` would be named `Sub button1_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73998-130">我們建議您在為自己的事件定義事件處理常式時，使用此命名慣例，但這並非必要；您可以使用任何有效的副程式名稱。</span><span class="sxs-lookup"><span data-stu-id="73998-130">We recommend that you use this naming convention when defining event handlers for your own events, but it is not required; you can use any valid subroutine name.</span></span>  
  
## <a name="associating-events-with-event-handlers"></a><span data-ttu-id="73998-131">建立事件與事件處理常式的關聯</span><span class="sxs-lookup"><span data-stu-id="73998-131">Associating Events with Event Handlers</span></span>  
 <span data-ttu-id="73998-132">讓事件處理常式變成可用之前，您必須先使用 `Handles` 或 `AddHandler` 陳述式來建立它與事件的關聯。</span><span class="sxs-lookup"><span data-stu-id="73998-132">Before an event handler becomes usable, you must first associate it with an event by using either the `Handles` or `AddHandler` statement.</span></span>  
  
### <a name="withevents-and-the-handles-clause"></a><span data-ttu-id="73998-133">WithEvents 和 Handles 子句</span><span class="sxs-lookup"><span data-stu-id="73998-133">WithEvents and the Handles Clause</span></span>  
 <span data-ttu-id="73998-134">`WithEvents` 陳述式和 `Handles` 子句提供一種宣告式方式來指定事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="73998-134">The `WithEvents` statement and `Handles` clause provide a declarative way of specifying event handlers.</span></span> <span data-ttu-id="73998-135">使用 `WithEvents` 關鍵字宣告之物件所引發的事件可以透過任何具有 `Handles` 陳述式的程序來處理，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="73998-135">An event raised by an object declared with the `WithEvents` keyword can be handled by any procedure with a `Handles` statement for that event, as shown in the following example:</span></span>  
  
 <span data-ttu-id="73998-136">[!code-vb[VbVbalrEvents#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="73998-136">[!code-vb[VbVbalrEvents#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_3.vb)]</span></span>  
  
 <span data-ttu-id="73998-137">`WithEvents` 陳述式和 `Handles` 子句通常是事件處理常式的最佳選擇，因為它們使用的宣告式語法讓事件能夠更容易處理程式碼、讀取及偵錯。</span><span class="sxs-lookup"><span data-stu-id="73998-137">The `WithEvents` statement and the `Handles` clause are often the best choice for event handlers because the declarative syntax they use makes event handling easier to code, read and debug.</span></span> <span data-ttu-id="73998-138">不過，請注意下列有關使用 `WithEvents` 變數的限制：</span><span class="sxs-lookup"><span data-stu-id="73998-138">However, be aware of the following limitations on the use of `WithEvents` variables:</span></span>  
  
-   <span data-ttu-id="73998-139">您不能使用 `WithEvents` 變數做為物件變數。</span><span class="sxs-lookup"><span data-stu-id="73998-139">You cannot use a `WithEvents` variable as an object variable.</span></span> <span data-ttu-id="73998-140">也就是說，您無法將它宣告為 `Object` - 當您宣告變數時，必須指定類別名稱。</span><span class="sxs-lookup"><span data-stu-id="73998-140">That is, you cannot declare it as `Object`—you must specify the class name when you declare the variable.</span></span>  
  
-   <span data-ttu-id="73998-141">由於共用的事件並未繫結至類別執行個體，因此，您無法使用 `WithEvents`，以宣告方式處理共用的事件。</span><span class="sxs-lookup"><span data-stu-id="73998-141">Because shared eventsare not tied to class instances, you cannot use `WithEvents` to declaratively handle shared events.</span></span> <span data-ttu-id="73998-142">同樣地，您不能使用 `WithEvents` 或 `Handles`，處理來自 `Structure` 的事件。</span><span class="sxs-lookup"><span data-stu-id="73998-142">Similarly, you cannot use `WithEvents` or `Handles` to handle events from a `Structure`.</span></span> <span data-ttu-id="73998-143">在這兩種情況下，您可以使用 `AddHandler` 陳述式來處理這些事件。</span><span class="sxs-lookup"><span data-stu-id="73998-143">In both cases, you can use the `AddHandler` statement to handle those events.</span></span>  
  
-   <span data-ttu-id="73998-144">您無法建立 `WithEvents` 變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="73998-144">You cannot create arrays of `WithEvents` variables.</span></span>  
  
 <span data-ttu-id="73998-145">`WithEvents` 變數可讓單一事件處理常式處理一或多種事件，或者讓一或多個事件處理常式處理相同種類的事件。</span><span class="sxs-lookup"><span data-stu-id="73998-145">`WithEvents` variables allow a single event handler to handle one or more kind of event, or one or more event handlers to handle the same kind of event.</span></span>  
  
 <span data-ttu-id="73998-146">雖然 `Handles` 子句是建立事件與事件處理常式之關聯的標準方式，但它只能在編譯時期建立事件與事件處理常式的關聯。</span><span class="sxs-lookup"><span data-stu-id="73998-146">Although the `Handles` clause is the standard way of associating an event with an event handler, it is limited to associating events with event handlers at compile time.</span></span>  
  
 <span data-ttu-id="73998-147">在某些情況下 (例如，與表單或控制項相關聯的事件)，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 會自動 Stub 出空的事件處理常式，並將它關聯至事件。</span><span class="sxs-lookup"><span data-stu-id="73998-147">In some cases, such as with events associated with forms or controls, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically stubs out an empty event handler and associates it with an event.</span></span> <span data-ttu-id="73998-148">例如，當您在設計模式中按兩下表單上的命令按鈕時，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 會為該命令按鈕建立空的事件處理常式和 `WithEvents` 變數，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="73998-148">For example, when you double-click a command button on a form in design mode, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] creates an empty event handler and a `WithEvents` variable for the command button, as in the following code:</span></span>  
  
 <span data-ttu-id="73998-149">[!code-vb[VbVbalrEvents#26](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="73998-149">[!code-vb[VbVbalrEvents#26](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_4.vb)]</span></span>  
  
### <a name="addhandler-and-removehandler"></a><span data-ttu-id="73998-150">AddHandler 和 RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="73998-150">AddHandler and RemoveHandler</span></span>  
 <span data-ttu-id="73998-151">`AddHandler` 陳述式類似 `Handles` 子句，這兩者都能讓您指定事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="73998-151">The `AddHandler` statement is similar to the `Handles` clause in that both allow you to specify an event handler.</span></span> <span data-ttu-id="73998-152">不過，與 `RemoveHandler` 搭配使用的 `AddHandler` 所提供的彈性比 `Handles` 子句更大，可讓您以動態方式加入、移除及變更與事件相關聯的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="73998-152">However, `AddHandler`, used with `RemoveHandler`, provides greater flexibility than the `Handles` clause, allowing you to dynamically add, remove, and change the event handler associated with an event.</span></span> <span data-ttu-id="73998-153">如果您想要處理共用的事件或來自結構的事件，就必須使用 `AddHandler`。</span><span class="sxs-lookup"><span data-stu-id="73998-153">If you want to handle shared events or events from a structure, you must use `AddHandler`.</span></span>  
  
 <span data-ttu-id="73998-154">`AddHandler` 會採用兩個引數︰來自事件傳送者的事件名稱 (例如控制項)，以及評估委派的運算式。</span><span class="sxs-lookup"><span data-stu-id="73998-154">`AddHandler` takes two arguments: the name of an event from an event sender such as a control, and an expression that evaluates to a delegate.</span></span> <span data-ttu-id="73998-155">使用 `AddHandler` 時，您不需明確指定委派類別，因為 `AddressOf` 陳述式一律會傳回對委派的參考。</span><span class="sxs-lookup"><span data-stu-id="73998-155">You do not need to explicitly specify the delegate class when using `AddHandler`, since the `AddressOf` statement always returns a reference to the delegate.</span></span> <span data-ttu-id="73998-156">下列範例會建立事件處理常式與物件所引發之事件的關聯：</span><span class="sxs-lookup"><span data-stu-id="73998-156">The following example associates an event handler with an event raised by an object:</span></span>  
  
 <span data-ttu-id="73998-157">[!code-vb[VbVbalrEvents#28](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="73998-157">[!code-vb[VbVbalrEvents#28](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_5.vb)]</span></span>  
  
 <span data-ttu-id="73998-158">`RemoveHandler` (其會中斷事件與事件處理常式的關聯) 會使用與 `AddHandler` 相同的語法。</span><span class="sxs-lookup"><span data-stu-id="73998-158">`RemoveHandler`, which disconnects an event from an event handler, uses the same syntax as `AddHandler`.</span></span> <span data-ttu-id="73998-159">例如: </span><span class="sxs-lookup"><span data-stu-id="73998-159">For example:</span></span>  
  
 <span data-ttu-id="73998-160">[!code-vb[VbVbalrEvents#29](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="73998-160">[!code-vb[VbVbalrEvents#29](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_6.vb)]</span></span>  
  
 <span data-ttu-id="73998-161">在下列範例中，事件處理常式會與事件相關聯，並引發事件。</span><span class="sxs-lookup"><span data-stu-id="73998-161">In the following example, an event handler is associated with an event, and the event is raised.</span></span> <span data-ttu-id="73998-162">事件處理常式會攔截事件，並顯示一則訊息。</span><span class="sxs-lookup"><span data-stu-id="73998-162">The event handler catches the event and displays a message.</span></span>  
  
 <span data-ttu-id="73998-163">接著，移除第一個事件處理常式，並將不同的事件處理常式關聯至該事件。</span><span class="sxs-lookup"><span data-stu-id="73998-163">Then the first event handler is removed and a different event handler is associated with the event.</span></span> <span data-ttu-id="73998-164">再次引發事件時，即會顯示不同的訊息。</span><span class="sxs-lookup"><span data-stu-id="73998-164">When the event is raised again, a different message is displayed.</span></span>  
  
 <span data-ttu-id="73998-165">最後，移除第二個事件處理常式，然後第三次引發事件。</span><span class="sxs-lookup"><span data-stu-id="73998-165">Finally, the second event handler is removed and the event is raised for a third time.</span></span> <span data-ttu-id="73998-166">由於不再有與事件相關聯的事件處理常式，因此不會採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="73998-166">Because there is no longer an event handler associated with the event, no action is taken.</span></span>  
  
 <span data-ttu-id="73998-167">[!code-vb[VbVbalrEvents#38](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="73998-167">[!code-vb[VbVbalrEvents#38](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_7.vb)]</span></span>  
  
## <a name="handling-events-inherited-from-a-base-class"></a><span data-ttu-id="73998-168">處理繼承自基底類別的事件</span><span class="sxs-lookup"><span data-stu-id="73998-168">Handling Events Inherited from a Base Class</span></span>  
 <span data-ttu-id="73998-169">「衍生類別」(繼承基底類別特性的類別) 可以使用 `Handles``MyBase` 陳述式，來處理其基底類別所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="73998-169">*Derived classes*—classes that inherit characteristics from a base class—can handle events raised by their base class using the `Handles``MyBase` statement.</span></span>  
  
#### <a name="to-handle-events-from-a-base-class"></a><span data-ttu-id="73998-170">處理來自基底類別的事件</span><span class="sxs-lookup"><span data-stu-id="73998-170">To handle events from a base class</span></span>  
  
-   <span data-ttu-id="73998-171">在衍生類別中宣告事件處理常式，方法是將 `Handles MyBase.`*eventname* 陳述式加入至事件處理常式程序的宣告行中，其中 *eventname* 為您要處理之基底類別中的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="73998-171">Declare an event handler in the derived class by adding a `Handles MyBase.`*eventname* statement to the declaration line of your event-handler procedure, where *eventname* is the name of the event in the base class you are handling.</span></span> <span data-ttu-id="73998-172">例如: </span><span class="sxs-lookup"><span data-stu-id="73998-172">For example:</span></span>  
  
     <span data-ttu-id="73998-173">[!code-vb[VbVbalrEvents#12](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="73998-173">[!code-vb[VbVbalrEvents#12](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_8.vb)]</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="73998-174">相關章節</span><span class="sxs-lookup"><span data-stu-id="73998-174">Related Sections</span></span>  
  
|<span data-ttu-id="73998-175">標題</span><span class="sxs-lookup"><span data-stu-id="73998-175">Title</span></span>|<span data-ttu-id="73998-176">說明</span><span class="sxs-lookup"><span data-stu-id="73998-176">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="73998-177">逐步解說：宣告和引發事件</span><span class="sxs-lookup"><span data-stu-id="73998-177">Walkthrough: Declaring and Raising Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|<span data-ttu-id="73998-178">提供如何宣告和引發類別事件的逐步說明。</span><span class="sxs-lookup"><span data-stu-id="73998-178">Provides a step-by-step description of how to declare and raise events for a class.</span></span>|  
|[<span data-ttu-id="73998-179">逐步解說：處理事件</span><span class="sxs-lookup"><span data-stu-id="73998-179">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|<span data-ttu-id="73998-180">示範如何撰寫事件處理常式的程序。</span><span class="sxs-lookup"><span data-stu-id="73998-180">Demonstrates how to write an event-handler procedure.</span></span>|  
|[<span data-ttu-id="73998-181">如何：宣告自訂事件以避免封鎖</span><span class="sxs-lookup"><span data-stu-id="73998-181">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|<span data-ttu-id="73998-182">示範如何定義自訂事件，以非同步方式呼叫它的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="73998-182">Demonstrates how to define a custom event that allows its event handlers to be called asynchronously.</span></span>|  
|[<span data-ttu-id="73998-183">如何：宣告自訂事件以節省記憶體</span><span class="sxs-lookup"><span data-stu-id="73998-183">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|<span data-ttu-id="73998-184">示範如何定義只有在處理事件時才會使用記憶體的自訂事件。</span><span class="sxs-lookup"><span data-stu-id="73998-184">Demonstrates how to define a custom event that uses memory only when the event is handled.</span></span>|  
|[<span data-ttu-id="73998-185">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="73998-185">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|<span data-ttu-id="73998-186">列出繼承元件中的事件處理常式所引發的常見問題。</span><span class="sxs-lookup"><span data-stu-id="73998-186">Lists common issues that arise with event handlers in inherited components.</span></span>|  
|[<span data-ttu-id="73998-187">事件</span><span class="sxs-lookup"><span data-stu-id="73998-187">Events</span></span>](../../../../standard/events/index.md)|<span data-ttu-id="73998-188">提供 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中事件模型的概觀。</span><span class="sxs-lookup"><span data-stu-id="73998-188">Provides an overview of the event model in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>|  
|[<span data-ttu-id="73998-189">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="73998-189">Creating Event Handlers in Windows Forms</span></span>](https://msdn.microsoft.com/library/dacysss4.aspx)|<span data-ttu-id="73998-190">描述如何使用與 Windows Form 物件相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="73998-190">Describes how to work with events associated with Windows Forms objects.</span></span>|  
|[<span data-ttu-id="73998-191">委派</span><span class="sxs-lookup"><span data-stu-id="73998-191">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|<span data-ttu-id="73998-192">提供 Visual Basic 中的委派概觀。</span><span class="sxs-lookup"><span data-stu-id="73998-192">Provides an overview of delegates in Visual Basic.</span></span>|

