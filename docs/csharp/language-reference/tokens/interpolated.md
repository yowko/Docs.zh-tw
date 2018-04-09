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
ms.openlocfilehash: b6873c3b419323fa9f5523143ad607289b6fd6e2
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="82dcd-103">$ - 字串內插補點 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="82dcd-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="82dcd-104">`$` 特殊字元會將字串常值識別為「字串內插補點」。</span><span class="sxs-lookup"><span data-stu-id="82dcd-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="82dcd-105">字串插值類似包含「插入運算式」的範本字串。</span><span class="sxs-lookup"><span data-stu-id="82dcd-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span> <span data-ttu-id="82dcd-106">解析字串內插補點時 (例如在指派陳述式或方法呼叫中)，其插入運算式會以結果的字串表示取代，，以產生結果字串。</span><span class="sxs-lookup"><span data-stu-id="82dcd-106">When the interpolated string is resolved, for example in an assignment statement or a method call, interpolated expressions are replaced by the string representations of their results to produce the result string.</span></span> <span data-ttu-id="82dcd-107">C# 6 及更新版本有提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="82dcd-107">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="82dcd-108">字串內插補點在建立格式化的字串時，是比[字串複合格式化](../../../standard/base-types/composite-formatting.md)功能更容易理解且方便的方式。</span><span class="sxs-lookup"><span data-stu-id="82dcd-108">String interpolation is a more readable and convenient way to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="82dcd-109">下列範例會使用這兩項功能，產生相同的輸出：</span><span class="sxs-lookup"><span data-stu-id="82dcd-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> <span data-ttu-id="82dcd-110">字串開頭的 `$` 與 `"` 之間不能有空白字元。</span><span class="sxs-lookup"><span data-stu-id="82dcd-110">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="82dcd-111">這樣做會導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="82dcd-111">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="82dcd-112">具有插值運算式的項目結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="82dcd-112">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="82dcd-113">在方括號中的元素是選擇性的元素。</span><span class="sxs-lookup"><span data-stu-id="82dcd-113">Elements in square brackets are optional.</span></span> <span data-ttu-id="82dcd-114">下表說明每個元素。</span><span class="sxs-lookup"><span data-stu-id="82dcd-114">The following table describes each element.</span></span>

|<span data-ttu-id="82dcd-115">元素</span><span class="sxs-lookup"><span data-stu-id="82dcd-115">Element</span></span>|<span data-ttu-id="82dcd-116">描述</span><span class="sxs-lookup"><span data-stu-id="82dcd-116">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="82dcd-117">要評估以便格式化結果的運算式。</span><span class="sxs-lookup"><span data-stu-id="82dcd-117">The expression to evaluate to get a result to be formatted.</span></span> <span data-ttu-id="82dcd-118">`null` 結果的字串表示是 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="82dcd-118">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="82dcd-119">常數的運算式，其值定義插值運算式結果的字串表示的字元數下限。</span><span class="sxs-lookup"><span data-stu-id="82dcd-119">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="82dcd-120">如果是正數，則字串表示是靠右對齊。如果是負數，它是靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="82dcd-120">If positive, the string representation is right-aligned; if negative, it is left-aligned.</span></span> <span data-ttu-id="82dcd-121">如需詳細資訊，請參閱[對齊元件](../../../standard/base-types/composite-formatting.md#alignment-component)。</span><span class="sxs-lookup"><span data-stu-id="82dcd-121">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="82dcd-122">運算式結果的型別所支援的標準或自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="82dcd-122">A standard or custom format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="82dcd-123">如需詳細資訊，請參閱[格式字串元件](../../../standard/base-types/composite-formatting.md#format-string-component)。</span><span class="sxs-lookup"><span data-stu-id="82dcd-123">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="82dcd-124">下列範例會使用上表所述的選擇性格式化元件：</span><span class="sxs-lookup"><span data-stu-id="82dcd-124">The following example uses optional formatting components described in the table above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

<span data-ttu-id="82dcd-125">若要在字串內插補點所產生的文字中包含大括弧 ("{" 或 "}")，請使用雙大括弧 "{{" 或 "}}"。</span><span class="sxs-lookup"><span data-stu-id="82dcd-125">To include a curly brace ("{" or "}") in the text produced by an interpolated string, use two curly braces, "{{" or "}}".</span></span> <span data-ttu-id="82dcd-126">如需詳細資訊，請參閱[逸出大括號](../../../standard/base-types/composite-formatting.md#escaping-braces)。</span><span class="sxs-lookup"><span data-stu-id="82dcd-126">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="82dcd-127">因為冒號 (:) 在插值運算式項目中具有特殊意義，為了在插值運算式中使用[條件運算子](../operators/conditional-operator.md)，請用括號括住運算式。</span><span class="sxs-lookup"><span data-stu-id="82dcd-127">As the colon (:) has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="82dcd-128">下列範例示範如何在結果字串中包含大括號以及如何在插值運算式中使用條件運算子：</span><span class="sxs-lookup"><span data-stu-id="82dcd-128">The following example shows how to include a curly brace into the result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="82dcd-129">逐字內插字串使用 `$` 字元，後面接著 `@` 字元。</span><span class="sxs-lookup"><span data-stu-id="82dcd-129">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="82dcd-130">如需逐字字串的詳細資訊，請參閱[字串](../keywords/string.md)主題。</span><span class="sxs-lookup"><span data-stu-id="82dcd-130">For more information about verbatim strings, see the [string](../keywords/string.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="82dcd-131">`$` 語彙基元必須出現在逐字內插字串中的 `@` 語彙基元之前。</span><span class="sxs-lookup"><span data-stu-id="82dcd-131">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions"></a><span data-ttu-id="82dcd-132">隱含轉換</span><span class="sxs-lookup"><span data-stu-id="82dcd-132">Implicit conversions</span></span>

<span data-ttu-id="82dcd-133">有三個來自字串插值的隱含型別轉換：</span><span class="sxs-lookup"><span data-stu-id="82dcd-133">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="82dcd-134">將字串內插補點轉換成字串內插補點解析結果的 <xref:System.String> 執行個體，且插值運算式項目取代為其結果的格式正確字串表示。</span><span class="sxs-lookup"><span data-stu-id="82dcd-134">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="82dcd-135">這項轉換會使用目前文化特性。</span><span class="sxs-lookup"><span data-stu-id="82dcd-135">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="82dcd-136">將字串內插補點轉換成 <xref:System.FormattableString> 變數，以代表複合格式字串，並將運算式結果格式化。</span><span class="sxs-lookup"><span data-stu-id="82dcd-136">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="82dcd-137">那可讓您從單一 <xref:System.FormattableString> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="82dcd-137">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="82dcd-138">若要執行此工作，請呼叫下列的其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="82dcd-138">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="82dcd-139">產生 <xref:System.Globalization.CultureInfo.CurrentCulture> 的結果字串的 <xref:System.FormattableString.ToString> 多載。</span><span class="sxs-lookup"><span data-stu-id="82dcd-139">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="82dcd-140">產生 <xref:System.Globalization.CultureInfo.InvariantCulture> 的結果字串的 <xref:System.FormattableString.Invariant%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="82dcd-140">A <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="82dcd-141">產生指定文化特性的結果字串的 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法。</span><span class="sxs-lookup"><span data-stu-id="82dcd-141">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

1. <span data-ttu-id="82dcd-142">將字串內插補點轉換成 <xref:System.IFormattable> 變數，也可讓您從單一 <xref:System.IFormattable> 執行個體建立多個具有特定文化特性內容的結果字串。</span><span class="sxs-lookup"><span data-stu-id="82dcd-142">Conversion of an interpolated string to an <xref:System.IFormattable> variable that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="82dcd-143">下列範例會使用隱含轉換成<xref:System.FormattableString>，來建立特定文化特性的結果字串：</span><span class="sxs-lookup"><span data-stu-id="82dcd-143">The following example uses implicit conversion to <xref:System.FormattableString> for creating culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-reading"></a><span data-ttu-id="82dcd-144">其他閱讀資料</span><span class="sxs-lookup"><span data-stu-id="82dcd-144">Additional reading</span></span>

<span data-ttu-id="82dcd-145">如果您是字串內插補點的新手，請檢查[字串內插補點快速入門](../../quick-starts//interpolated-strings.yml)。</span><span class="sxs-lookup"><span data-stu-id="82dcd-145">If you are new to the string interpolation, check the [interpolated strings quickstart](../../quick-starts//interpolated-strings.yml).</span></span> <span data-ttu-id="82dcd-146">如需其他範例，請參閱[字串內插補點教學課程](../../tutorials/string-interpolation.md)。</span><span class="sxs-lookup"><span data-stu-id="82dcd-146">For more examples, see the [string interpolation tutorial](../../tutorials/string-interpolation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="82dcd-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82dcd-147">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="82dcd-148">複合格式</span><span class="sxs-lookup"><span data-stu-id="82dcd-148">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="82dcd-149">字串</span><span class="sxs-lookup"><span data-stu-id="82dcd-149">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="82dcd-150">C# 特殊字元</span><span class="sxs-lookup"><span data-stu-id="82dcd-150">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)  
 [<span data-ttu-id="82dcd-151">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="82dcd-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="82dcd-152">C# 參考</span><span class="sxs-lookup"><span data-stu-id="82dcd-152">C# Reference</span></span>](../../../csharp/language-reference/index.md)  