---
title: "is (C# 參考)"
keywords: "is 關鍵字 (C#), is (C#)"
ms.date: 02/17/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords: is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f0242439caa21268a6c314409f41587890c4126
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="is-c-reference"></a><span data-ttu-id="ae285-103">is (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ae285-103">is (C# Reference)</span></span> #

<span data-ttu-id="ae285-104">檢查物件是否與指定的類型相容，或 (從 C# 7 開始) 根據模式來測試運算式。</span><span class="sxs-lookup"><span data-stu-id="ae285-104">Checks if an object is compatible with a given type, or (starting with C# 7) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="ae285-105">測試類型相容性</span><span class="sxs-lookup"><span data-stu-id="ae285-105">Testing for type compatibility</span></span> ##

<span data-ttu-id="ae285-106">`is` 關鍵字會評估執行階段的類型相容性，</span><span class="sxs-lookup"><span data-stu-id="ae285-106">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="ae285-107">並判斷運算式的物件執行個體或結果是否可轉換成指定的類型。</span><span class="sxs-lookup"><span data-stu-id="ae285-107">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="ae285-108">其語法為</span><span class="sxs-lookup"><span data-stu-id="ae285-108">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="ae285-109">其中 *expr* 是評估為特定類型執行個體的運算式，而 *type* 是 *expr* 的結果要轉換的目標類型名稱。</span><span class="sxs-lookup"><span data-stu-id="ae285-109">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="ae285-110">如果 *expr* 不是 null，而且透過評估運算式所產生的物件可轉換成 *type*，則 `is` 陳述式為 `true`；否則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="ae285-110">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="ae285-111">例如，下列程式碼會判斷 `obj` 是否可轉換成 `Person` 類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="ae285-111">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="ae285-112">如果下列條件為真，則 `is` 陳述式為 true：</span><span class="sxs-lookup"><span data-stu-id="ae285-112">The `is` statement is true if:</span></span>

- <span data-ttu-id="ae285-113">*expr* 是其類型與 *type* 相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae285-113">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="ae285-114">*expr* 是衍生自 *type* 的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae285-114">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="ae285-115">換句話說，*expr* 的結果可向上轉型成 *type* 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae285-115">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="ae285-116">*expr* 的編譯時期類型為 *type* 的基底類別，而 *expr* 的執行階段類型為 *type* 或衍生自 *type*。</span><span class="sxs-lookup"><span data-stu-id="ae285-116">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="ae285-117">變數的「編譯時期類型」是定義於變數宣告的變數類型。</span><span class="sxs-lookup"><span data-stu-id="ae285-117">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="ae285-118">變數的「執行階段類型」是指派給該變數的執行個體類型。</span><span class="sxs-lookup"><span data-stu-id="ae285-118">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="ae285-119">*expr* 是實作 *type* 介面的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae285-119">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="ae285-120">下列範例顯示在上述每個轉換過程中評估為 `true` 的 `is` 運算式。</span><span class="sxs-lookup"><span data-stu-id="ae285-120">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="ae285-121">如果運算式已知一定會是 `true` 或 `false`，`is` 關鍵字會產生編譯時期警告。</span><span class="sxs-lookup"><span data-stu-id="ae285-121">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="ae285-122">它只會考慮參考轉換、boxing 轉換和 unboxing 轉換，不會考慮使用者定義轉換，或是由類型的 [implicit](implicit.md) 和 [explicit](explicit.md) 運算子定義的轉換。</span><span class="sxs-lookup"><span data-stu-id="ae285-122">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="ae285-123">下列範例會產生警告，因為轉換的結果在編譯時期為已知。</span><span class="sxs-lookup"><span data-stu-id="ae285-123">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="ae285-124">請注意，從 `int` 轉換成 `long` 和 `double` 的 `is` 運算式會傳回 false，因為這些轉換是由 [implicit](implicit.md) 運算子處理。</span><span class="sxs-lookup"><span data-stu-id="ae285-124">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="ae285-125">`expr` 可以是傳回值的任何運算式，但匿名方法和 Lambda 運算式則除外。</span><span class="sxs-lookup"><span data-stu-id="ae285-125">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="ae285-126">下列範例使用 `is` 來評估方法呼叫的傳回值。</span><span class="sxs-lookup"><span data-stu-id="ae285-126">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="ae285-127">從 C# 7 開始，您可以搭配[類型模式](#type)使用模式比對來撰寫更簡潔的程式碼，以使用 `is` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ae285-127">Starting with C# 7, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="ae285-128">以 `is` 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="ae285-128">Pattern matching with `is`</span></span> ##

<span data-ttu-id="ae285-129">從 C# 7 開始，`is` 和 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式支援模式比對。</span><span class="sxs-lookup"><span data-stu-id="ae285-129">Starting with C# 7, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="ae285-130">`is` 關鍵字支援下列模式：</span><span class="sxs-lookup"><span data-stu-id="ae285-130">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="ae285-131">[類型模式](#type)，測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="ae285-131">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="ae285-132">[常數模式](#constant)，測試運算式是否評估為指定的常數值。</span><span class="sxs-lookup"><span data-stu-id="ae285-132">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="ae285-133">[var 模式](#var)，比對一定會成功，而且會將運算式的值繫結至新的區域變數。</span><span class="sxs-lookup"><span data-stu-id="ae285-133">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="ae285-134"><a name="type" /> 類型模式 </a></span><span class="sxs-lookup"><span data-stu-id="ae285-134"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="ae285-135">使用類型模式執行模式比對時，`is` 會測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="ae285-135">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="ae285-136">它是 `is` 陳述式的直接延伸，允許精簡類型的評估和轉換。</span><span class="sxs-lookup"><span data-stu-id="ae285-136">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="ae285-137">`is` 類型模式的一般格式為：</span><span class="sxs-lookup"><span data-stu-id="ae285-137">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="ae285-138">其中 *expr* 是評估為特定類型執行個體的運算式，*type* 是 *expr* 的結果要轉換的目標類型名稱，而 *varname* 是 *expr* 的結果所轉換的目標物件 (如果 `is` 測試為 `true`)。</span><span class="sxs-lookup"><span data-stu-id="ae285-138">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="ae285-139">如果下列任一項為真，`is` 運算式為`true`：</span><span class="sxs-lookup"><span data-stu-id="ae285-139">The `is` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="ae285-140">*expr* 是其類型與 *type* 相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae285-140">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="ae285-141">*expr* 是衍生自 *type* 的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae285-141">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="ae285-142">換句話說，*expr* 的結果可向上轉型成 *type* 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae285-142">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="ae285-143">*expr* 的編譯時期類型為 *type* 的基底類別，而 *expr* 的執行階段類型為 *type* 或衍生自 *type*。</span><span class="sxs-lookup"><span data-stu-id="ae285-143">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="ae285-144">變數的「編譯時期類型」是定義於變數宣告的變數類型。</span><span class="sxs-lookup"><span data-stu-id="ae285-144">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="ae285-145">變數的「執行階段類型」是指派給該變數的執行個體類型。</span><span class="sxs-lookup"><span data-stu-id="ae285-145">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="ae285-146">*expr* 是實作 *type* 介面的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae285-146">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="ae285-147">如果 *exp* 為 `true`，而且 `is` 搭配 `if` 陳述式使用，則 *varname* 會被指派，而且只在 `if` 陳述式內具有區域範圍。</span><span class="sxs-lookup"><span data-stu-id="ae285-147">If *exp* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="ae285-148">下列範例使用 `is` 類型模式來提供類型之 <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="ae285-148">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="ae285-149">如果沒有模式比對，此程式碼可能會撰寫如下。</span><span class="sxs-lookup"><span data-stu-id="ae285-149">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="ae285-150">使用類型模式比對時，由於不需要測試轉換的結果是否為 `null`，因此會產生更精簡且容易閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae285-150">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="ae285-151">`is` 類型模式也會產生更精簡的程式碼，來判斷實值型別的類型。</span><span class="sxs-lookup"><span data-stu-id="ae285-151">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="ae285-152">下列範例使用 `is` 類型模式來判斷物件為 `Person` 或 `Dog` 執行個體，再顯示適當屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ae285-152">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="ae285-153">不具有模式比對的對等程式碼需要包含明確轉換的個別指派。</span><span class="sxs-lookup"><span data-stu-id="ae285-153">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="ae285-154"><a name="constant" /> 常數模式</span><span class="sxs-lookup"><span data-stu-id="ae285-154"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="ae285-155">以常數模式執行模式比對時，`is` 會測試運算式是否等於指定的常數。</span><span class="sxs-lookup"><span data-stu-id="ae285-155">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="ae285-156">在 C# 6 (含) 以前版本中，[switch](switch.md) 陳述式支援常數模式。</span><span class="sxs-lookup"><span data-stu-id="ae285-156">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="ae285-157">從 C# 7 開始，`is` 陳述式也提供支援。</span><span class="sxs-lookup"><span data-stu-id="ae285-157">Starting with C# 7, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="ae285-158">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="ae285-158">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="ae285-159">其中 *expr* 是要評估的運算式，而 *constant* 是要測試的值。</span><span class="sxs-lookup"><span data-stu-id="ae285-159">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="ae285-160">*constant* 可以是下列任何常數運算式：</span><span class="sxs-lookup"><span data-stu-id="ae285-160">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="ae285-161">常值。</span><span class="sxs-lookup"><span data-stu-id="ae285-161">A literal value.</span></span>

- <span data-ttu-id="ae285-162">所宣告之 `const` 變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="ae285-162">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="ae285-163">列舉常數。</span><span class="sxs-lookup"><span data-stu-id="ae285-163">An enumeration constant.</span></span>

<span data-ttu-id="ae285-164">常數運算式評估如下：</span><span class="sxs-lookup"><span data-stu-id="ae285-164">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="ae285-165">如果 *expr* 和 *constant* 是整數型別，則 C# 等號比較運算子會判斷運算式是否傳回 `true` (亦即是否 `expr == constant`)。</span><span class="sxs-lookup"><span data-stu-id="ae285-165">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="ae285-166">否則，會呼叫靜態 [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) 方法來判斷運算式的值。</span><span class="sxs-lookup"><span data-stu-id="ae285-166">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="ae285-167">下列範例結合類型和常數模式來測試物件是否為 `Dice` 執行個體；如果是，則判斷擲出的骰子值是否為 6。</span><span class="sxs-lookup"><span data-stu-id="ae285-167">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <span data-ttu-id="ae285-168"><a name="var" /> var 模式 </a></span><span class="sxs-lookup"><span data-stu-id="ae285-168"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="ae285-169">以 var 模式進行模式比對一定會成功。</span><span class="sxs-lookup"><span data-stu-id="ae285-169">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="ae285-170">其語法為</span><span class="sxs-lookup"><span data-stu-id="ae285-170">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="ae285-171">其中 *expr* 的值一定會指派給名為 *varname* 的區域變數。</span><span class="sxs-lookup"><span data-stu-id="ae285-171">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="ae285-172">*varname* 是其類型與 *expr* 相同的靜態變數。</span><span class="sxs-lookup"><span data-stu-id="ae285-172">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="ae285-173">下列範例使用 var 模式將運算式指派給名為 `obj` 的變數，</span><span class="sxs-lookup"><span data-stu-id="ae285-173">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="ae285-174">然後顯示 `obj` 的值和類型。</span><span class="sxs-lookup"><span data-stu-id="ae285-174">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="ae285-175">請注意，如果 *expr* 為 `null`，`is` 運算式仍為 true，而且會將 `null` 指派給 *varname*。</span><span class="sxs-lookup"><span data-stu-id="ae285-175">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="ae285-176">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ae285-176">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ae285-177">請參閱</span><span class="sxs-lookup"><span data-stu-id="ae285-177">See also</span></span>  
 [<span data-ttu-id="ae285-178">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ae285-178">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ae285-179">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ae285-179">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ae285-180">typeof</span><span class="sxs-lookup"><span data-stu-id="ae285-180">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 [<span data-ttu-id="ae285-181">as</span><span class="sxs-lookup"><span data-stu-id="ae285-181">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
 [<span data-ttu-id="ae285-182">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="ae285-182">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
