---
title: $ - 字串內插補點 (C# 參考)
description: 字串內插補點提供比傳統字串複合格式化更容易讀取且方便的語法來格式化字串輸出。
ms.date: 03/26/2018
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 407ca9e4744ea9be45867a08e87c502821226472
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="7db78-103">$ - 字串內插補點 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7db78-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="7db78-104">`$` 特殊字元會將字串常值識別為「字串內插補點」。</span><span class="sxs-lookup"><span data-stu-id="7db78-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="7db78-105">插入字串是可能包含「插入運算式」的字串常值。</span><span class="sxs-lookup"><span data-stu-id="7db78-105">An interpolated string is a string literal that might contain *interpolated expressions*.</span></span> <span data-ttu-id="7db78-106">將插入字串解析為結果字串時，會將具有插入運算式的項目取代為運算式結果的字串表示。</span><span class="sxs-lookup"><span data-stu-id="7db78-106">When an interpolated string is resolved to a result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="7db78-107">C# 6 和更新版本的語言中有提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="7db78-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="7db78-108">字串插補在建立格式化字串時，是比[字串複合格式化](../../../standard/base-types/composite-formatting.md)功能更容易理解且方便的語法。</span><span class="sxs-lookup"><span data-stu-id="7db78-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="7db78-109">下列範例會使用這兩項功能，產生相同的輸出：</span><span class="sxs-lookup"><span data-stu-id="7db78-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="7db78-110">插入字串的結構</span><span class="sxs-lookup"><span data-stu-id="7db78-110">Structure of an interpolated string</span></span>

<span data-ttu-id="7db78-111">若要將字串常值識別為插入字串，請在其前面加上 `$` 符號。</span><span class="sxs-lookup"><span data-stu-id="7db78-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="7db78-112">字串常值開頭的 `$` 與 `"` 之間不能有空白字元。</span><span class="sxs-lookup"><span data-stu-id="7db78-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="7db78-113">這樣做會導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="7db78-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="7db78-114">具有插值運算式的項目結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="7db78-114">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="7db78-115">在方括號中的元素是選擇性的元素。</span><span class="sxs-lookup"><span data-stu-id="7db78-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="7db78-116">下表說明每個元素：</span><span class="sxs-lookup"><span data-stu-id="7db78-116">The following table describes each element:</span></span>

|<span data-ttu-id="7db78-117">元素</span><span class="sxs-lookup"><span data-stu-id="7db78-117">Element</span></span>|<span data-ttu-id="7db78-118">描述</span><span class="sxs-lookup"><span data-stu-id="7db78-118">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="7db78-119">產生要格式化之結果的運算式。</span><span class="sxs-lookup"><span data-stu-id="7db78-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="7db78-120">`null` 結果的字串表示是 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7db78-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="7db78-121">常數的運算式，其值定義插值運算式結果的字串表示的字元數下限。</span><span class="sxs-lookup"><span data-stu-id="7db78-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="7db78-122">如果是正數，則字串表示是靠右對齊；如果是負數，它是靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="7db78-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="7db78-123">如需詳細資訊，請參閱[對齊元件](../../../standard/base-types/composite-formatting.md#alignment-component)。</span><span class="sxs-lookup"><span data-stu-id="7db78-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="7db78-124">運算式結果的類型所支援的格式字串。</span><span class="sxs-lookup"><span data-stu-id="7db78-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="7db78-125">如需詳細資訊，請參閱[格式字串元件](../../../standard/base-types/composite-formatting.md#format-string-component)。</span><span class="sxs-lookup"><span data-stu-id="7db78-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="7db78-126">下列範例會使用上述的選擇性格式化元件：</span><span class="sxs-lookup"><span data-stu-id="7db78-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="7db78-127">特殊字元</span><span class="sxs-lookup"><span data-stu-id="7db78-127">Special characters</span></span>

<span data-ttu-id="7db78-128">若要在插入字串所產生的文字中包含大括弧 "{" 或 "}"，請使用雙大括弧 "{{" 或 "}}"。</span><span class="sxs-lookup"><span data-stu-id="7db78-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="7db78-129">如需詳細資訊，請參閱[逸出大括號](../../../standard/base-types/composite-formatting.md#escaping-braces)。</span><span class="sxs-lookup"><span data-stu-id="7db78-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="7db78-130">因為冒號 (":")　在插入運算式項目中具有特殊意義，為了在插入運算式中使用[條件運算子](../operators/conditional-operator.md)，請用括號括住運算式。</span><span class="sxs-lookup"><span data-stu-id="7db78-130">As the colon (":") has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="7db78-131">下列範例示範如何在結果字串中包含大括號以及如何在插入運算式中使用條件運算子：</span><span class="sxs-lookup"><span data-stu-id="7db78-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="7db78-132">逐字插入字串以 `$` 字元為開頭，後面接著 `@` 字元。</span><span class="sxs-lookup"><span data-stu-id="7db78-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="7db78-133">如需逐字字串的詳細資訊，請參閱[字串](../keywords/string.md)和[逐字識別碼](verbatim.md)主題。</span><span class="sxs-lookup"><span data-stu-id="7db78-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="7db78-134">`$` 語彙基元必須出現在逐字內插字串中的 `@` 語彙基元之前。</span><span class="sxs-lookup"><span data-stu-id="7db78-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="7db78-135">隱含轉換和指定 `IFormatProvider` 實作</span><span class="sxs-lookup"><span data-stu-id="7db78-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="7db78-136">有三個來自插入字串的隱含轉換：</span><span class="sxs-lookup"><span data-stu-id="7db78-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="7db78-137">將字串內插補點轉換成字串內插補點解析結果的 <xref:System.String> 執行個體，且插值運算式項目取代為其結果的格式正確字串表示。</span><span class="sxs-lookup"><span data-stu-id="7db78-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="7db78-138">這項轉換會使用目前文化特性。</span><span class="sxs-lookup"><span data-stu-id="7db78-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="7db78-139">將插入字串轉換成 <xref:System.FormattableString> 執行個體，以代表複合格式字串，並將運算式結果格式化。</span><span class="sxs-lookup"><span data-stu-id="7db78-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="7db78-140">那可讓您從單一 <xref:System.FormattableString> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="7db78-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="7db78-141">若要執行此工作，請呼叫下列的其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="7db78-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="7db78-142">產生 <xref:System.Globalization.CultureInfo.CurrentCulture> 的結果字串的 <xref:System.FormattableString.ToString> 多載。</span><span class="sxs-lookup"><span data-stu-id="7db78-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="7db78-143">產生 <xref:System.Globalization.CultureInfo.InvariantCulture> 的結果字串的 <xref:System.FormattableString.Invariant%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7db78-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="7db78-144">產生指定文化特性的結果字串的 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法。</span><span class="sxs-lookup"><span data-stu-id="7db78-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="7db78-145">您也可以使用 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法，提供 <xref:System.IFormatProvider> 介面的使用者定義實作以支援自訂格式。</span><span class="sxs-lookup"><span data-stu-id="7db78-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="7db78-146">如需詳細資訊，請參閱[使用 ICustomFormatter 的自訂格式](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter)。</span><span class="sxs-lookup"><span data-stu-id="7db78-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="7db78-147">將插入字串轉換成 <xref:System.IFormattable> 執行個體，也可讓您從單一 <xref:System.IFormattable> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="7db78-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="7db78-148">下列範例會使用隱含轉換成 <xref:System.FormattableString>，來建立文化特性特定結果字串：</span><span class="sxs-lookup"><span data-stu-id="7db78-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="7db78-149">其他資源</span><span class="sxs-lookup"><span data-stu-id="7db78-149">Additional resources</span></span>

<span data-ttu-id="7db78-150">如果您是字串插補的新手，請參閱 [C# 中的字串插值](../../quick-starts/interpolated-strings.yml)快速入門。</span><span class="sxs-lookup"><span data-stu-id="7db78-150">If you are new to string interpolation, see the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="7db78-151">如需其他範例，請參閱 [C# 中的字串插值](../../tutorials/string-interpolation.md)教學課程。</span><span class="sxs-lookup"><span data-stu-id="7db78-151">For more examples, see the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="see-also"></a><span data-ttu-id="7db78-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7db78-152">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="7db78-153">複合格式</span><span class="sxs-lookup"><span data-stu-id="7db78-153">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="7db78-154">字串</span><span class="sxs-lookup"><span data-stu-id="7db78-154">Strings</span></span>](../../programming-guide/strings/index.md)  
 [<span data-ttu-id="7db78-155">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7db78-155">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="7db78-156">C# 特殊字元</span><span class="sxs-lookup"><span data-stu-id="7db78-156">C# Special Characters</span></span>](index.md)  
 [<span data-ttu-id="7db78-157">C# 參考</span><span class="sxs-lookup"><span data-stu-id="7db78-157">C# Reference</span></span>](../index.md)  