---
title: 例外狀況處理 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 99a61dc4125d2fe86d70d5051741a1f1f33e58d4
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "43514038"
---
# <a name="exception-handling-c-programming-guide"></a><span data-ttu-id="0e442-102">例外狀況處理 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="0e442-102">Exception Handling (C# Programming Guide)</span></span>
<span data-ttu-id="0e442-103">C# 程式設計人員使用 [try](../../../csharp/language-reference/keywords/try-catch.md) 區塊分割可能受到例外狀況影響的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e442-103">A [try](../../../csharp/language-reference/keywords/try-catch.md) block is used by C# programmers to partition code that might be affected by an exception.</span></span> <span data-ttu-id="0e442-104">相關聯的 [catch](../../../csharp/language-reference/keywords/try-catch.md) 區塊用來處理任何產生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0e442-104">Associated [catch](../../../csharp/language-reference/keywords/try-catch.md) blocks are used to handle any resulting exceptions.</span></span> <span data-ttu-id="0e442-105">無論 `try` 區塊是否擲回例外狀況，[finally](../../../csharp/language-reference/keywords/try-finally.md) 區塊都包含執行的程式碼，例如釋放配置在 `try` 區塊中的資源。</span><span class="sxs-lookup"><span data-stu-id="0e442-105">A [finally](../../../csharp/language-reference/keywords/try-finally.md) block contains code that is run regardless of whether or not an exception is thrown in the `try` block, such as releasing resources that are allocated in the `try` block.</span></span> <span data-ttu-id="0e442-106">`try` 區塊需要一或多個相關聯的 `catch` 區塊，或 `finally` 區塊，或兩種都要。</span><span class="sxs-lookup"><span data-stu-id="0e442-106">A `try` block requires one or more associated `catch` blocks, or a `finally` block, or both.</span></span>  
  
 <span data-ttu-id="0e442-107">下例示範 `try-catch` 陳述式、`try-finally` 陳述式和 `try-catch-finally` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0e442-107">The following examples show a `try-catch` statement, a `try-finally` statement, and a `try-catch-finally` statement.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]  
  
 [!code-csharp[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]  
  
 [!code-csharp[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]  
  
 <span data-ttu-id="0e442-108">`try` 區塊沒有 `catch` 或 `finally` 區塊會造成編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="0e442-108">A `try` block without a `catch` or `finally` block causes a compiler error.</span></span>  
  
## <a name="catch-blocks"></a><span data-ttu-id="0e442-109">catch 區塊</span><span class="sxs-lookup"><span data-stu-id="0e442-109">Catch Blocks</span></span>  
 <span data-ttu-id="0e442-110">`catch` 區塊可以指定要攔截的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="0e442-110">A `catch` block can specify the type of exception to catch.</span></span> <span data-ttu-id="0e442-111">類型規格稱之為「例外狀況篩選條件」。</span><span class="sxs-lookup"><span data-stu-id="0e442-111">The type specification is called an *exception filter*.</span></span> <span data-ttu-id="0e442-112">例外狀況類型應衍生自 <xref:System.Exception>。</span><span class="sxs-lookup"><span data-stu-id="0e442-112">The exception type should be derived from <xref:System.Exception>.</span></span> <span data-ttu-id="0e442-113">一般情況下，不指定 <xref:System.Exception> 為例外狀況篩選條件，除非您知道如何處理 `try` 區塊中可能擲回的所有例外狀況，或您在 `catch` 區塊的結尾已包含 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0e442-113">In general, do not specify <xref:System.Exception> as the exception filter unless either you know how to handle all exceptions that might be thrown in the `try` block, or you have included a [throw](../../../csharp/language-reference/keywords/throw.md) statement at the end of your `catch` block.</span></span>  
  
 <span data-ttu-id="0e442-114">多個 `catch` 區塊有不同的例外狀況篩選條件可以鏈結在一起。</span><span class="sxs-lookup"><span data-stu-id="0e442-114">Multiple `catch` blocks with different exception filters can be chained together.</span></span> <span data-ttu-id="0e442-115">`catch` 區塊在您的程式碼中是由上往下評估，但每個被擲回的例外狀況只會執行一個 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="0e442-115">The `catch` blocks are evaluated from top to bottom in your code, but only one `catch` block is executed for each exception that is thrown.</span></span> <span data-ttu-id="0e442-116">執行指定確切類型或擲回例外狀況基底類別的第一個 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="0e442-116">The first `catch` block that specifies the exact type or a base class of the thrown exception is executed.</span></span> <span data-ttu-id="0e442-117">如果沒有任何 `catch` 區塊指定符合的例外狀況篩選條件，即選取沒有篩選的 `catch` 區塊，如果陳述式中有的話。</span><span class="sxs-lookup"><span data-stu-id="0e442-117">If no `catch` block specifies a matching exception filter, a `catch` block that does not have a filter is selected, if one is present in the statement.</span></span> <span data-ttu-id="0e442-118">請務必先定位 `catch` 區塊和最特定的 (亦即衍生程度最高的) 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0e442-118">It is important to position `catch` blocks with the most specific (that is, the most derived) exception types first.</span></span>  
  
 <span data-ttu-id="0e442-119">當下列條件成立時，您應該攔截例外狀況︰</span><span class="sxs-lookup"><span data-stu-id="0e442-119">You should catch exceptions when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="0e442-120">您已經了解例外狀況會擲回的可能原因，而且可以實作特定的復原，例如在您攔截 <xref:System.IO.FileNotFoundException> 物件時，提示使用者輸入新的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0e442-120">You have a good understanding of why the exception might be thrown, and you can implement a specific recovery, such as prompting the user to enter a new file name when you catch a <xref:System.IO.FileNotFoundException> object.</span></span>  
  
-   <span data-ttu-id="0e442-121">您可以建立並擲回更特定的新例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0e442-121">You can create and throw a new, more specific exception.</span></span>  
  
     [!code-csharp[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]  
  
-   <span data-ttu-id="0e442-122">您想要先稍微處理例外狀況，再傳遞它進行額外處理。</span><span class="sxs-lookup"><span data-stu-id="0e442-122">You want to partially handle an exception before passing it on for additional handling.</span></span> <span data-ttu-id="0e442-123">在下例中，`catch` 區塊是用來在重新擲回例外狀況之前，將項目新增至錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0e442-123">In the following example, a `catch` block is used to add an entry to an error log before re-throwing the exception.</span></span>  
  
     [!code-csharp[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]  
  
## <a name="finally-blocks"></a><span data-ttu-id="0e442-124">Finally 區塊</span><span class="sxs-lookup"><span data-stu-id="0e442-124">Finally Blocks</span></span>  
 <span data-ttu-id="0e442-125">`finally` 區塊可讓您清除 `try` 區塊中執行過的動作。</span><span class="sxs-lookup"><span data-stu-id="0e442-125">A `finally` block enables you to clean up actions that are performed in a `try` block.</span></span> <span data-ttu-id="0e442-126">如果有的話，`finally` 區塊會最後執行，在 `try` 區塊和任何符合的 `catch` 區塊之後。</span><span class="sxs-lookup"><span data-stu-id="0e442-126">If present, the `finally` block executes last, after the `try` block and any matched `catch` block.</span></span> <span data-ttu-id="0e442-127">不論是擲回例外狀況還是找到與例外狀況型別相符的 `catch` 區塊，`finally` 區塊會一律執行。</span><span class="sxs-lookup"><span data-stu-id="0e442-127">A `finally` block always runs, regardless of whether an exception is thrown or a `catch` block matching the exception type is found.</span></span>  
  
 <span data-ttu-id="0e442-128">`finally` 區塊可以用來釋放資源，例如檔案資料流、資料庫連接及圖形控點，不必等待執行階段的記憶體回收行程完成物件。</span><span class="sxs-lookup"><span data-stu-id="0e442-128">The `finally` block can be used to release resources such as file streams, database connections, and graphics handles without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="0e442-129">如需詳細資訊，請參閱 [sing 陳述式](../../../csharp/language-reference/keywords/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0e442-129">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="0e442-130">在下例中，`finally` 區塊用來關閉在 `try` 區塊中開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="0e442-130">In the following example, the `finally` block is used to close a file that is opened in the `try` block.</span></span> <span data-ttu-id="0e442-131">請注意，檔案關閉前已檢查過檔案控制代碼的狀態。</span><span class="sxs-lookup"><span data-stu-id="0e442-131">Notice that the state of the file handle is checked before the file is closed.</span></span> <span data-ttu-id="0e442-132">如果 `try` 區塊無法開啟檔案，檔案控制代碼仍有值 `null`，而 `finally` 區塊不會嘗試關閉它。</span><span class="sxs-lookup"><span data-stu-id="0e442-132">If the `try` block cannot open the file, the file handle still has the value `null` and the `finally` block does not try to close it.</span></span> <span data-ttu-id="0e442-133">或者，如果已成功在 `try` 區塊中開啟檔案，則 `finally` 區塊會關閉開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="0e442-133">Alternatively, if the file is opened successfully in the `try` block, the `finally` block closes the open file.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0e442-134">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0e442-134">C# Language Specification</span></span>  

<span data-ttu-id="0e442-135">如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)的[例外狀況](~/_csharplang/spec/exceptions.md)與 [try 陳述式](~/_csharplang/spec/statements.md#the-try-statement)。</span><span class="sxs-lookup"><span data-stu-id="0e442-135">For more information, see [Exceptions](~/_csharplang/spec/exceptions.md) and [The try statement](~/_csharplang/spec/statements.md#the-try-statement) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="0e442-136">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="0e442-136">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0e442-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e442-137">See Also</span></span>

- [<span data-ttu-id="0e442-138">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0e442-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0e442-139">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0e442-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0e442-140">例外狀況和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="0e442-140">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
- [<span data-ttu-id="0e442-141">try-catch</span><span class="sxs-lookup"><span data-stu-id="0e442-141">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="0e442-142">try-finally</span><span class="sxs-lookup"><span data-stu-id="0e442-142">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
- [<span data-ttu-id="0e442-143">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="0e442-143">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)  
- [<span data-ttu-id="0e442-144">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="0e442-144">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
