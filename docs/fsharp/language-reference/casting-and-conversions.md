---
title: 轉型和轉換 (F#)
description: '了解如何 F # 程式設計語言提供轉換運算子的各種不同的基本型別之間的算術轉換。'
ms.date: 05/16/2016
ms.openlocfilehash: aca1a2523130ee485a7e7c9a6a45a410904cb246
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508383"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="410c6-103">轉型和轉換 (F#)</span><span class="sxs-lookup"><span data-stu-id="410c6-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="410c6-104">本主題描述支援 F # 中的型別轉換。</span><span class="sxs-lookup"><span data-stu-id="410c6-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="410c6-105">算術類型</span><span class="sxs-lookup"><span data-stu-id="410c6-105">Arithmetic Types</span></span>

<span data-ttu-id="410c6-106">F # 提供轉換運算子算術轉換之間不同的基本類型，例如整數和浮點類型之間。</span><span class="sxs-lookup"><span data-stu-id="410c6-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="410c6-107">整數和 char 的轉換運算子已核取及取消核取的表單;浮點運算子和`enum`轉換運算子不這麼做。</span><span class="sxs-lookup"><span data-stu-id="410c6-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="410c6-108">未選取的表單中所定義`Microsoft.FSharp.Core.Operators`並核取的形式定義於`Microsoft.FSharp.Core.Operators.Checked`。</span><span class="sxs-lookup"><span data-stu-id="410c6-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="410c6-109">已檢查的 form 溢位檢查，並產生執行階段例外狀況，如果產生的值超出目標類型的限制。</span><span class="sxs-lookup"><span data-stu-id="410c6-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="410c6-110">每個運算子有相同名稱做為目的地類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="410c6-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="410c6-111">例如，在下列程式碼，在其中的類型明確註解，`byte`會顯示兩個不同的意義。</span><span class="sxs-lookup"><span data-stu-id="410c6-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="410c6-112">第一個相符項目類型，而且第二個是轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="410c6-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="410c6-113">下表顯示 F # 中定義的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="410c6-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="410c6-114">運算子</span><span class="sxs-lookup"><span data-stu-id="410c6-114">Operator</span></span>|<span data-ttu-id="410c6-115">描述</span><span class="sxs-lookup"><span data-stu-id="410c6-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="410c6-116">轉換為 byte，8 位元不帶正負號的型別。</span><span class="sxs-lookup"><span data-stu-id="410c6-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="410c6-117">將轉換成帶正負號位元組。</span><span class="sxs-lookup"><span data-stu-id="410c6-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="410c6-118">將轉換成 16 位元帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="410c6-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="410c6-119">將轉換成 16 位元不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="410c6-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="410c6-120">將轉換為 32 位元帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="410c6-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="410c6-121">將轉換為 32 位元不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="410c6-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="410c6-122">將轉換為 64 位元帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="410c6-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="410c6-123">將轉換為 64 位元不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="410c6-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="410c6-124">將轉換成原生整數。</span><span class="sxs-lookup"><span data-stu-id="410c6-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="410c6-125">將轉換成帶正負號的原生整數。</span><span class="sxs-lookup"><span data-stu-id="410c6-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="410c6-126">將轉換為 64 位元雙精確度 IEEE 浮點數。</span><span class="sxs-lookup"><span data-stu-id="410c6-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="410c6-127">將轉換為 32 位元單精確度 IEEE 浮點數。</span><span class="sxs-lookup"><span data-stu-id="410c6-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="410c6-128">將轉換成`System.Decimal`。</span><span class="sxs-lookup"><span data-stu-id="410c6-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="410c6-129">將轉換成`System.Char`，Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="410c6-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="410c6-130">轉換為列舉類型。</span><span class="sxs-lookup"><span data-stu-id="410c6-130">Convert to an enumerated type.</span></span>|
<span data-ttu-id="410c6-131">除了內建基本類型，您可以使用這些運算子與實作的型別`op_Explicit`或`op_Implicit`具有適當簽章的方法。</span><span class="sxs-lookup"><span data-stu-id="410c6-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="410c6-132">例如，`int`轉換運算子的運作方式與任何提供靜態方法的型別`op_Explicit`採用類型做為參數，並傳回`int`。</span><span class="sxs-lookup"><span data-stu-id="410c6-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="410c6-133">方法無法傳回型別多載的一般規則的特殊例外狀況，您可以在進行這`op_Explicit`和`op_Implicit`。</span><span class="sxs-lookup"><span data-stu-id="410c6-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="410c6-134">列舉型別</span><span class="sxs-lookup"><span data-stu-id="410c6-134">Enumerated Types</span></span>

<span data-ttu-id="410c6-135">`enum`運算子是一般運算子接受一個型別參數表示的型別`enum`將轉換成。</span><span class="sxs-lookup"><span data-stu-id="410c6-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="410c6-136">當轉換為列舉類型時，輸入判斷型別推斷嘗試`enum`您想要轉換成。</span><span class="sxs-lookup"><span data-stu-id="410c6-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="410c6-137">在下列範例中，變數`col1`未明確標註，但其類型從較新的等號比較測試推斷。</span><span class="sxs-lookup"><span data-stu-id="410c6-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="410c6-138">因此，編譯器可以推斷，您會將它轉換成`Color`列舉型別。</span><span class="sxs-lookup"><span data-stu-id="410c6-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="410c6-139">或者，您可以在其中提供的型別註釋，如同`col2`在下列範例中。</span><span class="sxs-lookup"><span data-stu-id="410c6-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="410c6-140">您也可以明確指定目標的列舉型別與型別參數，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="410c6-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="410c6-141">請注意，列舉型別轉換工作，只有當列舉的基礎類型是要轉換之類型相容。</span><span class="sxs-lookup"><span data-stu-id="410c6-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="410c6-142">下列程式碼，轉換無法編譯，因為不相符`int32`和`uint32`。</span><span class="sxs-lookup"><span data-stu-id="410c6-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="410c6-143">如需詳細資訊，請參閱 <<c0> [ 列舉型別](enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="410c6-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="410c6-144">轉型物件類型</span><span class="sxs-lookup"><span data-stu-id="410c6-144">Casting Object Types</span></span>

<span data-ttu-id="410c6-145">在物件階層架構中的型別之間的轉換是物件導向程式設計的基礎。</span><span class="sxs-lookup"><span data-stu-id="410c6-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="410c6-146">有兩個基本類型的轉換: （向上轉型） 向上轉型和轉型下 （向下轉型）。</span><span class="sxs-lookup"><span data-stu-id="410c6-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="410c6-147">階層架構中向上轉型表示從衍生的物件參考的基底物件參考的轉型。</span><span class="sxs-lookup"><span data-stu-id="410c6-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="410c6-148">這類轉換保證可以運作，只要基底類別衍生類別的繼承階層架構中。</span><span class="sxs-lookup"><span data-stu-id="410c6-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="410c6-149">物件實際上是正確的目的地 （衍生） 型別或目的型別衍生之類型的執行個體時，才會從衍生的物件參考的基底物件參考的階層中向下轉型成功。</span><span class="sxs-lookup"><span data-stu-id="410c6-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="410c6-150">F # 提供這些類型的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="410c6-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="410c6-151">`:>`運算子會轉換為階層架構，而`:?>`運算子會轉換為階層中向下。</span><span class="sxs-lookup"><span data-stu-id="410c6-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="410c6-152">向上轉型</span><span class="sxs-lookup"><span data-stu-id="410c6-152">Upcasting</span></span>

<span data-ttu-id="410c6-153">在許多物件導向語言中，向上轉型是隱含的;在 F # 中，規則會稍有不同。</span><span class="sxs-lookup"><span data-stu-id="410c6-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="410c6-154">將引數傳遞給方法的物件型別上時，會自動套用向上轉型。</span><span class="sxs-lookup"><span data-stu-id="410c6-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="410c6-155">不過，在模組中的 let 繫結函式，向上轉型不是自動的除非參數類型宣告為有彈性的類型。</span><span class="sxs-lookup"><span data-stu-id="410c6-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="410c6-156">如需詳細資訊，請參閱 <<c0> [ 彈性類型](flexible-Types.md)。</span><span class="sxs-lookup"><span data-stu-id="410c6-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="410c6-157">`:>`運算子會執行靜態轉型，這表示成功的轉換在編譯時期決定。</span><span class="sxs-lookup"><span data-stu-id="410c6-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="410c6-158">如果轉換使用`:>`會編譯成功，它是有效的轉型，並在執行階段中有不可能的失敗。</span><span class="sxs-lookup"><span data-stu-id="410c6-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="410c6-159">您也可以使用`upcast`運算子來執行這類轉換。</span><span class="sxs-lookup"><span data-stu-id="410c6-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="410c6-160">下列運算式會指定在階層中向上轉換：</span><span class="sxs-lookup"><span data-stu-id="410c6-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="410c6-161">當您使用向上轉型運算子時，編譯器會嘗試推斷您要從內容將轉換成的型別。</span><span class="sxs-lookup"><span data-stu-id="410c6-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="410c6-162">如果編譯器無法判斷目標型別，則編譯器會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="410c6-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="410c6-163">向下轉型</span><span class="sxs-lookup"><span data-stu-id="410c6-163">Downcasting</span></span>

<span data-ttu-id="410c6-164">`:?>`運算子會執行動態轉換，這表示成功的轉換在執行階段決定。</span><span class="sxs-lookup"><span data-stu-id="410c6-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="410c6-165">使用 cast`:?>`運算子不會檢查在編譯時期; 但在執行階段，嘗試轉換指定的型別。</span><span class="sxs-lookup"><span data-stu-id="410c6-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="410c6-166">如果物件是與目標型別相容，轉換就會成功。</span><span class="sxs-lookup"><span data-stu-id="410c6-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="410c6-167">如果物件不相容的目標型別，就會引發執行階段`InvalidCastException`。</span><span class="sxs-lookup"><span data-stu-id="410c6-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="410c6-168">您也可以使用`downcast`執行動態型別轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="410c6-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="410c6-169">下列運算式會指定從程式內容推斷的型別階層中向下轉換：</span><span class="sxs-lookup"><span data-stu-id="410c6-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="410c6-170">與`upcast`運算子，如果編譯器無法推斷特定的目標型別，從內容，則會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="410c6-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="410c6-171">下列程式碼說明如何使用`:>`和`:?>`運算子。</span><span class="sxs-lookup"><span data-stu-id="410c6-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="410c6-172">程式碼將說明`:?>`運算子用在您知道，轉換會成功，因為它會擲回`InvalidCastException`如果轉換失敗。</span><span class="sxs-lookup"><span data-stu-id="410c6-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="410c6-173">如果您不知道，轉換會成功，會使用型別測試`match`運算式是較佳，因為它可避免產生例外狀況的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="410c6-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="410c6-174">因為泛型運算子`downcast`和`upcast`依賴類型推斷來判斷引數和傳回型別，在上述程式碼中的，您可以取代</span><span class="sxs-lookup"><span data-stu-id="410c6-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="410c6-175">取代為</span><span class="sxs-lookup"><span data-stu-id="410c6-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="410c6-176">在先前的程式碼的引數類型和傳回類型是`Derived1`和`Base1`分別。</span><span class="sxs-lookup"><span data-stu-id="410c6-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="410c6-177">如需型別測試的詳細資訊，請參閱[比對運算式](match-Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="410c6-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="410c6-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="410c6-178">See also</span></span>

- [<span data-ttu-id="410c6-179">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="410c6-179">F# Language Reference</span></span>](index.md)
