---
title: RaiseEvent 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: 46b93c060a12d82b34dafdf3aa4ea677df6f54cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404287"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="267f1-102">RaiseEvent 陳述式</span><span class="sxs-lookup"><span data-stu-id="267f1-102">RaiseEvent Statement</span></span>
<span data-ttu-id="267f1-103">觸發在類別、表單或檔中，于模組層級宣告的事件。</span><span class="sxs-lookup"><span data-stu-id="267f1-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="267f1-104">Syntax</span></span>  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="267f1-105">組件</span><span class="sxs-lookup"><span data-stu-id="267f1-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="267f1-106">必要。</span><span class="sxs-lookup"><span data-stu-id="267f1-106">Required.</span></span> <span data-ttu-id="267f1-107">要觸發的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="267f1-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="267f1-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="267f1-108">Optional.</span></span> <span data-ttu-id="267f1-109">以逗號分隔的變數、陣列或運算式清單。</span><span class="sxs-lookup"><span data-stu-id="267f1-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="267f1-110">`argumentlist`引數必須以括弧括住。</span><span class="sxs-lookup"><span data-stu-id="267f1-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="267f1-111">如果沒有引數，則必須省略括弧。</span><span class="sxs-lookup"><span data-stu-id="267f1-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="267f1-112">備註</span><span class="sxs-lookup"><span data-stu-id="267f1-112">Remarks</span></span>  
 <span data-ttu-id="267f1-113">必要的 `eventname` 是在模組內宣告的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="267f1-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="267f1-114">它會遵循 Visual Basic 變數命名慣例。</span><span class="sxs-lookup"><span data-stu-id="267f1-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="267f1-115">如果事件尚未在引發它的模組內宣告，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="267f1-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="267f1-116">下列程式碼片段說明事件宣告，以及引發事件的程式。</span><span class="sxs-lookup"><span data-stu-id="267f1-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 <span data-ttu-id="267f1-117">您不能使用 `RaiseEvent` 來引發未在模組中明確宣告的事件。</span><span class="sxs-lookup"><span data-stu-id="267f1-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="267f1-118">例如，所有表單都會繼承 <xref:System.Windows.Forms.Control.Click> 來自的事件 <xref:System.Windows.Forms.Form?displayProperty=nameWithType> ，而無法使用 `RaiseEvent` 衍生表單中的來引發。</span><span class="sxs-lookup"><span data-stu-id="267f1-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="267f1-119">如果您 `Click` 在表單模組中宣告事件，它會遮蔽表單本身的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="267f1-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="267f1-120">您仍然可以藉 <xref:System.Windows.Forms.Control.Click> 由呼叫方法來叫用表單的事件 <xref:System.Windows.Forms.Control.OnClick%2A> 。</span><span class="sxs-lookup"><span data-stu-id="267f1-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="267f1-121">根據預設，在 Visual Basic 中定義的事件會依照建立連接的順序，引發其事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="267f1-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="267f1-122">由於事件可以有 `ByRef` 參數，因此連接延遲的進程可能會接收先前事件處理常式已變更的參數。</span><span class="sxs-lookup"><span data-stu-id="267f1-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="267f1-123">在事件處理常式執行之後，控制權會傳回給引發事件的副程式。</span><span class="sxs-lookup"><span data-stu-id="267f1-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="267f1-124">非共用事件不應在宣告它們的類別的函式中引發。</span><span class="sxs-lookup"><span data-stu-id="267f1-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="267f1-125">雖然這類事件不會造成執行階段錯誤，但關聯的事件處理常式可能無法攔截它們。</span><span class="sxs-lookup"><span data-stu-id="267f1-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="267f1-126">`Shared`如果您需要從函數引發事件，請使用修飾詞來建立共用事件。</span><span class="sxs-lookup"><span data-stu-id="267f1-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="267f1-127">您可以藉由定義自訂事件來變更事件的預設行為。</span><span class="sxs-lookup"><span data-stu-id="267f1-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="267f1-128">若為自訂事件，語句會叫用 `RaiseEvent` 事件的 `RaiseEvent` 存取子。</span><span class="sxs-lookup"><span data-stu-id="267f1-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="267f1-129">如需自訂事件的詳細資訊，請參閱[Event 語句](event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="267f1-129">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="267f1-130">範例</span><span class="sxs-lookup"><span data-stu-id="267f1-130">Example</span></span>  
 <span data-ttu-id="267f1-131">下列範例會使用事件以從 10 秒到 0 秒倒數計時。</span><span class="sxs-lookup"><span data-stu-id="267f1-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="267f1-132">此程式碼說明數個事件相關的方法、屬性和語句，包括 `RaiseEvent` 語句。</span><span class="sxs-lookup"><span data-stu-id="267f1-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="267f1-133">引發事件的類別是事件來源，處理事件的方法為事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="267f1-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="267f1-134">事件來源對於它所產生的事件可以有多個處理常式。</span><span class="sxs-lookup"><span data-stu-id="267f1-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="267f1-135">當類別引發事件時，該事件是在每個類別 (已被選擇來處理該物件執行個體的事件) 上引發。</span><span class="sxs-lookup"><span data-stu-id="267f1-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="267f1-136">此範例也會使用表單 (`Form1`) 與按鈕 (`Button1`) 和文字方塊 (`TextBox1`)。</span><span class="sxs-lookup"><span data-stu-id="267f1-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="267f1-137">當您按一下按鈕時時，第一個文字方塊會顯示從 10 秒到 0 秒的倒數計時。</span><span class="sxs-lookup"><span data-stu-id="267f1-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="267f1-138">在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。</span><span class="sxs-lookup"><span data-stu-id="267f1-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="267f1-139">`Form1` 的程式碼會指定表單的初始和終止狀態。</span><span class="sxs-lookup"><span data-stu-id="267f1-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="267f1-140">它也包含引發事件時執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="267f1-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="267f1-141">若要使用此範例，請開啟新的 Windows 應用程式專案，將名為的按鈕 `Button1` 和名 `TextBox1` 為的文字方塊新增至主要表單，名稱為 `Form1` 。</span><span class="sxs-lookup"><span data-stu-id="267f1-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="267f1-142">然後以滑鼠右鍵按一下表單，再按一下 [**查看程式碼**] 以開啟程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="267f1-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="267f1-143">將 `WithEvents` 變數新增至類別的宣告區段 `Form1` 。</span><span class="sxs-lookup"><span data-stu-id="267f1-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="267f1-144">範例</span><span class="sxs-lookup"><span data-stu-id="267f1-144">Example</span></span>  
 <span data-ttu-id="267f1-145">將下列程式碼加入至 `Form1` 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="267f1-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="267f1-146">取代可能存在的任何重複的程式，例如 `Form_Load` 或 `Button_Click` 。</span><span class="sxs-lookup"><span data-stu-id="267f1-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 <span data-ttu-id="267f1-147">按 F5 執行上述範例，然後按一下標示為 [**開始**] 的按鈕。</span><span class="sxs-lookup"><span data-stu-id="267f1-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="267f1-148">第一個文字方塊會開始倒數計時。</span><span class="sxs-lookup"><span data-stu-id="267f1-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="267f1-149">在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。</span><span class="sxs-lookup"><span data-stu-id="267f1-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="267f1-150">`My.Application.DoEvents`方法不會以與表單相同的方式來處理事件。</span><span class="sxs-lookup"><span data-stu-id="267f1-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="267f1-151">若要允許表單直接處理事件，您可以使用多執行緒。</span><span class="sxs-lookup"><span data-stu-id="267f1-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="267f1-152">如需詳細資訊，請參閱[Managed 執行緒](../../../standard/threading/index.md)。</span><span class="sxs-lookup"><span data-stu-id="267f1-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="267f1-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="267f1-153">See also</span></span>

- [<span data-ttu-id="267f1-154">事件</span><span class="sxs-lookup"><span data-stu-id="267f1-154">Events</span></span>](../../programming-guide/language-features/events/index.md)
- [<span data-ttu-id="267f1-155">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="267f1-155">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="267f1-156">AddHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="267f1-156">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="267f1-157">RemoveHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="267f1-157">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="267f1-158">控制代碼</span><span class="sxs-lookup"><span data-stu-id="267f1-158">Handles</span></span>](handles-clause.md)
