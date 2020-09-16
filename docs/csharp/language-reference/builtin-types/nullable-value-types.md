---
title: '可為 null 的實值型別-c # 參考'
description: '深入瞭解 c # 可為 null 的實值型別，以及如何使用它們'
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 8c3a8b997fbb8154f79dff04018cf3ea76f85d7a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537349"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="ca495-103">可為 null 的實數值型別 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="ca495-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="ca495-104">*可為 null*的實值型別 `T?` 代表其基礎實[值型](value-types.md)別的所有值 `T` ，以及一個額外的[null](../keywords/null.md)值。</span><span class="sxs-lookup"><span data-stu-id="ca495-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="ca495-105">例如，您可以將下列三個值的任何一個指派給 `bool?` 變數： `true` 、 `false` 或 `null` 。</span><span class="sxs-lookup"><span data-stu-id="ca495-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="ca495-106">基礎實值型別 `T` 不能是可為 null 的實值型別本身。</span><span class="sxs-lookup"><span data-stu-id="ca495-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="ca495-107">C # 8.0 引進可為 null 的參考型別功能。</span><span class="sxs-lookup"><span data-stu-id="ca495-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="ca495-108">如需詳細資訊，請參閱 [可為 null 的參考型別](nullable-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ca495-108">For more information, see [Nullable reference types](nullable-reference-types.md).</span></span> <span data-ttu-id="ca495-109">從 c # 2 開始可以使用可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="ca495-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="ca495-110">任何可為 null 的實值型別都是泛型結構的實例 <xref:System.Nullable%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ca495-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="ca495-111">您可以使用下列任何可交換形式的基礎類型來參考可為 null 的實數值型別 `T` ： `Nullable<T>` 或 `T?` 。</span><span class="sxs-lookup"><span data-stu-id="ca495-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="ca495-112">當您需要代表基礎實值型別的未定義值時，通常會使用可為 null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="ca495-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="ca495-113">例如，布林值或 `bool` 變數只能是 `true` 或 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ca495-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="ca495-114">不過，在某些應用程式中，變數值不能定義或遺失。</span><span class="sxs-lookup"><span data-stu-id="ca495-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="ca495-115">例如，資料庫欄位可能包含 `true` 或 `false` ，或可能完全不包含任何值，也就是 `NULL` 。</span><span class="sxs-lookup"><span data-stu-id="ca495-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="ca495-116">`bool?`在該案例中，您可以使用類型。</span><span class="sxs-lookup"><span data-stu-id="ca495-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="ca495-117">宣告與指派</span><span class="sxs-lookup"><span data-stu-id="ca495-117">Declaration and assignment</span></span>

<span data-ttu-id="ca495-118">因為實值型別可隱含轉換成對應的可為 null 實值型別，所以您可以將值指派給可為 null 實值型別的變數，就像您針對其基礎實值型別所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="ca495-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="ca495-119">您也可以指派 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="ca495-119">You can also assign the `null` value.</span></span> <span data-ttu-id="ca495-120">例如：</span><span class="sxs-lookup"><span data-stu-id="ca495-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="ca495-121">可為 null 之實值型別的預設值代表 `null` ，也就是其屬性會傳回的實例 <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> `false` 。</span><span class="sxs-lookup"><span data-stu-id="ca495-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="ca495-122">檢查可為 null 實值型別的實例</span><span class="sxs-lookup"><span data-stu-id="ca495-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="ca495-123">從 c # 7.0 開始，您可以使用[ `is` 運算子搭配型別模式](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching)來檢查可為 null 實值型別的實例 `null` ，並取出基礎型別的值：</span><span class="sxs-lookup"><span data-stu-id="ca495-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="ca495-124">您一律可以使用下列唯讀屬性來檢查並取得可為 null 實值型別變數的值：</span><span class="sxs-lookup"><span data-stu-id="ca495-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="ca495-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 指出可為 null 實值型別的實例是否具有其基礎類型的值。</span><span class="sxs-lookup"><span data-stu-id="ca495-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="ca495-126">若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。</span><span class="sxs-lookup"><span data-stu-id="ca495-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="ca495-127">若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="ca495-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="ca495-128">下列範例 `HasValue` 會使用屬性來測試變數是否包含值，然後才顯示它：</span><span class="sxs-lookup"><span data-stu-id="ca495-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="ca495-129">您也可以比較可為 null 實值型別的變數 `null` ，而不使用 `HasValue` 屬性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ca495-129">You can also compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="ca495-130">從可為 null 的實值型別轉換為基礎類型</span><span class="sxs-lookup"><span data-stu-id="ca495-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="ca495-131">如果您想要將可為 null 實值型別的值指派給不可為 null 的實值型別變數，您可能需要指定要指派的值來取代 `null` 。</span><span class="sxs-lookup"><span data-stu-id="ca495-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="ca495-132">使用[null 聯合運算子 `??` ](../operators/null-coalescing-operator.md)來執行該作業 (您也可以 <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> 針對相同的目的) 使用方法：</span><span class="sxs-lookup"><span data-stu-id="ca495-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you can also use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="ca495-133">如果您想要使用基礎數值型別的 [預設](default-values.md) 值來取代 `null` ，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ca495-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ca495-134">您也可以明確地將可為 null 的實值型別轉換為不可為 null 的型別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ca495-134">You can also explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

<span data-ttu-id="ca495-135">在執行時間，如果可為 null 的實值型別值為 `null` ，明確的轉換會擲回 <xref:System.InvalidOperationException> 。</span><span class="sxs-lookup"><span data-stu-id="ca495-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="ca495-136">不可為 null 的實值型別 `T` 可隱含轉換成對應的可為 null 實值型別 `T?` 。</span><span class="sxs-lookup"><span data-stu-id="ca495-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="ca495-137">提起運算子</span><span class="sxs-lookup"><span data-stu-id="ca495-137">Lifted operators</span></span>

<span data-ttu-id="ca495-138">對應的可為 null 實值型別也支援預先定義的一元和二元 [運算子](../operators/index.md) 或實數值型別所支援的任何多載運算子 `T` `T?` 。</span><span class="sxs-lookup"><span data-stu-id="ca495-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="ca495-139">如果一或兩個運算元都是，則這些運算子（也稱為 *提升運算子*） `null` 會產生 `null` ; 否則，運算子會使用其運算元的包含值來計算結果。</span><span class="sxs-lookup"><span data-stu-id="ca495-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="ca495-140">例如：</span><span class="sxs-lookup"><span data-stu-id="ca495-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="ca495-141">針對 `bool?` 類型，預先定義的 `&` 和 `|` 運算子不會遵循本節所述的規則：即使其中一個運算元為，運算子評估的結果也可以是非 null `null` 。</span><span class="sxs-lookup"><span data-stu-id="ca495-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="ca495-142">如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="ca495-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="ca495-143">針對 [比較運算子](../operators/comparison-operators.md) `<` 、、 `>` `<=` 和 `>=` ，如果其中一個或兩個運算元都是 `null` ，則結果為 `false` ; 否則會比較運算元的包含值。</span><span class="sxs-lookup"><span data-stu-id="ca495-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="ca495-144">請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="ca495-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="ca495-145">下列範例會顯示 10</span><span class="sxs-lookup"><span data-stu-id="ca495-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="ca495-146">不大於或等於 `null`</span><span class="sxs-lookup"><span data-stu-id="ca495-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="ca495-147">或小於 `null`</span><span class="sxs-lookup"><span data-stu-id="ca495-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="ca495-148">針對 [相等運算子](../operators/equality-operators.md#equality-operator-) `==` ，如果兩個運算元都是， `null` 結果就是 `true` ，如果只有一個運算元是，則結果為， `null` 否則會 `false` 比較運算元的包含值。</span><span class="sxs-lookup"><span data-stu-id="ca495-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="ca495-149">針對不 [等比較運算子](../operators/equality-operators.md#inequality-operator-) `!=` ，如果兩個運算元都是， `null` 結果就是 `false` ，如果只有一個運算元是，則結果為， `null` 否則會 `true` 比較運算元的包含值。</span><span class="sxs-lookup"><span data-stu-id="ca495-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="ca495-150">如果兩個實值型別之間有 [使用者定義的轉換](../operators/user-defined-conversion-operators.md) ，也可以在對應的可為 null 實值型別之間使用相同的轉換。</span><span class="sxs-lookup"><span data-stu-id="ca495-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="ca495-151">Box 處理和 Unbox 處理</span><span class="sxs-lookup"><span data-stu-id="ca495-151">Boxing and unboxing</span></span>

<span data-ttu-id="ca495-152">可為 null 的實值型別的實例 `T?` 會以下列方式 [裝箱](../../programming-guide/types/boxing-and-unboxing.md) ：</span><span class="sxs-lookup"><span data-stu-id="ca495-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="ca495-153">若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。</span><span class="sxs-lookup"><span data-stu-id="ca495-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="ca495-154">如果 <xref:System.Nullable%601.HasValue%2A> 傳回 `true` ，則會將基礎實值型別的對應值 `T` 裝箱，而不是的實例 <xref:System.Nullable%601> 。</span><span class="sxs-lookup"><span data-stu-id="ca495-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="ca495-155">您可以將實數值型別的已裝箱值取消封裝 `T` 為對應的可為 null 實值型別 `T?` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ca495-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="ca495-156">如何識別可為 null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="ca495-156">How to identify a nullable value type</span></span>

<span data-ttu-id="ca495-157">下列範例示範如何判斷 <xref:System.Type?displayProperty=nameWithType> 實例是否代表一個可為 null 的實值型別，也就是 <xref:System.Nullable%601?displayProperty=nameWithType> 具有指定型別參數的型別 `T` ：</span><span class="sxs-lookup"><span data-stu-id="ca495-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="ca495-158">如範例所示，您可以使用 [typeof](../operators/type-testing-and-cast.md#typeof-operator) 運算子來建立 <xref:System.Type?displayProperty=nameWithType> 實例。</span><span class="sxs-lookup"><span data-stu-id="ca495-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="ca495-159">如果您想要判斷某個實例是否屬於可為 null 的實值型別，請不要使用 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法來取得 <xref:System.Type> 要使用上述程式碼測試的實例。</span><span class="sxs-lookup"><span data-stu-id="ca495-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="ca495-160">當您 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 在可為 null 的實值型別實例上呼叫方法時，實例就會被 [封裝](#boxing-and-unboxing) 成 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="ca495-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="ca495-161">當可為 null 實值型別的非 null 實例的裝箱相當於基礎類型值的裝箱時，會傳回 <xref:System.Object.GetType%2A> <xref:System.Type> 表示可為 null 實值型別之基礎型別的實例：</span><span class="sxs-lookup"><span data-stu-id="ca495-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

<span data-ttu-id="ca495-162">此外，請勿使用「 [是](../operators/type-testing-and-cast.md#is-operator) 」運算子來判斷實例是否為可為 null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="ca495-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="ca495-163">如下列範例所示，您無法使用運算子來區別可為 null 的實值型別實例及其基礎型別實例的類型 `is` ：</span><span class="sxs-lookup"><span data-stu-id="ca495-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="ca495-164">您可以使用下列範例中所示的程式碼，判斷實例是否為可為 null 的實值型別：</span><span class="sxs-lookup"><span data-stu-id="ca495-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="ca495-165">在 [可為 null 的參考型別](nullable-reference-types.md)案例中，本節所述的方法不適用。</span><span class="sxs-lookup"><span data-stu-id="ca495-165">The methods described in this section are not applicable in the case of [nullable reference types](nullable-reference-types.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ca495-166">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ca495-166">C# language specification</span></span>

<span data-ttu-id="ca495-167">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="ca495-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="ca495-168">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="ca495-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="ca495-169">提起運算子</span><span class="sxs-lookup"><span data-stu-id="ca495-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="ca495-170">隱含可為 null 的轉換</span><span class="sxs-lookup"><span data-stu-id="ca495-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="ca495-171">明確可為 null 的轉換</span><span class="sxs-lookup"><span data-stu-id="ca495-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="ca495-172">提升的轉換運算子</span><span class="sxs-lookup"><span data-stu-id="ca495-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="ca495-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca495-173">See also</span></span>

- [<span data-ttu-id="ca495-174">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="ca495-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ca495-175">「提升」是什麼意思？</span><span class="sxs-lookup"><span data-stu-id="ca495-175">What exactly does 'lifted' mean?</span></span>](/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ca495-176">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="ca495-176">Nullable reference types</span></span>](nullable-reference-types.md)
