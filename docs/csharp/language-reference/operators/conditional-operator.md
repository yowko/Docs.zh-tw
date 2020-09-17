---
description: '?: 運算子 - C# 參考'
title: '?: 運算子 - C# 參考'
ms.date: 09/17/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: b6add045983619169bed0cd9f32eb27dba0a0338
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738875"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="df11e-103">?: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="df11e-103">?: operator (C# reference)</span></span>

<span data-ttu-id="df11e-104">條件運算子 `?:` （也稱為三元條件運算子）會評估布林運算式，並根據布林運算式是否評估為或，傳回兩個運算式其中之一的結果 `true` `false` 。</span><span class="sxs-lookup"><span data-stu-id="df11e-104">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="df11e-105">條件運算子的語法如下：</span><span class="sxs-lookup"><span data-stu-id="df11e-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="df11e-106">`condition` 運算式必須評估為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="df11e-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="df11e-107">如果 `condition` 評估為 `true`，則會接著評估 `consequent` 運算式，且其結果會成為運算的結果。</span><span class="sxs-lookup"><span data-stu-id="df11e-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="df11e-108">如果 `condition` 評估為 `false`，則會接著評估 `alternative` 運算式，且其結果會成為運算的結果。</span><span class="sxs-lookup"><span data-stu-id="df11e-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="df11e-109">系統只會評估 `consequent` 或 `alternative`。</span><span class="sxs-lookup"><span data-stu-id="df11e-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="df11e-110">從 c # 9.0 開始，條件運算式是目標型別。</span><span class="sxs-lookup"><span data-stu-id="df11e-110">Beginning with C# 9.0, conditional expressions are target-typed.</span></span> <span data-ttu-id="df11e-111">也就是說，如果已知條件運算式的目標型別，則和的型別 `consequent` `alternative` 必須可以隱含轉換成目標型別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="df11e-111">That is, if a target type of a conditional expression is known, the types of `consequent` and `alternative` must be implicitly convertible to the target type, as the following example shows:</span></span>

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

<span data-ttu-id="df11e-112">如果條件運算式的目標型別是未知的 (例如，當您使用 [`var`](../keywords/var.md) 關鍵字) 或在 c # 8.0 及更早版本中，和的型別 `consequent` `alternative` 必須相同，或者必須從某種類型隱含轉換成另一個類型：</span><span class="sxs-lookup"><span data-stu-id="df11e-112">If a target type of a conditional expression is unknown (for example, when you use the [`var`](../keywords/var.md) keyword) or in C# 8.0 and earlier, the type of `consequent` and `alternative` must be the same or there must be an implicit conversion from one type to the other:</span></span>

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

<span data-ttu-id="df11e-113">條件運算子是右向關聯運算子，亦即，以下形式的運算式</span><span class="sxs-lookup"><span data-stu-id="df11e-113">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="df11e-114">會評估為</span><span class="sxs-lookup"><span data-stu-id="df11e-114">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="df11e-115">您可以使用下列助憶鍵裝置來記住條件運算子的評估方式：</span><span class="sxs-lookup"><span data-stu-id="df11e-115">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="df11e-116">下列範例示範條件運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="df11e-116">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="df11e-117">條件 ref 運算式</span><span class="sxs-lookup"><span data-stu-id="df11e-117">Conditional ref expression</span></span>

<span data-ttu-id="df11e-118">從 c # 7.2 開始， [ref 區域變數](../keywords/ref.md#ref-locals) 或 [ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals) 可以使用條件式 ref 運算式有條件地指派。</span><span class="sxs-lookup"><span data-stu-id="df11e-118">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with a conditional ref expression.</span></span> <span data-ttu-id="df11e-119">您也可以使用條件式 ref 運算式做為[參考傳回值](../keywords/ref.md#reference-return-values)或做為[ `ref` 方法引數](../keywords/ref.md#passing-an-argument-by-reference)。</span><span class="sxs-lookup"><span data-stu-id="df11e-119">You can also use a conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="df11e-120">條件式 ref 運算式的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="df11e-120">The syntax for a conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="df11e-121">如同原始的條件運算子，條件式 ref 運算式只會評估兩個運算式的其中一個： `consequent` 或 `alternative` 。</span><span class="sxs-lookup"><span data-stu-id="df11e-121">Like the original conditional operator, a conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="df11e-122">在條件式 ref 運算式的案例中，和的型 `consequent` 別 `alternative` 必須相同。</span><span class="sxs-lookup"><span data-stu-id="df11e-122">In the case of a conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span> <span data-ttu-id="df11e-123">條件式 ref 運算式並非目標型別。</span><span class="sxs-lookup"><span data-stu-id="df11e-123">Conditional ref expressions are not target-typed.</span></span>

<span data-ttu-id="df11e-124">下列範例示範條件式 ref 運算式的使用方式：</span><span class="sxs-lookup"><span data-stu-id="df11e-124">The following example demonstrates the usage of a conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="df11e-125">條件運算子和 `if..else` 陳述式</span><span class="sxs-lookup"><span data-stu-id="df11e-125">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="df11e-126">當您需要有條件地計算值時，使用條件運算子來取代 [if else](../keywords/if-else.md) 語句可能會導致更簡潔的程式碼。</span><span class="sxs-lookup"><span data-stu-id="df11e-126">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="df11e-127">下列範例示範兩種將整數分類為負值或非負值的方法：</span><span class="sxs-lookup"><span data-stu-id="df11e-127">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="df11e-128">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="df11e-128">Operator overloadability</span></span>

<span data-ttu-id="df11e-129">使用者定義型別無法多載條件運算子。</span><span class="sxs-lookup"><span data-stu-id="df11e-129">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="df11e-130">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="df11e-130">C# language specification</span></span>

<span data-ttu-id="df11e-131">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[條件運算子](~/_csharplang/spec/expressions.md#conditional-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="df11e-131">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="df11e-132">如需有關 c # 7.2 和更新版本中新增之功能的詳細資訊，請參閱下列功能提案附注：</span><span class="sxs-lookup"><span data-stu-id="df11e-132">For more information about features added in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="df11e-133">條件式 ref 運算式 (c # 7.2) </span><span class="sxs-lookup"><span data-stu-id="df11e-133">Conditional ref expressions (C# 7.2)</span></span>](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [<span data-ttu-id="df11e-134">目標型別條件運算式 (c # 9.0) </span><span class="sxs-lookup"><span data-stu-id="df11e-134">Target-typed conditional expression (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a><span data-ttu-id="df11e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df11e-135">See also</span></span>

- [<span data-ttu-id="df11e-136">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="df11e-136">C# reference</span></span>](../index.md)
- [<span data-ttu-id="df11e-137">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="df11e-137">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="df11e-138">if-else 陳述式</span><span class="sxs-lookup"><span data-stu-id="df11e-138">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="df11e-139">[?.和？[] 運算子](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="df11e-139">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="df11e-140">??和？？= 運算子</span><span class="sxs-lookup"><span data-stu-id="df11e-140">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="df11e-141">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="df11e-141">ref keyword</span></span>](../keywords/ref.md)
