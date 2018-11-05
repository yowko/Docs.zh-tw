---
title: 測量單位 (F#)
description: 了解如何浮點數和帶正負號的整數值，F# 中可以有關聯的量值，通常用來表示長度、 磁碟區，以及大量的單位。
ms.date: 05/16/2016
ms.openlocfilehash: ad2193e25f3c0cee6e73cd529ab43d1e4b6b549b
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "45972513"
---
# <a name="units-of-measure"></a><span data-ttu-id="e757b-103">測量單位</span><span class="sxs-lookup"><span data-stu-id="e757b-103">Units of Measure</span></span>

<span data-ttu-id="e757b-104">在 F# 浮點和帶正負號的整數值可以具有相關聯的度量單位，通常用來表示長度，磁碟區，大量，依此類推。</span><span class="sxs-lookup"><span data-stu-id="e757b-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="e757b-105">藉由使用單位數量，您可以讓編譯器無法驗證算術的關聯性具有正確的單位，這有助於防止程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="e757b-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="e757b-106">語法</span><span class="sxs-lookup"><span data-stu-id="e757b-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="e757b-107">備註</span><span class="sxs-lookup"><span data-stu-id="e757b-107">Remarks</span></span>

<span data-ttu-id="e757b-108">先前的語法會定義*單位名稱*做為度量單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="e757b-109">選擇性的部分用來定義新的量值，依據先前定義的單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="e757b-110">例如下, 面這一行會定義量值`cm`（公分）。</span><span class="sxs-lookup"><span data-stu-id="e757b-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="e757b-111">下面這一行會定義量值`ml`(milliliter) 為三次方公分 (`cm^3`)。</span><span class="sxs-lookup"><span data-stu-id="e757b-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="e757b-112">在先前的語法*量值*是涉及單位的公式。</span><span class="sxs-lookup"><span data-stu-id="e757b-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="e757b-113">在涉及單位的公式，整數類資料的力量並支援 （正面和負面），單位之間的空格會指出兩個單位，產品`*`也表示的單位，產品和`/`表示單位的商數。</span><span class="sxs-lookup"><span data-stu-id="e757b-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="e757b-114">交互單位，您可以使用負值的整數冪或`/`表示的分子和分母單元公式的區隔。</span><span class="sxs-lookup"><span data-stu-id="e757b-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="e757b-115">應該以括號括住在分母中的多個單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="e757b-116">單位以之後的空格分隔`/`解譯為屬於分母，但遵循任何單位`*`都會解譯為屬於分子。</span><span class="sxs-lookup"><span data-stu-id="e757b-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="e757b-117">在單位運算式中，請單獨來指示此數量，或與其他單位，例如分子，您可以使用 1。</span><span class="sxs-lookup"><span data-stu-id="e757b-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="e757b-118">比方說，單位的費率會寫成`1/s`，其中`s`表示秒數。</span><span class="sxs-lookup"><span data-stu-id="e757b-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="e757b-119">括號不會在單位公式中使用。</span><span class="sxs-lookup"><span data-stu-id="e757b-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="e757b-120">您沒有指定單位公式; 中數字轉換常數不過，您可以分開定義單位轉換常數和單位檢查計算中使用它們。</span><span class="sxs-lookup"><span data-stu-id="e757b-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="e757b-121">代表相同意義的單位公式可以以各種不同的對等方式。</span><span class="sxs-lookup"><span data-stu-id="e757b-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="e757b-122">因此，編譯器會將單位公式轉換成一致的格式，這會將負乘方倒數，群組單位轉換成單一的分子和分母中，並依字母順序排列的分子和分母的單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="e757b-123">比方說，單位公式`kg m s^-2`並`m /s s * kg`都會轉換成`kg m/s^2`。</span><span class="sxs-lookup"><span data-stu-id="e757b-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="e757b-124">您可以使用測量的單位中浮動點運算式。</span><span class="sxs-lookup"><span data-stu-id="e757b-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="e757b-125">使用浮點數與相關聯的單位量值新增另一個層級的型別安全，並有助於避免使用弱型別浮點數時，可以發生在公式中的單元不符錯誤。</span><span class="sxs-lookup"><span data-stu-id="e757b-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="e757b-126">如果您撰寫的浮動點使用單位的運算式，必須符合在運算式中的單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="e757b-127">下列範例所示，您可以標註具有單元公式在角括弧中的常值。</span><span class="sxs-lookup"><span data-stu-id="e757b-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="e757b-128">請勿在數字的角括號; 之間的空間不過，您可以包含常值後置詞例如`f`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e757b-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="e757b-129">這類的註解變更的常值型別從其基本類型 (例如`float`) 為維度的類型，例如`float<cm>`或在此情況下， `float<miles/hour>`。</span><span class="sxs-lookup"><span data-stu-id="e757b-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="e757b-130">單位註釋`<1>`指出此數量，以及它的型別等於單元參數的基本類型。</span><span class="sxs-lookup"><span data-stu-id="e757b-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="e757b-131">測量單位的類型是浮點數或帶正負號整數類資料類型，以及額外的單位註釋，方括號中指出。</span><span class="sxs-lookup"><span data-stu-id="e757b-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="e757b-132">因此，當您撰寫的類型轉換`g`（字母組） 到`kg`（公斤），描述類型，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e757b-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="e757b-133">測量單位用於檢查的編譯時間單位，但不是會保存在執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="e757b-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="e757b-134">因此，它們不會影響效能。</span><span class="sxs-lookup"><span data-stu-id="e757b-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="e757b-135">測量單位可以套用至任何類型，不只浮點類型;不過，只有浮點類型，所簽署的整數類資料類型，以及十進位型別建立維度的支援數量。</span><span class="sxs-lookup"><span data-stu-id="e757b-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="e757b-136">因此，它才有意義的基本型別和包含這些基本類型的彙總上使用的測量單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="e757b-137">下列範例說明如何使用的測量單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

<span data-ttu-id="e757b-138">下列程式碼範例說明如何將此的浮點數轉換為維度的浮動點值。</span><span class="sxs-lookup"><span data-stu-id="e757b-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="e757b-139">您只是乘以 1.0 時，將套用至 1.0 的維度。</span><span class="sxs-lookup"><span data-stu-id="e757b-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="e757b-140">您可以執行像是函式簡化`degreesFahrenheit`。</span><span class="sxs-lookup"><span data-stu-id="e757b-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="e757b-141">此外，當您將維度的值傳遞至預期此浮點數的函式時，您必須先取消外延展單位或轉換成`float`使用`float`運算子。</span><span class="sxs-lookup"><span data-stu-id="e757b-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="e757b-142">在此範例中，除以`1.0<degC>`的引數`printf`因為`printf`預期此數量。</span><span class="sxs-lookup"><span data-stu-id="e757b-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="e757b-143">下列範例工作階段會顯示此程式碼的輸入與輸出。</span><span class="sxs-lookup"><span data-stu-id="e757b-143">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="e757b-144">使用泛型的單位</span><span class="sxs-lookup"><span data-stu-id="e757b-144">Using Generic Units</span></span>

<span data-ttu-id="e757b-145">您可以撰寫操作的泛型函式有相關聯的量值單位的資料。</span><span class="sxs-lookup"><span data-stu-id="e757b-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="e757b-146">您可以指定類型，以及泛型的單元型別參數，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="e757b-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="e757b-147">使用泛型的單位建立彙總類型</span><span class="sxs-lookup"><span data-stu-id="e757b-147">Creating Aggregate Types with Generic Units</span></span>

<span data-ttu-id="e757b-148">下列程式碼示範如何建立彙總類型，其中包含的個別浮動點值都是泛型的單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="e757b-149">這可讓單一類型來建立可搭配各種不同的單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="e757b-150">此外，泛型的單位，來確保泛型型別具有一組的單位類型不同於相同的泛型型別具有一組不同的單位保留型別安全。</span><span class="sxs-lookup"><span data-stu-id="e757b-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="e757b-151">這項技術的基礎在於`Measure`屬性可以套用至型別參數。</span><span class="sxs-lookup"><span data-stu-id="e757b-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a><span data-ttu-id="e757b-152">在執行階段的單位</span><span class="sxs-lookup"><span data-stu-id="e757b-152">Units at Runtime</span></span>

<span data-ttu-id="e757b-153">測量單位用於靜態類型檢查。</span><span class="sxs-lookup"><span data-stu-id="e757b-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="e757b-154">浮點值編譯時，會刪除的測量單位，因此在執行階段的單位都會遺失。</span><span class="sxs-lookup"><span data-stu-id="e757b-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="e757b-155">因此，任何嘗試實作取決於在執行階段檢查單位的功能不可能。</span><span class="sxs-lookup"><span data-stu-id="e757b-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="e757b-156">比方說，實作`ToString`函式來列印外延展單位不可能。</span><span class="sxs-lookup"><span data-stu-id="e757b-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>

## <a name="conversions"></a><span data-ttu-id="e757b-157">轉換</span><span class="sxs-lookup"><span data-stu-id="e757b-157">Conversions</span></span>

<span data-ttu-id="e757b-158">若要將具有單位的類型 (例如`float<'u>`) 沒有單位的類型，您可以使用標準轉換函式。</span><span class="sxs-lookup"><span data-stu-id="e757b-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="e757b-159">例如，您可以使用`float`要轉換成`float`沒有單位，如下列程式碼所示的值。</span><span class="sxs-lookup"><span data-stu-id="e757b-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="e757b-160">若要 unitless 值轉換為具有單位的值，可以將由值為 1 或 1.0 標註，利用適當的單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="e757b-161">不過，撰寫互通性層級，也有一些明確函數可用來將 unitless 值轉換為值，單位。</span><span class="sxs-lookup"><span data-stu-id="e757b-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="e757b-162">這些是在[Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3)模組。</span><span class="sxs-lookup"><span data-stu-id="e757b-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="e757b-163">例如，若要從 unitless 轉換`float`要`float<cm>`，使用[FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e757b-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="e757b-164">F# 核心程式庫中的測量單位</span><span class="sxs-lookup"><span data-stu-id="e757b-164">Units of Measure in the F# Core library</span></span>

<span data-ttu-id="e757b-165">單位程式庫都有`FSharp.Data.UnitSystems.SI`命名空間。</span><span class="sxs-lookup"><span data-stu-id="e757b-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="e757b-166">它包含這兩個符號格式的 SI 單位 (類似`m`個計量器) 中`UnitSymbols`子命名空間和其完整名稱 (例如`meter`個計量器) 中`UnitNames`子命名空間。</span><span class="sxs-lookup"><span data-stu-id="e757b-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="e757b-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e757b-167">See also</span></span>

- [<span data-ttu-id="e757b-168">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="e757b-168">F# Language Reference</span></span>](index.md)
