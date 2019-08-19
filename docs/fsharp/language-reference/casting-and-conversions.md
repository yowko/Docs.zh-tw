---
title: 轉型和轉換
description: 瞭解程式F#設計語言如何為各種基本型別之間的算術轉換提供轉換運算子。
ms.date: 05/16/2016
ms.openlocfilehash: ee4df588caabf58c7b9e18961e217ef8f15fcf93
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630430"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="cfab1-103">轉型和轉換 (F#)</span><span class="sxs-lookup"><span data-stu-id="cfab1-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="cfab1-104">本主題描述中F#類型轉換的支援。</span><span class="sxs-lookup"><span data-stu-id="cfab1-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="cfab1-105">算術類型</span><span class="sxs-lookup"><span data-stu-id="cfab1-105">Arithmetic Types</span></span>

<span data-ttu-id="cfab1-106">F#提供各種基本類型 (例如整數和浮點類型之間) 之算術轉換的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="cfab1-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="cfab1-107">整數和字元轉換運算子具有 checked 和 unchecked 形式;浮點運算子和`enum`轉換運算子不會。</span><span class="sxs-lookup"><span data-stu-id="cfab1-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="cfab1-108">未檢查的表單定義`Microsoft.FSharp.Core.Operators`于中, 而檢查的窗`Microsoft.FSharp.Core.Operators.Checked`體則定義于中。</span><span class="sxs-lookup"><span data-stu-id="cfab1-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="cfab1-109">如果產生的值超出目標型別的限制, 檢查的表單會檢查溢位並產生執行時間例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cfab1-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="cfab1-110">每個運算子的名稱都與目的地類型的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="cfab1-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="cfab1-111">例如, 在下列程式碼中, 明確標注`byte`類型的會以兩個不同的意義出現。</span><span class="sxs-lookup"><span data-stu-id="cfab1-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="cfab1-112">第一次出現的是類型, 而第二個是轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="cfab1-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="cfab1-113">下表顯示在中定義的F#轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="cfab1-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="cfab1-114">運算子</span><span class="sxs-lookup"><span data-stu-id="cfab1-114">Operator</span></span>|<span data-ttu-id="cfab1-115">描述</span><span class="sxs-lookup"><span data-stu-id="cfab1-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="cfab1-116">轉換成 byte, 這是8位不帶正負號的類型。</span><span class="sxs-lookup"><span data-stu-id="cfab1-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="cfab1-117">轉換成帶正負號的位元組。</span><span class="sxs-lookup"><span data-stu-id="cfab1-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="cfab1-118">轉換為16位帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="cfab1-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="cfab1-119">轉換成16位不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="cfab1-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="cfab1-120">轉換為32位帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="cfab1-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="cfab1-121">轉換為32位不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="cfab1-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="cfab1-122">轉換為64位帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="cfab1-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="cfab1-123">轉換為64位不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="cfab1-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="cfab1-124">轉換成原生整數。</span><span class="sxs-lookup"><span data-stu-id="cfab1-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="cfab1-125">轉換成不帶正負號的原生整數。</span><span class="sxs-lookup"><span data-stu-id="cfab1-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="cfab1-126">轉換成64位雙精確度 IEEE 浮點數字。</span><span class="sxs-lookup"><span data-stu-id="cfab1-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="cfab1-127">轉換成32位單精確度 IEEE 浮點數字。</span><span class="sxs-lookup"><span data-stu-id="cfab1-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="cfab1-128">轉換成`System.Decimal`。</span><span class="sxs-lookup"><span data-stu-id="cfab1-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="cfab1-129">轉換為`System.Char`Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="cfab1-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="cfab1-130">轉換為列舉類型。</span><span class="sxs-lookup"><span data-stu-id="cfab1-130">Convert to an enumerated type.</span></span>|

<span data-ttu-id="cfab1-131">除了內建的基本型別之外, 您還可以搭配使用這些運算子與使用適當`op_Explicit`簽`op_Implicit`章來執行或方法的類型。</span><span class="sxs-lookup"><span data-stu-id="cfab1-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="cfab1-132">例如, `int`轉換運算子適用于任何提供靜態方法的類型, 而此`op_Explicit`方法會採用類型`int`做為參數並傳回。</span><span class="sxs-lookup"><span data-stu-id="cfab1-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="cfab1-133">如需方法無法以傳回型別多載的一般規則例外, 您可以針對`op_Explicit`和`op_Implicit`執行此動作。</span><span class="sxs-lookup"><span data-stu-id="cfab1-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="cfab1-134">列舉類型</span><span class="sxs-lookup"><span data-stu-id="cfab1-134">Enumerated Types</span></span>

<span data-ttu-id="cfab1-135">運算子是泛型運算子, 接受一個代表`enum`要轉換成之型別的型別參數。 `enum`</span><span class="sxs-lookup"><span data-stu-id="cfab1-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="cfab1-136">當它轉換成列舉型別時, 型別推斷會嘗試判斷您想`enum`要轉換成的型別。</span><span class="sxs-lookup"><span data-stu-id="cfab1-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="cfab1-137">在下列範例中, 不會`col1`明確標注變數, 但它的類型是從之後的相等測試推斷而來。</span><span class="sxs-lookup"><span data-stu-id="cfab1-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="cfab1-138">因此, 編譯器可以推算您要轉換為`Color`列舉的。</span><span class="sxs-lookup"><span data-stu-id="cfab1-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="cfab1-139">或者, 您可以提供類型注釋, 如下列範例`col2`所示。</span><span class="sxs-lookup"><span data-stu-id="cfab1-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="cfab1-140">您也可以將目標列舉型別明確指定為型別參數, 如下列程式碼所示:</span><span class="sxs-lookup"><span data-stu-id="cfab1-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="cfab1-141">請注意, 只有在列舉的基礎類型與所轉換的類型相容時, 列舉轉換才會生效。</span><span class="sxs-lookup"><span data-stu-id="cfab1-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="cfab1-142">在下列程式碼中, 因為和`int32` `uint32`之間的不相符, 所以轉換無法編譯。</span><span class="sxs-lookup"><span data-stu-id="cfab1-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="cfab1-143">如需詳細資訊, 請參閱[列舉](enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="cfab1-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="cfab1-144">轉換物件類型</span><span class="sxs-lookup"><span data-stu-id="cfab1-144">Casting Object Types</span></span>

<span data-ttu-id="cfab1-145">物件階層中的類型之間的轉換是物件導向程式設計的基礎。</span><span class="sxs-lookup"><span data-stu-id="cfab1-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="cfab1-146">轉換有兩種基本類型: [向上轉換] (upcasting) 和 [向下轉換] (向下檢視)。</span><span class="sxs-lookup"><span data-stu-id="cfab1-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="cfab1-147">向上轉換階層表示從衍生的物件參考轉換成基底物件參考。</span><span class="sxs-lookup"><span data-stu-id="cfab1-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="cfab1-148">只要基類位於衍生類別的繼承階層架構中, 這類轉換就一定會正常執行。</span><span class="sxs-lookup"><span data-stu-id="cfab1-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="cfab1-149">將階層從基底物件參考向下轉換至衍生的物件參考時, 只有在物件實際上是正確目的地 (衍生) 類型的實例, 或衍生自目的地類型的類型時, 才會成功。</span><span class="sxs-lookup"><span data-stu-id="cfab1-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="cfab1-150">F#提供這些轉換類型的運算子。</span><span class="sxs-lookup"><span data-stu-id="cfab1-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="cfab1-151">運算子會向上轉換階層, `:?>`而運算子會向下轉換階層。 `:>`</span><span class="sxs-lookup"><span data-stu-id="cfab1-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="cfab1-152">Upcasting</span><span class="sxs-lookup"><span data-stu-id="cfab1-152">Upcasting</span></span>

<span data-ttu-id="cfab1-153">在許多物件導向語言中, upcasting 都是隱含的;在F#中, 規則會稍有不同。</span><span class="sxs-lookup"><span data-stu-id="cfab1-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="cfab1-154">當您將引數傳遞至物件類型上的方法時, 會自動套用 Upcasting。</span><span class="sxs-lookup"><span data-stu-id="cfab1-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="cfab1-155">不過, 針對模組中的 let 系結函式, 除非將參數類型宣告為彈性類型, 否則 upcasting 不會是自動的。</span><span class="sxs-lookup"><span data-stu-id="cfab1-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="cfab1-156">如需詳細資訊, 請參閱[彈性類型](flexible-Types.md)。</span><span class="sxs-lookup"><span data-stu-id="cfab1-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="cfab1-157">`:>`運算子會執行靜態轉換, 這表示轉換成功是在編譯時期決定的。</span><span class="sxs-lookup"><span data-stu-id="cfab1-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="cfab1-158">如果使用`:>`成功編譯的轉換, 則它是有效的轉換, 而且在執行時間沒有任何可能發生的失敗。</span><span class="sxs-lookup"><span data-stu-id="cfab1-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="cfab1-159">您也可以使用`upcast`運算子來執行這類轉換。</span><span class="sxs-lookup"><span data-stu-id="cfab1-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="cfab1-160">下列運算式會指定階層的向上轉換:</span><span class="sxs-lookup"><span data-stu-id="cfab1-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="cfab1-161">當您使用向上轉型運算子時, 編譯器會嘗試從內容推斷您要轉換成的類型。</span><span class="sxs-lookup"><span data-stu-id="cfab1-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="cfab1-162">如果編譯器無法判斷目標型別, 則編譯器會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="cfab1-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="cfab1-163">向下檢視</span><span class="sxs-lookup"><span data-stu-id="cfab1-163">Downcasting</span></span>

<span data-ttu-id="cfab1-164">`:?>`運算子會執行動態轉換, 這表示在執行時間會決定轉換成功與否。</span><span class="sxs-lookup"><span data-stu-id="cfab1-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="cfab1-165">使用`:?>`運算子的轉換不會在編譯時期進行檢查, 但在執行時間, 會嘗試轉換成指定的類型。</span><span class="sxs-lookup"><span data-stu-id="cfab1-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="cfab1-166">如果物件與目標型別相容, 轉換就會成功。</span><span class="sxs-lookup"><span data-stu-id="cfab1-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="cfab1-167">如果物件與目標型別不相容, 則執行時間會引發`InvalidCastException`。</span><span class="sxs-lookup"><span data-stu-id="cfab1-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="cfab1-168">您也可以使用`downcast`運算子來執行動態類型轉換。</span><span class="sxs-lookup"><span data-stu-id="cfab1-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="cfab1-169">下列運算式會指定將階層向下轉換為從程式內容推斷的類型:</span><span class="sxs-lookup"><span data-stu-id="cfab1-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="cfab1-170">`upcast`就運算子而言, 如果編譯器無法從內容推斷特定目標型別, 就會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="cfab1-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="cfab1-171">下列程式碼說明如何使用`:>`和`:?>`運算子。</span><span class="sxs-lookup"><span data-stu-id="cfab1-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="cfab1-172">此程式碼說明`:?>`當您知道轉換會成功時, 最好使用運算子, 因為`InvalidCastException`它會在轉換失敗時擲回。</span><span class="sxs-lookup"><span data-stu-id="cfab1-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="cfab1-173">如果您不知道轉換將會成功, 使用`match`運算式的類型測試會較佳, 因為它可避免產生例外狀況的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="cfab1-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="cfab1-174">因為泛型運算子`downcast`和`upcast`依賴型別推斷來判斷引數和傳回型別, 所以在上述程式碼中, 您可以取代</span><span class="sxs-lookup"><span data-stu-id="cfab1-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="cfab1-175">取代為</span><span class="sxs-lookup"><span data-stu-id="cfab1-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="cfab1-176">在上述程式碼中, 引數類型和傳回類型`Derived1`分別`Base1`是和。</span><span class="sxs-lookup"><span data-stu-id="cfab1-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="cfab1-177">如需類型測試的詳細資訊, 請參閱[Match 運算式](match-Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="cfab1-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cfab1-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfab1-178">See also</span></span>

- [<span data-ttu-id="cfab1-179">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="cfab1-179">F# Language Reference</span></span>](index.md)
