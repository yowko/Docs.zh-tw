---
title: 使用可為 null 的C#實數值型別-程式設計指南
ms.custom: seodec18
description: 瞭解如何使用可為C# null 的實數值型別
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396170"
---
# <a name="using-nullable-value-types-c-programming-guide"></a><span data-ttu-id="6af08-103">使用可為 null 的C#實數值型別（程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="6af08-103">Using nullable value types (C# Programming Guide)</span></span>

<span data-ttu-id="6af08-104">可為 null 的實數值型別是類型，代表基礎數值型別的所有值 `T`，以及額外的[null](../../language-reference/keywords/null.md)值。</span><span class="sxs-lookup"><span data-stu-id="6af08-104">Nullable value types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="6af08-105">如需詳細資訊，請參閱[可為 null 的實數值型別](index.md)主題。</span><span class="sxs-lookup"><span data-stu-id="6af08-105">For more information, see the [Nullable value types](index.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="6af08-106">C#8.0 引進了可為 null 的參考型別功能。</span><span class="sxs-lookup"><span data-stu-id="6af08-106">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="6af08-107">如需詳細資訊，請參閱[可為 null 的參考型別](../../nullable-references.md)。</span><span class="sxs-lookup"><span data-stu-id="6af08-107">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="6af08-108">從C# 2 開始可以使用可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="6af08-108">The nullable value types are available starting with C# 2.</span></span>

<span data-ttu-id="6af08-109">您可以使用下列任何可交換的形式來參考可為 null 的實數值型別： `Nullable<T>` 或 `T?`。</span><span class="sxs-lookup"><span data-stu-id="6af08-109">You can refer to a nullable value type in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="6af08-110">`T` 必須是實值型別。</span><span class="sxs-lookup"><span data-stu-id="6af08-110">`T` must be a value type.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="6af08-111">宣告與指派</span><span class="sxs-lookup"><span data-stu-id="6af08-111">Declaration and assignment</span></span>

<span data-ttu-id="6af08-112">當實值型別可以隱含地轉換成對應的可為 null 實值型別時，您可以將值指派給可為 null 的型別，就像它的基礎實值型別一樣。</span><span class="sxs-lookup"><span data-stu-id="6af08-112">As a value type can be implicitly converted to the corresponding nullable value type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="6af08-113">您也可以指派 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="6af08-113">You also can assign the `null` value.</span></span> <span data-ttu-id="6af08-114">例如:</span><span class="sxs-lookup"><span data-stu-id="6af08-114">For example:</span></span>

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="6af08-115">檢查可為 Null 型別的值</span><span class="sxs-lookup"><span data-stu-id="6af08-115">Examination of a nullable type value</span></span>

<span data-ttu-id="6af08-116">使用下列 readonly 屬性來檢查 null 實數值型別的實例是否為 null，並取出基礎類型的值：</span><span class="sxs-lookup"><span data-stu-id="6af08-116">Use the following readonly properties to examine an instance of a nullable value type for null and retrieve a value of an underlying type:</span></span>

- <span data-ttu-id="6af08-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 指出可為 Null 型別的執行個體是否有其基礎型別的值。</span><span class="sxs-lookup"><span data-stu-id="6af08-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>

- <span data-ttu-id="6af08-118">若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。</span><span class="sxs-lookup"><span data-stu-id="6af08-118"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="6af08-119">若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="6af08-119">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="6af08-120">下列範例中的程式碼會使用 `HasValue` 屬性，在顯示之前測試變數是否包含值：</span><span class="sxs-lookup"><span data-stu-id="6af08-120">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

<span data-ttu-id="6af08-121">您也可以比較可為 null 的實值型別與 `null` 的變數，而不是使用 `HasValue` 屬性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6af08-121">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="6af08-122">從C# 7.0 開始，您可以使用[模式](../../pattern-matching.md)比對來檢查並取得可為 null 的實數值型別的值：</span><span class="sxs-lookup"><span data-stu-id="6af08-122">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable value type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="6af08-123">從可為 null 的實數值型別轉換成基礎類型</span><span class="sxs-lookup"><span data-stu-id="6af08-123">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="6af08-124">如果您需要將可為 null 的實值型別值指派給不可為 null 的型別，請使用[null 聯合運算子 `??`](../../language-reference/operators/null-coalescing-operator.md)來指定如果可為 null 的實值型別值為 null 時要指派的值（您也可以使用 <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> 方法來這麼做）:</span><span class="sxs-lookup"><span data-stu-id="6af08-124">If you need to assign a value of a nullable value type to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a value of a nullable value type is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="6af08-125">如果可為 null 的實值型別的值為時要使用的值為 `null` 應該是基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="6af08-125">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a value of a nullable value type is `null` should be the default value of the underlying value type.</span></span>

<span data-ttu-id="6af08-126">您可以將可為 null 的實值型別明確轉換成不可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="6af08-126">You can explicitly cast a nullable value type to a non-nullable type.</span></span> <span data-ttu-id="6af08-127">例如:</span><span class="sxs-lookup"><span data-stu-id="6af08-127">For example:</span></span>

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="6af08-128">在執行時間，如果可為 null 的實值型別值為 `null`，則明確的轉換會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="6af08-128">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="6af08-129">不可為 Null 的實值型別會隱含轉換成對應的可為 Null 型別。</span><span class="sxs-lookup"><span data-stu-id="6af08-129">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>

## <a name="operators"></a><span data-ttu-id="6af08-130">運算子</span><span class="sxs-lookup"><span data-stu-id="6af08-130">Operators</span></span>

<span data-ttu-id="6af08-131">預先定義的一元和二元運算子，以及任何存在於實數值型別的使用者定義運算子，也可能會由對應的可為 null 類型使用。</span><span class="sxs-lookup"><span data-stu-id="6af08-131">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by corresponding nullable types.</span></span> <span data-ttu-id="6af08-132">如果一個或兩個運算元 `null`，這些運算子會產生 `null`;否則，運算子會使用包含的值來計算結果。</span><span class="sxs-lookup"><span data-stu-id="6af08-132">These operators produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="6af08-133">例如:</span><span class="sxs-lookup"><span data-stu-id="6af08-133">For example:</span></span>

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="6af08-134">若為 `bool?` 類型，預先定義的 `&` 和 @no__t 2 運算子不會遵循本節所述的規則：即使其中一個運算元是 `null`，運算子評估的結果也可以是非 null。</span><span class="sxs-lookup"><span data-stu-id="6af08-134">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="6af08-135">如需詳細資訊，請參閱[布林值邏輯運算子](../../language-reference/operators/boolean-logical-operators.md)一文的[可為 Null 的布林值邏輯運算子](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="6af08-135">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="6af08-136">對於關係運算子（`<`，`>`，`<=`，`>=`），如果其中一個或兩個運算元都是 `null`，則結果會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="6af08-136">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are `null`, the result is `false`.</span></span> <span data-ttu-id="6af08-137">請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="6af08-137">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="6af08-138">下列範例會顯示 10</span><span class="sxs-lookup"><span data-stu-id="6af08-138">The following example shows that 10 is</span></span>

- <span data-ttu-id="6af08-139">不能大於或等於 `null`，</span><span class="sxs-lookup"><span data-stu-id="6af08-139">neither greater than or equal to `null`,</span></span>
- <span data-ttu-id="6af08-140">或小於 `null`。</span><span class="sxs-lookup"><span data-stu-id="6af08-140">nor less than `null`.</span></span>

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

<span data-ttu-id="6af08-141">上述範例也顯示兩個 null 實值型別的相等比較會評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6af08-141">The above example also shows that an equality comparison of two nullable value types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="6af08-142">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[增益運算子](~/_csharplang/spec/expressions.md#lifted-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="6af08-142">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="6af08-143">Boxing 和 Unboxing</span><span class="sxs-lookup"><span data-stu-id="6af08-143">Boxing and unboxing</span></span>

<span data-ttu-id="6af08-144">根據下列規則，可為 Null 的實值型別將為 [boxed](../types/boxing-and-unboxing.md)：</span><span class="sxs-lookup"><span data-stu-id="6af08-144">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="6af08-145">若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。</span><span class="sxs-lookup"><span data-stu-id="6af08-145">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="6af08-146">若 <xref:System.Nullable%601.HasValue%2A> 傳回 `true`，則基礎實值型別 `T` 的值為 boxed，而非 <xref:System.Nullable%601> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6af08-146">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="6af08-147">您可以將已為 boxed 的實值型別 unbox 為對應的可為 Null 型別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="6af08-147">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="6af08-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6af08-148">See also</span></span>

- [<span data-ttu-id="6af08-149">可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="6af08-149">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="6af08-150">「增益」(Lift) 的真正意義是什麼？(英文)</span><span class="sxs-lookup"><span data-stu-id="6af08-150">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
