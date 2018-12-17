---
title: 使用可為 Null 的型別 - C# 程式設計手冊
ms.custom: seodec18
description: 了解如何使用可為 Null 的型別
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: d2c6f2f78ed71558b71adcc1d4d8cc9a6f459d75
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235211"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="8d51c-103">使用可為 Null 的型別 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="8d51c-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="8d51c-104">可為 Null 的型別為代表所有基礎實值型別 `T` 值的型別，以及一個額外的 [null](../../language-reference/keywords/null.md) 值。</span><span class="sxs-lookup"><span data-stu-id="8d51c-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="8d51c-105">如需詳細資訊，請參閱[可為 Null 的型別](index.md)主題。</span><span class="sxs-lookup"><span data-stu-id="8d51c-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="8d51c-106">您可以下列任何一種形式參考可為 Null 的型別：`Nullable<T>` 或 `T?`。</span><span class="sxs-lookup"><span data-stu-id="8d51c-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="8d51c-107">這兩種形式可互換。</span><span class="sxs-lookup"><span data-stu-id="8d51c-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="8d51c-108">宣告與指派</span><span class="sxs-lookup"><span data-stu-id="8d51c-108">Declaration and assignment</span></span>

<span data-ttu-id="8d51c-109">與實值型別可隱含轉換為對應可為 Null 的型別相同，您可以用為其基礎實值型別指派值的相同方式，將值指派給可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="8d51c-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="8d51c-110">您也可以指派 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="8d51c-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="8d51c-111">例如: </span><span class="sxs-lookup"><span data-stu-id="8d51c-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="8d51c-112">檢查可為 Null 型別的值</span><span class="sxs-lookup"><span data-stu-id="8d51c-112">Examination of a nullable type value</span></span>

<span data-ttu-id="8d51c-113">使用下列唯讀屬性檢查可為 Null 型別的執行個體，擷取 null 或基礎型別的值：</span><span class="sxs-lookup"><span data-stu-id="8d51c-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <span data-ttu-id="8d51c-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 指出可為 Null 型別的執行個體是否有其基礎型別的值。</span><span class="sxs-lookup"><span data-stu-id="8d51c-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <span data-ttu-id="8d51c-115">若 <xref:System.Nullable%601.HasValue%2A> 為 `true`，則 <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> 會取得基礎型別的值。</span><span class="sxs-lookup"><span data-stu-id="8d51c-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="8d51c-116">若 <xref:System.Nullable%601.HasValue%2A> 為 `false`，則 <xref:System.Nullable%601.Value%2A> 屬性會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="8d51c-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="8d51c-117">下列範例中的程式碼會使用 `HasValue` 屬性，在顯示之前測試變數是否包含值：</span><span class="sxs-lookup"><span data-stu-id="8d51c-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="8d51c-118">您也可以使用 `null` 而非 `HasValue` 屬性，比較可為 Null 型別的變數，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d51c-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="8d51c-119">從 C# 7.0 開始，您可以使用[模式比對](../../pattern-matching.md)檢查及取得可為 Null 型別的值：</span><span class="sxs-lookup"><span data-stu-id="8d51c-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="8d51c-120">從可為 Null 型別轉換至基礎型別</span><span class="sxs-lookup"><span data-stu-id="8d51c-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="8d51c-121">若您需要將可為 Null 型別的值指派給不可為 Null 的型別，請使用 [null-coalescing 運算子 `??`](../../language-reference/operators/null-coalescing-operator.md) 指定當可為 Null 型別的值為 null 時，要指派的值 (您也可以使用 <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> 方法進行同樣的動作)：</span><span class="sxs-lookup"><span data-stu-id="8d51c-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="8d51c-122">若可為 Null 型別的值為 Null 時要使用的值為基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8d51c-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="8d51c-123">您也可以明確將可為 Null 的型別轉換為不可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="8d51c-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="8d51c-124">例如: </span><span class="sxs-lookup"><span data-stu-id="8d51c-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="8d51c-125">在執行階段，若可為 Null 型別的值為 Null，則明確轉換會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="8d51c-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="8d51c-126">不可為 Null 的實值型別會隱含轉換成對應的可為 Null 型別。</span><span class="sxs-lookup"><span data-stu-id="8d51c-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="8d51c-127">運算子</span><span class="sxs-lookup"><span data-stu-id="8d51c-127">Operators</span></span>

<span data-ttu-id="8d51c-128">預先定義的一元和二元運算子，以及針對實值型別而存在的任何使用者定義的運算子，也能為可為 Null 的型別所用。</span><span class="sxs-lookup"><span data-stu-id="8d51c-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="8d51c-129">若其中一或兩個運算元皆為 Null，這些運算子便會產生 Null 值；否則，運算子會使用包含的值來計算結果。</span><span class="sxs-lookup"><span data-stu-id="8d51c-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="8d51c-130">例如：</span><span class="sxs-lookup"><span data-stu-id="8d51c-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]
  
<span data-ttu-id="8d51c-131">針對關係運算子 (`<`、`>`、`<=`、`>=`)，若其中一或兩個運算元皆為 Null，則結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="8d51c-131">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="8d51c-132">請不要因為特定的比較 (例如 `<=`) 傳回 `false`，就假設相反的比較 (`>`) 就會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="8d51c-132">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="8d51c-133">下列範例會顯示 10</span><span class="sxs-lookup"><span data-stu-id="8d51c-133">The following example shows that 10 is</span></span>

- <span data-ttu-id="8d51c-134">既不大於，也不等於 Null，</span><span class="sxs-lookup"><span data-stu-id="8d51c-134">neither greater than or equal to null,</span></span>
- <span data-ttu-id="8d51c-135">也不小於 Null。</span><span class="sxs-lookup"><span data-stu-id="8d51c-135">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="8d51c-136">上述範例也顯示兩個可為 Null 的型別，當其值皆為 Null 時，其相等比較評估結果為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8d51c-136">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="8d51c-137">Boxing 和 Unboxing</span><span class="sxs-lookup"><span data-stu-id="8d51c-137">Boxing and unboxing</span></span>

<span data-ttu-id="8d51c-138">根據下列規則，可為 Null 的實值型別將為 [boxed](../types/boxing-and-unboxing.md)：</span><span class="sxs-lookup"><span data-stu-id="8d51c-138">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="8d51c-139">若 <xref:System.Nullable%601.HasValue%2A> 傳回 `false`，則會產生 Null 參考。</span><span class="sxs-lookup"><span data-stu-id="8d51c-139">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="8d51c-140">若 <xref:System.Nullable%601.HasValue%2A> 傳回 `true`，則基礎實值型別 `T` 的值為 boxed，而非 <xref:System.Nullable%601> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d51c-140">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="8d51c-141">您可以將已為 boxed 的實值型別 unbox 為對應的可為 Null 型別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d51c-141">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="the-bool-type"></a><span data-ttu-id="8d51c-142">bool? 類型</span><span class="sxs-lookup"><span data-stu-id="8d51c-142">The bool? type</span></span>

<span data-ttu-id="8d51c-143">`bool?` 可為 Null 的型別可以包含三個不同的值︰[true](../../language-reference/keywords/true-literal.md)、[false](../../language-reference/keywords/false-literal.md) 和 [null](../../language-reference/keywords/null.md)。</span><span class="sxs-lookup"><span data-stu-id="8d51c-143">The `bool?` nullable type can contain three different values: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), and [null](../../language-reference/keywords/null.md).</span></span> <span data-ttu-id="8d51c-144">`bool?` 型別與 SQL 中使用的 Boolean 變數型別相似。</span><span class="sxs-lookup"><span data-stu-id="8d51c-144">The `bool?` type is like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="8d51c-145">為確定 `&` 和 `|` 運算子所產生的結果與 SQL 的三個布林值類型一致，會提供下列預先定義的運算子︰</span><span class="sxs-lookup"><span data-stu-id="8d51c-145">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>

- `bool? operator &(bool? x, bool? y)`  
- `bool? operator |(bool? x, bool? y)`  
  
<span data-ttu-id="8d51c-146">這些運算子的語意是由下列表格定義的：</span><span class="sxs-lookup"><span data-stu-id="8d51c-146">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="8d51c-147">x</span><span class="sxs-lookup"><span data-stu-id="8d51c-147">x</span></span>|<span data-ttu-id="8d51c-148">y</span><span class="sxs-lookup"><span data-stu-id="8d51c-148">y</span></span>|<span data-ttu-id="8d51c-149">x&y</span><span class="sxs-lookup"><span data-stu-id="8d51c-149">x&y</span></span>|<span data-ttu-id="8d51c-150">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="8d51c-150">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="8d51c-151">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-151">true</span></span>|<span data-ttu-id="8d51c-152">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-152">true</span></span>|<span data-ttu-id="8d51c-153">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-153">true</span></span>|<span data-ttu-id="8d51c-154">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-154">true</span></span>|  
|<span data-ttu-id="8d51c-155">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-155">true</span></span>|<span data-ttu-id="8d51c-156">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-156">false</span></span>|<span data-ttu-id="8d51c-157">false</span><span class="sxs-lookup"><span data-stu-id="8d51c-157">false</span></span>|<span data-ttu-id="8d51c-158">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-158">true</span></span>|  
|<span data-ttu-id="8d51c-159">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-159">true</span></span>|<span data-ttu-id="8d51c-160">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-160">null</span></span>|<span data-ttu-id="8d51c-161">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-161">null</span></span>|<span data-ttu-id="8d51c-162">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-162">true</span></span>|  
|<span data-ttu-id="8d51c-163">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-163">false</span></span>|<span data-ttu-id="8d51c-164">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-164">true</span></span>|<span data-ttu-id="8d51c-165">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-165">false</span></span>|<span data-ttu-id="8d51c-166">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-166">true</span></span>|  
|<span data-ttu-id="8d51c-167">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-167">false</span></span>|<span data-ttu-id="8d51c-168">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-168">false</span></span>|<span data-ttu-id="8d51c-169">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-169">false</span></span>|<span data-ttu-id="8d51c-170">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-170">false</span></span>|  
|<span data-ttu-id="8d51c-171">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-171">false</span></span>|<span data-ttu-id="8d51c-172">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-172">null</span></span>|<span data-ttu-id="8d51c-173">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-173">false</span></span>|<span data-ttu-id="8d51c-174">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-174">null</span></span>|  
|<span data-ttu-id="8d51c-175">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-175">null</span></span>|<span data-ttu-id="8d51c-176">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-176">true</span></span>|<span data-ttu-id="8d51c-177">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-177">null</span></span>|<span data-ttu-id="8d51c-178">true</span><span class="sxs-lookup"><span data-stu-id="8d51c-178">true</span></span>|  
|<span data-ttu-id="8d51c-179">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-179">null</span></span>|<span data-ttu-id="8d51c-180">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-180">false</span></span>|<span data-ttu-id="8d51c-181">False</span><span class="sxs-lookup"><span data-stu-id="8d51c-181">false</span></span>|<span data-ttu-id="8d51c-182">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-182">null</span></span>|  
|<span data-ttu-id="8d51c-183">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-183">null</span></span>|<span data-ttu-id="8d51c-184">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-184">null</span></span>|<span data-ttu-id="8d51c-185">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-185">null</span></span>|<span data-ttu-id="8d51c-186">null</span><span class="sxs-lookup"><span data-stu-id="8d51c-186">null</span></span>|  

<span data-ttu-id="8d51c-187">請注意，這兩個運算子不會遵循[運算子](#operators)一節中描述的規則：即使其中一個運算元為 Null，運算子評估的結果也可能為非 Null。</span><span class="sxs-lookup"><span data-stu-id="8d51c-187">Note that these two operators don't follow the rules described in the [Operators](#operators) section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8d51c-188">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d51c-188">See Also</span></span>

- [<span data-ttu-id="8d51c-189">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="8d51c-189">Nullable types</span></span>](index.md)  
- [<span data-ttu-id="8d51c-190">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8d51c-190">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="8d51c-191">「增益」(Lift) 的真正意義是什麼？(英文)</span><span class="sxs-lookup"><span data-stu-id="8d51c-191">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)  
