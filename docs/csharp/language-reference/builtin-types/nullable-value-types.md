---
title: 空白值型態 - C# 參考
description: 瞭解 C# 可空數型態與如何使用它們
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: c13ef6a091ec6aebd4608c5ed8d2c03b067c7312
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888068"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="689dd-103">空白值型態(C# 引用)</span><span class="sxs-lookup"><span data-stu-id="689dd-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="689dd-104">*空值類型*`T?`表示其基礎[值類型](value-types.md)`T`的所有值和附加[空](../keywords/null.md)值。</span><span class="sxs-lookup"><span data-stu-id="689dd-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="689dd-105">例如,您可以將以下三個值`bool?`中的任何一個分配給變數: `true``false`、`null`或 。</span><span class="sxs-lookup"><span data-stu-id="689dd-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="689dd-106">基礎值類型`T`不能為空值類型本身。</span><span class="sxs-lookup"><span data-stu-id="689dd-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="689dd-107">C# 8.0 引入了可無可引用類型功能。</span><span class="sxs-lookup"><span data-stu-id="689dd-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="689dd-108">有關詳細資訊,請參閱[空參考類型](nullable-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="689dd-108">For more information, see [Nullable reference types](nullable-reference-types.md).</span></span> <span data-ttu-id="689dd-109">空值類型從 C# 2 開始可用。</span><span class="sxs-lookup"><span data-stu-id="689dd-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="689dd-110">任何空值類型都是泛型<xref:System.Nullable%601?displayProperty=nameWithType>結構的實例。</span><span class="sxs-lookup"><span data-stu-id="689dd-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="689dd-111">在以下任何可相互換表單中,可以參考具有基礎類型的`T`空值類型:`Nullable<T>``T?`或 。</span><span class="sxs-lookup"><span data-stu-id="689dd-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="689dd-112">當您需要表示基礎值類型的未定義值時,通常使用空值類型。</span><span class="sxs-lookup"><span data-stu-id="689dd-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="689dd-113">例如,布林`bool`或的變數只能是`true``false`或 。</span><span class="sxs-lookup"><span data-stu-id="689dd-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="689dd-114">但是,在某些應用程式中,變數值可能是未定義或缺少的。</span><span class="sxs-lookup"><span data-stu-id="689dd-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="689dd-115">例如,資料庫欄位可能包含`true``false`或 ,或者它可能不包含任何`NULL`值, 即 。</span><span class="sxs-lookup"><span data-stu-id="689dd-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="689dd-116">您可以在該方案中使用`bool?`類型。</span><span class="sxs-lookup"><span data-stu-id="689dd-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="689dd-117">宣告與指派</span><span class="sxs-lookup"><span data-stu-id="689dd-117">Declaration and assignment</span></span>

<span data-ttu-id="689dd-118">由於值類型是隱式轉換為相應的空值類型,因此可以將值分配給可空值類型的變數,就像對其基礎值類型執行此操作一樣。</span><span class="sxs-lookup"><span data-stu-id="689dd-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="689dd-119">您也可以指派 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="689dd-119">You also can assign the `null` value.</span></span> <span data-ttu-id="689dd-120">例如：</span><span class="sxs-lookup"><span data-stu-id="689dd-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="689dd-121">null 值類型的預設值`null`表示,即它是<xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>屬性`false`返回的實例。</span><span class="sxs-lookup"><span data-stu-id="689dd-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="689dd-122">檢查空值類型的實體</span><span class="sxs-lookup"><span data-stu-id="689dd-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="689dd-123">從 C# 7.0 開始,可以使用`null`[`is`具有類型模式的運算子](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching)來檢查基礎類型的空值類型的實體與基礎類型的值:</span><span class="sxs-lookup"><span data-stu-id="689dd-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="689dd-124">將使用以下唯讀屬性來檢查與取得可 null 值類型變數的值:</span><span class="sxs-lookup"><span data-stu-id="689dd-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="689dd-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>指示空值類型的實例是否具有其基礎類型的值。</span><span class="sxs-lookup"><span data-stu-id="689dd-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="689dd-126">若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。</span><span class="sxs-lookup"><span data-stu-id="689dd-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="689dd-127">若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="689dd-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="689dd-128">下面的範例使用`HasValue`屬性 在顯示變數之前測試變數是否包含值:</span><span class="sxs-lookup"><span data-stu-id="689dd-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="689dd-129">您還可以將空值類型的變數與`null`而不是使用`HasValue`屬性進行比較,如以下範例所示:</span><span class="sxs-lookup"><span data-stu-id="689dd-129">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="689dd-130">從空白型別轉換為基礎型態</span><span class="sxs-lookup"><span data-stu-id="689dd-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="689dd-131">如果要將空數型態的值分配給非空值類型變數,則可能需要指定要分配的值以代替`null`。</span><span class="sxs-lookup"><span data-stu-id="689dd-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="689dd-132">使用[空聚運算子`??`](../operators/null-coalescing-operator.md)執行此動作(您也可以將<xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType>方法用於相同的目的):</span><span class="sxs-lookup"><span data-stu-id="689dd-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="689dd-133">如果要使用 基礎值類型的[預設值](default-values.md)`null`代替<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>, 請使用方法。</span><span class="sxs-lookup"><span data-stu-id="689dd-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="689dd-134">您還可以顯式將空值類型轉換為非空類型,如下例所示:</span><span class="sxs-lookup"><span data-stu-id="689dd-134">You also can explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

<span data-ttu-id="689dd-135">在執行時,如果空數型態為`null`,則顯示式強制轉換<xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="689dd-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="689dd-136">不可空值類型`T`隱式轉換為相應的空值類型`T?`。</span><span class="sxs-lookup"><span data-stu-id="689dd-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="689dd-137">提高運算子</span><span class="sxs-lookup"><span data-stu-id="689dd-137">Lifted operators</span></span>

<span data-ttu-id="689dd-138">預定義的未元運算元和二進位[運算元](../operators/index.md)或值類型`T`支援的任何重載運算符也受相應的空值類型`T?`的支援。</span><span class="sxs-lookup"><span data-stu-id="689dd-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="689dd-139">這些操作者,也稱為*提升運算符*,如果`null`一個或兩個操作數是`null`; 如果一個或兩個操作數是,則生產。否則,運算符使用其操作數的包含值來計算結果。</span><span class="sxs-lookup"><span data-stu-id="689dd-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="689dd-140">例如：</span><span class="sxs-lookup"><span data-stu-id="689dd-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="689dd-141">對於`bool?`類型,預`&`定義 運算元`|`和 運算符不遵循本節中描述的規則:即使其中一個操作數`null`為 ,運算符評估的結果也可以為非 null。</span><span class="sxs-lookup"><span data-stu-id="689dd-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="689dd-142">如需詳細資訊，請參閱[布林邏輯運算子](../operators/boolean-logical-operators.md)一文的[可為 Null 的布林邏輯運算子](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="689dd-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="689dd-143">對於[比較運算子](../operators/comparison-operators.md)`<``>``<=`、、`>=`和 ,如果一個或兩`null`個操作數`false`是 ,則 結果是 ;否則,將比較操作數的包含值。</span><span class="sxs-lookup"><span data-stu-id="689dd-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="689dd-144">請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="689dd-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="689dd-145">下列範例會顯示 10</span><span class="sxs-lookup"><span data-stu-id="689dd-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="689dd-146">既不大於也不等於`null`</span><span class="sxs-lookup"><span data-stu-id="689dd-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="689dd-147">也不小於`null`</span><span class="sxs-lookup"><span data-stu-id="689dd-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="689dd-148">對於[相等運算符](../operators/equality-operators.md#equality-operator-)`==``null`, 如果兩個操作數均為 ,`true`則結果是 ,如果只有一`null`個操作數是`false`,則結果是;否則,將比較操作數的包含值。</span><span class="sxs-lookup"><span data-stu-id="689dd-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="689dd-149">對於[不等式運算符](../operators/equality-operators.md#inequality-operator-)`!=`,如果兩個操作數`null`均為 ,則`false`結果是 ,如果只有一個`null`操作數是 ,`true`則結果是;否則,將比較操作數的包含值。</span><span class="sxs-lookup"><span data-stu-id="689dd-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="689dd-150">如果兩種值類型之間存在[使用者定義的轉換](../operators/user-defined-conversion-operators.md),則在相應的空值類型之間也可以使用相同的轉換。</span><span class="sxs-lookup"><span data-stu-id="689dd-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="689dd-151">Boxing 和 Unboxing</span><span class="sxs-lookup"><span data-stu-id="689dd-151">Boxing and unboxing</span></span>

<span data-ttu-id="689dd-152">空白型態型`T?`態的 實體[:](../../programming-guide/types/boxing-and-unboxing.md)</span><span class="sxs-lookup"><span data-stu-id="689dd-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="689dd-153">若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。</span><span class="sxs-lookup"><span data-stu-id="689dd-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="689dd-154">如果<xref:System.Nullable%601.HasValue%2A>返回`true`,則基礎值類型`T`的 相應值將裝箱<xref:System.Nullable%601>,而不是 實例。</span><span class="sxs-lookup"><span data-stu-id="689dd-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="689dd-155">您可以將值型態`T`的 裝箱值解箱到相應的空`T?`值類型 ,如下例所示:</span><span class="sxs-lookup"><span data-stu-id="689dd-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="689dd-156">如何辨識可無效值類型</span><span class="sxs-lookup"><span data-stu-id="689dd-156">How to identify a nullable value type</span></span>

<span data-ttu-id="689dd-157">下面的範例展示如何確定<xref:System.Type?displayProperty=nameWithType>實體是否表示建構的 null 值類型,即具有指定<xref:System.Nullable%601?displayProperty=nameWithType>`T`類型參數的類型 :</span><span class="sxs-lookup"><span data-stu-id="689dd-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="689dd-158">如範例所示,您可以使用[類型的](../operators/type-testing-and-cast.md#typeof-operator)運算符創建<xref:System.Type?displayProperty=nameWithType>實例。</span><span class="sxs-lookup"><span data-stu-id="689dd-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="689dd-159">如果要確定實例是否為空值類型,請不要使用<xref:System.Object.GetType%2A?displayProperty=nameWithType>方法 獲取使用上述<xref:System.Type>代碼測試 實例。</span><span class="sxs-lookup"><span data-stu-id="689dd-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="689dd-160">當您在<xref:System.Object.GetType%2A?displayProperty=nameWithType>null 值類型的實體上調用 方法時,實體將[裝箱](#boxing-and-unboxing)到<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="689dd-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="689dd-161">由於空值類型的非空實例的裝箱等效於基礎類型的值裝箱,因此<xref:System.Object.GetType%2A>傳回表示空值類型的基礎類型<xref:System.Type>的 實體:</span><span class="sxs-lookup"><span data-stu-id="689dd-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

<span data-ttu-id="689dd-162">此外,不要使用[is](../operators/type-testing-and-cast.md#is-operator)運算元來確定實例是否具有空值類型。</span><span class="sxs-lookup"><span data-stu-id="689dd-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="689dd-163">如以下範例所示,您無法與`is`運算子區分空值類型實體的類型及其基礎類型實例:</span><span class="sxs-lookup"><span data-stu-id="689dd-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="689dd-164">可以使用以下範例中的代碼來確定實體是否具有空值類型:</span><span class="sxs-lookup"><span data-stu-id="689dd-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="689dd-165">將最後選取的檔案不適用於[空引檔型態](nullable-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="689dd-165">The methods described in this section are not applicable in the case of [nullable reference types](nullable-reference-types.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="689dd-166">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="689dd-166">C# language specification</span></span>

<span data-ttu-id="689dd-167">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="689dd-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="689dd-168">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="689dd-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="689dd-169">提高運算子</span><span class="sxs-lookup"><span data-stu-id="689dd-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="689dd-170">隱含式空轉換</span><span class="sxs-lookup"><span data-stu-id="689dd-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="689dd-171">明確可不正確轉換</span><span class="sxs-lookup"><span data-stu-id="689dd-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="689dd-172">提高轉換運算子</span><span class="sxs-lookup"><span data-stu-id="689dd-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="689dd-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="689dd-173">See also</span></span>

- [<span data-ttu-id="689dd-174">C# 參考</span><span class="sxs-lookup"><span data-stu-id="689dd-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="689dd-175">"提升"究竟是什麼意思?</span><span class="sxs-lookup"><span data-stu-id="689dd-175">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="689dd-176">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="689dd-176">Nullable reference types</span></span>](nullable-reference-types.md)
