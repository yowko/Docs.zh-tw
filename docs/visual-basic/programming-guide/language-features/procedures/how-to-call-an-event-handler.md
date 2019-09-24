---
title: 作法：呼叫中的事件處理常式 Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: a9e090e83b180686ccb832aa6efb314c7e0fcc9a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216624"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="c2f7a-102">作法：呼叫中的事件處理常式 Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2f7a-102">How to: Call an Event Handler in Visual Basic</span></span>

<span data-ttu-id="c2f7a-103">*事件*是某些程式元件所能辨識的動作或發生的情況，例如滑鼠點擊或已超過點數限制，而您可以撰寫程式碼來回應。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="c2f7a-104">*事件處理常式*是您為了回應事件而撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-104">An *event handler* is the code you write to respond to an event.</span></span>

 <span data-ttu-id="c2f7a-105">Visual Basic 中的事件處理常式是`Sub`一個程式。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-105">An event handler in Visual Basic is a `Sub` procedure.</span></span> <span data-ttu-id="c2f7a-106">不過，您通常不會以與其他`Sub`程式相同的方式來呼叫它。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="c2f7a-107">相反地，您會將程式識別為事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="c2f7a-108">您可以使用[Handles](../../../language-reference/statements/handles-clause.md)子句和[WithEvents](../../../language-reference/modifiers/withevents.md)變數，或使用[AddHandler 語句](../../../language-reference/statements/addhandler-statement.md)來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-108">You can do this either with a [Handles](../../../language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="c2f7a-109">`Handles`使用子句是在 Visual Basic 中宣告事件處理常式的預設方式。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-109">Using a `Handles` clause is the default way to declare an event handler in Visual Basic.</span></span> <span data-ttu-id="c2f7a-110">當您在整合式開發環境（IDE）中進行程式設計時，這就是設計師撰寫事件處理常式的方式。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="c2f7a-111">`AddHandler`語句適用于在執行時間動態引發事件。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>

 <span data-ttu-id="c2f7a-112">當事件發生時，Visual Basic 會自動呼叫事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-112">When the event occurs, Visual Basic automatically calls the event handler procedure.</span></span> <span data-ttu-id="c2f7a-113">任何可存取事件的程式碼，都可以藉由執行[RaiseEvent 語句](../../../language-reference/statements/raiseevent-statement.md)來使其發生。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../language-reference/statements/raiseevent-statement.md).</span></span>

 <span data-ttu-id="c2f7a-114">您可以將一個以上的事件處理常式與同一個事件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="c2f7a-115">在某些情況下，您可以將處理常式與事件中斷關聯。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="c2f7a-116">如需詳細資訊，請參閱[事件](../events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-116">For more information, see [Events](../events/index.md).</span></span>

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="c2f7a-117">使用控制碼和 WithEvents 呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="c2f7a-117">To call an event handler using Handles and WithEvents</span></span>

1. <span data-ttu-id="c2f7a-118">請確定事件是以[事件語句](../../../language-reference/statements/event-statement.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-118">Make sure the event is declared with an [Event Statement](../../../language-reference/statements/event-statement.md).</span></span>

2. <span data-ttu-id="c2f7a-119">使用[WithEvents](../../../language-reference/modifiers/withevents.md)關鍵字，在模組或類別層級宣告物件變數。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-119">Declare an object variable at module or class level, using the [WithEvents](../../../language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="c2f7a-120">這個`As`變數的子句必須指定引發事件的類別。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-120">The `As` clause for this variable must specify the class that raises the event.</span></span>

3. <span data-ttu-id="c2f7a-121">在事件處理`Sub`程式的宣告中，加入可指定`WithEvents`變數和事件名稱的[控制碼](../../../language-reference/statements/handles-clause.md)子句。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>

4. <span data-ttu-id="c2f7a-122">當事件發生時，Visual Basic 會自動呼叫`Sub`程式。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-122">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="c2f7a-123">您的程式碼可以`RaiseEvent`使用語句來使事件發生。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

     <span data-ttu-id="c2f7a-124">下列範例定義的事件和`WithEvents`變數，會參考引發事件的類別。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="c2f7a-125">事件處理`Sub`程式會`Handles`使用子句來指定它所處理的類別和事件。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="c2f7a-126">使用 AddHandler 呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="c2f7a-126">To call an event handler using AddHandler</span></span>

1. <span data-ttu-id="c2f7a-127">請確定事件是使用`Event`語句宣告的。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-127">Make sure the event is declared with an `Event` statement.</span></span>

2. <span data-ttu-id="c2f7a-128">執行[AddHandler 語句](../../../language-reference/statements/addhandler-statement.md)，以動態方式將事件處理`Sub`程式與事件連接。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-128">Execute an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>

3. <span data-ttu-id="c2f7a-129">當事件發生時，Visual Basic 會自動呼叫`Sub`程式。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-129">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="c2f7a-130">您的程式碼可以`RaiseEvent`使用語句來使事件發生。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

     <span data-ttu-id="c2f7a-131">下列範例會定義`Sub` <xref:System.Windows.Forms.Form.Closing>處理表單事件的程式。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-131">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="c2f7a-132">然後，它會使用[AddHandler 語句](../../../language-reference/statements/addhandler-statement.md)，將`catchClose`程式與的事件處理常式<xref:System.Windows.Forms.Form.Closing>產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-132">It then uses the [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     <span data-ttu-id="c2f7a-133">您可以藉由執行[RemoveHandler 語句](../../../language-reference/statements/removehandler-statement.md)，將事件處理常式與事件中斷關聯。</span><span class="sxs-lookup"><span data-stu-id="c2f7a-133">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../language-reference/statements/removehandler-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2f7a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2f7a-134">See also</span></span>

- [<span data-ttu-id="c2f7a-135">程序</span><span class="sxs-lookup"><span data-stu-id="c2f7a-135">Procedures</span></span>](index.md)
- [<span data-ttu-id="c2f7a-136">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="c2f7a-136">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="c2f7a-137">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="c2f7a-137">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="c2f7a-138">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="c2f7a-138">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="c2f7a-139">如何：建立程式</span><span class="sxs-lookup"><span data-stu-id="c2f7a-139">How to: Create a Procedure</span></span>](how-to-create-a-procedure.md)
- [<span data-ttu-id="c2f7a-140">如何：呼叫不會傳回值的程式</span><span class="sxs-lookup"><span data-stu-id="c2f7a-140">How to: Call a Procedure that Does Not Return a Value</span></span>](how-to-call-a-procedure-that-does-not-return-a-value.md)
