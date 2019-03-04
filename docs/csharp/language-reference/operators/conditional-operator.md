---
title: ?:運算子 - C# 參考
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: c3c875cf5b8d1b5e69cd76cb0ee4df0a989a35a0
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202895"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="81fc1-102">?:運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="81fc1-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="81fc1-103">條件運算子 `?:` (通稱為三元條件運算子) 會評估布林運算式，然後根據布林運算式評估為 `true` 或 `false`，傳回評估兩個運算式其中之一的結果。</span><span class="sxs-lookup"><span data-stu-id="81fc1-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="81fc1-104">從 C# 7.2 開始，[條件 ref 運算式](#conditional-ref-expression)會傳回兩個運算式其中之一結果的參考。</span><span class="sxs-lookup"><span data-stu-id="81fc1-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="81fc1-105">條件運算子的語法如下：</span><span class="sxs-lookup"><span data-stu-id="81fc1-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequence : alternative
```

<span data-ttu-id="81fc1-106">`condition` 運算式必須評估為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="81fc1-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="81fc1-107">如果 `condition` 評估為 `true`，就會接著評估 `consequence` 運算式，且其結果會成為運算的結果。</span><span class="sxs-lookup"><span data-stu-id="81fc1-107">If `condition` evaluates to `true`, the `consequence` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="81fc1-108">如果 `condition` 評估為 `false`，則會接著評估 `alternative` 運算式，且其結果會成為運算的結果。</span><span class="sxs-lookup"><span data-stu-id="81fc1-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="81fc1-109">系統只會評估 `consequence` 或 `alternative`。</span><span class="sxs-lookup"><span data-stu-id="81fc1-109">Only `consequence` or `alternative` is evaluated.</span></span>

<span data-ttu-id="81fc1-110">`consequence` 和 `alternative` 的型別必須相同，或是必須有從一個型別轉換成另一型別的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="81fc1-110">The type of `consequence` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="81fc1-111">條件運算子是右向關聯運算子，亦即，以下形式的運算式</span><span class="sxs-lookup"><span data-stu-id="81fc1-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="81fc1-112">評估為</span><span class="sxs-lookup"><span data-stu-id="81fc1-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

<span data-ttu-id="81fc1-113">下列範例示範條件運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="81fc1-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="81fc1-114">條件 ref 運算式</span><span class="sxs-lookup"><span data-stu-id="81fc1-114">Conditional ref expression</span></span>

<span data-ttu-id="81fc1-115">從 C# 7.2 開始，您可以使用條件 ref 運算式來傳回兩個運算式其中之一結果的參考。</span><span class="sxs-lookup"><span data-stu-id="81fc1-115">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="81fc1-116">您可以將該參考指派給 [ref 區域變數](../keywords/ref.md#ref-locals)或[ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals)，或使用它作為[參考傳回值](../keywords/ref.md#reference-return-values)或作為 [`ref` 方法參數](../keywords/ref.md#passing-an-argument-by-reference)。</span><span class="sxs-lookup"><span data-stu-id="81fc1-116">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="81fc1-117">條件 ref 運算式的語法如下：</span><span class="sxs-lookup"><span data-stu-id="81fc1-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequence : ref alternative
```

<span data-ttu-id="81fc1-118">與原始條件運算子相同，條件 ref 運算式只會評估兩個運算式其中之一：`consequence` 或 `alternative`。</span><span class="sxs-lookup"><span data-stu-id="81fc1-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequence` or `alternative`.</span></span>

<span data-ttu-id="81fc1-119">就條件 ref 運算式而言，`consequence` 與 `alternative` 的型別必須相同。</span><span class="sxs-lookup"><span data-stu-id="81fc1-119">In the case of the conditional ref expression, the type of `consequence` and `alternative` must be the same.</span></span>

<span data-ttu-id="81fc1-120">下列範例示範條件 ref 運算式的用法：</span><span class="sxs-lookup"><span data-stu-id="81fc1-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

<span data-ttu-id="81fc1-121">如需詳細資訊，請參閱[功能提案注意事項](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="81fc1-121">For more information, see the [feature proposal note](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="81fc1-122">條件運算子和 `if..else` 陳述式</span><span class="sxs-lookup"><span data-stu-id="81fc1-122">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="81fc1-123">當您需要依據條件計算某個值時，透過 [if-else](../keywords/if-else.md) 陳述式使用條件運算子可能使程式碼更為簡潔。</span><span class="sxs-lookup"><span data-stu-id="81fc1-123">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="81fc1-124">下列範例示範兩種將整數分類為負值或非負值的方法：</span><span class="sxs-lookup"><span data-stu-id="81fc1-124">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="81fc1-125">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="81fc1-125">Operator overloadability</span></span>

<span data-ttu-id="81fc1-126">條件運算子不能多載。</span><span class="sxs-lookup"><span data-stu-id="81fc1-126">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="81fc1-127">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="81fc1-127">C# language specification</span></span>

<span data-ttu-id="81fc1-128">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[條件運算子](~/_csharplang/spec/expressions.md#conditional-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="81fc1-128">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81fc1-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81fc1-129">See also</span></span>

- [<span data-ttu-id="81fc1-130">C# 參考</span><span class="sxs-lookup"><span data-stu-id="81fc1-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="81fc1-131">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="81fc1-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="81fc1-132">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="81fc1-132">C# Operators</span></span>](index.md)
- [<span data-ttu-id="81fc1-133">if-else 陳述式</span><span class="sxs-lookup"><span data-stu-id="81fc1-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="81fc1-134">[?. 和 ?[] 運算子](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="81fc1-134">[?. and ?[] Operators](null-conditional-operators.md)</span></span>
- [<span data-ttu-id="81fc1-135">??運算子</span><span class="sxs-lookup"><span data-stu-id="81fc1-135">?? Operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="81fc1-136">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="81fc1-136">ref keyword</span></span>](../keywords/ref.md)
