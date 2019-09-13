---
title: ?? 還有？= 運算子- C#參考
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 1e94038a41a6a6cc19be6c67bff2891397793fb3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924686"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="46cf6-103">??</span><span class="sxs-lookup"><span data-stu-id="46cf6-103">??</span></span> <span data-ttu-id="46cf6-104">還有？= 運算子（C#參考）</span><span class="sxs-lookup"><span data-stu-id="46cf6-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="46cf6-105">如果 Null 聯合運算子 `??` 不是 `null`，會傳回其左方運算元的值；否則它會評估右方運算元，並傳回其結果。</span><span class="sxs-lookup"><span data-stu-id="46cf6-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="46cf6-106">如果左方運算元評估為非 Null，`??` 運算子不會評估其右方運算元。</span><span class="sxs-lookup"><span data-stu-id="46cf6-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="46cf6-107">在 8.0 C#和更新版本中，如果左運算元評估為`??=` `null`，則 null 聯合指派運算子只會將其右運算元的值指派給其左邊的運算元。</span><span class="sxs-lookup"><span data-stu-id="46cf6-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="46cf6-108">如果左方運算元評估為非 Null，`??=` 運算子不會評估其右方運算元。</span><span class="sxs-lookup"><span data-stu-id="46cf6-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="46cf6-109">`??=`運算子的左邊運算元必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../programming-guide/indexers/index.md)元素。</span><span class="sxs-lookup"><span data-stu-id="46cf6-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span> <span data-ttu-id="46cf6-110">如需有關 null 聯合指派的詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)。</span><span class="sxs-lookup"><span data-stu-id="46cf6-110">For more information about null-coalescing assignment, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

<span data-ttu-id="46cf6-111">在C# 7.3 和更早版本中， `??`運算子的左邊運算元類型必須是參考型別或[可為 null 的實數值型別](../../programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="46cf6-111">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a reference type or a [nullable value type](../../programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="46cf6-112">從C# 8.0 開始，會以下列內容取代該需求： `??`和`??=`運算子的左邊運算元類型不能是不可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="46cf6-112">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="46cf6-113">特別的是，您可以在8.0 和更新版本中C#使用 null 聯合運算子搭配不受限制的類型參數：</span><span class="sxs-lookup"><span data-stu-id="46cf6-113">In particular, you can use the null-coalescing operators with unconstrained type parameters in C# 8.0 and later:</span></span>

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="46cf6-114">Null 聯合運算子是右向關聯。</span><span class="sxs-lookup"><span data-stu-id="46cf6-114">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="46cf6-115">也就是表單的運算式</span><span class="sxs-lookup"><span data-stu-id="46cf6-115">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="46cf6-116">評估為</span><span class="sxs-lookup"><span data-stu-id="46cf6-116">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="46cf6-117">範例</span><span class="sxs-lookup"><span data-stu-id="46cf6-117">Examples</span></span>

<span data-ttu-id="46cf6-118">`??` 和`??=`運算子在下列案例中可能會很有用：</span><span class="sxs-lookup"><span data-stu-id="46cf6-118">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="46cf6-119">在使用 [Null 聯合運算子 ?. 和 ?[]](member-access-operators.md#null-conditional-operators--and-) 的運算式中，您可以使用 Null 聯合運算子在 Null 條件運算的結果為 `null` 的運算式中，提供用於評估的替代運算式：</span><span class="sxs-lookup"><span data-stu-id="46cf6-119">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="46cf6-120">當您使用[可為 Null 的實值型別](../../programming-guide/nullable-types/index.md)，而且需要提供基礎實值型別的值時，請使用 Null 聯合運算子，在可為 Null 的實值型別為 `null` 時，指定要提供的值：</span><span class="sxs-lookup"><span data-stu-id="46cf6-120">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the null-coalescing operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="46cf6-121">如果可為 Null 型別的值為 `null` 時要使用的值為基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="46cf6-121">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="46cf6-122">從 C# 7.0 開始，您可以使用 [`throw` 運算式](../keywords/throw.md#the-throw-expression)作為 Null 聯合運算子的右方運算元，讓引數檢查程式碼更簡潔：</span><span class="sxs-lookup"><span data-stu-id="46cf6-122">Starting with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the null-coalescing operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="46cf6-123">上述範例中也會示範如何使用[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)定義屬性。</span><span class="sxs-lookup"><span data-stu-id="46cf6-123">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="46cf6-124">從C# 8.0 開始，您可以使用`??=`運算子來取代表單的程式碼</span><span class="sxs-lookup"><span data-stu-id="46cf6-124">Starting with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="46cf6-125">使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="46cf6-125">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="46cf6-126">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="46cf6-126">Operator overloadability</span></span>

<span data-ttu-id="46cf6-127">運算子`??` 和`??=`無法多載。</span><span class="sxs-lookup"><span data-stu-id="46cf6-127">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="46cf6-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="46cf6-128">C# language specification</span></span>

<span data-ttu-id="46cf6-129">如需`??`運算子的詳細資訊，請參閱[ C#語言規格](~/_csharplang/spec/introduction.md)[的 null 聯合運算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="46cf6-129">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46cf6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46cf6-130">See also</span></span>

- [<span data-ttu-id="46cf6-131">C# 參考</span><span class="sxs-lookup"><span data-stu-id="46cf6-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="46cf6-132">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="46cf6-132">C# operators</span></span>](index.md)
- <span data-ttu-id="46cf6-133">[?. 和 ?[] 運算子](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="46cf6-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="46cf6-134">?: 運算子</span><span class="sxs-lookup"><span data-stu-id="46cf6-134">?: operator</span></span>](conditional-operator.md)
