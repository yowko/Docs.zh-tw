---
title: "RaiseEvent 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
dev_langs:
- VB
helpviewer_keywords:
- raising events, RaiseEvent statement
- RaiseEvent statement
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
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
ms.openlocfilehash: 6a0cf1c5635335f22fddd57c7dd2baaeca6ddd23
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="raiseevent-statement"></a><span data-ttu-id="8759a-102">RaiseEvent 陳述式</span><span class="sxs-lookup"><span data-stu-id="8759a-102">RaiseEvent Statement</span></span>
<span data-ttu-id="8759a-103">觸發程序在類別、 表單或文件中的模組層級宣告的事件。</span><span class="sxs-lookup"><span data-stu-id="8759a-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8759a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8759a-104">Syntax</span></span>  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="8759a-105">組件</span><span class="sxs-lookup"><span data-stu-id="8759a-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="8759a-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="8759a-106">Required.</span></span> <span data-ttu-id="8759a-107">若要觸發事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="8759a-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="8759a-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="8759a-108">Optional.</span></span> <span data-ttu-id="8759a-109">以逗號分隔的變數、 陣列或運算式清單。</span><span class="sxs-lookup"><span data-stu-id="8759a-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="8759a-110">`argumentlist`引數必須括在括號括住。</span><span class="sxs-lookup"><span data-stu-id="8759a-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="8759a-111">如果不有任何引數，必須省略括號。</span><span class="sxs-lookup"><span data-stu-id="8759a-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8759a-112">備註</span><span class="sxs-lookup"><span data-stu-id="8759a-112">Remarks</span></span>  
 <span data-ttu-id="8759a-113">必要`eventname`在模組中宣告的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="8759a-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="8759a-114">它會遵循 Visual Basic 變數命名慣例。</span><span class="sxs-lookup"><span data-stu-id="8759a-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="8759a-115">如果尚未在引發此模組中宣告事件，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8759a-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="8759a-116">下列程式碼片段將說明事件宣告和引發事件的程序。</span><span class="sxs-lookup"><span data-stu-id="8759a-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 <span data-ttu-id="8759a-117">[!code-vb[VbVbalrEvents #&37;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8759a-117">[!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="8759a-118">您不能使用`RaiseEvent`引發模組中未明確宣告的事件。</span><span class="sxs-lookup"><span data-stu-id="8759a-118">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="8759a-119">例如，所有的表單繼承<xref:System.Windows.Forms.Control.Click>事件<xref:System.Windows.Forms.Form?displayProperty=fullName>，無法升級使用`RaiseEvent`衍生格式中。</xref:System.Windows.Forms.Form?displayProperty=fullName> </xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="8759a-119">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=fullName>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="8759a-120">如果您宣告`Click`事件在表單的模組，它會遮蔽表單的自己<xref:System.Windows.Forms.Control.Click>事件。</xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="8759a-120">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="8759a-121">您仍然可以叫用表單的<xref:System.Windows.Forms.Control.Click>事件，藉由呼叫<xref:System.Windows.Forms.Control.OnClick%2A>方法。</xref:System.Windows.Forms.Control.OnClick%2A> </xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="8759a-121">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="8759a-122">根據預設，在 Visual Basic 中定義的事件會引發其事件處理常式，建立連接的順序。</span><span class="sxs-lookup"><span data-stu-id="8759a-122">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="8759a-123">因為事件可以有`ByRef`參數，較晚連接的處理程序可能會收到已由先前的事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="8759a-123">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="8759a-124">事件處理常式執行之後，控制權會傳回引發事件的副程式。</span><span class="sxs-lookup"><span data-stu-id="8759a-124">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8759a-125">在宣告的類別的建構函式應該不會引發非共用的事件。</span><span class="sxs-lookup"><span data-stu-id="8759a-125">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="8759a-126">雖然這類事件不會造成執行階段錯誤，因此可能無法相關聯的事件處理常式攔截。</span><span class="sxs-lookup"><span data-stu-id="8759a-126">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="8759a-127">使用`Shared`修飾詞，以建立共用的事件，若要引發事件，從建構函式。</span><span class="sxs-lookup"><span data-stu-id="8759a-127">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8759a-128">您可以定義自訂事件來變更事件的預設行為。</span><span class="sxs-lookup"><span data-stu-id="8759a-128">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="8759a-129">自訂事件，`RaiseEvent`陳述式會叫用此事件`RaiseEvent`存取子。</span><span class="sxs-lookup"><span data-stu-id="8759a-129">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="8759a-130">如需自訂事件的詳細資訊，請參閱[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="8759a-130">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8759a-131">範例</span><span class="sxs-lookup"><span data-stu-id="8759a-131">Example</span></span>  
 <span data-ttu-id="8759a-132">下列範例會使用事件以從 10 秒到 0 秒倒數計時。</span><span class="sxs-lookup"><span data-stu-id="8759a-132">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="8759a-133">程式碼將說明幾個事件相關的方法、 屬性和陳述式，包括`RaiseEvent`陳述式。</span><span class="sxs-lookup"><span data-stu-id="8759a-133">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="8759a-134">引發事件的類別是事件來源，處理事件的方法為事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8759a-134">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="8759a-135">事件來源對於它所產生的事件可以有多個處理常式。</span><span class="sxs-lookup"><span data-stu-id="8759a-135">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="8759a-136">當類別引發事件時，該事件是在每個類別 (已被選擇來處理該物件執行個體的事件) 上引發。</span><span class="sxs-lookup"><span data-stu-id="8759a-136">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="8759a-137">此範例也會使用表單 (`Form1`) 與按鈕 (`Button1`) 和文字方塊 (`TextBox1`)。</span><span class="sxs-lookup"><span data-stu-id="8759a-137">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="8759a-138">當您按一下按鈕時時，第一個文字方塊會顯示從 10 秒到 0 秒的倒數計時。</span><span class="sxs-lookup"><span data-stu-id="8759a-138">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="8759a-139">在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。</span><span class="sxs-lookup"><span data-stu-id="8759a-139">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="8759a-140">`Form1` 的程式碼會指定表單的初始和終止狀態。</span><span class="sxs-lookup"><span data-stu-id="8759a-140">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="8759a-141">它也包含引發事件時執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8759a-141">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="8759a-142">若要使用此範例中，開啟新的 Windows 應用程式專案中，加入名為按鈕`Button1`和名為文字方塊`TextBox1`主表單中，名為`Form1`。</span><span class="sxs-lookup"><span data-stu-id="8759a-142">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="8759a-143">然後以滑鼠右鍵按一下表單，並按一下 **檢視程式碼**開啟程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="8759a-143">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="8759a-144">新增`WithEvents`變數的宣告區段`Form1`類別。</span><span class="sxs-lookup"><span data-stu-id="8759a-144">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 <span data-ttu-id="8759a-145">[!code-vb[VbVbalrEvents #&14;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8759a-145">[!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8759a-146">範例</span><span class="sxs-lookup"><span data-stu-id="8759a-146">Example</span></span>  
 <span data-ttu-id="8759a-147">將下列程式碼加入至 `Form1` 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8759a-147">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="8759a-148">取代重複的程序可能存在，例如`Form_Load`，或`Button_Click`。</span><span class="sxs-lookup"><span data-stu-id="8759a-148">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 <span data-ttu-id="8759a-149">[!code-vb[VbVbalrEvents #&15;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="8759a-149">[!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="8759a-150">按 F5 以執行上述範例中，並按一下 按鈕**啟動**。</span><span class="sxs-lookup"><span data-stu-id="8759a-150">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="8759a-151">第一個文字方塊會開始倒數計時。</span><span class="sxs-lookup"><span data-stu-id="8759a-151">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="8759a-152">在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。</span><span class="sxs-lookup"><span data-stu-id="8759a-152">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8759a-153">`My.Application.DoEvents`方法不會處理事件的相同方式表單一樣。</span><span class="sxs-lookup"><span data-stu-id="8759a-153">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="8759a-154">若要讓表單直接處理事件，您可以使用多執行緒處理。</span><span class="sxs-lookup"><span data-stu-id="8759a-154">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="8759a-155">如需詳細資訊，請參閱[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)。</span><span class="sxs-lookup"><span data-stu-id="8759a-155">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8759a-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8759a-156">See Also</span></span>  
 <span data-ttu-id="8759a-157">[事件](../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="8759a-157">[Events](../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="8759a-158"> [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8759a-158"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="8759a-159"> [AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8759a-159"> [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span></span>  
<span data-ttu-id="8759a-160"> [RemoveHandler 陳述式](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8759a-160"> [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span></span>  
<span data-ttu-id="8759a-161"> [控制代碼](../../../visual-basic/language-reference/statements/handles-clause.md)</span><span class="sxs-lookup"><span data-stu-id="8759a-161"> [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)</span></span>
