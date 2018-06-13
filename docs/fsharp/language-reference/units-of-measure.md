---
title: 測量單位 (F#)
description: '了解如何浮點數和 F # 中的帶正負號的整數值可以具有相關聯的度量單位，通常會表示長度、 磁碟區，以及大量使用。'
ms.date: 05/16/2016
ms.openlocfilehash: 3e47c92100c1dd99161be709a065913f501854f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564947"
---
# <a name="units-of-measure"></a><span data-ttu-id="cdd5b-103">測量單位</span><span class="sxs-lookup"><span data-stu-id="cdd5b-103">Units of Measure</span></span>

<span data-ttu-id="cdd5b-104">浮點和帶正負號的整數值在 F # 中可以有關聯的度量單位，通常用來表示長度，磁碟區、 大量，依此類推。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="cdd5b-105">您可以藉由使用單位的數量，啟用編譯器驗證算術的關聯性沒有正確的單位，這有助於防止程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>


## <a name="syntax"></a><span data-ttu-id="cdd5b-106">語法</span><span class="sxs-lookup"><span data-stu-id="cdd5b-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="cdd5b-107">備註</span><span class="sxs-lookup"><span data-stu-id="cdd5b-107">Remarks</span></span>
<span data-ttu-id="cdd5b-108">先前語法定義*單位名稱*做為度量單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="cdd5b-109">選擇性的部分用來定義新的量值，根據先前定義的單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="cdd5b-110">例如，下列一行會定義量值`cm`（公分）。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="cdd5b-111">下列一行會定義量值`ml`(milliliter) 為三次方公分 (`cm^3`)。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="cdd5b-112">在先前的語法，*量值*是一種公式，包括單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="cdd5b-113">在公式中涉及的單位，整數次方 （正數和負數） 支援、 單位之間的空格會表示產品的兩個單位，`*`也會指出單位的產品和`/`表示單位的商數。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="cdd5b-114">交互單位，您可以使用負值的整數次方或`/`指出分子之間分母單元公式的隔離。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="cdd5b-115">應該以括號括住在分母中的多個單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="cdd5b-116">單位以之後的空格分隔`/`會解譯為屬於分母，但下列任何單元`*`都會解譯為分子的一部分。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="cdd5b-117">您可以使用 1 單位在運算式中，單獨用於表示程度的數量，或搭配其他的單位，例如分子。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="cdd5b-118">比方說，率的單位會寫成`1/s`，其中`s`表示秒數。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="cdd5b-119">括號不會以單元公式。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="cdd5b-120">單元公式; 中沒有指定數值的轉換常數不過，分別定義轉換常數的單位，然後在單位檢查計算中使用它們。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="cdd5b-121">相同的意義的單元公式可以撰寫以相等的各種方式。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="cdd5b-122">因此，編譯器會將單位公式轉換成一致的格式，將負乘方倒數、 群組單位轉換成單一的分子和，並依字母順序排列的分子和分母中的單元。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="cdd5b-123">例如，單元公式`kg m s^-2`和`m /s s * kg`都會轉換成`kg m/s^2`。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="cdd5b-124">您可以使用測量的單位的浮動點運算式。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="cdd5b-125">使用浮點數連同相關聯的單位量值加入另一個層級的型別安全，因此有助於避免使用弱型別浮點數時，可以發生在公式中的單位不符錯誤。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="cdd5b-126">如果您撰寫的浮動點使用的單位的運算式，必須符合在運算式中的單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="cdd5b-127">下列範例所示，您可以標註具有單元公式在角括弧中的常值。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="cdd5b-128">您不將放在數字的角括號; 之間的空間不過，您可以包含常值後置詞例如`f`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="cdd5b-129">這類的註解變更自其基本類型的常值類型 (例如`float`) 為維度的類型，例如`float<cm>`或在此情況下， `float<miles/hour>`。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="cdd5b-130">單位註解`<1>`指出程度的數量，而它的類型相當於沒有單元參數的基本類型。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="cdd5b-131">測量單位的型別是浮點數或帶正負號整數類資料類型以及額外單元註釋，方括號中指出。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="cdd5b-132">因此，當您撰寫的類型轉換，以從`g`（字母組） 到`kg`（公斤），描述類型，如下所示。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="cdd5b-133">測量單位用於檢查的編譯時間單位，但不是會保存在執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="cdd5b-134">因此，它們不會影響效能。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="cdd5b-135">測量單位可以套用至任何類型，不只浮點類型。不過，只有浮點類型，帶正負號整數類資料類型和十進位型別的支援建立維度數量。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="cdd5b-136">因此，它才有意義的基本型別和彙總包含這些基本型別上使用的測量單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="cdd5b-137">下列範例說明如何使用的測量單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
<span data-ttu-id="cdd5b-138">下列程式碼範例說明如何從程度的浮點數轉換成維度的浮動點值。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="cdd5b-139">您只將其乘以 1.0，套用到 1.0 的維度。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="cdd5b-140">您可以執行像是函式來擷取這`degreesFahrenheit`。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="cdd5b-141">此外，當您將維度的值傳遞至函式的預期程度的浮點數時，您必須先取消出單位或轉型為`float`使用`float`運算子。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="cdd5b-142">在此範例中，除以`1.0<degC>`的引數`printf`因為`printf`必須要有此數量。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="cdd5b-143">下列範例工作階段顯示的輸出和輸入此程式碼。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-143">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="cdd5b-144">使用泛型單位</span><span class="sxs-lookup"><span data-stu-id="cdd5b-144">Using Generic Units</span></span>
<span data-ttu-id="cdd5b-145">您可以撰寫操作的泛型函式有相關聯的量值單位的資料。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="cdd5b-146">您藉由指定的類型與泛型單位做為型別參數，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="cdd5b-147">建立彙總類型與泛型單位</span><span class="sxs-lookup"><span data-stu-id="cdd5b-147">Creating Aggregate Types with Generic Units</span></span>
<span data-ttu-id="cdd5b-148">下列程式碼會示範如何建立彙總類型組成的個別浮動點值都是泛型的單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="cdd5b-149">這可讓單一類型來建立適用於各種不同的單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="cdd5b-150">此外，泛型單位保留型別安全確保擁有單位的一組的泛型類型的類型不同於相同的泛型類型具有一組不同的單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="cdd5b-151">這項技術的基礎在於`Measure`屬性可以套用至型別參數。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a><span data-ttu-id="cdd5b-152">在執行階段的單位</span><span class="sxs-lookup"><span data-stu-id="cdd5b-152">Units at Runtime</span></span>
<span data-ttu-id="cdd5b-153">測量單位用於靜態類型檢查。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="cdd5b-154">浮點值會進行編譯，當的測量單位也會刪除，因此單位都將在執行階段遺失。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="cdd5b-155">因此，任何嘗試實作取決於執行階段檢查之單元的功能不可能。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="cdd5b-156">例如，實作`ToString`函式，以列印出單位不可能。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>


## <a name="conversions"></a><span data-ttu-id="cdd5b-157">轉換</span><span class="sxs-lookup"><span data-stu-id="cdd5b-157">Conversions</span></span>
<span data-ttu-id="cdd5b-158">要轉換的類型具有單位 (例如， `float<'u>`) 型別，但是沒有單位，您可以使用標準轉換函式。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="cdd5b-159">例如，您可以使用`float`將轉換成`float`沒有單位，如下列程式碼所示的值。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="cdd5b-160">若要將無單位的值轉換成具有單位的值，您可以乘以與適當的單位值為 1 或 1.0 標註。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="cdd5b-161">不過，撰寫互通性層級，也有某些 explicit 函式可讓您將無單位的值轉換成值的單位。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="cdd5b-162">這些是在[Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3)模組。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="cdd5b-163">例如，若要將無單位轉換`float`至`float<cm>`，使用[FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a><span data-ttu-id="cdd5b-164">F # Power Pack 中的度量單位</span><span class="sxs-lookup"><span data-stu-id="cdd5b-164">Units of Measure in the F# Power Pack</span></span>
<span data-ttu-id="cdd5b-165">提供 F # PowerPack 單元程式庫。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-165">A unit library is available in the F# PowerPack.</span></span> <span data-ttu-id="cdd5b-166">單元程式庫包含 SI 單位和實體的常數。</span><span class="sxs-lookup"><span data-stu-id="cdd5b-166">The unit library includes SI units and physical constants.</span></span>


## <a name="see-also"></a><span data-ttu-id="cdd5b-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdd5b-167">See Also</span></span>
[<span data-ttu-id="cdd5b-168">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="cdd5b-168">F# Language Reference</span></span>](index.md)
