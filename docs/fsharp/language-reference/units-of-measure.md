---
title: 測量單位
description: 瞭解中的浮點數和帶正負號F#的整數值如何具有相關聯的測量單位，通常用來表示長度、數量和品質。
ms.date: 05/16/2016
ms.openlocfilehash: a81f7760301dc580e333d4659a72e6259d2c916b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216684"
---
# <a name="units-of-measure"></a><span data-ttu-id="4bd9a-103">測量單位</span><span class="sxs-lookup"><span data-stu-id="4bd9a-103">Units of Measure</span></span>

<span data-ttu-id="4bd9a-104">中的浮點數和帶正負F#號的整數值可以具有相關聯的測量單位，通常用來表示長度、數量、品質等等。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="4bd9a-105">藉由使用具有單位的數量，您可以讓編譯器驗證算術關聯性是否有正確的單位，這有助於防止程式設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="4bd9a-106">語法</span><span class="sxs-lookup"><span data-stu-id="4bd9a-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="4bd9a-107">備註</span><span class="sxs-lookup"><span data-stu-id="4bd9a-107">Remarks</span></span>

<span data-ttu-id="4bd9a-108">先前的語法會將*單位名稱*定義為量值單位。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="4bd9a-109">選擇性部分是用來根據先前定義的單位來定義新的量值。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="4bd9a-110">例如，下列程式程式碼會定義量值`cm` （釐米）。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="4bd9a-111">下一行會將量值`ml` （milliliter）定義為三釐米（`cm^3`）。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="4bd9a-112">在先前的語法中， *measure*是包含單位的公式。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="4bd9a-113">在牽涉到單位的公式中，整數類支援（正和負數）、單位之間的空格表示兩個單位的產品`*` ，也表示單位的乘積，並`/`指出單位的商。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="4bd9a-114">針對交互單位，您可以使用負整數乘冪或`/` ，表示單位公式的分子和分母之間的分隔。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="4bd9a-115">分母中的多個單位應該以括弧括住。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="4bd9a-116">以空格`/`分隔的單位會解讀為分母的一部分，但`*`後面的任何單位都會被視為分子的一部分。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="4bd9a-117">您可以在單位運算式中使用1來表示量維度數量，或與其他單位（例如分子）一起使用。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="4bd9a-118">例如，速率的單位會寫成`1/s`，其中`s`表示秒數。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="4bd9a-119">單元公式中不使用括弧。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="4bd9a-120">您不會在單元公式中指定數值轉換常數;不過，您可以分別使用單位來定義轉換常數，並在單元檢查計算中使用它們。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="4bd9a-121">表示相同事物的單位公式可以用各種同等的方式撰寫。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="4bd9a-122">因此，編譯器會將單元公式轉換成一致的形式，將負冪轉換成 reciprocals、將單位群組成單一分子和分母，然後 Alphabetizes 分子和分母中的單位。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="4bd9a-123">例如，單位公式`kg m s^-2`和`m /s s * kg`都會轉換成`kg m/s^2`。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="4bd9a-124">您在浮點運算式中使用量值單位。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="4bd9a-125">使用浮點數搭配相關聯的測量單位，會增加另一層的型別安全，並協助避免當您使用弱式類型的浮點數時，公式中可能發生的單位不相符錯誤。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="4bd9a-126">如果您撰寫使用單位的浮點運算式，則運算式中的單位必須相符。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="4bd9a-127">您可以使用單元公式以角括弧標注常值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="4bd9a-128">您不會在數位和角括弧之間加上空格。不過，您可以包含常值尾碼`f`，例如，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="4bd9a-129">這類注釋會將常值的類型從其基本類型（例如`float`）變更為維度類型， `float<cm>`例如或`float<miles/hour>`，在此案例中為。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="4bd9a-130">的`<1>`單位注釋表示量維度數量，而其類型等同于不含 unit 參數的基本型別。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="4bd9a-131">量值單位的類型是一個浮點數或帶正負號的整數類資料類型，以及一個額外的單位注釋，以方括弧表示。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="4bd9a-132">因此，當您將轉換類型從`g` （克`kg` ）寫入（千克）時，您會依照下列方式描述類型。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="4bd9a-133">測量單位用於編譯時間單元檢查，但不會保存在執行時間環境中。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="4bd9a-134">因此，它們不會影響效能。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="4bd9a-135">量值單位可以套用至任何類型，而不只是浮點數類型。不過，只有浮點類型、帶正負號的整數類資料類型和十進位類型支援維度數量。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="4bd9a-136">因此，在基本型別和包含這些基本型別的匯總上使用測量單位是合理的。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="4bd9a-137">下列範例說明測量單位的使用。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

<span data-ttu-id="4bd9a-138">下列程式碼範例說明如何從量值浮點數轉換為已維度的浮點數。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="4bd9a-139">您只要乘以1.0，就會將維度套用至1.0。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="4bd9a-140">您可以將此抽象成類似`degreesFahrenheit`的函式。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="4bd9a-141">此外，當您將已維度的值傳遞給預期會有量維度浮點數的函式時，您必須`float` `float`使用運算子取消單位或轉換成。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="4bd9a-142">在此範例中，您會`1.0<degC>`將的`printf`引數除以`printf` ，因為需要量維度數量。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="4bd9a-143">下列範例會話會顯示此程式碼的輸出和輸入。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-143">The following example session shows the outputs from and inputs to this code.</span></span>

```console
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="4bd9a-144">使用泛型單位</span><span class="sxs-lookup"><span data-stu-id="4bd9a-144">Using Generic Units</span></span>

<span data-ttu-id="4bd9a-145">您可以撰寫可在具有相關聯測量單位的資料上運作的泛型函數。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="4bd9a-146">若要這麼做，您可以將類型與一般單位一起指定為類型參數，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="4bd9a-147">建立具有泛型單位的匯總類型</span><span class="sxs-lookup"><span data-stu-id="4bd9a-147">Creating Aggregate Types with Generic Units</span></span>

<span data-ttu-id="4bd9a-148">下列程式碼示範如何建立匯總類型，其中包含具有泛型單位的個別浮點值。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="4bd9a-149">這可讓您建立單一類型，以搭配各種單位使用。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="4bd9a-150">此外，一般單位會藉由確保具有一組單位的泛型型別與具有不同單位集合的相同泛型型別不同，來保留型別安全。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="4bd9a-151">這項技術的基礎是`Measure`可以將屬性套用至型別參數。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a><span data-ttu-id="4bd9a-152">執行時間的單位</span><span class="sxs-lookup"><span data-stu-id="4bd9a-152">Units at Runtime</span></span>

<span data-ttu-id="4bd9a-153">測量單位用於靜態類型檢查。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="4bd9a-154">當您編譯浮點值時，測量單位會被排除，因此在執行時間會遺失單位。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="4bd9a-155">因此，任何嘗試執行的功能，都不可能發生于檢查執行時間的單位。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="4bd9a-156">例如，不可能執行`ToString`函數來列印單位。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>

## <a name="conversions"></a><span data-ttu-id="4bd9a-157">轉換</span><span class="sxs-lookup"><span data-stu-id="4bd9a-157">Conversions</span></span>

<span data-ttu-id="4bd9a-158">若要將具有單位（例如`float<'u>`）的類型轉換成不具有單位的類型，您可以使用標準轉換函數。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="4bd9a-159">例如，您可以使用`float`將轉換`float`成沒有單位的值，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="4bd9a-160">若要將未使用的值轉換為具有單位的值，您可以乘以以適當單位標注的1或1.0 值。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="4bd9a-161">不過，若要撰寫互通性層，還有一些明確的函式，可讓您用來將沒有單位的值轉換成值。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="4bd9a-162">這些是在[languageprimitives.physicalequality](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3)模組中。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="4bd9a-163">例如，若要從`float`無單位的轉換`float<cm>`為，請使用[FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="4bd9a-164">F#核心程式庫中的測量單位</span><span class="sxs-lookup"><span data-stu-id="4bd9a-164">Units of Measure in the F# Core library</span></span>

<span data-ttu-id="4bd9a-165">在`FSharp.Data.UnitSystems.SI`命名空間中可以使用單位程式庫。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="4bd9a-166">`m`它在`UnitSymbols`子命名空間中的符號形式（例如 for 計量）中包含 SI 單位，而在`UnitNames`子命名空間中， `meter`其完整名稱（例如 for 計量）。</span><span class="sxs-lookup"><span data-stu-id="4bd9a-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bd9a-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bd9a-167">See also</span></span>

- [<span data-ttu-id="4bd9a-168">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="4bd9a-168">F# Language Reference</span></span>](index.md)
