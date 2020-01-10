---
title: 嘗試 .。。Catch .。。Finally 語句
description: 瞭解如何搭配 Visual Basic Try/Catch/Finally 語句來使用例外狀況處理。
ms.date: 12/07/2018
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
ms.openlocfilehash: bb6f17f7ce88caea0b9d30ec880194f2bb71c6a6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705765"
---
# <a name="trycatchfinally-statement-visual-basic"></a><span data-ttu-id="3dcc9-103">Try...Catch...Finally 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dcc9-103">Try...Catch...Finally Statement (Visual Basic)</span></span>

<span data-ttu-id="3dcc9-104">提供一種方法來處理特定程式碼區塊中可能發生的部分或所有可能錯誤，同時仍執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-104">Provides a way to handle some or all possible errors that may occur in a given block of code, while still running code.</span></span>

## <a name="syntax"></a><span data-ttu-id="3dcc9-105">語法</span><span class="sxs-lookup"><span data-stu-id="3dcc9-105">Syntax</span></span>

```vb
Try
    [ tryStatements ]
    [ Exit Try ]
[ Catch [ exception [ As type ] ] [ When expression ]
    [ catchStatements ]
    [ Exit Try ] ]
[ Catch ... ]
[ Finally
    [ finallyStatements ] ]
End Try
```

## <a name="parts"></a><span data-ttu-id="3dcc9-106">組件</span><span class="sxs-lookup"><span data-stu-id="3dcc9-106">Parts</span></span>

|<span data-ttu-id="3dcc9-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="3dcc9-107">Term</span></span>|<span data-ttu-id="3dcc9-108">定義</span><span class="sxs-lookup"><span data-stu-id="3dcc9-108">Definition</span></span>|
|---|---|
|`tryStatements`|<span data-ttu-id="3dcc9-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-109">Optional.</span></span> <span data-ttu-id="3dcc9-110">可能發生錯誤的語句。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-110">Statement(s) where an error can occur.</span></span> <span data-ttu-id="3dcc9-111">可以是複合陳述式。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-111">Can be a compound statement.</span></span>|
|`Catch`|<span data-ttu-id="3dcc9-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-112">Optional.</span></span> <span data-ttu-id="3dcc9-113">允許多個 `Catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-113">Multiple `Catch` blocks permitted.</span></span> <span data-ttu-id="3dcc9-114">如果在處理 `Try` 區塊時發生例外狀況，則會以文字順序檢查每個 `Catch` 語句，以判斷它是否會處理例外狀況，而 `exception` 則代表已擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-114">If an exception occurs when processing the `Try` block, each `Catch` statement is examined in textual order to determine whether it handles the exception, with `exception` representing the exception that has been thrown.</span></span>|
|`exception`|<span data-ttu-id="3dcc9-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-115">Optional.</span></span> <span data-ttu-id="3dcc9-116">任何變數名稱。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-116">Any variable name.</span></span> <span data-ttu-id="3dcc9-117">`exception` 的初始值就是擲回之錯誤的值。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-117">The initial value of `exception` is the value of the thrown error.</span></span> <span data-ttu-id="3dcc9-118">與 `Catch` 搭配使用，以指定攔截到的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-118">Used with `Catch` to specify the error caught.</span></span> <span data-ttu-id="3dcc9-119">如果省略，則 `Catch` 語句會攔截任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-119">If omitted, the `Catch` statement catches any exception.</span></span>|
|`type`|<span data-ttu-id="3dcc9-120">選擇項。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-120">Optional.</span></span> <span data-ttu-id="3dcc9-121">指定類別篩選的類型。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-121">Specifies the type of class filter.</span></span> <span data-ttu-id="3dcc9-122">如果 `exception` 的值是由 `type` 或衍生類型所指定的類型，則識別碼會變成系結至例外狀況物件。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-122">If the value of `exception` is of the type specified by `type` or of a derived type, the identifier becomes bound to the exception object.</span></span>|
|`When`|<span data-ttu-id="3dcc9-123">選擇項。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-123">Optional.</span></span> <span data-ttu-id="3dcc9-124">只有在 `expression` 評估為 `True`時，具有 `When` 子句的 `Catch` 語句才會攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-124">A `Catch` statement with a `When` clause catches exceptions only when `expression` evaluates to `True`.</span></span> <span data-ttu-id="3dcc9-125">只有在檢查例外狀況的類型之後，才會套用 `When` 子句，而 `expression` 可能會參考代表例外狀況的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-125">A `When` clause is applied only after checking the type of the exception, and `expression` may refer to the identifier representing the exception.</span></span>|
|`expression`|<span data-ttu-id="3dcc9-126">選擇項。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-126">Optional.</span></span> <span data-ttu-id="3dcc9-127">必須可以隱含地轉換成 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-127">Must be implicitly convertible to `Boolean`.</span></span> <span data-ttu-id="3dcc9-128">描述一般篩選準則的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-128">Any expression that describes a generic filter.</span></span> <span data-ttu-id="3dcc9-129">通常用來依錯誤號碼篩選。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-129">Typically used to filter by error number.</span></span> <span data-ttu-id="3dcc9-130">與 `When` 關鍵字搭配使用，以指定發生錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-130">Used with `When` keyword to specify circumstances under which the error is caught.</span></span>|
|`catchStatements`|<span data-ttu-id="3dcc9-131">選擇項。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-131">Optional.</span></span> <span data-ttu-id="3dcc9-132">用來處理相關聯 `Try` 區塊中所發生之錯誤的語句。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-132">Statement(s) to handle errors that occur in the associated `Try` block.</span></span> <span data-ttu-id="3dcc9-133">可以是複合陳述式。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-133">Can be a compound statement.</span></span>|
|`Exit Try`|<span data-ttu-id="3dcc9-134">選擇項。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-134">Optional.</span></span> <span data-ttu-id="3dcc9-135">`Try...Catch...Finally` 結構中斷的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-135">Keyword that breaks out of the `Try...Catch...Finally` structure.</span></span> <span data-ttu-id="3dcc9-136">以緊接在 `End Try` 語句後面的程式碼繼續執行。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-136">Execution resumes with the code immediately following the `End Try` statement.</span></span> <span data-ttu-id="3dcc9-137">`Finally` 語句仍然會執行。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-137">The `Finally` statement will still be executed.</span></span> <span data-ttu-id="3dcc9-138">`Finally` 區塊中不允許使用。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-138">Not allowed in `Finally` blocks.</span></span>|
|`Finally`|<span data-ttu-id="3dcc9-139">選擇項。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-139">Optional.</span></span> <span data-ttu-id="3dcc9-140">當執行離開 `Try...Catch` 語句的任何部分時，一律會執行 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-140">A `Finally` block is always executed when execution leaves any part of the `Try...Catch` statement.</span></span>|
|`finallyStatements`|<span data-ttu-id="3dcc9-141">選擇項。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-141">Optional.</span></span> <span data-ttu-id="3dcc9-142">發生所有其他錯誤處理之後執行的語句。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-142">Statement(s) that are executed after all other error processing has occurred.</span></span>|
|`End Try`|<span data-ttu-id="3dcc9-143">終止 `Try...Catch...Finally` 結構。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-143">Terminates the `Try...Catch...Finally` structure.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3dcc9-144">備註</span><span class="sxs-lookup"><span data-stu-id="3dcc9-144">Remarks</span></span>

<span data-ttu-id="3dcc9-145">如果您預期特定的例外狀況可能會在程式碼的特定區段中發生，請將程式碼放在 `Try` 區塊中，然後使用 `Catch` 區塊來保留控制項並處理例外狀況（如果發生）。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-145">If you expect that a particular exception might occur during a particular section of code, put the code in a `Try` block and use a `Catch` block to retain control and handle the exception if it occurs.</span></span>

<span data-ttu-id="3dcc9-146">`Try…Catch` 語句是由 `Try` 區塊後面接著一個或多個 `Catch` 子句所組成，這會指定各種例外狀況的處理常式。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-146">A `Try…Catch` statement consists of a `Try` block followed by one or more `Catch` clauses, which specify handlers for various exceptions.</span></span> <span data-ttu-id="3dcc9-147">當 `Try` 區塊中擲回例外狀況時，Visual Basic 會尋找處理例外狀況的 `Catch` 語句。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-147">When an exception is thrown in a `Try` block, Visual Basic looks for the `Catch` statement that handles the exception.</span></span> <span data-ttu-id="3dcc9-148">如果找不到相符的 `Catch` 語句，Visual Basic 會檢查呼叫目前方法的方法，並在呼叫堆疊上開啟。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-148">If a matching `Catch` statement is not found, Visual Basic examines the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="3dcc9-149">如果找不到 `Catch` 區塊，Visual Basic 會向使用者顯示未處理的例外狀況訊息，並停止執行程式。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-149">If no `Catch` block is found, Visual Basic displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="3dcc9-150">您可以在 `Try…Catch` 語句中使用一個以上的 `Catch` 語句。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-150">You can use more than one `Catch` statement in a `Try…Catch` statement.</span></span> <span data-ttu-id="3dcc9-151">如果您這樣做，`Catch` 子句的順序很重要，因為它們會依序進行檢查。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-151">If you do this, the order of the `Catch` clauses is significant because they are examined in order.</span></span> <span data-ttu-id="3dcc9-152">在較不特定的例外狀況之前攔截較特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-152">Catch the more specific exceptions before the less specific ones.</span></span>

<span data-ttu-id="3dcc9-153">下列 `Catch` 語句條件是最不明確的，而且會攔截衍生自 <xref:System.Exception> 類別的所有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-153">The following `Catch` statement conditions are the least specific, and will catch all exceptions that derive from the <xref:System.Exception> class.</span></span> <span data-ttu-id="3dcc9-154">在捕捉到您預期的所有特定例外狀況之後，通常應該使用這些變化之一做為 `Try...Catch...Finally` 結構中的最後一個 `Catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-154">You should ordinarily use one of these variations as the last `Catch` block in the `Try...Catch...Finally` structure, after catching all the specific exceptions you expect.</span></span> <span data-ttu-id="3dcc9-155">控制流程永遠不能觸及遵循下列其中一種變化的 `Catch` 組塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-155">Control flow can never reach a `Catch` block that follows either of these variations.</span></span>

- <span data-ttu-id="3dcc9-156">`type` `Exception`，例如： `Catch ex As Exception`</span><span class="sxs-lookup"><span data-stu-id="3dcc9-156">The `type` is `Exception`, for example: `Catch ex As Exception`</span></span>

- <span data-ttu-id="3dcc9-157">語句沒有 `exception` 變數，例如： `Catch`</span><span class="sxs-lookup"><span data-stu-id="3dcc9-157">The statement has no `exception` variable, for example: `Catch`</span></span>

<span data-ttu-id="3dcc9-158">當 `Try…Catch…Finally` 語句嵌套于另一個 `Try` 區塊時，Visual Basic 會先檢查最內層 `Try` 區塊中的每個 `Catch` 語句。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-158">When a `Try…Catch…Finally` statement is nested in another `Try` block, Visual Basic first examines each `Catch` statement in the innermost `Try` block.</span></span> <span data-ttu-id="3dcc9-159">如果找不到相符的 `Catch` 語句，搜尋會繼續進行外部 `Try…Catch…Finally` 區塊的 `Catch` 語句。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-159">If no matching `Catch` statement is found, the search proceeds to the `Catch` statements of the outer `Try…Catch…Finally` block.</span></span>

<span data-ttu-id="3dcc9-160">`Try` 區塊中的區域變數無法在 `Catch` 區塊中使用，因為它們是個別的區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-160">Local variables from a `Try` block are not available in a `Catch` block because they are separate blocks.</span></span> <span data-ttu-id="3dcc9-161">如果您想要在多個區塊中使用變數，請在 `Try...Catch...Finally` 結構外宣告變數。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-161">If you want to use a variable in more than one block, declare the variable outside the `Try...Catch...Finally` structure.</span></span>

> [!TIP]
> <span data-ttu-id="3dcc9-162">`Try…Catch…Finally` 語句是以 IntelliSense 程式碼片段的形式提供。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-162">The `Try…Catch…Finally` statement is available as an IntelliSense code snippet.</span></span> <span data-ttu-id="3dcc9-163">在 [程式碼片段管理員] 中，展開 [**程式碼模式]-如果每個都嘗試 Catch、Property 等**，然後再進行**錯誤處理（例外狀況）** 。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-163">In the Code Snippets Manager, expand **Code Patterns - If, For Each, Try Catch, Property, etc**, and then **Error Handling (Exceptions)**.</span></span> <span data-ttu-id="3dcc9-164">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-164">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>

## <a name="finally-block"></a><span data-ttu-id="3dcc9-165">Finally 區塊</span><span class="sxs-lookup"><span data-stu-id="3dcc9-165">Finally block</span></span>

<span data-ttu-id="3dcc9-166">如果您在結束 `Try` 結構之前，有一或多個必須執行的語句，請使用 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-166">If you have one or more statements that must run before you exit the `Try` structure, use a `Finally` block.</span></span> <span data-ttu-id="3dcc9-167">控制項傳入 `Try…Catch` 結構之前，會傳遞至 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-167">Control passes to the `Finally` block just before it passes out of the `Try…Catch` structure.</span></span> <span data-ttu-id="3dcc9-168">即使在 `Try` 結構內的任何位置發生例外狀況，也是如此。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-168">This is true even if an exception occurs anywhere inside the `Try` structure.</span></span>

<span data-ttu-id="3dcc9-169">`Finally` 區塊適用于執行任何必須執行的程式碼，即使發生例外狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-169">A `Finally` block is useful for running any code that must execute even if there is an exception.</span></span> <span data-ttu-id="3dcc9-170">不論 `Try...Catch` 區塊結束的方式為何，控制項都會傳遞至 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-170">Control is passed to the `Finally` block regardless of how the `Try...Catch` block exits.</span></span>

<span data-ttu-id="3dcc9-171">即使您的程式碼在 `Try` 或 `Catch` 區塊中遇到 `Return` 語句，`Finally` 區塊中的程式碼也會執行。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-171">The code in a `Finally` block runs even if your code encounters a `Return` statement in a `Try` or `Catch` block.</span></span> <span data-ttu-id="3dcc9-172">在下列情況下，控制項不會從 `Try` 或 `Catch` 區塊傳遞至對應的 `Finally` 區塊：</span><span class="sxs-lookup"><span data-stu-id="3dcc9-172">Control does not pass from a `Try` or `Catch` block to the corresponding `Finally` block in the following cases:</span></span>

- <span data-ttu-id="3dcc9-173">在 `Try` 或 `Catch` 區塊中遇到[End 語句](end-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-173">An [End Statement](end-statement.md) is encountered in the `Try` or `Catch` block.</span></span>

- <span data-ttu-id="3dcc9-174"><xref:System.StackOverflowException> 會在 `Try` 或 `Catch` 區塊中擲回。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-174">A <xref:System.StackOverflowException> is thrown in the `Try` or `Catch` block.</span></span>

<span data-ttu-id="3dcc9-175">將執行明確轉移到 `Finally` 區塊是不正確。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-175">It is not valid to explicitly transfer execution into a `Finally` block.</span></span> <span data-ttu-id="3dcc9-176">除了例外狀況之外，從 `Finally` 區塊傳出執行是不正確。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-176">Transferring execution out of a `Finally` block is not valid, except through an exception.</span></span>

<span data-ttu-id="3dcc9-177">如果 `Try` 語句不包含至少一個 `Catch` 區塊，它就必須包含 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-177">If a `Try` statement does not contain at least one `Catch` block, it must contain a `Finally` block.</span></span>

> [!TIP]
> <span data-ttu-id="3dcc9-178">如果您不需要攔截特定的例外狀況，則 `Using` 語句的行為就像是 `Try…Finally` 區塊，並保證資源的處置，不論您如何結束區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-178">If you do not have to catch specific exceptions, the `Using` statement behaves like a `Try…Finally` block, and guarantees disposal of the resources, regardless of how you exit the block.</span></span> <span data-ttu-id="3dcc9-179">即使有未處理的例外狀況，也是如此。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-179">This is true even with an unhandled exception.</span></span> <span data-ttu-id="3dcc9-180">如需詳細資訊，請參閱 [Using 陳述式](using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-180">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="exception-argument"></a><span data-ttu-id="3dcc9-181">Exception 引數</span><span class="sxs-lookup"><span data-stu-id="3dcc9-181">Exception argument</span></span>

<span data-ttu-id="3dcc9-182">`Catch` 區塊 `exception` 引數是 <xref:System.Exception> 類別的實例，或衍生自 `Exception` 類別的類別。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-182">The `Catch` block `exception` argument is an instance of the <xref:System.Exception> class or a class that derives from the `Exception` class.</span></span> <span data-ttu-id="3dcc9-183">`Exception` 類別實例會對應至 `Try` 區塊中發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-183">The `Exception` class instance corresponds to the error that occurred in the `Try` block.</span></span>

<span data-ttu-id="3dcc9-184">`Exception` 物件的屬性有助於找出例外狀況的原因和位置。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-184">The properties of the `Exception` object help to identify the cause and location of an exception.</span></span> <span data-ttu-id="3dcc9-185">例如，<xref:System.Exception.StackTrace%2A> 屬性會列出導致例外狀況的被呼叫方法，協助您找出程式碼中發生錯誤的位置。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-185">For example, the <xref:System.Exception.StackTrace%2A> property lists the called methods that led to the exception, helping you find where the error occurred in the code.</span></span> <span data-ttu-id="3dcc9-186"><xref:System.Exception.Message%2A> 會傳回描述例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-186"><xref:System.Exception.Message%2A> returns a message that describes the exception.</span></span> <span data-ttu-id="3dcc9-187"><xref:System.Exception.HelpLink%2A> 會傳回相關聯說明檔的連結。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-187"><xref:System.Exception.HelpLink%2A> returns a link to an associated Help file.</span></span> <span data-ttu-id="3dcc9-188"><xref:System.Exception.InnerException%2A> 會傳回造成目前例外狀況的 `Exception` 物件，或如果沒有原始 `Exception`，它會傳回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-188"><xref:System.Exception.InnerException%2A> returns the `Exception` object that caused the current exception, or it returns `Nothing` if there is no original `Exception`.</span></span>

## <a name="considerations-when-using-a-trycatch-statement"></a><span data-ttu-id="3dcc9-189">使用 [嘗試 ...] 時的考慮Catch 語句</span><span class="sxs-lookup"><span data-stu-id="3dcc9-189">Considerations when using a Try…Catch statement</span></span>

<span data-ttu-id="3dcc9-190">僅使用 `Try…Catch` 語句，以表示發生異常或意外的程式事件。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-190">Use a `Try…Catch` statement only to signal the occurrence of unusual or unanticipated program events.</span></span> <span data-ttu-id="3dcc9-191">其原因包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="3dcc9-191">Reasons for this include the following:</span></span>

- <span data-ttu-id="3dcc9-192">在執行時間攔截例外狀況會產生額外的負荷，而且可能比預先檢查來避免例外狀況的速度慢。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-192">Catching exceptions at runtime creates additional overhead, and is likely to be slower than pre-checking to avoid exceptions.</span></span>

- <span data-ttu-id="3dcc9-193">如果未正確處理 `Catch` 區塊，則例外狀況可能不會正確地回報給使用者。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-193">If a `Catch` block is not handled correctly, the exception might not be reported correctly to users.</span></span>

- <span data-ttu-id="3dcc9-194">例外狀況處理會使程式變得更複雜。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-194">Exception handling makes a program more complex.</span></span>

<span data-ttu-id="3dcc9-195">您不一定需要 `Try…Catch` 語句來檢查是否有可能發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-195">You do not always need a `Try…Catch` statement to check for a condition that is likely to occur.</span></span> <span data-ttu-id="3dcc9-196">下列範例會先檢查檔案是否存在，然後再嘗試開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-196">The following example checks whether a file exists before trying to open it.</span></span> <span data-ttu-id="3dcc9-197">這可減少攔截 <xref:System.IO.File.OpenText%2A> 方法所擲回之例外狀況的需求。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-197">This reduces the need for catching an exception thrown by the <xref:System.IO.File.OpenText%2A> method.</span></span>

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

<span data-ttu-id="3dcc9-198">請確定 `Catch` 區塊中的程式碼可以正確地向使用者報告例外狀況，不論是透過安全線程記錄或適當的訊息。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-198">Ensure that code in `Catch` blocks can properly report exceptions to users, whether through thread-safe logging or appropriate messages.</span></span> <span data-ttu-id="3dcc9-199">否則，例外狀況可能會維持不明。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-199">Otherwise, exceptions might remain unknown.</span></span>

## <a name="async-methods"></a><span data-ttu-id="3dcc9-200">非同步方法</span><span class="sxs-lookup"><span data-stu-id="3dcc9-200">Async methods</span></span>

<span data-ttu-id="3dcc9-201">如果您使用[Async](../modifiers/async.md)修飾詞來標示方法，則可以在方法中使用[Await](../operators/await-operator.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-201">If you mark a method with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the method.</span></span> <span data-ttu-id="3dcc9-202">具有 `Await` 運算子的語句會暫停執行方法，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-202">A statement with the `Await` operator suspends execution of the method until the awaited task completes.</span></span> <span data-ttu-id="3dcc9-203">工作代表進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-203">The task represents ongoing work.</span></span> <span data-ttu-id="3dcc9-204">當與 `Await` 運算子相關聯的工作完成時，就會在相同的方法中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-204">When the task that's associated with the `Await` operator finishes, execution resumes in the same method.</span></span> <span data-ttu-id="3dcc9-205">如需詳細資訊，請參閱[非同步程式中的控制流程](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-205">For more information, see [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>

<span data-ttu-id="3dcc9-206">非同步方法傳回的工作可能會以錯誤狀態結束，表示它已因未處理的例外狀況而完成。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-206">A task returned by an Async method may end in a faulted state, indicating that it completed due to an unhandled exception.</span></span> <span data-ttu-id="3dcc9-207">工作可能也會以取消的狀態結束，這會導致在 await 運算式中擲回 `OperationCanceledException`。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-207">A task may also end in a canceled state, which results in an `OperationCanceledException` being thrown out of the await expression.</span></span> <span data-ttu-id="3dcc9-208">若要攔截任一類型的例外狀況，請將與工作相關聯的 `Await` 運算式放在 `Try` 區塊中，並攔截 `Catch` 區塊中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-208">To catch either type of exception, place the `Await` expression that's associated with the task in a `Try` block, and catch the exception in the `Catch` block.</span></span> <span data-ttu-id="3dcc9-209">本主題稍後會提供範例。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-209">An example is provided later in this topic.</span></span>

<span data-ttu-id="3dcc9-210">工作可能處於錯誤狀態，因為有多個例外狀況負責其錯誤。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-210">A task can be in a faulted state because multiple exceptions were responsible for its faulting.</span></span> <span data-ttu-id="3dcc9-211">例如，工作可能是對 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-211">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3dcc9-212">當您等候這類工作時，攔截到的例外狀況只是其中一個例外狀況，而且您無法預測會攔截到哪個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-212">When you await such a task, the caught exception is only one of the exceptions, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="3dcc9-213">本主題稍後會提供範例。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-213">An example is provided later in this topic.</span></span>

<span data-ttu-id="3dcc9-214">`Await` 運算式不能在 `Catch` 區塊或 `Finally` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-214">An `Await` expression can't be inside a `Catch` block or `Finally` block.</span></span>

## <a name="iterators"></a><span data-ttu-id="3dcc9-215">Iterators</span><span class="sxs-lookup"><span data-stu-id="3dcc9-215">Iterators</span></span>

<span data-ttu-id="3dcc9-216">Iterator 函數或 `Get` 存取子會在集合上執行自訂反復專案。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-216">An iterator function or `Get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="3dcc9-217">反覆運算器會使用[Yield](yield-statement.md)語句，一次傳回集合中的每個元素。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-217">An iterator uses a [Yield](yield-statement.md) statement to return each element of the collection one at a time.</span></span> <span data-ttu-id="3dcc9-218">您可以使用[For Each ... 來呼叫 iterator 函數。下一個語句](for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-218">You call an iterator function by using a [For Each...Next Statement](for-each-next-statement.md).</span></span>

<span data-ttu-id="3dcc9-219">`Yield` 語句可以在 `Try` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-219">A `Yield` statement can be inside a `Try` block.</span></span> <span data-ttu-id="3dcc9-220">包含 `Yield` 語句的 `Try` 區塊可以有 `Catch` 區塊，而且可以有 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-220">A `Try` block that contains a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span> <span data-ttu-id="3dcc9-221">如需範例，請參閱[反覆運算](../../programming-guide/concepts/iterators.md)器的「在 Visual Basic 中嘗試區塊」一節。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-221">See the "Try Blocks in Visual Basic" section of [Iterators](../../programming-guide/concepts/iterators.md) for an example.</span></span>

<span data-ttu-id="3dcc9-222">`Yield` 語句不能在 `Catch` 區塊或 `Finally` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-222">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="3dcc9-223">如果 `For Each` 主體（iterator 函數之外）擲回例外狀況，則不會執行 iterator 函式中的 `Catch` 區塊，但會執行 iterator 函式中的 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-223">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="3dcc9-224">Iterator 函式內的 `Catch` 區塊只會攔截在 iterator 函式內發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-224">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="partial-trust-situations"></a><span data-ttu-id="3dcc9-225">部分信任的情況</span><span class="sxs-lookup"><span data-stu-id="3dcc9-225">Partial-trust situations</span></span>

<span data-ttu-id="3dcc9-226">在部分信任的情況下（例如，在網路共用上裝載的應用程式），`Try...Catch...Finally` 不會在叫用包含呼叫的方法之前，攔截發生的安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-226">In partial-trust situations, such as an application hosted on a network share, `Try...Catch...Finally` does not catch security exceptions that occur before the method that contains the call is invoked.</span></span> <span data-ttu-id="3dcc9-227">下列範例中，當您將它放在伺服器共用並從該處執行時，會產生錯誤「SecurityException：要求失敗。」</span><span class="sxs-lookup"><span data-stu-id="3dcc9-227">The following example, when you put it on a server share and run from there, produces the error "System.Security.SecurityException: Request Failed."</span></span> <span data-ttu-id="3dcc9-228">如需安全性例外狀況的詳細資訊，請參閱 <xref:System.Security.SecurityException> 類別。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-228">For more information about security exceptions, see the <xref:System.Security.SecurityException> class.</span></span>

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

<span data-ttu-id="3dcc9-229">在這種部分信任的情況下，您必須將 `Process.Start` 語句放在不同的 `Sub`中。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-229">In such a partial-trust situation, you have to put the `Process.Start` statement in a separate `Sub`.</span></span> <span data-ttu-id="3dcc9-230">`Sub` 的初始呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-230">The initial call to the `Sub` will fail.</span></span> <span data-ttu-id="3dcc9-231">這可讓 `Try...Catch` 在包含 `Process.Start` 的 `Sub` 啟動，以及產生的安全性例外狀況之前攔截它。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-231">This enables `Try...Catch` to catch it before the `Sub` that contains `Process.Start` is started and the security exception produced.</span></span>

## <a name="examples"></a><span data-ttu-id="3dcc9-232">範例</span><span class="sxs-lookup"><span data-stu-id="3dcc9-232">Examples</span></span>

### <a name="the-structure-of-trycatchfinally"></a><span data-ttu-id="3dcc9-233">Try 的結構 .。。Catch .。。一點</span><span class="sxs-lookup"><span data-stu-id="3dcc9-233">The structure of Try...Catch...Finally</span></span>

<span data-ttu-id="3dcc9-234">下列範例說明 `Try...Catch...Finally` 語句的結構。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-234">The following example illustrates the structure of the `Try...Catch...Finally` statement.</span></span>

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a><span data-ttu-id="3dcc9-235">從 Try 區塊呼叫的方法中發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="3dcc9-235">Exception in a method called from a Try block</span></span>

<span data-ttu-id="3dcc9-236">在下列範例中，`CreateException` 方法會擲回 `NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-236">In the following example, the `CreateException` method throws a `NullReferenceException`.</span></span> <span data-ttu-id="3dcc9-237">產生例外狀況的程式碼不在 `Try` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-237">The code that generates the exception is not in a `Try` block.</span></span> <span data-ttu-id="3dcc9-238">因此，`CreateException` 方法不會處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-238">Therefore, the `CreateException` method does not handle the exception.</span></span> <span data-ttu-id="3dcc9-239">`RunSample` 方法會處理例外狀況，因為呼叫 `CreateException` 方法是在 `Try` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-239">The `RunSample` method does handle the exception because the call to the `CreateException` method is in a `Try` block.</span></span>

<span data-ttu-id="3dcc9-240">此範例包含數個例外狀況類型的 `Catch` 語句，從最特定到最常見的順序排序。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-240">The example includes `Catch` statements for several types of exceptions, ordered from the most specific to the most general.</span></span>

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a><span data-ttu-id="3dcc9-241">Catch When 語句</span><span class="sxs-lookup"><span data-stu-id="3dcc9-241">The Catch When statement</span></span>

<span data-ttu-id="3dcc9-242">下列範例顯示如何使用 `Catch When` 語句來篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-242">The following example shows how to use a `Catch When` statement to filter on a conditional expression.</span></span> <span data-ttu-id="3dcc9-243">如果條件運算式評估為 `True`，`Catch` 區塊中的程式碼就會執行。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-243">If the conditional expression evaluates to `True`, the code in the `Catch` block runs.</span></span>

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a><span data-ttu-id="3dcc9-244">嵌套的 Try 語句</span><span class="sxs-lookup"><span data-stu-id="3dcc9-244">Nested Try statements</span></span>

<span data-ttu-id="3dcc9-245">下列範例包含包含在 `Try` 區塊中的 `Try…Catch` 語句。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-245">The following example has a `Try…Catch` statement that is contained in a `Try` block.</span></span> <span data-ttu-id="3dcc9-246">內部 `Catch` 區塊會擲回例外狀況，並將其 `InnerException` 屬性設定為原始例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-246">The inner `Catch` block throws an exception that has its `InnerException` property set to the original exception.</span></span> <span data-ttu-id="3dcc9-247">外部 `Catch` 區塊會報告其本身的例外狀況和內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-247">The outer `Catch` block reports its own exception and the inner exception.</span></span>

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a><span data-ttu-id="3dcc9-248">非同步方法的例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="3dcc9-248">Exception handling for async methods</span></span>

<span data-ttu-id="3dcc9-249">下列範例說明非同步方法的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-249">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="3dcc9-250">若要攔截適用于非同步工作的例外狀況，`Await` 運算式位於呼叫端的 `Try` 區塊內，而在 `Catch` 區塊中攔截到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-250">To catch an exception that applies to an async task, the `Await` expression is in a `Try` block of the caller, and the exception is caught in the `Catch` block.</span></span>

<span data-ttu-id="3dcc9-251">取消註解範例中的 `Throw New Exception` 行來示範例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-251">Uncomment the `Throw New Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="3dcc9-252">`Catch` 區塊中攔截到例外狀況，工作的 `IsFaulted` 屬性會設定為 `True`，而工作的 `Exception.InnerException` 屬性會設定為例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-252">The exception is caught in the `Catch` block, the task's `IsFaulted` property is set to `True`, and the task's `Exception.InnerException` property is set to the exception.</span></span>

<span data-ttu-id="3dcc9-253">取消註解 `Throw New OperationCancelledException` 行來示範取消非同步處理序時會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-253">Uncomment the `Throw New OperationCancelledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="3dcc9-254">`Catch` 區塊中攔截到例外狀況，且工作的 [`IsCanceled`] 屬性設定為 [`True`]。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-254">The exception is caught in the `Catch` block, and the task's `IsCanceled` property is set to `True`.</span></span> <span data-ttu-id="3dcc9-255">不過，在某些不適用此範例的情況下，`IsFaulted` 設定為 `True`，`IsCanceled` 設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-255">However, under some conditions that don't apply to this example, `IsFaulted` is set to `True` and `IsCanceled` is set to `False`.</span></span>

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a><span data-ttu-id="3dcc9-256">處理非同步方法中的多個例外狀況</span><span class="sxs-lookup"><span data-stu-id="3dcc9-256">Handling multiple exceptions in async methods</span></span>

<span data-ttu-id="3dcc9-257">下列範例說明多項工作可能會導致多個例外狀況的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-257">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="3dcc9-258">`Try` 區塊具有 `Await` 運算式，適用于 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 傳回的工作。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-258">The `Try` block has the `Await` expression for the task that <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> returned.</span></span> <span data-ttu-id="3dcc9-259">當套用 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 的三項工作完成時，工作就會完成。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-259">The task is complete when the three tasks to which <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> is applied are complete.</span></span>

<span data-ttu-id="3dcc9-260">這三個工作都會造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-260">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="3dcc9-261">`Catch` 區塊會逐一查看例外狀況，這會在 `Task.WhenAll` 傳回之工作的 `Exception.InnerExceptions` 屬性中找到。</span><span class="sxs-lookup"><span data-stu-id="3dcc9-261">The `Catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that `Task.WhenAll` returned.</span></span>

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a><span data-ttu-id="3dcc9-262">請參閱</span><span class="sxs-lookup"><span data-stu-id="3dcc9-262">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [<span data-ttu-id="3dcc9-263">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="3dcc9-263">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="3dcc9-264">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="3dcc9-264">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="3dcc9-265">使用程式碼片段的最佳做法</span><span class="sxs-lookup"><span data-stu-id="3dcc9-265">Best Practices for Using Code Snippets</span></span>](/visualstudio/ide/best-practices-for-using-code-snippets)
- [<span data-ttu-id="3dcc9-266">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="3dcc9-266">Exception Handling</span></span>](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [<span data-ttu-id="3dcc9-267">Throw 陳述式</span><span class="sxs-lookup"><span data-stu-id="3dcc9-267">Throw Statement</span></span>](throw-statement.md)
