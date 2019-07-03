---
title: is - C# 參考
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 45e37dcb15e178fe37907e00cc14ef48c1bf230d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306584"
---
# <a name="is-c-reference"></a><span data-ttu-id="3f1a7-102">is (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3f1a7-102">is (C# Reference)</span></span>

<span data-ttu-id="3f1a7-103">`is` 運算子會檢查運算式的結果是否與指定的類型相容，或 (從 C# 7.0 開始) 根據模式來測試運算式。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-103">The `is` operator checks if the result of an expression is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span> <span data-ttu-id="3f1a7-104">如需類型測試 `is` 運算子的相關資訊，請參閱[類型測試和轉換運算子](../operators/type-testing-and-conversion-operators.md)一文的 [is 運算子](../operators/type-testing-and-conversion-operators.md#is-operator)小節。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-104">For information about the type-testing `is` operator see the [is operator](../operators/type-testing-and-conversion-operators.md#is-operator) section of the [Type-testing and conversion operators](../operators/type-testing-and-conversion-operators.md) article.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="3f1a7-105">以 `is` 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="3f1a7-105">Pattern matching with `is`</span></span>

<span data-ttu-id="3f1a7-106">從 C# 7.0 開始，`is` 和 [switch](switch.md) 陳述式支援模式比對。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-106">Starting with C# 7.0, the `is` and [switch](switch.md) statements support pattern matching.</span></span> <span data-ttu-id="3f1a7-107">`is` 關鍵字支援下列模式：</span><span class="sxs-lookup"><span data-stu-id="3f1a7-107">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="3f1a7-108">[類型模式](#type-pattern)，其能測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-108">[Type pattern](#type-pattern), which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="3f1a7-109">[常數模式](#constant-pattern)，測試運算式是否評估為指定的常數值。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-109">[Constant pattern](#constant-pattern), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="3f1a7-110">[var 模式](#var-pattern)，比對一定會成功，而且會將運算式的值繫結至新的區域變數。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-110">[var pattern](#var-pattern), a match that always succeeds and binds the value of an expression to a new local variable.</span></span>

### <a name="type-pattern"></a><span data-ttu-id="3f1a7-111">類型模式</span><span class="sxs-lookup"><span data-stu-id="3f1a7-111">Type pattern</span></span>

<span data-ttu-id="3f1a7-112">使用類型模式執行模式比對時，`is` 會測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-112">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="3f1a7-113">它是 `is` 陳述式的直覺性延伸，允許精簡的類型評估和轉換。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-113">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="3f1a7-114">`is` 類型模式的一般格式為：</span><span class="sxs-lookup"><span data-stu-id="3f1a7-114">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname
```

<span data-ttu-id="3f1a7-115">其中 *expr* 是評估為特定類型執行個體的運算式，*type* 是 *expr* 的結果要轉換的目標類型名稱，而 *varname* 是 *expr* 的結果所轉換的目標物件 (如果 `is` 測試為 `true`)。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-115">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="3f1a7-116">如果 *expr* 不是 `null`，且下列任何一個條件成立，則 `is` 運算式為 `true`：</span><span class="sxs-lookup"><span data-stu-id="3f1a7-116">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="3f1a7-117">*expr* 是其類型與 *type* 相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-117">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="3f1a7-118">*expr* 是衍生自 *type* 的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-118">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="3f1a7-119">換句話說，*expr* 的結果可向上轉型成 *type* 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-119">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="3f1a7-120">*expr* 的編譯時期類型為 *type* 的基底類別，而 *expr* 的執行階段類型為 *type* 或衍生自 *type*。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-120">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="3f1a7-121">變數的「編譯時期類型」  是定義於變數宣告的變數類型。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-121">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="3f1a7-122">變數的「執行階段類型」  是指派給該變數的執行個體類型。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-122">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="3f1a7-123">*expr* 是實作 *type* 介面的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-123">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="3f1a7-124">從 C# 7.1 開始，*expr* 可以擁有由泛型類型參數及其條件約束所定義的編譯時間類型。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-124">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span>

<span data-ttu-id="3f1a7-125">如果 *expr* 為 `true`，且 `is` 搭配 `if` 陳述式使用，則 *varname* 僅在 `if` 陳述式內指派。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-125">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned within the `if` statement only.</span></span> <span data-ttu-id="3f1a7-126">*varname* 的範圍從 `is` 運算式到包含 `if` 陳述式的區塊結尾。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-126">The scope of *varname* is from the `is` expression to the end of the block enclosing the `if` statement.</span></span> <span data-ttu-id="3f1a7-127">在任何其他位置使用 *varname*，會因使用尚未指派的變數而產生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-127">Using *varname* in any other location generates a compile-time error for use of a variable that has not been assigned.</span></span>

<span data-ttu-id="3f1a7-128">下列範例使用 `is` 類型模式來提供類型之 <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-128">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="3f1a7-129">如果沒有模式比對，此程式碼可能會撰寫如下。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-129">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="3f1a7-130">使用類型模式比對時，由於不需要測試轉換的結果是否為 `null`，因此會產生更精簡且容易閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-130">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="3f1a7-131">`is` 類型模式也會產生更精簡的程式碼，來判斷實值型別的類型。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-131">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="3f1a7-132">下列範例使用 `is` 類型模式來判斷物件為 `Person` 或 `Dog` 執行個體，再顯示適當屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-132">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span>

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="3f1a7-133">不具有模式比對的對等程式碼需要包含明確轉換的個別指派。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-133">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a><span data-ttu-id="3f1a7-134">常數模式</span><span class="sxs-lookup"><span data-stu-id="3f1a7-134">Constant pattern</span></span>

<span data-ttu-id="3f1a7-135">以常數模式執行模式比對時，`is` 會測試運算式是否等於指定的常數。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-135">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="3f1a7-136">在 C# 6 (含) 以前版本中，[switch](switch.md) 陳述式支援常數模式。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-136">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="3f1a7-137">從 C# 7.0 開始，它同時也被 `is` 陳述式支援。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-137">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="3f1a7-138">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="3f1a7-138">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="3f1a7-139">其中 *expr* 是要評估的運算式，而 *constant* 是要測試的值。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-139">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="3f1a7-140">*constant* 可以是下列任何常數運算式：</span><span class="sxs-lookup"><span data-stu-id="3f1a7-140">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="3f1a7-141">常值。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-141">A literal value.</span></span>

- <span data-ttu-id="3f1a7-142">所宣告之 `const` 變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-142">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="3f1a7-143">列舉常數。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-143">An enumeration constant.</span></span>

<span data-ttu-id="3f1a7-144">常數運算式評估如下：</span><span class="sxs-lookup"><span data-stu-id="3f1a7-144">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="3f1a7-145">如果 *expr* 和 *constant* 是整數型別，則 C# 等號比較運算子會判斷運算式是否傳回 `true` (亦即是否 `expr == constant`)。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-145">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="3f1a7-146">否則，會呼叫靜態 [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) 方法來判斷運算式的值。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-146">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="3f1a7-147">下列範例結合類型和常數模式來測試物件是否為 `Dice` 執行個體；如果是，則判斷擲出的骰子值是否為 6。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-147">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="3f1a7-148">檢查是否可以使用常數模式來執行 `null`。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-148">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="3f1a7-149">`is` 陳述式支援 `null` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-149">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="3f1a7-150">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="3f1a7-150">Its syntax is:</span></span>

```csharp
   expr is null
```

<span data-ttu-id="3f1a7-151">下列範例示範 `null` 檢查的比較：</span><span class="sxs-lookup"><span data-stu-id="3f1a7-151">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a><span data-ttu-id="3f1a7-152">var 模式</span><span class="sxs-lookup"><span data-stu-id="3f1a7-152">var pattern</span></span>

<span data-ttu-id="3f1a7-153">`var` 模式是任何類型或值的全能模式。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-153">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="3f1a7-154">*expr* 的值一律會被指派至類型與 *expr* 的編譯時間類型相同的區域變數。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-154">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="3f1a7-155">`is` 運算式的結果一律是 `true`。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-155">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="3f1a7-156">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="3f1a7-156">Its syntax is:</span></span>

```csharp
   expr is var varname
```

<span data-ttu-id="3f1a7-157">下列範例使用 var 模式將運算式指派給名為 `obj` 的變數，</span><span class="sxs-lookup"><span data-stu-id="3f1a7-157">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="3f1a7-158">然後顯示 `obj` 的值和類型。</span><span class="sxs-lookup"><span data-stu-id="3f1a7-158">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="3f1a7-159">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3f1a7-159">C# language specification</span></span>
  
<span data-ttu-id="3f1a7-160">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [is 運算子](~/_csharplang/spec/expressions.md#the-is-operator)一節，以及下列 C# 語言提案：</span><span class="sxs-lookup"><span data-stu-id="3f1a7-160">For more information, see [The is operator](~/_csharplang/spec/expressions.md#the-is-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the following C# language proposals:</span></span>

- [<span data-ttu-id="3f1a7-161">模式比對</span><span class="sxs-lookup"><span data-stu-id="3f1a7-161">Pattern matching</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="3f1a7-162">以一般項進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="3f1a7-162">Pattern matching with generics</span></span>](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a><span data-ttu-id="3f1a7-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f1a7-163">See also</span></span>

- [<span data-ttu-id="3f1a7-164">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3f1a7-164">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3f1a7-165">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="3f1a7-165">C# keywords</span></span>](index.md)
- [<span data-ttu-id="3f1a7-166">類型測試和轉換運算子</span><span class="sxs-lookup"><span data-stu-id="3f1a7-166">Type-testing and conversion operators</span></span>](../operators/type-testing-and-conversion-operators.md)
