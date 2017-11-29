---
title: "try-finally (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 927b851419f2c5245518ee39bf847cb1f1664917
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="9d7f6-102">try-finally (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9d7f6-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="9d7f6-103">使用 `finally` 區塊，即可清除 [try](../../../csharp/language-reference/keywords/try-catch.md) 區塊中所配置的任何資源，以及執行程式碼，即使 `try` 區塊中發生例外狀況也是一樣。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="9d7f6-104">一般而言，會在控制權離開 `try` 陳述式時，執行 `finally` 區塊的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="9d7f6-105">控制權轉移可能是正常執行、執行 `break`、`continue`、`goto` 或 `return` 陳述式，或是傳播 `try` 陳述式的例外狀況所造成。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="9d7f6-106">在處理的例外狀況內，一定會執行關聯的 `finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="9d7f6-107">不過，如果無法處理例外狀況，則執行 `finally` 區塊取決於如何觸發例外狀況回溯作業。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="9d7f6-108">接著，取決於您電腦的設定方式。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-108">That, in turn, is dependent on how your computer is set up.</span></span>
  
 <span data-ttu-id="9d7f6-109">通常，未處理的例外狀況結束應用程式時，是否執行 `finally` 區塊並不重要。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="9d7f6-110">不過，如果您的 `finally` 區塊中有即使在這種情況下都必須執行的陳述式，則其中一個解決方案是將 `catch` 區塊新增至 `try`-`finally` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="9d7f6-111">或者，您可以攔截可能會在呼叫堆疊較高之 `try`-`finally` 陳述式的 `try` 區塊中擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="9d7f6-112">亦即，您可以攔截下列方法中的例外狀況：呼叫包含 `try`-`finally` 陳述式的方法、呼叫該方法的方法，或呼叫堆疊的任何方法。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="9d7f6-113">如果未攔截到例外狀況，則執行 `finally` 區塊取決於作業系統是否選擇觸發例外狀況回溯作業。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d7f6-114">範例</span><span class="sxs-lookup"><span data-stu-id="9d7f6-114">Example</span></span>  
 <span data-ttu-id="9d7f6-115">在下列範例中，無效的轉換陳述式會導致 `System.InvalidCastException` 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="9d7f6-116">例外狀況未進行處理。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-116">The exception is unhandled.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 <span data-ttu-id="9d7f6-117">在下列範例中，會攔截到來自呼叫堆疊最遠的方法中之 `TryCast` 方法的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 <span data-ttu-id="9d7f6-118">如需 `finally` 的詳細資訊，請參閱 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-118">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="9d7f6-119">C# 也會包含 [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)，以透過方便使用的語法提供 <xref:System.IDisposable> 物件的類似功能。</span><span class="sxs-lookup"><span data-stu-id="9d7f6-119">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9d7f6-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9d7f6-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d7f6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d7f6-121">See Also</span></span>  
 [<span data-ttu-id="9d7f6-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9d7f6-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9d7f6-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9d7f6-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9d7f6-124">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="9d7f6-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9d7f6-125">try、throw 和 catch 陳述式 (C++)</span><span class="sxs-lookup"><span data-stu-id="9d7f6-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="9d7f6-126">例外狀況處理陳述式</span><span class="sxs-lookup"><span data-stu-id="9d7f6-126">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="9d7f6-127">throw</span><span class="sxs-lookup"><span data-stu-id="9d7f6-127">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="9d7f6-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="9d7f6-128">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="9d7f6-129">操作說明：明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="9d7f6-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
