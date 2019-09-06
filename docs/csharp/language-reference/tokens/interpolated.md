---
title: $-字串內插C#補點-參考
ms.custom: seodec18
description: 字串內插補點提供比傳統字串複合格式化更容易讀取且方便的語法來格式化字串輸出。
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 53a8938a373136df65e23c162b94c4d8dc1f30b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253856"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="027bb-103">$-字串插補C# （參考）</span><span class="sxs-lookup"><span data-stu-id="027bb-103">$ - string interpolation (C# reference)</span></span>

<span data-ttu-id="027bb-104">`$` 特殊字元會將字串常值識別為「字串內插補點」。</span><span class="sxs-lookup"><span data-stu-id="027bb-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="027bb-105">插入字串是可能包含「內插補點運算式」的字串常值。</span><span class="sxs-lookup"><span data-stu-id="027bb-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="027bb-106">將插入字串解析為結果字串時，會將具有內插補點運算式之項目取代為運算式結果的字串表示。</span><span class="sxs-lookup"><span data-stu-id="027bb-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="027bb-107">從C# 6 開始就提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="027bb-107">This feature is available starting with C# 6.</span></span>

<span data-ttu-id="027bb-108">字串插補在建立格式化字串時，是比[字串複合格式化](../../../standard/base-types/composite-formatting.md)功能更容易理解且方便的語法。</span><span class="sxs-lookup"><span data-stu-id="027bb-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="027bb-109">下列範例會使用這兩項功能，產生相同的輸出：</span><span class="sxs-lookup"><span data-stu-id="027bb-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="027bb-110">插入字串的結構</span><span class="sxs-lookup"><span data-stu-id="027bb-110">Structure of an interpolated string</span></span>

<span data-ttu-id="027bb-111">若要將字串常值識別為插入字串，請在其前面加上 `$` 符號。</span><span class="sxs-lookup"><span data-stu-id="027bb-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="027bb-112">字串常值開頭的 `$` 與 `"` 之間不能有空白字元。</span><span class="sxs-lookup"><span data-stu-id="027bb-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span>

<span data-ttu-id="027bb-113">具有內插補點運算式的項目結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="027bb-113">The structure of an item with an interpolation expression is as follows:</span></span>

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="027bb-114">在方括號中的元素是選擇性的元素。</span><span class="sxs-lookup"><span data-stu-id="027bb-114">Elements in square brackets are optional.</span></span> <span data-ttu-id="027bb-115">下表說明每個元素：</span><span class="sxs-lookup"><span data-stu-id="027bb-115">The following table describes each element:</span></span>

|<span data-ttu-id="027bb-116">項目</span><span class="sxs-lookup"><span data-stu-id="027bb-116">Element</span></span>|<span data-ttu-id="027bb-117">說明</span><span class="sxs-lookup"><span data-stu-id="027bb-117">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="027bb-118">產生要格式化之結果的運算式。</span><span class="sxs-lookup"><span data-stu-id="027bb-118">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="027bb-119">的`null`字串表示為<xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="027bb-119">String representation of `null` is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="027bb-120">常數運算式，其值會定義運算式結果的字串表示中的最小字元數。</span><span class="sxs-lookup"><span data-stu-id="027bb-120">The constant expression whose value defines the minimum number of characters in the string representation of the expression result.</span></span> <span data-ttu-id="027bb-121">如果是正數，則字串表示是靠右對齊；如果是負數，它是靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="027bb-121">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="027bb-122">如需詳細資訊，請參閱[對齊元件](../../../standard/base-types/composite-formatting.md#alignment-component)。</span><span class="sxs-lookup"><span data-stu-id="027bb-122">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="027bb-123">運算式結果的類型所支援的格式字串。</span><span class="sxs-lookup"><span data-stu-id="027bb-123">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="027bb-124">如需詳細資訊，請參閱[格式字串元件](../../../standard/base-types/composite-formatting.md#format-string-component)。</span><span class="sxs-lookup"><span data-stu-id="027bb-124">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="027bb-125">下列範例會使用上述的選擇性格式化元件：</span><span class="sxs-lookup"><span data-stu-id="027bb-125">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="027bb-126">特殊字元</span><span class="sxs-lookup"><span data-stu-id="027bb-126">Special characters</span></span>

<span data-ttu-id="027bb-127">若要在插入字串所產生的文字中包含大括弧 "{" 或 "}"，請使用雙大括弧 "{{" 或 "}}"。</span><span class="sxs-lookup"><span data-stu-id="027bb-127">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="027bb-128">如需詳細資訊，請參閱[逸出大括號](../../../standard/base-types/composite-formatting.md#escaping-braces)。</span><span class="sxs-lookup"><span data-stu-id="027bb-128">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="027bb-129">因為冒號 (":")　在內插補點運算式項目中具有特殊意義，為了在內插補點運算式中使用[條件運算子](../operators/conditional-operator.md)，請用括弧括住運算式。</span><span class="sxs-lookup"><span data-stu-id="027bb-129">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="027bb-130">下列範例示範如何在結果字串中包含大括弧以及如何在內插補點運算式中使用條件運算子：</span><span class="sxs-lookup"><span data-stu-id="027bb-130">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="027bb-131">內插逐字字串`$`是以字元開頭，後面接著`@`字元。</span><span class="sxs-lookup"><span data-stu-id="027bb-131">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="027bb-132">如需逐字字串的詳細資訊，請參閱[字串](../keywords/string.md)和[逐字識別碼](verbatim.md)主題。</span><span class="sxs-lookup"><span data-stu-id="027bb-132">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="027bb-133">從C# 8.0 開始，您可以依任何`$`順序`@`使用和 token： `$@"..."`和`@$"..."`都是有效的內插逐字字串。</span><span class="sxs-lookup"><span data-stu-id="027bb-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="027bb-134">在較C#舊的版本`$`中，權杖`@`必須出現在標記之前。</span><span class="sxs-lookup"><span data-stu-id="027bb-134">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a><span data-ttu-id="027bb-135">隱含轉換和如何指定`IFormatProvider`實作為</span><span class="sxs-lookup"><span data-stu-id="027bb-135">Implicit conversions and how to specify `IFormatProvider` implementation</span></span>

<span data-ttu-id="027bb-136">有三個來自插入字串的隱含轉換：</span><span class="sxs-lookup"><span data-stu-id="027bb-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="027bb-137">將插入字串轉換成插入字串解析結果的 <xref:System.String> 執行個體，且內插補點運算式項目取代為其結果的格式正確字串表示。</span><span class="sxs-lookup"><span data-stu-id="027bb-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="027bb-138">這種轉換會<xref:System.Globalization.CultureInfo.CurrentCulture>使用來格式化運算式結果。</span><span class="sxs-lookup"><span data-stu-id="027bb-138">This conversion uses the <xref:System.Globalization.CultureInfo.CurrentCulture> to format expression results.</span></span>

1. <span data-ttu-id="027bb-139">將插入字串轉換成 <xref:System.FormattableString> 執行個體，以代表複合格式字串，並將運算式結果格式化。</span><span class="sxs-lookup"><span data-stu-id="027bb-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="027bb-140">那可讓您從單一 <xref:System.FormattableString> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="027bb-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="027bb-141">若要這麼做，請呼叫下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="027bb-141">To do that, call one of the following methods:</span></span>

      - <span data-ttu-id="027bb-142">產生 <xref:System.Globalization.CultureInfo.CurrentCulture> 的結果字串的 <xref:System.FormattableString.ToString> 多載。</span><span class="sxs-lookup"><span data-stu-id="027bb-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="027bb-143">產生 <xref:System.Globalization.CultureInfo.InvariantCulture> 的結果字串的 <xref:System.FormattableString.Invariant%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="027bb-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="027bb-144">產生指定文化特性的結果字串的 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法。</span><span class="sxs-lookup"><span data-stu-id="027bb-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="027bb-145">您也可以使用 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法，提供 <xref:System.IFormatProvider> 介面的使用者定義實作以支援自訂格式。</span><span class="sxs-lookup"><span data-stu-id="027bb-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="027bb-146">如需詳細資訊，請參閱在[.net 中格式化類型](../../../standard/base-types/formatting-types.md)一文中的[使用 ICustomFormatter 自訂格式](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter)一節。</span><span class="sxs-lookup"><span data-stu-id="027bb-146">For more information, see the [Custom formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) section of the [Formatting types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

1. <span data-ttu-id="027bb-147">將插入字串轉換成 <xref:System.IFormattable> 執行個體，也可讓您從單一 <xref:System.IFormattable> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="027bb-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="027bb-148">下列範例會使用隱含轉換成 <xref:System.FormattableString>，來建立文化特性特定結果字串：</span><span class="sxs-lookup"><span data-stu-id="027bb-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="027bb-149">其他資源</span><span class="sxs-lookup"><span data-stu-id="027bb-149">Additional resources</span></span>

<span data-ttu-id="027bb-150">如果您是字串插補的新手，請參閱 [C# 中的字串插補](../../tutorials/exploration/interpolated-strings.yml)互動式教學課程。</span><span class="sxs-lookup"><span data-stu-id="027bb-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="027bb-151">您也可以查看其他教學課程：[C# 中的字串插值](../../tutorials/string-interpolation.md)，其中示範如何使用內插字串來產生格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="027bb-151">You also can check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="027bb-152">內插字串的編譯</span><span class="sxs-lookup"><span data-stu-id="027bb-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="027bb-153">如果內插字串的類型為 `string`，它通常會轉換成 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="027bb-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="027bb-154">如果分析的行為相當於串連，編譯器可以將 <xref:System.String.Format%2A?displayProperty=nameWithType> 取代為 <xref:System.String.Concat%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="027bb-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="027bb-155">如果內插字串的類型為 <xref:System.IFormattable> 或 <xref:System.FormattableString>，編譯器會產生 <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="027bb-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="027bb-156">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="027bb-156">C# language specification</span></span>

<span data-ttu-id="027bb-157">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[內插字串](~/_csharplang/spec/expressions.md#interpolated-strings)一節。</span><span class="sxs-lookup"><span data-stu-id="027bb-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="027bb-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="027bb-158">See also</span></span>

- [<span data-ttu-id="027bb-159">C# 參考</span><span class="sxs-lookup"><span data-stu-id="027bb-159">C# reference</span></span>](../index.md)
- [<span data-ttu-id="027bb-160">C# 特殊字元</span><span class="sxs-lookup"><span data-stu-id="027bb-160">C# special characters</span></span>](index.md)
- [<span data-ttu-id="027bb-161">字串</span><span class="sxs-lookup"><span data-stu-id="027bb-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="027bb-162">格式化數值結果表</span><span class="sxs-lookup"><span data-stu-id="027bb-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="027bb-163">複合格式</span><span class="sxs-lookup"><span data-stu-id="027bb-163">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
