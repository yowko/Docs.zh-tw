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
ms.openlocfilehash: 22f1611786a3da512632b5b547b7ef141c8f65c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391764"
---
# <a name="trycatchfinally-statement-visual-basic"></a><span data-ttu-id="f1812-103">Try...Catch...Finally 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1812-103">Try...Catch...Finally Statement (Visual Basic)</span></span>

<span data-ttu-id="f1812-104">提供一種方法來處理特定程式碼區塊中可能發生的部分或所有可能錯誤，同時仍執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="f1812-104">Provides a way to handle some or all possible errors that may occur in a given block of code, while still running code.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1812-105">語法</span><span class="sxs-lookup"><span data-stu-id="f1812-105">Syntax</span></span>

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

## <a name="parts"></a><span data-ttu-id="f1812-106">組件</span><span class="sxs-lookup"><span data-stu-id="f1812-106">Parts</span></span>

|<span data-ttu-id="f1812-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="f1812-107">Term</span></span>|<span data-ttu-id="f1812-108">定義</span><span class="sxs-lookup"><span data-stu-id="f1812-108">Definition</span></span>|
|---|---|
|`tryStatements`|<span data-ttu-id="f1812-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1812-109">Optional.</span></span> <span data-ttu-id="f1812-110">可能發生錯誤的語句。</span><span class="sxs-lookup"><span data-stu-id="f1812-110">Statement(s) where an error can occur.</span></span> <span data-ttu-id="f1812-111">可以是複合陳述式。</span><span class="sxs-lookup"><span data-stu-id="f1812-111">Can be a compound statement.</span></span>|
|`Catch`|<span data-ttu-id="f1812-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1812-112">Optional.</span></span> <span data-ttu-id="f1812-113">允許多個 `Catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="f1812-113">Multiple `Catch` blocks permitted.</span></span> <span data-ttu-id="f1812-114">如果在處理區塊時發生例外狀況 `Try` ， `Catch` 則會以文字順序檢查每個語句，以判斷是否要處理例外狀況，並代表已擲回 `exception` 的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-114">If an exception occurs when processing the `Try` block, each `Catch` statement is examined in textual order to determine whether it handles the exception, with `exception` representing the exception that has been thrown.</span></span>|
|`exception`|<span data-ttu-id="f1812-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1812-115">Optional.</span></span> <span data-ttu-id="f1812-116">任何變數名稱。</span><span class="sxs-lookup"><span data-stu-id="f1812-116">Any variable name.</span></span> <span data-ttu-id="f1812-117">`exception` 的初始值就是擲回之錯誤的值。</span><span class="sxs-lookup"><span data-stu-id="f1812-117">The initial value of `exception` is the value of the thrown error.</span></span> <span data-ttu-id="f1812-118">與搭配使用 `Catch` ，以指定攔截到的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1812-118">Used with `Catch` to specify the error caught.</span></span> <span data-ttu-id="f1812-119">如果省略，語句會攔截 `Catch` 任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-119">If omitted, the `Catch` statement catches any exception.</span></span>|
|`type`|<span data-ttu-id="f1812-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1812-120">Optional.</span></span> <span data-ttu-id="f1812-121">指定類別篩選的類型。</span><span class="sxs-lookup"><span data-stu-id="f1812-121">Specifies the type of class filter.</span></span> <span data-ttu-id="f1812-122">如果的值 `exception` 是由或衍生型別所指定的型別 `type` ，則識別碼會變成系結至例外狀況物件。</span><span class="sxs-lookup"><span data-stu-id="f1812-122">If the value of `exception` is of the type specified by `type` or of a derived type, the identifier becomes bound to the exception object.</span></span>|
|`When`|<span data-ttu-id="f1812-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1812-123">Optional.</span></span> <span data-ttu-id="f1812-124">`Catch` `When` 只有當評估為時，含有子句的語句才會攔截例外狀況 `expression` `True` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-124">A `Catch` statement with a `When` clause catches exceptions only when `expression` evaluates to `True`.</span></span> <span data-ttu-id="f1812-125">`When`只有在檢查例外狀況的類型之後，才會套用子句，而且 `expression` 可能會參考代表例外狀況的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f1812-125">A `When` clause is applied only after checking the type of the exception, and `expression` may refer to the identifier representing the exception.</span></span>|
|`expression`|<span data-ttu-id="f1812-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1812-126">Optional.</span></span> <span data-ttu-id="f1812-127">必須可以隱含地轉換為 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-127">Must be implicitly convertible to `Boolean`.</span></span> <span data-ttu-id="f1812-128">描述一般篩選準則的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="f1812-128">Any expression that describes a generic filter.</span></span> <span data-ttu-id="f1812-129">通常用來依錯誤號碼篩選。</span><span class="sxs-lookup"><span data-stu-id="f1812-129">Typically used to filter by error number.</span></span> <span data-ttu-id="f1812-130">搭配 `When` 關鍵字用來指定發生錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="f1812-130">Used with `When` keyword to specify circumstances under which the error is caught.</span></span>|
|`catchStatements`|<span data-ttu-id="f1812-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1812-131">Optional.</span></span> <span data-ttu-id="f1812-132">用來處理相關聯區塊中所發生之錯誤的語句 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-132">Statement(s) to handle errors that occur in the associated `Try` block.</span></span> <span data-ttu-id="f1812-133">可以是複合陳述式。</span><span class="sxs-lookup"><span data-stu-id="f1812-133">Can be a compound statement.</span></span>|
|`Exit Try`|<span data-ttu-id="f1812-134">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1812-134">Optional.</span></span> <span data-ttu-id="f1812-135">違反結構的關鍵字 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-135">Keyword that breaks out of the `Try...Catch...Finally` structure.</span></span> <span data-ttu-id="f1812-136">執行時，會以緊接在語句之後的程式碼繼續進行 `End Try` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-136">Execution resumes with the code immediately following the `End Try` statement.</span></span> <span data-ttu-id="f1812-137">`Finally`語句仍會執行。</span><span class="sxs-lookup"><span data-stu-id="f1812-137">The `Finally` statement will still be executed.</span></span> <span data-ttu-id="f1812-138">區塊中不允許使用 `Finally` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-138">Not allowed in `Finally` blocks.</span></span>|
|`Finally`|<span data-ttu-id="f1812-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1812-139">Optional.</span></span> <span data-ttu-id="f1812-140">`Finally`當執行離開語句的任何部分時，一律會執行區塊 `Try...Catch` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-140">A `Finally` block is always executed when execution leaves any part of the `Try...Catch` statement.</span></span>|
|`finallyStatements`|<span data-ttu-id="f1812-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f1812-141">Optional.</span></span> <span data-ttu-id="f1812-142">發生所有其他錯誤處理之後執行的語句。</span><span class="sxs-lookup"><span data-stu-id="f1812-142">Statement(s) that are executed after all other error processing has occurred.</span></span>|
|`End Try`|<span data-ttu-id="f1812-143">終止 `Try...Catch...Finally` 結構。</span><span class="sxs-lookup"><span data-stu-id="f1812-143">Terminates the `Try...Catch...Finally` structure.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f1812-144">備註</span><span class="sxs-lookup"><span data-stu-id="f1812-144">Remarks</span></span>

<span data-ttu-id="f1812-145">如果您預期特定的例外狀況可能會在程式碼的特定區段中發生，請將程式碼放在區塊中， `Try` 然後使用 `Catch` 區塊來保留控制項並處理例外狀況（如果發生）。</span><span class="sxs-lookup"><span data-stu-id="f1812-145">If you expect that a particular exception might occur during a particular section of code, put the code in a `Try` block and use a `Catch` block to retain control and handle the exception if it occurs.</span></span>

<span data-ttu-id="f1812-146">`Try…Catch`語句是由 `Try` 區塊後面接著一個或多個 `Catch` 子句所組成，其指定各種例外狀況的處理常式。</span><span class="sxs-lookup"><span data-stu-id="f1812-146">A `Try…Catch` statement consists of a `Try` block followed by one or more `Catch` clauses, which specify handlers for various exceptions.</span></span> <span data-ttu-id="f1812-147">在區塊中擲回例外 `Try` 狀況時，Visual Basic 會尋找 `Catch` 處理例外狀況的語句。</span><span class="sxs-lookup"><span data-stu-id="f1812-147">When an exception is thrown in a `Try` block, Visual Basic looks for the `Catch` statement that handles the exception.</span></span> <span data-ttu-id="f1812-148">如果找不到相符的 `Catch` 語句，Visual Basic 會檢查呼叫目前方法的方法，並在呼叫堆疊上開啟。</span><span class="sxs-lookup"><span data-stu-id="f1812-148">If a matching `Catch` statement is not found, Visual Basic examines the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="f1812-149">如果 `Catch` 找不到任何區塊，Visual Basic 會向使用者顯示未處理的例外狀況訊息，並停止執行程式。</span><span class="sxs-lookup"><span data-stu-id="f1812-149">If no `Catch` block is found, Visual Basic displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="f1812-150">您可以在語句中使用一個以上的 `Catch` 語句 `Try…Catch` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-150">You can use more than one `Catch` statement in a `Try…Catch` statement.</span></span> <span data-ttu-id="f1812-151">如果您這樣做，子句的順序 `Catch` 很重要，因為它們會依序進行檢查。</span><span class="sxs-lookup"><span data-stu-id="f1812-151">If you do this, the order of the `Catch` clauses is significant because they are examined in order.</span></span> <span data-ttu-id="f1812-152">在較不特定的例外狀況之前攔截較特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-152">Catch the more specific exceptions before the less specific ones.</span></span>

<span data-ttu-id="f1812-153">下列 `Catch` 語句條件是最不明確的，而且會攔截所有衍生自類別的例外狀況 <xref:System.Exception> 。</span><span class="sxs-lookup"><span data-stu-id="f1812-153">The following `Catch` statement conditions are the least specific, and will catch all exceptions that derive from the <xref:System.Exception> class.</span></span> <span data-ttu-id="f1812-154">在 `Catch` `Try...Catch...Finally` 捕捉到您預期的所有特定例外狀況之後，通常應該使用這些變化之一做為結構中的最後一個區塊。</span><span class="sxs-lookup"><span data-stu-id="f1812-154">You should ordinarily use one of these variations as the last `Catch` block in the `Try...Catch...Finally` structure, after catching all the specific exceptions you expect.</span></span> <span data-ttu-id="f1812-155">控制流程永遠不能觸及 `Catch` 遵循下列其中一種變化的區塊。</span><span class="sxs-lookup"><span data-stu-id="f1812-155">Control flow can never reach a `Catch` block that follows either of these variations.</span></span>

- <span data-ttu-id="f1812-156">`type`是 `Exception` ，例如：`Catch ex As Exception`</span><span class="sxs-lookup"><span data-stu-id="f1812-156">The `type` is `Exception`, for example: `Catch ex As Exception`</span></span>

- <span data-ttu-id="f1812-157">語句沒有 `exception` 變數，例如：`Catch`</span><span class="sxs-lookup"><span data-stu-id="f1812-157">The statement has no `exception` variable, for example: `Catch`</span></span>

<span data-ttu-id="f1812-158">當 `Try…Catch…Finally` 語句嵌套于另一個 `Try` 區塊時，Visual Basic 會先檢查 `Catch` 最內層區塊中的每個語句 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-158">When a `Try…Catch…Finally` statement is nested in another `Try` block, Visual Basic first examines each `Catch` statement in the innermost `Try` block.</span></span> <span data-ttu-id="f1812-159">如果找不到相符 `Catch` 的語句，搜尋會繼續進行 `Catch` 外部區塊的語句 `Try…Catch…Finally` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-159">If no matching `Catch` statement is found, the search proceeds to the `Catch` statements of the outer `Try…Catch…Finally` block.</span></span>

<span data-ttu-id="f1812-160">區塊中的本機變數 `Try` 無法在區塊中使用， `Catch` 因為它們是個別的區塊。</span><span class="sxs-lookup"><span data-stu-id="f1812-160">Local variables from a `Try` block are not available in a `Catch` block because they are separate blocks.</span></span> <span data-ttu-id="f1812-161">如果您想要在多個區塊中使用變數，請在結構外宣告變數 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-161">If you want to use a variable in more than one block, declare the variable outside the `Try...Catch...Finally` structure.</span></span>

> [!TIP]
> <span data-ttu-id="f1812-162">`Try…Catch…Finally`語句是以 IntelliSense 程式碼片段的形式提供。</span><span class="sxs-lookup"><span data-stu-id="f1812-162">The `Try…Catch…Finally` statement is available as an IntelliSense code snippet.</span></span> <span data-ttu-id="f1812-163">在 [程式碼片段管理員] 中，展開 [**程式碼模式]-如果每個都嘗試 Catch、Property 等**，然後再進行**錯誤處理（例外狀況）**。</span><span class="sxs-lookup"><span data-stu-id="f1812-163">In the Code Snippets Manager, expand **Code Patterns - If, For Each, Try Catch, Property, etc**, and then **Error Handling (Exceptions)**.</span></span> <span data-ttu-id="f1812-164">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="f1812-164">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>

## <a name="finally-block"></a><span data-ttu-id="f1812-165">Finally 區塊</span><span class="sxs-lookup"><span data-stu-id="f1812-165">Finally block</span></span>

<span data-ttu-id="f1812-166">如果您有一或多個必須在結束結構之前執行的語句 `Try` ，請使用 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="f1812-166">If you have one or more statements that must run before you exit the `Try` structure, use a `Finally` block.</span></span> <span data-ttu-id="f1812-167">控制項在 `Finally` 傳入結構之前就會傳遞至區塊 `Try…Catch` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-167">Control passes to the `Finally` block just before it passes out of the `Try…Catch` structure.</span></span> <span data-ttu-id="f1812-168">即使在結構內的任何位置發生例外狀況，也是如此 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-168">This is true even if an exception occurs anywhere inside the `Try` structure.</span></span>

<span data-ttu-id="f1812-169">`Finally`區塊適用于執行任何必須執行的程式碼，即使發生例外狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="f1812-169">A `Finally` block is useful for running any code that must execute even if there is an exception.</span></span> <span data-ttu-id="f1812-170">不論區塊結束的方式為何，控制項都會傳遞至 `Finally` 區塊 `Try...Catch` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-170">Control is passed to the `Finally` block regardless of how the `Try...Catch` block exits.</span></span>

<span data-ttu-id="f1812-171">`Finally`即使您的程式碼在 `Return` 或區塊中遇到語句，區塊中的程式碼還是會執行 `Try` `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-171">The code in a `Finally` block runs even if your code encounters a `Return` statement in a `Try` or `Catch` block.</span></span> <span data-ttu-id="f1812-172">在下列情況下，控制項不會從 `Try` 或 `Catch` 區塊傳遞至對應的 `Finally` 區塊：</span><span class="sxs-lookup"><span data-stu-id="f1812-172">Control does not pass from a `Try` or `Catch` block to the corresponding `Finally` block in the following cases:</span></span>

- <span data-ttu-id="f1812-173">在或區塊中遇到[End 語句](end-statement.md) `Try` `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-173">An [End Statement](end-statement.md) is encountered in the `Try` or `Catch` block.</span></span>

- <span data-ttu-id="f1812-174"><xref:System.StackOverflowException>或區塊中擲回 `Try` `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-174">A <xref:System.StackOverflowException> is thrown in the `Try` or `Catch` block.</span></span>

<span data-ttu-id="f1812-175">將執行明確轉移到區塊中是不正確 `Finally` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-175">It is not valid to explicitly transfer execution into a `Finally` block.</span></span> <span data-ttu-id="f1812-176">`Finally`除了例外狀況之外，從區塊傳出執行是不正確。</span><span class="sxs-lookup"><span data-stu-id="f1812-176">Transferring execution out of a `Finally` block is not valid, except through an exception.</span></span>

<span data-ttu-id="f1812-177">如果 `Try` 語句未包含至少一個 `Catch` 區塊，它必須包含一個 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="f1812-177">If a `Try` statement does not contain at least one `Catch` block, it must contain a `Finally` block.</span></span>

> [!TIP]
> <span data-ttu-id="f1812-178">如果您不需要攔截特定的例外狀況，則 `Using` 語句的行為就像 `Try…Finally` 區塊，並保證資源的處置，不論您如何結束區塊。</span><span class="sxs-lookup"><span data-stu-id="f1812-178">If you do not have to catch specific exceptions, the `Using` statement behaves like a `Try…Finally` block, and guarantees disposal of the resources, regardless of how you exit the block.</span></span> <span data-ttu-id="f1812-179">即使有未處理的例外狀況，也是如此。</span><span class="sxs-lookup"><span data-stu-id="f1812-179">This is true even with an unhandled exception.</span></span> <span data-ttu-id="f1812-180">如需詳細資訊，請參閱[Using 語句](using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f1812-180">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="exception-argument"></a><span data-ttu-id="f1812-181">Exception 引數</span><span class="sxs-lookup"><span data-stu-id="f1812-181">Exception argument</span></span>

<span data-ttu-id="f1812-182">`Catch`Block `exception` 引數是類別的實例， <xref:System.Exception> 或衍生自類別的類別 `Exception` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-182">The `Catch` block `exception` argument is an instance of the <xref:System.Exception> class or a class that derives from the `Exception` class.</span></span> <span data-ttu-id="f1812-183">`Exception`類別實例會對應到區塊中發生的錯誤 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-183">The `Exception` class instance corresponds to the error that occurred in the `Try` block.</span></span>

<span data-ttu-id="f1812-184">物件的屬性 `Exception` 有助於找出例外狀況的原因和位置。</span><span class="sxs-lookup"><span data-stu-id="f1812-184">The properties of the `Exception` object help to identify the cause and location of an exception.</span></span> <span data-ttu-id="f1812-185">例如， <xref:System.Exception.StackTrace%2A> 屬性會列出導致例外狀況的被呼叫方法，協助您找出程式碼中發生錯誤的位置。</span><span class="sxs-lookup"><span data-stu-id="f1812-185">For example, the <xref:System.Exception.StackTrace%2A> property lists the called methods that led to the exception, helping you find where the error occurred in the code.</span></span> <span data-ttu-id="f1812-186"><xref:System.Exception.Message%2A>傳回描述例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="f1812-186"><xref:System.Exception.Message%2A> returns a message that describes the exception.</span></span> <span data-ttu-id="f1812-187"><xref:System.Exception.HelpLink%2A>傳回關聯之說明檔的連結。</span><span class="sxs-lookup"><span data-stu-id="f1812-187"><xref:System.Exception.HelpLink%2A> returns a link to an associated Help file.</span></span> <span data-ttu-id="f1812-188"><xref:System.Exception.InnerException%2A>傳回 `Exception` 造成目前例外狀況的物件，如果沒有原始的則傳回 `Nothing` `Exception` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-188"><xref:System.Exception.InnerException%2A> returns the `Exception` object that caused the current exception, or it returns `Nothing` if there is no original `Exception`.</span></span>

## <a name="considerations-when-using-a-trycatch-statement"></a><span data-ttu-id="f1812-189">使用 [嘗試 ...] 時的考慮Catch 語句</span><span class="sxs-lookup"><span data-stu-id="f1812-189">Considerations when using a Try…Catch statement</span></span>

<span data-ttu-id="f1812-190">僅使用 `Try…Catch` 語句來表示發生異常或意外的程式事件。</span><span class="sxs-lookup"><span data-stu-id="f1812-190">Use a `Try…Catch` statement only to signal the occurrence of unusual or unanticipated program events.</span></span> <span data-ttu-id="f1812-191">其原因包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="f1812-191">Reasons for this include the following:</span></span>

- <span data-ttu-id="f1812-192">在執行時間攔截例外狀況會產生額外的負荷，而且可能比預先檢查來避免例外狀況的速度慢。</span><span class="sxs-lookup"><span data-stu-id="f1812-192">Catching exceptions at runtime creates additional overhead, and is likely to be slower than pre-checking to avoid exceptions.</span></span>

- <span data-ttu-id="f1812-193">如果 `Catch` 未正確處理區塊，則例外狀況可能不會正確地回報給使用者。</span><span class="sxs-lookup"><span data-stu-id="f1812-193">If a `Catch` block is not handled correctly, the exception might not be reported correctly to users.</span></span>

- <span data-ttu-id="f1812-194">例外狀況處理會使程式變得更複雜。</span><span class="sxs-lookup"><span data-stu-id="f1812-194">Exception handling makes a program more complex.</span></span>

<span data-ttu-id="f1812-195">您不一定需要 `Try…Catch` 語句來檢查是否有可能發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-195">You do not always need a `Try…Catch` statement to check for a condition that is likely to occur.</span></span> <span data-ttu-id="f1812-196">下列範例會先檢查檔案是否存在，然後再嘗試開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="f1812-196">The following example checks whether a file exists before trying to open it.</span></span> <span data-ttu-id="f1812-197">這可減少攔截方法所擲回之例外狀況的需要 <xref:System.IO.File.OpenText%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f1812-197">This reduces the need for catching an exception thrown by the <xref:System.IO.File.OpenText%2A> method.</span></span>

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

<span data-ttu-id="f1812-198">請確定區塊中的程式碼 `Catch` 可以正確地向使用者報告例外狀況，不論是透過安全線程記錄或適當的訊息。</span><span class="sxs-lookup"><span data-stu-id="f1812-198">Ensure that code in `Catch` blocks can properly report exceptions to users, whether through thread-safe logging or appropriate messages.</span></span> <span data-ttu-id="f1812-199">否則，例外狀況可能會維持不明。</span><span class="sxs-lookup"><span data-stu-id="f1812-199">Otherwise, exceptions might remain unknown.</span></span>

## <a name="async-methods"></a><span data-ttu-id="f1812-200">非同步方法</span><span class="sxs-lookup"><span data-stu-id="f1812-200">Async methods</span></span>

<span data-ttu-id="f1812-201">如果您使用[Async](../modifiers/async.md)修飾詞來標示方法，則可以在方法中使用[Await](../operators/await-operator.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="f1812-201">If you mark a method with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the method.</span></span> <span data-ttu-id="f1812-202">具有運算子的語句會 `Await` 暫停執行方法，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="f1812-202">A statement with the `Await` operator suspends execution of the method until the awaited task completes.</span></span> <span data-ttu-id="f1812-203">工作代表進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="f1812-203">The task represents ongoing work.</span></span> <span data-ttu-id="f1812-204">當與運算子相關聯的工作 `Await` 完成時，會在相同的方法中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="f1812-204">When the task that's associated with the `Await` operator finishes, execution resumes in the same method.</span></span> <span data-ttu-id="f1812-205">如需詳細資訊，請參閱[非同步程式中的控制流程](../../programming-guide/concepts/async/control-flow-in-async-programs.md)。</span><span class="sxs-lookup"><span data-stu-id="f1812-205">For more information, see [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>

<span data-ttu-id="f1812-206">非同步方法傳回的工作可能會以錯誤狀態結束，表示它已因未處理的例外狀況而完成。</span><span class="sxs-lookup"><span data-stu-id="f1812-206">A task returned by an Async method may end in a faulted state, indicating that it completed due to an unhandled exception.</span></span> <span data-ttu-id="f1812-207">工作可能也會以取消的狀態結束，這會導致 `OperationCanceledException` 從 await 運算式擲回。</span><span class="sxs-lookup"><span data-stu-id="f1812-207">A task may also end in a canceled state, which results in an `OperationCanceledException` being thrown out of the await expression.</span></span> <span data-ttu-id="f1812-208">若要攔截任一類型的例外狀況，請將 `Await` 與工作相關聯的運算式放在區塊中， `Try` 並攔截區塊中的例外狀況 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-208">To catch either type of exception, place the `Await` expression that's associated with the task in a `Try` block, and catch the exception in the `Catch` block.</span></span> <span data-ttu-id="f1812-209">本主題稍後會提供範例。</span><span class="sxs-lookup"><span data-stu-id="f1812-209">An example is provided later in this topic.</span></span>

<span data-ttu-id="f1812-210">工作可能處於錯誤狀態，因為有多個例外狀況負責其錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1812-210">A task can be in a faulted state because multiple exceptions were responsible for its faulting.</span></span> <span data-ttu-id="f1812-211">例如，工作可能是對 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="f1812-211">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f1812-212">當您等候這類工作時，攔截到的例外狀況只是其中一個例外狀況，而且您無法預測會攔截到哪個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-212">When you await such a task, the caught exception is only one of the exceptions, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="f1812-213">本主題稍後會提供範例。</span><span class="sxs-lookup"><span data-stu-id="f1812-213">An example is provided later in this topic.</span></span>

<span data-ttu-id="f1812-214">`Await`運算式不能在 `Catch` 區塊或區塊內 `Finally` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-214">An `Await` expression can't be inside a `Catch` block or `Finally` block.</span></span>

## <a name="iterators"></a><span data-ttu-id="f1812-215">迭代器</span><span class="sxs-lookup"><span data-stu-id="f1812-215">Iterators</span></span>

<span data-ttu-id="f1812-216">反覆運算器函數或存取子會在 `Get` 集合上執行自訂反復專案。</span><span class="sxs-lookup"><span data-stu-id="f1812-216">An iterator function or `Get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="f1812-217">反覆運算器會使用[Yield](yield-statement.md)語句，一次傳回集合中的每個元素。</span><span class="sxs-lookup"><span data-stu-id="f1812-217">An iterator uses a [Yield](yield-statement.md) statement to return each element of the collection one at a time.</span></span> <span data-ttu-id="f1812-218">您可以使用[For Each ... 來呼叫 iterator 函數。下一個語句](for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f1812-218">You call an iterator function by using a [For Each...Next Statement](for-each-next-statement.md).</span></span>

<span data-ttu-id="f1812-219">`Yield`語句可以在 `Try` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="f1812-219">A `Yield` statement can be inside a `Try` block.</span></span> <span data-ttu-id="f1812-220">`Try`包含語句的區塊 `Yield` 可以有 `Catch` 區塊，而且可以有 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="f1812-220">A `Try` block that contains a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span> <span data-ttu-id="f1812-221">如需範例，請參閱[反覆運算](../../programming-guide/concepts/iterators.md)器的「在 Visual Basic 中嘗試區塊」一節。</span><span class="sxs-lookup"><span data-stu-id="f1812-221">See the "Try Blocks in Visual Basic" section of [Iterators](../../programming-guide/concepts/iterators.md) for an example.</span></span>

<span data-ttu-id="f1812-222">`Yield`語句不能在 `Catch` 區塊或 `Finally` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="f1812-222">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="f1812-223">如果 `For Each` 主體（iterator 函式之外）擲回例外狀況， `Catch` 則不會執行 iterator 函式中的區塊，但 `Finally` 會執行 iterator 函式中的區塊。</span><span class="sxs-lookup"><span data-stu-id="f1812-223">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="f1812-224">`Catch`Iterator 函式內的區塊只會攔截反覆運算器函數內所發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-224">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="partial-trust-situations"></a><span data-ttu-id="f1812-225">部分信任的情況</span><span class="sxs-lookup"><span data-stu-id="f1812-225">Partial-trust situations</span></span>

<span data-ttu-id="f1812-226">在部分信任的情況下，例如在網路共用上裝載的應用程式， `Try...Catch...Finally` 並不會攔截在叫用包含呼叫之方法之前發生的安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-226">In partial-trust situations, such as an application hosted on a network share, `Try...Catch...Finally` does not catch security exceptions that occur before the method that contains the call is invoked.</span></span> <span data-ttu-id="f1812-227">下列範例中，當您將它放在伺服器共用並從該處執行時，會產生錯誤「SecurityException：要求失敗。」</span><span class="sxs-lookup"><span data-stu-id="f1812-227">The following example, when you put it on a server share and run from there, produces the error "System.Security.SecurityException: Request Failed."</span></span> <span data-ttu-id="f1812-228">如需安全性例外狀況的詳細資訊，請參閱 <xref:System.Security.SecurityException> 類別。</span><span class="sxs-lookup"><span data-stu-id="f1812-228">For more information about security exceptions, see the <xref:System.Security.SecurityException> class.</span></span>

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

<span data-ttu-id="f1812-229">在這種部分信任的情況下，您必須將 `Process.Start` 語句放在不同的 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-229">In such a partial-trust situation, you have to put the `Process.Start` statement in a separate `Sub`.</span></span> <span data-ttu-id="f1812-230">的初始呼叫 `Sub` 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f1812-230">The initial call to the `Sub` will fail.</span></span> <span data-ttu-id="f1812-231">這可讓在 `Try...Catch` 啟動包含的之前攔截它 `Sub` `Process.Start` ，並產生安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-231">This enables `Try...Catch` to catch it before the `Sub` that contains `Process.Start` is started and the security exception produced.</span></span>

## <a name="examples"></a><span data-ttu-id="f1812-232">範例</span><span class="sxs-lookup"><span data-stu-id="f1812-232">Examples</span></span>

### <a name="the-structure-of-trycatchfinally"></a><span data-ttu-id="f1812-233">Try 的結構 .。。Catch .。。一點</span><span class="sxs-lookup"><span data-stu-id="f1812-233">The structure of Try...Catch...Finally</span></span>

<span data-ttu-id="f1812-234">下列範例說明語句的結構 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-234">The following example illustrates the structure of the `Try...Catch...Finally` statement.</span></span>

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a><span data-ttu-id="f1812-235">從 Try 區塊呼叫的方法中發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="f1812-235">Exception in a method called from a Try block</span></span>

<span data-ttu-id="f1812-236">在下列範例中，方法會擲回 `CreateException` `NullReferenceException` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-236">In the following example, the `CreateException` method throws a `NullReferenceException`.</span></span> <span data-ttu-id="f1812-237">產生例外狀況的程式碼不在區塊中 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-237">The code that generates the exception is not in a `Try` block.</span></span> <span data-ttu-id="f1812-238">因此， `CreateException` 方法不會處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-238">Therefore, the `CreateException` method does not handle the exception.</span></span> <span data-ttu-id="f1812-239">`RunSample`方法會處理例外狀況，因為方法的呼叫 `CreateException` 是在 `Try` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="f1812-239">The `RunSample` method does handle the exception because the call to the `CreateException` method is in a `Try` block.</span></span>

<span data-ttu-id="f1812-240">此範例包含 `Catch` 數個例外狀況類型的語句，從最特定到最常見的順序排序。</span><span class="sxs-lookup"><span data-stu-id="f1812-240">The example includes `Catch` statements for several types of exceptions, ordered from the most specific to the most general.</span></span>

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a><span data-ttu-id="f1812-241">Catch When 語句</span><span class="sxs-lookup"><span data-stu-id="f1812-241">The Catch When statement</span></span>

<span data-ttu-id="f1812-242">下列範例顯示如何使用 `Catch When` 語句來篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="f1812-242">The following example shows how to use a `Catch When` statement to filter on a conditional expression.</span></span> <span data-ttu-id="f1812-243">如果條件運算式評估為 `True` ，則區塊中的程式碼會 `Catch` 執行。</span><span class="sxs-lookup"><span data-stu-id="f1812-243">If the conditional expression evaluates to `True`, the code in the `Catch` block runs.</span></span>

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a><span data-ttu-id="f1812-244">嵌套的 Try 語句</span><span class="sxs-lookup"><span data-stu-id="f1812-244">Nested Try statements</span></span>

<span data-ttu-id="f1812-245">下列範例包含 `Try…Catch` 包含在區塊中的語句 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-245">The following example has a `Try…Catch` statement that is contained in a `Try` block.</span></span> <span data-ttu-id="f1812-246">內部 `Catch` 區塊會擲回例外狀況， `InnerException` 並將其屬性設定為原始例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-246">The inner `Catch` block throws an exception that has its `InnerException` property set to the original exception.</span></span> <span data-ttu-id="f1812-247">外部 `Catch` 區塊會報告其本身的例外狀況和內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-247">The outer `Catch` block reports its own exception and the inner exception.</span></span>

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a><span data-ttu-id="f1812-248">非同步方法的例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="f1812-248">Exception handling for async methods</span></span>

<span data-ttu-id="f1812-249">下列範例說明非同步方法的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="f1812-249">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="f1812-250">若要攔截適用于非同步工作的例外狀況， `Await` 運算式會在呼叫端的區塊中， `Try` 而例外狀況會在區塊中攔截 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-250">To catch an exception that applies to an async task, the `Await` expression is in a `Try` block of the caller, and the exception is caught in the `Catch` block.</span></span>

<span data-ttu-id="f1812-251">取消註解範例中的 `Throw New Exception` 行來示範例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="f1812-251">Uncomment the `Throw New Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="f1812-252">在區塊中攔截到例外狀況時 `Catch` ，工作的 `IsFaulted` 屬性會設定為 `True` ，而工作的 `Exception.InnerException` 屬性會設定為例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-252">The exception is caught in the `Catch` block, the task's `IsFaulted` property is set to `True`, and the task's `Exception.InnerException` property is set to the exception.</span></span>

<span data-ttu-id="f1812-253">取消註解 `Throw New OperationCancelledException` 行來示範取消非同步處理序時會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f1812-253">Uncomment the `Throw New OperationCancelledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="f1812-254">在區塊中攔截到例外狀況 `Catch` ，而工作的 `IsCanceled` 屬性設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-254">The exception is caught in the `Catch` block, and the task's `IsCanceled` property is set to `True`.</span></span> <span data-ttu-id="f1812-255">不過，在某些不適用此範例的情況下， `IsFaulted` 會設為 `True` ，且 `IsCanceled` 會設定為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-255">However, under some conditions that don't apply to this example, `IsFaulted` is set to `True` and `IsCanceled` is set to `False`.</span></span>

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a><span data-ttu-id="f1812-256">處理非同步方法中的多個例外狀況</span><span class="sxs-lookup"><span data-stu-id="f1812-256">Handling multiple exceptions in async methods</span></span>

<span data-ttu-id="f1812-257">下列範例說明多項工作可能會導致多個例外狀況的例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="f1812-257">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="f1812-258">`Try`區塊具有傳回之 `Await` 工作的運算式 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f1812-258">The `Try` block has the `Await` expression for the task that <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> returned.</span></span> <span data-ttu-id="f1812-259">當套用的三項工作完成時，工作就會完成 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f1812-259">The task is complete when the three tasks to which <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> is applied are complete.</span></span>

<span data-ttu-id="f1812-260">這三個工作都會造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1812-260">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="f1812-261">`Catch`區塊會逐一查看例外狀況，這會在傳回的 `Exception.InnerExceptions` 工作的屬性中找到 `Task.WhenAll` 。</span><span class="sxs-lookup"><span data-stu-id="f1812-261">The `Catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that `Task.WhenAll` returned.</span></span>

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a><span data-ttu-id="f1812-262">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1812-262">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [<span data-ttu-id="f1812-263">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="f1812-263">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="f1812-264">On Error 陳述式</span><span class="sxs-lookup"><span data-stu-id="f1812-264">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="f1812-265">使用程式碼片段的最佳作法</span><span class="sxs-lookup"><span data-stu-id="f1812-265">Best Practices for Using Code Snippets</span></span>](/visualstudio/ide/best-practices-for-using-code-snippets)
- [<span data-ttu-id="f1812-266">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="f1812-266">Exception Handling</span></span>](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [<span data-ttu-id="f1812-267">Throw 語句</span><span class="sxs-lookup"><span data-stu-id="f1812-267">Throw Statement</span></span>](throw-statement.md)
