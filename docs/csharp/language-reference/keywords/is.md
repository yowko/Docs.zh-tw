---
title: is - C# 參考
ms.custom: seodec18
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 2721048145253a441770a96f8383358bb1ceda01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710348"
---
# <a name="is-c-reference"></a><span data-ttu-id="01ccc-102">is (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="01ccc-102">is (C# Reference)</span></span> #

<span data-ttu-id="01ccc-103">檢查物件是否與指定的類型相容，或 (從 C# 7.0 開始) 根據模式來測試運算式。</span><span class="sxs-lookup"><span data-stu-id="01ccc-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="01ccc-104">測試類型相容性</span><span class="sxs-lookup"><span data-stu-id="01ccc-104">Testing for type compatibility</span></span> ##

<span data-ttu-id="01ccc-105">`is` 關鍵字會評估執行階段的類型相容性，</span><span class="sxs-lookup"><span data-stu-id="01ccc-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="01ccc-106">並判斷運算式的物件執行個體或結果是否可轉換成指定的類型。</span><span class="sxs-lookup"><span data-stu-id="01ccc-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="01ccc-107">其語法為</span><span class="sxs-lookup"><span data-stu-id="01ccc-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="01ccc-108">其中 *expr* 是評估為特定類型執行個體的運算式，而 *type* 是 *expr* 的結果要轉換的目標類型名稱。</span><span class="sxs-lookup"><span data-stu-id="01ccc-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="01ccc-109">如果 *expr* 不是 null，而且透過評估運算式所產生的物件可轉換成 *type*，則 `is` 陳述式為 `true`；否則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="01ccc-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="01ccc-110">例如，下列程式碼會判斷 `obj` 是否可轉換成 `Person` 類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="01ccc-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="01ccc-111">如果下列條件為真，則 `is` 陳述式為 true：</span><span class="sxs-lookup"><span data-stu-id="01ccc-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="01ccc-112">*expr* 是其類型與 *type* 相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="01ccc-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="01ccc-113">*expr* 是衍生自 *type* 的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="01ccc-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="01ccc-114">換句話說，*expr* 的結果可向上轉型成 *type* 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="01ccc-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="01ccc-115">*expr* 的編譯時期類型為 *type* 的基底類別，而 *expr* 的執行階段類型為 *type* 或衍生自 *type*。</span><span class="sxs-lookup"><span data-stu-id="01ccc-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="01ccc-116">變數的「編譯時期類型」是定義於變數宣告的變數類型。</span><span class="sxs-lookup"><span data-stu-id="01ccc-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="01ccc-117">變數的「執行階段類型」是指派給該變數的執行個體類型。</span><span class="sxs-lookup"><span data-stu-id="01ccc-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="01ccc-118">*expr* 是實作 *type* 介面的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="01ccc-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="01ccc-119">下列範例顯示在上述每個轉換過程中評估為 `true` 的 `is` 運算式。</span><span class="sxs-lookup"><span data-stu-id="01ccc-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="01ccc-120">如果運算式已知一定會是 `true` 或 `false`，`is` 關鍵字會產生編譯時期警告。</span><span class="sxs-lookup"><span data-stu-id="01ccc-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="01ccc-121">它只會考慮參考轉換、boxing 轉換和 unboxing 轉換，不會考慮使用者定義轉換，或是由類型的 [implicit](implicit.md) 和 [explicit](explicit.md) 運算子定義的轉換。</span><span class="sxs-lookup"><span data-stu-id="01ccc-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="01ccc-122">下列範例會產生警告，因為轉換的結果在編譯時期為已知。</span><span class="sxs-lookup"><span data-stu-id="01ccc-122">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="01ccc-123">請注意，從 `int` 轉換成 `long` 和 `double` 的 `is` 運算式會傳回 false，因為這些轉換是由 [implicit](implicit.md) 運算子處理。</span><span class="sxs-lookup"><span data-stu-id="01ccc-123">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="01ccc-124">`expr` 可以是傳回值的任何運算式，但匿名方法和 Lambda 運算式則除外。</span><span class="sxs-lookup"><span data-stu-id="01ccc-124">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="01ccc-125">下列範例使用 `is` 來評估方法呼叫的傳回值。</span><span class="sxs-lookup"><span data-stu-id="01ccc-125">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="01ccc-126">從 C# 7.0 開始，您可以搭配[類型模式](#type)使用模式比對來撰寫更簡潔的程式碼，以使用 `is` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="01ccc-126">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="01ccc-127">以 `is` 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="01ccc-127">Pattern matching with `is`</span></span> ##

<span data-ttu-id="01ccc-128">從 C# 7.0 開始，`is` 和 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式支援模式比對。</span><span class="sxs-lookup"><span data-stu-id="01ccc-128">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="01ccc-129">`is` 關鍵字支援下列模式：</span><span class="sxs-lookup"><span data-stu-id="01ccc-129">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="01ccc-130">[類型模式](#type)，測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="01ccc-130">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="01ccc-131">[常數模式](#constant)，測試運算式是否評估為指定的常數值。</span><span class="sxs-lookup"><span data-stu-id="01ccc-131">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="01ccc-132">[var 模式](#var)，比對一定會成功，而且會將運算式的值繫結至新的區域變數。</span><span class="sxs-lookup"><span data-stu-id="01ccc-132">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="01ccc-133"><a name="type" /> 類型模式 </a></span><span class="sxs-lookup"><span data-stu-id="01ccc-133"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="01ccc-134">使用類型模式執行模式比對時，`is` 會測試運算式是否可轉換成指定的類型；如果可以的話，則會將它轉換成該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="01ccc-134">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="01ccc-135">它是 `is` 陳述式的直接延伸，允許精簡類型的評估和轉換。</span><span class="sxs-lookup"><span data-stu-id="01ccc-135">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="01ccc-136">`is` 類型模式的一般格式為：</span><span class="sxs-lookup"><span data-stu-id="01ccc-136">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="01ccc-137">其中 *expr* 是評估為特定類型執行個體的運算式，*type* 是 *expr* 的結果要轉換的目標類型名稱，而 *varname* 是 *expr* 的結果所轉換的目標物件 (如果 `is` 測試為 `true`)。</span><span class="sxs-lookup"><span data-stu-id="01ccc-137">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="01ccc-138">如果 *expr* 不是 `null`，且符合下列任一項，則 `is` 運算式為 `true`：</span><span class="sxs-lookup"><span data-stu-id="01ccc-138">The `is` expression is `true` if *expr* is not `null`, and any of the following is true:</span></span>

- <span data-ttu-id="01ccc-139">*expr* 是其類型與 *type* 相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="01ccc-139">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="01ccc-140">*expr* 是衍生自 *type* 的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="01ccc-140">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="01ccc-141">換句話說，*expr* 的結果可向上轉型成 *type* 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="01ccc-141">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="01ccc-142">*expr* 的編譯時期類型為 *type* 的基底類別，而 *expr* 的執行階段類型為 *type* 或衍生自 *type*。</span><span class="sxs-lookup"><span data-stu-id="01ccc-142">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="01ccc-143">變數的「編譯時期類型」是定義於變數宣告的變數類型。</span><span class="sxs-lookup"><span data-stu-id="01ccc-143">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="01ccc-144">變數的「執行階段類型」是指派給該變數的執行個體類型。</span><span class="sxs-lookup"><span data-stu-id="01ccc-144">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="01ccc-145">*expr* 是實作 *type* 介面的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="01ccc-145">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="01ccc-146">如果 *exp* 為 `true`，且 `is` 與 `if` 陳述式搭配使用，則會指派 *varname* ；而且只在 `if` 陳述式內具有區域範圍。</span><span class="sxs-lookup"><span data-stu-id="01ccc-146">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="01ccc-147">下列範例使用 `is` 類型模式來提供類型之 <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="01ccc-147">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="01ccc-148">如果沒有模式比對，此程式碼可能會撰寫如下。</span><span class="sxs-lookup"><span data-stu-id="01ccc-148">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="01ccc-149">使用類型模式比對時，由於不需要測試轉換的結果是否為 `null`，因此會產生更精簡且容易閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="01ccc-149">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="01ccc-150">`is` 類型模式也會產生更精簡的程式碼，來判斷實值型別的類型。</span><span class="sxs-lookup"><span data-stu-id="01ccc-150">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="01ccc-151">下列範例使用 `is` 類型模式來判斷物件為 `Person` 或 `Dog` 執行個體，再顯示適當屬性的值。</span><span class="sxs-lookup"><span data-stu-id="01ccc-151">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="01ccc-152">不具有模式比對的對等程式碼需要包含明確轉換的個別指派。</span><span class="sxs-lookup"><span data-stu-id="01ccc-152">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="01ccc-153"><a name="constant" /> 常數模式</span><span class="sxs-lookup"><span data-stu-id="01ccc-153"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="01ccc-154">以常數模式執行模式比對時，`is` 會測試運算式是否等於指定的常數。</span><span class="sxs-lookup"><span data-stu-id="01ccc-154">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="01ccc-155">在 C# 6 (含) 以前版本中，[switch](switch.md) 陳述式支援常數模式。</span><span class="sxs-lookup"><span data-stu-id="01ccc-155">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="01ccc-156">從 C# 7.0 開始，`is` 陳述式也提供支援。</span><span class="sxs-lookup"><span data-stu-id="01ccc-156">Starting with C# 7.0, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="01ccc-157">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="01ccc-157">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="01ccc-158">其中 *expr* 是要評估的運算式，而 *constant* 是要測試的值。</span><span class="sxs-lookup"><span data-stu-id="01ccc-158">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="01ccc-159">*constant* 可以是下列任何常數運算式：</span><span class="sxs-lookup"><span data-stu-id="01ccc-159">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="01ccc-160">常值。</span><span class="sxs-lookup"><span data-stu-id="01ccc-160">A literal value.</span></span>

- <span data-ttu-id="01ccc-161">所宣告之 `const` 變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="01ccc-161">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="01ccc-162">列舉常數。</span><span class="sxs-lookup"><span data-stu-id="01ccc-162">An enumeration constant.</span></span>

<span data-ttu-id="01ccc-163">常數運算式評估如下：</span><span class="sxs-lookup"><span data-stu-id="01ccc-163">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="01ccc-164">如果 *expr* 和 *constant* 是整數型別，則 C# 等號比較運算子會判斷運算式是否傳回 `true` (亦即是否 `expr == constant`)。</span><span class="sxs-lookup"><span data-stu-id="01ccc-164">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="01ccc-165">否則，會呼叫靜態 [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) 方法來判斷運算式的值。</span><span class="sxs-lookup"><span data-stu-id="01ccc-165">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="01ccc-166">下列範例結合類型和常數模式來測試物件是否為 `Dice` 執行個體；如果是，則判斷擲出的骰子值是否為 6。</span><span class="sxs-lookup"><span data-stu-id="01ccc-166">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="01ccc-167">檢查是否可以使用常數模式來執行 `null`。</span><span class="sxs-lookup"><span data-stu-id="01ccc-167">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="01ccc-168">`is` 陳述式支援 `null` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="01ccc-168">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="01ccc-169">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="01ccc-169">Its syntax is:</span></span>

```csharp 
   expr is null
```

<span data-ttu-id="01ccc-170">下列範例示範 `null` 檢查的比較：</span><span class="sxs-lookup"><span data-stu-id="01ccc-170">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]
 
### <span data-ttu-id="01ccc-171"><a name="var" /> var 模式 </a></span><span class="sxs-lookup"><span data-stu-id="01ccc-171"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="01ccc-172">以 var 模式進行模式比對一定會成功。</span><span class="sxs-lookup"><span data-stu-id="01ccc-172">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="01ccc-173">其語法為</span><span class="sxs-lookup"><span data-stu-id="01ccc-173">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="01ccc-174">其中 *expr* 的值一定會指派給名為 *varname* 的區域變數。</span><span class="sxs-lookup"><span data-stu-id="01ccc-174">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="01ccc-175">*varname* 是其類型與 *expr* 相同的靜態變數。</span><span class="sxs-lookup"><span data-stu-id="01ccc-175">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="01ccc-176">下列範例使用 var 模式將運算式指派給名為 `obj` 的變數，</span><span class="sxs-lookup"><span data-stu-id="01ccc-176">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="01ccc-177">然後顯示 `obj` 的值和類型。</span><span class="sxs-lookup"><span data-stu-id="01ccc-177">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="01ccc-178">請注意，如果 *expr* 為 `null`，`is` 運算式仍為 true，而且會將 `null` 指派給 *varname*。</span><span class="sxs-lookup"><span data-stu-id="01ccc-178">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

## <a name="c-language-specification"></a><span data-ttu-id="01ccc-179">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="01ccc-179">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="01ccc-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01ccc-180">See also</span></span>

- [<span data-ttu-id="01ccc-181">C# 參考</span><span class="sxs-lookup"><span data-stu-id="01ccc-181">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="01ccc-182">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="01ccc-182">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="01ccc-183">typeof</span><span class="sxs-lookup"><span data-stu-id="01ccc-183">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)
- [<span data-ttu-id="01ccc-184">as</span><span class="sxs-lookup"><span data-stu-id="01ccc-184">as</span></span>](../../../csharp/language-reference/keywords/as.md)
- [<span data-ttu-id="01ccc-185">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="01ccc-185">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
