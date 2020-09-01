---
description: '?: 運算子 - C# 參考'
title: '?: 運算子 - C# 參考'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 0efa6de2b537fd3af76807938ac2b50a2716561f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122351"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a61fc-103">?: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a61fc-103">?: operator (C# reference)</span></span>

<span data-ttu-id="a61fc-104">條件運算子 `?:` （也稱為三元條件運算子）會評估布林運算式，並根據布林運算式是否評估為或，傳回兩個運算式其中之一的結果 `true` `false` 。</span><span class="sxs-lookup"><span data-stu-id="a61fc-104">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="a61fc-105">條件運算子的語法如下：</span><span class="sxs-lookup"><span data-stu-id="a61fc-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="a61fc-106">`condition` 運算式必須評估為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="a61fc-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="a61fc-107">如果 `condition` 評估為 `true`，則會接著評估 `consequent` 運算式，且其結果會成為運算的結果。</span><span class="sxs-lookup"><span data-stu-id="a61fc-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="a61fc-108">如果 `condition` 評估為 `false`，則會接著評估 `alternative` 運算式，且其結果會成為運算的結果。</span><span class="sxs-lookup"><span data-stu-id="a61fc-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="a61fc-109">系統只會評估 `consequent` 或 `alternative`。</span><span class="sxs-lookup"><span data-stu-id="a61fc-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="a61fc-110">`consequent` 和 `alternative` 的型別必須相同，或是必須有從一個型別轉換成另一型別的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="a61fc-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="a61fc-111">條件運算子是右向關聯運算子，亦即，以下形式的運算式</span><span class="sxs-lookup"><span data-stu-id="a61fc-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="a61fc-112">會評估為</span><span class="sxs-lookup"><span data-stu-id="a61fc-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="a61fc-113">您可以使用下列助憶鍵裝置來記住條件運算子的評估方式：</span><span class="sxs-lookup"><span data-stu-id="a61fc-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="a61fc-114">下列範例示範條件運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="a61fc-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="a61fc-115">條件 ref 運算式</span><span class="sxs-lookup"><span data-stu-id="a61fc-115">Conditional ref expression</span></span>

<span data-ttu-id="a61fc-116">從 c # 7.2 開始， [ref 區域變數](../keywords/ref.md#ref-locals) 或 [ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals) 可以使用條件式 ref 運算式有條件地指派。</span><span class="sxs-lookup"><span data-stu-id="a61fc-116">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="a61fc-117">您也可以使用條件式 ref 運算式做為[參考傳回值](../keywords/ref.md#reference-return-values)或做為[ `ref` 方法引數](../keywords/ref.md#passing-an-argument-by-reference)。</span><span class="sxs-lookup"><span data-stu-id="a61fc-117">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="a61fc-118">條件 ref 運算式的語法如下：</span><span class="sxs-lookup"><span data-stu-id="a61fc-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="a61fc-119">與原始條件運算子相同，條件 ref 運算式只會評估兩個運算式其中之一：`consequent` 或 `alternative`。</span><span class="sxs-lookup"><span data-stu-id="a61fc-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="a61fc-120">就條件 ref 運算式而言，`consequent` 與 `alternative` 的型別必須相同。</span><span class="sxs-lookup"><span data-stu-id="a61fc-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="a61fc-121">下列範例示範條件 ref 運算式的用法：</span><span class="sxs-lookup"><span data-stu-id="a61fc-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="a61fc-122">條件運算子和 `if..else` 陳述式</span><span class="sxs-lookup"><span data-stu-id="a61fc-122">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="a61fc-123">當您需要有條件地計算值時，使用條件運算子來取代 [if else](../keywords/if-else.md) 語句可能會導致更簡潔的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a61fc-123">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="a61fc-124">下列範例示範兩種將整數分類為負值或非負值的方法：</span><span class="sxs-lookup"><span data-stu-id="a61fc-124">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="a61fc-125">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="a61fc-125">Operator overloadability</span></span>

<span data-ttu-id="a61fc-126">使用者定義型別無法多載條件運算子。</span><span class="sxs-lookup"><span data-stu-id="a61fc-126">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a61fc-127">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a61fc-127">C# language specification</span></span>

<span data-ttu-id="a61fc-128">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[條件運算子](~/_csharplang/spec/expressions.md#conditional-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="a61fc-128">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="a61fc-129">如需條件式 ref 運算式的詳細資訊，請參閱 [功能提案注意事項](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)。</span><span class="sxs-lookup"><span data-stu-id="a61fc-129">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a61fc-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a61fc-130">See also</span></span>

- [<span data-ttu-id="a61fc-131">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="a61fc-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a61fc-132">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="a61fc-132">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="a61fc-133">if-else 陳述式</span><span class="sxs-lookup"><span data-stu-id="a61fc-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="a61fc-134">[?.和？[] 運算子](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="a61fc-134">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="a61fc-135">??和？？= 運算子</span><span class="sxs-lookup"><span data-stu-id="a61fc-135">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="a61fc-136">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="a61fc-136">ref keyword</span></span>](../keywords/ref.md)
