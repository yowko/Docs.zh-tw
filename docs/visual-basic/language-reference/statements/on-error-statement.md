---
title: On Error 陳述式 (Visual Basic)
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
ms.openlocfilehash: 4474b217147aca74f2c6e5376c8f55318a05bf4a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046506"
---
# <a name="on-error-statement-visual-basic"></a><span data-ttu-id="b083a-102">On Error 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b083a-102">On Error Statement (Visual Basic)</span></span>
<span data-ttu-id="b083a-103">啟用錯誤處理常式, 並在程式中指定常式的位置;也可以用來停用錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="b083a-103">Enables an error-handling routine and specifies the location of the routine within a procedure; can also be used to disable an error-handling routine.</span></span> <span data-ttu-id="b083a-104">`On Error`語句用於非結構化錯誤處理中, 而且可以用來取代結構化例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="b083a-104">The `On Error` statement is used in unstructured error handling and can be used instead of structured exception handling.</span></span> <span data-ttu-id="b083a-105">[結構化例外狀況處理](../../../standard/exceptions/index.md)內建于 .net 中, 通常更有效率, 而且在處理應用程式中的執行階段錯誤時建議使用。</span><span class="sxs-lookup"><span data-stu-id="b083a-105">[Structured exception handling](../../../standard/exceptions/index.md) is built into .NET, is generally more efficient, and so is recommended when handling runtime errors in your application.</span></span>

 <span data-ttu-id="b083a-106">如果沒有錯誤處理或例外狀況處理, 則發生的任何執行階段錯誤都是嚴重的: 會顯示錯誤訊息, 並停止執行。</span><span class="sxs-lookup"><span data-stu-id="b083a-106">Without error handling or exception handling, any run-time error that occurs is fatal: an error message is displayed, and execution stops.</span></span>

> [!NOTE]
> <span data-ttu-id="b083a-107">關鍵字也用於[Error 語句](../../../visual-basic/language-reference/statements/error-statement.md), 這是為了回溯相容性所支援的。 `Error`</span><span class="sxs-lookup"><span data-stu-id="b083a-107">The `Error` keyword is also used in the [Error Statement](../../../visual-basic/language-reference/statements/error-statement.md), which is supported for backward compatibility.</span></span>

## <a name="syntax"></a><span data-ttu-id="b083a-108">語法</span><span class="sxs-lookup"><span data-stu-id="b083a-108">Syntax</span></span>

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a><span data-ttu-id="b083a-109">組件</span><span class="sxs-lookup"><span data-stu-id="b083a-109">Parts</span></span>

|<span data-ttu-id="b083a-110">詞彙</span><span class="sxs-lookup"><span data-stu-id="b083a-110">Term</span></span>|<span data-ttu-id="b083a-111">定義</span><span class="sxs-lookup"><span data-stu-id="b083a-111">Definition</span></span>|
|---|---|
|<span data-ttu-id="b083a-112">`GoTo`*行*</span><span class="sxs-lookup"><span data-stu-id="b083a-112">`GoTo` *line*</span></span>|<span data-ttu-id="b083a-113">啟用在必要*行*引數中指定的行開始的錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="b083a-113">Enables the error-handling routine that starts at the line specified in the required *line* argument.</span></span> <span data-ttu-id="b083a-114">*Line*引數是任何行標籤或行號。</span><span class="sxs-lookup"><span data-stu-id="b083a-114">The *line* argument is any line label or line number.</span></span> <span data-ttu-id="b083a-115">如果發生執行階段錯誤, 請將分支控制到指定的行, 使錯誤處理常式變成作用中。</span><span class="sxs-lookup"><span data-stu-id="b083a-115">If a run-time error occurs, control branches to the specified line, making the error handler active.</span></span> <span data-ttu-id="b083a-116">指定的行必須與`On Error`語句位於相同的程式中, 否則會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="b083a-116">The specified line must be in the same procedure as the `On Error` statement or a compile-time error will occur.</span></span>|
|`GoTo 0`|<span data-ttu-id="b083a-117">停用目前程式中已啟用的錯誤處理常式, `Nothing`並將它重設為。</span><span class="sxs-lookup"><span data-stu-id="b083a-117">Disables enabled error handler in the current procedure and resets it to `Nothing`.</span></span>|
|`GoTo -1`|<span data-ttu-id="b083a-118">停用目前程式中已啟用的例外狀況, `Nothing`並將它重設為。</span><span class="sxs-lookup"><span data-stu-id="b083a-118">Disables enabled exception in the current procedure and resets it to `Nothing`.</span></span>|
|`Resume Next`|<span data-ttu-id="b083a-119">指定發生執行階段錯誤時, 控制權會移至緊接在發生錯誤的語句之後的語句, 並從該點繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b083a-119">Specifies that when a run-time error occurs, control goes to the statement immediately following the statement where the error occurred, and execution continues from that point.</span></span> <span data-ttu-id="b083a-120">`On Error GoTo`在存取物件時, 請使用此表單, 而不是。</span><span class="sxs-lookup"><span data-stu-id="b083a-120">Use this form rather than `On Error GoTo` when accessing objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b083a-121">備註</span><span class="sxs-lookup"><span data-stu-id="b083a-121">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="b083a-122">我們建議您盡可能在程式碼中使用結構化例外狀況處理, 而不是使用非結構化`On Error`例外狀況處理和語句。</span><span class="sxs-lookup"><span data-stu-id="b083a-122">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` statement.</span></span> <span data-ttu-id="b083a-123">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b083a-123">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>

 <span data-ttu-id="b083a-124">「已啟用」錯誤處理常式是由`On Error`語句開啟的。</span><span class="sxs-lookup"><span data-stu-id="b083a-124">An "enabled" error handler is one that is turned on by an `On Error` statement.</span></span> <span data-ttu-id="b083a-125">「作用中」錯誤處理常式是已啟用的處理常式, 正在處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="b083a-125">An "active" error handler is an enabled handler that is in the process of handling an error.</span></span>

 <span data-ttu-id="b083a-126">如果錯誤處理常式正在使用中時發生錯誤 (發生錯誤`Resume`和、 `Exit Sub`、 `Exit Function`或`Exit Property`語句), 則目前程式的錯誤處理常式無法處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="b083a-126">If an error occurs while an error handler is active (between the occurrence of the error and a `Resume`, `Exit Sub`, `Exit Function`, or `Exit Property` statement), the current procedure's error handler cannot handle the error.</span></span> <span data-ttu-id="b083a-127">控制項會回到呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="b083a-127">Control returns to the calling procedure.</span></span>
  
 <span data-ttu-id="b083a-128">如果呼叫程式具有已啟用的錯誤處理常式, 就會啟動以處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="b083a-128">If the calling procedure has an enabled error handler, it is activated to handle the error.</span></span> <span data-ttu-id="b083a-129">如果呼叫程式的錯誤處理常式也是作用中, 則控制權會透過先前的呼叫程式回傳, 直到找到已啟用但非使用中的錯誤處理常式為止。</span><span class="sxs-lookup"><span data-stu-id="b083a-129">If the calling procedure's error handler is also active, control passes back through previous calling procedures until an enabled, but inactive, error handler is found.</span></span> <span data-ttu-id="b083a-130">如果找不到這類錯誤處理常式, 則錯誤在實際發生的時間點是嚴重的。</span><span class="sxs-lookup"><span data-stu-id="b083a-130">If no such error handler is found, the error is fatal at the point at which it actually occurred.</span></span>
  
 <span data-ttu-id="b083a-131">每次錯誤處理常式將控制權回傳給呼叫的進程時, 該程式就會成為目前的程式。</span><span class="sxs-lookup"><span data-stu-id="b083a-131">Each time the error handler passes control back to a calling procedure, that procedure becomes the current procedure.</span></span> <span data-ttu-id="b083a-132">一旦任何程式中的錯誤處理常式處理錯誤之後, 就會在`Resume`語句所指定的目前程式中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b083a-132">Once an error is handled by an error handler in any procedure, execution resumes in the current procedure at the point designated by the `Resume` statement.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b083a-133">錯誤處理常式不是一個`Sub`程式`Function`或程式。</span><span class="sxs-lookup"><span data-stu-id="b083a-133">An error-handling routine is not a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="b083a-134">它是以線條標籤或行號標記的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="b083a-134">It is a section of code marked by a line label or a line number.</span></span>
  
## <a name="number-property"></a><span data-ttu-id="b083a-135">Number 屬性</span><span class="sxs-lookup"><span data-stu-id="b083a-135">Number Property</span></span>
 <span data-ttu-id="b083a-136">錯誤處理常式會依賴`Number` `Err`物件之屬性中的值, 以判斷錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="b083a-136">Error-handling routines rely on the value in the `Number` property of the `Err` object to determine the cause of the error.</span></span> <span data-ttu-id="b083a-137">常式應該先測試或儲存物件中的`Err`相關屬性值, 然後才會發生任何其他錯誤, 或呼叫可能造成錯誤的程式之前。</span><span class="sxs-lookup"><span data-stu-id="b083a-137">The routine should test or save relevant property values in the `Err` object before any other error can occur or before a procedure that might cause an error is called.</span></span> <span data-ttu-id="b083a-138">`Err`物件中的屬性值只會反映最近的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b083a-138">The property values in the `Err` object reflect only the most recent error.</span></span> <span data-ttu-id="b083a-139">與`Err.Number`相關聯的錯誤訊息包含在`Err.Description`中。</span><span class="sxs-lookup"><span data-stu-id="b083a-139">The error message associated with `Err.Number` is contained in `Err.Description`.</span></span>  
  
## <a name="throw-statement"></a><span data-ttu-id="b083a-140">Throw 陳述式</span><span class="sxs-lookup"><span data-stu-id="b083a-140">Throw Statement</span></span>  
 <span data-ttu-id="b083a-141">以`Err.Raise`方法引發的錯誤會`Exception`將屬性設定為<xref:System.Exception>類別的新建立實例。</span><span class="sxs-lookup"><span data-stu-id="b083a-141">An error that is raised with the `Err.Raise` method sets the `Exception` property to a newly created instance of the <xref:System.Exception> class.</span></span> <span data-ttu-id="b083a-142">為了支援引發衍生的例外狀況類型的例外狀況, `Throw`語言中支援語句。</span><span class="sxs-lookup"><span data-stu-id="b083a-142">In order to support the raising of exceptions of derived exception types, a `Throw` statement is supported in the language.</span></span> <span data-ttu-id="b083a-143">這會採用單一參數, 也就是要擲回的例外狀況實例。</span><span class="sxs-lookup"><span data-stu-id="b083a-143">This takes a single parameter that is the exception instance to be thrown.</span></span> <span data-ttu-id="b083a-144">下列範例顯示如何將這些功能與現有的例外狀況處理支援搭配使用:</span><span class="sxs-lookup"><span data-stu-id="b083a-144">The following example shows how these features can be used with the existing exception handling support:</span></span>

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 <span data-ttu-id="b083a-145">請注意, `On Error GoTo`語句會捕捉所有錯誤, 而不論例外狀況類別為何。</span><span class="sxs-lookup"><span data-stu-id="b083a-145">Notice that the `On Error GoTo` statement traps all errors, regardless of the exception class.</span></span>
  
## <a name="on-error-resume-next"></a><span data-ttu-id="b083a-146">發生錯誤時繼續下一步</span><span class="sxs-lookup"><span data-stu-id="b083a-146">On Error Resume Next</span></span>
 <span data-ttu-id="b083a-147">`On Error Resume Next`讓執行繼續進行, 緊接在導致執行階段錯誤的語句之後的語句, 或緊接在包含`On Error Resume Next`語句的程式之外的最後一次呼叫後面的語句。</span><span class="sxs-lookup"><span data-stu-id="b083a-147">`On Error Resume Next` causes execution to continue with the statement immediately following the statement that caused the run-time error, or with the statement immediately following the most recent call out of the procedure containing the `On Error Resume Next` statement.</span></span> <span data-ttu-id="b083a-148">即使執行階段錯誤, 此語句仍可繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b083a-148">This statement allows execution to continue despite a run-time error.</span></span> <span data-ttu-id="b083a-149">您可以將錯誤處理常式放在發生錯誤的位置, 而不是將控制權轉移到程式內的另一個位置。</span><span class="sxs-lookup"><span data-stu-id="b083a-149">You can place the error-handling routine where the error would occur rather than transferring control to another location within the procedure.</span></span> <span data-ttu-id="b083a-150">呼叫`On Error Resume Next`另一個程式時, 語句會變成非作用中, 因此, `On Error Resume Next`如果您想要在該常式內進行內嵌錯誤處理, 則應該在每個呼叫的常式中執行語句。</span><span class="sxs-lookup"><span data-stu-id="b083a-150">An `On Error Resume Next` statement becomes inactive when another procedure is called, so you should execute an `On Error Resume Next` statement in each called routine if you want inline error handling within that routine.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b083a-151">在`On Error Resume Next`處理存取其他物件期間`On Error GoTo`所產生的錯誤時, 可能會比較理想。</span><span class="sxs-lookup"><span data-stu-id="b083a-151">The `On Error Resume Next` construct may be preferable to `On Error GoTo` when handling errors generated during access to other objects.</span></span> <span data-ttu-id="b083a-152">在`Err`每個與物件的互動之後檢查, 會移除程式碼所存取的物件不明確。</span><span class="sxs-lookup"><span data-stu-id="b083a-152">Checking `Err` after each interaction with an object removes ambiguity about which object was accessed by the code.</span></span> <span data-ttu-id="b083a-153">您可以確定哪個物件將錯誤碼放在中`Err.Number`, 以及最初產生錯誤的物件 (在中`Err.Source`指定的物件)。</span><span class="sxs-lookup"><span data-stu-id="b083a-153">You can be sure which object placed the error code in `Err.Number`, as well as which object originally generated the error (the object specified in `Err.Source`).</span></span>

## <a name="on-error-goto-0"></a><span data-ttu-id="b083a-154">On Error GoTo 0</span><span class="sxs-lookup"><span data-stu-id="b083a-154">On Error GoTo 0</span></span>
 <span data-ttu-id="b083a-155">`On Error GoTo 0`停用目前程式中的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="b083a-155">`On Error GoTo 0` disables error handling in the current procedure.</span></span> <span data-ttu-id="b083a-156">它不會將第0行指定為錯誤處理常式代碼的開頭, 即使套裝程式含編號為0的行。</span><span class="sxs-lookup"><span data-stu-id="b083a-156">It doesn't specify line 0 as the start of the error-handling code, even if the procedure contains a line numbered 0.</span></span> <span data-ttu-id="b083a-157">如果沒有`On Error GoTo 0`語句, 當程式結束時, 就會自動停用錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="b083a-157">Without an `On Error GoTo 0` statement, an error handler is automatically disabled when a procedure is exited.</span></span>

## <a name="on-error-goto--1"></a><span data-ttu-id="b083a-158">發生錯誤時為-1</span><span class="sxs-lookup"><span data-stu-id="b083a-158">On Error GoTo -1</span></span>
 <span data-ttu-id="b083a-159">`On Error GoTo -1`停用目前程式中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b083a-159">`On Error GoTo -1` disables the exception in the current procedure.</span></span> <span data-ttu-id="b083a-160">它不會指定行-1 做為錯誤處理常式代碼的開頭, 即使套裝程式含編號為-1 的行。</span><span class="sxs-lookup"><span data-stu-id="b083a-160">It does not specify line -1 as the start of the error-handling code, even if the procedure contains a line numbered -1.</span></span> <span data-ttu-id="b083a-161">如果沒有`On Error GoTo -1`語句, 當程式結束時, 就會自動停用例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b083a-161">Without an `On Error GoTo -1` statement, an exception is automatically disabled when a procedure is exited.</span></span>

 <span data-ttu-id="b083a-162">若要防止錯誤處理常式代碼在未發生錯誤時執行, 請將`Exit Sub`、 `Exit Function`或`Exit Property`語句立即放在錯誤處理常式之前, 如下列片段所示:</span><span class="sxs-lookup"><span data-stu-id="b083a-162">To prevent error-handling code from running when no error has occurred, place an `Exit Sub`, `Exit Function`, or `Exit Property` statement immediately before the error-handling routine, as in the following fragment:</span></span>

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 <span data-ttu-id="b083a-163">在這裡, 錯誤處理常式代碼會遵循`Exit Sub`語句, 並在`End Sub`語句之前, 將它與程式流程分開。</span><span class="sxs-lookup"><span data-stu-id="b083a-163">Here, the error-handling code follows the `Exit Sub` statement and precedes the `End Sub` statement to separate it from the procedure flow.</span></span> <span data-ttu-id="b083a-164">您可以將錯誤處理常式代碼放在程式中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="b083a-164">You can place error-handling code anywhere in a procedure.</span></span>

## <a name="untrapped-errors"></a><span data-ttu-id="b083a-165">Untrapped 錯誤</span><span class="sxs-lookup"><span data-stu-id="b083a-165">Untrapped Errors</span></span>
 <span data-ttu-id="b083a-166">當物件當做可執行檔執行時, 物件中的 Untrapped 錯誤會傳回給控制應用程式。</span><span class="sxs-lookup"><span data-stu-id="b083a-166">Untrapped errors in objects are returned to the controlling application when the object is running as an executable file.</span></span> <span data-ttu-id="b083a-167">在開發環境中, 只有在設定適當的選項時, 才會將 untrapped 錯誤傳回給控制應用程式。</span><span class="sxs-lookup"><span data-stu-id="b083a-167">Within the development environment, untrapped errors are returned to the controlling application only if the proper options are set.</span></span> <span data-ttu-id="b083a-168">請參閱主應用程式的檔, 以瞭解在調試過程中應該設定哪些選項、如何設定它們, 以及主機是否可以建立類別的描述。</span><span class="sxs-lookup"><span data-stu-id="b083a-168">See your host application's documentation for a description of which options should be set during debugging, how to set them, and whether the host can create classes.</span></span>

 <span data-ttu-id="b083a-169">如果您建立的物件會存取其他物件, 您應該嘗試處理其傳回的任何未處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="b083a-169">If you create an object that accesses other objects, you should try to handle any unhandled errors they pass back.</span></span> <span data-ttu-id="b083a-170">如果您無法這樣做, 請將中`Err.Number`的錯誤碼對應至您自己的其中一個錯誤, 然後將它們傳回給物件的呼叫者。</span><span class="sxs-lookup"><span data-stu-id="b083a-170">If you cannot, map the error codes in `Err.Number` to one of your own errors and then pass them back to the caller of your object.</span></span> <span data-ttu-id="b083a-171">您應該將錯誤碼新增至`VbObjectError`常數來指定錯誤。</span><span class="sxs-lookup"><span data-stu-id="b083a-171">You should specify your error by adding your error code to the `VbObjectError` constant.</span></span> <span data-ttu-id="b083a-172">例如, 如果您的錯誤碼為 1052, 請將其指派如下:</span><span class="sxs-lookup"><span data-stu-id="b083a-172">For example, if your error code is 1052, assign it as follows:</span></span>

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> <span data-ttu-id="b083a-173">呼叫 Windows 動態連結程式庫 (Dll) 期間發生系統錯誤, 並不會引發例外狀況, 也無法在 Visual Basic 錯誤捕捉時加以攔截。</span><span class="sxs-lookup"><span data-stu-id="b083a-173">System errors during calls to Windows dynamic-link libraries (DLLs) do not raise exceptions and cannot be trapped with Visual Basic error trapping.</span></span> <span data-ttu-id="b083a-174">呼叫 DLL 函式時, 您應該檢查每個傳回值是否成功或失敗 (根據 API 規格), 並在發生失敗時檢查`Err` `LastDLLError`物件屬性中的值。</span><span class="sxs-lookup"><span data-stu-id="b083a-174">When calling DLL functions, you should check each return value for success or failure (according to the API specifications), and in the event of a failure, check the value in the `Err` object's `LastDLLError` property.</span></span>

## <a name="example"></a><span data-ttu-id="b083a-175">範例</span><span class="sxs-lookup"><span data-stu-id="b083a-175">Example</span></span>
 <span data-ttu-id="b083a-176">這個範例會先使用`On Error GoTo`語句來指定程式內的錯誤處理常式位置。</span><span class="sxs-lookup"><span data-stu-id="b083a-176">This example first uses the `On Error GoTo` statement to specify the location of an error-handling routine within a procedure.</span></span> <span data-ttu-id="b083a-177">在此範例中, 嘗試零除會產生錯誤號碼6。</span><span class="sxs-lookup"><span data-stu-id="b083a-177">In the example, an attempt to divide by zero generates error number 6.</span></span> <span data-ttu-id="b083a-178">錯誤會在錯誤處理常式中處理, 然後再將控制權傳回給造成錯誤的語句。</span><span class="sxs-lookup"><span data-stu-id="b083a-178">The error is handled in the error-handling routine, and control is then returned to the statement that caused the error.</span></span> <span data-ttu-id="b083a-179">`On Error GoTo 0`語句會關閉錯誤捕捉。</span><span class="sxs-lookup"><span data-stu-id="b083a-179">The `On Error GoTo 0` statement turns off error trapping.</span></span> <span data-ttu-id="b083a-180">然後, `On Error Resume Next`語句會用來延遲錯誤捕捉, 讓下一個語句所產生的錯誤內容可以知道。</span><span class="sxs-lookup"><span data-stu-id="b083a-180">Then the `On Error Resume Next` statement is used to defer error trapping so that the context for the error generated by the next statement can be known for certain.</span></span> <span data-ttu-id="b083a-181">請注意`Err.Clear` , 在處理錯誤之後`Err` , 會用來清除物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="b083a-181">Note that `Err.Clear` is used to clear the `Err` object's properties after the error is handled.</span></span>

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a><span data-ttu-id="b083a-182">需求</span><span class="sxs-lookup"><span data-stu-id="b083a-182">Requirements</span></span>
 <span data-ttu-id="b083a-183">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="b083a-183">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>

 <span data-ttu-id="b083a-184">**Assembly**Visual Basic Runtime Library (位於 Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="b083a-184">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>

## <a name="see-also"></a><span data-ttu-id="b083a-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b083a-185">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [<span data-ttu-id="b083a-186">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="b083a-186">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
- [<span data-ttu-id="b083a-187">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="b083a-187">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="b083a-188">Resume 陳述式</span><span class="sxs-lookup"><span data-stu-id="b083a-188">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="b083a-189">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="b083a-189">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
- [<span data-ttu-id="b083a-190">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="b083a-190">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
