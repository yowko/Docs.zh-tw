---
title: ?? 和？？• 運算子 - C# 參考
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
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847309"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="b1e8e-103">??</span><span class="sxs-lookup"><span data-stu-id="b1e8e-103">??</span></span> <span data-ttu-id="b1e8e-104">和？？• 運算子（C# 參考）</span><span class="sxs-lookup"><span data-stu-id="b1e8e-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="b1e8e-105">如果 Null 聯合運算子 `??` 不是 `null`，會傳回其左方運算元的值；否則它會評估右方運算元，並傳回其結果。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="b1e8e-106">如果左方運算元評估為非 Null，`??` 運算子不會評估其右方運算元。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="b1e8e-107">在 C# 8.0 及更高版本中可用，空合併賦值`??=`運算子僅在左側運算元計算為`null`時，才會將其右側運算元的值分配給其左側運算元。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="b1e8e-108">如果左方運算元評估為非 Null，`??=` 運算子不會評估其右方運算元。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="b1e8e-109">運算子的`??=`左側操作符必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../programming-guide/indexers/index.md)元素。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="b1e8e-110">在 C# 7.3 和更早版本中，`??`運算子的左側運算元的類型必須是[參考型別](../keywords/reference-types.md)或[空數值型別](../builtin-types/nullable-value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="b1e8e-111">從 C# 8.0 開始，該要求替換為以下內容：`??`和`??=`運算子的左側運算元的類型不能為非空數值型別。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="b1e8e-112">特別是，從 C# 8.0 開始，可以使用具有無約束類型參數的空合併運算子：</span><span class="sxs-lookup"><span data-stu-id="b1e8e-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="b1e8e-113">空合併運算子是右關聯的。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="b1e8e-114">也就是說，表單的運算式</span><span class="sxs-lookup"><span data-stu-id="b1e8e-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="b1e8e-115">評估為</span><span class="sxs-lookup"><span data-stu-id="b1e8e-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="b1e8e-116">範例</span><span class="sxs-lookup"><span data-stu-id="b1e8e-116">Examples</span></span>

<span data-ttu-id="b1e8e-117">和`??``??=`運算子在以下方案中非常有用：</span><span class="sxs-lookup"><span data-stu-id="b1e8e-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="b1e8e-118">在具有 null[條件運算子的運算式中 ，](member-access-operators.md#null-conditional-operators--and-)可以使用`??`運算子提供替代運算式來計算，以防具有 null 條件操作的運算式的結果為`null`：</span><span class="sxs-lookup"><span data-stu-id="b1e8e-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="b1e8e-119">當您使用[空數值型別](../builtin-types/nullable-value-types.md)並且需要提供基礎數值型別的值時，使用`??`運算子指定要提供的值，以防空類型值為`null`：</span><span class="sxs-lookup"><span data-stu-id="b1e8e-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="b1e8e-120">如果可為 Null 型別的值為 `null` 時要使用的值為基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="b1e8e-121">從 C# 7.0 開始，可以使用[`throw`運算式](../keywords/throw.md#the-throw-expression)作為`??`運算子的右側運算元，以使參數檢查代碼更加簡潔：</span><span class="sxs-lookup"><span data-stu-id="b1e8e-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="b1e8e-122">上述範例中也會示範如何使用[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)定義屬性。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="b1e8e-123">從 C# 8.0 開始，`??=`可以使用運算子替換表單的代碼</span><span class="sxs-lookup"><span data-stu-id="b1e8e-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="b1e8e-124">取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b1e8e-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="b1e8e-125">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="b1e8e-125">Operator overloadability</span></span>

<span data-ttu-id="b1e8e-126">運算子`??`不能`??=`重載。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b1e8e-127">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b1e8e-127">C# language specification</span></span>

<span data-ttu-id="b1e8e-128">有關運算子的詳細資訊，`??`請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[空合併運算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)部分。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="b1e8e-129">有關運算子的詳細資訊，`??=`請參閱[功能建議注釋](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)。</span><span class="sxs-lookup"><span data-stu-id="b1e8e-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1e8e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1e8e-130">See also</span></span>

- [<span data-ttu-id="b1e8e-131">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b1e8e-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b1e8e-132">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="b1e8e-132">C# operators</span></span>](index.md)
- <span data-ttu-id="b1e8e-133">[?.和？[ 運算子] 運算子](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="b1e8e-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="b1e8e-134">？： 運算子</span><span class="sxs-lookup"><span data-stu-id="b1e8e-134">?: operator</span></span>](conditional-operator.md)
