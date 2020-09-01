---
description: throw - C# 參考
title: throw - C# 參考
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 4cad4810b89f976f92ce576917feb2398acce636
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142033"
---
# <a name="throw-c-reference"></a><span data-ttu-id="ac821-103">throw (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ac821-103">throw (C# Reference)</span></span>

<span data-ttu-id="ac821-104">在程式執行期間發出出現例外狀況的訊號。</span><span class="sxs-lookup"><span data-stu-id="ac821-104">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac821-105">備註</span><span class="sxs-lookup"><span data-stu-id="ac821-105">Remarks</span></span>

<span data-ttu-id="ac821-106">`throw` 的語法為：</span><span class="sxs-lookup"><span data-stu-id="ac821-106">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="ac821-107">而 `e` 是衍生自 <xref:System.Exception?displayProperty=nameWithType> 之類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac821-107">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ac821-108">如果傳遞給 `GetNumber` 方法的引數未對應至內部陣列的有效索引，則下列範例會使用 `throw` 陳述式來擲回  <xref:System.IndexOutOfRangeException> 。</span><span class="sxs-lookup"><span data-stu-id="ac821-108">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="ac821-109">方法呼叫端接著會使用 `try-catch` 或 `try-catch-finally` 區塊來處理所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac821-109">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="ac821-110">下列範例會處理 `GetNumber` 方法所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac821-110">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="ac821-111">重新擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="ac821-111">Re-throwing an exception</span></span>

<span data-ttu-id="ac821-112">`throw` 也可以用於 `catch` 區塊，以重新擲回 `catch` 區塊中所處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac821-112">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="ac821-113">在此情況下，`throw` 陳述式不接受例外狀況運算元。</span><span class="sxs-lookup"><span data-stu-id="ac821-113">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="ac821-114">這最適用於當方法將來自呼叫端的引數傳遞給某個其他程式庫方法，且程式庫方法擲回必須傳遞給呼叫端的例外狀況時。</span><span class="sxs-lookup"><span data-stu-id="ac821-114">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="ac821-115">例如，下列範例會重新擲回 <xref:System.NullReferenceException>，而這是在嘗試擷取未初始化字串的第一個字元時擲回。</span><span class="sxs-lookup"><span data-stu-id="ac821-115">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="ac821-116">您也可以使用 `catch` 區塊中的 `throw e` 語法，來具現化傳遞給呼叫端的新例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac821-116">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="ac821-117">在此情況下，不會保留原始例外狀況的堆疊追蹤 (可從 <xref:System.Exception.StackTrace> 屬性取得)。</span><span class="sxs-lookup"><span data-stu-id="ac821-117">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="ac821-118">`throw` 運算式</span><span class="sxs-lookup"><span data-stu-id="ac821-118">The `throw` expression</span></span>

<span data-ttu-id="ac821-119">從 C# 7.0 開始，`throw` 可以用作運算式和陳述式。</span><span class="sxs-lookup"><span data-stu-id="ac821-119">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="ac821-120">這可在先前不支援的內容中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac821-120">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="ac821-121">其中包含：</span><span class="sxs-lookup"><span data-stu-id="ac821-121">These include:</span></span>

- <span data-ttu-id="ac821-122">[條件運算子](../operators/conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="ac821-122">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="ac821-123">如果將空字串陣列傳遞給方法，則下列範例會使用 `throw` 運算式來擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="ac821-123">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="ac821-124">在 C# 7.0 之前，這個邏輯必須出現在 `if`/`else` 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="ac821-124">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="ac821-125">[Null 聯合運算子](../operators/null-coalescing-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="ac821-125">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="ac821-126">在下列範例中，如果指派給 `Name` 屬性的字串是 `null`，則搭配使用 `throw` 運算式與 Null 聯合運算子會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac821-126">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="ac821-127">運算式主體 [ambda](../operators/lambda-expressions.md) 或方法。</span><span class="sxs-lookup"><span data-stu-id="ac821-127">an expression-bodied [lambda](../operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="ac821-128">下列範例說明因不支援轉換為 <xref:System.DateTime> 值而擲回 <xref:System.InvalidCastException> 的運算式主體方法。</span><span class="sxs-lookup"><span data-stu-id="ac821-128">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="ac821-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ac821-129">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ac821-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac821-130">See also</span></span>

- [<span data-ttu-id="ac821-131">C # 參考</span><span class="sxs-lookup"><span data-stu-id="ac821-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ac821-132">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ac821-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ac821-133">try-catch</span><span class="sxs-lookup"><span data-stu-id="ac821-133">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="ac821-134">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ac821-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ac821-135">如何：明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="ac821-135">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
