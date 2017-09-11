---
title: "如何︰ 在 Visual Basic 中呼叫事件處理常式 |Microsoft 文件"
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
- Visual Basic code, procedures
- event handlers, calling
- event handlers
- procedures, event handlers
- procedures, calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: 19
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
ms.openlocfilehash: dc0174d50c7b5f5cda9d057bce39960b3e563f4e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="fecac-102">如何：在 Visual Basic 中呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="fecac-102">How to: Call an Event Handler in Visual Basic</span></span>
<span data-ttu-id="fecac-103">*事件*時的動作或狀況，例如滑鼠按一下或信用額度超過 — 辨認某個程式元件，而且您可以撰寫程式碼來回應。</span><span class="sxs-lookup"><span data-stu-id="fecac-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="fecac-104">*事件處理常式*是撰寫來回應事件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fecac-104">An *event handler* is the code you write to respond to an event.</span></span>  
  
 <span data-ttu-id="fecac-105">事件處理常式中的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="fecac-105">An event handler in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is a `Sub` procedure.</span></span> <span data-ttu-id="fecac-106">不過，您不正常呼叫它相同方式其他`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="fecac-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="fecac-107">相反地，您可以識別程序為事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="fecac-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="fecac-108">您可以使用[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句和[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)變數，或使用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="fecac-108">You can do this either with a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="fecac-109">使用`Handles`子句是宣告中的事件處理常式的預設方式[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fecac-109">Using a `Handles` clause is the default way to declare an event handler in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="fecac-110">這是在整合式的開發環境 (IDE) 中進行程式設計時，設計工具撰寫事件處理常式的方式。</span><span class="sxs-lookup"><span data-stu-id="fecac-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="fecac-111">`AddHandler`陳述式是適用於在執行階段動態地引發事件。</span><span class="sxs-lookup"><span data-stu-id="fecac-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>  
  
 <span data-ttu-id="fecac-112">發生事件時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會自動呼叫事件處理常式的程序。</span><span class="sxs-lookup"><span data-stu-id="fecac-112">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the event handler procedure.</span></span> <span data-ttu-id="fecac-113">任何可以存取事件的程式碼可能會導致發生這個問題藉由執行[RaiseEvent 陳述式](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="fecac-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>  
  
 <span data-ttu-id="fecac-114">您可以將多個事件處理常式與相同的事件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="fecac-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="fecac-115">在某些情況下，您可以中斷關聯的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="fecac-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="fecac-116">如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fecac-116">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="fecac-117">若要呼叫事件處理常式使用控制代碼和 WithEvents</span><span class="sxs-lookup"><span data-stu-id="fecac-117">To call an event handler using Handles and WithEvents</span></span>  
  
1.  <span data-ttu-id="fecac-118">請確定事件宣告與[Event 陳述式](../../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="fecac-118">Make sure the event is declared with an [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
2.  <span data-ttu-id="fecac-119">宣告物件變數在模組或類別層級，使用[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fecac-119">Declare an object variable at module or class level, using the [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="fecac-120">`As`子句，這個變數必須指定引發事件的類別。</span><span class="sxs-lookup"><span data-stu-id="fecac-120">The `As` clause for this variable must specify the class that raises the event.</span></span>  
  
3.  <span data-ttu-id="fecac-121">宣告中的事件處理`Sub`程序中，加入[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句指定`WithEvents`變數和事件名稱。</span><span class="sxs-lookup"><span data-stu-id="fecac-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>  
  
4.  <span data-ttu-id="fecac-122">發生事件時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動呼叫`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="fecac-122">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="fecac-123">您的程式碼可以使用`RaiseEvent`陳述式就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="fecac-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="fecac-124">下列範例會定義事件和`WithEvents`指的是在類別中引發事件的變數。</span><span class="sxs-lookup"><span data-stu-id="fecac-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="fecac-125">事件處理`Sub`程序會使用`Handles`子句，以指定的類別和它處理的事件。</span><span class="sxs-lookup"><span data-stu-id="fecac-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>  
  
     <span data-ttu-id="fecac-126">[!code-vb[VbVbcnProcedures #&4;](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fecac-126">[!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]</span></span>  
  
### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="fecac-127">若要呼叫使用 AddHandler 的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="fecac-127">To call an event handler using AddHandler</span></span>  
  
1.  <span data-ttu-id="fecac-128">請確定事件宣告與`Event`陳述式。</span><span class="sxs-lookup"><span data-stu-id="fecac-128">Make sure the event is declared with an `Event` statement.</span></span>  
  
2.  <span data-ttu-id="fecac-129">執行[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)動態連接事件處理`Sub`與事件的程序。</span><span class="sxs-lookup"><span data-stu-id="fecac-129">Execute an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>  
  
3.  <span data-ttu-id="fecac-130">發生事件時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動呼叫`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="fecac-130">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="fecac-131">您的程式碼可以使用`RaiseEvent`陳述式就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="fecac-131">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="fecac-132">下列範例會定義`Sub`程序處理<xref:System.Windows.Forms.Form.Closing>表單的事件。</xref:System.Windows.Forms.Form.Closing></span><span class="sxs-lookup"><span data-stu-id="fecac-132">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="fecac-133">然後它會使用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)關聯`catchClose` <xref:System.Windows.Forms.Form.Closing>.</xref:System.Windows.Forms.Form.Closing>的事件處理常式的程序</span><span class="sxs-lookup"><span data-stu-id="fecac-133">It then uses the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>  
  
     <span data-ttu-id="fecac-134">[!code-vb[VbVbcnProcedures #&5;](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="fecac-134">[!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]</span></span>  
  
     <span data-ttu-id="fecac-135">您可以藉由執行關聯事件的事件處理常式[RemoveHandler 陳述式](../../../../visual-basic/language-reference/statements/removehandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="fecac-135">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fecac-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fecac-136">See Also</span></span>  
 <span data-ttu-id="fecac-137">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="fecac-137">[Procedures](./index.md) </span></span>  
<span data-ttu-id="fecac-138"> [Sub 程序](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="fecac-138"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="fecac-139"> [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="fecac-139"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="fecac-140"> [AddressOf 運算子](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="fecac-140"> [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="fecac-141"> [如何︰ 建立程序](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="fecac-141"> [How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
<span data-ttu-id="fecac-142"> [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="fecac-142"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span></span>
