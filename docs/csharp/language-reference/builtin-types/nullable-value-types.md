---
title: 空數值型別 - C# 引用
description: 瞭解 C# 可空數值型別以及如何使用它們
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: a84b3d60269491846b783e5046a84a1d14e258a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399585"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="e5c8c-103">空數值型別（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="e5c8c-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="e5c8c-104">*空數值型別*`T?`表示其基礎[數值型別](value-types.md)`T`的所有值和附加[空](../keywords/null.md)值。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="e5c8c-105">例如，您可以將以下三個值`bool?`中的任何一個分配給變數： `true`、`false`或`null`。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="e5c8c-106">基礎數值型別`T`不能為空數值型別本身。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c8c-107">C# 8.0 引入了可無可參考型別功能。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="e5c8c-108">有關詳細資訊，請參閱[空參考型別](../../nullable-references.md)。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-108">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="e5c8c-109">空數值型別從 C# 2 開始可用。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="e5c8c-110">任何空數值型別都是泛型<xref:System.Nullable%601?displayProperty=nameWithType>結構的實例。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="e5c8c-111">在以下任何可互換表單中，可以引用具有基礎類型的`T`空數值型別：`Nullable<T>`或`T?`。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="e5c8c-112">當您需要表示基礎數值型別的未定義值時，通常使用空數值型別。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="e5c8c-113">例如，布林或`bool`的 變數只能是 或`true``false`。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="e5c8c-114">但是，在某些應用程式中，變數值可能是未定義或缺少的。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="e5c8c-115">例如，資料庫欄位可能包含`true`或`false`，或者它可能不包含任何值，`NULL`即 。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="e5c8c-116">您可以在該方案中使用`bool?`類型。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="e5c8c-117">宣告與指派</span><span class="sxs-lookup"><span data-stu-id="e5c8c-117">Declaration and assignment</span></span>

<span data-ttu-id="e5c8c-118">由於數值型別是隱式轉換為相應的空數值型別，因此可以將值分配給可空數值型別的變數，就像對其基礎數值型別執行此操作一樣。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="e5c8c-119">您也可以指派 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-119">You also can assign the `null` value.</span></span> <span data-ttu-id="e5c8c-120">例如：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="e5c8c-121">null 數值型別的預設值表示`null`，即它是屬性<xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>返回`false`的實例。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="e5c8c-122">檢查空數值型別的實例</span><span class="sxs-lookup"><span data-stu-id="e5c8c-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="e5c8c-123">從 C# 7.0 開始，可以使用[`is`具有類型模式的運算子](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching)來檢查基礎類型的空數值型別的實例`null`並檢索基礎類型的值：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="e5c8c-124">始終可以使用以下唯讀屬性來檢查和獲取可 null 數值型別變數的值：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="e5c8c-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>指示空數值型別的實例是否具有其基礎類型的值。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="e5c8c-126">若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="e5c8c-127">若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="e5c8c-128">下面的示例使用 屬性`HasValue`在顯示變數之前測試變數是否包含值：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="e5c8c-129">您還可以將空數值型別的變數與`null`而不是使用`HasValue`屬性進行比較，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-129">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="e5c8c-130">從空數值型別轉換為基礎類型</span><span class="sxs-lookup"><span data-stu-id="e5c8c-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="e5c8c-131">如果要將空數值型別的值分配給非空數值型別變數，則可能需要指定要分配的值以代替`null`。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="e5c8c-132">使用[空聚運運算子`??`](../operators/null-coalescing-operator.md)執行此操作（您也可以將<xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType>方法用於相同的目的）：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="e5c8c-133">如果要使用 基礎數值型別的[預設值](default-values.md)代替`null`， 請使用<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="e5c8c-134">您還可以顯式將空數值型別轉換為非空類型，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-134">You also can explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

<span data-ttu-id="e5c8c-135">在運行時，如果空數值型別的值為`null`，則顯式強制轉換 。 <xref:System.InvalidOperationException></span><span class="sxs-lookup"><span data-stu-id="e5c8c-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="e5c8c-136">不可空數值型別`T`隱式轉換為相應的空數值型別。 `T?`</span><span class="sxs-lookup"><span data-stu-id="e5c8c-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="e5c8c-137">提升運算子</span><span class="sxs-lookup"><span data-stu-id="e5c8c-137">Lifted operators</span></span>

<span data-ttu-id="e5c8c-138">預定義的未元運算子和二進位[運算子](../operators/index.md)或數值型別`T`支援的任何重載運算子也受相應的空數值型別`T?`的支援。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="e5c8c-139">這些操作者，也稱為*提升運算子*，如果一`null`個或兩個運算元是;`null`如果一個或兩個運算元是，則生產。否則，運算子使用其運算元的包含值來計算結果。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="e5c8c-140">例如：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="e5c8c-141">對於`bool?`類型，預定義`&`運算子和`|`運算子不遵循本節中描述的規則：即使其中一個運算元為`null`，運算子評估的結果也可以為非 null。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="e5c8c-142">如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="e5c8c-143">對於[比較運算子](../operators/comparison-operators.md)`<` `>`、、`<=`和`>=`，如果一個或兩個運算元`null`是 ，則`false`結果是 ;否則，將比較運算元的包含值。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="e5c8c-144">請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="e5c8c-145">下列範例會顯示 10</span><span class="sxs-lookup"><span data-stu-id="e5c8c-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="e5c8c-146">既不大於也不等於`null`</span><span class="sxs-lookup"><span data-stu-id="e5c8c-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="e5c8c-147">也不小於`null`</span><span class="sxs-lookup"><span data-stu-id="e5c8c-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="e5c8c-148">對於[相等運算子](../operators/equality-operators.md#equality-operator-)`==`，`null`如果兩個運算元均為 ，則結果是`true`，如果只有一個運算元是`null`，則結果是; `false`否則，將比較運算元的包含值。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="e5c8c-149">對於[不等式運算子](../operators/equality-operators.md#inequality-operator-)`!=`，如果兩個運算元均為`null`，則結果是`false`，如果只有一個運算元是`null`，則結果是; `true`否則，將比較運算元的包含值。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="e5c8c-150">如果兩種數值型別之間存在[使用者定義的轉換](../operators/user-defined-conversion-operators.md)，則在相應的空數值型別之間也可以使用相同的轉換。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="e5c8c-151">Boxing 和 Unboxing</span><span class="sxs-lookup"><span data-stu-id="e5c8c-151">Boxing and unboxing</span></span>

<span data-ttu-id="e5c8c-152">空數值型別的`T?`實例[按如下方式裝箱](../../programming-guide/types/boxing-and-unboxing.md)：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="e5c8c-153">若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="e5c8c-154">如果<xref:System.Nullable%601.HasValue%2A>返回`true`，則基礎數值型別的`T`相應值將裝箱，而不是<xref:System.Nullable%601>實例。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="e5c8c-155">您可以將數值型別的`T`裝箱值解箱到相應的空數值型別`T?`，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="e5c8c-156">如何識別可無效數值型別</span><span class="sxs-lookup"><span data-stu-id="e5c8c-156">How to identify a nullable value type</span></span>

<span data-ttu-id="e5c8c-157">下面的示例演示如何確定<xref:System.Type?displayProperty=nameWithType>實例是否表示構造的 null 數值型別，即具有指定類型參數<xref:System.Nullable%601?displayProperty=nameWithType>`T`的類型 ：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="e5c8c-158">如示例所示，您可以使用[類型的](../operators/type-testing-and-cast.md#typeof-operator)運算子創建<xref:System.Type?displayProperty=nameWithType>實例。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="e5c8c-159">如果要確定實例是否為空數值型別，請不要使用 方法<xref:System.Object.GetType%2A?displayProperty=nameWithType>獲取使用上述代碼測試<xref:System.Type>實例。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="e5c8c-160">當您在<xref:System.Object.GetType%2A?displayProperty=nameWithType>null 數值型別的實例上調用 方法時，實例將[裝箱](#boxing-and-unboxing)到<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="e5c8c-161">由於空數值型別的非空實例的裝箱等效于基礎類型的值裝箱，因此<xref:System.Object.GetType%2A>返回表示空數值型別的基礎類型的<xref:System.Type>實例：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

<span data-ttu-id="e5c8c-162">此外，不要使用[is](../operators/type-testing-and-cast.md#is-operator)運算子來確定實例是否具有空數值型別。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="e5c8c-163">如以下示例所示，您無法與`is`運算子區分空數值型別實例的類型及其基礎類型實例：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="e5c8c-164">可以使用以下示例中提供的代碼來確定實例是否具有空數值型別：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="e5c8c-165">本節中描述的方法不適用於[空參考型別](../../nullable-references.md)。</span><span class="sxs-lookup"><span data-stu-id="e5c8c-165">The methods described in this section are not applicable in the case of [nullable reference types](../../nullable-references.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e5c8c-166">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e5c8c-166">C# language specification</span></span>

<span data-ttu-id="e5c8c-167">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="e5c8c-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="e5c8c-168">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="e5c8c-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="e5c8c-169">提升運算子</span><span class="sxs-lookup"><span data-stu-id="e5c8c-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="e5c8c-170">隱式空轉換</span><span class="sxs-lookup"><span data-stu-id="e5c8c-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="e5c8c-171">顯式可無效轉換</span><span class="sxs-lookup"><span data-stu-id="e5c8c-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="e5c8c-172">提升轉換運算子</span><span class="sxs-lookup"><span data-stu-id="e5c8c-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="e5c8c-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5c8c-173">See also</span></span>

- [<span data-ttu-id="e5c8c-174">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e5c8c-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e5c8c-175">"提升"究竟是什麼意思？</span><span class="sxs-lookup"><span data-stu-id="e5c8c-175">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e5c8c-176">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="e5c8c-176">Nullable reference types</span></span>](../../nullable-references.md)
