---
title: throw (C# 參考)
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 831c4cce14e902697d84129e54cc54f07d26b9f3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43417354"
---
# <a name="throw-c-reference"></a><span data-ttu-id="c639e-102">throw (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c639e-102">throw (C# Reference)</span></span>
<span data-ttu-id="c639e-103">在程式執行期間發出出現例外狀況的訊號。</span><span class="sxs-lookup"><span data-stu-id="c639e-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c639e-104">備註</span><span class="sxs-lookup"><span data-stu-id="c639e-104">Remarks</span></span>

<span data-ttu-id="c639e-105">`throw` 的語法為：</span><span class="sxs-lookup"><span data-stu-id="c639e-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```
<span data-ttu-id="c639e-106">而 `e` 是衍生自 <xref:System.Exception?displayProperty=nameWithType> 之類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c639e-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c639e-107">如果傳遞給 `GetNumber` 方法的引數未對應至內部陣列的有效索引，則下列範例會使用 `throw` 陳述式來擲回  <xref:System.IndexOutOfRangeException> 。</span><span class="sxs-lookup"><span data-stu-id="c639e-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="c639e-108">方法呼叫端接著會使用 `try-catch` 或 `try-catch-finally` 區塊來處理所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c639e-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="c639e-109">下列範例會處理 `GetNumber` 方法所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c639e-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="c639e-110">重新擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="c639e-110">Re-throwing an exception</span></span>

<span data-ttu-id="c639e-111">`throw` 也可以用於 `catch` 區塊，以重新擲回 `catch` 區塊中所處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c639e-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="c639e-112">在此情況下，`throw` 陳述式不接受例外狀況運算元。</span><span class="sxs-lookup"><span data-stu-id="c639e-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="c639e-113">這最適用於當方法將來自呼叫端的引數傳遞給某個其他程式庫方法，且程式庫方法擲回必須傳遞給呼叫端的例外狀況時。</span><span class="sxs-lookup"><span data-stu-id="c639e-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="c639e-114">例如，下列範例會重新擲回 <xref:System.NullReferenceException>，而這是在嘗試擷取未初始化字串的第一個字元時擲回。</span><span class="sxs-lookup"><span data-stu-id="c639e-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span> 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="c639e-115">您也可以使用 `catch` 區塊中的 `throw e` 語法，來具現化傳遞給呼叫端的新例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c639e-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="c639e-116">在此情況下，不會保留原始例外狀況的堆疊追蹤 (可從 <xref:System.Exception.StackTrace> 屬性取得)。</span><span class="sxs-lookup"><span data-stu-id="c639e-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>
 
## <a name="the-throw-expression"></a><span data-ttu-id="c639e-117">`throw` 運算式</span><span class="sxs-lookup"><span data-stu-id="c639e-117">The `throw` expression</span></span>

<span data-ttu-id="c639e-118">從 C# 7.0 開始，`throw` 可以用作運算式和陳述式。</span><span class="sxs-lookup"><span data-stu-id="c639e-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="c639e-119">這可在先前不支援的內容中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c639e-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="c639e-120">它們包括：</span><span class="sxs-lookup"><span data-stu-id="c639e-120">These include:</span></span>

- <span data-ttu-id="c639e-121">[條件運算子](../operators/conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="c639e-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="c639e-122">如果將空字串陣列傳遞給方法，則下列範例會使用 `throw` 運算式來擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="c639e-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="c639e-123">在 C# 7.0 之前，這個邏輯必須出現在 `if`/`else` 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="c639e-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="c639e-124">[Null 聯合運算子](../operators/null-coalescing-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="c639e-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="c639e-125">在下列範例中，如果指派給 `Name` 屬性的字串是 `null`，則搭配使用 `throw` 運算式與 Null 聯合運算子會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c639e-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- <span data-ttu-id="c639e-126">運算式主體 [ambda](../../lambda-expressions.md) 或方法。</span><span class="sxs-lookup"><span data-stu-id="c639e-126">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="c639e-127">下列範例說明因不支援轉換為 <xref:System.DateTime> 值而擲回 <xref:System.InvalidCastException> 的運算式主體方法。</span><span class="sxs-lookup"><span data-stu-id="c639e-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a><span data-ttu-id="c639e-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c639e-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c639e-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="c639e-129">See Also</span></span>

- [<span data-ttu-id="c639e-130">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c639e-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c639e-131">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c639e-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c639e-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="c639e-132">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="c639e-133">C++ 中的 try、catch 和 throw 陳述式</span><span class="sxs-lookup"><span data-stu-id="c639e-133">The try, catch, and throw Statements in C++</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="c639e-134">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c639e-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="c639e-135">例外狀況處理陳述式</span><span class="sxs-lookup"><span data-stu-id="c639e-135">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [<span data-ttu-id="c639e-136">操作說明：明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="c639e-136">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
