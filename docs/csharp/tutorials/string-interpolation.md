---
title: C# 中的字串插補
description: 了解如何使用字串插補，在 C# 的結果字串中包含已格式化的運算式結果。
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 1a5d451f6fef926f0f142c7f09f564ce95618b39
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188634"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="54d9c-103">C# 中的字串插補</span><span class="sxs-lookup"><span data-stu-id="54d9c-103">String interpolation in C#</span></span> #

<span data-ttu-id="54d9c-104">本教學課程會示範如何使用[字串插補](../language-reference/tokens/interpolated.md)進行格式化，並將運算式結果包含在結果字串中。</span><span class="sxs-lookup"><span data-stu-id="54d9c-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="54d9c-105">這些範例假設您熟悉 C# 基本概念和 .NET 類型格式設定。</span><span class="sxs-lookup"><span data-stu-id="54d9c-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="54d9c-106">如果您不熟悉字串插補或 .NET 類型格式設定，請先參閱[互動式字串插補教學課程](../tutorials/intro-to-csharp/interpolated-strings.yml)。</span><span class="sxs-lookup"><span data-stu-id="54d9c-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](../tutorials/intro-to-csharp/interpolated-strings.yml) first.</span></span> <span data-ttu-id="54d9c-107">如需在 .NET 中格式化類型的詳細資訊，請參閱[在 .NET 中將類型格式化](../../standard/base-types/formatting-types.md)主題。</span><span class="sxs-lookup"><span data-stu-id="54d9c-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="54d9c-108">簡介</span><span class="sxs-lookup"><span data-stu-id="54d9c-108">Introduction</span></span>

<span data-ttu-id="54d9c-109">[字串插補](../language-reference/tokens/interpolated.md)功能是以[複合格式](../../standard/base-types/composite-formatting.md)功能為基礎建置而成，可提供更容易理解且方便的語法，在結果字串中包含已格式化的運算式結果。</span><span class="sxs-lookup"><span data-stu-id="54d9c-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="54d9c-110">若要將字串常值識別為插入字串，請在其前面加上 `$` 符號。</span><span class="sxs-lookup"><span data-stu-id="54d9c-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="54d9c-111">您可以內嵌任何有效的 C# 運算式，以在插入字串中傳回值。</span><span class="sxs-lookup"><span data-stu-id="54d9c-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="54d9c-112">在下列範例中，只要評估運算式，其結果即會轉換成字串，並包含在結果字串中：</span><span class="sxs-lookup"><span data-stu-id="54d9c-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="54d9c-113">如範例所示，藉由用括號括住運算式，即可在插入字串中包含運算式：</span><span class="sxs-lookup"><span data-stu-id="54d9c-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolatedExpression>}
```

<span data-ttu-id="54d9c-114">在編譯時期，插入字串通常會轉換成 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="54d9c-114">At compile time, an interpolated string is typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="54d9c-115">這也可讓[字串複合格式](../../standard/base-types/composite-formatting.md)功能的所有功能供您與插入字串一起使用。</span><span class="sxs-lookup"><span data-stu-id="54d9c-115">That makes all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature available to you to use with interpolated strings as well.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a><span data-ttu-id="54d9c-116">如何指定插入運算式的格式字串</span><span class="sxs-lookup"><span data-stu-id="54d9c-116">How to specify a format string for an interpolated expression</span></span>

<span data-ttu-id="54d9c-117">在插入運算式後面接著冒號 (":") 和格式字串，即可指定運算式結果類型所支援的格式字串：</span><span class="sxs-lookup"><span data-stu-id="54d9c-117">You specify a format string that is supported by the type of the expression result by following the interpolated expression with a colon (":") and the format string:</span></span>

```
{<interpolatedExpression>:<formatString>}
```

<span data-ttu-id="54d9c-118">下列範例會示範如何針對產生日期與時間或數值結果的運算式，指定標準和自訂的格式字串：</span><span class="sxs-lookup"><span data-stu-id="54d9c-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="54d9c-119">如需詳細資訊，請參閱[複合格式](../../standard/base-types/composite-formatting.md)主題的[格式字串元件](../../standard/base-types/composite-formatting.md#format-string-component)一節。</span><span class="sxs-lookup"><span data-stu-id="54d9c-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="54d9c-120">該節中提供了一些主題連結，以描述 .NET 基底類型所支援的標準和自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="54d9c-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a><span data-ttu-id="54d9c-121">如何控制已格式化之插入運算式的欄位寬度和對齊</span><span class="sxs-lookup"><span data-stu-id="54d9c-121">How to control the field width and alignment of the formatted interpolated expression</span></span>

<span data-ttu-id="54d9c-122">在插入運算式後面接著逗號 (",") 和常數運算式，即可指定已格式化之運算式結果的最小欄位寬度和對齊：</span><span class="sxs-lookup"><span data-stu-id="54d9c-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolated expression with a comma (",") and the constant expression:</span></span>

```
{<interpolatedExpression>,<alignment>}
```

<span data-ttu-id="54d9c-123">如果 *alignment* 值是正數，已格式化的運算式結果為靠右對齊；如果是負數，則是靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="54d9c-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="54d9c-124">如果您需要指定對齊和格式字串，請從對齊元件開始：</span><span class="sxs-lookup"><span data-stu-id="54d9c-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="54d9c-125">下列範例會示範如何指定對齊，並使用管道字元 ("|") 來分隔文字欄位：</span><span class="sxs-lookup"><span data-stu-id="54d9c-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="54d9c-126">如範例輸出所示，如果已格式化的運算式結果長度超過指定的欄位寬度，則會忽略 *alignment* 值。</span><span class="sxs-lookup"><span data-stu-id="54d9c-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="54d9c-127">如需詳細資訊，請參閱[複合格式](../../standard/base-types/composite-formatting.md)主題的[對齊元件](../../standard/base-types/composite-formatting.md#alignment-component)一節。</span><span class="sxs-lookup"><span data-stu-id="54d9c-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="54d9c-128">如何在插入字串中使用逸出序列</span><span class="sxs-lookup"><span data-stu-id="54d9c-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="54d9c-129">插入字串支援可用於一般字串常值中所有逸出序列。</span><span class="sxs-lookup"><span data-stu-id="54d9c-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="54d9c-130">如需詳細資訊，請參閱[字串逸出序列](../programming-guide/strings/index.md#string-escape-sequences)。</span><span class="sxs-lookup"><span data-stu-id="54d9c-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="54d9c-131">若要逐字解譯逸出序列，請使用[逐字](../language-reference/tokens/verbatim.md)字串常值。</span><span class="sxs-lookup"><span data-stu-id="54d9c-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="54d9c-132">逐字插入字串以 `$` 字元為開頭，後面接著 `@` 字元。</span><span class="sxs-lookup"><span data-stu-id="54d9c-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="54d9c-133">若要在結果字串中包含大括號 "{" 或 "}"，請使用兩個大括號 "{{" 或 "}}"。</span><span class="sxs-lookup"><span data-stu-id="54d9c-133">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="54d9c-134">如需詳細資訊，請參閱[複合格式](../../standard/base-types/composite-formatting.md)主題的[逸出大括號](../../standard/base-types/composite-formatting.md#escaping-braces)一節。</span><span class="sxs-lookup"><span data-stu-id="54d9c-134">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="54d9c-135">下列範例會示範如何在結果字串中包含大括號，並建構逐字插入字串：</span><span class="sxs-lookup"><span data-stu-id="54d9c-135">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a><span data-ttu-id="54d9c-136">如何在插入運算式中使用三元條件運算子 `?:`</span><span class="sxs-lookup"><span data-stu-id="54d9c-136">How to use a ternary conditional operator `?:` in an interpolated expression</span></span>

<span data-ttu-id="54d9c-137">因為冒號 (":") 在插入運算式的項目中具有特殊意義，為了在運算式中使用[條件運算子](../language-reference/operators/conditional-operator.md)，請用括號括住運算式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="54d9c-137">As the colon (":") has special meaning in an item with an interpolated expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="54d9c-138">如何使用字串插補建立文化特性特有的結果字串</span><span class="sxs-lookup"><span data-stu-id="54d9c-138">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="54d9c-139">根據預設，插入字串會使用 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> 屬性針對所有格式設定作業所定義的目前文化特性。</span><span class="sxs-lookup"><span data-stu-id="54d9c-139">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="54d9c-140">請使用插入字串到 <xref:System.FormattableString?displayProperty=nameWithType> 執行個體的隱含轉換，並呼叫其 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法來建立文化特性特有的結果字串。</span><span class="sxs-lookup"><span data-stu-id="54d9c-140">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="54d9c-141">下列範例顯示如何執行該項工作：</span><span class="sxs-lookup"><span data-stu-id="54d9c-141">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="54d9c-142">如範例所示，您可以使用一個 <xref:System.FormattableString> 執行個體，針對各種文化特性產生多個結果字串。</span><span class="sxs-lookup"><span data-stu-id="54d9c-142">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="54d9c-143">如何建立使用不因文化特性而異的結果字串</span><span class="sxs-lookup"><span data-stu-id="54d9c-143">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="54d9c-144">除了 <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> 方法之外，您還可以使用靜態 <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> 方法將插入字串解析為 <xref:System.Globalization.CultureInfo.InvariantCulture> 的結果字串。</span><span class="sxs-lookup"><span data-stu-id="54d9c-144">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="54d9c-145">下列範例顯示如何執行該項工作：</span><span class="sxs-lookup"><span data-stu-id="54d9c-145">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="54d9c-146">結論</span><span class="sxs-lookup"><span data-stu-id="54d9c-146">Conclusion</span></span>

<span data-ttu-id="54d9c-147">本教學課程描述了使用字串插補的常見案例。</span><span class="sxs-lookup"><span data-stu-id="54d9c-147">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="54d9c-148">如需字串插補的詳細資訊，請參閱[字串插補](../language-reference/tokens/interpolated.md)主題。</span><span class="sxs-lookup"><span data-stu-id="54d9c-148">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="54d9c-149">如需在 .NET 中格式化類型的詳細資訊，請參閱[在 .NET 中格式化類型](../../standard/base-types/formatting-types.md)和[複合格式](../../standard/base-types/composite-formatting.md)主題。</span><span class="sxs-lookup"><span data-stu-id="54d9c-149">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="54d9c-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54d9c-150">See Also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>  
- <xref:System.FormattableString?displayProperty=nameWithType>  
- <xref:System.IFormattable?displayProperty=nameWithType>  
- [<span data-ttu-id="54d9c-151">字串</span><span class="sxs-lookup"><span data-stu-id="54d9c-151">Strings</span></span>](../programming-guide/strings/index.md)  
