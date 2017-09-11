---
title: "throw (C# 參考) | Microsoft Docs"
ms.date: 2015-03-02
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 9f157bf836bafa2f947c9c46f6705568132422fe
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="throw-c-reference"></a><span data-ttu-id="39137-102">throw (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="39137-102">throw (C# Reference)</span></span>
<span data-ttu-id="39137-103">在程式執行期間發出出現例外狀況的訊號。</span><span class="sxs-lookup"><span data-stu-id="39137-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39137-104">備註</span><span class="sxs-lookup"><span data-stu-id="39137-104">Remarks</span></span>

<span data-ttu-id="39137-105">`throw` 的語法為：</span><span class="sxs-lookup"><span data-stu-id="39137-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```
<span data-ttu-id="39137-106">其中 `e` 是衍生自 <xref:System.Exception?displayProperty=fullName> 的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="39137-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=fullName>.</span></span> <span data-ttu-id="39137-107">如果傳遞給 `GetNumber` 方法的引數未對應至內部陣列的有效索引，則下列範例會使用 `throw` 陳述式來擲回 @System.IndexOutOfRangeException。</span><span class="sxs-lookup"><span data-stu-id="39137-107">The following example uses the `throw` statement to throw an @System.IndexOutOfRangeException if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

<span data-ttu-id="39137-108">[!code-cs[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="39137-108">[!code-cs[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]</span></span>  

<span data-ttu-id="39137-109">方法呼叫端接著會使用 `try-catch` 或 `try-catch-finally` 區塊來處理所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="39137-109">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="39137-110">下列範例會處理 `GetNumber` 方法所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="39137-110">The following example handles the exception thrown by the `GetNumber` method.</span></span>

<span data-ttu-id="39137-111">[!code-cs[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="39137-111">[!code-cs[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]</span></span>  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="39137-112">重新擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="39137-112">Re-throwing an exception</span></span>

<span data-ttu-id="39137-113">`throw` 也可以用於 `catch` 區塊，以重新擲回 `catch` 區塊中所處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="39137-113">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="39137-114">在此情況下，`throw` 陳述式不接受例外狀況運算元。</span><span class="sxs-lookup"><span data-stu-id="39137-114">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="39137-115">這最適用於當方法將來自呼叫端的引數傳遞給某個其他程式庫方法，且程式庫方法擲回必須傳遞給呼叫端的例外狀況時。</span><span class="sxs-lookup"><span data-stu-id="39137-115">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="39137-116">例如，下列範例會重新擲回 @System.NullReferenceException，而這是在嘗試擷取未初始化字串的第一個字元時擲回。</span><span class="sxs-lookup"><span data-stu-id="39137-116">For example, the following example re-throws an @System.NullReferenceException that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span> 

<span data-ttu-id="39137-117">[!code-cs[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="39137-117">[!code-cs[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="39137-118">您也可以使用 `catch` 區塊中的 `throw e` 語法，來具現化傳遞給呼叫端的新例外狀況。</span><span class="sxs-lookup"><span data-stu-id="39137-118">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="39137-119">在此情況下，不會保留原始例外狀況的堆疊追蹤 (可從 @System.Exception.Stacktrace 屬性取得)。</span><span class="sxs-lookup"><span data-stu-id="39137-119">In this case, the stack trace of the original exception, which is available from the @System.Exception.Stacktrace property, is not preserved.</span></span>
 
## <a name="the-throw-expression"></a><span data-ttu-id="39137-120">`throw` 運算式</span><span class="sxs-lookup"><span data-stu-id="39137-120">The `throw` expression</span></span>

<span data-ttu-id="39137-121">從 C# 7 開始，`throw` 可以用作運算式和陳述式。</span><span class="sxs-lookup"><span data-stu-id="39137-121">Starting with C# 7, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="39137-122">這可在先前不支援的內容中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="39137-122">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="39137-123">它們包括：</span><span class="sxs-lookup"><span data-stu-id="39137-123">These include:</span></span>

- <span data-ttu-id="39137-124">[條件運算子](../operators/conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="39137-124">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="39137-125">如果將空字串陣列傳遞給方法，則下列範例會使用 `throw` 運算式來擲回 @System.ArgumentException。</span><span class="sxs-lookup"><span data-stu-id="39137-125">The following example uses a `throw` expression to throw an @System.ArgumentException if a method is passed an empty string array.</span></span> <span data-ttu-id="39137-126">在 C# 7 之前，這個邏輯必須出現在 `if`/`else` 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="39137-126">Before C# 7, this logic would need to appear in an `if`/`else` statement.</span></span>

   <span data-ttu-id="39137-127">[!code-cs[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="39137-127">[!code-cs[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]</span></span>  
  
- <span data-ttu-id="39137-128">[Null 聯合運算子](../operators/null-conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="39137-128">[the null-coalescing operator](../operators/null-conditional-operator.md).</span></span> <span data-ttu-id="39137-129">在下列範例中，如果指派給 `Name` 屬性的字串是 `null`，則搭配使用 `throw` 運算式與 Null 聯合運算子會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="39137-129">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>
 
   <span data-ttu-id="39137-130">[!code-cs[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="39137-130">[!code-cs[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]</span></span>  
 
- <span data-ttu-id="39137-131">運算式主體 [ambda](../../lambda-expressions.md) 或方法。</span><span class="sxs-lookup"><span data-stu-id="39137-131">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="39137-132">下列範例說明因不支援轉換為 @System.DateTime 值而擲回 @System.InvalidCastException 的運算式主體方法。</span><span class="sxs-lookup"><span data-stu-id="39137-132">The following example illustrates an expression-bodied method that throws an @System.InvalidCastException because a conversion to a @System.DateTime value is not supported.</span></span>
 
   <span data-ttu-id="39137-133">[!code-cs[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="39137-133">[!code-cs[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]</span></span>  
 
  
## <a name="c-language-specification"></a><span data-ttu-id="39137-134">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="39137-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="39137-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39137-135">See Also</span></span>  
 <span data-ttu-id="39137-136">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="39137-136">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="39137-137"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="39137-137"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="39137-138"> [try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="39137-138"> [try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
<span data-ttu-id="39137-139"> [C++ 中的 try、catch 和 throw 陳述式](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="39137-139"> [The try, catch, and throw Statements in C++](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
<span data-ttu-id="39137-140"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="39137-140"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="39137-141"> [例外狀況處理陳述式](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span><span class="sxs-lookup"><span data-stu-id="39137-141"> [Exception Handling Statements](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span></span>  
<span data-ttu-id="39137-142"> [如何：明確擲回例外狀況](https://msdn.microsoft.com/library/xhcbs8fz)</span><span class="sxs-lookup"><span data-stu-id="39137-142"> [How to: Explicitly Throw Exceptions](https://msdn.microsoft.com/library/xhcbs8fz)</span></span>
