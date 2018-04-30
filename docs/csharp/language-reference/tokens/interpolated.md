---
title: $ - 字串內插補點 (C# 參考)
description: 字串內插補點提供比傳統字串複合格式化更容易讀取且方便的語法來格式化字串輸出。
ms.date: 03/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cabb40c9c449780c8c2a504aad3e53938e2ed957
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="46043-103">$ - 字串內插補點 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="46043-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="46043-104">`$` 特殊字元會將字串常值識別為「字串內插補點」。</span><span class="sxs-lookup"><span data-stu-id="46043-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="46043-105">字串插值類似包含「插入運算式」的範本字串。</span><span class="sxs-lookup"><span data-stu-id="46043-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span> <span data-ttu-id="46043-106">將插入字串解析為結果字串時，會將具有插入運算式的項目取代為運算式結果的字串表示。</span><span class="sxs-lookup"><span data-stu-id="46043-106">When the interpolated string is resolved to the result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="46043-107">C# 6 及更新版本有提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="46043-107">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="46043-108">字串插補在建立格式化字串時，是比[字串複合格式化](../../../standard/base-types/composite-formatting.md)功能更容易理解且方便的語法。</span><span class="sxs-lookup"><span data-stu-id="46043-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="46043-109">下列範例會使用這兩項功能，產生相同的輸出：</span><span class="sxs-lookup"><span data-stu-id="46043-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> <span data-ttu-id="46043-110">字串開頭的 `$` 與 `"` 之間不能有空白字元。</span><span class="sxs-lookup"><span data-stu-id="46043-110">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="46043-111">這樣做會導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="46043-111">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="46043-112">具有插值運算式的項目結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="46043-112">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="46043-113">在方括號中的元素是選擇性的元素。</span><span class="sxs-lookup"><span data-stu-id="46043-113">Elements in square brackets are optional.</span></span> <span data-ttu-id="46043-114">下表說明每個元素。</span><span class="sxs-lookup"><span data-stu-id="46043-114">The following table describes each element.</span></span>

|<span data-ttu-id="46043-115">元素</span><span class="sxs-lookup"><span data-stu-id="46043-115">Element</span></span>|<span data-ttu-id="46043-116">描述</span><span class="sxs-lookup"><span data-stu-id="46043-116">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="46043-117">要評估以便格式化結果的運算式。</span><span class="sxs-lookup"><span data-stu-id="46043-117">The expression to evaluate to get a result to be formatted.</span></span> <span data-ttu-id="46043-118">`null` 結果的字串表示是 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="46043-118">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="46043-119">常數的運算式，其值定義插值運算式結果的字串表示的字元數下限。</span><span class="sxs-lookup"><span data-stu-id="46043-119">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="46043-120">如果是正數，則字串表示是靠右對齊。如果是負數，它是靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="46043-120">If positive, the string representation is right-aligned; if negative, it is left-aligned.</span></span> <span data-ttu-id="46043-121">如需詳細資訊，請參閱[對齊元件](../../../standard/base-types/composite-formatting.md#alignment-component)。</span><span class="sxs-lookup"><span data-stu-id="46043-121">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="46043-122">運算式結果的型別所支援的標準或自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="46043-122">A standard or custom format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="46043-123">如需詳細資訊，請參閱[格式字串元件](../../../standard/base-types/composite-formatting.md#format-string-component)。</span><span class="sxs-lookup"><span data-stu-id="46043-123">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="46043-124">下列範例會使用上述的選擇性格式化元件：</span><span class="sxs-lookup"><span data-stu-id="46043-124">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

<span data-ttu-id="46043-125">若要在插入字串所產生的文字中包含大括弧 ("{" 或 "}")，請使用雙大括弧 "{{" 或 "}}"。</span><span class="sxs-lookup"><span data-stu-id="46043-125">To include a brace ("{" or "}") in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="46043-126">如需詳細資訊，請參閱[逸出大括號](../../../standard/base-types/composite-formatting.md#escaping-braces)。</span><span class="sxs-lookup"><span data-stu-id="46043-126">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="46043-127">因為冒號 (:) 在插值運算式項目中具有特殊意義，為了在插值運算式中使用[條件運算子](../operators/conditional-operator.md)，請用括號括住運算式。</span><span class="sxs-lookup"><span data-stu-id="46043-127">As the colon (:) has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="46043-128">下列範例示範如何在結果字串中包含大括號以及如何在插入運算式中使用條件運算子：</span><span class="sxs-lookup"><span data-stu-id="46043-128">The following example shows how to include a brace into the result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="46043-129">逐字內插字串使用 `$` 字元，後面接著 `@` 字元。</span><span class="sxs-lookup"><span data-stu-id="46043-129">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="46043-130">如需逐字字串的詳細資訊，請參閱[字串](../keywords/string.md)主題。</span><span class="sxs-lookup"><span data-stu-id="46043-130">For more information about verbatim strings, see the [string](../keywords/string.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="46043-131">`$` 語彙基元必須出現在逐字內插字串中的 `@` 語彙基元之前。</span><span class="sxs-lookup"><span data-stu-id="46043-131">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

<span data-ttu-id="46043-132">有三個來自插入字串的隱含轉換：</span><span class="sxs-lookup"><span data-stu-id="46043-132">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="46043-133">將字串內插補點轉換成字串內插補點解析結果的 <xref:System.String> 執行個體，且插值運算式項目取代為其結果的格式正確字串表示。</span><span class="sxs-lookup"><span data-stu-id="46043-133">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="46043-134">這項轉換會使用目前文化特性。</span><span class="sxs-lookup"><span data-stu-id="46043-134">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="46043-135">將插入字串轉換成 <xref:System.FormattableString> 執行個體，以代表複合格式字串，並將運算式結果格式化。</span><span class="sxs-lookup"><span data-stu-id="46043-135">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="46043-136">那可讓您從單一 <xref:System.FormattableString> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="46043-136">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="46043-137">若要執行此工作，請呼叫下列的其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="46043-137">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="46043-138">產生 <xref:System.Globalization.CultureInfo.CurrentCulture> 的結果字串的 <xref:System.FormattableString.ToString> 多載。</span><span class="sxs-lookup"><span data-stu-id="46043-138">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="46043-139">產生 <xref:System.Globalization.CultureInfo.InvariantCulture> 的結果字串的 <xref:System.FormattableString.Invariant%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="46043-139">A <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="46043-140">產生指定文化特性的結果字串的 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法。</span><span class="sxs-lookup"><span data-stu-id="46043-140">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

1. <span data-ttu-id="46043-141">將插入字串轉換成 <xref:System.IFormattable> 執行個體，也可讓您從單一 <xref:System.IFormattable> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="46043-141">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="46043-142">下列範例會使用隱含轉換成 <xref:System.FormattableString>，來建立文化特性特定結果字串：</span><span class="sxs-lookup"><span data-stu-id="46043-142">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

<span data-ttu-id="46043-143">如果您是字串插補的新手，請檢查[字串插補](../../quick-starts/interpolated-strings.yml)快速入門。</span><span class="sxs-lookup"><span data-stu-id="46043-143">If you are new to the string interpolation, check the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="46043-144">如需其他範例，請參閱[字串內插補點教學課程](../../tutorials/string-interpolation.md)。</span><span class="sxs-lookup"><span data-stu-id="46043-144">For more examples, see the [string interpolation tutorial](../../tutorials/string-interpolation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46043-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46043-145">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="46043-146">複合格式</span><span class="sxs-lookup"><span data-stu-id="46043-146">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="46043-147">字串</span><span class="sxs-lookup"><span data-stu-id="46043-147">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="46043-148">C# 特殊字元</span><span class="sxs-lookup"><span data-stu-id="46043-148">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)  
 [<span data-ttu-id="46043-149">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="46043-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="46043-150">C# 參考</span><span class="sxs-lookup"><span data-stu-id="46043-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  