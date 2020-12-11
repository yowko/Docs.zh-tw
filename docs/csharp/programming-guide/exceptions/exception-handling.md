---
title: 例外狀況處理 - C# 程式設計手冊
description: 瞭解例外狀況處理。 請參閱 try-catch、try-finally 和 try-catch 語句的範例。
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: fabf1413ba498232e67f45460195fe96e25fab0a
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110191"
---
# <a name="exception-handling-c-programming-guide"></a><span data-ttu-id="66c36-104">例外狀況處理 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="66c36-104">Exception Handling (C# Programming Guide)</span></span>

<span data-ttu-id="66c36-105">C# 程式設計人員使用 [try](../../language-reference/keywords/try-catch.md) 區塊分割可能受到例外狀況影響的程式碼。</span><span class="sxs-lookup"><span data-stu-id="66c36-105">A [try](../../language-reference/keywords/try-catch.md) block is used by C# programmers to partition code that might be affected by an exception.</span></span> <span data-ttu-id="66c36-106">相關聯的 [catch](../../language-reference/keywords/try-catch.md) 區塊用來處理任何產生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="66c36-106">Associated [catch](../../language-reference/keywords/try-catch.md) blocks are used to handle any resulting exceptions.</span></span> <span data-ttu-id="66c36-107">[Finally](../../language-reference/keywords/try-finally.md)區塊包含的程式碼會在區塊中擲回例外狀況時執行 `try` ，例如釋放在區塊中配置的資源 `try` 。</span><span class="sxs-lookup"><span data-stu-id="66c36-107">A [finally](../../language-reference/keywords/try-finally.md) block contains code that is run whether or not an exception is thrown in the `try` block, such as releasing resources that are allocated in the `try` block.</span></span> <span data-ttu-id="66c36-108">`try` 區塊需要一或多個相關聯的 `catch` 區塊，或 `finally` 區塊，或兩種都要。</span><span class="sxs-lookup"><span data-stu-id="66c36-108">A `try` block requires one or more associated `catch` blocks, or a `finally` block, or both.</span></span>

<span data-ttu-id="66c36-109">下例示範 `try-catch` 陳述式、`try-finally` 陳述式和 `try-catch-finally` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="66c36-109">The following examples show a `try-catch` statement, a `try-finally` statement, and a `try-catch-finally` statement.</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryFinallyStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchFinallyStructure":::

<span data-ttu-id="66c36-110">`try` 區塊沒有 `catch` 或 `finally` 區塊會造成編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="66c36-110">A `try` block without a `catch` or `finally` block causes a compiler error.</span></span>

## <a name="catch-blocks"></a><span data-ttu-id="66c36-111">catch 區塊</span><span class="sxs-lookup"><span data-stu-id="66c36-111">Catch Blocks</span></span>

<span data-ttu-id="66c36-112">`catch` 區塊可以指定要攔截的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="66c36-112">A `catch` block can specify the type of exception to catch.</span></span> <span data-ttu-id="66c36-113">類型規格稱之為「例外狀況篩選條件」。</span><span class="sxs-lookup"><span data-stu-id="66c36-113">The type specification is called an *exception filter*.</span></span> <span data-ttu-id="66c36-114">例外狀況類型應衍生自 <xref:System.Exception>。</span><span class="sxs-lookup"><span data-stu-id="66c36-114">The exception type should be derived from <xref:System.Exception>.</span></span> <span data-ttu-id="66c36-115">一般而言， <xref:System.Exception> 除非您知道如何處理區塊中可能擲回的所有例外狀況 `try` ，或在區塊結尾包含 [throw](../../language-reference/keywords/throw.md) 語句，否則請勿指定為例外狀況篩選準則 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="66c36-115">In general, don't specify <xref:System.Exception> as the exception filter unless either you know how to handle all exceptions that might be thrown in the `try` block, or you've included a [throw](../../language-reference/keywords/throw.md) statement at the end of your `catch` block.</span></span>

<span data-ttu-id="66c36-116">`catch`具有不同例外狀況類別的多個區塊可以連結在一起。</span><span class="sxs-lookup"><span data-stu-id="66c36-116">Multiple `catch` blocks with different exception classes can be chained together.</span></span> <span data-ttu-id="66c36-117">`catch` 區塊在您的程式碼中是由上往下評估，但每個被擲回的例外狀況只會執行一個 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="66c36-117">The `catch` blocks are evaluated from top to bottom in your code, but only one `catch` block is executed for each exception that is thrown.</span></span> <span data-ttu-id="66c36-118">執行指定確切類型或擲回例外狀況基底類別的第一個 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="66c36-118">The first `catch` block that specifies the exact type or a base class of the thrown exception is executed.</span></span> <span data-ttu-id="66c36-119">如果沒有 `catch` 區塊指定相符的例外狀況類別， `catch` 則會選取沒有任何類型的區塊（如果語句中有一個）。</span><span class="sxs-lookup"><span data-stu-id="66c36-119">If no `catch` block specifies a matching exception class, a `catch` block that doesn't have any type is selected, if one is present in the statement.</span></span> <span data-ttu-id="66c36-120">請務必以 `catch` 最特定的 (定位區塊，也就是最優先的) 例外狀況類別。</span><span class="sxs-lookup"><span data-stu-id="66c36-120">It's important to position `catch` blocks with the most specific (that is, the most derived) exception classes first.</span></span>

<span data-ttu-id="66c36-121">當下列條件成立時，請攔截例外狀況：</span><span class="sxs-lookup"><span data-stu-id="66c36-121">Catch exceptions when the following conditions are true:</span></span>

- <span data-ttu-id="66c36-122">您已經了解例外狀況會擲回的可能原因，而且可以實作特定的復原，例如在您攔截 <xref:System.IO.FileNotFoundException> 物件時，提示使用者輸入新的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="66c36-122">You have a good understanding of why the exception might be thrown, and you can implement a specific recovery, such as prompting the user to enter a new file name when you catch a <xref:System.IO.FileNotFoundException> object.</span></span>
- <span data-ttu-id="66c36-123">您可以建立並擲回更特定的新例外狀況。</span><span class="sxs-lookup"><span data-stu-id="66c36-123">You can create and throw a new, more specific exception.</span></span>
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="ThrowMoreSpecificException":::
- <span data-ttu-id="66c36-124">您想要先稍微處理例外狀況，再傳遞它進行額外處理。</span><span class="sxs-lookup"><span data-stu-id="66c36-124">You want to partially handle an exception before passing it on for additional handling.</span></span> <span data-ttu-id="66c36-125">在下列範例中， `catch` 區塊是用來在重新擲回例外狀況之前將專案加入至錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="66c36-125">In the following example, a `catch` block is used to add an entry to an error log before rethrowing the exception.</span></span>
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="RethrowError":::

<span data-ttu-id="66c36-126">您也可以指定 *例外狀況篩選準則* ，以將布林運算式加入至 catch 子句。</span><span class="sxs-lookup"><span data-stu-id="66c36-126">You can also specify *exception filters* to add a boolean expression to a catch clause.</span></span> <span data-ttu-id="66c36-127">這些表示特定的 catch 子句只有在條件為 true 時才會符合。</span><span class="sxs-lookup"><span data-stu-id="66c36-127">These indicate that a specific catch clause matches only when that condition is true.</span></span> <span data-ttu-id="66c36-128">在下列範例中，兩個 catch 子句都會使用相同的例外狀況類別，但會檢查額外的條件來建立不同的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="66c36-128">In the following example, both catch clauses use the same exception class, but an additional condition is checked to create a different error message:</span></span>

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="DemonstrateExceptionFilter":::

<span data-ttu-id="66c36-129">一律傳回的例外狀況篩選準則 `false` 可以用來檢查所有例外狀況，但不能處理它們。</span><span class="sxs-lookup"><span data-stu-id="66c36-129">An exception filter that always returns `false` can be used to examine all exceptions but not process them.</span></span> <span data-ttu-id="66c36-130">一般用途是記錄例外狀況：</span><span class="sxs-lookup"><span data-stu-id="66c36-130">A typical use is to log exceptions:</span></span>

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="ShowExceptionFilter":::

<span data-ttu-id="66c36-131">`LogException`方法一律會傳回 `false` ，不會有 `catch` 使用這個例外狀況篩選準則的子句相符。</span><span class="sxs-lookup"><span data-stu-id="66c36-131">The `LogException` method always returns `false`, no `catch` clause using this exception filter matches.</span></span> <span data-ttu-id="66c36-132">Catch 子句可以是一般，使用 <xref:System.Exception?displayProperty=nameWithType> 和更新的子句可以處理更明確的例外狀況類別。</span><span class="sxs-lookup"><span data-stu-id="66c36-132">The catch clause can be general, using <xref:System.Exception?displayProperty=nameWithType>, and later clauses can process more specific exception classes.</span></span>

## <a name="finally-blocks"></a><span data-ttu-id="66c36-133">Finally 區塊</span><span class="sxs-lookup"><span data-stu-id="66c36-133">Finally Blocks</span></span>

<span data-ttu-id="66c36-134">`finally` 區塊可讓您清除 `try` 區塊中執行過的動作。</span><span class="sxs-lookup"><span data-stu-id="66c36-134">A `finally` block enables you to clean up actions that are performed in a `try` block.</span></span> <span data-ttu-id="66c36-135">如果有的話，`finally` 區塊會最後執行，在 `try` 區塊和任何符合的 `catch` 區塊之後。</span><span class="sxs-lookup"><span data-stu-id="66c36-135">If present, the `finally` block executes last, after the `try` block and any matched `catch` block.</span></span> <span data-ttu-id="66c36-136">`finally`區塊一律會執行、是否擲回例外狀況，或 `catch` 找到符合例外狀況類型的區塊。</span><span class="sxs-lookup"><span data-stu-id="66c36-136">A `finally` block always runs, whether an exception is thrown or a `catch` block matching the exception type is found.</span></span>

<span data-ttu-id="66c36-137">`finally` 區塊可以用來釋放資源，例如檔案資料流、資料庫連接及圖形控點，不必等待執行階段的記憶體回收行程完成物件。</span><span class="sxs-lookup"><span data-stu-id="66c36-137">The `finally` block can be used to release resources such as file streams, database connections, and graphics handles without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="66c36-138">如需詳細資訊，請參閱 [Using 語句](../../language-reference/keywords/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="66c36-138">For more information See the [using Statement](../../language-reference/keywords/using-statement.md).</span></span>

<span data-ttu-id="66c36-139">在下例中，`finally` 區塊用來關閉在 `try` 區塊中開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="66c36-139">In the following example, the `finally` block is used to close a file that is opened in the `try` block.</span></span> <span data-ttu-id="66c36-140">請注意，檔案關閉前已檢查過檔案控制代碼的狀態。</span><span class="sxs-lookup"><span data-stu-id="66c36-140">Notice that the state of the file handle is checked before the file is closed.</span></span> <span data-ttu-id="66c36-141">如果 `try` 區塊無法開啟檔案，檔案控制代碼仍具有值 `null` ，而且 `finally` 區塊不會嘗試關閉它。</span><span class="sxs-lookup"><span data-stu-id="66c36-141">If the `try` block can't open the file, the file handle still has the value `null` and the `finally` block doesn't try to close it.</span></span> <span data-ttu-id="66c36-142">相反地，如果檔案已成功在區塊中開啟 `try` ，則 `finally` 區塊會關閉開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="66c36-142">Instead, if the file is opened successfully in the `try` block, the `finally` block closes the open file.</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" id="CleanupIfNotNull":::

## <a name="c-language-specification"></a><span data-ttu-id="66c36-143">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="66c36-143">C# Language Specification</span></span>

<span data-ttu-id="66c36-144">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[例外狀況](~/_csharplang/spec/exceptions.md)與 [try 陳述式](~/_csharplang/spec/statements.md#the-try-statement)。</span><span class="sxs-lookup"><span data-stu-id="66c36-144">For more information, see [Exceptions](~/_csharplang/spec/exceptions.md) and [The try statement](~/_csharplang/spec/statements.md#the-try-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="66c36-145">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="66c36-145">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="66c36-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66c36-146">See also</span></span>

- [<span data-ttu-id="66c36-147">C # 參考</span><span class="sxs-lookup"><span data-stu-id="66c36-147">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="66c36-148">try-catch</span><span class="sxs-lookup"><span data-stu-id="66c36-148">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="66c36-149">try-finally</span><span class="sxs-lookup"><span data-stu-id="66c36-149">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="66c36-150">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="66c36-150">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
- [<span data-ttu-id="66c36-151">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="66c36-151">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
