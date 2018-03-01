---
title: "On Error 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96baa5d91d0a600b84ed832fb1e3b1ed71a9d89d
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="on-error-statement-visual-basic"></a><span data-ttu-id="4f9d1-102">On Error 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f9d1-102">On Error Statement (Visual Basic)</span></span>
<span data-ttu-id="4f9d1-103">啟用錯誤處理常式，並指定位置的程序; 內的常式也可以用來停用錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-103">Enables an error-handling routine and specifies the location of the routine within a procedure; can also be used to disable an error-handling routine.</span></span>  
  
 <span data-ttu-id="4f9d1-104">不需要錯誤處理發生的任何執行階段錯誤是嚴重錯誤： 會顯示錯誤訊息，並停止執行。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-104">Without error handling, any run-time error that occurs is fatal: an error message is displayed, and execution stops.</span></span>  
  
 <span data-ttu-id="4f9d1-105">可能的話，我們建議您在使用結構化例外狀況處理程式碼中，而不是使用非結構化例外狀況處理和`On Error`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-105">Whenever possible, we suggest you use structured exception handling in your code, rather than using unstructured exception handling and the `On Error` statement.</span></span> <span data-ttu-id="4f9d1-106">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-106">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f9d1-107">`Error`關鍵字也用於[Error 陳述式](../../../visual-basic/language-reference/statements/error-statement.md)，這支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-107">The `Error` keyword is also used in the [Error Statement](../../../visual-basic/language-reference/statements/error-statement.md), which is supported for backward compatibility.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f9d1-108">語法</span><span class="sxs-lookup"><span data-stu-id="4f9d1-108">Syntax</span></span>  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a><span data-ttu-id="4f9d1-109">組件</span><span class="sxs-lookup"><span data-stu-id="4f9d1-109">Parts</span></span>  
  
|<span data-ttu-id="4f9d1-110">詞彙</span><span class="sxs-lookup"><span data-stu-id="4f9d1-110">Term</span></span>|<span data-ttu-id="4f9d1-111">定義</span><span class="sxs-lookup"><span data-stu-id="4f9d1-111">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="4f9d1-112">`GoTo` `line`</span><span class="sxs-lookup"><span data-stu-id="4f9d1-112">`GoTo` `line`</span></span>|<span data-ttu-id="4f9d1-113">可讓啟動指定在所需的那一行的錯誤處理常式`line`引數。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-113">Enables the error-handling routine that starts at the line specified in the required `line` argument.</span></span> <span data-ttu-id="4f9d1-114">`line`引數是任何行標籤或行號。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-114">The `line` argument is any line label or line number.</span></span> <span data-ttu-id="4f9d1-115">如果發生執行階段錯誤，控制移至指定的行，進行錯誤處理常式的使用中。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-115">If a run-time error occurs, control branches to the specified line, making the error handler active.</span></span> <span data-ttu-id="4f9d1-116">指定的行必須位於相同的程序`On Error`陳述式或編譯時期錯誤發生。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-116">The specified line must be in the same procedure as the `On Error` statement, or a compile-time error will occur.</span></span>|  
|<span data-ttu-id="4f9d1-117">`GoTo` 0</span><span class="sxs-lookup"><span data-stu-id="4f9d1-117">`GoTo` 0</span></span>|<span data-ttu-id="4f9d1-118">停用目前的程序中已啟用的錯誤處理常式，並將它重設`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-118">Disables enabled error handler in the current procedure and resets it to `Nothing`.</span></span>|  
|<span data-ttu-id="4f9d1-119">`GoTo` -1</span><span class="sxs-lookup"><span data-stu-id="4f9d1-119">`GoTo` -1</span></span>|<span data-ttu-id="4f9d1-120">停用目前的程序中啟用例外狀況，並將它重設`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-120">Disables enabled exception in the current procedure and resets it to `Nothing`.</span></span>|  
|`Resume Next`|<span data-ttu-id="4f9d1-121">指定執行階段錯誤發生時，緊接著此陳述式位置發生錯誤，並從該時間點繼續執行的陳述式會控制。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-121">Specifies that when a run-time error occurs, control goes to the statement immediately following the statement where the error occurred, and execution continues from that point.</span></span> <span data-ttu-id="4f9d1-122">使用此表單而非`On Error GoTo`存取物件時。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-122">Use this form rather than `On Error GoTo` when accessing objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f9d1-123">備註</span><span class="sxs-lookup"><span data-stu-id="4f9d1-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f9d1-124">我們建議您使用結構化例外狀況處理，可能的話，程式碼中的，而不是使用非結構化例外狀況處理和`On Error`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-124">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` statement.</span></span> <span data-ttu-id="4f9d1-125">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-125">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="4f9d1-126">"Enabled"的錯誤處理常式是會開啟`On Error`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-126">An "enabled" error handler is one that is turned on by an `On Error` statement.</span></span> <span data-ttu-id="4f9d1-127">「 作用中 」 的錯誤處理常式是啟用的處理常式，而且正在處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-127">An "active" error handler is an enabled handler that is in the process of handling an error.</span></span>  
  
 <span data-ttu-id="4f9d1-128">錯誤處理常式時，如果發生錯誤 (之間發生錯誤而`Resume`， `Exit Sub`， `Exit Function`，或`Exit Property`陳述式)，目前的程序錯誤處理常式無法處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-128">If an error occurs while an error handler is active (between the occurrence of the error and a `Resume`, `Exit Sub`, `Exit Function`, or `Exit Property` statement), the current procedure's error handler cannot handle the error.</span></span> <span data-ttu-id="4f9d1-129">控制權會傳回呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-129">Control returns to the calling procedure.</span></span>  
  
 <span data-ttu-id="4f9d1-130">如果呼叫的程序已啟用的錯誤處理常式，則會啟動以處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-130">If the calling procedure has an enabled error handler, it is activated to handle the error.</span></span> <span data-ttu-id="4f9d1-131">如果呼叫的程序錯誤處理常式也是使用中，控制權會傳回到先前的呼叫程序找到已啟用，但非作用中，錯誤處理常式之前。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-131">If the calling procedure's error handler is also active, control passes back through previous calling procedures until an enabled, but inactive, error handler is found.</span></span> <span data-ttu-id="4f9d1-132">如果找到這類錯誤處理常式，就是它實際發生的點嚴重的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-132">If no such error handler is found, the error is fatal at the point at which it actually occurred.</span></span>  
  
 <span data-ttu-id="4f9d1-133">錯誤處理常式會將控制項傳遞至呼叫的程序中，每次該程序會成為目前的程序。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-133">Each time the error handler passes control back to a calling procedure, that procedure becomes the current procedure.</span></span> <span data-ttu-id="4f9d1-134">一旦處理錯誤，錯誤處理常式中的任何程序，在目前的程序中所指定的點就會繼續執行`Resume`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-134">Once an error is handled by an error handler in any procedure, execution resumes in the current procedure at the point designated by the `Resume` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f9d1-135">錯誤處理常式不是`Sub`程序或`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-135">An error-handling routine is not a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="4f9d1-136">它是一段程式碼所標記的行標籤或行號。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-136">It is a section of code marked by a line label or a line number.</span></span>  
  
## <a name="number-property"></a><span data-ttu-id="4f9d1-137">Number 屬性</span><span class="sxs-lookup"><span data-stu-id="4f9d1-137">Number Property</span></span>  
 <span data-ttu-id="4f9d1-138">錯誤處理常式依賴中的值`Number`屬性`Err`物件，以判斷錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-138">Error-handling routines rely on the value in the `Number` property of the `Err` object to determine the cause of the error.</span></span> <span data-ttu-id="4f9d1-139">此常式應該測試或儲存在相關的屬性值`Err`物件就會發生任何其他錯誤，或可能會導致程序之前的錯誤稱為之前。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-139">The routine should test or save relevant property values in the `Err` object before any other error can occur or before a procedure that might cause an error is called.</span></span> <span data-ttu-id="4f9d1-140">屬性值在`Err`物件會反映最近的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-140">The property values in the `Err` object reflect only the most recent error.</span></span> <span data-ttu-id="4f9d1-141">錯誤訊息相關聯`Err.Number`包含於`Err.Description`。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-141">The error message associated with `Err.Number` is contained in `Err.Description`.</span></span>  
  
## <a name="throw-statement"></a><span data-ttu-id="4f9d1-142">Throw 陳述式</span><span class="sxs-lookup"><span data-stu-id="4f9d1-142">Throw Statement</span></span>  
 <span data-ttu-id="4f9d1-143">引發錯誤`Err.Raise`方法會設定`Exception`新建立的執行個體的屬性<xref:System.Exception>類別。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-143">An error that is raised with the `Err.Raise` method sets the `Exception` property to a newly created instance of the <xref:System.Exception> class.</span></span> <span data-ttu-id="4f9d1-144">為了支援在引發例外狀況的衍生的例外狀況類型、`Throw`語言支援陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-144">In order to support the raising of exceptions of derived exception types, a `Throw` statement is supported in the language.</span></span> <span data-ttu-id="4f9d1-145">這會採用單一參數，會擲回的例外狀況執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-145">This takes a single parameter that is the exception instance to be thrown.</span></span> <span data-ttu-id="4f9d1-146">下列範例會示範如何使用這些功能，與現有的例外狀況處理支援：</span><span class="sxs-lookup"><span data-stu-id="4f9d1-146">The following example shows how these features can be used with the existing exception handling support:</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 <span data-ttu-id="4f9d1-147">請注意，`On Error GoTo`陳述式的設陷不論例外狀況類別的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-147">Notice that the `On Error GoTo` statement traps all errors, regardless of the exception class.</span></span>  
  
## <a name="on-error-resume-next"></a><span data-ttu-id="4f9d1-148">On Error Resume Next</span><span class="sxs-lookup"><span data-stu-id="4f9d1-148">On Error Resume Next</span></span>  
 <span data-ttu-id="4f9d1-149">`On Error Resume Next`導致執行動作繼續緊接造成執行階段錯誤的陳述式的陳述式，或緊接的最新的陳述式呼叫從程序包含`On Error Resume Next`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-149">`On Error Resume Next` causes execution to continue with the statement immediately following the statement that caused the run-time error, or with the statement immediately following the most recent call out of the procedure containing the `On Error Resume Next` statement.</span></span> <span data-ttu-id="4f9d1-150">這個陳述式可讓您忽略執行階段錯誤繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-150">This statement allows execution to continue despite a run-time error.</span></span> <span data-ttu-id="4f9d1-151">您可以將錯誤處理常式就會發生錯誤，而不會將控制權傳輸至另一個程序內的位置。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-151">You can place the error-handling routine where the error would occur rather than transferring control to another location within the procedure.</span></span> <span data-ttu-id="4f9d1-152">`On Error Resume Next`陳述式變成非作用中呼叫另一個程序時，因此，您應該執行`On Error Resume Next`中每個陳述式呼叫常式，如果您想要內嵌錯誤處理該常式內。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-152">An `On Error Resume Next` statement becomes inactive when another procedure is called, so you should execute an `On Error Resume Next` statement in each called routine if you want inline error handling within that routine.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f9d1-153">`On Error Resume Next`建構可能會比`On Error GoTo`處理其他物件的存取權期間所產生的錯誤時。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-153">The `On Error Resume Next` construct may be preferable to `On Error GoTo` when handling errors generated during access to other objects.</span></span> <span data-ttu-id="4f9d1-154">檢查`Err`之後每個互動的物件移除的物件存取的程式碼的模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-154">Checking `Err` after each interaction with an object removes ambiguity about which object was accessed by the code.</span></span> <span data-ttu-id="4f9d1-155">您可以確定哪一個物件放在錯誤碼`Err.Number`，以及哪些物件最初產生的錯誤 (中指定的物件`Err.Source`)。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-155">You can be sure which object placed the error code in `Err.Number`, as well as which object originally generated the error (the object specified in `Err.Source`).</span></span>  
  
## <a name="on-error-goto-0"></a><span data-ttu-id="4f9d1-156">On Error GoTo 0</span><span class="sxs-lookup"><span data-stu-id="4f9d1-156">On Error GoTo 0</span></span>  
 <span data-ttu-id="4f9d1-157">`On Error GoTo 0`停用目前的程序中的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-157">`On Error GoTo 0` disables error handling in the current procedure.</span></span> <span data-ttu-id="4f9d1-158">它不會作為的錯誤處理程式碼中，指定第 0 行，即使程序包含行號 0。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-158">It doesn't specify line 0 as the start of the error-handling code, even if the procedure contains a line numbered 0.</span></span> <span data-ttu-id="4f9d1-159">不含`On Error GoTo 0`陳述式中，錯誤處理常式會自動停用程序結束時。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-159">Without an `On Error GoTo 0` statement, an error handler is automatically disabled when a procedure is exited.</span></span>  
  
## <a name="on-error-goto--1"></a><span data-ttu-id="4f9d1-160">On Error GoTo-1</span><span class="sxs-lookup"><span data-stu-id="4f9d1-160">On Error GoTo -1</span></span>  
 <span data-ttu-id="4f9d1-161">`On Error GoTo -1`停用目前的程序中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-161">`On Error GoTo -1` disables the exception in the current procedure.</span></span> <span data-ttu-id="4f9d1-162">它未指定行-1 開始的錯誤處理程式碼，即使此程序包含行號-1。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-162">It does not specify line -1 as the start of the error-handling code, even if the procedure contains a line numbered -1.</span></span> <span data-ttu-id="4f9d1-163">不含`On Error GoTo -1`陳述式中，例外狀況會自動停用程序結束時。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-163">Without an `On Error GoTo -1` statement, an exception is automatically disabled when a procedure is exited.</span></span>  
  
 <span data-ttu-id="4f9d1-164">若要防止錯誤處理程式碼執行時沒有發生任何錯誤，加上`Exit Sub`， `Exit Function`，或`Exit Property`陳述式之前的錯誤處理常式，如下列片段所示：</span><span class="sxs-lookup"><span data-stu-id="4f9d1-164">To prevent error-handling code from running when no error has occurred, place an `Exit Sub`, `Exit Function`, or `Exit Property` statement immediately before the error-handling routine, as in the following fragment:</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 <span data-ttu-id="4f9d1-165">錯誤處理程式碼會遵循此處`Exit Sub`陳述式，而且前面出現`End Sub`分開的程序流程的陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-165">Here, the error-handling code follows the `Exit Sub` statement and precedes the `End Sub` statement to separate it from the procedure flow.</span></span> <span data-ttu-id="4f9d1-166">您可以在程序的任意位置放置錯誤處理程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-166">You can place error-handling code anywhere in a procedure.</span></span>  
  
## <a name="untrapped-errors"></a><span data-ttu-id="4f9d1-167">設陷的錯誤</span><span class="sxs-lookup"><span data-stu-id="4f9d1-167">Untrapped Errors</span></span>  
 <span data-ttu-id="4f9d1-168">物件的可執行檔以執行時，物件中的設陷的錯誤會傳回控制的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-168">Untrapped errors in objects are returned to the controlling application when the object is running as an executable file.</span></span> <span data-ttu-id="4f9d1-169">在開發環境中，未設陷的錯誤會傳回控制應用程式必須設定適當的選項。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-169">Within the development environment, untrapped errors are returned to the controlling application only if the proper options are set.</span></span> <span data-ttu-id="4f9d1-170">參閱主應用程式的文件選項都應該是設定在偵錯、 如何設定它們，和主機是否可以建立類別的描述。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-170">See your host application's documentation for a description of which options should be set during debugging, how to set them, and whether the host can create classes.</span></span>  
  
 <span data-ttu-id="4f9d1-171">如果您建立存取其他物件的物件，您應該嘗試處理傳遞回任何未處理的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-171">If you create an object that accesses other objects, you should try to handle any unhandled errors they pass back.</span></span> <span data-ttu-id="4f9d1-172">如果您不能對應中的錯誤代碼`Err.Number`您自己的錯誤，然後階段的其中一個送回給呼叫者的物件。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-172">If you cannot, map the error codes in `Err.Number` to one of your own errors and then pass them back to the caller of your object.</span></span> <span data-ttu-id="4f9d1-173">您應該加入您錯誤的程式碼，以指定您的錯誤`VbObjectError`常數。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-173">You should specify your error by adding your error code to the `VbObjectError` constant.</span></span> <span data-ttu-id="4f9d1-174">例如，如果您的錯誤代碼是 1052年，將它指派，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4f9d1-174">For example, if your error code is 1052, assign it as follows:</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  <span data-ttu-id="4f9d1-175">系統 Windows 動態連結程式庫 (Dll) 的呼叫期間發生的錯誤不會引發例外狀況，並不能與 Visual Basic 錯誤截取截取。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-175">System errors during calls to Windows dynamic-link libraries (DLLs) do not raise exceptions and cannot be trapped with Visual Basic error trapping.</span></span> <span data-ttu-id="4f9d1-176">在呼叫 DLL 函式時，您應該檢查成功或失敗 （根據應用程式開發介面規格），每個傳回值，萬一故障，請檢查值`Err`物件的`LastDLLError`屬性。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-176">When calling DLL functions, you should check each return value for success or failure (according to the API specifications), and in the event of a failure, check the value in the `Err` object's `LastDLLError` property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f9d1-177">範例</span><span class="sxs-lookup"><span data-stu-id="4f9d1-177">Example</span></span>  
 <span data-ttu-id="4f9d1-178">這個範例會先使用`On Error GoTo`陳述式來指定的錯誤處理常式的程序內的位置。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-178">This example first uses the `On Error GoTo` statement to specify the location of an error-handling routine within a procedure.</span></span> <span data-ttu-id="4f9d1-179">在範例中，嘗試除以零會產生錯誤的數字 6。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-179">In the example, an attempt to divide by zero generates error number 6.</span></span> <span data-ttu-id="4f9d1-180">在錯誤處理常式中，處理錯誤，然後將控制權傳回給造成錯誤的陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-180">The error is handled in the error-handling routine, and control is then returned to the statement that caused the error.</span></span> <span data-ttu-id="4f9d1-181">`On Error GoTo 0`陳述式會關閉錯誤設陷。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-181">The `On Error GoTo 0` statement turns off error trapping.</span></span> <span data-ttu-id="4f9d1-182">然後在`On Error Resume Next`陳述式用來延遲錯誤捕捉使某些已知的內容下一個陳述式所產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-182">Then the `On Error Resume Next` statement is used to defer error trapping so that the context for the error generated by the next statement can be known for certain.</span></span> <span data-ttu-id="4f9d1-183">請注意，`Err.Clear`用來清除`Err`錯誤處理之後，物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="4f9d1-183">Note that `Err.Clear` is used to clear the `Err` object's properties after the error is handled.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="4f9d1-184">需求</span><span class="sxs-lookup"><span data-stu-id="4f9d1-184">Requirements</span></span>  
 <span data-ttu-id="4f9d1-185">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="4f9d1-185">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="4f9d1-186">**組件：** Visual Basic Runtime Library （位於 Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="4f9d1-186">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f9d1-187">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f9d1-187">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [<span data-ttu-id="4f9d1-188">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="4f9d1-188">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="4f9d1-189">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="4f9d1-189">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="4f9d1-190">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="4f9d1-190">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="4f9d1-191">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="4f9d1-191">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)  
 [<span data-ttu-id="4f9d1-192">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="4f9d1-192">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
