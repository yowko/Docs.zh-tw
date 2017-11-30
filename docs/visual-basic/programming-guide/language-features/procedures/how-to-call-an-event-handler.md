---
title: "如何：在 Visual Basic 中呼叫事件處理常式"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52b4b6ca8b03d8301535d6aeedc3bd0190d8527f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="c1fb1-102">如何：在 Visual Basic 中呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="c1fb1-102">How to: Call an Event Handler in Visual Basic</span></span>
<span data-ttu-id="c1fb1-103">*事件*是動作或狀況，例如滑鼠點選或信用限制，或是超過 — 辨認某個程式元件，而且您可以撰寫程式碼回應。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="c1fb1-104">*事件處理常式*是您撰寫來回應事件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-104">An *event handler* is the code you write to respond to an event.</span></span>  
  
 <span data-ttu-id="c1fb1-105">中的事件處理常式[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]是`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-105">An event handler in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is a `Sub` procedure.</span></span> <span data-ttu-id="c1fb1-106">不過，您不正常呼叫它相同方式其他`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="c1fb1-107">相反地，您會識別此程序為事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="c1fb1-108">您可以執行方式是使用[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句和[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)變數，或使用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-108">You can do this either with a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="c1fb1-109">使用`Handles`子句是宣告中的事件處理常式的預設方式[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-109">Using a `Handles` clause is the default way to declare an event handler in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="c1fb1-110">這是整合式的開發環境 (IDE) 中進行程式設計時，事件處理常式由設計工具所撰寫的方式。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="c1fb1-111">`AddHandler`陳述式適合用來在執行階段動態地引發事件。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>  
  
 <span data-ttu-id="c1fb1-112">發生事件時，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]自動呼叫事件處理常式的程序。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-112">When the event occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically calls the event handler procedure.</span></span> <span data-ttu-id="c1fb1-113">具有事件的存取權的任何程式碼可能會導致它藉由執行發生[RaiseEvent 陳述式](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>  
  
 <span data-ttu-id="c1fb1-114">您可以將多個事件處理常式與相同的事件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="c1fb1-115">在某些情況下，您可以中斷關聯的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="c1fb1-116">如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-116">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="c1fb1-117">若要呼叫事件處理常式使用控制代碼和 WithEvents</span><span class="sxs-lookup"><span data-stu-id="c1fb1-117">To call an event handler using Handles and WithEvents</span></span>  
  
1.  <span data-ttu-id="c1fb1-118">請確定事件宣告為[Event 陳述式](../../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-118">Make sure the event is declared with an [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
2.  <span data-ttu-id="c1fb1-119">宣告物件變數在模組或類別層級，請使用[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-119">Declare an object variable at module or class level, using the [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="c1fb1-120">`As`子句，這個變數必須指定引發事件的類別。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-120">The `As` clause for this variable must specify the class that raises the event.</span></span>  
  
3.  <span data-ttu-id="c1fb1-121">宣告中的事件處理`Sub`程序中，加入[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)指定子句`WithEvents`變數和事件名稱。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>  
  
4.  <span data-ttu-id="c1fb1-122">發生事件時，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]自動呼叫`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-122">When the event occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="c1fb1-123">您的程式碼可以使用`RaiseEvent`陳述式就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="c1fb1-124">下列範例會定義事件和`WithEvents`指的是在類別中引發事件的變數。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="c1fb1-125">事件處理`Sub`程序會使用`Handles`子句，以指定的類別和它所處理的事件。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="c1fb1-126">若要呼叫事件處理常式使用 AddHandler</span><span class="sxs-lookup"><span data-stu-id="c1fb1-126">To call an event handler using AddHandler</span></span>  
  
1.  <span data-ttu-id="c1fb1-127">請確定事件宣告為`Event`陳述式。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-127">Make sure the event is declared with an `Event` statement.</span></span>  
  
2.  <span data-ttu-id="c1fb1-128">執行[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)動態連接事件處理`Sub`程序與事件。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-128">Execute an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>  
  
3.  <span data-ttu-id="c1fb1-129">發生事件時，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]自動呼叫`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-129">When the event occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="c1fb1-130">您的程式碼可以使用`RaiseEvent`陳述式就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="c1fb1-131">下列範例會定義`Sub`程序處理<xref:System.Windows.Forms.Form.Closing>表單的事件。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-131">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="c1fb1-132">然後它會使用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)關聯`catchClose`與事件處理常式的程序<xref:System.Windows.Forms.Form.Closing>。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-132">It then uses the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     <span data-ttu-id="c1fb1-133">您可以藉由執行中斷關聯事件的事件處理常式[RemoveHandler 陳述式](../../../../visual-basic/language-reference/statements/removehandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c1fb1-133">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1fb1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1fb1-134">See Also</span></span>  
 [<span data-ttu-id="c1fb1-135">程序</span><span class="sxs-lookup"><span data-stu-id="c1fb1-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="c1fb1-136">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="c1fb1-136">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="c1fb1-137">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="c1fb1-137">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="c1fb1-138">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="c1fb1-138">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="c1fb1-139">如何：建立程序</span><span class="sxs-lookup"><span data-stu-id="c1fb1-139">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="c1fb1-140">如何：呼叫不傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="c1fb1-140">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
