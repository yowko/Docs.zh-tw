---
title: 如何呼叫事件處理常式
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
no-loc:
- WithEvents
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 3762c79dd3d883ae2ccfe76b335cf98ac87d4246
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89464957"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="08602-102">如何在 Visual Basic 中呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="08602-102">How to call an event handler in Visual Basic</span></span>

<span data-ttu-id="08602-103">*事件*是由某些程式元件辨識的動作或發生（例如滑鼠點擊或超過的點數限制），且您可以撰寫程式碼來回應。</span><span class="sxs-lookup"><span data-stu-id="08602-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="08602-104">*事件處理常式*是您為了回應事件而撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="08602-104">An *event handler* is the code you write to respond to an event.</span></span>

<span data-ttu-id="08602-105">Visual Basic 中的事件處理常式是程式 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="08602-105">An event handler in Visual Basic is a `Sub` procedure.</span></span> <span data-ttu-id="08602-106">不過，您通常不會以與其他程式相同的方式來呼叫它 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="08602-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="08602-107">相反地，您會將程式識別為事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="08602-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="08602-108">您可以使用 [`Handles`](../../../language-reference/statements/handles-clause.md) 子句和 [`WithEvents`](../../../language-reference/modifiers/withevents.md) 變數，或使用 [AddHandler 語句](../../../language-reference/statements/addhandler-statement.md)來進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="08602-108">You can do this either with a [`Handles`](../../../language-reference/statements/handles-clause.md) clause and a [`WithEvents`](../../../language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="08602-109">使用 `Handles` 子句是在 Visual Basic 中宣告事件處理常式的預設方式。</span><span class="sxs-lookup"><span data-stu-id="08602-109">Using a `Handles` clause is the default way to declare an event handler in Visual Basic.</span></span> <span data-ttu-id="08602-110">當您在整合式開發環境中進行程式設計時，當您在 (IDE) 中進行程式設計時，設計工具就會撰寫事件處理常式的方式。</span><span class="sxs-lookup"><span data-stu-id="08602-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="08602-111">`AddHandler`語句適合用來在執行時間動態引發事件。</span><span class="sxs-lookup"><span data-stu-id="08602-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>

<span data-ttu-id="08602-112">當事件發生時，Visual Basic 會自動呼叫事件處理常式程式。</span><span class="sxs-lookup"><span data-stu-id="08602-112">When the event occurs, Visual Basic automatically calls the event handler procedure.</span></span> <span data-ttu-id="08602-113">任何可存取事件的程式碼，都可以藉由執行 [RaiseEvent 語句](../../../language-reference/statements/raiseevent-statement.md)來使其發生。</span><span class="sxs-lookup"><span data-stu-id="08602-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../language-reference/statements/raiseevent-statement.md).</span></span>

<span data-ttu-id="08602-114">您可以將一個以上的事件處理常式與相同事件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="08602-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="08602-115">在某些情況下，您可以中斷處理常式與事件之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="08602-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="08602-116">如需詳細資訊，請參閱[事件](../events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="08602-116">For more information, see [Events](../events/index.md).</span></span>

## <a name="call-an-event-handler-using-no-loc-texthandles-and-no-locwithevents"></a><span data-ttu-id="08602-117">使用和呼叫事件處理常式 :::no-loc text="Handles":::WithEvents</span><span class="sxs-lookup"><span data-stu-id="08602-117">Call an event handler using :::no-loc text="Handles"::: and WithEvents</span></span>

1. <span data-ttu-id="08602-118">請確定事件是使用 [事件語句](../../../language-reference/statements/event-statement.md)宣告的。</span><span class="sxs-lookup"><span data-stu-id="08602-118">Make sure the event is declared with an [Event Statement](../../../language-reference/statements/event-statement.md).</span></span>

2. <span data-ttu-id="08602-119">使用關鍵字來宣告模組或類別層級的物件變數 [`WithEvents`](../../../language-reference/modifiers/withevents.md) 。</span><span class="sxs-lookup"><span data-stu-id="08602-119">Declare an object variable at module or class level, using the [`WithEvents`](../../../language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="08602-120">`As`這個變數的子句必須指定引發事件的類別。</span><span class="sxs-lookup"><span data-stu-id="08602-120">The `As` clause for this variable must specify the class that raises the event.</span></span>

3. <span data-ttu-id="08602-121">在事件處理常式的宣告中 `Sub` ，加入 [`Handles`](../../../language-reference/statements/handles-clause.md) 指定 `WithEvents` 變數和事件名稱的子句。</span><span class="sxs-lookup"><span data-stu-id="08602-121">In the declaration of the event-handling `Sub` procedure, add a [`Handles`](../../../language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>

4. <span data-ttu-id="08602-122">當事件發生時，Visual Basic 會自動呼叫程式 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="08602-122">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="08602-123">您的程式碼可以使用 `RaiseEvent` 語句來讓事件發生。</span><span class="sxs-lookup"><span data-stu-id="08602-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="08602-124">下列範例會定義事件，以及 `WithEvents` 參考引發事件之類別的變數。</span><span class="sxs-lookup"><span data-stu-id="08602-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="08602-125">事件處理常式 `Sub` `Handles` 會使用子句來指定它所處理的類別和事件。</span><span class="sxs-lookup"><span data-stu-id="08602-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="4":::

## <a name="call-an-event-handler-using-addhandler"></a><span data-ttu-id="08602-126">使用 AddHandler 呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="08602-126">Call an event handler using AddHandler</span></span>

1. <span data-ttu-id="08602-127">請確定事件是使用語句宣告的 `Event` 。</span><span class="sxs-lookup"><span data-stu-id="08602-127">Make sure the event is declared with an `Event` statement.</span></span>

2. <span data-ttu-id="08602-128">執行 [AddHandler 語句](../../../language-reference/statements/addhandler-statement.md) ，以動態方式連接事件處理常式 `Sub` 和事件。</span><span class="sxs-lookup"><span data-stu-id="08602-128">Execute an [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>

3. <span data-ttu-id="08602-129">當事件發生時，Visual Basic 會自動呼叫程式 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="08602-129">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="08602-130">您的程式碼可以使用 `RaiseEvent` 語句來讓事件發生。</span><span class="sxs-lookup"><span data-stu-id="08602-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="08602-131">下列範例會在此函式中使用 [AddHandler 語句](../../../language-reference/statements/addhandler-statement.md) ，將 `OnFormClosing` 程式與的事件處理常式產生關聯 <xref:System.Windows.Forms.Form.FormClosing> 。</span><span class="sxs-lookup"><span data-stu-id="08602-131">The following example uses the [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) in the constructor to associate the `OnFormClosing` procedure as an event handler for <xref:System.Windows.Forms.Form.FormClosing>.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="5":::

    <span data-ttu-id="08602-132">您可以藉由執行 [RemoveHandler 語句](../../../language-reference/statements/removehandler-statement.md)來中斷事件處理常式與事件之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="08602-132">You can dissociate an event handler from an event by executing the [RemoveHandler statement](../../../language-reference/statements/removehandler-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="08602-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08602-133">See also</span></span>

- [<span data-ttu-id="08602-134">程序</span><span class="sxs-lookup"><span data-stu-id="08602-134">Procedures</span></span>](index.md)
- [<span data-ttu-id="08602-135">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="08602-135">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="08602-136">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="08602-136">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="08602-137">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="08602-137">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="08602-138">如何：建立程序</span><span class="sxs-lookup"><span data-stu-id="08602-138">How to: Create a Procedure</span></span>](how-to-create-a-procedure.md)
- [<span data-ttu-id="08602-139">如何：呼叫不傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="08602-139">How to: Call a Procedure that Does Not Return a Value</span></span>](how-to-call-a-procedure-that-does-not-return-a-value.md)
