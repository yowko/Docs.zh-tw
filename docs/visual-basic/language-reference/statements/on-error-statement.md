---
title: On Error 陳述式
ms.date: 07/20/2015
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
ms.openlocfilehash: 7e007d59292fc577c0c8927766423ba6f7896a71
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873185"
---
# <a name="on-error-statement-visual-basic"></a><span data-ttu-id="a4bd9-102">On Error 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4bd9-102">On Error Statement (Visual Basic)</span></span>

<span data-ttu-id="a4bd9-103">啟用錯誤處理常式，並在程式內指定常式的位置;也可以用來停用錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-103">Enables an error-handling routine and specifies the location of the routine within a procedure; can also be used to disable an error-handling routine.</span></span> <span data-ttu-id="a4bd9-104">`On Error`語句用於非結構化錯誤處理中，而且可以用來取代結構化例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-104">The `On Error` statement is used in unstructured error handling and can be used instead of structured exception handling.</span></span> <span data-ttu-id="a4bd9-105">[結構化例外狀況處理](../../../standard/exceptions/index.md) 內建于 .net 中，通常更有效率，而且在處理應用程式中的執行時間錯誤時，建議使用此方式。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-105">[Structured exception handling](../../../standard/exceptions/index.md) is built into .NET, is generally more efficient, and so is recommended when handling runtime errors in your application.</span></span>

 <span data-ttu-id="a4bd9-106">如果沒有錯誤處理或例外狀況處理，任何發生的執行階段錯誤都是嚴重的：顯示錯誤訊息，並停止執行。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-106">Without error handling or exception handling, any run-time error that occurs is fatal: an error message is displayed, and execution stops.</span></span>

> [!NOTE]
> <span data-ttu-id="a4bd9-107">`Error`關鍵字也會用於[錯誤語句](error-statement.md)，以提供回溯相容性支援。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-107">The `Error` keyword is also used in the [Error Statement](error-statement.md), which is supported for backward compatibility.</span></span>

## <a name="syntax"></a><span data-ttu-id="a4bd9-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4bd9-108">Syntax</span></span>

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a><span data-ttu-id="a4bd9-109">組件</span><span class="sxs-lookup"><span data-stu-id="a4bd9-109">Parts</span></span>

|<span data-ttu-id="a4bd9-110">詞彙</span><span class="sxs-lookup"><span data-stu-id="a4bd9-110">Term</span></span>|<span data-ttu-id="a4bd9-111">定義</span><span class="sxs-lookup"><span data-stu-id="a4bd9-111">Definition</span></span>|
|---|---|
|<span data-ttu-id="a4bd9-112">`GoTo`*行*</span><span class="sxs-lookup"><span data-stu-id="a4bd9-112">`GoTo` *line*</span></span>|<span data-ttu-id="a4bd9-113">啟用在必要 *行* 引數中指定的行開始的錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-113">Enables the error-handling routine that starts at the line specified in the required *line* argument.</span></span> <span data-ttu-id="a4bd9-114">*Line*引數是任何行標籤或行號。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-114">The *line* argument is any line label or line number.</span></span> <span data-ttu-id="a4bd9-115">如果發生執行階段錯誤，請將分支控制到指定的行，使錯誤處理常式成為使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-115">If a run-time error occurs, control branches to the specified line, making the error handler active.</span></span> <span data-ttu-id="a4bd9-116">指定的行必須與語句位於相同的程式中， `On Error` 否則會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-116">The specified line must be in the same procedure as the `On Error` statement or a compile-time error will occur.</span></span>|
|`GoTo 0`|<span data-ttu-id="a4bd9-117">在目前程式中停用已啟用的錯誤處理常式，並將它重設為 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-117">Disables enabled error handler in the current procedure and resets it to `Nothing`.</span></span>|
|`GoTo -1`|<span data-ttu-id="a4bd9-118">在目前的程式中停用已啟用的例外狀況，並將其重設為 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-118">Disables enabled exception in the current procedure and resets it to `Nothing`.</span></span>|
|`Resume Next`|<span data-ttu-id="a4bd9-119">指定當執行階段錯誤發生時，控制權會移至緊接在發生錯誤的語句之後的語句，並從該點繼續執行。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-119">Specifies that when a run-time error occurs, control goes to the statement immediately following the statement where the error occurred, and execution continues from that point.</span></span> <span data-ttu-id="a4bd9-120">`On Error GoTo`當您存取物件時，請使用此表單而不是。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-120">Use this form rather than `On Error GoTo` when accessing objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a4bd9-121">備註</span><span class="sxs-lookup"><span data-stu-id="a4bd9-121">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="a4bd9-122">建議您盡可能在程式碼中使用結構化例外狀況處理，而不是使用非結構化例外狀況處理和 `On Error` 語句。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-122">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` statement.</span></span> <span data-ttu-id="a4bd9-123">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-123">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>

 <span data-ttu-id="a4bd9-124">「已啟用」錯誤處理常式是由語句開啟的錯誤處理常式 `On Error` 。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-124">An "enabled" error handler is one that is turned on by an `On Error` statement.</span></span> <span data-ttu-id="a4bd9-125">「作用中」錯誤處理常式是在處理錯誤的處理常式中啟用的處理常式。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-125">An "active" error handler is an enabled handler that is in the process of handling an error.</span></span>

 <span data-ttu-id="a4bd9-126">如果錯誤處理常式在發生錯誤時 (發生錯誤，以及) 發生的 `Resume` 、、 `Exit Sub` `Exit Function` 或 `Exit Property` 語句之間，則目前的程式錯誤處理常式無法處理此錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-126">If an error occurs while an error handler is active (between the occurrence of the error and a `Resume`, `Exit Sub`, `Exit Function`, or `Exit Property` statement), the current procedure's error handler cannot handle the error.</span></span> <span data-ttu-id="a4bd9-127">控制權會返回呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-127">Control returns to the calling procedure.</span></span>
  
 <span data-ttu-id="a4bd9-128">如果呼叫的程式有已啟用的錯誤處理常式，則會啟用它來處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-128">If the calling procedure has an enabled error handler, it is activated to handle the error.</span></span> <span data-ttu-id="a4bd9-129">如果呼叫程式的錯誤處理常式也在使用中，控制權會透過先前的呼叫程式回傳，直到找到已啟用但非使用中的錯誤處理常式為止。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-129">If the calling procedure's error handler is also active, control passes back through previous calling procedures until an enabled, but inactive, error handler is found.</span></span> <span data-ttu-id="a4bd9-130">如果找不到這類錯誤處理常式，則錯誤會在實際發生的位置發生嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-130">If no such error handler is found, the error is fatal at the point at which it actually occurred.</span></span>
  
 <span data-ttu-id="a4bd9-131">每當錯誤處理常式將控制權傳遞回呼叫程式時，該程式就會變成目前的程式。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-131">Each time the error handler passes control back to a calling procedure, that procedure becomes the current procedure.</span></span> <span data-ttu-id="a4bd9-132">一旦任何程式中的錯誤處理常式處理錯誤，就會在語句指定的點，于目前的程式中繼續執行 `Resume` 。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-132">Once an error is handled by an error handler in any procedure, execution resumes in the current procedure at the point designated by the `Resume` statement.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a4bd9-133">錯誤處理常式不是程式或程式 `Sub` `Function` 。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-133">An error-handling routine is not a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="a4bd9-134">它是以行標籤或行號標記的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-134">It is a section of code marked by a line label or a line number.</span></span>
  
## <a name="number-property"></a><span data-ttu-id="a4bd9-135">Number 屬性</span><span class="sxs-lookup"><span data-stu-id="a4bd9-135">Number Property</span></span>

 <span data-ttu-id="a4bd9-136">錯誤處理常式依賴 `Number` 物件的屬性值 `Err` 來判斷錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-136">Error-handling routines rely on the value in the `Number` property of the `Err` object to determine the cause of the error.</span></span> <span data-ttu-id="a4bd9-137">常式應該先測試或儲存物件中的相關屬性值， `Err` 然後再發生任何其他錯誤，或呼叫可能造成錯誤的程式之前。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-137">The routine should test or save relevant property values in the `Err` object before any other error can occur or before a procedure that might cause an error is called.</span></span> <span data-ttu-id="a4bd9-138">物件中的屬性值 `Err` 只會反映最新的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-138">The property values in the `Err` object reflect only the most recent error.</span></span> <span data-ttu-id="a4bd9-139">與相關聯的錯誤訊息 `Err.Number` 包含在中 `Err.Description` 。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-139">The error message associated with `Err.Number` is contained in `Err.Description`.</span></span>  
  
## <a name="throw-statement"></a><span data-ttu-id="a4bd9-140">Throw 陳述式</span><span class="sxs-lookup"><span data-stu-id="a4bd9-140">Throw Statement</span></span>  

 <span data-ttu-id="a4bd9-141">以方法引發的錯誤，會 `Err.Raise` 將屬性設定 `Exception` 為類別的新建立實例 <xref:System.Exception> 。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-141">An error that is raised with the `Err.Raise` method sets the `Exception` property to a newly created instance of the <xref:System.Exception> class.</span></span> <span data-ttu-id="a4bd9-142">為了支援引發衍生例外狀況類型的例外狀況， `Throw` 語言支援語句。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-142">In order to support the raising of exceptions of derived exception types, a `Throw` statement is supported in the language.</span></span> <span data-ttu-id="a4bd9-143">這會採用單一參數，此參數是要擲回的例外狀況實例。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-143">This takes a single parameter that is the exception instance to be thrown.</span></span> <span data-ttu-id="a4bd9-144">下列範例顯示如何搭配現有的例外狀況處理支援來使用這些功能：</span><span class="sxs-lookup"><span data-stu-id="a4bd9-144">The following example shows how these features can be used with the existing exception handling support:</span></span>

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 <span data-ttu-id="a4bd9-145">請注意， `On Error GoTo` 不論例外狀況類別為何，語句都會捕捉所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-145">Notice that the `On Error GoTo` statement traps all errors, regardless of the exception class.</span></span>
  
## <a name="on-error-resume-next"></a><span data-ttu-id="a4bd9-146">On Error Resume Next</span><span class="sxs-lookup"><span data-stu-id="a4bd9-146">On Error Resume Next</span></span>

 <span data-ttu-id="a4bd9-147">`On Error Resume Next` 使執行繼續使用緊接在引發執行階段錯誤的語句後面的語句，或使用緊接在包含語句之程式的最新呼叫之後的語句 `On Error Resume Next` 。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-147">`On Error Resume Next` causes execution to continue with the statement immediately following the statement that caused the run-time error, or with the statement immediately following the most recent call out of the procedure containing the `On Error Resume Next` statement.</span></span> <span data-ttu-id="a4bd9-148">這個語句可讓您在執行階段錯誤時繼續執行。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-148">This statement allows execution to continue despite a run-time error.</span></span> <span data-ttu-id="a4bd9-149">您可以將錯誤處理常式放在發生錯誤的位置，而不是將控制項傳送至程式內的另一個位置。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-149">You can place the error-handling routine where the error would occur rather than transferring control to another location within the procedure.</span></span> <span data-ttu-id="a4bd9-150">`On Error Resume Next`當呼叫另一個程式時，語句會變成非使用中狀態，因此， `On Error Resume Next` 如果您想要在該常式內內嵌錯誤處理，請在每個呼叫的常式中執行語句。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-150">An `On Error Resume Next` statement becomes inactive when another procedure is called, so you should execute an `On Error Resume Next` statement in each called routine if you want inline error handling within that routine.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a4bd9-151">在 `On Error Resume Next` `On Error GoTo` 處理存取其他物件時所產生的錯誤時，最好使用此結構。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-151">The `On Error Resume Next` construct may be preferable to `On Error GoTo` when handling errors generated during access to other objects.</span></span> <span data-ttu-id="a4bd9-152">`Err`在每次與物件互動之後進行檢查，都不會對程式碼所存取的物件造成混淆。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-152">Checking `Err` after each interaction with an object removes ambiguity about which object was accessed by the code.</span></span> <span data-ttu-id="a4bd9-153">您可以確定哪個物件放入錯誤碼 `Err.Number` ，以及哪個物件最初產生的錯誤 () 中指定的物件 `Err.Source` 。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-153">You can be sure which object placed the error code in `Err.Number`, as well as which object originally generated the error (the object specified in `Err.Source`).</span></span>

## <a name="on-error-goto-0"></a><span data-ttu-id="a4bd9-154">On Error GoTo 0</span><span class="sxs-lookup"><span data-stu-id="a4bd9-154">On Error GoTo 0</span></span>

 <span data-ttu-id="a4bd9-155">`On Error GoTo 0` 停用目前程式中的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-155">`On Error GoTo 0` disables error handling in the current procedure.</span></span> <span data-ttu-id="a4bd9-156">它不會將第0行指定為錯誤處理常式代碼的開頭，即使套裝程式含編號為0的行。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-156">It doesn't specify line 0 as the start of the error-handling code, even if the procedure contains a line numbered 0.</span></span> <span data-ttu-id="a4bd9-157">如果沒有 `On Error GoTo 0` 語句，則會在程式結束時自動停用錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-157">Without an `On Error GoTo 0` statement, an error handler is automatically disabled when a procedure is exited.</span></span>

## <a name="on-error-goto--1"></a><span data-ttu-id="a4bd9-158">錯誤 GoTo-1</span><span class="sxs-lookup"><span data-stu-id="a4bd9-158">On Error GoTo -1</span></span>

 <span data-ttu-id="a4bd9-159">`On Error GoTo -1` 停用目前程式中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-159">`On Error GoTo -1` disables the exception in the current procedure.</span></span> <span data-ttu-id="a4bd9-160">它不會指定行1做為錯誤處理常式代碼的開頭，即使套裝程式含編號1的行。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-160">It does not specify line -1 as the start of the error-handling code, even if the procedure contains a line numbered -1.</span></span> <span data-ttu-id="a4bd9-161">如果沒有 `On Error GoTo -1` 語句，則會在程式結束時自動停用例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-161">Without an `On Error GoTo -1` statement, an exception is automatically disabled when a procedure is exited.</span></span>

 <span data-ttu-id="a4bd9-162">若要避免在未發生錯誤時執行錯誤處理常式代碼，請 `Exit Sub` `Exit Function` `Exit Property` 在錯誤處理常式之前放置、或語句，如下列片段所示：</span><span class="sxs-lookup"><span data-stu-id="a4bd9-162">To prevent error-handling code from running when no error has occurred, place an `Exit Sub`, `Exit Function`, or `Exit Property` statement immediately before the error-handling routine, as in the following fragment:</span></span>

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 <span data-ttu-id="a4bd9-163">在此，錯誤處理常式代碼會遵循 `Exit Sub` 語句，並在 `End Sub` 語句之前，將它與程式流程分開。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-163">Here, the error-handling code follows the `Exit Sub` statement and precedes the `End Sub` statement to separate it from the procedure flow.</span></span> <span data-ttu-id="a4bd9-164">您可以將錯誤處理常式代碼放在程式中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-164">You can place error-handling code anywhere in a procedure.</span></span>

## <a name="untrapped-errors"></a><span data-ttu-id="a4bd9-165">未被截取錯誤</span><span class="sxs-lookup"><span data-stu-id="a4bd9-165">Untrapped Errors</span></span>

 <span data-ttu-id="a4bd9-166">當物件做為可執行檔執行時，物件中的未被截取錯誤會傳回至控制應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-166">Untrapped errors in objects are returned to the controlling application when the object is running as an executable file.</span></span> <span data-ttu-id="a4bd9-167">在開發環境內，只有在設定適當的選項時，才會將未被截取錯誤傳回給控制應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-167">Within the development environment, untrapped errors are returned to the controlling application only if the proper options are set.</span></span> <span data-ttu-id="a4bd9-168">請參閱您的主應用程式檔，以取得在偵錯工具期間應設定哪些選項、如何設定它們，以及主機是否可以建立類別的說明。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-168">See your host application's documentation for a description of which options should be set during debugging, how to set them, and whether the host can create classes.</span></span>

 <span data-ttu-id="a4bd9-169">如果您建立可存取其他物件的物件，您應該嘗試處理傳回的任何未處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-169">If you create an object that accesses other objects, you should try to handle any unhandled errors they pass back.</span></span> <span data-ttu-id="a4bd9-170">如果您無法這樣做，請將錯誤碼對應 `Err.Number` 至您自己的其中一個錯誤，然後將它們傳遞回物件的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-170">If you cannot, map the error codes in `Err.Number` to one of your own errors and then pass them back to the caller of your object.</span></span> <span data-ttu-id="a4bd9-171">您應該將您的錯誤碼新增至常數來指定錯誤 `VbObjectError` 。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-171">You should specify your error by adding your error code to the `VbObjectError` constant.</span></span> <span data-ttu-id="a4bd9-172">例如，如果您的錯誤碼為1052，請將其指派如下：</span><span class="sxs-lookup"><span data-stu-id="a4bd9-172">For example, if your error code is 1052, assign it as follows:</span></span>

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> <span data-ttu-id="a4bd9-173">呼叫 Windows 動態連結程式庫時的系統錯誤 (Dll) 不會引發例外狀況，而且無法在 Visual Basic 錯誤捕捉時加以攔截。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-173">System errors during calls to Windows dynamic-link libraries (DLLs) do not raise exceptions and cannot be trapped with Visual Basic error trapping.</span></span> <span data-ttu-id="a4bd9-174">呼叫 DLL 函式時，您應該根據) 的 API 規格來檢查每個成功或失敗 (的傳回值，而在發生失敗的情況下，請檢查 `Err` 物件的 `LastDLLError` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-174">When calling DLL functions, you should check each return value for success or failure (according to the API specifications), and in the event of a failure, check the value in the `Err` object's `LastDLLError` property.</span></span>

## <a name="example"></a><span data-ttu-id="a4bd9-175">範例</span><span class="sxs-lookup"><span data-stu-id="a4bd9-175">Example</span></span>

 <span data-ttu-id="a4bd9-176">此範例會先使用 `On Error GoTo` 語句來指定程式中錯誤處理常式的位置。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-176">This example first uses the `On Error GoTo` statement to specify the location of an error-handling routine within a procedure.</span></span> <span data-ttu-id="a4bd9-177">在此範例中，零除的嘗試會產生錯誤號碼6。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-177">In the example, an attempt to divide by zero generates error number 6.</span></span> <span data-ttu-id="a4bd9-178">錯誤會在錯誤處理常式中處理，然後控制權會傳回給造成錯誤的語句。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-178">The error is handled in the error-handling routine, and control is then returned to the statement that caused the error.</span></span> <span data-ttu-id="a4bd9-179">`On Error GoTo 0`語句會關閉錯誤捕捉。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-179">The `On Error GoTo 0` statement turns off error trapping.</span></span> <span data-ttu-id="a4bd9-180">然後 `On Error Resume Next` 語句會用來延遲錯誤捕捉，讓下一個語句所產生之錯誤的內容可以知道。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-180">Then the `On Error Resume Next` statement is used to defer error trapping so that the context for the error generated by the next statement can be known for certain.</span></span> <span data-ttu-id="a4bd9-181">請注意，這 `Err.Clear` 是在 `Err` 處理錯誤之後用來清除物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="a4bd9-181">Note that `Err.Clear` is used to clear the `Err` object's properties after the error is handled.</span></span>

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a><span data-ttu-id="a4bd9-182">規格需求</span><span class="sxs-lookup"><span data-stu-id="a4bd9-182">Requirements</span></span>

 <span data-ttu-id="a4bd9-183">**命名空間：** [Microsoft.](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="a4bd9-183">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>

 <span data-ttu-id="a4bd9-184">**元件：** Microsoft.VisualBasic.dll) 中的 Visual Basic 執行時間程式庫 (</span><span class="sxs-lookup"><span data-stu-id="a4bd9-184">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>

## <a name="see-also"></a><span data-ttu-id="a4bd9-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4bd9-185">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [<span data-ttu-id="a4bd9-186">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="a4bd9-186">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="a4bd9-187">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="a4bd9-187">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="a4bd9-188">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="a4bd9-188">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="a4bd9-189">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="a4bd9-189">Error Messages</span></span>](../error-messages/index.md)
- [<span data-ttu-id="a4bd9-190">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="a4bd9-190">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
